---
title: "installation problems/335 updates ran out of space"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by arranskye on 2013-06-21
Hi, I ran lubuntu for a couple of days then decided to install.   Everything appeared to go ok. Then an update request appeared. 335  updates need to be installed.  Considered installing in block of 50 or  so but new to linux and was concerned about omitting dependancies.   About 90% of the updates downloaded then stopped. Looked like it had ran  out of space.

I had used the auto install on an 85GB partition but this procedure  allocated only 1.75GB swap partition. I thought that the swap should be  twice the ram in this case 4GB???

My laptop is a compaq. C60 notebook. 2GHz CPU   2GB ram   160HDD running vista on sda1

Sda1 vista  70GB    Sda2 extended  80GB  Sda6 ext4 (lubuntu) 78GB   Sda5 swap 1.75gb

While watching the updates there appeared to be a lot of "replacement" stuff. I tried *sudo apt-get clean*  to try to get additional space but nothing happened.  Used knoppix to  try to increase the size of the swap partition but could reduce the size  but not increase it.

Pop up again: Upgrade manager wants to run partial update: starts: gets to the same place with the same error : [I]glibc  detected lockfile create free invalid next size (fast) 0                glibc detected lockfile -create malloc memory corruption fast 0x09119048
[/I]
Another message: *Software index is broken.  it is impossible to install or remove any software Use synaptic or run sudo 'apt-get install* *-f' to fix this issue.*  Ran it and got output * dpkg was interrupted you must manually run 'dpkg --configure -a' to correct. *ran it got command not found.

wireless pci card & wifi usb not working. Hoped the updates &  restricted extras would help. Usb wifi works on Ubuntu on my desktop and  as soon as I boot into vista it starts working.  I have tried about 5/6  distro's live & installed but cannot get the wireless card or usb  to work.
Can this be fixed please??  Do I need to re-install manually to increase  the swap size??  Are the problems being caused by the small size of the  swap partition??

Thanks

---

### Post by marinara on 2013-06-21
if you keep having problems run "system stability tester" from .tar.gz and monitor your hardware temperatures.  to be honest, i donno why you are having literally 3-4 different SERIOUS problems.

---

### Post by arranskye on 2013-06-22
Thanks.  Quite relieved to find it was not my incompetence, because you are absolutley right, overheating graphic card or CPU.
the laptop was given to me. Its about 6/7 years old and not worth fixing so next step a new laptop.

Is there anything i should avoid or does Linux cope with most "middle of the road"   Never managed to get a wireless connection on that laptop so I would like to ensure that a new one will have a more compatible wireless card, although the high temperatures inside the laptop may well have made life difficult for many of the components.

Also when I install on a new laptop how do I ensure that the auto install creates an 8 GB swap partition. (twice 4GB ram) 

thanks again

---

### Post by Impavidus on 2013-06-22
Just clearing the dust out of the laptop may stop the overheating problem. Maybe you can try it before buying a new one.

The advice that swap must be twice RAM is outdated. With modern amounts of RAM you don't need that much, because you rarely run out of RAM. If you want to hibernate, make swap slightly larger than RAM, else, well, in principle you could do without, depending on how much memory intensive stuff you want to do. Of course compare to the amount of disk space available. You can always partition manually to get the right partition sizes. The automatic choices aren't always very good, although they work. On my laptop the swap was automatically made way too large, but as it's still less than 3% of my disk space I keep it like that until I reinstall. Often it doesn't really matter.

There are some general guidelines about what kind of hardware generally works and what doesn't. For wifi Atheros usually works (I have one), Broadcom is often problematic. I don't know about others. For graphics Intel just works, but isn't really high performance, nvidia and ATI require some work to get them running, but once everything is installed it's fine, although ATI is somewhat less reliable when it concerns making drivers available. On the other hand, I hear they're cheaper. I would avoid other manufacturers. Hybrid systems with multiple video cards are difficult too, I heard.

When you have something specific in mind you should be able to find out whether others have had success making the hardware work with Ubuntu.

---

### Post by marinara on 2013-06-22
everyday people who know better buy new laptops that don't work with ubuntu. so you should do your homework.

---

