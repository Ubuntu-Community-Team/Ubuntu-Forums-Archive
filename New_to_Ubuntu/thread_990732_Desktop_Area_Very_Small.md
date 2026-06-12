---
title: "Desktop Area Very Small"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by kevvy on 2008-11-23
Just installed copy of 8.10 on an older (P4) Toshiba laptop. Everything went perfectly except that the desktop is tiny. it only uses about 2/3 of the screen, leaving a wide black border around the desktop. Any ideas?

---

### Post by joshedmonds on 2008-11-23
While I haven't come across this problem myself, it sounds similar to an issue I've had in the past with laptops and external displays that have a different resolution. Try fn-F5 (or the particular combo you'd use on that laptop to change to an external display), give it a second and if it doesn't work repeat a couple of times.

---

### Post by kevvy on 2008-11-23
No luck Josh. Fn keys don't do anything. Weird. Installed on my wife's laptop also, no problem with the display on hers.

---

### Post by eternalnewbee on 2008-11-23
This may sound silly, but have you tried adjusting height and width from the monitor itself?

---

### Post by ciscosurfer on 2008-11-23
I don't know about on a laptop, but my free-standing monitor has an auto/select button that self-corrects these types of issues.  Perhaps your laptop has a similar key combo or F-Key that could do the same.  Check with Toshiba's documentation for your particular model.

---

### Post by ciscosurfer on 2008-11-23
Could you post a screenshot of exactly what you are seeing. Press the PrtScn button, save the image, upload to your next post.  Thanks :-)

---

### Post by kevvy on 2008-11-23
The print screen only shows the area of the monitor that is being used, and not the black, unused area around it. This laptop has a 15" monitor. When I load Ubuntu, the usable, 'lit up' desktop measures 9.5" diagonally. The computer seems to think it has a 9.5" monitor. I rebooted Windows XP and the display is fine, full screen, everything is normal. Back to Ubuntu, the same issue.

---

### Post by kevvy on 2008-12-13
Here's a photo of my computer. I could not use a screenshot because it would only show the area of the screen being used, and not the unused area around it. I have looked for settings and preferences to fix this issue but had no luck. I used the same image of Ubuntu on another laptop (not mine) and had no problems. Any ideas?

---

### Post by kevvy on 2008-12-13
Bump...pureley out of desperation. See photo in last post. Thanks

---

### Post by theoldgit on 2008-12-13
I have had this a few times and the solution i found was to go to System - Preferences - Screen resolution (I think thats right from memory, im on a windows pc right now)

Then try selecting a different refresh rate, this somehow changes how much of the sceen is used, you can also try a different resolution too that can have an effect. If you are using a dual boot you could also use the same settings as windows and see if that works.
The refresh rate worked best for me though

TheOldGit

---

### Post by kevvy on 2008-12-13
I can change the settings but I can't save them because the bottom of the dialogue box is cut off. no way to scroll down to save.

---

### Post by dummyhead3 on 2008-12-13
In order to change your screen resolution, to , say, 1024*768:
1.go to Applications>Accessories>Terminal
2.type the following:
xrandr -s 1024*768
3.Press Enter

Your resolution should now be bigger and you can tweak it again through System>Preferences>Screen Resolution now that you see the bottom of the window.

---

### Post by kevvy on 2008-12-13
Thanks for trying. The desktop is now slightly larger, but I still have a good 1 1/4" black border around the desktop. It seems like the computer thinks the display is a very small monitor. Any more ideas?

---

### Post by CatKiller on 2008-12-13
> **kevvy said:**
> Just installed copy of 8.10 on an older (P4) Toshiba laptop. Everything went perfectly except that the desktop is tiny. it only uses about 2/3 of the screen, leaving a wide black border around the desktop. Any ideas?

That sounds like the resolution being used is lower than the native resolution of the monitor, and so it's only using part of the screen.

What is the native resolution of the monitor on your laptop, and what resolution are you using now? Is the native resolution listed in System -> Preferences -> Screen Resolution?

If you've changed the resolution or refresh rate using that tool, **Alt-A** is equivalent to hitting the _A_pply button.

You should also be able to set the resolution to your monitor's native resolution (once you know what that is) by modifying the *xrandr* command that dummyhead3 gave you.

---

### Post by kevvy on 2008-12-13
> **CatKiller said:**
> That sounds like the resolution being used is lower than the native resolution of the monitor, and so it's only using part of the screen.

What is the native resolution of the monitor on your laptop, and what resolution are you using now? Is the native resolution listed in System -> Preferences -> Screen Resolution?

If you've changed the resolution or refresh rate using that tool, **Alt-A** is equivalent to hitting the _A_pply button.

You should also be able to set the resolution to your monitor's native resolution (once you know what that is) by modifying the *xrandr* command that dummyhead3 gave you.

How can I find the native resolution? the choices in Ubuntu go up to 800x600 and that's the one I selected. In windows Its 1024x768. Can that b the difference?

---

### Post by CatKiller on 2008-12-13
> **kevvy said:**
> How can I find the native resolution? the choices in Ubuntu go up to 800x600 and that's the one I selected.

You'd look in the manual, or at the specifications for your laptop.

To get the appropriate resolution, you're also going to need to find out what graphics adaptor is in that laptop, and potentially install restricted drivers for it.

There are many, many posts on this forum about getting Ubuntu to detect higher resolutions (800×600 is a failsafe that will not damage any monitors, which is why it gets used when X can't work out what the resolution should be) but if you post your details here someone will walk you through the process.

---

### Post by Jackie999 on 2008-12-14
I have the same problem on my Toshiba. With 8.04 I was able to follow the instructions in this post:
[http://ubuntuforums.org/showthread.php?t=763964](http://ubuntuforums.org/showthread.php?t=763964) using ' sudo displayconfig-gtk' ...unfortunately that doesn't work with 8.10 so I'll have to find another way. If you figure it out - please post how :)

---

### Post by dummyhead3 on 2008-12-14
Ok, so open up the Trminal and type
xrandr
This will show you all the possible resolutions and refresh rates your monitor supports. I suggest you choose the highest resolution and the highest refresh rate and type:

xrandr -s <put your resolution here> -r <refresh rate here>


for examle, this is my result of xrandr on my PC:

Screen 0: minimum 320 x 240, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      50.0*    51.0  
   1280x960       52.0  
   1152x864       53.0     54.0     55.0     56.0  
   1024x768       57.0     58.0     59.0  
 [...]

So, if you were on my computer, you'd type this command:

xrandr -s 1280*1024 -r 51

So try it and inform us of the results.

---

### Post by dwasifar on 2008-12-14
Sorry, double-hit, forum server is having some proxy issues.  Real reply follows

---

### Post by dwasifar on 2008-12-14
I had a problem like this years ago in an old Toshiba laptop, and the solution turned out to be a BIOS setting, not an OS setting at all.

Not saying this will for sure fix it for you, but it wouldn't hurt to go check the BIOS to see if there are any resolution-related settings in there.

---

