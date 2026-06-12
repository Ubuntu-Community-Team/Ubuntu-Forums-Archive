---
title: "[SOLVED] Installing Ubuntu Studio packages"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by djbushido on 2008-12-01
I was wanting to install the packages for the ubuntu studio programs listed [here]("https://wiki.ubuntu.com/UbuntuStudio/PackageList"). I have seen previously that i need to install the linux-rt kernel, and would like to avoid that if at all possible. So my question is if i can just install the packages listed (like audio and video applications) and avoid the rt kernel. Please make sure your information works, as i have broken two systems over this.

---

### Post by markbuntu on 2008-12-01
The rt kernel has a lot of problems in Intrepid so you are wise to avoid it. Otherwise, just get the ubuntustudio meta packages with synaptic. You can deselect the linux-rt packages if they get selected automatically before you hit apply and start the download/installation. All the meta package does is select all the necessary packages at once and all their dependencies.

It is a really really big download so be aware of that. 

If your connectin breaks Synaptic will try to pick up where it left off which is very helpful.

The rt kernel helps mostly with audio stuff and it really does help but it can be problematic, even in hardy.

Anyway, good luck with that and if you have any problems be sure to come back for help. There is a large collection of Ubuntu Studio how-tos at 

[https://help.ubuntu.com/community/Ubuntu](https://help.ubuntu.com/community/Ubuntu)

Be sure to read them.

---

### Post by djbushido on 2008-12-01
So question before i go through with this: installation of the ubuntustudio-audio package **will not** actually need the linux-rt kernel, because previously on a fresh hardy 8.04 install, doing this broke the system twice. I can't afford for that to happen again. So, installation of ubuntustudio-audio and other meta packages **does not** need the linux-rt, and not installing this **will not** break my system.

---

### Post by snowpine on 2008-12-01
Hi there, the absolute worst-case scenario is that you accidentally install the linux-rt kernel even though you didn't want to. In this case, you can simply select the generic (non-rt) kernel from Grub when you boot the computer. :)

---

### Post by djbushido on 2008-12-01
Is that really all i had to do???
Great, now i look like an idiot.
Anyway, thanks, i will install these soon.

---

