---
title: "OhNo. auto fsck failed.  Can't start."
date: 2008-05-05
forum: New to Ubuntu
---

### Post by movrshakr on 2008-05-05
Got this:
fsck died with exit status 4
An automaatic file system check of the root filesystem failed. A manual fsck must be performed, then the system restarted.  The fsck should be performed in maintenance mode [HOW DO I GET INTO THAT?] with the root filesystem in read-only mode.
* the root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
Afer performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found 
bash: lesspipe: command not found 
bash: Command: command not found 
bash: The: command not found 
bash: dircolors: command not found 
bash: Command: command not found 
bash: The: command not found 
root@maximus"~#
=======================================================
ls at this point produces "Desktop" in blue
I have no idea how to recover my machine or why this occurred out of the blue.  Can anybody help?

---

### Post by spydon on 2008-05-05
Just write in ```
fsck
``` in there and it will probably do a filesystem check. :)

It automatically took you into the maintenance shell so you'll probably just have to write that and press enter.

This could have happened because your harddrive has badblocks, you can check that later with ```
badblocks /dev/sda
``` or maybe hda.

---

### Post by movrshakr on 2008-05-05
OK, it started and is taking a long time, but disk light is blinking.  I didn't know if any switches would be needed on the command is why I didn't start it before.

Will report back when it finishes.  Now it is saying=running additional passes to resolve multiply claimed blocks.

---

### Post by movrshakr on 2008-05-05
It asked if I wanted to clone multiply claimed blocks.  Default was yes...accepted.  And to fix a block count or something--I don't remember the exact 2nd question.  Said yes.  When finished, did Ctrl-D to exit (even though it did not tell me how to restart, I remembered that from before).  Reboot brought it up.  Yea!!!!

One of the files claiming the common block was a png file in the folder for an app I don't use...didn't really see it tell me the other filename also claiming it.  So one of the two files may now have a block in it that is not correct...future problem possible.

But I am back up.  Happy now.  Don't need this aggravation.

---

### Post by spydon on 2008-05-05
I'm glad that it worked for you, do you want to check if your harddisk has any bad blocks?

---

### Post by movrshakr on 2008-05-05
> **spydon said:**
> I'm glad that it worked for you, do you want to check if your harddisk has any bad blocks?
Probably would be a good idea, no?  Is it a switch on fsck?  

And how do I get the machine into the proper state to do it (I assume you don't just command it from a terminal window)?

---

### Post by philinux on 2008-05-05
Just a note, if you run badblocks it will take a long while.....

You're better of running smartmontools if your disk drive supports it. It's in the repo and there's a website about it if you google. This runs quick and will report any disk i/o/ errors.

Also if you check in /var/log/messages for disk read/write errors that should really suffice.

---

