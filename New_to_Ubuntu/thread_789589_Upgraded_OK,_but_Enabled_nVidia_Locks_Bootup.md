---
title: "Upgraded OK, but Enabled nVidia Locks Bootup"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by GregA on 2008-05-10
Hello,

I upgraded Gutsy to Hardy and everything went perfect, until I saw the popup about restricted drivers being availabe (for older integrated mx4 chip).  Anyway, Ubuntu requires a restart after the nVidia install, and that's when the system basically stops during the re-start.

The screen displays "running local boot scripts" and hangs there.   At this point, I'd just prefer to get my gui back so I can disable the nVidia driver (or re-enable plain nv).

How can I get a basic gui back, or even finish boot-up to log-in and use some console commands to edit xorg?  (and what would that command look like?).

thanks for any help, this is the one PC I need for the job - - thanks!

---

### Post by Journeyman on 2008-05-10
have you tried booting into safe mode?

---

### Post by GregA on 2008-05-10
How is that done?  Do I need a Live CD?

---

### Post by Journeyman on 2008-05-10
when the grub menu comes up there should be an option to select the safe mode, you may have to hit "ESC" to access the menu (this happens on bootup)

If you have a live CD, you can mount your harddrive and edit the file that way too.

---

### Post by inportb on 2008-05-10
That would be recovery mode. Hardy has this "friendly" menu with an xfix option.

---

### Post by Sef on 2008-05-10
> when the grub menu comes up there should be an option to select the safe mode, you may have to hit "ESC" to access the menu (this happens on bootup)

Safe mode is called recovery mode.  Usually it is the second one down from the top.  Since you upgraded you likely will have 4 kernel choices (two from Hardy and two from Gutsy.)  You could try the Gutsy kernel and see if it works. If not, then try the recovery mode. It says recovery mode after the kernel.)

---

### Post by GregA on 2008-05-10
What an experience!

If I were a total windows to linux newbie, well, Ubuntu would be history.

I finally fixed the botched nVidia driver update (still am not sure why it failed, but it caused this system HPA250N with GeForce MX4 Integrated graphics to stop before the login prompt,. without a gui).

Anyway, having been through this before with a couple of other distros, I remembered I need to change the text in "/etc/x11/xorg.conf" in the display section of that file, from use "nVidia" to "nv".   BUT, in Ubuntu, it was harder for me to do that, than Mepis Linux, where their Live CD has a tool to do that automatically (one of Warren's proprietary apps).   But it's not hard to edit xorg, IF, you can even get to it (the file).

My first attempt to fix made this situation worse . . . it was to restart, and press ESC to get a menu to boot into a "recovery" mode.  Let me see, Ubuntu is not on par with many Linux distros re the capability or user friendliness of that limited set of options.   There is the choice to boot into root console, or have the system try to repair X automatically.   Well, that was a mistake, as it over-rode xorg with a file that had practically nothing in it, and booted to a 800 x 600 mode.

A bunch of other crappy things resulted which I won't bore anyone with, but I finally had to do "sudo gedit xorg.conf" and delete all the crap Ubuntu wrote to it, and then copy/paste an older backup xorg.conf.

Anyway, all is back to normal now, but I sure hope the Ubuntu developers look at the Mepis Live CD, and try to emulate it's key features for system recovery - - I would probably even re-install Mepis 7 but the future of that distro is so uncertain now - Warren is not updating Mepis, and is next to impossible to contact.  So, for better or worse, I can live with Ubuntu as it seems to get a little better with each version.

---

