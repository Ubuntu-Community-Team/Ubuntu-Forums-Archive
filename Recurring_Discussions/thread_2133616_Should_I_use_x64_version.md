---
title: "Should I use x64 version?"
date: 2013-04-08
forum: Recurring Discussions
---

### Post by ymilev on 2013-04-08
Hello!
My laptop is HP Probok 4510s with Core2Duo T5870 processor, running at 2GHz, 4 GB RAM, ATI Radeon HD4350 video card. According to Intel's site thi processor supports x64 instructions.
For the last 5 years I used all the actual Ubuntu x86 versions, with no  significant problems.
As far as I have known the issue for RAM more than 3 GB was the only reason to choose x64 version, but there was isues with another applications for this platform. 
Now I hope this is not an issue.
I read some threads about the differences between x86 and x86_64 platforms. 
Could you advise me what platform is better for my machine?
Should I experience any significant improve in perormance if I reinstall using x86_64 version?
 Thank you

---

### Post by QIII on 2013-04-08
Moved to Recurring Discussions

---

### Post by VeeDubb on 2013-04-08
Here is my simple test to determine whether or not a person should be running 64bit.

Answer these questions in order and follow instructions:

1. Is your computer capable of running 64bit?
Yes: Read and answer #2.
No: Stop here and run 32 bit.
I don't know: Then find out.  Google is your friend.

2. Do you have at least 2GB of RAM?
Yes: Read and answer #3.
No: Stop here and run 32 bit, or buy more RAM and move to question #3 because even though you don't need 64bit to address all your memory without PAE until you reach 4GB, 64bit addressing is 'slightly' less efficient on systems with very little RAM.

3. Are you running obscure/outdated/poorly packaged/unmaintained software that will only work on a 32bit system?
Yes: Read and answer #4.
No: Stop here and run 64 bit.
I don't know: If all of your software either came from a PPA (in other words, you installed with Synaptic, Ubuntu Software Center, or with sudo apt-get install) then you're fine.  If you installed it from source, you're probably fine as long as it's not ancient source code.  If it's windows software installed through wine, you're also just fine.  If it was a binary install that hasn't seen an update in years, you're probably not fine unless you can find a modern replacement.  If all else fails, there's always google....  

4. Are you willing and/or able to replace your outdated garbage software that probably doesn't work well anyway with something that has seen an update in the last 5 years?
Yes: Run 64 bit.
No: Run 32 bit.

As with all the other times that someone has posted the same question recently and had it moved to recurring discussions, you will encounter some folks who are just absolutely stuck on outdated information and ideas from 5-10 years ago about bugs, compatibility, and all the issues that used to be real concerns with 64 bit.  The simple reality is that everyone who's answers to those questions end with "Run 64 bit" can and should be running 64bit.  It is fully mature, fully stable, fully supported, and is increasingly the main focus of forward development.

---

### Post by ymilev on 2013-04-08
Nothing but great thanks

---

### Post by VeeDubb on 2013-04-08
You're very welcome.

---

### Post by 3rdalbum on 2013-04-09
If you can run 64-bit, you should, with two exceptions:

1. You have 1 GiB of RAM or less
2. You're a big emulation fan - some games console emulators are only available for 32-bit (zSNES being the only example I can think of at the moment)

Otherwise you'll probably never come across anything that doesn't work on 64-bit.

---

### Post by ka55o5 on 2013-04-09
> **VeeDubb said:**
> Is your computer capable of running 64bit?
Booting from LiveCD and/or LiveUSB 64-Bit won't work if the hardware can't support it, simple way to check for that..;) :)

> **3rdalbum said:**
> If you can run 64-bit, you should [..]+1

---

