---
title: "Questions on debootstrap from ubuntu"
date: 2006-06-28
forum: Other OS Talk
---

### Post by SkyNet2029 on 2006-06-28
What I have been attempting (in vain so far) to do is use debootstrap to slap Debian Sarge (31r2a) on a spare partition
(60GB) on my current machine, which is running Kubuntu Dapper
w/ damnsmalllinux on another (350Mb) partition. However,all goes
well until I get to installing the kernel, then it just dumps me into a vicious cycle of dependencies (asking me for a previous kernel image and then yet another after another)  and refuses to move forward. I have been using the installation instructions from the Debian site for i386, to the letter. Double checked, re-ran all of the steps on a fresh install, but no dice. Is anyone aware of a more recent installation manual (and a more useful one) than what is available?
Here is what I have been using: 
[http://www.debian.org/releases/stable/i386/apcs04.html.en]("http://www.debian.org/releases/stable/i386/apcs04.html.en")

as a manual. It seems pretty straight-forward, and I don't believe disk space is an issue, as I have plenty of that. Also, The reason I am installing using this method is my cd-burner died. No USB drive (kid smashed it :o ) . Any pointers would be greatly appreciated. Sorry bout the long post.

---

### Post by SkyNet2029 on 2006-06-28
Nevermind... I ended up sending across my home network to another machine (an iso image I had on hard drive i mean) and pointed debootstrap at it. All is well now.

---

