# EX-NO-12 — ELGAMAL ALGORITHM

## AIM

To implement ElGamal Algorithm.

---

# ALGORITHM

1. ElGamal encryption is a public-key cryptosystem based on the Diffie-Hellman key exchange.

2. Initialization:

   * Choose a large prime number `p`.
   * Choose a primitive root `g`.
   * Select private key `x`.

3. Key Generation:

   * Compute public key:

          y = g^x (mod p)

* Public key: `(p, g, y)`
* Private key: `x`

4. Encryption:

   * Choose random integer `k`.
   * Compute:

```text id="h9p0i3"
c1 = g^k mod p
c2 = m × y^k mod p
```

* Ciphertext is `(c1, c2)`.

5. Decryption:

   * Compute:

```text id="t0zlb8"
s = c1^x mod p
m = c2 × s^-1 mod p
```

6. Security:

   * Security depends on the difficulty of solving the discrete logarithm problem.

---

# PROGRAM

```c id="g1v22h"
#include <stdio.h>
#include <math.h>

int main() {
    int p = 23;
    int g = 5;
    int x = 6;
    int k = 10;
    int m = 15;

    int y, c1, c2;

    // Public key generation
    y = (int)pow(g, x) % p;

    // Encryption
    c1 = (int)pow(g, k) % p;
    c2 = (m * ((int)pow(y, k) % p)) % p;

    printf("Public Key (y): %d\n", y);
    printf("Cipher Text:\n");
    printf("c1 = %d\n", c1);
    printf("c2 = %d\n", c2);

    return 0;
}
```

---

# SAMPLE OUTPUT

```text id="9l9vch"
Public Key (y): 8
Cipher Text:
c1 = 9
c2 = 5
```

---

# RESULT

The ElGamal Algorithm program was implemented and executed successfully.
