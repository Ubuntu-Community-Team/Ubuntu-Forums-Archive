---
title: "Howto install Call Off Duty 1 on ubuntu 9.04"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by Hankbonk on 2013-10-13
How can I download and run the first version of COD on my Jaunty ubuntu 9.04 ?

---

### Post by MrMichaelHill on 2013-10-13
Buy a copy of COD1 first, then check out WINE :)

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1346](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1346)

---

### Post by Hankbonk on 2013-10-13
Dear MrMichaelHill,

I'm running Ubuntu version 9.04 Jaunty, which doesn't include the Ubuntu Software Center, which is mentioned when I click your link .

---

### Post by sanderj on 2013-10-13
> **Hankbonk said:**
> 
I'm running Ubuntu version 9.04 Jaunty, which doesn't include the Ubuntu Software Center

... and which is not supported anymore since October 2010.

---

### Post by david98 on 2013-10-13
I suggest a o.s upgrade is there a reason why your using a outdated operating software which you get no update's. I recommend you upgrading to 12.04 lts which has updates until august 2017. If your using older hardware try lubuntu works with minimal resources like early xp system's. Is there any reason why you haven't updated since 2009 that's a long time in computer tech your system is certainly vulnerable as you have had no security update's since 2010 which is not recommended.

Always remember to back up your data

---

### Post by Hankbonk on 2013-10-27
Is there really no way to install COD 1 on an Ubuntu 9.04 ?  It must be the same generation, no ?

---

### Post by Impavidus on 2013-10-27
Try pointing your software sources to old releases, install wine and try to run it. It has platinum rating, so it should work once you have wine installed. (Edit: that would probably be with a recent version of wine, not the old one in the 9.04 repos. You may need a manual installation of wine and hope it works with your old libraries.)

No one here still uses 9.04, so I don't think you'll get much support here. After all, it's unsupported and insecure. You'll have to use your own skills.

---

### Post by asifnaz on 2013-10-27
9.04 is no more supported try a newer version

---

### Post by ikt on 2013-10-27
> **Hankbonk said:**
> Is there really no way to install COD 1 on an Ubuntu 9.04 ?  It must be the same generation, no ?

Gaming support has only just started to get going really well since 12.04, especially with steam coming to linux, even if COD1 and 9.04 were released around the same time, at the time COD1 would have been unplayable.

I highly recommend installing maybe Lubuntu or Xubuntu 13.10 and trying to run COD1 on it, so they would be better for it.

---

### Post by Hankbonk on 2013-10-28
Dear Impavidus,

Thanks for your interesting answer, which I think  says it IS possible to do so . But I'm just a rookie on linux/ubuntu .   Is it possible to give me a step by step guidance for this way of installing Wine ?

---

### Post by Hankbonk on 2013-10-28
Dear ikt,

thanks for your reply, sorry about this late reaction .

As I understand your reply, you state that COD1 will never be playable on my very old and unsupported Ubuntu 9.04 ?  So I just would have to load Lubuntu or Xubuntu 13.10 ?  But I'm a rookie on Ubuntu and the PC is not mine (from a good friend) and he pointed me out that upgrading an Ubuntu system is a whole lot of work, work that I don't know about .  Another poster on this thread, sir Impavidius, mentioned that I should install a newer version of wine and then it might work .  What are your thoughts on this ?

---

### Post by whatthefunk on 2013-10-28
You really need to upgrade.  Your system hasnt received security updates for three years and is vulnerable to attacks.  Its also very difficult to install new software since the repos arent being maintained anymore.  I would suggest upgrading to a new version befoe trying anything else.

---

### Post by whatthefunk on 2013-10-28
> **Hankbonk said:**
> Dear ikt,

thanks for your reply, sorry about this late reaction .

As I understand your reply, you state that COD1 will never be playable on my very old and unsupported Ubuntu 9.04 ?  So I just would have to load Lubuntu or Xubuntu 13.10 ?  But I'm a rookie on Ubuntu and the PC is not mine (from a good friend) and he pointed me out that upgrading an Ubuntu system is a whole lot of work, work that I don't know about .  Another poster on this thread, sir Impavidius, mentioned that I should install a newer version of wine a,d then it might work .  What are your thoughts on this ?

Installing a newer version of Wine would be very difficult for you because its not in the repos.  What kind of computer are you using?  What are the system specs?  Maybe we can help you choose a new OS:)

---

### Post by 3rdalbum on 2013-10-28
> **Hankbonk said:**
> But I'm a rookie on Ubuntu and the PC is not mine (from a good friend) and he pointed me out that upgrading an Ubuntu system is a whole lot of work, work that I don't know about.

Well, hang on a moment. Upgrading an Ubuntu system is not that difficult. You'd basically need to download a later Ubuntu, burn it to CD, boot from the CD and run the Installer program. At the partitioning screen you can simply click the "Upgrade" button and your system will be upgraded without you losing any data. It'll even update your current software.

Quite easy and there are HOWTO guides around the Internet. Most of it is stuff you could just work out by yourself. Nobody taught me how to do absolutely everything on the computer, I was taught the basics and then I had to figure the rest out myself. If I got stuck I could read the manual.

If you really really get stuck, you could get help from a local Linux User Group, or LUG. Or you might even be able to find someone on here from your area who could come around to your place and upgrade Ubuntu for the price of a bottle of wine or a six-pack.

> Another poster on this thread, sir Impavidius, mentioned that I should install a newer version of wine and then it might work .  What are your thoughts on this ?

Newer versions of programs usually depend on newer versions of libraries. Newer versions of libraries ship in newer Linux distributions. If you were merely trying to run the latest Wine on Ubuntu 12.04 you could probably do it with a couple of newer libraries, but not from a version of Ubuntu that is four and a half years old. That's too old, sorry, and very much an "advanced user" kind of thing to do. It's definitely easier to install a newer version of Ubuntu.

---

### Post by Impavidus on 2013-10-28
I wrote it *may* be possible to install a recent wine, but you'd have to do it manually *and* you may have to manually install the new libraries this new wine depends on. It's definitely more complicated than installing for example Lubuntu 13.10, which should run on your machine (512MB ram, if I remember correctly from a different thread). Lubuntu can probably be installed in about 30 minutes. Right now, your system is insecure and very hard to maintain.

I your case I wouldn't run the automatic upgrade but do a clean install, as you would be skipping 8 versions and change from Ubuntu to Lubuntu. It should be quite easy though. Try running a live disk of Lubuntu 13.10. If it works, make backups of your files and click "install". Wait for half an hour and you'll have a clean, easy to maintain and secure system.

---

### Post by Hankbonk on 2013-12-11
To all poster on this thread : Thanks all for your replies . And sorry for this late reply from me .

Since the owner ( a friend of mine ) doesn't want me to upgrade, I will let loose of my search for now, and mark this thread as closed .
Thanks to everybody for their replies !

---

