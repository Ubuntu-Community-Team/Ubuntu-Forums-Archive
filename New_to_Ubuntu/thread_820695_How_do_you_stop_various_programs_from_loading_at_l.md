---
title: "How do you stop various programs from loading at login?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by canthus13 on 2008-06-06
I'm having problems with really long login times because Skype and Pidgin are autoloading at login.  It's not anywhere under autostarted apps in the settings manager.

--Me

---

### Post by sdennie on 2008-06-06
One thing you could try would be to close all running apps and then go to System->Preferences->Session.  On the third tab, you can choose to save the current session.

---

### Post by Duck2006 on 2008-06-06
Right click on the icon, click Preferences and turn it of within from there.

---

### Post by Hospadar on 2008-06-06
apps like skype and pidgin often have their own method for starting at login time.  Try poking around in their options menus, I'm pretty sure somewhere in pidgin and skype preferences you can control whether or not it starts up on boot.
Also, they may be using the old way of autostarting themselves which involves putting a link in some hidden folder in your home directory.  I forget exactly where this is because it's been a while since I used xfce, but I think it might be like ~/.xfce4/autostart or ~/.config/autostart or something like that.  If you can't make it happen through those application's options menus, try poking around your hidden folders in your home directory and see what you see.  Just be careful not to delete anything important, those folders are generally hidden for a reason.  Feel free to ask here if you have any questions

---

### Post by Bruce McGoose on 2008-06-25
I had the same problem..  just noticed that Pidgin was minimising to tray..
closed those and that stopped it.

---

