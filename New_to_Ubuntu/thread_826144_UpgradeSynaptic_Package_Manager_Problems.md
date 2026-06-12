---
title: "Upgrade/Synaptic Package Manager Problems"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Techpenguin on 2008-06-11
Hi Everyone, I am running 6.10 ubuntu and was trying to upgrade to 8.04 but, first of all, my update manager only displays 7.04 as an update, and when I try to do that it says that, "Authenticating the upgrade failed. There may be a problem with the network or with the server." what should  I do? also, I can't update the applications on my synaptic package manager because, "The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences." now, I know my internet is working fine, I'm typing this on that computer. Are these problems related in any way, and how do I fix them?

---

### Post by RequinB4 on 2008-06-11
If you're sure everything else is fine, it might be the server's problem.  In system - admin - software sources, change from FOOBAR server (where foobar is your country) to the Main server.

---

### Post by forestpixie on 2008-06-11
Also I believe if you want go the upgrade route from 6.10 , you have to do 7.04,7.10,8.04 as there isn't an upgrade route from 6.10 to 8.04.

I would seriously think about doing a clean install, apart from the downloads - you have to hope you can upgrade each time without problems.

---

### Post by Oldsoldier2003 on 2008-06-11
> **Techpenguin said:**
> Hi Everyone, I am running 6.10 ubuntu and was trying to upgrade to 8.04 but, first of all, my update manager only displays 7.04 as an update, and when I try to do that it says that, "Authenticating the upgrade failed. There may be a problem with the network or with the server." what should  I do? also, I can't update the applications on my synaptic package manager because, "The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences." now, I know my internet is working fine, I'm typing this on that computer. Are these problems related in any way, and how do I fix them?

6.10's upgrade path is 6.10>7.04>7.10>8.04

it would be easier and less problematic to just download the alternate cd install iso and run the upgrade by inserting it in your cd rom drive. its not actually supported officially but if it doesn't work you can do a clean install.

---

### Post by cdtech on 2008-06-11
I upgraded from 6.10 to 8.04 using the command line. I changed my sources.list to this:
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main universe multiverse restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse

```

Then I typed in a terminal:
```
sudo apt-get dist-upgrade
```

After everything was downloaded and installed I did (to be sure everything configured properly):
```
sudo dpkg &#8211;configure -a
```

After that I checked my System > Admin > Software Sources to be sure I had no old links. After I rebooted, I did another update cleaned out the Synaptic package manager; status > not installed (residual config).

Worked for me......

P.S.
Be sure to setup your GRUB menu.lst and add your new kernel to the list before reboot.

---

### Post by Oldsoldier2003 on 2008-06-11
> **cdtech said:**
> I upgraded from 6.10 to 8.04 using the command line. I changed my sources.list to this:
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main universe multiverse restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse

```

Then I typed in a terminal:
```
sudo apt-get dist-upgrade
```

After everything was downloaded and installed I did (to be sure everything configured properly):
```
sudo dpkg –configure -a
```

After that I checked my System > Admin > Software Sources to be sure I had no old links. After I rebooted, I did another update cleaned out the Synaptic package manager; status > not installed (residual config).

Worked for me......

direct upgrade from 6.10>8.04 is not supported but I'm glad to see it worked for you. you lucked out :)

---

### Post by cdtech on 2008-06-11
> **Oldsoldier2003 said:**
> 6.10's upgrade path is 6.10>7.04>7.10>8.04

it would be easier and less problematic to just download the alternate cd install iso and run the upgrade by inserting it in your cd rom drive.

I had a ton of programs that I did not want to reinstall. By upgrading you wont loose anything you have installed (it's all upgraded).

---

