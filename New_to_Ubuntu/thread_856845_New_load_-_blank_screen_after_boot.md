---
title: "New load - blank screen after boot"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Bartee on 2008-07-11
OK... 

New computer.  

ASUS P5E-VM HDMI mobo, Core 2 Duo E8200
This mobo has dual video on board.  1 hdmi and 1 vga.

I am plugged into the vga for now just to get build working.

Installed ubuntu with 8.04 64 iso cd.  

took defaults, disk partitioned.  I got the weird bird background and was told to reboot.

I reboot and get the moving slider.

It goes across screen blinks with dash in upper left corner then screen blinks and I get blank screen.

I was able to interrupt the loading processes and saw a message that there was a problem loading x window and to look in the syslog. 

Where is syslog ?  what directory ? 

I have interrupted grub and messed with that.

I know enough shell to simple things and have books to look at.

So I think there is a graphics driver problem.

QUESTION # 2....

Also how do I log in as root.

I set a password in the install process but that was for the 1st user ( me ).  Nowhere did I set a root password, so not sure how to get logged in as root.
How do I find it.

---

### Post by markbuntu on 2008-07-11
syslog is in /var/log

If you select safe mode in the grub menu, the second selection down, you will be root user by default.

There is no root password per-se. You need to use sudo on the command line to be root.

---

### Post by Bartee on 2008-07-12
I am very new to ubuntu.  I just kept trying things (like logging in at root on a terminal command line ) .

Now I know how to interrupt grub and what happens there.

I really think the last thing I did before it worked was  to start x-windows like this from the root command line: 

 startx --help

I was trying to see what the startx parameters were so I might could get some more info out of the startup.

WELL........ the UI displayed.  So I logged on and the 1st thing I did was load 20 updates to the release.  

Now When I reboot it is working.  

So I am NOT sure what it was.  I do not think it was a driver problem  ( although I learned more than I wanted about drivers in the process )

So,... thanks for replying.

WOW I am very impressed with this box.  I guess this mobo and E8200 combination are  a good thing

---

