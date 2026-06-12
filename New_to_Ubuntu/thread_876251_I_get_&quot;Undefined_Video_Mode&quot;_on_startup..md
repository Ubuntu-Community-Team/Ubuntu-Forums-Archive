---
title: "I get &quot;Undefined Video Mode&quot; on startup..."
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Brightbelt on 2008-07-31
Hi,
  I'm on an HP dv9000 laptop. I know this problem started because I have installed a new usplash theme and I changed the resolution and bit-rate in the Startup Manager. (to the highest, 1600 x 1200/ 24-bit)

Now when I reboot, I get something very close to this on my startup:

```
Undefined Video Mode: 31f 
Press enter to choose from various video modes or press the space bar to continue.
```

So I press the space bar and I boot as normal and the usplash works fine and looks good.

Is there any way to remedy this?

I appreciate any suggestions,...

Many Thanks, Frank B.

---

### Post by phidia on 2008-07-31
is that "31f" part of an entry/edit you made to menu.lst?
if so comment "#" that out(well actually you may need to delete that stanza from menu.lst if it's there) and restart and see if that corrects the problem.

---

### Post by sisco311 on 2008-07-31
i think your video card doesn't support  the resolution.
list the available resolutions:
```
sudo hwinfo --framebuffer
```

---

### Post by daimaru on 2008-07-31
> **Brightbelt said:**
> Hi,
  I'm on an HP dv9000 laptop. I know this problem started because I have installed a new usplash theme and I changed the resolution and bit-rate in the Startup Manager. (to the highest, 1600 x 1200/ 24-bit)

Now when I reboot, I get something very close to this on my startup:

```
Undefined Video Mode: 31f 
Press enter to choose from various video modes or press the space bar to continue.
```So I press the space bar and I boot as normal and the usplash works fine and looks good.

Is there any way to remedy this?

I appreciate any suggestions,...

Many Thanks, Frank B.
I think usplash's maximum resolution is 
   vga=794 = 1280x1024

not too sure though :D

---

### Post by Brightbelt on 2008-08-01
Thanks guys for the responses - work got in the way of me responding back sooner.

I'll try some of your suggestions right now.

Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-08-01
Okay, I looked into menu.lst and '31f' is not there in the file to begin with. So I left the file as is.

Sisco, I ran ```
sudo hwinfo --framebuffer
``` and got an error directory around framebuffer.

Also, I use the Startup Manager for this and the resolution choices for Usplash seem pre-established in a drop-down menu. And 1600 x 1200 is the largest choice. 

And I can tell you that 1600 works, since I see the difference after having tried the 1280 x 1024 resolution.

I appreciate any other ideas...if any!

Many Thanks, Frank B.

---

### Post by pheonix7117 on 2008-09-08
I had the same problem, and following this post [http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=5377196&postcount=8](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=5377196&postcount=8) solved it for me. Give it a try and see if it works! :)

---

