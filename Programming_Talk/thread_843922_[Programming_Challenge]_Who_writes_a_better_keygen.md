---
title: "[Programming Challenge] Who writes a better keygen for ID Software?"
date: 2008-06-28
forum: Programming Talk
---

### Post by WitchCraft on 2008-06-28
Are you bored?
Do you want to program something, but don't know what?

Then here is something interesting for you:

ID Software, the creators of the famous games Quake & Doom have problems with their product key validation algorithm. 

About the nature of the problem you can read in this hilarious thread here:
[http://www.nixcoders.org/forum/index.php?showtopic=84&](http://www.nixcoders.org/forum/index.php?showtopic=84&)
:lolflag:

Show ID Software that it's easy to develop a more sophisticated and harder to crack key generator ( & validator) than the one they currently use.

The winner gets awarded 60 minutes per hour.

---

### Post by WitchCraft on 2008-06-29
bump.

---

### Post by WitchCraft on 2008-06-30
bump.

---

### Post by WitchCraft on 2008-07-01
bump.

---

### Post by snova on 2008-07-01
This sounds like a cryptographic problem. Actually, several problems:

[LIST=1]
[*]How do you make keys unique? So a key will only work for one copy?
[*]How do you verify a key for a piece of software?
[*]How do you prevent installation without the key? So you can't install it manually by extracting archives and putting everything in the right place? Making it complicated won't help. All you'd need is a legitimate installation to serve as a guide.
[*]How do you make it so that the disk and key cannot be propagated together?
[/LIST]

Being no expert at cryptography, I can't solve any of these.

But I do know enough to tell you (and the abundance of pirated software shows this to be true) that **there is no perfect solution**. There will always be a weakness somewhere, because you cannot trust the client computer to be honest (or anything else). Network protocols can be reverse engineered, responses forged, or even the server forged. Encryption can help authenticate the transmission, but not entirely. Symmetric keys can be recovered from executables, for example.

If it were already solvable, pirated software couldn't exist. This is more evidence of its impossibility.

If a corporation as big as Microsoft can't solve it with all their money, (I hate to say it) we probably can't either. Don't you think that if they could do it, they would?

Free software technically *does* solve this by making piracy pointless- it's free anyway. Though one could also argue that it doesn't solve it, but instead avoids the problem.

I won't apologize for my thoroughly useless post that goes out of its way to tell you how hard it will be. :)

Edit: Oh, wait. You wanted to make one that's merely *harder* to break? Well, there's plenty of those around. Just they're all secret, because if they got out, their weaknesses would be public (instead of merely obfuscated).

---

### Post by qix on 2008-07-01
I'm not registered at the other forum, so I'll ask here:
Why is that charstring the interval 0..15 ??
And why is it 0..20 in Quake4?

I think I got the rest.. hilarious. But as far as I see, it's half of the truth. I think that the "real" keycheck is on the internet play servers, and not on the client - and that it's far more complicated (ie. keys that pass the client check wont always work for internet play).

---

### Post by WitchCraft on 2008-07-01
> **qix said:**
> 
I think that the "real" keycheck is on the internet play servers, and not on the client - and that it's far more complicated (ie. keys that pass the client check wont always work for internet play).

This may be true for Quake4 (i didn't try, but it's what I would, too), but it definitely is not for Quake3.

And with Quake4, you just need to keep trying, one in 100 will probably work, so you can write a little script, which will in turn get your IP banned ;-)))


> **qix said:**
> 
Why is that charstring the interval 0..15 ??
And why is it 0..20 in Quake4?

Because there are 16 valid characters in quake3, and 21 in quake4
16 = array[0..15]
21 = array[0..20]

--> random number must be in interval 0..15 of array in Quake3 and 0..20 in Quake4 :popcorn:

---

### Post by WitchCraft on 2008-07-01
> **snova said:**
> 
[LIST=1]
[*]How do you make keys unique? So a key will only work for one copy?
[*]How do you verify a key for a piece of software?
[*]How do you prevent installation without the key? So you can't install it manually by extracting archives and putting everything in the right place? Making it complicated won't help. All you'd need is a legitimate installation to serve as a guide.
[*]How do you make it so that the disk and key cannot be propagated together?
[/LIST]


Being no expert at cryptography, I can't solve any of these.


Well, it was just a 'Make a better keygen' contest, not a 'Make an unbreakable keygen' contest. You don't need to be a cryptography expert, you only need phantasy...

> **snova said:**
> 
If it were already solvable, pirated software couldn't exist. This is more evidence of its impossibility.

If a corporation as big as Microsoft can't solve it with all their money, (I hate to say it) we probably can't either. Don't you think that if they could do it, they would?

Yes, and they tried hard with Vista Ultimate, I agree.


> **snova said:**
> 
Edit: Oh, wait. You wanted to make one that's merely *harder* to break? Well, there's plenty of those around. Just they're all secret, because if they got out, their weaknesses would be public (instead of merely obfuscated).

:lolflag: YEA, well said, I agree 200%


However, the first step in making it less breakable would be to make a non-bijective verification algorithm, meaning that if an evil hacker reverse engineers (or simply reads the source code), he can have the algorithm, but that won't help him/her, because he/she then couldn't reconstruct the key creation algorithm from the key verification algorithm.

Meaning you would learn the first thing from any cryptographic algorithm, if you have ever seen one: use the unary operators ^ | & and combine them with fantasy and mathematical aptitude.



[B]PS (@everybody):
This should be a programming contest. The motto should be 'do whatever you can', and not 'search reasons why it can't be done perfectly'.[/B]

---

