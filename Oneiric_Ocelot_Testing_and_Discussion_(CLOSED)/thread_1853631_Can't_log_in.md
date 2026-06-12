---
title: "Can't log in"
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by linuxman94 on 2011-10-02
I'm running oneiric with the latest updates and i cannot log into my account.  Once i type my password and hit enter, it returns me to the login after ~1 second.  I can, however, log in to the guest session fine.  It works fine in my virtual machine on windows vista.  Anyone else have this problem?

offtopic:  It's kinda unnerving to see this problem in beta 2

---

### Post by effenberg0x0 on 2011-10-02
Hey,

Switch to a VT with Ctrl+Alt+(F1 to F6). If it doesn't work (sometimes VTs are garbled / unusable), you can always boot and choose recovery mode in Grub (hold shift while booting to see Grub). 

Once you are in a VT, run:

sudo service lightdm stop
sudo mv ~/.Xauthority ~/.Xauthority.old
sudo reboot now

Try to login. Hopefully it will be fixed.

Regards,
Effenberg

---

### Post by linuxman94 on 2011-10-04
That fixed it, thanks.

---

### Post by QBX on 2011-10-06
Just wanted to give kudos where they are due - this handled it for me as well and I was rather pleased about that.

---

### Post by penguinmaster on 2011-10-06
This unfortunately does not fix it for me.  When I try to do the lightdm stop command the screen freaks out and I can't type in the rest of the commands.

For me it's almost like Unity and Gnome-shell are gone.  When I try to select which session I want to log into the two options I get are User Defined Session and Recovery Console.

I've done a reinstall of both Unity and Gnome-Shell with no luck.

---

### Post by cariboo on 2011-10-06
> **penguinmaster said:**
> This unfortunately does not fix it for me.  When I try to do the lightdm stop command the screen freaks out and I can't type in the rest of the commands.

For me it's almost like Unity and Gnome-shell are gone.  When I try to select which session I want to log into the two options I get are User Defined Session and Recovery Console.

I've done a reinstall of both Unity and Gnome-Shell with no luck.

You have to be in a console in order for the instructions to work, trying them in a terminal will fail.

---

### Post by penguinmaster on 2011-10-06
I am when I do that.  I go into console 1 (ctl+alt+F1), and when I type sudo lightdm stop it switches me back to the graphical login (Ctl+Alt+F7) with the console taking up half the screen in garbled type. I can then type in the commands I found out, but they do nothing in terms of giving me the sessions I need.  I'm still left with only the Recovery Console and User Defined Session.

If I click User Defined Session and login, which I can now do, it just boots me into a screen with just an arrow on it.  No Unity is booting up.

Thanks!

---

### Post by cariboo on 2011-10-06
> **penguinmaster said:**
> I am when I do that.  I go into console 1 (ctl+alt+F1), and when I type sudo lightdm stop it switches me back to the graphical login (Ctl+Alt+F7) with the console taking up half the screen in garbled type. I can then type in the commands I found out, but they do nothing in terms of giving me the sessions I need.  I'm still left with only the Recovery Console and User Defined Session.

If I click User Defined Session and login, which I can now do, it just boots me into a screen with just an arrow on it.  No Unity is booting up.

Thanks!

The command you are using is wrong it's:

```
sudo service lightdm stop
```

---

### Post by penguinmaster on 2011-10-07
That still does not work for me.  I've tried to do a reinstall of both lightdm and gdm (just to see if it was a lightdm issue), no joy.  Also have done reinstalls of both Unity and Gnome 3, no joy as well.  

Bit frustrating as I can't login to do any work!

-Tom

---

### Post by effenberg0x0 on 2011-10-07
My mistake: I did typed "sudo lightdm stop" instead of "sudo service lightdm stop" in my post. Sorry, always doing things in a hurry. But its sort of obvious anyway.

At any rate, I can't picture what you're seeing there (a garbled console taking half the screen, inability to use a VT, etc). And you mention playing with gdm, compiz, unity, installs / reinstall also - which makes me think this system is severely broken.

At this point, I think the best option for you would be to fully reinstall lightdm, unity, compiz and your video driver and purge gdm before proceeding with what I suggested in recovery mode. It's just a suggestion. You might choose a full reinstall if you don't have anything to lose and have spare time.

For a reinstall of this vital packages, you would have to do something like this:

Reboot and hold shift until you see the Grub menu. Select "Recovery" and drop to a Root Shell prompt with networking.

```

sudo service lightdm stop
sudo service gdm stop
sudo killall -s KILL /usr/bin/X
sudo apt-get remove --purge gdm gdm-guest-session
sudo apt-get update
sudo apt-get install --reinstall unity unity-2d-spread unity-lens-files unity-scope-musicstores unity-2d unity-asset-pool unity-lens-gwibber unity-services unity-2d-launcher unity-common unity-lens-music unity-2d-panel unity-greeter unity-place-applications unity-2d-places unity-lens-applications unity-place-files compiz compiz-dev compiz-kde compiz-plugins-main-default compizconfig-backend-gconf compiz-fusion-bcop compiz-plugins compiz-plugins-main-dev compizconfig-backend-kconfig compiz-fusion-plugins-extra compiz-plugins-default compizconfig-settings-manager compiz-fusion-plugins-main compiz-plugins-extra compiz-core compiz-gnome compiz-plugins-main lightdm lightdm-gtk-greeter lightdm-qt-greeter
sudo apt-get upgrade

```Don't forget to fix the main lightdm problem which brought you to this thread...
```
sudo mv ~/.Xautorithy ~/.Xauthority.backup
```At this point, you can give a try to lightdm (sudo service lightdm start) or reboot the system. I would reboot and check the system after. 
```
sudo reboot now
```If you still have problems, like the video weird stuff you have mentioned, I'd go for a complete purge of all video drivers and installation of the correct one for your card (which I don't know what it is: nvidia, ati, intel, etc). This is simple anyway and you'll find plenty of threads with detailed instructions. Don't use Jockey. Try to download and install video drivers yourself. Jockey is unreliable right now with some drivers.

**If you don't feel comfortable doing such procedure (it might make your machine unusable) or if you have important information that you can't afford to lose in this machine, do a backup first or don't try this at all. Testing is for people that can afford to break a machine and reinstall everything.**

Regards,
Effenberg

**EDIT**
Maybe you could post a screenshot of the screen you're seeing there when attempting to switch to a VT? It would make it easier for me, at least, to understand what might be going on there.

---

### Post by penguinmaster on 2011-10-07
Still not working for me.  I did a complete reinstall of the components listed above and now I'm back to the original issue we have at the top of the posts.  I try to login and within a second I'm booted right back to the login screen. When I click on the gear to select which window manager I want to use though nothing comes up at all, which is where I think my issue is coming.

To compound it even more, when I switch to a VT and try to do the mv command it tells me the file does not exist.  

As for the scrambled screen I've tracked that down to using the incorrect command to stop lightdm (which btw, I should have known too, but in my rush I was just typing exactly what I saw and getting flustered it wasn't working.)

At this point I'm seriously considering just doing a full reinstall.  I do daily backups of everything important so it's not super painful to do.  I'll wait for one more round of help (if you'd so oblige) and if that doesn't work I'll do that.

---

