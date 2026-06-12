---
title: "Can I ferry programs using a flash drive to a computer with no internet?"
date: 2014-11-30
forum: New to Ubuntu
---

### Post by William_Yingst on 2014-11-30
My brand spankin new Linux machine (Lubuntu 14.04.1) has no internet access at the moment. Is it possible to download Linux programs on my Windows machine, put them on a flash drive, and take the drive to my Linux machine? Would this work?

---

### Post by Mark Phelps on 2014-11-30
It can work, but it can be a lot of work to do it that way.  Why? Because, unlike with downloads of MS Windows apps, Linux apps don't package everything needed with the app; instead, they package only the app itself.

Apps generally need other middleware to work, most often, libraries.

When you install on a Linux machine, using the Software Center, it goes to the Internet to grab any missing "dependencies" -- and downloads them as well.  

When you install using the package manager (utilizing .deb files), once again, Internet access is used to obtain any missing "dependencies".

When you install from source files, generally contained inside compressed archives, yet again, the Internet is used ...

Problem you're going to run into is when you copy the download to the Linux box and try to install it, you're going to get stopped by the first "unmet dependency".  And then, you're going to have to go back to the Windows box to download that.  You'll have to keep doing this over and over until all the dependencies have been identified and downloaded.  It could be a handful, or it could be dozens -- depends on the app you're trying to install.

Linux distros have been designed to rely on Internet access; installing stuff in a offline mode is a lot of manual work.

---

### Post by oldfred on 2014-11-30
I do not know if this still is current or not?
[http://www.debian-administration.org/article/648/Offline_Package_Management_for_APT](http://www.debian-administration.org/article/648/Offline_Package_Management_for_APT)

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by tea for one on 2014-11-30
> **William_Yingst said:**
> My brand spankin new Linux machine (Lubuntu 14.04.1) has no internet access at the moment. Is it possible to download Linux programs on my Windows machine, put them on a flash drive, and take the drive to my Linux machine? Would this work?

Yes, it is possible.

I've used these instructions prepared by an Ubuntu user:-

[https://cortman.wordpress.com/2012/07/08/download-packages-with-windows/](https://cortman.wordpress.com/2012/07/08/download-packages-with-windows/)

Hopefully, it will provide you with a solution.

---

### Post by jp32 on 2014-12-09
It looks like Synaptic isn't installed in 14.04 by default.  Are there directions somewhere for installing that on a computer without Internet access?

---

### Post by deadflowr on 2014-12-09
> **jp32 said:**
> It looks like Synaptic isn't installed in 14.04 by default.  Are there directions somewhere for installing that on a computer without Internet access?

[s]Forgive me, but what would be the point?[/s]
Nevermind, I kind of see a point.

But anyway, you would need to make sure you have all the needed dependencies installed/satisfied, and then you can install it by downloading it from the ubuntu packages
[http://packages.ubuntu.com/trusty/synaptic](http://packages.ubuntu.com/trusty/synaptic)

you would then use dpkg to install, like so

```
cd Downloads
sudo dpkg -i <name-of-package.deb>
```
replace name-of-package for the package name, in this case synaptic.
The first entry would move you into the Downloads folder so you would only need to type the packages full name, and not have to add the full path to the package in the dpkg command. Quick hint is to use tab completion when filling the name of the package (you start typing the name of the package and hit the tab button, and it will autofill the rest, accurately)

But of course befor you install synpatic, you need to install the packages listed on the package link that have a red dot next to it. That means synaptic will not install until those packages are installed first.
Seems tedious to me, but that's one way to do it.

---

### Post by jp32 on 2014-12-11
Exactly what I needed.  Thank you so much!

---

### Post by Mark Phelps on 2014-12-11
You need to know that each one of the 14 or so packages listed also has its own dependencies -- which you won't know unless you open each package link and look for its dependencies.

It's a very tedious job to install new stuff offline.  What takes a few minutes online can easily take hours offline.

---

### Post by sudodus on 2014-12-11
There is another alternative, if your new computer works without proprietary drivers, that is, with the free drivers, that come with linux. Typical hardware that might need proprietary drivers are graphics chips/cards and wifi chips/cards.

Use another computer, which has access to the internet. Install the system into an external drive, for example a USB pendrive. Such a pendrive is portable (as long as you avoid proprietary drivers). So simply shutdown that other computer, plug the pendrive into your new computer, and boot from it. Test that it works (at least well enough so that you can tweak it.)

With three drives you can clone that system.

Boot from another pendrive, for example a Clonezilla pendrive. Clone from the pendrive with the installed system to the internal drive of your new computer.

---

