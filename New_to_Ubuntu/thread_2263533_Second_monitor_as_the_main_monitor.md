---
title: "Second monitor as the main monitor"
date: 2015-02-01
forum: New to Ubuntu
---

### Post by Mr_Media on 2015-02-01
Hello,

I am trying to set up a second monitor (television) to be the main screen for an old laptop setup. There is no problem showing the Ubuntu image on both screens or simple one screen, but I would like it to always start showing on the second screen and not on both or just the main screen. 

I would like this because then I would not need to open up my laptop to change the the display settings (like find projector/second monitor). Later I will work on remotely wake up the PC and/or turn on without using power button.

Thank you! If you need me to be more clear, let me know.

---

### Post by Benjamin_Eunice on 2015-02-02
Go to the settings program and enter displays where you will find the settings for both screens. Can you tell me if you configured the screens or not?

---

### Post by mansonfan78 on 2015-02-03
Your laptop's bios may have a setting for primary display (internal or external).  If you haven't already checked, it couldn't hurt to try.

---

### Post by Mr_Media on 2015-02-04
Hej Benjamin and mansonfan,
I can get the screen to come up (either share screen, mirror screen, internal or external display), so there are no problems there. I have now set the Screen Display settings to turning off the internal display and turning on the external. With the launcher options I set Launcher placement to be placed on the external, though I do not think that should affect which screen should show up when I turn on the laptop. 

I am going to test the turn off/on now and see if it automatically goes to the external.

Edit: So when I restart the screen is extended so that the login screen is on the laptop and only after I log in does it change to just the external. This isn't that big of ett problem, but is not ideal. Any help would be appreciated. (with Edit2: If I have the laptop screen down then it only shows on external, which is the plan in the long run, so this is not a worry.)

I will check the bios then too.

Edit2: bios does not seem to have an option for this.

---

### Post by mansonfan78 on 2015-02-04
I believe the login screen (and splash screen before it) follow the display settings of the grub menu as opposed to the system settings once logged in.  Somebody more knowledgable in editing grub settings may be able to help with that, but considering how the smallest mistake in grub could seriously mess things up I won't recommend it.

---

