---
title: "open VMS operating system"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by reham on 2011-11-05
hi,everyone.
I am a new in a DCL(Digital Command Language),and the operating system for it is openvms,i didn't find  a free .iso software for it, and i don't know another solution for execute the DCL commands ,anyone can help me anyway.

thanks,
reham

---

### Post by haqking on 2011-11-05
> **reham said:**
> hi,everyone.
I am a new in a DCL(Digital Command Language),and the operating system for it is openvms,i didn't find  a free .iso software for it, and i don't know another solution for execute the DCL commands ,anyone can help me anyway.

thanks,
reham

You want a .iso for what ?

DCL is the command language used to be used on DEC equipment which usually used VMS.

So you want a .iso for VMS ? to install on what ? a home PC ?

use an emulator, there are a few Alpha, VAX emulators out there.

There used to be one in the repos but i cant remember its name

---

### Post by reham on 2011-11-05
do you mean that i donot need OS to execute this commands?only this emulator do that?

---

### Post by haqking on 2011-11-05
> **reham said:**
> do you mean that i donot need OS to execute this commands?only this emulator do that?

i need you to explain more first before i can answer succinctly.

You want to be able to execute DCL commands (for studying i presume)

Then yes you can do so with an emulator.

Or do you mean you need to connect to a DEC (PDP or something) and you need to execute these commands on a live system ?

If you type **simh** into the software centre, that is the emulator i was referring to before, it contains 33 different emulations. one of them is VAX/VMS

---

### Post by reham on 2011-11-05
i will explain for you.
i am a beginner in a training,they told me some scripting languages to learn,inside them DCL,TCL/TK, i didn't hear about them ; so i am so conflict about using them ,if you have any guide for me,it would be from my pleasure.

Respectfully, 
Reham

---

### Post by haqking on 2011-11-05
> **reham said:**
> i will explain for you.
i am a beginner in a training,they told me some scripting languages to learn,inside them DCL,TCL/TK, i didn't hear about them ; so i am so conflict about using them ,if you have any guide for me,it would be from my pleasure.

Respectfully, 
Reham

TCL/TK you already have installed.

You can access it with

```
tclsh
``` from terminal

that will bring you to the % prompt.

You can use DCL in the emulator i mentioned

---

### Post by reham on 2011-11-05
Thanks a lot.

---

### Post by haqking on 2011-11-05
> **reham said:**
> Thanks a lot.

no worries, good luck.

If your problem is solved please use thread tools to mark as solved, cheers.

---

