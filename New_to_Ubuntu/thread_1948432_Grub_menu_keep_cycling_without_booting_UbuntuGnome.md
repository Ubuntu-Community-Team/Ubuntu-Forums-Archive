---
title: "Grub menu keep cycling without booting Ubuntu/Gnome"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by CompBio on 2012-03-28
Recently I've run into an intermittent problem with Ubuntu 11.04 (linux 2.6.38-13-generic) where the Grub menu appears and the 8-second timeout does not activate.  When I hit Enter to initiate the boot, the screen goes dark, the Acer screen appears and then it returns to the Grub menu.  The only way to shut it down is to hold down the power button.  (This is on an Acer Aspire 5736Z).

This happened about a week ago and I managed to find my way to another menu that eventually allowed me to boot.  After loading a bunch of diagnostic software and getting rid of some old distros the problem disappeared.  I was worried that the disk had bad sectors, but the diagnostics all seemed to show that it's in pristine condition.

Now the problem is back.  Can anyone suggest a way to fix it?  Is there a command from the 'c' command-line that I can use?

For now I'm having to use my tiny netbook to do everything.  It's better than nothing, but I'd like my "real" computer back!

Thanks...

---

### Post by forrestcupp on 2012-03-28
I guess with all of that messing around, you need to repair/restore Grub. One easy way to do that is by booting into an Ubuntu Live CD/USB and installing a graphical app called Boot Repair. Boot into your Live CD and open a terminal. The install the app by typing these commands:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
```
After it is installed, run it by clicking the Unity Dash button and typing Boot Repair.

This will help you repair or reinstall Grub by detecting all of the distros you have installed and setting it up properly for everything.

---

### Post by kc1di on 2012-03-28
you can try re installing grub by following this pages suggestions

[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")
or this

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by CompBio on 2012-03-28
Yes, boot-repair was one of the applications I downloaded last week.  I guess I just need to get a boot CD/USB before I can use it (my machines came with Ubuntu already installed).  I'll give that a try.  Thanks!

---

### Post by CompBio on 2012-03-28
Well, I tried creating an 11.04 USB boot drive (my netbook doesn't have a CD burner), but the laptop never recognized it -- it kept cycling through the GRUB menu as usual.  I'm going to try burning the distro to a CD using a machine at school (as soon as I can find the CDs buried in our basement).

---

### Post by CompBio on 2012-03-28
> **CompBio said:**
> Well, I tried creating an 11.04 USB boot drive (my netbook doesn't have a CD burner), but the laptop never recognized it -- it kept cycling through the GRUB menu as usual.  I'm going to try burning the distro to a CD using a machine at school (as soon as I can find the CDs buried in our basement).

My bad -- I screwed up creating the USB boot.  It now recognizes the boot drive, but when the installation program starts, the graphics are far too dim to see what I'm doing even if I shut out all the lights in the room.

My hair is concerned that I will start pulling it out soon...

---

### Post by CompBio on 2012-03-28
Success!

After turning off the laptop, I pulled out the USB drive and turned the laptop on again to make sure the screen was OK.  At the GRUB menu, I reinserted the USB while I mulled over what to try next.  I hit Enter on the GRUB menu (selecting the currently installed distro) and as it started, I pulled the USB out.

Voila!  It booted.  (WTF??)

I ran boot-repair immediately, which did its magic and provided me with a paste.ubuntu.com URL.  Now it seems to be booting normally.

I guess I'll run boot-repair after every update.  It seems like a hack, but if it works...

Thanks for your advice, folks!

---

### Post by kc1di on 2012-03-28
> **CompBio said:**
> Success!

After turning off the laptop, I pulled out the USB drive and turned the laptop on again to make sure the screen was OK.  At the GRUB menu, I reinserted the USB while I mulled over what to try next.  I hit Enter on the GRUB menu (selecting the currently installed distro) and as it started, I pulled the USB out.

Voila!  It booted.  (WTF??)

I ran boot-repair immediately, which did its magic and provided me with a paste.ubuntu.com URL.  Now it seems to be booting normally.

I guess I'll run boot-repair after every update.  It seems like a hack, but if it works...

Thanks for your advice, folks!
glad you got it working :)

---

