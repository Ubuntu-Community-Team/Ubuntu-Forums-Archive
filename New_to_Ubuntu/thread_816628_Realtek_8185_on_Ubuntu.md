---
title: "Realtek 8185 on Ubuntu"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Aarookie on 2008-06-02
I am really close to getting my wireless card working on my desktop.  I thought I would share easy steps of what I have put together from this forum and other places, as well as thank the people on this forum who are right there to answer beginners at the drop of a hat, you guys are awesome.

I'm still having a slight problem but I believe the driver is configured correctly it's just at the moment of truth network will not let me in.
Here goes

Download the windows driver for your card for mine someone suggest the 98/ME driver but I stubbornly tried the XP driver which I'm about to change if it won't connect in the next try or two.

Open a terminal and enter these commands:
(this is also assuming like me the target computer has no way of getting to the internet, if you have RJ45 plugged in or some alternate method of connecting to internet you can skip first step.

1. Insert your Ubuntu cd and open terminal
2.sudo apt-cdrom add
3.sudo apt-get install build-essential (Not sure this part is necessary but it sure was for proper tarballing when I was trying to install multiple tar.gz files.
4.sudo apt-get install ndisgtk

5.Open system>administration>Windows wireless drivers menu/program.
6.My computer sort of stuttered at this point but eventually a little window opened up and I was able to browse to my .inf file from winxp driver.  
7.For some reason configure network didn't work at this point the unlock button was greyed out, also mouse pointer was skipping a few beats every so often but after a restart I am able to click on my 2 little computers in the gnome task bar and attempt to connect to my network same way I have done on my laptop here.  However for me and it may be a signal strength problem but I'm not sure that's where I'm stuck, but closer than I have been, and maybe when I move my laptop away from desktop, or try winme driver it may work.  Sorry for babbling hope this helps someone out there in Linux land!!!!

LONG LIVE UBUNTU!!!

---

### Post by Aarookie on 2008-06-02
Will connect on wep128 will not connect on wpa2

---

