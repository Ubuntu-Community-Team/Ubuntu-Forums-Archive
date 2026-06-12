---
title: "After making changes, Gnome desktop is blank with gray box"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by kkaitan on 2008-08-04
hi,

I've been using Ubuntu 8.04 for a few days. This morning, I went to change one of the colors in the Appearance control panel applet. I think it was the background color.

When I clicked "OK" to apply the changes, my system became unresponsive and all the windows grayed out (I think this is a Compiz effect to indicate busy windows). The appearance window stayed normal. I could move my mouse, but my desktop became completely unresponsive otherwise. It was suggested that I restart X with Ctrl-Alt-Backspace.

I did this. When I got back to the login screen, the resolution had been reset to the default 800x600. I logged in and my Gnome desktop is now completely blank except for a mouse cursor and doesn't appear to start anything. After about maybe 15-20 seconds of waiting, a blank gray box appears on the upper-left corner. Nothing further happens after about 10 minutes. If I start gnome-settings-manager from the failsafe terminal session (a suggested fix) I just get an error message saying it couldn't start.

I rebooted into safe mode and had it fix my X session defaults so that the resolution was back to normal. That part worked.

I made a new dummy user called 'failsafe' from the failsafe terminal session. If I log into this user, there's no issue - everything comes up beautifully.

What's going on here? Do I need to reinstall? That's really going to suck, I had everything almost working the way I wanted. This is a pretty frustrating experience! :|

---

### Post by philinux on 2008-08-04
If your working user has admin rights then use 

gksudo nautilus

browse to your non-working users home folder. ctrl h to show hidden files and then delete any starting .gnome

Then ctrl alt backspace or logoff and then try loggin in to your normal user.

These .gnome folders will then be recreated but set to default.

---

### Post by kkaitan on 2008-08-04
I backed up my .gnome* settings folders to new directories (beginning with .old-...) and deleted it. When I log out and in again, I get the same result. The folders are not recreated.

---

### Post by philinux on 2008-08-04
There are 3 directories that need to be deleted

.gnome
.gnome2
.gnome2-private

---

### Post by kkaitan on 2008-08-04
hi Phil,

Sorry, I wasn't clear in my previous message. I meant that I backed up all three of the directories you mentioned. They are still not recreated.

(I'll edit my previous message to reflect this.)

---

### Post by philinux on 2008-08-04
That usually does the trick.

Try a reboot.

Failing that I'd copy all your stuff to the user that works, always backup as well - delete the old user and rename the new one.

---

