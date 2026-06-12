---
title: "Update resulted in total confusion and no wireless connection or network manager icon"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by samdu on 2008-10-19
no network mgr icon
no wireless option
Hi--

I installed 7.10 using a DVD that came with a book I bought (Linux Bible 2008 ed.). 7.10 worked fine, and I was pleased to see that all I had to do to get my wireless going was type in my WAN password. Cool.  Unfortunately, then when I had a chance to do some updating, (this happened about 3 times--first I updated to what it said was a new upgrade, after that skipped the version upgrade, but installed recommended updates) I lost my wireless!  I never did find the network manager icon anywhere in the task bar (or anywhere else), and when I did go to System to get to where you'd have a choice of selecting configs for wireless, wired or manual, there was nothing about wireless at all.

I did look at WiFiDocs WPAHowTo, and I did see something about install Network Manager by doing/using sudo apt-get install netork-manager-gnome
but of course then I had no internet access on this computer to download that even if I could have known where it went when I downloaded it.

Of course, I feel like a total dufus posting this because of how clearly it reveals my ignorance/inexperience, but I'd love to get some advice.

Solution at the moment was to reinstall 7.10 off the DVD and not upgrade/update anything!

Thanks in advance.:confused:

---

### Post by forger on 2008-10-19
I would suggest to get the new stable version ubuntu 8.04 hardy heron:
- download: [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)
- request a cd: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

or Ubuntu 8.10 Intrepid Ibex (beta, but soon stable - really worth to try for hardware support):
- download: [http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)

Also, please reply with the brand and model number of your wireless network card

---

### Post by samdu on 2008-10-19
Wireless card is a Zyxel G-102 v2

Thanks!

---

### Post by PocketDog on 2008-10-20
It may be the notification area which has disappeared, it happens. - right-click the task bar > add to panel > choose 'notification area'. If that's not on your task bar then your network manager applet (nm-applet) won't be there either.

---

