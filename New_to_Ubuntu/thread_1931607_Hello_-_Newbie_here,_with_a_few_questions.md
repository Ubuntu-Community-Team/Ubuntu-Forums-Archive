---
title: "Hello - Newbie here, with a few questions"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by atrampus on 2012-02-25
Hello All.
 
Allow me to introduce myself - My name is Andrew.
 
I mostly use Mac's in my household, and have been for the past 6 years after using Windows, and some RetHAT Linux in my past.
 
My home setup compromises of a MBP 13', MB 13', iMac 20, 1 x iPad2, and 2 x iPhones. I have also recently purchased a WD TV Live, which I wish to replace with an Apple TV 2, with Mountian Lions impending release to take full use of AirPlay Mirroring.
 
I have been doing some research on what I want to do, but it seems that iTunes streaming to an ATV seems to be an issue.
 
Basically, I wish to do the following.
 
1. Use Ubuntu/Server to setup 2x 6 drive RAID 5 arrays. (starting off with one, then adding a second when required / funds allow)
2. Have Time Machine backup to the machine - (seems easy enough)
3. Find a way to automatically sync all my documents to the Ubuntu machine
4. Have my iTunes libary on the server, with iTunes installed via WINE.
5. Have iTunes stream to an ATV - (It seems that this has issues with crashing on ubuntu ?)
6. Have full blown copies of Office / IE so I can remotely access from my iPad (should allow me to carry my laptop around a lot less).
 
Also, I have done some work on this, but I would like to hear everyones experience on which VPN software/clients are best for use with iOS, and Mac OSX.
 
I appreciate everyones assistance on this, and it would go a long way to helping me complete this.
 
Regards, AT.

---

### Post by d4m1r on 2012-02-25
1) Office 2007 and 2010 worked perfectly fine under Wine/Ubuntu last time I checked.

2) Do NOT use iTunes under Wine/Ubuntu! Most functionality doesn't work (including syncing so I am guessing Air Play too) so I'd recommend Rythmbox instead. It is able to detect iDevices and sync. However, you are going to have to do more research into the Air Play functionality in terms of Ubuntu.

3) For VPN I suggest OpenVPN. You can run the server on Ubuntu and there's an official client for Linux, Windows, and Mac OS.

---

