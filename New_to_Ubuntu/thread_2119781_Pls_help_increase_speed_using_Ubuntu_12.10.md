---
title: "Pls help increase speed using Ubuntu 12.10"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by sge454 on 2013-02-24
I have just installed ubuntu 12.10 (32-bit version) on my old Toshiba Satellite (496.3 MiB, Intel Pentium 4 CPU 2.40GHz processor, NV17 graphics card, 58.5 GB HD).  Although this is an older system, it ran Windows XP smoothly and fairly quickly especially compared to ubuntu.  I had installed Knoppix 6.5 just prior to ubuntu.  Knoppix installed easily without any issues and ran at a good pace.  After installing ubuntu, the speed of opening applications or folders takes a few minutes to complete.  Is there anything I can do to increase the speed of this OS?  Although I'm new to the linux world, I'm testing out these OSs to see which I would like to install on a netbook for future international travel so any assistance anyone can provide would be very helpful.  Thanks!

---

### Post by Pilot6 on 2013-02-24
Install a proprietary video driver.
And also install xubuntu-desktop. It may help. The hardware is too weak to run standard Ubuntu.

---

### Post by tartalo on 2013-02-24
Your graphic card is not properly supported in Unity, Gnome 3 or Cinnamon. EDIT: I misread a bug report, it might be supported, anyway I stand in my recommendation for a light desktop environment given the rest of specs.

With those specs your best bet inside the _buntu world would be Lubuntu, which uses LXDE:
[http://lubuntu.net/](http://lubuntu.net/)

But Xubuntu (XFCE) might also work well:
[http://xubuntu.org/](http://xubuntu.org/)

Unity, Gnome 3, Cinnamon, XFCE and LXDE are [Desktop Environments](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available). Another Desktop Environment that can be installed very easily in Ubuntu is KDE, and it supports your graphic card, but in your case I don't recommend it because of the amount of RAM you have.

There are more but they are probably not well suited for newcomers to Linux.

---

### Post by kabukiM0n0 on 2013-02-24
If you are looking for netbook distros, have a look in other OS/distro talk. There is a thread I created with great information about lightweight distros. 

If Ubuntu is too heavy to run on your system, try Xbuntu or Lubuntu.

---

### Post by ptn107 on 2013-02-24
I would have recommended [_Lubuntu_]("http://lubuntu.net/") to start with, but if you already have Ubuntu install you can easily add Lubuntu and remove the stock gnome Ubuntu stuff later.  This should do it:

```
sudo apt-get install lubuntu-desktop plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text
```

---

