---
title: "[SOLVED] 32 or 64 bits?"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by FaBioW114 on 2008-09-05
Hi, I'm new in the Ubuntu community and need to install a program. But in order to do that, I have to know if my OS is 32 or 64 bits... Actually I don't even know exactly what that means... How do I get that information? Please, I want to know how to do that, not just an answer like "oh, if your processor is ***, then it's ** bits".

One last thing: this 32-64-bits-thing is an OS property and a processor property too? I've searched for that in the net I didn't get it.

Thank you!

---

### Post by gmxgeek on 2008-09-05
type in
```

uname -a

```
in a terminal

if you see something like
```

x86_64 GNU/Linux

```

then it is 64 bit, otherwise, is 32

---

### Post by tuxxy on 2008-09-05
Try uname 

> uname -m

---

### Post by Ryadt on 2008-09-05
> **FaBioW114 said:**
> Hi, I'm new in the Ubuntu community and need to install a program. But in order to do that, I have to know if my OS is 32 or 64 bits... Actually I don't even know exactly what that means... How do I get that information? Please, I want to know how to do that, not just an answer like "oh, if your processor is ***, then it's ** bits".

One last thing: this 32-64-bits-thing is an OS property and a processor property too? I've searched for that in the net I didn't get it.

Thank you!

Type in terminal```
uname -m
```
i686 - 32bits
x_64 - 64bits

---

### Post by Archmage on 2008-09-05
It is a processor thing.

If you processor supports it, you can run either 32-bit or 64-bit. If it isn't supporting it, you can run only 32-bit.

64-bit has the potential of beeing slightly faster and supporting more than 3.8 GB memory, but some user have problems with it.

---

### Post by natman on 2008-09-05
Just as a note, if you want to check how much ram you have, open a terminal and type
> free -m
The number under total is the amount of ram if its less than 4000, 32 Linux is fine, if its more than 4000 better off with 64 ( if your processor supports it ) 64 is not as good as 32 but its not far off these days. Have Fun welcome to Ubuntu!

---

### Post by Darkade on 2008-09-05
Try ```
uname -m
```
Also most times you can install 32 bits without problems

---

### Post by sharks on 2008-09-05
32 bit software can be installed in 64 bit.

---

### Post by FaBioW114 on 2008-09-05
Yeah, I got it! Thank you guys! o/

---

### Post by iaculallad on 2008-09-05
> **Ryadt said:**
> Type in terminal```
uname -m
```
i686 - 32bits
x_64 - 64bits

That should be:

x86_64 for the 64-bit :)

---

### Post by knix on 2008-09-06
> **FaBioW114 said:**
> Yeah, I got it! Thank you guys! o/

When you get a chance, could you mark this as solved? It lets other people know they can find an answer, or that you don't need help.
Good luck

---

### Post by Lexicon101 on 2008-09-06
> **FaBioW114 said:**
> Yeah, I got it! Thank you guys! o/

How did you get it from that? That help was.. well.. unhelpful. (I shouldn't say that.. it told you what you were looking for, but not what it meant is what I meant..)
32 bit and 64 bit both refer to how your processor is set up, 32 bit is the default option most of the time, because it's very much more supported than 64 bit, as 32 bit = an i386 processor architecture (one core, one stream) and 64 bit = an i686 processor architecture (multi-core processor).
Most newer processors (all multi-core processors) are 64 bit processors which can run 32 or 64 bit OSes.. Older processors, on the other hand.. (I think a P4 is an example) are just 32 bit processors, and can't do anything with 64 bit code.
So if your uname output says x86_64, you could install the 64 bit version, but remember that a little more setting up is required to run 32 bit code in a 64 bit OS.

(Just a wild guess though, I'd bet your Ubuntu installation is, in fact, 32 bit. It's the one people have the least problem with, and it's the one that sticks out on the download page. If you're not pulling your hair out (since you don't even know what 32 bit and 64 bit are..) you've probably got the default 32 bit. A 64 bit install requires more setup, by the end of which you'd know what it entails.)

---

### Post by FaBioW114 on 2008-09-27
> **knix said:**
> When you get a chance, could you mark this as solved? It lets other people know they can find an answer, or that you don't need help.
Good luck

oh, sorry about that, I'm not very familiar with forums either, i thought the big guys here were supposed to set a topic as solved... ok, i'll handle it right now =)

> **Lexicon101 said:**
> How did you get it from that? That help was.. well.. unhelpful. (I shouldn't say that.. it told you what you were looking for, but not what it meant is what I meant..)
32 bit and 64 bit both refer to how your processor is set up, 32 bit is the default option most of the time, because it's very much more supported than 64 bit, as 32 bit = an i386 processor architecture (one core, one stream) and 64 bit = an i686 processor architecture (multi-core processor).
Most newer processors (all multi-core processors) are 64 bit processors which can run 32 or 64 bit OSes.. Older processors, on the other hand.. (I think a P4 is an example) are just 32 bit processors, and can't do anything with 64 bit code.
So if your uname output says x86_64, you could install the 64 bit version, but remember that a little more setting up is required to run 32 bit code in a 64 bit OS.

(Just a wild guess though, I'd bet your Ubuntu installation is, in fact, 32 bit. It's the one people have the least problem with, and it's the one that sticks out on the download page. If you're not pulling your hair out (since you don't even know what 32 bit and 64 bit are..) you've probably got the default 32 bit. A 64 bit install requires more setup, by the end of which you'd know what it entails.)

what i meant when I said I got it was that i found out if my processor was 32 or 64 bits. But in fact, there was an explanation missing and you explained it =) Thanks \o/

---

