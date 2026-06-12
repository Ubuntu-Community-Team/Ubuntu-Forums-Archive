---
title: "Executable code obfuscation...?"
date: 2007-06-04
forum: Programming Talk
---

### Post by Cheese Sandwich on 2007-06-04
I know this is not in the open-source spirit of this community, but suppose you wanted to obfuscate the algorithm employed within an executable file, say compiled using gcc or a derivative? How easy is it to reverse engineer such an executable file, and are there any techniques to make this more difficult?

---

### Post by pmasiar on 2007-06-04
It all depends on skill level and determination of the reverse-engineer guy. 

Look at obfuscation techniques used for Skype (and tools used to break in anyway): [link](http://www.secdev.org/conf/skype_BHEU06.handout.pdf)

---

### Post by Cheese Sandwich on 2007-06-04
> **pmasiar said:**
> Look at obfuscation techniques used for Skype (and tools used to break in anyway): [link](http://www.secdev.org/conf/skype_BHEU06.handout.pdf)

:lol: Wow - I'm only on page 8 so far & I'm very impressed with Skype's measures, & even more impressed with the debugger!

---

### Post by Lux Perpetua on 2007-06-04
Three words: **self-modifying code**

---

### Post by Cheese Sandwich on 2007-06-04
> **Lux Perpetua said:**
> Three words: **self-modifying code**

I think making a lot of the code data driven (way more so than would be necessary), and populating that data in an obfuscatory way, would be an equivalent measure...

---

### Post by aks44 on 2007-06-04
IMHO obfuscation is a useless waste of time.

If the machine can execute it, a human can understand it too.

The only way to fully protect your code from reverse engineering is to write a program that nobody will ever want to use or disassemble!

---

### Post by amo-ej1 on 2007-06-05
I also second this, whatever you, there will always be machine code, you can only make things more difficult but never impossible .... for example see what's happing with all the playstations, xboxes and nintendo consoles out there even those nontrivial machines draw attention upon them, so imagine the effort you would need to to in software in what companies like ms, nintendo and sony almost fail to do in hardware ... (encrypted firmwares and such) .... 

Apart from this, ... obfuscation is never the way to go, it's better to invest your time in further development of your algorithm and such to gain an advantage towards competitors instead of trying (and failing) to protect everything inside ...

---

### Post by AnRa on 2007-06-05
A simple way to obfuscate your executable is to compress it using [UPX](htpp://upx.sf.net) and remove the UPX headers from the file by hand.

---

### Post by eckertd on 2007-06-05
> **aks44 said:**
> IMHO obfuscation is a useless waste of time.

If the machine can execute it, a human can understand it too.

The only way to fully protect your code from reverse engineering is to write a program that nobody will ever want to use or disassemble!

I've got a drawer full of 5.25" floppies full of these! :D

---

