---
title: "Hardy Heron as guest in VirtualBox"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by CC_Joe on 2008-05-30
Hey all, this is my first post!


I have a question: I'm running 8.04 as a guest OS in VirtualBox (XP is the host). When I try enabling normal or extra visual effects, I get a message saying the effects could not be enabled.

I installed VboxAdditions, to try to fix the problem. That increased my resolution (woot), but didn't help my visual effects problem.

So, I figured I may have to update my drivers. The computer is running Nvidia Geforce 6600. After some browsing I decided to use Envy to auto-install the drivers. But when I run envy it says Nvidia device not detected! I also tried to to install the new nvidia binary driver via add/remove. No luck, either.

Is this a fixable problem? Or is this an intractable Vbox issue? I read on a forum somewhere that virtual machines don't give you the full graphical performance that a dualboot would.


Any suggestions would be much appreciated! This is probably about my 4th hour using a linux distro, so please assume I am a complete newbie.


Thanks,
Joe

---

### Post by overdrank on 2008-05-30
> **CC_Joe said:**
> Hey all, this is my first post!


I have a question: I'm running 8.04 as a guest OS in VirtualBox (XP is the host). When I try enabling normal or extra visual effects, I get a message saying the effects could not be enabled.

I installed VboxAdditions, to try to fix the problem. That increased my resolution (woot), but didn't help my visual effects problem.

So, I figured I may have to update my drivers. The computer is running Nvidia Geforce 6600. After some browsing I decided to use Envy to auto-install the drivers. But when I run envy it says Nvidia device not detected! I also tried to to install the new nvidia binary driver via add/remove. No luck, either.

Is this a fixable problem? Or is this an intractable Vbox issue? I read on a forum somewhere that virtual machines don't give you the full graphical performance that a dualboot would.


Any suggestions would be much appreciated! This is probably about my 4th hour using a linux distro, so please assume I am a complete newbie.


Thanks,
Joe

HI and I believe that the 3d is not support in virtual machines as of yet. :(

---

### Post by Oldsoldier2003 on 2008-05-30
> **overdrank said:**
> HI and I believe that the 3d is not support in virtual machines as of yet. :(

yep VirtualBox can't yet handle many games in a virtualized windows session because of that. Its also the reason compiz effects don't work inside a VM.

---

### Post by CC_Joe on 2008-05-30
Wow, quick reply guys!

Thanks for the info. So I can stop worrying about enabling the eye-candy until I set up dual-boot? Good to know.


-Joe

---

