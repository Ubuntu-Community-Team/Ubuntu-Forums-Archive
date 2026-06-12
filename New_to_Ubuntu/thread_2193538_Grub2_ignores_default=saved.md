---
title: "Grub2 ignores default=saved"
date: 2013-12-13
forum: New to Ubuntu
---

### Post by 6ejrpksjgj on 2013-12-13
Hello.

I am running a dual boot ubuntu 12.04 and windows 7 system. I am attempting to get Grub2 to boot the last booted OS as its default.

It is completely ignoring my efforts.

I have tried boot-repair. I have tried grub-customizer. I have directly editing /etc/default/grub. I have not attempted to directly edit the config file. Regardless of what I change, Grub picks the top menu entry when the menu times out. Yes, I have run update-grub when necessary.

Suggestions? I am an Ubuntu noob, but this shouldn't be that hard.

Thanks,
  ~aero2600

---

### Post by Dennis N on 2013-12-13
You must have both the settings **GRUB_SAVEDEFAULT=true** and **GRUB_DEFAULT=saved** for this to work.

See: [https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

---

### Post by 6ejrpksjgj on 2013-12-13
I have both of those in /etc/default/grub.

---

### Post by Dennis N on 2013-12-13
I will try it out and see how it works for me.

---

### Post by Dennis N on 2013-12-13
Results of test:

Settings in /etc/default/grub
```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
Confirmed your outcome. Didn't work properly for me either. Using above settings, ran update-grub, then rebooted and chose third menu entry. Rebooted again, and grub booted the first entry. 

Sorry, no further insights at this time.

---

### Post by 6ejrpksjgj on 2013-12-13
Anyone else have any suggestions? Should I ditch Grub2 for LILO?

---

### Post by squakie on 2013-12-13
I just tried this same thing - matching what was found in askubuntu and the wiki - and I can verify that those steps alone don't work for 13.04 either.  After running update-grub, rebooting, selecting and entry, shutdow/reboot, it sitll defaults to the 1st entry in my case.  I figured surely it has to store what was selected on the last pass through the grub menu, but using find I could not find any files that were changed.  Perhaps there is something missing.  I'll try reading the docs again and see if there is more to it that I can understand ("I ain't the sharpest knife in the drawer anymore" ;) )

---

### Post by squakie on 2013-12-13
Okay, some progress, but no solution:

In looing at the grub.cfg file, there are some things there for saving/restoring the default:

saved_entry  and prev_saved_entry and the functions up front to process those.  The previous grub menu selection is supposed to be saved in the /boot/grub/grubenv file - the top most line - and points to the string representing the menu option as defined in the grub.cfg file.  For me, the entry in grubenv is not being modified.  I manually changed the string there to match another option in grub.cfg and upon reboot (DON"T run update-grub if testing this as it regens the file!) and then indeed the default on the grub menu shows as the entry in the grubenv file.  I had a "small" problem - I assume something to do with what I was testing - in that selecting normall boot resulted in some message about a block sizing problem and it took a while to reboot.  I then ran sudo update-grub to reset evertyhing back from my testing.

There are a couple of things that come to mind:

- the program that is actually running when it reads grub.cfg apparently uses the statement loadenv to load the variable from the grubenv file.  There are some statements there that apparently tell the program to set the saved_entry to what was read, and wherever prev_saved_entry is coming from can also replace it.

- program also appears to use saveentry (not sure of the exact command as I've closed the file already) to supposedly save the entry when you selected one from the menu.

I suspect that somehow this "saveentry" causes the program to execute some code to save the selection to the grubenv file, so perhaps the name of the command is misspelled or perhaps the internals of the code aren't working for the save.

Now, I could be wrong about all of this.  I have no clue what program is running (like is it actually called grub??) that is reading the grub.cfg file, so I can't look at the source and see if I can even understand it enough to see what it does with those options.

---

### Post by sammiev on 2013-12-13
> **6ejrpksjgj said:**
> Hello.

I am running a dual boot ubuntu 12.04 and windows 7 system. I am attempting to get Grub2 to boot the last booted OS as its default.

It is completely ignoring my efforts.

I have tried boot-repair. I have tried grub-customizer. I have directly editing /etc/default/grub. I have not attempted to directly edit the config file. Regardless of what I change, Grub picks the top menu entry when the menu times out. Yes, I have run update-grub when necessary.

Suggestions? I am an Ubuntu noob, but this shouldn't be that hard.

Thanks,
  ~aero2600

I noticed this as well but never had time to look at all the details. So now I can watch on as I play with other things. I usually have a few configs and thought I maybe affecting one from another.

---

### Post by squakie on 2013-12-14
I have a question:  when any of you have tried this using the 2 commands for /etc/default/grub and running update-grub, when you reboot and select a menu entry does it give you a message about environment block too small and wait for you to press a key befoire continueing on with the boot?

---

### Post by Dennis N on 2013-12-14
> **squakie said:**
> I have a question:  when any of you have tried this using the 2 commands for /etc/default/grub and running update-grub, when you reboot and select a menu entry does it give you a message about environment block too small and wait for you to press a key befoire continueing on with the boot?

I had no messages (error or any other) appear at any time during my test. See post #5.

---

### Post by squakie on 2013-12-14
I know I never got it until I manually changed the grubenv file - don't do it by the way - to do some testing.  If you're interested, I have another thread on the grub2 source code where I've added a couple of new comments:

[http://ubuntuforums.org/showthread.php?t=2193617&p=12873659#post12873659](http://ubuntuforums.org/showthread.php?t=2193617&p=12873659#post12873659)

---

### Post by Dennis N on 2013-12-15
@squakie,
Sorry to read you messed up your grub exploring this. This problem exists in Grub 1.99 as well, so should affect releases back to 11.04. Even further if it affected Grub 1.98. I now see a new bug report on it. I also don't use the settings we tested.

---

### Post by squakie on 2013-12-15
Yeah, I think with the bug report I'm going to go ahead and stop working on it.  That code is pretty difficult for me to follow, but I'm sure it is a bug in the program itself.

Now I've just got to go back and straighten out my mess - ooppss! ;)

---

