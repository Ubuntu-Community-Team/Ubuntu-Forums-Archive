---
title: "ok, this is my graphics card"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by pcrussell50 on 2008-07-30
just upgraded from 7.10 to 8.04 and...

...i'm having the dreaded 800x600 as my _only_ choice for a screen resolution.  i see that all the kind folks wanting to help want to know what the graphics card is, sooo...when i go to the support site of my computer, it lists the graphics driver as:

VIA/S3 Unichrome KM400 Driver

the specs page lists graphics as:

VIA S3 UniChrome™ 3D Graphics

if this is not the name of the graphics "card", i don't know how to find it. it appears to be integrated into the MB.  

the kicker is, my graphics and sound worked _perfectly_ in 7.10 and older.  it still works fine in windows, too.

-peter

---

### Post by PmDematagoda on 2008-07-30
Post the output of:-
```
lshw -C video
```

About the S3 driver, the UniChrome driver has been deprecated, so now you will need to use the OpenChrome driver which can be installed with:-
```
sudo apt-get install xserver-xorg-video-openchrome
```
after installing OpenChrome, boot Ubuntu in Recovery Mode and then choose xfix, after that is done see if your problem is now solved.

---

### Post by pcrussell50 on 2008-07-30
> WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: VT8378 [S3 UniChrome] Integrated Video
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=32 mingnt=2

here it is!  thanks.

-peter

---

### Post by pcrussell50 on 2008-07-30
and when i run this command you gave me:

```
sudo apt-get install xserver-xorg-video-openchrome
```

i get:

> ~$ sudo apt-get install xserver-xorg-video-openchrome
Reading package lists... Done
Building dependency tree       
Reading state information... Done[B]
xserver-xorg-video-openchrome is already the newest version.[/B]
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 


say, what does it mean that unichrome has been "depracated"?  does that mean the developers have dropped my mother's computer from their interest?

-peter

---

### Post by PmDematagoda on 2008-07-30
Can you post the output of:-
```
cat /etc/X11/xorg.conf
```

> say, what does it mean that unichrome has been "depracated"? does that mean the developers have dropped my mother's computer from their interest?
Not the VGA card, just the driver which has been dropped in favour of OpenChrome.

---

### Post by prshah on 2008-07-30
> **pcrussell50 said:**
> 
```
sudo apt-get install xserver-xorg-video-openchrome
```


It seems you have the driver installed, but it may not be activated. You can check which driver is active by:

1) Press Alt+F2
2) give the command```
gksudo displayconfig-gtk
```
3) Click on the "Graphics card" tab
4) Check, and if necessary, change the driver to a suitable one (don't know what exactly it is for this card, but the description should give a clue).

If the driver is already correctly set, post your "/var/log/Xorg.0.log" file here; you may need to (g/b)zip it up first.

---

