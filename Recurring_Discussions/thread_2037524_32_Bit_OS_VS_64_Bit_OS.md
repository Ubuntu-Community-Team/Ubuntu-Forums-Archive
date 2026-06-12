---
title: "32 Bit OS VS 64 Bit OS"
date: 2012-08-04
forum: Recurring Discussions
---

### Post by Shadius on 2012-08-04
Hey everybody! :)

I have a system with 4 GB of RAM, 80 GB HDD, ASUS motherboard, etc. I'm wondering whether to put the 32 bit or 64 bit version of Ubuntu on it. I'm thinking that the 64 bit version would be better because it would take advantage of the 4 GB of RAM, yes? I thought that 64 bit was unstable, so I'm a little hesistant to install it. If I install the 32 bit version, it would use PAE (Physical Address Extension), right? I don't know much about how PAE works, but I read an article that said Linux doesn't like using PAE. Is that true? Could someone explain to me how PAE works in my case and what would be the best version, 32 or 64 bit, to install on my system? Thank you.

---

### Post by oldos2er on 2012-08-04
[https://help.ubuntu.com/community/EnablingPAE/](https://help.ubuntu.com/community/EnablingPAE/)

---

### Post by Shadius on 2012-08-04
Then I guess my question becomes, why use PAE and not 64 bit?

---

### Post by oldos2er on 2012-08-04
Moved to Recurring.

Personally I use 64-bit rather than PAE.

---

### Post by Shadius on 2012-08-04
> **oldos2er said:**
> Moved to Recurring.

Personally I use 64-bit rather than PAE.

That's what I'm trying to figure out for myself. Why did you go for 64 bit instead of PAE? I'm leaning towards the 64 bit version because I read an article that Linux doesn't like PAE.

---

### Post by 3Miro on 2012-08-04
Search the forum, this has been asked and answered a million times.

64-bit is faster, but it uses a bit more RAM.

32-bit is slower and more conservative, but cannot access more than 4GB of RAM (this is system and video card combined).

PAE is a 32-bit version that can access more RAM, but it is slower than the regular 32-bit. It is just a hack, not a real solution.

My advice is: if you have at least 3GB of RAM, go for 64-bit as you can get the extra speed without worrying about the overhead.

---

### Post by Lightstar on 2012-08-04
I had trouble with audio in a few programs on 64bit.  Sometimes I could listen to music but not voice chat, some other times was the opposite.  
I don't have that trouble on 32bit.

I have always used PAE, even from before it was part of the normal kernel (back then i'd install the server kernel and enable pae).
I never had trouble, all my RAM is detected and working fine.

---

### Post by 3Miro on 2012-08-04
> **Lightstar said:**
> I had trouble with audio in a few programs on 64bit.  Sometimes I could listen to music but not voice chat, some other times was the opposite.  
I don't have that trouble on 32bit.

I have always used PAE, even from before it was part of the normal kernel (back then i'd install the server kernel and enable pae).
I never had trouble, all my RAM is detected and working fine.

You must have hit a rare bug. Naturally if you cannot use 64 -bit, then stick to 32, but there is no reason why 64-bit would be any less stable and in fact the opposite can happen too.

There was a time when 64-bit was less stable in general, but this is long gone.

---

### Post by oldos2er on 2012-08-04
> **Shadius said:**
> That's what I'm trying to figure out for myself. Why did you go for 64 bit instead of PAE? 

Because I have a 64-bit CPU.

---

### Post by Shadius on 2012-08-05
Okay, I think I will install Ubuntu 12.04 64 bit since I have 4 GB of RAM and a 64 bit processor. Thank you all for the help.

---

