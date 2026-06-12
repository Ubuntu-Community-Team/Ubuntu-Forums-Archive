---
title: "Cannot change screen resolution"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by bigal1932flying on 2011-11-30
If I go to System Settings>Displays it says that Display is unknown and Resolution is 640X480 (4:3) I cannot change this so can someone please tell me what I can do. This large screen size is driving me nuts!

---

### Post by farrinux on 2011-11-30
> **bigal1932flying said:**
> If I go to System Settings>Displays it says that Display is unknown and Resolution is 640X480 (4:3) I cannot change this so can someone please tell me what I can do. This large screen size is driving me nuts!

What do you have for a video card?

---

### Post by creator101 on 2011-11-30
This happened to me before EXACTLY!! Here's what I did to solve the problem:

1. Type in the terminal ```
gksudo gedit /etc/X11/xorg.conf
``` and authenticiate.
2 Scroll down to Section "Screen" and add the following: ```
Viewport 0 0
 Modes "1280x1024"
``` Make sure it is typed EXACTLY.
3. Save and reboot. If it hangs on the splash screen, reboot and while it says your computer manufacturer hold down shift until the GRUB comes up. Then boot into an older kernel.

Hope that helps!:D

---

### Post by creator101 on 2011-11-30
Oh yeah, and make sure it is in subsection "Display"

---

### Post by bigal1932flying on 2011-12-01
Tried this command and seem to have  really stuffed things. After reboot all I receive is a Login Screen.What can I do now?

---

### Post by creator101 on 2011-12-01
your supposed to see a login screen! Log in and if the screen still doesn't look right you should now be able to change it in the settings.

---

### Post by bigal1932flying on 2011-12-01
Sorry, I didn't explain the problem correctly. The screen I receive is not the normal Login Screen but a Black Screen with White writing like a Terminal Screen. Which asks for Login Name and then Password, then goes to a command line. Sorry about that.
Any help would be appreciated.

---

### Post by bigal1932flying on 2011-12-02
I am three things, Old, stupid and impatient. So instead of waiting for an answer I booted from CD and selected "Upgrade from 11.10 to 11.10 keeping docs etc. after the usual wait it went to "will now reboot" but did not reboot. When I manually rebooted all I received was a pretty pink blank screen, so I booted from CD again hoping I would see something about repair installation but the only choice I could make was to install on a separate partition. I did this and it boots sort of OK, but when I installed the Nvidia Drivers I ended up with the same horrible screen resolution that started the problem.
Is there any hope for this old stupid guy?

---

### Post by lpuppy on 2011-12-03
Do you have any other video cards around that you can try?

---

### Post by BC59 on 2011-12-03
> **bigal1932flying said:**
> If I go to System Settings>Displays it says that Display is unknown and Resolution is 640X480 (4:3) I cannot change this so can someone please tell me what I can do. This large screen size is driving me nuts!

You should run ```
xrandr
``` to see what resolutions are supported from your computer.

---

### Post by sadaruwan12 on 2011-12-03
You have a display driver issue remove the nvidia drivers and install it from hardware drivers which will give you the better drivers to install.

---

### Post by bigal1932flying on 2011-12-03
Output from xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
Doesn't give me much choice does it.

---

### Post by bigal1932flying on 2011-12-04
Put hard drive in a friends computer and using his monitor I had several options and was able to change the screen resolution. So bought his computer home and connected to my wide screen. On startup a message came up saying that resolution settings could not be kept and then Ubuntu started with exactly the same resolution as I had before and once again when I went into display settings I could not make any change.

---

### Post by fantab on 2011-12-04
There are issues with 1280x1024 resolutions and Ubuntu... I don't exactly know what the bug is, however see [**my post from another thread**]("http://ubuntuforums.org/showpost.php?p=11503588&postcount=4").. and try to fix it by forcing the required resolution.

---

### Post by bigal1932flying on 2011-12-05
Thanks for going to the trouble to post this possible solution. I don't think I will try it however it sounds a bit too technical and complicated for me.
I did have to set a new resolution for my W7 system and the only resolution the monitor would accept was "1920X1080@60HZ. 
Thanks again but it looks as though it will just have to wait and see what happens.

---

### Post by bigal1932flying on 2011-12-05
Sorry I have put you to so much trouble as well as the anguish I have caused myself. I have been connecting my Ubuntu Computer via a VKM Switch and have only just discovered that if I connect it straight to the Monitor I have a choice of several Resolutions including the 1920X1080 that I had to set on my W7 Computer.
Thanks again for all your help!

---

### Post by burnsmicro on 2011-12-05
Check out posting #4 at "			 			[**boot-up: Cannot display this video mode**]("http://ubuntuforums.org/showthread.php?t=1888642&highlight=display+video+mode")" by Fantab on how to boot-up with the correct screen resolution.

---

