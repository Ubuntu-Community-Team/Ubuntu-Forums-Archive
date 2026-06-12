---
title: "swap hard drive with ubuntu to new computer"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by flyingsolo on 2012-01-20
I'm wondering if I can take a Sata hard drive with Ubuntu installed on it and put it into a different computer and have it recognized as is.  Essentially, I wish to move the installed ubuntu from an old computer to a new one; old one is two drives with XP on one and ubuntu on the other in dual boot but I'd like to move the ubuntu hard drive to a new computer which has Win 7 home premium on its one hard drive. In the end, I wish to have dual boot on the new computer and am looking for the easiest way to achieve it without wiping drives, reinstalling etc.
Is this possible to do?
Advice please & thanks.

---

### Post by pierreyy on 2012-01-20
hello 
i found this thread on geek.com

>  [http://www.geek.com/forums/topic/can-i-swap-my-hard-drive-with-operating-system-to-another-motherboard](http://www.geek.com/forums/topic/can-i-swap-my-hard-drive-with-operating-system-to-another-motherboard)  

its for windows but from what i read i dont think there should be a problem, either way dont forget to backup and have a live medium incase you have to fix your system or the grub menu.

---

### Post by QIII on 2012-01-20
Back up, uninstall your video driver (and perhaps other special hardware drivers), move your drive, set your Ubuntu drive to boot first in your BIOS, run 

```
sudo update-grub
```

and install the appropriate video driver

---

