---
title: "Lubuntu - Virtural computer question and LDXE question"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by aingels on 2014-02-07
I installed Lubuntu 13.10 64 bit at home and it RUNs great haven't had a problem. Expect when i tried to make pipelight work but i uninstalled it and it went back to working great. Got steam working playing some half-life 2 on linux which is sweet. Really enjoying it so far. But work has come along and decided i need to run some windows program from home so I would really like to try a virtual computer to run it so i don't have to use windows at home. Have no desire to duel boot or any of that but I needs something reliable so i can keep getting a pay check. So which virtual PC is going to be the most reliable? Virtualbox, VMware, Qemu? I have tried Virtualbox before but I remember the images seeming to break all the time but that was several years ago and maybe things have improved?

The other question is probably a lot easier when I installed LDXE on debian there is a little box in the lower right hand corner that displays processor usages and that isn't on in Lubuntu is there a way to turn that on?

---

### Post by mikewhatever on 2014-02-07
Just add the CPU indicator to the panel, though I am not really sure how it would help.

---

### Post by SeijiSensei on 2014-02-07
> **aingels said:**
> I have tried Virtualbox before but I remember the images seeming to break all the time but that was several years ago and maybe things have improved?

VirtualBox has worked well for me over the past few years now.  I recommend that you follow the [installation method at virtualbox.org]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions") rather than simply installing the image in the Ubuntu repositories.

Remember that you'll need a good chunk of memory to run a virtualised Windows.  For Win7 I typically allocate 1.5 GB to the virtual machine; for WinXP you can get away with about half that, 768 MB.  This is memory unavailable to Linux when the VM is running, so you'll need a machine with about 2 GB or more depending on the version of Windows you are installing.

---

### Post by aingels on 2014-02-07
Thank you I will give it a try when I get home. Have you had better luck with windows XP or window 7 with the virtualbox? I have licenses available for both. As for the ram I got 4 GB in my computer so should be enough for either.

---

### Post by walterorlin on 2014-02-07
The better way to explain the the cpu frequency is right click the panel click panel applets then click add on cpu usage monitor. You can also use up and down in the from the panel applets.

---

### Post by SeijiSensei on 2014-02-08
> **aingels said:**
> Thank you I will give it a try when I get home. Have you had better luck with windows XP or window 7 with the virtualbox?

Not really. I've used both at different times.  I have a slight preference for Win7, but that's based on the two versions themselves, not their performance in a VirtualBox.

---

