---
title: "Why do I have to use the --force-architecture flag to install a 32 bit program?"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by venom104 on 2012-05-30
I really don't understand this. I am using a 64 bit OS, and everytime I install a 32 bit deb, I have use the --force-architecture flag. Why is this?

Some helpful info...

I play SWTOR and Diablo 3. For the SWTOR game, I had to install a patch to get it to work under wine; winehq.org explictly states to NOT use the patch in a 64 bit wine install. I also run the nvidia binary driver (the ubuntu one does not support my card), and when I installed it it explicitly asked me if I wanted to install the 32-bit openGL libraries. ALSO, I have an old printer, and they do NOT supply a 64 bit driver for the printer, I used it and it works fine.

Installing a 32 bit deb package does not apparently break break any dependinces, I have not had to run sudo apt-get install -f to fix my system. Not to mention, when installing a 64 bit linux os, you CAN install 32 bit libaries (and they are available under almost every gnu/linux OS).

I could understand if you were trying to install a 64 bit program under a 32 bit system, but why do I have to do the --force-architecture flag to install a 32 bit program under a 64 bit OS?

---

### Post by zombifier25 on 2012-05-31
```
--force-architecture
```
to install a program made for another architecture on your system. Dunno about you, but it makes sense to me.

---

### Post by Paqman on 2012-05-31
> **venom104 said:**
> 
I could understand if you were trying to install a 64 bit program under a 32 bit system, but why do I have to do the --force-architecture flag to install a 32 bit program under a 64 bit OS?

Because by default it will always try to install 64-bit apps. You have to tell it not to.

---

### Post by venom104 on 2012-05-31
> **Paqman said:**
> Because by default it will always try to install 64-bit apps. You have to tell it not to.

I realize the obvious, my question is what the harm is in installing a 32 bit program in a 64 bit system. The libraries exist, and it doesn't break dependices, so why?

---

### Post by cmcanulty on 2012-05-31
Can you give the order of install with force which comes 1st etc?

---

### Post by Dngrsone on 2012-05-31
> **venom104 said:**
> I realize the obvious, my question is what the harm is in installing a 32 bit program in a 64 bit system. The libraries exist, and it doesn't break dependices, so why?

Because you can break things.

The 64-bit OS is essentially running the 32-bit program through an emulator (the OS is *pretending* to be 32-bit), and there are no guarantees that everything will work as intended, dependencies or not.

Using --force-architecture is basically you telling the machine, "I know it isn't the right type of program, but do it anyway, *I* know what I am doing."

Even though sometimes you don't.

---

### Post by wildmanne39 on 2012-05-31
Hi, yep you will force one to many times and break your system most likely at some point.
Thanks

---

