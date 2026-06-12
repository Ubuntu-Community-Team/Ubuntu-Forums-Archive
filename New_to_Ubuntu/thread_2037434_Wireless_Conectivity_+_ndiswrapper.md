---
title: "Wireless Conectivity + ndiswrapper"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by Blindsniper on 2012-08-04
Hi everybody,

Yesterday night I decided to install Ubuntu, because I wanted to see how it is and play around, so I formatted an old 160 GB harddrive and Installed Ubuntu. So far I am very impressed with the speed of Ubuntu and I would like to keep it on my computer.

Now to the problem: I have a Wifi usb stick, to be precise it's a Trendnet TEW-624UB, and I have tried connecting but to no avail. I figured it was the drivers so I started searching. It seems that Trendnet doesn't make drivers for Linux, but then I discovered ndiswrapper. I followed some instructions([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) and installed it. I then installed the windows drivers from the CD I got. The guid on how to install ndiswrapper then told me to run the following commands in terminal
```
sudo depmod -a
sudo modprobe ndiswrapper
```
The first command seems to execute fine(no errors) but the seconds command gives me an error, I can't recall the exact error right now but it went something like
```

Fatal: module ndiswrapper not found

```
The guid says if you recieve that error then you didn't uninstall the ndiswrapper that comes with ubuntu. I tried my best to uninstall it but it didn't work. 
The command I used for uninstalling was the same one I used for installing: dpkg , but with the -r switch
After uninstalling I tried reinstalling but that didn't work.
Any help appreciated.
Sorry for long post

---

### Post by HermanAB on 2012-08-04
You have two solutions:
a. Go to the ndiswrapper web site and read the real instructions.
b. Buy another wifi dongle.

The second option is usually a whole lot less trouble.  Look for a dongle that has a Linux Penguin or an Apple Mac sign on the box.

---

### Post by Blindsniper on 2012-08-04
The ndiswrapper site links to the site I linked. I can't really afford to buy a new dongle just for ubuntu. I think I'm missing something simple. A friend told me that clean ubuntu installs don't have all the updates, so maybe If I could connect via a cable I could install the updates, but do updates contain new drivers ?

---

### Post by Blindsniper on 2012-08-04
I Formatted and Re-Installed Ubuntu, and now it works, It seems my meddling with  Terminal broke something.

---

