---
title: "Issue at Startup"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by ch1ck3n on 2008-05-20
So this is a pretty old PC (Compaq with 900MHz AMD) but I never had this issue with previous Ubuntu versions. When I log in to the OS The screen does not fully load up, you can see the menu bars and a box but it isnt filled in with anything. After letting it sit a while, everything loads up and here is the error I see in the box:

---------------------------------------------------------
There was an error starting the GNOME Settings Daemon

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
---------------------------------------------------------

This wouldnt be a problem because everything loads up fine after a while, but it just takes too long. What is the issue?

I tried the fix in an older post that had me modify two files, but that did not fix. CTRL+ALT_BKSPACE doesnt fix the issue either.

---

### Post by cmnorton on 2008-05-21
I get that a lot on an older PC, but when I log out and back in, I do not get the error. I have never tested it thoroughly, but in my case I am fiddling with the mouse koala pad during the log in process. But, who knows, it could be something else.

---

### Post by nicedude on 2008-05-21
I would strongly suggest you have a look at Xubuntu which is built on the same base as Ubuntu but instead of using the Gnome desktop ( Which while the nicest looking and most powerful IMHO ) is large and requires the hardware to make it run speedily. The Xubuntu is based on a desktop called XFCE4 which is much more lightweight and will be much speedier on older computers ( I had one that would barely boot Ubuntu that Xubuntu does just fine with ). It just uses different settings utils and GUI windows than Gnome but in general is just about as user friendly as Gnome. 

So have a look at it and read what some others say about it and if you think I may be right, Install it on your box and you will be pleasantly surprised at the speed difference.


Hope that helps and Good Luck,

nicedude

---

### Post by spiderbatdad on 2008-05-21
Agree with nicedude in that the machine is probably more suited to Xubuntu.
I have also had success with older compaqs with the use of some boot parameters, in particular: noapic nolapic
As the long boot time is most likely the result of hardware detection problems. Sometimes specifying vga is necessary too: noapic nolapic vga=791 
for example.

VGA:```
	640x480   800x600   1024x768   1280x1024   1600x1200
8bit	769	   771       773        775         777
15bit   784        787       790        793         796
16bit   785        788       791        794         797
24bit   786        789       792        795         798
```

---

### Post by NIT006.5 on 2008-05-25
If everything runs fine once your login has eventually completed, then I would think the machine is actually "ok" to run standard Ubuntu. I've also been having the long delay after logging in, with the same error, and I've been struggling to find a solution the whole week. However, in my case it was happening because my loopback address wasn't working, and this is obviously used somehow to connect to the settings daemon by the looks of it.

Try:
```

ping 127.0.0.1

```

If you get a reply, then this is not the problem. If you don't get a reply then check in /etc/network/interfaces and make sure your loopback interface is defined there. It should look something like this:

```

auto lo
iface lo inet loopback

```

If those lines are missing, try adding them in. You will then need to either reboot, or restart networking as follows:

```

sudo ifdown -a --force
sudi ifup -a --force

```

Then logout and test. Really hope that helps, as I know how frustrated I was on this!

---

