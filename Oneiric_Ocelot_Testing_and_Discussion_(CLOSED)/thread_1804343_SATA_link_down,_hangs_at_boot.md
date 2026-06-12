---
title: "SATA link down, hangs at boot"
date: 2011-07-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by paola123 on 2011-07-14
Currently I am using ubuntu oneiric (I know it's alpha...). Today I did an aptitude safe-upgrade to get some slightly newer versions of packages (hoping that some bugs might be fixed :-)) - the last safe-upgrade was some days ago (without problems). 

However the upgrade progress hangs at the point when some cups config files were installed. I canceled this and rebooted. Now it boots into a black screen, mouse and keyboard don't react. 

I tried to boot in recovery mode then it hangs at:

SATA link down (SStatus 0 SControl 300)

Any idea?

---

### Post by Quackers on 2011-07-14
Welcome to UF.
You may be better off asking for help in the Oneiric Ocelot testing section
[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=403](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=403)

Or click on the "report abuse" icon to the left and ask a moderator to move this thread to that forum.

---

### Post by paola123 on 2011-07-14
Thanks, I asked the moderator for moving the question.

---

### Post by paola123 on 2011-07-15
Any ideas?

---

### Post by dino99 on 2011-07-15
i have an old ich7 MB that was hanging at bios check sata devices; the workaround was to increase the time allowed to discover these chipsets (into bios)

---

### Post by Quackers on 2011-07-15
That's not an error that I've seen.

If you're on a desktop unplug and re-plug the keyboard and mouse. They may start working. If they do try ctrl+Alt+F1 and see if you can get to a text based login. If so login and run sudo dpkg -configure -a then sudo apt-get -f install I think it is.
See what is reported.

Also see above post :-)

---

### Post by paola123 on 2011-07-15
> **Quackers said:**
> That's not an error that I've seen.

If you're on a desktop unplug and re-plug the keyboard and mouse. They may start working. If they do try ctrl+Alt+F1 and see if you can get to a text based login. 
Also see above post :-)

I have a laptop.

---

### Post by Hobbes on 2011-07-15
something like this happened to me... yesterday my updates hung while they were being applied, though most seemed to have finished, then when I restarted (to complete upgrades, etc.) my laptop stops at the ubuntu + 4 orange dots screen with a message like "waiting for /" or "/ cannot be found" - press 's' to skip mounting or R for recovery terminal

so.... yeah that's not good.

---

### Post by paola123 on 2011-07-15
Perhaps it would be a good idea to post this bug on launchpad. However I don't know to which category it belongs to.

---

### Post by paola123 on 2011-07-16
> **Quackers said:**
> If so login and run sudo dpkg -configure -a then sudo apt-get -f install I think it is.
See what is reported.


Is it possible to do this from a live-cd?

---

### Post by dino99 on 2011-07-16
> **paola123 said:**
> Perhaps it would be a good idea to post this bug on launchpad. However I don't know to which category it belongs to.

ubuntu-bug linux

---

### Post by paola123 on 2011-07-16
> **paola123 said:**
> Is it possible to do this from a live-cd?

Ok, I did it via chroot. Now it boots into commandline - no graphical interface. I tried to do aptitude update, but get the error "too many levels of symblic links". Same for example for cd /var/lock

If I want to reboot, it stops and gives the WARNING: Unattendet-upgrade in progress during shutdown, sleeping for 5s

---

### Post by SushiR on 2011-07-16
> **paola123 said:**
> I tried to do aptitude update, but get the error "too many levels of symblic links".

Same here. No idea how to fix it...

---

