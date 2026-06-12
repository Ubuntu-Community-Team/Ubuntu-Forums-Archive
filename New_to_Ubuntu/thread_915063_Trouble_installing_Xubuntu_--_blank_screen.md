---
title: "Trouble installing Xubuntu -- blank screen"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2008-09-09
Hello,

I recently picked up an old Dell Latitude CPX (I believe PIII 500mHZ, 256MB Ram, 6GB HD).  Here's what's going on:

-Pop in the disc & boot, select "Install Xubuntu"
-Loads various things
-Eventually, the screen goes blank--

When the screen goes blank the backlight is still on & there are sounds from the computer, i.e. CD reading & CPU Activity light on.  No text, though.  It seems to get stuck like this every time--what could this be?

---

### Post by kjohansen on 2008-09-09
you could try the alternative cd installer. the alternate is used for low resource computers.

> 
The Alternative installation CD provides an installer that is text-based rather than graphical. It is needed for installation on computers with less than 256 megabytes of RAM.

   1.Go to the Official Download Page
   2.Select the desktop edition you want.
   3.Choose the location that is closest to you.
   4.Most users should download Standard personal computer
       *If you have a 64-bit system, you can use 64bit AMD and Intel computers 
   5.Check the box labeled Check here if you need the alternate desktop CD
   6.Click the start download button.
   7.Burn the CD on to a blank disc. Please refer to the BurningIsoHowto page which describes how to verify and burn the ISO image properly. 


from [https://help.ubuntu.com/community/GettingUbuntu](https://help.ubuntu.com/community/GettingUbuntu).

---

### Post by schauerlich on 2008-09-09
> **beetlejuice_masterson said:**
> Hello,

I recently picked up an old Dell Latitude CPX (I believe PIII 500mHZ, 256MB Ram, 6GB HD).  Here's what's going on:

-Pop in the disc & boot, select "Install Xubuntu"
-Loads various things
-Eventually, the screen goes blank--

When the screen goes blank the backlight is still on & there are sounds from the computer, i.e. CD reading & CPU Activity light on.  No text, though.  It seems to get stuck like this every time--what could this be?

That computer has too low of specs to install Xubuntu. Even if you could convince it to install with the alternate CD, it would run too slow for comfort. Also, with a 6GB HD you wouldn't really have room for many of your documents. ~1-2GB, probably. I'd recommend DSL or Puppy linux for a computer like that.

---

### Post by beetlejuice_masterson on 2008-09-09
Thanks for the tips, guys.  I may have to get that alternate install disc (i'm downloading now).

However, I **am** convinced that xubuntu will run on my PC.  I've read a post or two by searching google about users who've installed xubuntu on a latitude cpx.

---

### Post by snowpine on 2008-09-09
> **beetlejuice_masterson said:**
> Hello,

I recently picked up an old Dell Latitude CPX (I believe PIII 500mHZ, 256MB Ram, 6GB HD).  Here's what's going on:

-Pop in the disc & boot, select "Install Xubuntu"
-Loads various things
-Eventually, the screen goes blank--

When the screen goes blank the backlight is still on & there are sounds from the computer, i.e. CD reading & CPU Activity light on.  No text, though.  It seems to get stuck like this every time--what could this be?

Hi, I have this exact same computer. I've successfully installed Xubuntu and Ubuntu on it (using the Alternate CD) and I'm currently running Crunchbang. You'll be fine--it is possible! :)

Here is a tip. When the Xubuntu CD first starts up, press F6. This will allow you to edit your boot options. Add the following to the end of the line of code:

```
all_generic_ide
```

This gets around a problem with Hardy not recognizing the swappable CD/floppy drive bay.

If that works, once you install the system, you can:

```
sudo nano /boot/grub/menu.lst
```

(or 'gksu mousepad /boot/grub/menu.lst'; I can't remember if Xubuntu includes Nano or not)

and manually add the 'all_generic_ide' to the end of the appropriate grub entry to make the change permanent.

Hope that works! Don't give up, because Xubuntu WILL run on that laptop.

ps I'm subscribed to the thread, so if you have any problems, I'll try my best to help you out.

---

### Post by beetlejuice_masterson on 2008-09-09
Alright, I've been letting the laptop sit for a few hours now and here's what's going on:

The screen is black with the backlight on and I've got a little "X"-shaped cursor that I can move around.  The HDD activity light is still intermittently flashing (every second or two) but it seems to have slowed down some.  What's going on?  Will the desktop show up & the rest of the install take place, or is the install D.O.A.?

Also--the cursor movement is jerky, as if the system were busy processing other stuff.

---

### Post by snowpine on 2008-09-09
> **beetlejuice_masterson said:**
> Alright, I've been letting the laptop sit for a few hours now and here's what's going on:

The screen is black with the backlight on and I've got a little "X"-shaped cursor that I can move around.  The HDD activity light is still intermittently flashing (every second or two) but it seems to have slowed down some.  What's going on?  Will the desktop show up & the rest of the install take place, or is the install D.O.A.?

Also--the cursor movement is jerky, as if the system were busy processing other stuff.

This suggests to me that you are still using the Live CD, instead of the Alternate CD like we suggested. :)

The Alternate CD is a text-based installer, it shouldn't have the X shaped cursor.

---

