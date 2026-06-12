---
title: "Laptop screen issues"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by ZOOstation on 2008-11-10
What does it mean when my screen does this?
[IMG]http://i35.tinypic.com/2rz8hab.jpg[/IMG]

---

### Post by keplerspeed on 2008-11-10
That looks interesting. When does this occur? on boot? after grub? when gnome loads?

---

### Post by ZOOstation on 2008-11-10
It happened once a long time ago, almost a whole year, shortly after replacing Windows with Gutsy. That time it was on startup. It rebooted normally on command and never appeared again. Because a burn of my old Windows desktop showed softly in the background I referred to it as "the Ghost of Windows."

Lately I've been having [a lot of problems]("http://ubuntuforums.org/showthread.php?t=972674") with my Intrepid upgrade (from Hardy) and its compatibility with my graphics driver, and the screen did this once or twice when shutting down to reboot. (It has an Ubuntu burn in it now, but it's so faint you can't even see it in the photos).

Right now I'm trying to redo the upgrade, but when I boot with the alternate cd and select "Install Ubuntu," "Check CD for defects," or "Rescue a broken system" it brings me reliably to this ghost screen.

Relevant specs:
HP Pavilion zd8000 ("Lappy")
3gHz Intel Pentium 4 HT
ATI Mobile Radeon X600

---

### Post by Coreigh on 2008-11-10
Does the screen function normally through the boot up? I mean can you see the BIOS information? Also does the LiveCD work normally? Is this only a problem for the OS on the hard drive?

---

### Post by ZOOstation on 2008-11-10
Yes, all of the above. Except I currently have no GUI when I boot from the hard drive (see the link in my last post), but the screen is perfectly functional.

---

### Post by Coreigh on 2008-11-10
What about the LiveCD not the alternate, does that one give the same behavior?

Another idea; when that ghost screen is up can you hit ctrl+alt+backspace. If X windows is running (with wrong driver or settings) those keys woult restart X. (ctrl alt +) or (ctrl alt -) would try alternate screen resolutions.

---

### Post by ZOOstation on 2008-11-10
No, the LiveCD runs perfectly fine. I boot from it in order to go online and look for help while my GUI on the hard disk is being a glitch.

The ctrl alt commands didn't seem to have any effect, which surprises me because it still recognizes ctrl alt del when it's in that state.

---

### Post by ZOOstation on 2008-11-11
For what it's worth, I fixed my GUI issues on the hard disk so this problem isn't pressing in any way now. But I'd still like to know why, so I can prevent it from coming back.

---

### Post by scprosser on 2008-11-11
Had the same thing happen to me today. Are you by chance on Hardy and using a Laptop with an Nvidia card? Happened to me when I enabled the Nvidia restricted drivers (Toshiba Satellite Pro 6100 btw). If this IS the case, reboot, hit Esc when offered the option, and run option to fix your XConfig (Last one on list) then reboot, you will go back to lo-res graphics and boot fine, then look for a solution to your graphics issue (I'm still looking)...if this is not the case, I hope it helps someone else.

---

### Post by Crafty Kisses on 2008-11-11
Try booting into recovery mode from the GRUB menu and at the prompt, reconfigure your X server.
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo shutdown -r now
```
Once it's rebooted and you are able to login once again, look in **System ---> Administration ---> Hardware Drivers** to see if your graphics card is on the list. Look for the proper driver for your graphics card. Don't forget to go into the BIOS to turn off the onboard graphic card controller first before you boot into the recovery mode from GRUB menu.

---

