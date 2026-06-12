---
title: "screens and graphics error"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-08-16
When I click on the icon for Screens and Graphics, nothing happens.
So I opened a root terminal and typed in the command manually.

$:  gksu displayconfig -gtk

Here are the results that appeared in Terminal:

Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 236, in __init__
    self._sync_screens()
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 551, in _sync_screens
    screen == gfxcard.getScreens()[1]:
IndexError: list index out of range


Does anyone have an idea how I can get Screens and Graphics  (displayconfig) to work?

Thanks

JBA2337

---

### Post by glennric on 2008-08-16
Have you tried reinstalling the package "dislpayconfig-gtk"?

---

### Post by JBA2337 on 2008-08-16
With Synaptics Package Manager I reinstalled displayconfig.gtk, rebooted my computer, and still when I click on Screens and Graphics icon I get a message in the lower panel that Screens and Graphics is starting, but after that nothing happens. Screens and Graphics will not open when I click on the icon, nor will it open when I use a Terminal command.
Any other ideas?

JBA2337

---

