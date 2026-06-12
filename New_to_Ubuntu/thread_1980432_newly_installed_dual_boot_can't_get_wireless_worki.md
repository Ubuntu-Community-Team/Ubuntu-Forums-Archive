---
title: "newly installed dual boot can't get wireless working"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by Vamplock on 2012-05-15
Hi forum, (first ever post)

I'm using an old dell D620 Broadcom NIC is fine, however internal wireless isn't currently working.

how do I properly address the issue?
locate the correct driver,
install said driver.

also, since updating I notice that sound is no longer working, but that is a separate issue.

I ran a dual boot of Ubuntu a while back, and was, in my very limited spare time - trying to learn more about the whole Linux environment. Unfortunately the old machine died and I haven't got back round to looking at Linux again until now. This flavour has become very GUI orientated, which is very impressive, and has a nice look and feel - but coming from a dos background ... I still want to be addressing things from the CLI... (old hat - I agree)

 I have been a dos/windows guy for years, and dabbled a bit in Novell 3.x up to 5.
I need to enhance my Linux knowledge to put an end to the niggling voice that I have thus far been ignoring... (prob because I'm getting old)...

cheers

V

---

### Post by Lisiano on 2012-05-15
Wanting to do stuff from the command line is something I applaud for =D>
Anyway, tell us more about your WiFi adapter, open up a terminal (Ctrl+Alt+T) and type in ```
lspci
```

---

### Post by Vamplock on 2012-05-15
):P thank you for the prompt reply ...


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)

---

### Post by Lisiano on 2012-05-15
You have a Broadcom Corporation BCM4311 802.11a/b/g
Run this.
```
sudo apt-get install firmware-b43-installer
```
Now either reboot or run this
```
sudo modprobe -r -f b43
sudo modprobe b43
```

*Feel the power of CLI &#8482;*

---

### Post by kc1di on 2012-05-15
you may find this page of help:

[https://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/]("https://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/")

---

### Post by sudodus on 2012-05-15
I suggest that you have a look at this link for command line tips
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1909108_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1909108")

and for your particular wifi problem, you can look at this link
[[COLOR="Red"]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

*Edit: I just noticed that Lisiano posted detailed advice while I was writing*

---

### Post by Vamplock on 2012-05-15
that returned:

frank@ubuntu:~$ sudo apt-get install firmware-b43-installer
[sudo] password for frank: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base firefox-locale-zh-hans language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
frank@ubuntu:~$ sudo modprobe -r -f b43
frank@ubuntu:~$ sudo modprobe b43

and as if by magic!
my wireless controller connected to my hub...

*Bows in awe* Thank you :KS

---

### Post by Vamplock on 2012-05-15
Thank you Dave! although I am fixed now, I will give it a look anyway... no point in fixing it if you don't understand how! :-) cheers!

V

---

### Post by Vamplock on 2012-05-15
> **sudodus said:**
> I suggest that you have a look at this link for command line tips
[[COLOR=Red]_http://ubuntuforums.org/showthread.php?t=1909108_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1909108")

and for your particular wifi problem, you can look at this link
[[COLOR=Red]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

*Edit: I just noticed that Lisiano posted detailed advice while I was writing*

Thanks for the tips !! ;)

---

### Post by Lisiano on 2012-05-15
Your welcome, if you have no further questions for example about the commands used above or about anything else, please mark the thread as solved in the thread tools above.

Have a good day!

---

