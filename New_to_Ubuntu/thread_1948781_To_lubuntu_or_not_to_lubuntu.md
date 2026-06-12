---
title: "To lubuntu or not to lubuntu?"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by Foobarz on 2012-03-28
Ok, so I was wondering if a PC with an Intel Celeron M processor, and 512 MB RAM with Accelerated Graphics should use Lubuntu 11.04? Will there be a significant improvement in speed? (Cause if not, I might just switch the Ubuntu 11.04 WM from Metacity to Openbox)

BTW, Lubuntu comes with apps such as Abiword and Gnumeric? If I uninstall these after installing lubuntu (since I like Libreoffice better) will the metapackage be removed and affect my receiving security updates?

---

### Post by motoroller on 2012-03-28
> **Foobarz said:**
> Ok, so I was wondering if a PC with an Intel Celeron M processor, and 512 MB RAM with Accelerated Graphics should use Lubuntu 11.04? Will there be a significant improvement in speed? (Cause if not, I might just switch the Ubuntu 11.04 WM from Metacity to Openbox)

BTW, Lubuntu comes with apps such as Abiword and Gnumeric? If I uninstall these after installing lubuntu (since I like Libreoffice better) will the metapackage be removed and affect my receiving security updates?

I installed Ubuntu 11.10 then later Lubuntu on an old laptop, and the speed difference was noticeable. This machine had 256MB memory, a 20Gb HDD, and an Intel celeron processor. Lubuntu ran and did things much faster, with less drain on system resources. Unfortunately it would seem that some of the features that make Ubuntu easier to use and friendlier can also tax an old system's resources. 

Lubuntu comes with the office software suite that is the counterpart to Libre Office. It also comes with a pretty good assortment of other general apps, but you can always add more through the synaptic package manager. It's all laid out in a neat, tidy manner and programs are pretty easy to find in the menus. Overall I think it's a fine choice for an older machine.

---

### Post by cortman on 2012-03-28
> **Foobarz said:**
> Ok, so I was wondering if a PC with an Intel Celeron M processor, and 512 MB RAM with Accelerated Graphics should use Lubuntu 11.04? Will there be a significant improvement in speed? (Cause if not, I might just switch the Ubuntu 11.04 WM from Metacity to Openbox)

BTW, Lubuntu comes with apps such as Abiword and Gnumeric? If I uninstall these after installing lubuntu (since I like Libreoffice better) will the metapackage be removed and affect my receiving security updates?

Lubuntu is MADE for that spec of system. Give it a try.
If you feel a little adventurous, I'm having a lot of fun with [Crunchbang]("http://crunchbang.org/"), which is even more lightweight. Based on Debian stable.

---

### Post by Rodney9 on 2012-03-28
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Foobarz on 2012-03-29
Wait if I already set up my printer in GNOME 2 do I have to set it up again in LXDE?

---

### Post by flurospar on 2012-03-29
> **Foobarz said:**
> Wait if I already set up my printer in GNOME 2 do I have to set it up again in LXDE?

For an existing install of GNOME on Ubuntu on top of which you want to install LXDE, no reconfiguration is required.

For a fresh Lubuntu install you will have to configure your printer again (but many printers are supported by default nowadays.)

[QUOTE=Foobarz]If I uninstall these after installing lubuntu (since I like Libreoffice  better) will the metapackage be removed and affect my receiving security  updates?[/QUOTE]

Try removing these. Even if the metapackage is removed, it wont stop the flow of security updates.

---

### Post by mastablasta on 2012-03-29
you can install Lubuntu desktop, then on login you choose it and log in. then, you remove gnome desktop.
 
you can install libre office. i don't think desktop matters. though it might pull in gnome dependency files on install.

---

### Post by I2k4 on 2012-03-29
I've been dual booting Lubuntu 10.10 contentedly on a netbook for a while.  After testing on Live USB, I found 10.10 noticeably faster than 11.10 - Ubuntu's move to more demanding 11.x reminds a bit of Windows move from XP to Vista - it really takes more guts to run it, LXDE or otherwise.

Be aware that Lubuntu is cruder.  Synaptic Package Manager is not as user friendly as Software Center, the File Manager lacks some features, and the panel clock has no GUI but needs ridiculous strings to configure it - mine is %a %b %d, %l:%M%P

I've had no problems deleting unwanted or installing preferred programs using Synaptic.

---

### Post by Rex Bouwense on 2012-03-29
Not sure if you are aware of it but there is a Lubuntu Software Center in the repository.  It works quite well.  I installed the Ubuntu Software Center as well and it works well in Lubuntu also but now with the lubuntu Software Center there is no need for it.

---

### Post by I2k4 on 2012-03-29
> **Rex Bouwense said:**
> Not sure if you are aware of it but there is a Lubuntu Software Center in the repository.  It works quite well.  I installed the Ubuntu Software Center as well and it works well in Lubuntu also but now with the lubuntu Software Center there is no need for it.

Thanks, good to know.  I'm actually kind of proud of figuring out Synaptic, including adding some odd PPAs that I wouldn't know how to get into a software center.

---

### Post by Foobarz on 2012-03-30
Oh yes if I ever wanted to uninstall lubuntu what would be the command, since installing is easy by just installing metapackage: 

sudo apt-get install lubuntu-desktop

But how would I go about uninstalling?

---

### Post by jerome1232 on 2012-03-30
> **Foobarz said:**
> Oh yes if I ever wanted to uninstall lubuntu what would be the command, since installing is easy by just installing metapackage: 

sudo apt-get install lubuntu-desktop

But how would I go about uninstalling?

It involves jumping 10 hurdles with your hands tied, I really do wish it was easier to remove things in this situation.

Here's a guide to do it, a note of warning, I tried this on my netbook trying to go to pure lubuntu, and it borked my system, I was happy to reinstall anyways since it was a fresh install. But be warned.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

