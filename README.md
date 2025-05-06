# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```
#include <stdio.h>

// Power function to return value of (a ^ b) % P
long long int power(long long int a, long long int b, long long int P) {
    long long int result = 1;
    a = a % P;

    while (b > 0) {
        if (b % 2 == 1) {
            result = (result * a) % P;
        }
        b = b >> 1; // b = b / 2
        a = (a * a) % P;
    }

    return result;
}

int main() {
    long long int P, G, x, a, y, b, ka, kb;

    printf("\n***** Diffie-Hellman Key Exchange Algorithm *****\n\n");

    // Input public keys P and G
    printf("Enter the value of P (a prime number): ");
    scanf("%lld", &P);
    printf("Enter the value of G (a primitive root of P): ");
    scanf("%lld", &G);

    // Alice selects private key a
    a = 4;
    printf("\nThe private key a for Alice: %lld\n", a);
    x = power(G, a, P); // Public key sent by Alice

    // Bob selects private key b
    b = 3;
    printf("The private key b for Bob: %lld\n", b);
    y = power(G, b, P); // Public key sent by Bob

    // Shared secret keys calculated
    ka = power(y, a, P); // Alice computes shared secret
    kb = power(x, b, P); // Bob computes shared secret

    printf("\nSecret key for Alice is: %lld\n", ka);
    printf("Secret key for Bob is: %lld\n", kb);

    return 0;
}

```


## Output:

![image](https://github.com/user-attachments/assets/01e1359c-9f93-4a52-a18c-b4e5d66ecfba)


## Result:
  The program is executed successfully

