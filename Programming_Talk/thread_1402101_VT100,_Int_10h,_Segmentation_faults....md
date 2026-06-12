---
title: "VT100, Int 10h, Segmentation faults..."
date: 2010-02-08
forum: Programming Talk
---

### Post by Carl Hamlin on 2010-02-08
I'm working on a piece of software for a client who needs it written in assembly language. She'd like me to stick with BIOS interrupts for console manipulation as opposed to VT100 escape sequences.

However, calls to int 10h are returning segfaults and I'm not entirely sure why. Neither is she. Anybody got a clue for us?

---

### Post by rCXer on 2010-02-08
Can you give sample code of an int 10h call that results in a segfault?

---

### Post by Carl Hamlin on 2010-02-08
> **rCXer said:**
> Can you give sample code of an int 10h call that results in a segfault?

You betcha. Here's the first call encountered in the execution flow - the function is attempting to move the console cursor to the upper left corner of the terminal.

```

		mov	ah, 002h
		sub	bh, bh
		sub	dx, dx
		int	010h

```

---

### Post by NathanB on 2010-02-08
A "segmentation fault" indicates that the offending software component is the operating system.  Remove the OS from your target machine and you will be able to make as many calls as you wish to Int 10h (or any other BIOS function) without the nasty OS complaining to you.  :)

If that is not a viable option....  (like most of us) if you desire to retain the comforts of having Operating System facilities & services available to your application, then install onto your target machine a OS that will also allow you to freely call upon BIOS services without complaint.  One example of such is FreeDOS:

[http://www.freedos.org/](http://www.freedos.org/)

HTH!

---

### Post by Carl Hamlin on 2010-02-09
> **NathanB said:**
> A "segmentation fault" indicates that the offending software component is the operating system.  Remove the OS from your target machine and you will be able to make as many calls as you wish to Int 10h (or any other BIOS function) without the nasty OS complaining to you.  :)

Tried it. What a pain!

> **NathanB said:**
> If that is not a viable option....  (like most of us) if you desire to retain the comforts of having Operating System facilities & services available to your application, then install onto your target machine a OS that will also allow you to freely call upon BIOS services without complaint.  One example of such is FreeDOS:

[http://www.freedos.org/](http://www.freedos.org/)

HTH!

Thanks, Nathan. I'll run that by her and see what she thinks. Now where did I leave my flameproof suit?

:D

---

### Post by pbrane on 2010-02-09
I assume you intend to set bh and dx to zero. Wouldn't it be better to xor instead of sub?

Is int10 the only BIOS interrupt that segfaults? And is it only that particular call, or all BIOS interrupts?

Kinda curious about the need for an app written in assembly.

---