### Post by Npl on 2008-07-02
> **WitchCraft said:**
> However, the first step in making it less breakable would be to make a non-bijective verification algorithm, meaning that if an evil hacker reverse engineers (or simply reads the source code), he can have the algorithm, but that won't help him/her, because he/she then couldn't reconstruct the key creation algorithm from the key verification algorithm.That unfortunatly aint helping alot unless we are talking about HUGE keys (200 decimals or more). Otherwise the hacker can just rip out the verification-algorithm and test randomly generated keys until one passes. You can obfusicate your code, but anything that a computer can run can be reversed.

---

### Post by snova on 2008-07-02
> However, the first step in making it less breakable would be to make a non-bijective verification algorithm, meaning that if an evil hacker reverse engineers (or simply reads the source code), he can have the algorithm, but that won't help him/her, because he/she then couldn't reconstruct the key creation algorithm from the key verification algorithm.

This is a fundamental assumption in cryptography- that the enemy has every detail about your system and its implementation.

>  Meaning you would learn the first thing from any cryptographic algorithm, if you have ever seen one: use the unary operators ^ | & and combine them with fantasy and mathematical aptitude.

Oh sure. I've seen plenty. That's not to say they are entirely readable, and I look at what are supposed to be reference implementations.

But believe me, there's a lot more to Rijndael, Twofish, SHA, and all the rest than bitwise operators. I really have no idea what a Galois field is, but I know that they are popular in block ciphers. Along with finite-field theory and a good deal of matrix math (which is way over my head).

The fantasy part seems appropriate as well. Ciphers don't have a very long lifespan. Some are broken the hour they are proposed!

> That unfortunately won't help a lot unless we are talking about HUGE keys (200 decimals or more). Otherwise the hacker can just rip out the verification-algorithm and test randomly generated keys until one passes. You can obfuscate your code, but anything that a computer can run can be reversed.

Quite true. Assuming 32 bit integers, 6400 bits is way more than necessary. (It's also more than practical to expect of the average consumer. 25 characters is long enough!) My ElGamal encryption key is only 4096 bits, and that's considered *large*. Most block ciphers these days accept 128 bit keys, or 256 if the need arises.

Anyway, I've come up with another problem to solve:

[LIST=5]
[*]It should not be that every copy of the software must be different, as this would be to much work. Only the keys should differ.
[/LIST]

I don't know much about Quake, but if it's as popular as I think it is, there's no way ID Software is going to stamp out thousands of disks, non of which are the same. It's just not practical (or is it? I really have no idea.).

Once again, I have used my knowledge to inform you of the impossibility of the task, without offering any possible solution.

I have, however, realized something.

The client cannot trust the server, it might be faked. However, it won't do any good to fake an OkayToPlay reply, because the real server won't allow it anyway. This might have been obvious to everybody else, but I only just noticed this. You can, then, assume that the server is impartial. The client, of course, cannot be trusted no matter how you do it.

---

### Post by WitchCraft on 2008-07-06
> **snova said:**
> This is a fundamental assumption in cryptography- that the enemy has every detail about your system and its implementation.


If you take that to the logical extreme, then private-public key cryptography would be useless, because you have to save the private key somewhere on your system (at least if it's a server).

> **snova said:**
> 
But believe me, there's a lot more to Rijndael, Twofish, SHA, and all the rest than bitwise operators.

I hope so. Unfortunately that's not always the case. Besides, if you think that a math student knows more about galouise theory then what is in the wikipedia article, then you don't understand the miserable quality of education in math @ universities.

> **snova said:**
> 
The fantasy part seems appropriate as well. Ciphers don't have a very long lifespan. Some are broken the hour they are proposed!

Well, you should read a book about basic cryptoanalysis first, before implementing a cryptograhic algorithm. Quite often, PHD people don't do that (the: I am good - i don't need that - syndrome), e.g leading to such perls as the 'magenta algorithm'.

> 
Quite true. Assuming 32 bit integers, 6400 bits is way more than necessary. (It's also more than practical to expect of the average consumer. 25 characters is long enough!) My ElGamal encryption key is only 4096 bits, and that's considered *large*. Most block ciphers these days accept 128 bit keys, or 256 if the need arises.

The windows vista ultimate product key is not more than 25 characters - and hasn't been broken, yet. There are brute force attacks, yes, but they don't even deliver usable results on a supercomputer cluster...
However, that doesn't mean you cannot circumvent the key verification algorithm (clock bug, oem bios emulation, bios/mbr-hack)
But so far the vista key has remained unhacked, just for being non-bijective (and for using a more complex verification algorithm on the server, that  is to say incomplete verification at the client when not online)... It's not that easy to try it out with a brute-force attack, at least not if a pattern in the keys is sufficiently unrecognizable...


> 
I have, however, realized something.

The client cannot trust the server, 

it might be faked. However, it won't do any good to fake an OkayToPlay reply, because the real server won't allow it anyway. This might have been obvious to everybody else, but I only just noticed this. You can, then, assume that the server is impartial. 

Well, you cannot fake a game server when you don't have the code/binary.
(Well, not without exorbitant effort) 
You could of course disable key checking on the server, if you had one, but deploying the server amongst the clients would 1. mean for the company to give away the COMPLETE key verification algorithm (pure stupidity), or it would 2. mean that you could only play on the manipulated servers (only your own). 


> 
The client, of course, cannot be trusted no matter how you do it.
Agreed, and not only for key verification, if you would put collision detection on the client, you wouldn't have to wounder about players walking through walls or being immortal. None-the-less, it wouldn't be the first time if some moron working at a gaming company committed such a stupidity... :lolflag:

---

