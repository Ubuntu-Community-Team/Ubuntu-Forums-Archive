---
title: "GNOME (I think). How do I extend desktop?"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by Jonathan47 on 2013-02-11
I have a duel boot system with windows on the other partition. Extended desktop works there.
I assume I need a driver to extend the desktop in Ubuntu. How do I find out which, and where do I find it?

Also, on the monitor that is working, ubuntu does not fill the screen, there is a black border. How do I extend the window to fill the screen?

Thanks  :)

Jonathan

---

### Post by omeomi on 2013-02-11
Can you provide a little bit more information about the system your are using? Especially about the graphics card and Ubuntu version.

Did you install the drivers for your card? You can do this via 'Additional Drivers'.

---

### Post by Jibril00 on 2013-02-11
I use Unity. Should be the same as yours. If you go to the System Settings (gnome-control-center) under hardware you should see 'Displays', click on that and you should be able to choose your displays settings from there. Changing the Resolution should fix the black bars.

If I understood your question right.

---

### Post by Jonathan47 on 2013-02-12
Hi again and thanks. 

Ubuntu does not recognise my monitor, even though it works

omeomi:
My system is a 2 year old desktop
My Ubuntu version is 10.04 LTS
My graphics card is a gigabyte NVIDIA GEFORCE  GTS 450
No, I haven't installed drivers for it, I don't (think I) have any, for linux
When I searched for them, I got a message saying that there were no proprietary drivers on the system
Where do I find "additional drivers"?

Jibril00:
 I still have the black border on all resolutions that I have access to at the moment

Thanks.

PS How do I subscribe to this thread? If that is the correct terminology? How can I make it easy to find again anyway? :)

---

### Post by omeomi on 2013-02-12
> **Jonathan47 said:**
> PS How do I subscribe to this thread? If that is the correct terminology? How can I make it easy to find again anyway? :)

At the top of the thread there is a button 'Thread tools' click that and then click 'Subscribe' ;)

IIRC the Additional Drivers are located in the System Settings for your Ubuntu version (10.10 LTS). If you launch this it will automatically start searching for available drivers.

---

### Post by NikTh on 2013-02-12
Hi ,
please open a terminal (CTRL+ALT+T) and copy-paste from here the commands below one by one. (press ENTER after each command for results)
```
lsb_release -rcd ; uname -rm
echo $DESKTOP_SESSION
lspci -nnk | grep -iA2 vga
```

Post back here to a new answer the results.

_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by 3rdalbum on 2013-02-12
> **Jonathan47 said:**
> Hi again and thanks. 

Ubuntu does not recognise my monitor, even though it works

omeomi:
My system is a 2 year old desktop
My Ubuntu version is 10.04 LTS
My graphics card is a gigabyte NVIDIA GEFORCE  GTS 450
No, I haven't installed drivers for it, I don't (think I) have any, for linux
When I searched for them, I got a message saying that there were no proprietary drivers on the system

The GTS450 was released after Ubuntu 10.04, which is why it doesn't recognise it and it doesn't offer any additional drivers to you.

Ubuntu 10.04 is quite old now. If you upgrade it to 12.04 or 12.10 you'll be able to use the full features and performance of your card.

---

### Post by Jonathan47 on 2013-02-12
to Nikth:

theboss@Ubuntu-desktop:~$ lsb_release -rcd ; uname -rm
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
3.2.0-37-generic-pae i686
theboss@Ubuntu-desktop:~$ echo $DESKTOP_SESSION
ubuntu
theboss@Ubuntu-desktop:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF106 [GeForce GTS 450] [10de:0dc4] (rev a1)
    Subsystem: Giga-byte Technology Device [1458:34fe]
    Kernel driver in use: nouveau

to 3rdalbum:
I have now updated, and have an extended desktop, + full screen. Thanks :)

---

### Post by Bryan55 on 2013-02-12
To upgrade start the update manager(look in Systems,Admin)
You will see the option to upgrade to 12.4 LTS. If it does not give that option. Click on setting to change. 
Make sure to back-up all your files first.

Bryan

---

