---
title: "Black Death"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by Darren01 on 2012-03-05
I've knackered my Ubuntu box.  When I log in from wibu I get the following,

"
*Stopping save kernel messages                [ OK ]
*Starting CUPS printing spooler/server        [ OK ]
*Starting bluetooth                                     [ OK ]
*PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
*checking battery state...                           [ OK ]

*Stopping System V runlevel compatibility   [ OK ]

*Stopping CPU interrupts balancing daemon [ OK ]
"

At this point the instrument hangs.  All I see is a black screen with the above messages at the top of it.

When I try to boot up through the recovery mode I get to,

"
root@ubuntu:~#
"

except the tilde appears to be in the superscript position, which I don't know how to reproduce.

I can exit from root and login from my account but from thereon I can't do anything.  For example, when I type in,

"
startx
"
I get lots of error messages.

Can anyone help?
Prior to this I was installing software (OpenBugs).

Darren.

---

### Post by An Sanct on 2012-03-05
Welcome to the forums!

Well, wubi is actually not meant to be a *real* install, it is meant for testing and previewing purposes. Just like a Live USB, it has a *read only* part, thus a limitation on what you can do (like install things, that make deeper changes to the system, eg. kernel updates, ...)

---

### Post by Mark Phelps on 2012-03-06
Good grief!! Never cease to be amazed by the MIS-information that folks spread on this forum ...

Wubi is NOT read-only!!  Wubi just installs from INSIDE MS Windows into a virtual file system.  Apart from that, it runs and works pretty much like a separate Ubuntu install.

Sorry ... but don't use Wubi myself, so don't really know how to fix it.

---

### Post by muteXe on 2012-03-06
Is this definately a wubi install?  It's the way the OP says
> 
I've knackered my Ubuntu *box*

 that makes me wonder.

---

### Post by Frogs Hair on 2012-03-06
From the information given I can only suggest these two links. 

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)  (WubiMega)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by mlentink on 2012-03-06
Where did the previous posters get the idea that this is a wubi install? There's nothing the OP said that indicates that.

EDIT: unless you meant wubi rather than 'wibu', which is likely... my bad

@An Sanct: I agree with Mark Phelps. What wubi does i install a fully functional Ubuntu into a large windows file acting as a virtual disk for Ubuntu. Therefore you can, if you want, update as usual, including kernel updates. No read-only stuff.

@Darren01: Sorry, haven't the foggiest. But  it most certainly doesn't look nice. Do you have backups (or a separate /home-partition)?

---

### Post by Darren01 on 2012-03-06
wubi may (most probably is) a red herring.

Can anyone suggest how I would go about trying to fix my system?


Anyone, anyone, anyone?

---

### Post by An Sanct on 2012-03-06
So i see i caused a little commotion there, guessing the wrong thing (wubi/wibu) :) 

Anyhow, I still do not know which version of Ubuntu (it may help a lot) and a whole bunch of other informations. As I could track, open bugs has a deb package for 10.10 and source install options - which did you choose?

PS. So it is not wubi .. it is wibu ... please be kind and explain "wibu"? :)
PS2. wubi-sorry to anybody, who was upset by my misinterpretation of how this peace pf software works (if desired, I will also remove the misleading post)

---

