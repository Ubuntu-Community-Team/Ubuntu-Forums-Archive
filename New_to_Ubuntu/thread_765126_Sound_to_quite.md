---
title: "Sound to quite?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Bleak Outlook on 2008-04-24
at first i thought i had no sound at all but after turning my speakers and volume in the taskbar all the way up i found that i do and it works fine

but its way to low im wondering if there is some way to turn the sound up?

i see lots of posts with people needing help with no sound at all
so i feel a little bad for my complaining
but im dual booting i forgot about my sound issues and nearly blew my head off when i went back to windows briefly 

thanks for any help

---

### Post by hotstyle765 on 2008-04-24
> **Bleak Outlook said:**
> at first i thought i had no sound at all but after turning my speakers and volume in the taskbar all the way up i found that i do and it works fine

but its way to low im wondering if there is some way to turn the sound up?

i see lots of posts with people needing help with no sound at all
so i feel a little bad for my complaining
but im dual booting i forgot about my sound issues and nearly blew my head off when i went back to windows briefly 

thanks for any help

If using GNOME try right clicking on the volume button on the top right and click open volume controls. See if making any adjustments in there help. There might be a device you can add it its prefrences called PCM. 

Sorry I am not so detailed in the instructions I am writing this from memory.

---

### Post by kansasnoob on 2008-04-24
Point to: System > Administration > Synaptic package manager, then open Synaptic. If you haven't been in Synaptic yet I'd click on reload and then see if there are any upgrades available (it'll tell you in the bar at the bottom of the screen) and if there are upgrades available I'd accept them by clicking on Mark All Upgrades ............

Then click on Search and type in: alsamixer

You'll likely see 3 items listed with alsa-utils already installed as indicated by a "green box". Now, 90% of the time I've found that installing "gnome-alsamixer" gives me the adjustments I need to solve the problem, so tick on the box next to "gnome-alsamixer" and the package manager will ask you if you want to install it .............. yes, you do! (it's removable if it doesn't solve the problem)

When you're done just click on Apply. When the installer is done just close synaptic.

Now go to Sound&Video and you should see Gnome Alsamixer in the menu, just open it and adjust away! Usually one of the last four toggles will let you increase the proper output.

If not we have dozens of options left.

---

### Post by Bleak Outlook on 2008-04-24
> **kansasnoob said:**
> Point to: System > Administration > Synaptic package manager, then open Synaptic. If you haven't been in Synaptic yet I'd click on reload and then see if there are any upgrades available (it'll tell you in the bar at the bottom of the screen) and if there are upgrades available I'd accept them by clicking on Mark All Upgrades ............

Then click on Search and type in: alsamixer

You'll likely see 3 items listed with alsa-utils already installed as indicated by a "green box". Now, 90% of the time I've found that installing "gnome-alsamixer" gives me the adjustments I need to solve the problem, so tick on the box next to "gnome-alsamixer" and the package manager will ask you if you want to install it .............. yes, you do! (it's removable if it doesn't solve the problem)

When you're done just click on Apply. When the installer is done just close synaptic.

Now go to Sound&Video and you should see Gnome Alsamixer in the menu, just open it and adjust away! Usually one of the last four toggles will let you increase the proper output.

If not we have dozens of options left.


thanks for the info that seemed to sort it
not as loud as i would like but very respectable

thanks greatly now to :guitar:

---

