# HILL CIPHER
HILL CIPHER EX. NO: 3 
## AIM:
IMPLEMENTATION OF HILL CIPHER
To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To decrypt the message, each block is multiplied by the inverse of the m trix used for encryption. The matrix used for encryption is the cipher key, and it should be chosen randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

## STEP-1: Read the plain text and key from the user.
## STEP-2: Split the plain text into groups of length three. 
## STEP-3: Arrange the keyword in a 3*3 matrix.
## STEP-4: Multiply the two matrices to obtain the cipher text of length three.
## STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
import numpy as np

def text_to_num(text):
    return [ord(c) - 65 for c in text.upper()]

def num_to_text(nums):
    return ''.join(chr(n % 26 + 65) for n in nums)

plain = input("Enter Plain Text: ").upper().replace(" ", "")
while len(plain) % 3 != 0:
    plain += 'X'

print("Enter 9 key values:")
key = np.array([list(map(int, input().split())) for _ in range(3)])

cipher = ""
for i in range(0, len(plain), 3):
    p = np.array(text_to_num(plain[i:i+3]))
    c = np.dot(key, p) % 26
    cipher += num_to_text(c)

print("Encrypted Text:", cipher)

det = int(round(np.linalg.det(key)))
det_inv = pow(det % 26, -1, 26)
adj = np.round(np.linalg.inv(key) * det).astype(int)
key_inv = (det_inv * adj) % 26

decrypted = ""
for i in range(0, len(cipher), 3):
    c = np.array(text_to_num(cipher[i:i+3]))
    p = np.dot(key_inv, c) % 26
    decrypted += num_to_text(p)

print("Decrypted Text:", decrypted)
```
## OUTPUT

## RESULT
