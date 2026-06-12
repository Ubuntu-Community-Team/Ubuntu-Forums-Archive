---
title: "WINE and my graphics card..."
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Omegaomni on 2008-11-16
[http://s392.photobucket.com/albums/pp3/Omegaomni313/?action=view&current=fixed.jpg](http://s392.photobucket.com/albums/pp3/Omegaomni313/?action=view&current=fixed.jpg)

^^^this is my WINE with no restricted graphics drivers turn on^^^

[http://s392.photobucket.com/albums/pp3/Omegaomni313/?action=view&current=Broken.jpg](http://s392.photobucket.com/albums/pp3/Omegaomni313/?action=view&current=Broken.jpg)

^^^and this is it with my graphics driver turned on...restricted of course...

is there any way to solve this?

because I intend to play games...and so far I cant knowing this is happening.:confused::(

---

### Post by Omegaomni on 2008-11-16
[http://i392.photobucket.com/albums/pp3/Omegaomni313/Broken.jpg](http://i392.photobucket.com/albums/pp3/Omegaomni313/Broken.jpg)

^^^this is my WINE with no restricted graphics drivers turn on^^^

[http://i392.photobucket.com/albums/pp3/Omegaomni313/fixed.jpg](http://i392.photobucket.com/albums/pp3/Omegaomni313/fixed.jpg)

^^^and this is it with my graphics driver turned on...restricted of course...

is there any way to solve this?

because I intend to play games...and so far I cant knowing this is happening.

didnt get the title right the first time...sorry.

---

### Post by Steve1961 on 2008-11-16
Those links aren't working for me, they just take me to the main photobucket page

---

### Post by Omegaomni on 2008-11-16
damn....one sec.

---

### Post by overdrank on 2008-11-16
The links work fine in the original post 
[http://ubuntuforums.org/showthread.php?t=984174](http://ubuntuforums.org/showthread.php?t=984174)

Threads merged :)

---

### Post by Omegaomni on 2008-11-16
anyway...sorry for that...i get kinda confused 0_o

---

### Post by Steve1961 on 2008-11-16
From the look of it it might be a graphics driver issue rather than a wine one - although I'm no expert in wine.  Try describing in detail exactly what the issue is rather than just putting up links to jpegs, and also give information about the type of graphics card you have, what driver you're using, and whether these display problems affect your desktop generally, or just wine.  That way you stand more of a chance of getting help.

Also, just check that direct rendering is enabled.  Type this in a terminal:

glxinfo | grep rendering

---

### Post by Omegaomni on 2008-11-16
thanks much....one sec while i pull up the info....

GeForce2 MX/MX 400
and direct rendering is enabled...

if you didnt see the pictures then my WINE becomes distorted when the driver is activated and it becomes normal when de-activated the computer is restarted.

---

### Post by Steve1961 on 2008-11-16
Not sure what's going on there then.  Why don't you try installing something in wine and see if it affects installed programmes.

---

### Post by Omegaomni on 2008-11-16
sure

---

### Post by Omegaomni on 2008-11-16
well it doesnt affect program functionality...i just cant see any words clearly.
they get scrambled and fuzzy

---

### Post by Omegaomni on 2008-11-16
guess ill find a way to solve my problem on my own.

---

### Post by markharding557 on 2008-11-16
I had a corruption problem in wine a while ago on my debian installation i resolved this by installing an older ati video driver because as it turned out it was a bug in their driver

---

### Post by Omegaomni on 2008-11-16
sweet...ill be sure to try that out.

---

### Post by cariboo on 2008-11-16
WHich driver are you using? Is the latest legacy driver? or just the open source nvidia driver. A quick check would be to go to System-->Administartion-->Nvidia X Server Settings.

Jim

---

### Post by Omegaomni on 2008-11-17
96.43.09 driver version

---

