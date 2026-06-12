---
title: "Ubuntu 11.10, wireless disconnects and reconnects"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by Raven609 on 2012-02-11
Hi, I'm practically new in Linux and Ubuntu. I have Ubuntu 11.10, along side with Windows XP, in my laptop, it a Compaq Presario V3000, I can connect to the internet by wireless, and ubuntu recognizes my network card witch is a "Broadcom-BCM4311 802.11b/g WLAN", but when I'm on the internet sometimes it disconnects by it self, and after a few minutes it reconnects, when I first turn on my laptop and use Ubuntu,I get disconnected after 15 minutes, and then reconnects instantly, but then after that, I gets disconnected like every 2 or 3 minutes and then it takes more time to reconnect, like 5 or 10 minutes.  I've only tried this solution, but it didn't work, but I don't know if I did it correctly:

[http://ubuntuforums.org/showthread.php?t=1860799](http://ubuntuforums.org/showthread.php?t=1860799)

I did what the is in post #5. but I still have the problem, I read the rest of the forum, but I wasn't sure if I should do it or not. so please if someone could help me please, and if it's not much to ask please tell me step by step what to do, I haven't get used to Ubuntu yet, so please and Thank you

---

### Post by Ms. Daisy on 2012-02-12
Some things to consider:
1. How far are you from the wireless router? Are there walls or objects between your computer & the router?  Test this by hanging out right next to the router.

2. Could it be the internet connection itself that's cutting in & out, not the computer? A simple test is to see if other computers on the same network are having the same problems.

3. On my laptop I have noticed that when I'm running on the battery my internet connection gets flaky when the battery drains a bit.  Are you running on battery or plugged in?

4. Do you have similar problems when you run XP on the same computer?

---

### Post by Raven609 on 2012-02-14
> **Ms. Daisy said:**
> Some things to consider:
1. How far are you from the wireless router? Are there walls or objects between your computer & the router?  Test this by hanging out right next to the router.

2. Could it be the internet connection itself that's cutting in & out, not the computer? A simple test is to see if other computers on the same network are having the same problems.

3. On my laptop I have noticed that when I'm running on the battery my internet connection gets flaky when the battery drains a bit.  Are you running on battery or plugged in?

4. Do you have similar problems when you run XP on the same computer?
Hi, sorry it took me a while to answer you, I have a lot of things to do at school.

1) it's not really that far is at least like 10 meters in a room, and there's only like 2 wooden doors, the room where my modem/router is and my bedroom
2)All my other computers in my house work fine and have no problems, iPods, iPhones, other PCs, even my laptop with Windows XP works
3) Battery has never affected my internet connection, including with Windows XP
4)With windows XP there's no problem at all

Thanks for your answer, but if you know something or somebody who could help me I would really appreciate.

---

### Post by Ms. Daisy on 2012-02-15
See this for a possible fix, looks like someone was successful with a different model of Compaq Presario:

[http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)

---

### Post by kwchristensen on 2012-02-15
I've been battling this issue for a few weeks now. I have come across it in both Ubuntu 11.10 and Mint 12. I finally found a workaround that seems to have fixed the issue in an old bug report here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/295414]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/295414")

remove the gnome network manager
[INDENT]*sudo apt-get remove network manager**[/INDENT]

replace it with wicd
[INDENT]*sudo apt-get install wicd*[/INDENT]

---

### Post by jmlm-1970 on 2012-10-07
If you still get internet off and on, this is most probably caused by the computer storage support (for example: hard disk) having hardware failure in IO (input/output) operations.

To test if this is the case, just disconnect the current hard disk, and boot from a USB disk (a 8 GB PEN is enough to install Ubuntu 12.04.1) or from a bootable CD, and test if internet keeps disconnecting...

---

### Post by will1982 on 2012-10-07
Whoa, dead thread revival.

Is your wireless card fully compatible with Ubuntu? I know that some have problems.

---

