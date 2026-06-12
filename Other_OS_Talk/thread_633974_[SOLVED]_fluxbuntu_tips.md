---
title: "[SOLVED] fluxbuntu tips?"
date: 2007-12-07
forum: Other OS Talk
---

### Post by staticvoid on 2007-12-07
aloha


I just installed fluxbuntu :) I got my wireless working, my screen res and my claws mail configured.

woohoo so far!  :D

Now... about fluxbox, and fluxbuntu repositories...


**I tried installing stuff but it did not find the packages** e.g. audacious

**I hit alt f4 and instead of closing the windows it changes to "desktop four"** where can I change the keyboard shortcuts and is there a GUI for this so I can cheat :P

Thanks for you help guys! I'd a appreciate some links on using fluxbox and configuring it and stuff. 

its supa dupa faaast  :D

oh and one last thing: the Usplash loader looks bad. (Usplash?) its at the wrong resolution...is it Usplash? can I change it just like I would any old Usplash? in the config file?



ok, by for real,



Static VOID  :popcorn:  <<for you <3

---

### Post by cknight on 2007-12-07
Have you enabled any extra repositories?  This is probably why you can't find audacious.  Try uncommenting lines in your /etc/apt/sources.list file to see if it can find it now.

As for changing the key binding for Alt-F4, put the following in your ~/.fluxbox/keys file. (Don't forget to "reconfigure" (aka reload-config) after modifying your keys file for fluxbox to pick up the changes)
```
Mod1 F4                 :Close
```

There *is* a GUI helper for the keys file, but I recommend against using it as it can corrupt your keys file with bad entries which will cause your more trouble than its worth.

This howto will help you customize your keys file further if you are interested:  [http://ubuntuforums.org/showthread.php?t=617812]("http://ubuntuforums.org/showthread.php?t=617812").

For customizing the menu, this is howto you want:  [http://ubuntuforums.org/showthread.php?t=371144]("http://ubuntuforums.org/showthread.php?t=371144")

Not sure what USplash is, sorry...  Enjoy and give us a shout if you run into any problems.

---

### Post by staticvoid on 2007-12-08
Ok,

thanks for the pointer :) great links too.


ciao

---

### Post by xtrm_redbull on 2007-12-08
As I understands it fluxbuntu uses [SLiM - Simple Login Manager]("http://slim.berlios.de/") , not usplash, if thats what you mean.:)

---

### Post by cknight on 2007-12-08
> **cknight said:**
> Have you enabled any extra repositories?  This is probably why you can't find audacious.  Try uncommenting lines in your /etc/apt/sources.list file to see if it can find it now.

As for changing the key binding for Alt-F4, put the following in your ~/.fluxbox/keys file. (Don't forget to "reconfigure" (aka reload-config) after modifying your keys file for fluxbox to pick up the changes)
```
Mod1 F4                 :Close
```

There *is* a GUI helper for the keys file, but I recommend against using it as it can corrupt your keys file with bad entries which will cause your more trouble than its worth.

This howto will help you customize your keys file further if you are interested:  [http://ubuntuforums.org/showthread.php?t=617812]("http://ubuntuforums.org/showthread.php?t=617812").

For customizing the menu, this is howto you want:  [http://ubuntuforums.org/showthread.php?t=371144]("http://ubuntuforums.org/showthread.php?t=371144")

Not sure what USplash is, sorry...  Enjoy and give us a shout if you run into any problems.

I should have noted that you can't have the same key combo used for two different commands in your keys file, so you'll need to replace the existing command in your keys file which is bound to Mod1-F4 with the above.

---

### Post by meborc on 2007-12-08
> **xtrm_redbull said:**
> As I understands it fluxbuntu uses [SLiM - Simple Login Manager]("http://slim.berlios.de/") , not usplash, if thats what you mean.:)

i think he ment the usplash as the stopper watch with white background during the boot sequence? 

if so, one could try to install ubuntu-artwork, but this would probably overwrite all artwork related stuff (not sure, have not tried)

i simply modified the /boot/grub/menu.lst file so that no splash is shown during boot (just delete the "splash" option from the kernel line)

there is a active bug in the kernel so that you can not change the vga modes to higher with using vga=791 or other options... there is a fix available, try searching for vga and grub as thread titles, this should give you the answer

btw - running my fluxbuntu since RC came out... just a few known bugs with easy fixes (like adding .ivman folder for automounting usb drives etc.) ... i have now greatly modified the look and feel of the system, but overall fluxbuntu has been stone-stable :)

---

### Post by K.Mandla on 2007-12-08
You might also look to the [Fluxbuntu forums]("http://community.fluxbuntu.org") if you have questions specific to Fluxbuntu.

Of course, someone will probably refer you back here, so on second thought, feel free to ask! :lol:

---

### Post by staticvoid on 2007-12-08
hey guys,

thanks for all your help. yea, i'll check out fluxbunutu forums.

I love all these choices linux has to offer!!!

fluxbox is a quick windows manager.. just could use a little tweaking :D


sv

---

