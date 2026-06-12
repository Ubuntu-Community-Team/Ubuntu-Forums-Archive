---
title: "Preparing for Hardy - Fedora 9 dual-boot??????"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-10-05
I actually did this once before and I swore I'd never do it again but my youngest son convinced me to do it for one of his friends.

The first time I used the full install DVD, installing Fedora on a machine with a working Ubuntu OS, and I used Fedora's grub.

This time I plan on using the Fedora Live CD and after installing I'll restore grub to Ubuntu and then add Fedora to the Ubuntu menu list.

Is there any reason this won't work?

I hope not because I find Ubuntu's menu list much easier to work with than Fedora's grub.conf file.

Any and all feedback appreciated:)

---

### Post by vamped on 2008-10-06
> **kansasnoob said:**
> 
I find Ubuntu's menu list much easier to work with than Fedora's grub.conf file.

I like Fedora's better.

> **kansasnoob said:**
> 
Is there any reason this won't work?


The only tricky thing is that both Ubuntu and Fedora change the kernel version from time to time, and with it their grub file. A nice trick so that you don't have to manually update the working grub file each time the other distro changes is to actually use both distributions' grub files.

I used Fedora's and chainloaded Ubuntu's. You'll want to do the opposite. Change the timeout of the one you're not using to 0.

```

default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
title Fedora (2.6.23.1-49.fc8)
	root (hd0,0)
	kernel /vmlinuz-2.6.23.1-49.fc8 ro root=/dev/Fedora/root rhgb quiet
	initrd /initrd-2.6.23.1-49.fc8.img
title Ubuntu
	rootnoverify (hd1,4)
	chainloader +1

```

---

### Post by kansasnoob on 2008-10-06
I decided to give this a try on a spare testing hard drive first that has Intrepid Beta on it!

That way if I hose things I can just start over from scratch with nothing lost but time.

---

### Post by louieb on 2008-10-06
> **vamped said:**
> ...I used Fedora's and chainloaded Ubuntu's. You'll want to do the opposite....
+1 for chainloading  

Also same result different method is the configfile option.

```

title use another menu.lst
configfile (hd0,1)/boot/grub/menu.lst
```more on both here [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by vamped on 2008-10-11
> **louieb said:**
> 

Also same result different method is the configfile option.



That's right! That's actually what I ended up doing, but I couldn't remember the command when I posted my first comment.

---

