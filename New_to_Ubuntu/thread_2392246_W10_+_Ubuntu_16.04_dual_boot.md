---
title: "W10 + Ubuntu 16.04 dual boot"
date: 2018-05-18
forum: New to Ubuntu
---

### Post by regentix on 2018-05-18
Hello, I'm not sure if this is the right place to ask this question, but why not give it a shot.

I installed Ubuntu 16.04 as my main OS a few months ago. Turns out i need w10 quite often for school and work, so I would like to dual boot w10 + Ubuntu 16.04.

Is it possible for me to make a system image of my current OS to then use it in the dual booting process so i don't lose everything i have on this system?

I am new to dual booting and all the fancy knowledge that goes along this topic, so any help would be highly appreciated.

Thanks!

---

### Post by monkeybrain20122 on 2018-05-18
If you have at least 4G of ram, just put win in virtualbox, save you lots of troubles.

---

### Post by regentix on 2018-05-18
> **monkeybrain20122 said:**
> If you have at least 4G of ram, just put win in virtualbox, save you lots of troubles.

Hello monkeybrain20122, i do run windows 10 inside virtualbox, but i ran into a problem where i need to run Windows XP inside a vm for a school project. I couldn't install the Windows XP inside my windows 10 client for some odd reason.

---

### Post by monkeybrain20122 on 2018-05-18
> **regentix said:**
> Hello monkeybrain20122, i do run windows 10 inside virtualbox, but i ran into a problem where i need to run Windows XP inside a vm for a school project. I couldn't install the Windows XP inside my windows 10 client for some odd reason.

You can run both xp and win10 as separate clients in VB instead of nesting XP inside Win10. Just out of curiosity, what kind of school project would require XP?? Doesn't look like it would be a useful thing to learn if it can't work without obsolete software.

---

### Post by regentix on 2018-05-18
> **monkeybrain20122 said:**
> You can run both xp and win10 as separate clients in VB instead of nesting XP inside Win10. Just out of curiosity, what kind of school project would require XP?? Doesn't look like it would be a useful thing to learn if it can't work without obsolete software.

The windows XP has netbeans with a default project of a tv applet. I have tried to run it in vmware and virtualbox, but this doesn't work. 
Inside VMware workstation player 12, i can select "open a virtual machine" but up on clicking and submitting the MHP.vmx file, nothing happens...

When i try to do the same in virtualbox, I select windows xp 32 bit and "use an existing virtual hard disk file" with the MHP.vmdk file. Up on launching, i receive "problem while loading operating system"

I also get this error inside my windos 10 (in the vm) that has vmware installed.

I'm quite clueless on what to do next...

---

### Post by monkeybrain20122 on 2018-05-18
> **regentix said:**
> The windows XP has netbeans with a default project of a tv applet. I have tried to run it in vmware and virtualbox, but this doesn't work. 
Inside VMware workstation player 12, i can select "open a virtual machine" but up on clicking and submitting the MHP.vmx file, nothing happens...

When i try to do the same in virtualbox, I select windows xp 32 bit and "use an existing virtual hard disk file" with the MHP.vmdk file. Up on launching, i receive "problem while loading operating system"

I also get this error inside my windos 10 (in the vm) that has vmware installed.

I'm quite clueless on what to do next...

I could be wrong, but I don't think VB uses .vmx files. Not sure about VMware, never used it. But if your VM image doesn't work then it won't work even if you dualboot with Win10 and put xp in a VM inside, and I don't think you can make a dualboot with XP from a VM file.

It seems that you need XP, Win10 is neither here nor there. Do you have a XP .iso?

(But still I don't see the value of a school project using obsolete tools, maybe you should ask your teacher about that)

---

### Post by regentix on 2018-05-18
> **monkeybrain20122 said:**
> I could be wrong, but I don't think VB uses .vmx files. Not sure about VMware, never used it. But if your VM image doesn't work then it won't work even if you dualboot with Win10 and put xp in a VM inside, and I don't think you can make a dualboot with XP from a VM file.

It seems that you need XP, Win10 is neither here nor there. Do you have a XP .iso?

(But still I don't see the value of a school project using obsolete tools, maybe you should ask your teacher about that)

I've had it working when i had windows 10 on this same laptop. I was running the .vmx inside VMware and that worked. Thats my idea behind the windows 10 ubuntu dual boot. Guess i'll have to ask my teacher again..
And i'm not sure why we are using XP for this... When a student asked him why the *bleep* we are using XP, he says that alot of applets still run on obsolete tools, and that IF somebody ever asks us to make an applet for such obsolete systems, we can do it.

Anyways, thanks for willing to help! I do appreciate it a lot!

---

### Post by monkeybrain20122 on 2018-05-18
> **regentix said:**
> I've had it working when i had windows 10 on this same laptop. I was running the .vmx inside VMware and that worked. Thats my idea behind the windows 10 ubuntu dual boot. Guess i'll have to ask my teacher again..
And i'm not sure why we are using XP for this... When a student asked him why the *bleep* we are using XP, he says that alot of applets still run on obsolete tools, and that IF somebody ever asks us to make an applet for such obsolete systems, we can do it.

Anyways, thanks for willing to help! I do appreciate it a lot!

Do you mean the xp VM doesn't work at all or just that app?

Sounds like your teacher is one of those dead woods who know only obsolete tools because they haven't learned anything new for the last 10 years. I know the type, once taught in a community college for a semester. :)

And what if people don't have XP? Is he going to provide that?

---

### Post by pete-br on 2018-05-21
Dual-booting should allow you to install Windows 10 next to Ubuntu, so it should give you a solution.

The first question to answer is how does your system boot?
Does it use the old BIOS way, or is it a newer UEFI based system?

---

### Post by pete-br on 2018-05-21
Before messing around with booting things, you should realize that you could lose access to you current OS if you make a mistake.

Did you make a backup of your system? Do you have experience in backing up? You really should make a backup first!

---

