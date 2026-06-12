---
title: "how to remove virtual box"
date: 2015-09-07
forum: New to Ubuntu
---

### Post by flex567 on 2015-09-07
I installed virtual box this way([https://help.ubuntu.com/community/VirtualBox/Installation](https://help.ubuntu.com/community/VirtualBox/Installation)) and I want to completely remove it. How can I do that? I wold also like to install 3.xx version from the Ubuntu repository.

---

### Post by patlkli on 2015-09-07
If you installed VirtualBox using the first command in that article, then you can uninstall the virtualbox-5.0 package and the file in /etc/apt/sources.list.d and you should be fine:

```
sudo rm /etc/apt/sources.list.d/virtualbox.list
sudo apt-get remove virtualbox
```

Then you can install virtualbox (and virtualbox-qt for the GUI if you like) from the Ubuntu repositories using:

```
sudo apt-get install virtualbox virtualbox-qt
```

Note that packages in the Ubuntu repositories are in version 4.3.x and not 3.x like you wanted. If you really want such an old version, you'd probably have to manually install it.

---

### Post by flex567 on 2015-09-07
```
~$ sudo apt-get remove virtualboxReading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'virtualbox' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.



```

---

### Post by patlkli on 2015-09-07
Well, that's surprising.
Could you look which VirtualBox packages you have installed?

```
dpkg -l virtualbox*
```

---

### Post by flex567 on 2015-09-07
```
dpkg -l virtualbox*Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  virtualbox     <none>       <none>       (no description available)
ii  virtualbox-5.0 5.0.2-102096 amd64        Oracle VM VirtualBox
un  virtualbox-gue <none>       <none>       (no description available)
un  virtualbox-gue <none>       <none>       (no description available)
un  virtualbox-ose <none>       <none>       (no description available)



```

---

### Post by patlkli on 2015-09-07
Well, then you have to uninstall virtualbox-5.0:

```
sudo apt-get remove virtualbox-5.0
```

The other steps should be the same as in my first answer.

---

### Post by flex567 on 2015-09-07
How can I completely remove the package I just installed([COLOR=#000000][FONT=Ubuntu Mono]virtualbox virtualbox-qt[/FONT][/COLOR]) because it is not working for me?

---

### Post by patlkli on 2015-09-07
You can remove it using: ```
sudo apt-get remove virtualbox virtualbox-qt && sudo apt-get autoremove
```

What is it, what you're trying to do, if I may ask?

---

### Post by flex567 on 2015-09-07
I tried to install virtualbox  and now it works

---

### Post by Geoffrey_Arndt on 2015-09-07
Danke patlkli . . . !   The terminal can be very helpful.

---

