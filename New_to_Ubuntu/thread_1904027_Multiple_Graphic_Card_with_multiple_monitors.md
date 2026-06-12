---
title: "Multiple Graphic Card with multiple monitors"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by valter479 on 2012-01-03
Hello there, 

I am newbie, after install Ubuntu 11.10 i try to set up multiple monitors using Nvidia X Server Setting. 


First:
 Video cards are 2 (two) - nvidia GeForce GTS 250. 
 Monitors are  Asus S211HL(Main monitor) and Dell 1704FPT (second monitor). 
 (each monitor is plug to each card)

On Nvidia X Server Setting i try this:
On the Xserver Display Configuration, i set the second monitor Configuration to "Separate X screen (requires X restart)" It is the only option.  It doesn't allow me to change to "TwinView".  

After changing the Configuration to "Separate X screen (requires X restart)", i click on "Save to X Configuration file". Which i believe saves the setting to the  xorg.conf file. After that i restart the machine. When it boot up, the second monitor is white and when i move the mouse to the second monitor, the cursor change to a X and i can not drag anything to the second monitor. 

My question is what is going on? Why is doing that? Is it because of each monitor is plug to each video card? Does it has to be in "TwinView" to make it work?

I need a little help here. If you need to look at the xorg.conf i believe i can post it. 

Thanks,
Valter479

---

### Post by cariboo on 2012-01-06
You don't need two graphics cards to use two monitors, just remove one graphics card and connect both monitors to the remaining video card. You should then be able to setup twin view.

If you have to use two graphics cards for whatever reason, make sure the drivers for each card are configured in /etc/X11/xorg.conf

---

### Post by valter479 on 2012-01-06
Hello Cariboo907,

Thanks for reply.
 I have two graphics cards because i also have windows install on the machine and i play games on windows. 

I also checked the xorg.conf file and both cards are configured. 

Do you have any other suggestion or opinion i would appreciate. 

Thanks again,
Valter479

---

### Post by rlg231 on 2012-02-12
Was this ever resolved? I am having the exact same issue. I am using two cards with four monitors ( I use them to monitor my network). I also get the white screen on anything other than the first display.

---

### Post by Theact on 2012-02-15
What a mission...

I have reached a point where i can get all the screens working.
Yes all 4 of them using two graphics cards. 
But now I cannot for the life of me get it such that
the screens on the second card can do anything other than display the background.
So you can move the mouse nicely from the second to the third screen but
you can not move a window across or right click on the background.

I have 2 nVidia cards. So anyone got any ideas how to solve this?

---

### Post by Larry64 on 2013-03-21
Was this ever resolved?

I have been running 3 monitor on two graphics cards for years, with no real problems.  But since Unity came along and I think Gnome3 they all seem to in no way support having multiple monitors or later not multiple graphics cards.

I currently work around it by using LXDE which mostly works.  Still sometimes you right click and the menu will pop up on the wrong monitor.

I want my multi-graphics cards and monitors support back!

---

### Post by QIII on 2013-03-21
This thread is a year old.

&#65279;If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.


*Thread **closed.***

---

