---
title: "New to Ubuntu. Dell Inspiron D830 refuses to shut down"
date: 2015-12-26
forum: New to Ubuntu
---

### Post by billnes on 2015-12-26
Hello all,

I installed Ubuntu 14.04.3 LTS on a Dell Inspiron D830. The Inspiron is running the Core2 Duo processor and has 4Gb of RAM. The installation has two annoying quirks & I was hoping that someone had answers for a complete & total Ubuntu noob.

The computer refuses to shut down. The system hangs on a black Ubuntu screen that has five dots underneath the word Ubuntu.  From left to right, the five dots cycle between white-to-orange and that's where it stays.  

Next, it appears that a driver for the D830's internal Wi-Fi card has not been installed. I can get around that by using a USB Wi-Fi dongle, but it's still annoying & I'd like the internal Wi-Fi to work properly.

I was really surprised to see these problems. I read on the official Ubuntu web site that Canonical has a software agreement with Dell. Inside the Ubuntu Software Center, I found two programs for Dell computers. I have no clue how to use them. When I click on the app "Dell Driver Installer", it says it will install a driver package that I downloaded.  I don't know what to download and don't know what site download site to use.

Please help me. Thanks so much.

---

### Post by mörgæs on 2015-12-26
Hi, welcome to the fora.

You don't need to add 'New to Ubuntu' to the title. You are already posting in the 'New to Ubuntu' forum.

For the networking problem please follow this: 
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Does the computer shut down if you push Enter when it's hanging with the five dots?

Yes, Canonical is cooperating with Dell regarding new hardware. The program was not in place when the 830 was born (but the 830 and similar Dells are easy to get running).

---

### Post by Geoffrey_Arndt on 2015-12-26
Did you verify the original install was from a good image (checksum matched)?   If you use that same install DVD or USB flash-stick, does the system shut-down completely (from a live session)?     Also, if you log out, then shut down, will it do so without issue?

---

### Post by techvish81 on 2015-12-28
try by removing the modem manager, don't worry you can reinstall it . ```
sudo apt-get autoremove modemmanager
```

---

