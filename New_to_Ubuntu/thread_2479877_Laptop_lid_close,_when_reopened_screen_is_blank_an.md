---
title: "Laptop lid close, when reopened screen is blank and unresponsive"
date: 2022-10-11
forum: New to Ubuntu
---

### Post by cwmoser2 on 2022-10-11
Ubuntu Mate 22.04, Lenovo w510 laptop.
When I close the laptop lid and then reopen it the screen is blank.
Happens when just using battery and also when plugged into adaptor.
Have to reset to get working again.

Tried various settings in /etc/systemd/logind.conf but no help.

Any suggestions?

---

### Post by cwmoser2 on 2022-10-13
Did a little more investigating via this URL:
[https://askubuntu.com/questions/1268650/laptop-will-not-suspend-on-lid-close](https://askubuntu.com/questions/1268650/laptop-will-not-suspend-on-lid-close)

Said to check to see if the Lid Switch is actually being detected via:
```
$ journalctl | grep -i " lid "
```

My output is showing the Lid Switch stopped being logged as opened on September 26.
That's around the same time I updated from Ubuntu 20.04 to 22.04

---

### Post by patrick2957672 on 2022-10-13
install devuan, it helps a lot.
[www.devuan.org](www.devuan.org)

the lid close action can be unactivated in ubuntu into gnome/kde settings.

---

### Post by cwmoser2 on 2022-10-13
I found this solved my issue:

                        [SIZE=2]**$ gnome-tweaks**[/SIZE]
 [SIZE=2]**General tab -> Toggle the "Suspend when laptop lid is closed" switch to off**[/SIZE]
 
 
 [[SIZE=2][/SIZE]]("https://help.ubuntu.com/stable/ubuntu-help/power-closelid.html.en")[SIZE=2]**[https://help.ubuntu.com/stable/ubuntu-help/power-closelid.html.en](https://help.ubuntu.com/stable/ubuntu-help/power-closelid.html.en)**[/SIZE]

---

### Post by cwmoser2 on 2022-10-15
Update:  On my second laptop I found that I also had to:
  	 	 	 	   
 
 [SIZE=2]**ALSO, click on the Battery Power Icon and select Power Settings ...**[/SIZE]

 [SIZE=2]**On AC Power, When laptop lid is closed:  Do nothing**[/SIZE]
 [SIZE=2]**On Battery Power, When laptop lid is closed:  Do nothing**[/SIZE]
 [SIZE=2]**On General: **[/SIZE] 
 [SIZE=2]**	When Power button is pressed:  Ask Me**[/SIZE]
 [SIZE=2]**	When the suspend button is pressed:  Suspend**[/SIZE]
 [SIZE=2]**	Select:  Always display an icon     **[/SIZE][SIZE=2]**vc**[/SIZE]

---

