---
title: "Loading Windows Driver"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by dennis17 on 2014-04-19
How do I install a Windows driver that I have on a CD that came with the wireless card? My card is [COLOR=#000000][FONT=Arial]Broadcom Corp BCM4318 [Air Force One 54G] 802.11G wireless L controller [14e4:4318] (Rev 02). I used Linux Lite prior to this and I had to install [/FONT][/COLOR][COLOR=#000000][FONT=Arial]NDISGTK and use the MENU>INSTALL WINDOWS DRIVER. I found the .inf driver that I needed and followed the instructions to install it. It worked fine until I rebooted then it wouldn't work again. I figured I would try Lubuntu 14.04. NEWBIE here so please go slow and explain.
Tks[/FONT][/COLOR]

---

### Post by coffeecat on 2014-04-19
Forget about ndiswrapper and the Windows driver disc and have a look at this sticky in the Wireless & Networking section:

[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

From the list there, it looks as though you need to install the linux-firmware-nonfree package. Don't forget you need a temporary internet connection with an ethernet cable. If that doesn't work for you, post back and one of our members who takes a special interest in wireless will be able to help.

---

### Post by whitesmith on 2014-04-19
First welcome to the forums, **dennis17**. Windows drivers are not recognized by Linux, which uses a different method to "personalize" hardware (they are a part of the Linux kernel called modules). I'm at a loss to understand how a .inf file would be recognized by Linux under any circumstances. Perhaps you are running a dual-boot machine and what you describe was done while you were in Windows. More details would be helpful. Cheers.

---

### Post by coffeecat on 2014-04-19
> **whitesmith said:**
> First welcome to the forums, **dennis17**. Windows drivers are not recognized by Linux, which uses a different method to "personalize" hardware (modules which are a part of the Linux kernel). I'm at a loss to understand how a .inf file would be recognized by Linux. Perhaps you are running a dual-boot machine and what you describe was done while you were in Windows. More details would be helpful. Cheers.

@whitesmith, dennis17 is describing ndiswrapper - ndisgtk is the graphical frontend - which they say they had to use in an earlier and different version of Linux. Ndiswrapper is a way of using Windows wireless drivers in Linux and was more often needed a few years ago when Linux wireless drivers did not cover the range of wireless devices that they do now. Very few wireless devices require the use of ndiswrapper now. Hopefully, the link I posted will help the OP get their Broadcom card working for which they do not need ndiswrapper.

---

### Post by kc1di on 2014-04-19
Hello dennis17, 

You do not need to install windows driver for your card.  Linux has a driver for it already.

can you connect your machine temporarily via a Ethernet cable?  If you can go to a terminal and run these commands :

```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```

Then these:

```
sudo modprobe -rv b43
sudo modprobe -v b43
```

Then reboot . your wiresless should be working. 

good luck.

---

### Post by dennis17 on 2014-04-19
kc1di/Dave
Thanks for that response. I did what instructed and my card "Link" light came on which shows it's recognized. There was no network manager showing on my menu bar so I found the bottom link and followed the instructions. Once installed I found my home connection, entered my PW and bingo..connected..tks
[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

---

### Post by wildmanne39 on 2014-04-19
Please mark your thread solved using thread tools at the top of the page.
Thanks

---

### Post by kc1di on 2014-04-19
Glad it worked for you enjoy ;)

---

