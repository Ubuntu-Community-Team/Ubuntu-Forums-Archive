---
title: "touchpad not working"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by antobbo on 2011-12-30
HI guys, I am experiencing a very annoying problem: my touchpad stops working all of a sudden and I cannot understand why it is doing it. I have done a bit of research, and I have found out how to get around it (either bring up the terminal and run ```
synclient TouchpadOff=0
``` or log out with ctrl+alt+l - I think - and log in again). All these work, fair enough, but I remember the person who posted that - I seem to remember it was on this forum somewhere - said it was a one off problem, or sth that doesn't happen on a regular basis. Unfortunately for me, this happens every time I switch on my computer, after 2-3 minutes. This is getting really annoying now, so I was wondering if anybody knows how to find out what it is that is switching my touchpad off. COuld it be a piece of software I have installed?
I have a samsung nc10, with dual boot (windows xp and ubuntu 11.10) and this problem started all of a sudden and , as mentioned, it happens every day without failing.
any help appreciated
thanks

---

### Post by cmcanulty on 2011-12-30
Install dconf-tools in synaptic. Then go to applications-system tools-dconf.Navigate to
org.gnome.settings-daemon.peripherals.touchpad
make sure touchpad-enabled is checked.

---

### Post by antobbo on 2011-12-30
Hi cmcanulty,
thanks for your post. SOrry I am not well versed in ubuntu, how do I install that? do I run ```
sudo  dconf-tools
``` in the terminal?
thanks

---

### Post by cmcanulty on 2011-12-31
go to synaptic under applications-other and type it in then click to install. If you don't have synaptic install it from software center first

---

### Post by antobbo on 2012-01-01
Hi there, thanks I have installed the synaptic and then  dconf-tools. I don't really see the application panel or anything similar, can I do it from the terminal, it might be easier. If so how would I do it please?
thanks

---

### Post by cmcanulty on 2012-01-01
i am using classic if using unity just type dconf-tools in the search box then go to the spot

---

### Post by Miljet on 2012-01-01
I believe antobbo is running Lubuntu, in which case gnome tools aren't going to help much.

---

### Post by sbandeira on 2012-01-04
I had the same problem with my toshiba satellite.
My touchpad happened to be blocked in windows. So I restarted it in windows, unblocked and it came to life in ubuntu.
HTH.

---

