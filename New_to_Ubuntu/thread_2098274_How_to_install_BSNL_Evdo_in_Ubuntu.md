---
title: "How to install BSNL Evdo in Ubuntu?"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by chndn on 2012-12-26
I am having a BSNL EVDO Rev A USB Data Card Model No.:T-U500 and want to install it in my Ubuntu which has no internet connection. What should I do?

I have installes wvdial, gnome-ppp.
When I click detect on gnome-ppp I get "No modem was found on your system"

I have posted similar questions on same problem in:
[http://askubuntu.com/questions/232837/how-to-install-bsnl-evdo-u500-data-card-in-ubuntu?lq=1](http://askubuntu.com/questions/232837/how-to-install-bsnl-evdo-u500-data-card-in-ubuntu?lq=1)
[http://askubuntu.com/questions/231665/install-bsnl-evdo-card-in-ubuntu-12-10](http://askubuntu.com/questions/231665/install-bsnl-evdo-card-in-ubuntu-12-10)
[http://askubuntu.com/questions/227496/how-to-install-wvdial-without-getting-the-following-error?lq=1](http://askubuntu.com/questions/227496/how-to-install-wvdial-without-getting-the-following-error?lq=1)
:popcorn:

**_I logged into Windows, uninstalled it, unplugged the modem, plugged it again, clicked "open folder to view files", clicked Linux, Copied "BSNL EVDO Installer" to the desktop. Then I logged onto Ubuntu moved the file into its desktop and installed it. After installation I clicked "EVDO Data Card" but nothing happened. What should I do?_**

PLEASE HELP:(:(:(:(:(

---

### Post by Cheesemill on 2012-12-26
Can we get more details about the data card please. If you can post back with the result of the following command:
```
lsusb
```

---

### Post by sahabcse on 2012-12-26
The below link may help

[http://ubuntuforums.org/showthread.php?t=1868076](http://ubuntuforums.org/showthread.php?t=1868076)

---

### Post by fantab on 2012-12-26
> "No modem was found on your system"This means your USB-MODEM is not being detected. Post the output of:

```
$ lsusb
```'usbmodeswitch' is pre-installed on Ubuntu... Check if it is there. Even if its there remove it with Synaptic or Software Centre and then reinstall it.

Remember you may have to wait/give a few minutes for your USB-Modem to get detected. 

NetworkManager (which is pre-installed on Ubuntu) generally works well without wvdial.

Post the output of the *lsusb* so that we know whether your modem is being detected or not.

---

### Post by chndn on 2012-12-27
> **Cheesemill said:**
> Can we get more details about the data card please. If you can post back with the result of the following command:
```
lsusb
```

15eb:7153 It is detected (that is why I gave the links):lolflag::lolflag:

---

### Post by purezen on 2013-08-04
Hey..!


I have bought the same data card and am facing the same issue as well..!


So, I have started a thread here:
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=3&t=1601](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=3&t=1601)


Also, interestingly, I found a Linux installable on the USB Modem itself by accessing via a Windows machine.


However, the application is not running on my machine.
I also, extracted the files in the same but could not figure out what to do with them.


Here's the link to the .deb that was included. Hope that it at least lets us get connected somehow.


[https://dl.dropboxusercontent.com/u/93115409/Linux/BSNL%20EVDO%20Installer.deb](https://dl.dropboxusercontent.com/u/93115409/Linux/BSNL%20EVDO%20Installer.deb)


Cheers..!

---

