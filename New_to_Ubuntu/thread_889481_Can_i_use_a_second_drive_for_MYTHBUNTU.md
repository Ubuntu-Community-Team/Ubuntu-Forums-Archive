---
title: "Can i use a second drive for MYTHBUNTU"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Peterfc on 2008-08-14
HI All

I have a 200gb drive set as 114.9 for Windows. 22.5 gb for Ubuntu and 19.6 gb for ubuntu. As i am only learning about Ubuntu i do not wish to change while all is running perfect.

Can i add a second drive for Mythbuntu the drive would be 80gb. If it can be done how would i boot from the second drive

The purpose of this machine is to learn what i am doing and then build a Mythbuntu system for home.

Thanks for taking the time to read this post

Dell Dimension 2400series 200gb drive 1gb ram dvd rw

---

### Post by oliviacond on 2008-08-18
yes, u can by configure the grub.
1st install the Mythbuntu on the 80gb (be sure u really select the 80gb drive, if not u may end up erasing 200gb)
don't restart after u install it, using the live cd, open the terminal,
```

sudo gedit

```
from the text editor, click 'Open' and go to the partition where your original ubuntu is installed, from that partition, open /boot/grub/menu.lst
add this to the last line:
```

title		Mythbuntu
root		(hd1,0)
chainloader	+1

```

after u restart, u should be able to boot Mythbuntu from the grub.
lastly, be sure the 200gb drive is your primary drive in BIOS

---

