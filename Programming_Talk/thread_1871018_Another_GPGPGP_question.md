---
title: "Another GPG/PGP question"
date: 2011-10-28
forum: Programming Talk
---

### Post by ki4jgt on 2011-10-28
OK, so I've read several online articles about gpg, but they all fall short of actually stating how the protocol works.

So far I've got:
Two large prime numbers (private key) are generated and multiplied (public key). Then a key is generated for each file (password). This password is encrypted using the private key, which is then placed into the header of the (encrypted) file. Basically:

private-key-encrypted(password)
-------------
password-encrypted(file contents)

This is where I fail miserably. In my own expiriment:

Private(7 * 3) = Public(21)

file password = "AAA"

password encryption (letter substitution) = "HDH"

how do I use 21 on "HDH" to arrive back at "AAA"

---

### Post by 11jmb on 2011-10-28
I'll preface this by saying that I have never used PGP/GPG, but I do have experience with cryptosystems, so hopefully I can help you out a bit.

I'm assuming by the description of your keys, you are using RSA. The way RSA works is that its public key is used for encrypting messages, while the private key is used for decrypting cyphertexts. You would be able to let anybody know what your public key is so that they can send you encrypted messages that only you can decode using your private key. For large numbers, prime factorization is an extremely complex NP-complete problem, so while its easy to figure out 7 and 3 from 21 it is almost impossible for numbers in the 1024-2048 bit range


Hope this can shed a bit of light on what you are trying to get done.

---

### Post by Paddy Landau on 2011-10-28
Public-key encryption, which uses prime numbers, works as follows.


