---
title: "Practicing Power PC 64 Assembly on a x86 workstation?"
date: 2009-12-16
forum: Programming Talk
---

### Post by tophor on 2009-12-16
I want to start programming in Power PC 64 assembly language, but do not have access to a Power PC machine. Is there a way I can write my programs in Power PC 64 assembly, but have them compiled in x86, to see if they actually work in a cmd prompt in Linux?

Kinda like Just in Time, but not?

I don't really want to emulate a Power PC 64 either.

Theres an article on IBM that details the use of cross compilers and emulation, but is it that difficult? I don't care about if it actually is accurate....i just want to practice my skills.

I'd also like to understand any recommendations given. Lots of work is put into cross compiling since almost all game consoles use Power PC.

Thanks.

---

### Post by kahumba on 2009-12-17
I know this isn't a reply you're looking for, sorry, but are you sure you wanna spend your time learning assembly for power pc? What do you need it for? To hack game consoles?

---

### Post by falconindy on 2009-12-17
> **tophor said:**
> I want to start programming in Power PC 64 assembly language, but do not have access to a Power PC machine. Is there a way I can write my programs in Power PC 64 assembly, but have them compiled in x86, to see if they actually work in a cmd prompt in Linux?

Kinda like Just in Time, but not?

I don't really want to emulate a Power PC 64 either.

Theres an article on IBM that details the use of cross compilers and emulation, but is it that difficult? I don't care about if it actually is accurate....i just want to practice my skills.

I'd also like to understand any recommendations given. Lots of work is put into cross compiling since almost all game consoles use Power PC.

Thanks.
Your (lack of) logic is baffling. You want to write low level code for an architecture that you don't want to touch. Even if you can assemble the code on Linux (which yasm can likely do), you have zero way of executing the code to ensure that it runs properly.

If you're going to pursue this in any semi-serious fashion, you need to look into Qemu (cpu virtualization).

---

### Post by Redache on 2009-12-17
You would lose performance in the emulation and I don't understand why you'd even want to learn PPC Assembly anyway.

I'd recommend thinking about why it is you want to learn PPC assembly. If you don't have a PPC machine, then it seems ultimately futile.

---

### Post by tophor on 2009-12-17
....

---

### Post by spykez on 2009-12-22
> **tophor said:**
> I want to start programming in Power PC 64 assembly language, but do not have access to a Power PC machine. 
...snip...
I'd also like to understand any recommendations given. Lots of work is put into cross compiling since almost all game consoles use Power PC....

Firstly, I will state that I think you are likely wasting your time. Just appreciate that statement for what it is. Wasting time is okay, as long as you know that you're doing it :) I waste my time doing lots of silly things myself, hahaha. 

But since you're into time wasting, I would suggest time wasting in a more commonly available (at least in terms of desktop presence) architecture, and hence something you probably already have, how about AMD64? Concepts are the same, really. 

If you remain undeterred, how about geting a real powerpc? 

Short of getting an old cheap ppc mac, I can't think of any other easier / cheaper way of getting a ppc, than buying a fat ps3. If you like your desktop very much you can easily network it to your ps3 and do a lot of stuff on your desktop then test it on the ps3

Why assembly by the way? Why ppc64? I am curious. Have you got some 'big plan' ? :)

As to good links, well, you've probably got the ibm one. Apart from that I would suggest getting one of the many detailed downloadable pdfs on the instruction set, ABI and elf formats (assuming linux), look at what gcc spits out etc.... The way the call stack is set up is quite different from the intel way, I should warn you.

Oh btw, I use YDL 6.2 on my PS3 although I might try ubuntu once I make more room to dual boot by upgrading the HD (which is why I'm here, looking around to see what it's like)

Cheers
Rob

---

