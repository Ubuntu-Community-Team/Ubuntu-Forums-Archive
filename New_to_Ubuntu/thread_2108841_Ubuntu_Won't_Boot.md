---
title: "Ubuntu Won't Boot"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by Mortarius on 2013-01-25
So I recently I changed from Ubuntu 12.10 to 12.04 due to driver compatability and I've run into a problem. 12.10 would boot up just fine, but 12.04 will boot until I get to the login screen, once there I will input my password and hit enter. Next all I get is the desktop wallpaper and a cursor, nothing more. I don't know what to do but it seems that everything is against me using and learning Ubuntu.
 
Thanks
 
*edit* So I booted into Recovery and ran a file checking option. After it finally booted up, but everything is extremely slow. Opening the software center took me about a minute or two. I also see that my graphics is 'unkown'.

---

### Post by Double.J on 2013-01-25
Hi there, try resetting unity ALT + F2

```
unity --reset
```

Hope it helps!

---

### Post by grahammechanical on 2013-01-25
Hi

As for this

> graphics is 'unkown'.

that is standard for 12.04 and I think 12.10. The Details page gives us more accurate information about our graphics adapter in 13.04.

As for the other problem - I suggest trying another video driver. In 12.04 you will be able to change video drivers with the Additional Drviers utility.

I am curious. Did you re-install 12.04 formatting the / partition as you did so?

Regards.

---

### Post by Double.J on 2013-01-25
When you say opened software centre, are you now able to load the full desktop on a normal boot? If so you don't need to reset unity.

---

### Post by Mortarius on 2013-01-25
This seems to have helped with opening programs, I was on Firefox for a minute googling how to update my video drivers and all of a sudden the screen went black, I still have the dashboard on the left and the taskbar at the top and moving the mouse it will change to a typing cursor and back as Firefox is still open, it's just black.

---

### Post by Mortarius on 2013-01-25
> **grahammechanical said:**
> Hi
 
As for this
 
 
 
that is standard for 12.04 and I think 12.10. The Details page gives us more accurate information about our graphics adapter in 13.04.
 
As for the other problem - I suggest trying another video driver. In 12.04 you will be able to change video drivers with the Additional Drviers utility.
 
I am curious. Did you re-install 12.04 formatting the / partition as you did so?
 
Regards.
 
I did format when I reinstalled, and I just found the additional drivers and I am activiating some now to see if this helps.

---

### Post by Mortarius on 2013-01-25
> **gnu/mirow said:**
> When you say opened software centre, are you now able to load the full desktop on a normal boot? If so you don't need to reset unity.
 
This is still after using recovery, I believe it did a normal boot. After the reset I am getting a lot of graphical issues, the windows are flickering or not even visible until I mouse over an icon. So I am trying to activate ATI/AMD proprietary FGLRX graphics driver (post-release update) and see how that helps.

---

### Post by Bucky Ball on 2013-01-25
The post-release update has always crashed my system while the regular one works fine. If I have them both installed at the same time I get problems.

---

### Post by Mortarius on 2013-01-25
> **Bucky Ball said:**
> The post-release update has always crashed my system while the regular one works fine. If I have them both installed at the same time I get problems.
 
Alright, thanks I tried cancelling it and then it just sat there so I restarted and will try the regular ones if I can get the computer to boot up again.
 
*Edit* So I restarted the computer and did a normal boot and I am stuck at the same screen again. Just the desktop background and a cursor, nothing else.
*Edit 2* So did recovery and ran fschk again and it booted. It fixes something everytime, something about a ' time is set for a future date'. I am downloading and installing the regular ATI/AMD proprietary FGLRX graphics driver.

---

### Post by Mortarius on 2013-01-25
Well I got a little farther, after installing and updating the drivers I was abe to boot up a little farther. It took about 7 minutes and now it seems to be frozen again. I logged in and I am left with a movable cursor, desktop background, and the buttons on the left side which are unclickable. The taskbar at the top doesn't display any of the options on the top right (Wireless, Bluetooth, Logout, etc..), it only says Ubuntu Desktop on the far left. Also during the long boot there were multiple black screens.

---

### Post by Bucky Ball on 2013-01-25
Try this if you are getting to the menu list at boot (if not hit shift after the BIOS screen).

Highlight the kernel you want, hit 'e' to edit, find the line that ends with 'quiet splash' or either of those words, after a space add 'nomodset', follow instruction at bottom of page to save changes at boot.

This won't fix your problem but might get you in so you can have a better chance of a fix with a normally operating system. That change will also be lost on reboot.

---

