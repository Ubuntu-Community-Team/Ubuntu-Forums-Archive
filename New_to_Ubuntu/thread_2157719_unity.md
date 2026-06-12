---
title: "unity"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by ub9876 on 2013-06-26
I run gnome but reinstalled the left side icons in unity. But I dont like them so I want to go back. to just gnome. Actually what I would like to do by terminal hopefully is get the absolute bare bones light desktop environment....the lightest and fastest....Dont need half the bling of unity.And I dont mean have hidden stuff running in the background but get rid of everything that isnt part of my desktop.
what should I do..???

---

### Post by jcer93705 on 2013-06-26
> **ub9876 said:**
> I run gnome but reinstalled the left side icons in unity. But I dont like them so I want to go back. to just gnome. Actually what I would like to do by terminal hopefully is get the absolute bare bones light desktop environment....the lightest and fastest....Dont need half the bling of unity.And I dont mean have hidden stuff running in the background but get rid of everything that isnt part of my desktop.
what should I do..???

Go for Xubuntu and be done with it. Or back to older version of Ubuntu like 10.10 if ur computer is a bit older. I think Xubuntu is a great replacement for old style Gnome. Very easy to navigate.

---

### Post by TNFrank on 2013-06-26
From what I understand Gnome 3 is the Unity version and Gnome 2 was the older version. Having never used the Gnome 2 version but having come over from Mac OS X the Gnome 3 Unity version is fairly intuitive to me and reminds me of OS X quite a bit.  I did see a program you can install, forget if it was on TeckZilla or HAK5 where you can make your Gnome 3 Unity look like the older Gnome 2 version. You might do a search for it to see if you can come up with it. Good luck.

---

### Post by jcer93705 on 2013-06-26
> **TNFrank said:**
> From what I understand Gnome 3 is the Unity version and Gnome 2 was the older version. Having never used the Gnome 2 version but having come over from Mac OS X the Gnome 3 Unity version is fairly intuitive to me and reminds me of OS X quite a bit.  I did see a program you can install, forget if it was on TeckZilla or HAK5 where you can make your Gnome 3 Unity look like the older Gnome 2 version. You might do a search for it to see if you can come up with it. Good luck.

Problem is he doesn't want to adopt the new Unity because of needing to learn all over again. Old gnome is easier to navigate in fact easier then kde. But Xubuntu i found that it's so easy to navigate and tweak if needed. Xubuntu is great out of the box. I do love the new latest Kubuntu with KDE. Also Unity is sloooower then kde or other interface. I think for Gnome replacement is Xubuntu after that KDE but KDE is not easy as old gnome.

---

### Post by 2Stoned on 2013-06-26
> **jcer93705 said:**
> Or back to older version of Ubuntu like 10.10 if ur computer is a bit older.

You can run Ubuntu 12.04 LTS with the mate desktop environment wich is very lightweight. I have tested it on several older machines, so no need for outdated distro's. Xubuntu and Lubuntu are good as well.

---

### Post by HermanAB on 2013-06-26
Install XFCE, log out and log in again:
[http://www.aeronetworks.ca/2013/05/virtualbox-ubuntu.html](http://www.aeronetworks.ca/2013/05/virtualbox-ubuntu.html)

---

### Post by newb85 on 2013-06-26
Gnome 3 and Unity are two different desktop environments.   10.04 is no longer supported. Neither is Gnome 2, although Mate is essentially the same and is supported. It's not in the repos, but it can be installed from a PPA instructions van be found by searching at [www.webupd8.net](www.webupd8.net)

---

### Post by wildmanne39 on 2013-06-26
Hi, if you want less blout as you stated you could intall the minimal version of ubuntu but I do not recommend removing packages you will end up breaking ubuntu most likely doing it that way.
Thanks

---

### Post by 2Stoned on 2013-06-27
To install MATE on Ubuntu mini 12.04 Precise:
```
sudo apt-get install python-software-properties
sudo add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu precise main"
sudo add-apt-repository "deb http://repo.mate-desktop.org/ubuntu precise main"
sudo add-apt-repository "deb http://mirror1.mate-desktop.org/ubuntu precise main"
```

```
sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get install mate-desktop-environment  **(or)**  sudo apt-get install mate-desktop-environment-extra
sudo apt-get install caja-gksu caja-sendto mate-bluetooth mate-indicator-applet mate-media-gstreamer mate-text-editor caja-share mate-notification-deamon
```

If you like you could Install the MDM login Greeter + themes by LinuxMint (DM)
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install mdm mint-mdm-themes
```

This should work.

---

