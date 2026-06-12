---
title: "dual boot"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by jerryheavyarms on 2008-07-04
hello!

Ive recently installed windows 2000 on a pc that i used ubuntu studio with but on a seperate harddisk. When i want to use windows 2000, I&#314;l disconnect the ubuntu harddisk. And the same thing when i want to use ubuntu. What I want to do is to make a boot loader that will ask me if i want to boot from windows or ubuntu. Is it possible? 

Thanks in advance!

---

### Post by ZabiGG on 2008-07-04
Hi, you can read up on this subject and follow user-friendly howtos here:

[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)
 

Hope this helps,

Z.

---

### Post by 505 on 2008-07-04
Yes it is possible. You need to have Grub installed on the Linux hard disk and set this hard disk as the primary, so that your system boot from that drive by default.

Then you can add Windows 2000 to the /boot/grub/menu.lst file so you can select it. Only Windows likes to be on the first hard drive, so you need an extra command to 'virtually' make the second disk the first. The complete code will look like this:
```

title		Windows 2000
map 		(hd0) (hd1)
map 		(hd1) (hd0)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
I'm not 100% sure about the root line, could also be "root (hd1,0)".

---

### Post by jerryheavyarms on 2008-07-04
Thanks 505 and ZabiGG.. Ill try those...

---

