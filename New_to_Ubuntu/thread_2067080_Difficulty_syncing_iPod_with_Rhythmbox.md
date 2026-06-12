---
title: "Difficulty syncing iPod with Rhythmbox"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by JSF16 on 2012-10-06
I have been battling this thrice-cursed device for hours now, so I pray you please offer me mercy and help me fix this evil afflicting me.

Okay: Trying to sync iPod touch with Rhythmbox. The program recognized my iPod, I can delete songs on it. Now, I am trying to sync my library with the iPod so I can listen to music, on the iPod. No problem right? WELL.

I don't know what it means. But it is saying to me that my 8GB iPod with a clear memory doesn't have room for thirteen or so songs. And this is wrong. And I need help. Please.

---

### Post by DuckHook on 2012-10-07
It is very difficult to sync Apple products with Linux because Apple is a closed-silo proprietary company that does not release its code base to Linux developers. Therefore, the only way to communicate with Apple devices is for Linux developers to reverse engineer the iPod communication subsystem and file structure and then write drivers that approximate the various system calls, etc. needed to communicate effectively. It becomes a frustrating game of catch-up, where Linux/Ubuntu/Rythmbox is programmed sufficiently to work with a given iPod OS only to have that programming broken with a new Apple OS upgrade.

Paul McEnery has written utilities that work with some older versions of Apple phones and iPods. His PPA can be found at: [https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa)

Warning: use of such utilities is at your own risk. Due to the reverse-engineering nature of this process, it is only prudent to consider all such utilities to be experimental or effectively beta.

---

### Post by JRBASTIEN on 2012-10-08
Just a wild guess:  Try enabling disk usage first with iTunes if you have access to this application.

[http://support.apple.com/kb/HT1478](http://support.apple.com/kb/HT1478)

If it is not enabled, perhaps RB cannot calculate the disk space properly.

---

