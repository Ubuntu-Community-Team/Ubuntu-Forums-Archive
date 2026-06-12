---
title: "computer screwed up, &quot;dd&quot; command related?"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by mschooler93 on 2011-12-29
I screwed up my computer badly.

For whatever reason, I chose to copy-paste something on the internet into a terminal (it said it would make my game work), and when it didn't work I used "sudo" (looking back, I realize how stupid It was) About 5 minutes later, my browser stopped working, so I restarted and it wouldn't even turn on.

I don't remember exactly what it was, but I remember some part

```
dd if=/dev/sda
```

And, looking that up I found something that I think it was 

```
dd if=/dev/zero of =/dev/sda
```

I don't know what any of that means, but the site I found that on said it "zeroes out the disk partition"

Is there any way to fix this? I can run it on a livecd, but I want to know if there is any way to recover some of my files (mainly the ones in home, don't have much else on the computer)

When I turn it on, it only goes just past the bios screen (it says lenovo) and then completely blank screen.

The livecd is slow as heck, but I can re-install the OS no problem (i think) but I want to get back my home folder

Also, all of my music, movies, etc. are on a external hard drive and they're safe. 

I appreciate any help.
Ubuntu 10.04 LTS

---

### Post by 2F4U on 2011-12-29
It seems as if you have overwritten the content of your hdd (/dev/sda is your first hard disk) with zeroes. Depending on how long it run, this has killed more or less everything on the hdd. There are special programs to recover deleted or overwritten files

[http://lifehacker.com/393084/how-to-recover-deleted-files-with-free-software](http://lifehacker.com/393084/how-to-recover-deleted-files-with-free-software)

or you could get the help of a professional service.

---

### Post by mschooler93 on 2011-12-29
Well,  I got some things back with that.  However,  it says there is no OS installed on my computer.  So now I have to reinstall ubuntu from a painfully slow cd.  I have now learned to never trust the Internet (except for here.)

---

### Post by 2F4U on 2011-12-29
The command killed the boot loader and at least part of the root partition and therefore the BIOS has nothing to boot from. I would not recommend that you try to recover the OS but instead do a clean installation.
Yes, its true, never trust the internet and be especially careful when you do something with as root. Try to double check any suggestion and find out as much as you can about the commands used. If in doubt, try it on a test machine (for example, in a virtual machine) or don't use the command.

---

