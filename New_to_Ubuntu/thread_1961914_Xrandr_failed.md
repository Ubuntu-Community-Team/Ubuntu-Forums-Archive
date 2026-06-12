---
title: "Xrandr failed"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by Zachiryus on 2012-04-20
I installed ubuntu 11.10 and right away i realized that the resolution was off. after a while of looking around i found a thread about xrandr. when i attempt to change the resolution settings i get a "Failed to get size of gamma for output default"
Please help. thanks in advance -Zach

---

### Post by Drum Pan Sound on 2012-04-20
...I apologize in advance if I got your hopes up when you first see a response, but I'm having the same problem, kinda - total noob here.

I'm trying to setup an old computer with xubuntu 11.10:
     Dell Dimension 4550
     nVidia graphics card

     I've got a 17" dell LCD monitor that tells me the optimum resolution is 1280X1024.  My options in display settings were 640x480 and 320x240, but after the following command line entries, I have 1280x1024 as an option that doesn't do anything:

```
teos@teos-Dimension-4550:~$ cvt 1280 1024 60
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
teos@teos-Dimension-4550:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr: Failed to get size of gamma for output default
teos@teos-Dimension-4550:~$ xrandr --addmode default "1280x1024_60.00"
xrandr: Failed to get size of gamma for output default
```

The nVidia X Server settings says "Unable to load X Server Display Configuration page:
Failed to query NoScanout for screen 0." under the 'X Server Display Configuration' menu item.

I've tried all available drivers in the 'Additional Drivers' tool.

The cool thing is I'm using Linux now even though the resolution is a P in the A.

Any help or guidance is more than welcome!

-dps

---

### Post by Drum Pan Sound on 2012-04-21
Zachiryus,

Check out:

**11.10 not working properly with NVIDIA drivers**
[http://ubuntuforums.org/showthread.php?t=1869917&highlight=Unable+load+Server+Display+Configuration](http://ubuntuforums.org/showthread.php?t=1869917&highlight=Unable+load+Server+Display+Configuration)

I was able to get a better resolution following this post:

 				 				**Re: 11.10 not working properly with NVIDIA drivers** 			
 			 			 		   		 		 		log out, 
log in gnome classic, 
install latest nvidia (current-17:cool:, 
reboot, log back in gnome classic, 
set your displays
log into gnome3 or unity
rejoice :smile:
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11798247") 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=11798247")
Thanks [munzerelli]("http://ubuntuforums.org/member.php?u=1308745")!!!!!!!111!1!!11!!11!

kthnx
-dps

---

### Post by idoitprone on 2012-04-21
> **Zachiryus said:**
> I installed ubuntu 11.10 and right away i realized that the resolution was off. after a while of looking around i found a thread about xrandr. when i attempt to change the resolution settings i get a "Failed to get size of gamma for output default"
Please help. thanks in advance -Zach

```
xrandr -q
``` get info on all displays
?
to change the resolution

```
xrandr --output NAMEOFDISPLAY --auto
```

most laptops use LVDS1

```
xrandr --output LVDS1 --auto
```

---

