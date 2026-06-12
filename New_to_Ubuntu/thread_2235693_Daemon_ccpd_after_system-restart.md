---
title: "Daemon ccpd after system-restart"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by sigtermans2 on 2014-07-22
I'm a absolute beginner in Linux/Ubuntu, and I installed Ubuntu 14.04.

I installed a Canon Laserprinter LBP6310dn network-connected. After some confusion in reading and understanding the Canon online installation manual the printer works FINE!

But... after every system-restart the printer daemon 'ccpd' is no longer activated. Which means I have to activate it with: 
sudo /etc/init.d/ccpd restart > after this: sudo /etc/init.d/ccpd status returns two(2) values which is OK!
So printing works fine again.

Question: what should I do to make the printer work after every system-restart?

Note: I searched the internet for solutions (for weeks),and followed all kind of tips but noreal solution found till now.

Pleaase HELP!

---

### Post by pdc on 2014-07-23
Hi sigtermans2; welcome to the Ubuntu forums; sorry to hear of your restart issues; you have done very well to get the CAPT driver installed and all set up;

......not sure what you have tried: 

[http://askubuntu.com/questions/105891/how-to-make-lbp-1120-canon-printer-work](http://askubuntu.com/questions/105891/how-to-make-lbp-1120-canon-printer-work) links such as this 

and this [http://askubuntu.com/questions/246515/how-to-set-ccpd-daemon-to-start-automatically-at-startup](http://askubuntu.com/questions/246515/how-to-set-ccpd-daemon-to-start-automatically-at-startup)

at the bottom suggest 

> [COLOR="#FF0000"]gksudo gedit /etc/rc.local[/COLOR] and paste into it > [COLOR="#EE82EE"]/etc/init.d/ccpd start[/COLOR] just above the line exit 0  (see attached thumbnail)

SAVE ..........CLOSE ..............

it would seem you should issue these further commands

> sudo update-rc.d ccpd defaults 50          (to assign it a run level)    I added the value 50 from here [http://wiki.ubuntu.org.cn/UbuntuHelp:CanonCaptDrv190#Auto_Start_ccpd](http://wiki.ubuntu.org.cn/UbuntuHelp:CanonCaptDrv190#Auto_Start_ccpd)

_______________

I hope this may be helpful

___________

In fact before doing anything, can I suggest you read the above CAPT guide [http://wiki.ubuntu.org.cn/UbuntuHelp:CanonCaptDrv190#Auto_Start_ccpd](http://wiki.ubuntu.org.cn/UbuntuHelp:CanonCaptDrv190#Auto_Start_ccpd)  ..........it seems very thoughtful and well laid out and you may value perusing it

---