[LIST]
[*]Private key = 2 prime numbers.
Public key = the two private keys multiplied together.
[*]Encryption is a process where the file is encoded using the public key.
Decryption is a process where the file is decoded using the private key.
[*]Signing is a process where the file is encoded using the private key.
Verifying is a process where the file is decoded using the public key.
[*]It is possible to encrypt and then sign a file; likewise, to verify and then decode the file.
[*]The private key is **not** embedded anywhere.
[*]Encoding and decoding is a specific process (it is many years since I've looked at this, so I have forgotten the exact process).
[/LIST]

Now, those are less than the basics. In practice, it is significantly more complex, as the two prime numbers chosen need to have certain restrictions in order to increase security.

Cryptology is a large subject, too large for this forum. Start with [Wikipedia's article]("http://en.wikipedia.org/wiki/Cryptography#Public-key_cryptography") and Google and, if you are serious about it, get some books from the library and the bookshops.

---

### Post by ki4jgt on 2011-10-28
> **11jmb said:**
> I'll preface this by saying that I have never used PGP/GPG, but I do have experience with cryptosystems, so hopefully I can help you out a bit.

I'm assuming by the description of your keys, you are using RSA. The way RSA works is that its public key is used for encrypting messages, while the private key is used for decrypting cyphertexts. You would be able to let anybody know what your public key is so that they can send you encrypted messages that only you can decode using your private key. For large numbers, prime factorization is an extremely complex NP-complete problem, so while its easy to figure out 7 and 3 from 21 it is almost impossible for numbers in the 1024-2048 bit range


Hope this can shed a bit of light on what you are trying to get done.

Yeah, I knew that. I was asking how the decrypting end arrives to the conclusion that 7 and 3 were the numbers used. In an ideal system, the two numbers could be any number of prime factors of the public key, how then does the computer which has the public key arrive at the conclusion that the private key used those two factors?

> **Paddy Landau said:**
> Public-key encryption, which uses prime numbers, works as follows.


[LIST]
[*]Private key = 2 prime numbers.
Public key = the two private keys multiplied together.
[*]Encryption is a process where the file is encoded using the public key.
Decryption is a process where the file is decoded using the private key.
[*]Signing is a process where the file is encoded using the private key.
Verifying is a process where the file is decoded using the public key.
[*]It is possible to encrypt and then sign a file; likewise, to verify and then decode the file.
[*]The private key is **not** embedded anywhere.
[*]Encoding and decoding is a specific process (it is many years since I've looked at this, so I have forgotten the exact process).
[/LIST]

Now, those are less than the basics. In practice, it is significantly more complex, as the two prime numbers chosen need to have certain restrictions in order to increase security.

Cryptology is a large subject, too large for this forum. Start with [Wikipedia's article]("http://en.wikipedia.org/wiki/Cryptography#Public-key_cryptography") and Google and, if you are serious about it, get some books from the library and the bookshops.

I wasn't suggesting that the private key was stored within the file. From what I've read, encrypting with either of the keys on fairly large files would take hours (because of the sheer magnitude of the keys and file sizes) To cover this, GPG uses symmetric key cryptology to encrypt the files, (randomly generated password for each file) the file encryption is actually done in another encryption AES256/Blowfish (pick your poison). and then the randomly generated symmetric password (the one which decrypts the file) is encrypted with the private key and then stored on the file's header.
When it's decrypted, the public key decrypts the symmetric password, and the symmetric password is used with whatever original encryption you used to encrypt the file.

That's what I've read so far anyways.


My question, in my example, I used 7 and 3 to come up with 21. How does the recipient's computer come to the point of knowing which factors (7 and 3) were used in the encryption of the file?

When a (larger scaled) public key could possibly have any number of factors in it, how does the computer pull out the factors to decrypt the message?

---

### Post by 11jmb on 2011-10-28
> **ki4jgt said:**
> 
My question, in my example, I used 7 and 3 to come up with 21. How does the recipient's computer come to the point of knowing which factors (7 and 3) were used in the encryption of the file?

When a (larger scaled) public key could possibly have any number of factors in it, how does the computer pull out the factors to decrypt the message?

It doesn't. Prime factorization is extremely complex. 

The way this works is that only you will know the private keys (in this case 7 and 3) and everybody* will know your public keys (in this case 21 and some e). Anybody can encrypt messages with your public key, but only you can decrypt them, because you need to know the private keys to decrypt.

If you want to send an encrypted message to your buddy, you will use his public keys to encrypt your message. He will then use his private keys to decrypt it.


*not everybody, but I'm using as a point that you can give away your public key to anybody you want a message from, and still be secure.

---

### Post by Arndt on 2011-10-29
> **11jmb said:**
>  For large numbers, prime factorization is an extremely complex NP-complete problem,

No fast algorithm for factorization is known yet, but I don't think it has been shown to be NP-complete either.

---

### Post by Bachstelze on 2011-10-29
First thing: you are confusing PGP and RSA. PGP is a protocol that may or may not use RSA at the cryptographic building block. Right now, RSA is standard, but there was ElGamal before it and there will be another one (probably based on elliptic curves) after it. PGP as a protocol does not need to be modified if you use a different algorithm. Since you are really asking about RSA, not PGP, here's how it works:

Private key: two prime numbers p and q, and the decryption exponent a
Public key: the product n of p and q and the encryption exponent b

We choose p, q and b. b must be smaller than the product (p-1)(q-1) (which is &#966;(n), the Euler function of n) and relatively prime to it. Mathematics (theorem of Bachet-Bézout) tells us that if b is relatively prime to &#966;(n), there exists an integer a such that ab gives a remainder of 1 when divided by &#966;(n). Our encryption exponent a is that number.

Now we want to send a message, that we suppose can be represented as an integer x by any method we want (but of course the method must be reversible, so that the recipient can retrieve the message from x). We have the public key of the recipient: n and b. What we do is that we compute the remainder of x to the bth power, divided by n. It is our encrypted message, that we call y.

Now to decrypt the message, the recipient simply does the same with the decryption exponent a: calculate the remainder of y to the ath power divided by n. Mathematics (theorem of Lagrange on finite groups) tells us that this will always produce x.

What this means is that in order to decrypt a message, an attacker needs a way to compute a from the public key (b and n). However, computing a requires b and &#966;(n) = (p-1)(q-1). In other words, you need p and q, not n. As Arndt said, it is believed but not yet proven that computing p and q from n requires exponential time relative to the size of n. If n is 2048 bits, that's a lot of time. (I should add that it is also not proven that the difficulty of attacking RSA is equivalent to that of factoring n, i.e. that factoring n is the only way to attack RSA.)

---

