---
title: "Encryption algorithm suggestion?"
date: 2007-09-14
forum: Programming Talk
---

### Post by aks44 on 2007-09-14
These days I've been looking for an encryption algorithm that can operate on 4-bit nibbles rather than full bytes (8-bit), with no success so far.

This is because I'm working with blocks that are made of four base-32 digits (4 x 5-bit = 20 bits, ie. 2 bytes 1/2).

Ideally I'd want a block cypher (with the block size being able to adapt to my total buffer length, it should be possible since I don't have to handle more than 320 bits of data, ie. 16x 20-bit blocks) which has good propagation properties (ideally 1 bit changed propagates to *all* base-32 digits, at least 2 bits per digit).

I'm running out of ideas concerning search terms, and anyway all the algorithms I found (seem to) operate only on 8-bit blocks. The problem with that kind of algorithm is that when I have an odd number of 20-bit blocks, I loose one 4-bit nibble of data. :(


Note: I'm far from being an encryption expert, so if you're knowledgeable in this area please bear with me. :)


So, my question is two-fold:
- any tips regarding that wonderful can-do-it-all encryption algorithm I'm looking for?
- I wonder whether I should go back to base-16 (and make those 20-bits blocks 24-bits wide, even if the 4 additional bits are unused)...


Any suggestions?
(damn I really hate being stuck like that :()

---

### Post by Awalton on 2007-09-14
The problem is at such a small block size you're going to lose a lot of security. Almost all modern block ciphers work on huge blocks, like 64-bits or bigger, because the security of smaller block ciphers is cheesy at best.

What you'd want to do is push your blocks of 20-bits into the cipher as a 32 bit buffer (two for a 64-bit buffer, etc). You can pad out the blocks using anything you want really, just as long as when you go to decode the data on the other end you're remembering the padding you used. Some cryptographers will suggest using random noise for the other bits, but any good block cipher's going to mask the effects of even a constant padding.

My favorite block cipher is Bluefish mainly because it's so easy to implement, and (Block) XXTEA is pretty fun too for the amazingly-small-but-secure aspect of it.

---

### Post by gnusci on 2007-09-14
Did you check OpenSSL?

[http://www.openssl.org/docs/](http://www.openssl.org/docs/)
[http://www.vanemery.com/Linux/Apache/openSSL.html](http://www.vanemery.com/Linux/Apache/openSSL.html)
[http://www.madboa.com/geek/openssl/#encrypt](http://www.madboa.com/geek/openssl/#encrypt)

---

### Post by aks44 on 2007-09-14
> **Awalton said:**
> The problem is at such a small block size you're going to lose a lot of security. Almost all modern block ciphers work on huge blocks, like 64-bits or bigger

Ok, I guess I wasn't precise enough.
My *plain text* data comes in 20-bits blocks (1 up to 16 such 20-bits blocks).

What I'm looking for is a block cypher that can be 20-bits wide (when I have only one block of data), 40-bits wide (2 blocks of data), 60-bits wide (3 blocks) and so on.

ie. the algorithm's block size can "adaptively" match my total buffer length (up to 320 bits, by 20-bits steps).



But anyway, your answer kinda comforted me in my other opinion...
I'd rather pad those 20 bits with 4 more additional bits (to make the blocks a multiple of 8 bits) and switch to base-16 representation.


Thanks for your input.


@gnusci: OpenSSL (and any other PKI system) is way overkill for encoding *at most* 320 bits of data. ;) Moreover, the main goal is to obfuscate the data from the user POV (hence the good propagation requirement), not to make it resistant to serious cryptanalysis.

---

### Post by CptPicard on 2007-09-14
What are your requirements as regards the key and its security and transmission? Such small amounts could be handled by one time pad, and it would easily scale to arbitrary bit length :)

---

### Post by aks44 on 2007-09-14
> **CptPicard said:**
> What are your requirements as regards the key and its security and transmission?

Security: I don't really care as long as it is quite well obfuscated in the user's POV (ie. even very small changes propagate to the whole buffer).

Transmission: by phone (or maybe e-mail) :mrgreen: (that's why I decided in the first place to make it base-32 :oops:)

---

### Post by Awalton on 2007-09-14
You're idea behind encryption is broken. Block ciphers only work on a block at a time, in order to combine blocks, you have to use some kind of Cipher block chaining. The easiest and least secure is just running your plaintext through the cipher and putting the resulting data together (right next to each other), and they get more complicated and secure from there.

You don't *want* a crypto system that only works on 20-bit blocks at a time because they can be broken within about 2 hours on a modern PC. 64-bit blocks are the minimum still considered "secure", with 128-bit block ciphers becoming standard practice.

So how do we make this work? If you've got one chunk of 20-bit data, you need to pad out a 64-bit block, pass it to the block cipher and you're done. If you've got 4 chunks of data (80-bits), you need to find a way to put that into two blocks (either as 2-chunks in each block, or writing over the edge of the block with the first 64-bits in the first chunk and the remaining in the second). This is entirely up to you. Pass both 64-bit blocks to your cipher, and then choose a Mode of Operation to combine them; the easiest is just to take the two 64-bit blocks returned by the block cipher and to concatenated them together and call it done. This is known as "Electronic Code Book" or ECB, and is incredibly weak. A better way is Cipher Block Chaining (CBC mode), where you xor the first block with some known initialization vector (a block of random numbers that's the same size as your block size, 64-bits), then xor the next block with the first block, and so on and so forth. To decrypt, you do the whole process backwards, decode the first block, xor it with the initialization vector to reclaim the original data, and then go down the chain xoring with the previous block.

There are other ways too, but they're less often used. Block ciphers were designed to work off of arbitrary chunks at a time, and to have the programmer decide what is going to be done with those chunks. You might think about switching to a stream cipher if all you want to do is stream in some data with an encryption key and get a stream of encrypted data on the other side.

---

