---
title: "Skype in 8.04"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by pijiu on 2008-04-26
I'm just wondering if people have any trouble installing skype on Hardy Heron? When I open the .deb file it tells me "Wrong architecture 'i386'" and doesn't let me install the package.

Can anyone tell me what this means and if you require more information please tell me what.

---

### Post by FuturePilot on 2008-04-26
Are you running 64bit? Sounds like you're trying to install a package built for a different architecture.

---

### Post by enigmaniac23 on 2008-04-26
I installed Skype on both a fresh install of 8.04 without any problems.  

I also had Skype on another computer that was upgraded to 8.04, and on that one, I had to re-install skype, but it re-installed fine.  Sounds like maybe you have the wrong .deb?

---

### Post by MillDaKill on 2008-04-26
> **FuturePilot said:**
> Are you running 64bit? Sounds like you're trying to install a package built for a different architecture.

Can skype be installed on 64bit 8.04, I am having the same problem as the OP,

Just installed 8.04 64 bit.

---

### Post by pijiu on 2008-04-26
I don't think I'm running 64bit, I installed ubuntu via 'wubi' (how can i check). When I click on the ubuntu dl link on the skype website I get this file skype-debian_2.0.0.68-1_i386.deb, I'm assuming this is wrong? I also tried adding repositories but they didn't work.

---

### Post by enigmaniac23 on 2008-04-26
Check out this thread for installing skype in 64 bit.

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

---

### Post by janmartin on 2008-04-26
Hi piju,

you are using Wubi, so I assume you are running a Windows and testing Ubuntu.

First, goto Windows System Information and check what processor you have. Anything "64" and its a 64 bit architecture.

Then follow this link to check what Ubuntu thinks it is.
[http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/](http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/)

I am not aware if Wubi can run a 32 bit Ubuntu on a 64 bit Windows?

In that case reinstall the matching 64 bit Ubuntu first, then try Skype again.

Good Luck!

---

### Post by mooks007 on 2008-04-27
I'm a newb, I installed Ubuntu 8.04 via Wubu, I downloaded skype from skype.com (the latest, for Ubi, 7.10).  I installed the .deb file and skype installed fine without any errors. It worked for a bit, then I started having sound problems where I couldn't hear the other person, or another where they couldn't hear me. When I would go to shut skype down it wouldn't shut down. Kill process is the only thing that would close it.
I've read that skype doesn't work with the Pulse Audio that 8.04 uses. Is there a way to make skype work/stable?
Skype is really the only thing stopping me from making the complete switch.

---

