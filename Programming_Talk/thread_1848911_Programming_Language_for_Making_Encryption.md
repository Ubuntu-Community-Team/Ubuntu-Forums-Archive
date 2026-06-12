---
title: "Programming Language for Making Encryption?"
date: 2011-09-23
forum: Programming Talk
---

### Post by x-D on 2011-09-23
Hey, which Programming Language would it be recommended to learn, if I wish to learn more about encryption and cryptology. I would like to use it to make my own methods of encryption?

---

### Post by ofnuts on 2011-09-23
> **x-D said:**
> Hey, which Programming Language would it be recommended to learn, if I wish to learn more about encryption and cryptology. I would like to use it to make my own methods of encryption?nything with a good math lib ("BigDecimals" and the like).

---

### Post by x-D on 2011-09-23
> **ofnuts said:**
> nything with a good math lib ("BigDecimals" and the like).
Cheers for the reply, but could you tell me, for instance? Python really doesn't cut it for me, because I have been attempting to use it with little success, for these purposes.

---

### Post by CptPicard on 2011-09-23
Any language will do in the end, but you shouldn't be making your own encryption methods. Best way to study cryptology is just to learn the math, which does not involve programming. Then, when you need to use the methods, use an implementation that is known to be solid.

---

### Post by x-D on 2011-09-23
> **CptPicard said:**
> Any language will do in the end, but you shouldn't be making your own encryption methods. Best way to study cryptology is just to learn the math, which does not involve programming. Then, when you need to use the methods, use an implementation that is known to be solid.

I already know some of the Maths behind it, I was just wondering if there was any Language that would be useful (for personal use), for making encryption methods.

---

### Post by karlson on 2011-09-23
> **x-D said:**
> Hey, which Programming Language would it be recommended to learn, if I wish to learn more about encryption and cryptology. I would like to use it to make my own methods of encryption?

If you want it fast C would be an obvious choice, but have you worked out the math behind the encryption/decryption mechanism?

When you need an implementation example I'd look at OpenSSL

---

### Post by x-D on 2011-09-23
> **karlson said:**
> If you want it fast C would be an obvious choice, but have you worked out the math behind the encryption/decryption mechanism?

When you need an implementation example I'd look at OpenSSL

Yes, I have studied quite a bit of the Maths behind it. I have an idea that I want to attempt to implement.

---

### Post by simeon87 on 2011-09-23
Any programming language can implement encryption so why are you asking this question? As karlson said, others things, such as speed, should be considered. A low-level language such as C would indeed be a good choice as it's a good fit to manipulation of bits and memory.

---

### Post by Bachstelze on 2011-09-23
C is really the only sane choice. With languages with an automated garbage collector like Java or Python, your secrets will basically stay in memory until the garbage collector decides to wipe them, which could very well be never. Some primitives can be implemented in assembly too, I had a lot of fun with Rijndael.

---

### Post by CptPicard on 2011-09-23
> **Bachstelze said:**
> With languages with an automated garbage collector like Java or Python, your secrets will basically stay in memory until the garbage collector decides to wipe them, which could very well be never.

An interesting and very good point. Then again, even in C, you may get swapped out by the OS at will, no?

I still frankly can't understand the idea of trying to implement one's own crypto solutions. It is far, far more important to understand the theory, after which the implementations should be the common, open, generally understood to be safe ones.

---

### Post by Bachstelze on 2011-09-23
> **CptPicard said:**
> An interesting and very good point. Then again, even in C, you may get swapped out by the OS at will, no?

Yes. And there's stuff you leave on the stack and in registers, etc. Today's computers are not designed with security in mind, so at some point you just throw your hands in the air and say there's nothing you can do. :p But at least with C you can remove the biggest part of it.

> I still frankly can't understand the idea of trying to implement one's own crypto solutions. It is far, far more important to understand the theory, after which the implementations should be the common, open, generally understood to be safe ones.

It depends what the goal is. Of course if the goal is to be secure, you use a well-known algorithm *and* implementation. But if one is interested in designing new ones (because someone has to design the good ones, and that someone has to start somewhere), or even just for fun when you understand that it is probably lousy, then implementing your own can be a good exercise.

---

### Post by karlson on 2011-09-23
> **CptPicard said:**
> I still frankly can't understand the idea of trying to implement one's own crypto solutions. It is far, far more important to understand the theory, after which the implementations should be the common, open, generally understood to be safe ones.

Why not accept the possibility that may be the one OP is writing would be better?

---

### Post by Bachstelze on 2011-09-23
> **karlson said:**
> Why not accept the possibility that may be the one OP is writing would be better?

Because if OP had the knowledge to write something better, he wouldn't be asking questions here. Only a handful of good ciphers are designed every decade, and they are designed by people with years of experience.

---

### Post by karlson on 2011-09-23
> **Bachstelze said:**
> Because if OP had the knowledge to write something better, he wouldn't be asking questions here. Only a handful of good ciphers are designed every decade, and they are designed by people with years of experience.

I agree but in 20-30 years it might be.  The thing of it is that time being spent on trying to do this is not yours or mine or CptPicard's it's OP's.  If he chooses to do this and prove to the world that he didn't waste years of his life let him.

---

### Post by Bachstelze on 2011-09-23
> **karlson said:**
> I agree but in 20-30 years it might be.  The thing of it is that time being spent on trying to do this is not yours or mine or CptPicard's it's OP's.  If he chooses to do this and prove to the world that he didn't waste years of his life let him.

That's basically what I said in my message above, but if OP wants to design his own encryption algorithm and *then* use it to encrypt sensitive data, then a warning is very well in order. As I  said, as long as you understand that your algorithm is almost certainly lousy, then go ahead and have fun. :)

---

### Post by x-D on 2011-11-19
> **Bachstelze said:**
> That's basically what I said in my message above, but if OP wants to design his own encryption algorithm and *then* use it to encrypt sensitive data, then a warning is very well in order. As I  said, as long as you understand that your algorithm is almost certainly lousy, then go ahead and have fun. :)
I can assure you, this will not be for anything extensive or overly important. I want to make my own crypto solutions and I thought that maybe getting more hands-on experience would be good. And as previously said, maybe in 20 years; after tinkering, I will be able to create my own solutions that are better than the ones out there today. Who knows? I want to try and it sounds fun. Thanks everyone

---

### Post by davetv on 2011-11-19
Bachstelze vs karlson in a programming methodologies debate would be most entertaining. I respect both of your advices/posts immensely.

Sorry offtopic

---

