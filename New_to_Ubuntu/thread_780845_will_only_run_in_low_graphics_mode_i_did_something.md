---
title: "will only run in low graphics mode i did something stupid help!"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by aceramicbunny on 2008-05-03
i was trying to get my computer to run througha different monitor, and i went into screens and graphics and changed the default and it went nuts, and now when i try to get it to run through the regular monitor it only runs in low graphics mode because it says it isnt dedecting it right or something. i totally screwed up and miss my graphics HELP!

---

### Post by RequinB4 on 2008-05-03
You may just need to re-install the proprietary drivers.  Try System - admin - hardware drivers, once you're sure it's back to the regular moniter.

---

### Post by aceramicbunny on 2008-05-03
you mean restricted drivers? thats the only thing i see that resembles what you said.
system-admin-restriced drivers

---

### Post by RequinB4 on 2008-05-03
Yes.  It is hardware drivers in Hardy Heron (8.04), but older versions are called Restricted Drivers Manager.

Hopefully that will fix the problem, assuming you didn't completely mess stuff up trying to get the other monitor to work.

---

### Post by aceramicbunny on 2008-05-03
hate to sound like a total noob, but how do i reinstall them? all i see enable and disable.

---

### Post by RequinB4 on 2008-05-03
No problem:  Check "enable" - if there is more than one, the one that corresponds to your graphics (graphics driver) is the one you need.  Any others should not be enabled/disabled if you are happy with how the rest of your system works :)

Edit:  It should tell you to reboot afterwards.  Do so.

---

### Post by Cap'n Redbeard on 2008-05-03
Hi aceramicbunny,

Or, you could try:

> sudo displayconfig-gtk

from the command line.

Please read the warnings about complete strangers getting you to run dodgy commands that destroy your computer before trying this. :)

On this one, it would only start up in 800 x 600 and system/preferences/screen resolution offered that as tops.

"displayconfig-gtk" runs a great little programme which lets you choose graphics card, drivers and monitor type, resolution and refresh rate.

i am only a beginner at Ubuntu Linux, so don't trust anything i say.

However, on this machine (which used to be a Marconi Neptune 800 internet payphone, inherited when the factory in Chorley closed), i used the "displayconfig-gtk" app, set it to "generic VGA", chose this telly (Samsung SyncMaster 710n), set the resolution and refresh rate and it works fine.

Hope this helps,

---

### Post by aceramicbunny on 2008-05-03
ok, its enabled. rebooting now, wish me luck

---

### Post by aceramicbunny on 2008-05-03
no dice, when i boot up there is a black screen white text saying that various resolutions failed (i guess thats it trying to boot with the monitor?) and then it goes all crazy for a sec with green lines and weird images everywhere and then back to black with a message saying its booting in low graphics mode. is there anyway to force it back to the settings it had before i screwed everything up?

---

### Post by sam_delta on 2008-05-03
do what Cap'n Redbeard sayd, go into a terminal and type 

```
sudo displayconfig-gtk
```

and go into graphic card tab, and select the apropiate driver for your graphic card,
if you dont know which driver to choose, tell us your graphic card model, and we'll tell you which driver to use.

you can also change freq rate and resolution there, but you have to have the correct drivers, you can even test current settings in there.

restart and 
tell us how it goes, 
sam

---

### Post by aceramicbunny on 2008-05-03
id tell you the name of my graphics card, but i dont know. how do i check what it is?
im in the device manager but cant tell one thing from another, where would my graphics card be?
once again, appoligies all around for my utter linux noobness

---

### Post by sam_delta on 2008-05-03
post the output of 
```
lspci
```

sam

---

### Post by Cap'n Redbeard on 2008-05-03
Hi aceramicbunny,

Don't really matter what's yer graphics card for now, when you find out which it is you can select the proper driver &c.

Try "generic vga" for now, as all video driver cards have to be able to work that way.

See if your monitor type comes up in the list, choose a resolution and sync rate you know will work.

If you choose either resolution or sync too high, the display will be all jumbled up and illegible.

If that happens, re-boot and go down one arrow to select the Linux equivalent of safe mode and run "sudo displayconfig-gtk" again and try another sync/resolution.

When you know which graphics card yer've got, set it up as above.

Let us know how you get along, eh ? :)

---

### Post by angin on 2008-05-03
im totally n00b in ubuntu, but from my experience playing with this OS for few months, i found that ubuntu will always make a backup of xorg.conf everytime the display or driver config changed. try to find your old xorg.conf and restore it.

if im not wrong, you can find it in /etc/X11/
you may will find some of xorg.conf* just say xorg.conf1 xorg.conf2 etc. just delete your current xorg.conf and rename the backup file to xorg.conf. try it...hope this can help you. sorry for my bad english.

---

