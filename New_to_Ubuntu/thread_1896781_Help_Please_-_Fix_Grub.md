---
title: "Help Please - Fix Grub"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by luckylucky on 2011-12-17
I loved the old grub.  When I had a problem it was easy to fix.  Ever since grub2, whenever I had some boot problem the only solution I found worked was to simply install another version of Ubuntu in a free partition which then of course would automagically find all the other OSes and create a nice new grub.  It seems that a couple times a year I'd mess up my boot somehow, and honestly I find grub2 to be a pain in the rump.

This time I don't have a free partition and after extensive googling I've not found a suitable solution.  Someone PLEASE PLEASE PLEASE enlighten me on how to install a new grub.

Is there some kind of linux recovery disk (I don't care whether it is ubuntu or something else) that will simply set up a new grub?  Anybody have any suggestions on how to install a new grub.

BTW, I am writting this post from a live CD.

Thanks in advance to any help.

---

### Post by luckylucky on 2011-12-17
For what it is worth I think that a suggestion should be made to the development team to include a program on live CDs that will install a new grub, just like what happens when you install the OS... but not installing the OS, just the grub.

---

### Post by kapsklok on 2011-12-17
I believe you can perform
grub-install /dev/hdx
and it will install grub to your selected device

---

### Post by luckylucky on 2011-12-17
Thanks for the suggestion but I get this error when I try what you said:

mint@mint ~ $ sudo grub-install /dev/hda
grub-probe: error: cannot stat `aufs'.
/usr/sbin/grub-probe: error: cannot stat `aufs'.

Is there another solution?

---

### Post by audiomick on 2011-12-17
Read through this.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

There are instructions for re-installing a fair way down. There is also a lot of useful information about various other things.

---

### Post by luckylucky on 2011-12-17
I hate grub2.  I wish we never changed from grub.

I tried suggestions.  I even downloaded and tried [http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/) but it didn't work for me either.

I'm now, having wasted hours... AGAIN... am backing up and am about to do a fresh install.  And then I'll spend hours re-configuring the system, again.  

Sigh.

I'm signing off, but am leaving this issue as unsolved.

---

### Post by Michael Dooley on 2011-12-17
> **luckylucky said:**
> I hate grub2.  I wish we never changed from grub.

I tried suggestions.  I even downloaded and tried [http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/) but it didn't work for me either.

I'm now, having wasted hours... AGAIN... am backing up and am about to do a fresh install.  And then I'll spend hours re-configuring the system, again.

Hey luckylucky, I feel your pain. However, the page that audiomick referred you to has directions for re-installing grub2. But more importantly, down at the bottom of that page, there are directions for un-installing grub2 and installing good old grub - grub legacy. You know, just text files that are easily configurable.

You should try *that* instead of reinstalling your OS and trying to make the new install mimic the old install.

Good luck however...

---

