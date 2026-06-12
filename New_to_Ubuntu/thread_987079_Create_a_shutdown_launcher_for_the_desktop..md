---
title: "Create a shutdown launcher for the desktop."
date: 2008-11-19
forum: New to Ubuntu
---

### Post by too_funky on 2008-11-19
I want to create a desktop icon that if clciked will shutdown the computer. Iv created a launcher and have found the shutdown icon for it, but im stugling with what to put as a command to make the computer shut down.

I apologise if its an obvious question but im stuck:confused:

thanks

---

### Post by philinux on 2008-11-19
shutdown -h

See
 ```
man shutdown
```

---

### Post by LeAstrale on 2008-11-19
As far as I know you need to be root to use the shutdown command. So I would go for "sudo shutdown -time now -H"

/LeAstrale

---

### Post by too_funky on 2008-11-19
yeah iv tried putting that, but nothing happens when i click the launcher.

---

### Post by Sarmacid on 2008-11-19
Try with gksu instead of sudo. I usually use *shutdown -P now*, so you might want to give that a try too.

---

### Post by Bodsda on 2008-11-19
try this script

```

#! /bin/bash

sudo -k
gksudo shutdown -h now
```

Use -h, -H or -P depending on what you want, see ```
man shutdown
``` for details
the sudo -k resets the sudo timer, and gksudo is graphical sudo, make sure after you make the script you make it executable like this

```
 sudo chmod a+x /path/to/script/your_script 
```

Bodsda

---

### Post by too_funky on 2008-11-19
thanks sarmacid, the gk bit seemed to do the trick, is there a way though so you can excute the comand without typing the sudo password, like a save password thing, or how would i set up a no password flag?

---

### Post by philinux on 2008-11-19
You would need to modify the sudoers file. Here be dragons.

[http://ubuntuforums.org/archive/index.php/t-342763.html](http://ubuntuforums.org/archive/index.php/t-342763.html)

---

### Post by too_funky on 2008-11-19
oh dear, as philinux will tell you hes allready helped me with a no power down after shutdown issue, which i fixed by adding acpi=force to the grub, but after tryng the new shutdown launcher it hung up again and wouldnt power off after shutting down:(

---

### Post by Bodsda on 2008-11-19
> **too_funky said:**
> oh dear, as philinux will tell you hes allready helped me with a no power down after shutdown issue, which i fixed by adding acpi=force to the grub, but after tryng the new shutdown launcher it hung up again and wouldnt power off after shutting down:(

Which switch did you use for the shutdown command?

-P

would be the way to go for a script

---

### Post by too_funky on 2008-11-19
for the command i have,

gksudo shutdown -time now -P

then comes up with ''would your like you screen grabbed whilst you enter password'' then i enter sudo password, then xubuntu shut down screen appears and then hangs up.

---

### Post by Bodsda on 2008-11-19
I don't know why your using the command like that, try

```
gksudo shutdown -P now
```

---

### Post by too_funky on 2008-11-19
that command has the exact same effect, it comes up with xubuntu screen with a blue bar that expands from left to right, the bar then hangs up just before the it would reach the end. then have to power off manually and when i turn it back on, before it can boot up trhe bios has to erase my ram memory and reprogramme it or soemthing??? then boots as normal

---

### Post by too_funky on 2008-11-19
however if i shut down via the normal way via the taskbar, then it comes up with an xubuntu screen with a a full blue bar that shrinks from left to right and shuts down as normal

---

### Post by too_funky on 2008-11-19
is there a way to find the command or script or whatever that the task bar shutdown method uses and copy it for a desktop launcher?

---

### Post by philinux on 2008-11-19
Forgot to ask, why do you need this?

---

### Post by too_funky on 2008-11-19
fair enough question, im trying to sort out my grandpa with a computer he can very easily use. All he wants to do is type, he gets easily confused, the more menus there are, the more buttons to click, even things like forgetting to double click can make him come unstuck. I just want to have 3 launchers on the desktop, one for abiword, which iv done, one for a link to a folder where he can save his work, and another one to shut down. No other menus or options to confuse him and no way for hin to do something by accident and easy to remember what to do.Sseems to be the simplest soultion to me.

More info [http://ubuntuforums.org/showthread.php?t=986017](http://ubuntuforums.org/showthread.php?t=986017)

infact i think you commented in that thread too, so thanks for the all the help so far

---

### Post by philinux on 2008-11-19
In that case having the one normal shutdown button on one panel seems the way to go. He'll soon get used to it as it would be, by the sound of it, the only icon in the panel.

---

### Post by too_funky on 2008-11-19
yeah, your probably right, seems like too much hassel trying to get a launcher to work, how can i completely remove the bottom panel then? i want to move the top panel to the bottom of the screen in place of the bottom panel. then add a task list to it.

---

### Post by Sorivenul on 2008-11-19
> **too_funky said:**
> yeah, your probably right, seems like too much hassel trying to get a launcher to work, how can i completely remove the bottom panel then? i want to move the top panel to the bottom of the screen in place of the bottom panel. then add a task list to it.

Not logged into an Xfce session right now, but you should be able to right click the panel you want to remove, and choose and option like "Configure Panels".  This should bring up a simple interface.  Select the panel you want to remove (make sure, but it is likely Panel 2), and click the "minus" button next to it.  Done.  To add a task list to the remaining panel, right click it, select "Add" and find what you wish to add.

Good luck!

---

### Post by too_funky on 2008-11-19
never mind, done it:)

---

