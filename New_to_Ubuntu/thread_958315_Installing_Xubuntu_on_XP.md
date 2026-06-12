---
title: "Installing Xubuntu on XP"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Kubuntox on 2008-10-25
Hi, I just downloaded the latest Xubuntu and its sitting in the Transfers on Opera. I am running XP at the mo, so how do I switch to Xubuntu, and do I need to transfer all my files onto a disc and then put them back on the comp. or will they stay on the hard drive? 

Iv never done this kinda thing before so any other help would be great!

Thanks :)

---

### Post by Duck2006 on 2008-10-25
This may help.

[http://ubuntuforums.org/showthread.php?t=770838](http://ubuntuforums.org/showthread.php?t=770838)

---

### Post by Paqman on 2008-10-25
Depends, do you want to set up a dual-boot (ie: have both XP and Xubuntu?)

First thing you want to do is [burn the disk image you downloaded onto a blank CD](https://help.ubuntu.com/community/BurningIsoHowto). The boot up into that LiveCD and check all your hardware works.

After that, there's two main ways to install:

[list]
[*]With partitioning.
From the LiveCD, click on the install icon. You'll need to partition your hard drive so Windows and Linux can coexist. It's best to plan that in advance.
[*]Without partitioning.
This uses Ubuntu's new Wubi install method. Ubuntu gets installed to a virtual partition that is located on the Windows partition. It's very simple, but you won't be able to use hibernation. You can transfer a Wubi-installed system to a dedicated partition later if you wish.
[/list]

[Psychocats](http://www.psychocats.net/ubuntu/) is a pretty good site that should fill in a lot of blanks for you.

---

### Post by ww711 on 2008-10-25
Would suggest using virtualbox [http://www.virtualbox.org/](http://www.virtualbox.org/) to create a virtual xubuntu machine, in your XP so it's effectively a sandpit system. This way you can have Xubuntu and XP, and you can try installing, setting up a xubuntu machine without any worries about rendering your XP system dead and you still have a functioning system that works.

---

### Post by RadioMirchi on 2008-10-25
thankss dude

---

