---
title: "I blew up my HAL"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by wicook on 2008-09-10
I was running Hardy just fine after the new HAL was released. My Toshiba U300 has an Atheros 5700 wireless and I couldn't get it to work for more than one Ubuntu update. The release a couple of weeks ago apparently incorporated the new HAL and everything was working very well. Then I ran an update that was available about a week or so ago and lost my wireless. I tried a variety of fixes, to no avail. To make a long story short, I ended up deleting HAL so I could reinstall it. BIG mistake. 

Now I can get to the username and password screens, but no further. It hangs when I hit enter after entering my password. I can't figure out how to boot from the CD to reinstall Hardy. Every time I boot up from the CD, the installed multiboot menu takes over and forces me to boot either Ubuntu or Win Vista from the hard drive. Vista works ok, but I can't get into Ubuntu.

Thanks in advance for your help.

Bill

---

### Post by redactech on 2008-09-10
Have you try to boot with the recovery console in ubuntu (it's in the grub option)

For the rest I'm not sure which package you deleted and need to be re-installed

---

### Post by wicook on 2008-09-10
No, I haven't tried that. Thanks for the tip.

---

### Post by Locutus_of_Borg on 2008-09-10
Just what do you think you're doing, Dave?

---

### Post by wicook on 2008-09-12
OK...I tried doing the restore/repair option from the boot menu. No luck. :( The restore function goes through its hoops, then tells me that it needs to download a file. I tried doing it with my wireless card turned on...nothing. I plugged it in to my ethernet box...nothing again. I have searched for ways to get around grub, but so far I haven't found a solution. I'm about to do an fdisk, system restore, and start over...

---

