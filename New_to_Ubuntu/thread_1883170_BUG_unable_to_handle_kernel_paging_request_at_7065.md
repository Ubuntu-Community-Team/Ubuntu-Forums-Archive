---
title: "BUG: unable to handle kernel paging request at 70655287"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by prookie on 2011-11-18
Hello everyone,

I've experienced crash of the system in the case when I've tried to connect to Internet with my HSPA+ USB Stick (Vodafone Mobile Broadband K4505-Z). I have installed Ubuntu 11.10, and I've installed Xubuntu with Xfce desktop manager over it.
 
When Xfce started, I've logged in, and then I insterted USB stick, clicked Connect, and I've got "black scree on of death". After that I was able only to press power reset button on my PC. This happened for a 4th times now in a week.

My kernel release is:
Linux michelangelo 3.1.0-030100-generic #201110241006 SMP Mon Oct 24 14:20:44 UTC 2011 i686 athlon i386 GNU/Linux

Who can I report this? How is it done? What files I should provide?

I've made a photo of the "black screen of death" providing details and the messages. Unfortunately, I can not attach this in this post because I don't have my camera cable at the moment. Tomorow I will send it here.

Thank you for your help in advance.

pRookie

---

### Post by prookie on 2011-11-21
As I promised, I deliver screenshoots of crashed desktop manager.

pRookie

---

### Post by wolfen69 on 2011-11-21
> **prookie said:**
> 

Who can I report this? How is it done? What files I should provide?



Bugs need to be reported to Launchpad. First you will need to sign up there, sign the ubuntu code of conduct, and get a PGP key. As an example of reporting a bug: let's say I want to report a bug for Nautilus file manager. I would open a terminal and do:
```
ubuntu-bug nautilus
```
which would automatically give launchpad relevant info about your system and nautilus. But, as I mentioned, you need to sign up there first. Here's more info: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by prookie on 2011-12-30
Hello again Ubuntu community,

I didn't have time to cope with the problems causing crashes I've reported a month ago. But last two days I am persistent in solving my problem.

As I've reported earlier, my crashes are sudden and always I've got black screen of death reporting:
"BUG: unable to handle kernel ..."
Also, PID is always different and related to different program (kswapd0, gtk, etc.). 

I've tried to install Fedora 16, and I've got the same problem but more often.

I've tried to install Ubuntu back, and I even got the same problem during installation of OS, so I had to repeat the process.

I think that the problem lies in the kernel support for nVidia nForce2 chipset. How can I report bug on kernel?
 I think, this problem is affecting all distributions.

Regards,
pRookie

---

### Post by prookie on 2012-01-03
It seems that after fresh install of Ubuntu without the SWAP space on disk, I do not have any crashes related to "BUG: unable to handle paging request". The installation is stable for a few day now.

I've made a S.M.A.R.T. disk check and there are no bad sectors and my disk seems OK.

Does anyone has an idea of the cause of crashes on my computer?

pRookie

---

### Post by Bodsda on 2012-01-04
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/848864](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/848864)

Same sort of error reported here. Seems to be an issue with an earlier kernel release.

Bodsda

---

