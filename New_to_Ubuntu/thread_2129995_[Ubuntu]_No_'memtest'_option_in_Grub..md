---
title: "[Ubuntu] No 'memtest' option in Grub."
date: 2013-03-27
forum: New to Ubuntu
---

### Post by jimafternoon on 2013-03-27
I've been trying to run a memtest but I don't have the option in Grub. I'm running Ubuntu 12.10 64 bit, dual boot with Win7

All I get is this:

Ubuntu
Advanced Options for Ubuntu
Windows 7 (loader) on /dev/sda1
Windows 7 (loader) on /dev/sda2

I tried to run a live USB (the one I installed from) but I don't have the option there either. 

I tried searching the archives but couldn't find any similar threads. Thanks for any help.

---

### Post by alphacrucis2 on 2013-03-28
Did you look under Advanced Otions?

---

### Post by jimafternoon on 2013-03-28
Yes. IIRC, it said something like this:

Ubuntu
Ubuntu [something, something] recovery 
Ubuntu
Ubuntu [something, something] recovery

Each entry had a slightly different number in the [something something] area.

---

### Post by alphacrucis2 on 2013-03-28
In your /etc/grub.d folder, is there a file called 20_memtest86+

The files in /etc/grub.d are used to generate the grub2 config file

---

### Post by jimafternoon on 2013-03-28
That file is named '20_memtest86+.save' in my folder. I'm uploading a screenshot now of the grub.d contents

[IMG]http://i.imgur.com/NnzYW4P.png[/IMG]

---

### Post by alphacrucis2 on 2013-03-28
So when update_grub runs it wont get included in the menu I guess. Take a look at this:

[http://askubuntu.com/questions/126160/how-can-i-add-the-memtest86-options-back-to-the-grub-menu](http://askubuntu.com/questions/126160/how-can-i-add-the-memtest86-options-back-to-the-grub-menu)

---

### Post by jimafternoon on 2013-03-28
Ok, looks like that fixed it, thanks!

---

