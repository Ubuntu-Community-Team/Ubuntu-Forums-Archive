---
title: "Several Ubuntu Problems"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Laser Dude on 2008-05-03
I had a few problems with the update to 8.04.  I used update, from update manager.
[list=1][*]The updater added an entry for Ubuntu to GRUB, even though one already exists.  I now have two links to Ubuntu in GRUB.
[*]Ubuntu doesn't detect my screen resolution right, so my screen was really really blurry (I changed the resolution manually), but the login window still shows everything in the bottom right corner.  Also, this has probably been mentioned before, but a lot of menus require a high screen resolution when they shouldn't.  For example (this was present on the 7.10 Live CD as well), when I load from the live CD, it detects my screen resolution as 800x600, I can't increase it in the screen resolution menu, and many of the screens (including the install menu) go off the page, and as such, are impossible to use without tabbing (I can see this being a major problem to people who actually do have small screens, or don't have much technical knowledge).  I'm fairly certain it's not my monitor, because I've used two different monitors with the same problem.
[*]The sound is really, really, choppy in VLC.  I've traced this to find that this is a problem with the visualizations, because turning them off yeilds good quality, but it still worked in 7.10.  Any ideas?
[*]Sometimes, when a password prompt comes up, and I enter the password and close it, the screen remains dark.  See the second attached screenshot.
[*]Go ahead and call me an idiot, but I cannot figure out the Tracker search tool.  Since it's a default tool, I assume it's worked for at least one person.  When I run a search, it brings up a list at the left side which tells me that it's found results, but it will not actually show me its results.  See the first screenshot.
[*] Audacity won't work.  It opens and imports sound files fine, but if I try to play, I get an error message: "Error while opening sound device. Please check the output device settings and the project sample rate."  I don't know what to check for...
[*]Most of the time my Emerald themes don't work, and I can't figure out why.  Sometimes they turn on, but I can't figure out what's triggering it.  This worked perfectly in 7.10.
[*]For some reason, Opera's been crashing a lot recently.  Does anyone who uses Opera know why this is happening?  In fact, it crashing caused me to lose this entire post.  :(  It's never crashed for me before, but since I installed Hardy it seems to crash about twice a day.
[*][SOLVED] (it recently occured to me that the name might have "gnome" in front of it.  The link was "gnome-control-center", as opposed to just "control-center") I accidentally deleted the link to my control center in the menu editor (oops!), how can I get it back?[/list]

Also, this isn't really related to Ubuntu, but does anyone know how to work around Windows Vista's shrink drive problems?  I've tried disabling page files, hibernate files, and all sorts of other things, but I'd like to remove 70GB, and it won't even let me remove 6GB, and errors out when I try.  If it comes down to it, I'll do a format, and partition, followed by a clean install of Vista, followed by a clean install of Ubuntu.  (You can probably see where this is going ;) )

I've had Ubuntu installed for just a few months now.  Everything else has been *awesome*, and I've gotten to the point where I rarely have to boot Windows Vista at all.  I think I've probably taken a bit more advanced approach than most beginners, but it's been a lot of fun.  It's given me an amazing impression of Linux in general.  Even Starcraft works better in Wine then it does in Vista!  :D

---

### Post by Alekth on 2008-05-03
I get Emerald themes disappearing fairly often. To reenable them I do alt+f2 (or terminal) "emerald --replace"

Too much of a newbie for the other questions^^ But when 8.04 upgrade installed Pulseaudio, sound became a problem for me so I removed it after failing to configure it into something working.

Maybe the tracker needs to reindex stuff.. then again it finds numbers.

---

### Post by Laser Dude on 2008-05-03
> **Alekth said:**
> I get Emerald themes disappearing fairly often. To reenable them I do alt+f2 (or terminal) "emerald --replace"

That works, but it only lasts until I close terminal or log out.  The solution I was looking for was to have it run whenever I log in.  It worked on 7.10, and the problem happened when I updated.

---

### Post by Laser Dude on 2008-05-08
Bump.

---

