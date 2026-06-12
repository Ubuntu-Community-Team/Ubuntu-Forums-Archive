---
title: "problem with 11.10"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by pantea on 2012-05-21
I am a user of CERN root and some other physics programs, i used to use them on Ubuntu 9.01. newly as i had problem with supporting new programs i changed to 11.10 but using it is really a big trouble for me!
i activated root account like before it is essential for me because each time i run a program or compile something must change ownerships one by one if i do not login as root, but in 11.10 when i login i always seems as guest!
thew worse is that i can not bring back the old menu bars on the top of page when i have logged in as root (which is now named guest!) and the accesses to programs not easy as before .... did everyone knows that the same problems are in the newer version 12.04 or not? 
it seems that i must give up using 11.10 because it is not an easy to use for root users.

---

### Post by mlentink on 2012-05-21
Hi pantea,

You are of course aware that using the root account comes with security issues, which is why the root account has been disabled by default in Ubuntu? This has been the case since I tried Warty and started using Dapper. Please see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

As far as the menu bars are concerned, you might want to read this sticky thread: [http://ubuntuforums.org/showthread.php?t=1859960](http://ubuntuforums.org/showthread.php?t=1859960)
Going to 12.04 will not help you much in this regard.

---

### Post by xedi on 2012-05-21
> **pantea said:**
> 
i activated root account like before it is essential for me because each time i run a program or compile something must change ownerships one by one if i do not login as root, but in 11.10 when i login i always seems as guest!

I'm not exactly sure what you mean so this advice might be not very helpful but can't you just start the program, compiler, whatever with sudo? This should give the program full power concerning changing ownerships, e.g. it is possible to start the file manager (nautilus) in sudo if you want to mess around with ownerships.

> 
thew worse is that i can not bring back the old menu bars on the top of page when i have logged in as root (which is now named guest!) and the accesses to programs not easy as before .... did everyone knows that the same problems are in the newer version 12.04 or not? 
it seems that i must give up using 11.10 because it is not an easy to use for root users.

There are two ways to access programs in Unity, which are both faster and easier than with menus in my opinion.

1. Open the dash and search for it (by typing the name or description or something associated with the program). You can open the dash by clicking on the Ubuntu symbol or by pushing the windows/super key.

2. Put the program in the launcher on the left side and then you can just click on it. You can do that by starting the program, right clicking on the icon of the program in the launcher and click on lock.

This is the same for 12.04 so upgrading won't help in those regards.

If this is not satisfying, as mlentik has suggested you could install gnome classic which looks like the old Ubuntus. Alternatively you could install another dekstop environment which is more menu driven, such as XFCE, LXDE or KDE, which you can download and install in the software center.

---

### Post by pantea on 2012-05-21
Thank you for your replay.
in fact i have used root login for a long time and know the problems and even many times from the start i reinstalled all my programs+Ubuntu. but as i told when using other codes like as CORSIKA or CERN ROOT, .... many others, it is not possible to use "sudo" because each time I must change the ownerships many many times and it should be repeated for each compilation of those programs.
I have seen all that threads, it does not work for root login and just changes the administrator account who has first installed the program. 
where should i use alt+right click? in login menu?

---

### Post by mlentink on 2012-05-21
Hi Pantea,

I do not want to promote the use of root accounts in Ubuntu. If you read the 'RootSudo' link in my earlier post carefully, it will explain how you can change things to your liking.

As regards to the second one, as stated earlier, if you do not wish to switch to the classic gnome, you could always install e.g. the Xubuntu desktop environment, which gives you a panel with a menu.
AFAIK:
```
sudo apt-get install xubuntu-desktop
```
then log out and at log in choose the xubuntu DE.

Hope this helps

---

### Post by pantea on 2012-07-30
I did your suggestion many times but after choosing the Xubuntu it seems that it is not capable to start it and again the same menus apear

---

