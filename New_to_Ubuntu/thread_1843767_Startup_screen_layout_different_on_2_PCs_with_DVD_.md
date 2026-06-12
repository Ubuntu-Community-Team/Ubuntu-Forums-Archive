---
title: "Startup screen layout different on 2 PCs with DVD - 11.04"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-09-14
I've run the 11.04 DVD on my XP desktop and also on my Windows 7 Acer Laptop.   On the laptop I have the left menu icons by default and on the desktop the menuis at the top.

After rebooting each, any idea why the screen display would be different?  Is there a setting to change this?   I'm not sure which I like better.

Thanks.

---

### Post by LowSky on 2011-09-14
does the desktop gave a video card from nvidia or ati?

---

### Post by jtarin on 2011-09-14
As per the answer above your seeing the default layout for your graphics setup.....more than likely.

---

### Post by oscarivera9 on 2011-09-14
Easy answer.  What's going on is that the laptop obviously has a graphics card that allows for 3D acceleration and the desktop probably doesn't.  Ubuntu 11.04 uses Unity as the default desktop environment which needs 3D acceleration to run.  However, if you don't have 3D acceleration, then Ubuntu 11.04 will default to a Gnome desktop environment which doesn't need 3D acceleration.  I believe that's what the previous answers were trying to reference.

If you know for a fact that the desktop has a graphics card that should be able to run Unity, then go to the top to System>Administration>Additional Drivers and enable the proprietary driver that you need.  You may need to re-boot after installing the driver, after the computer restarts, you will most likely see that it looks the same as the laptop.

---

### Post by mastablasta on 2011-09-14
desktop needs additional drivers installed to be able to run the hardware accelerated desktop. While the laptop used the opensource drivers for it's card which were so good that they already enabled this function on it.

---

### Post by Denver Dave on 2011-09-14
Thanks for the replies

My older desktop without a left menu, is a Compaq Presario (XP) with a NVIDIA GoForce 6150 LE video card

My newer Acer Aspire laptop, with the left menu, but no bottom menu or status bar, has an Intel(R) HD Graphics card if I'm reading this right.

However, there is another directly related issue.  While researching why my desktop does not play sound (solved - old layout default to sound muted) with Ubuntu (does with XP and Knoppix), another thread suggested I do System -> Adminstration -> System Testing, which is easily done from from the top menu, select system

However, from the laptop (with the left menu), I don't have a system choice at the top - only file - view - places and help if I click on the desktop to remove the FireFox menus.

I'm also wondering if on the laptop with the left menu, if there is supposed to be a bottom status bar (there is none on my laptop).

On the laptop down the left menu, I have
- Install Ubuntu 11.04
- Home Folder
- FireFox web browser
- Libre Office, Writer and Calc
- Ubuntu Software Center
- Ubuntu One
- Workspace switcher
- Applications
- Files and Folders

*** but no system choice

- On the top left menu bar there is a left wheel for short-cuts
- On the right top menu bar there is an up down arrow icon for wireless connections (good to know)
- an icon for sound - says unmute - that's interesting, must default to muted on desktop - tried several times.   Wish ubuntu came with a sample audio file to - banshee mentioned, nothing playing on either desktop or laptop.  Install flash again on desktop - says software package called "adobe-flashplugin is not in my current sources, yet it installs it.  Try Youtube again .....

Sound now works fine on my Desktop - seems at least on my desktop the older menu defaults to sound muted.  Solved other thread. 

Back to screen layout Q - looking for system - 

-to the right of sound, mail
- to the right of mail
- to the right of time - ununtu chat accounts
- to the right of ubuntu chat accounts - logoff stuff, but also system settings (this might be useful)
- in the power off icon / system settings - nothing seems to happen when I click on system settings under power off icon.

<sigh> think I better test this again after a break and move the DVD back from the desktop to the laptop and reboot.

With the Unity menus where is the system menu supposed to be?

---

### Post by anewguy on 2011-09-14
You know, I'm using classic instead of Unity with 11.04, but I seem to remember it was all somewhere under applications - I think you have to click on a little text that says "Show all xx applicatons" or some such thing to expand it.  The classic menu is also in there, though I never clicked it to see where it put it.

Dave ;)

---

### Post by Denver Dave on 2011-09-14
Thank you for the reply, I did find the system menu under unity - it is under the extreme top right menu bar under the icon that looks like a power button.  (hid rather well)

I started out wondering why my desktop didn't have the unity menus.  Amazing that the screen display menu default is determined by by the video card - my desktop has a much bigger monitor.

I started out wondering how to get the unity menu on my desktop - now l wonder if it is possible to select?   And now I'm wondering how to revert from unity on the laptop to the classic.  I should probably practice with the unity some more, but it would be nice to have the option to have the same layout on my desktop and laptop,

I thought launcher and menus might be the way to change, but doesn't look like it.  Here's something:
[http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/](http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/)

Looks like can change with above, but might have to reboot which would not help if running from DVD?  Maybe time to do a USB installation anyway.  I know Knoppix has an install to USB Flash drive option, don't see anything here, but might have been on the startup screen where we picked the language - I know I saw this option on Desktop, will reboot the Laptop and see.  I was concerned I might install on hard drive by mistake.  I'll reboot and check.

Is there a way switch to classic menus me without rebooting (which won't work when using DVD)?   Any idea why video card is a factor in which menu to display? - seems rather strange.

Thanks.

---

### Post by anewguy on 2011-09-15
If you log out, then when you log on and enter your userid, before entering your password, look at the bottom of the screen.  There is a section there for session type - it might say Unity on your laptop.  Click this and select Ubuntu Classic either with or without desktop effects.

Ubuntu does have a USB option - I believe you have to look unetbootlin or some such program.  instructions for this can be found with a search in the forum, as it has been the topic of many threads.  You might also check at ubuntu.com and look for USB installation related things.  You may want to search for persistent usb installation in the forum - that's the way to have things "remembered" from 1 session to the next if booting from and using a USB device (flash drive, external disk, etc.) to boot and run the system.

As far as video cards, I believe it's already been mentioned:  it's a combination of the adapter chipset and the driver that has to be able to provide the video that Unity wants - I know you can have 2d Unity, but I don't remember how to get there - this was in the forum threads as well.

Dave ;)

---

