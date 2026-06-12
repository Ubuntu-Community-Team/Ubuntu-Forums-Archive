---
title: "Ghosting Ubuntu"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by witwolf on 2008-07-29
I ghosted Ubuntu with Norton Ghost 8.0 but I couldn't get it to load back after release it to the new computers.  I kept getting this screen that says:

*An automatic file system check (fsck) of the root system failed A manual fsck must be performed, then the system reestared.
The fsck should be preformed in maintenance mode with the root filesystem moutned ni read-only mode.
*The root filesystem is currently mounted in read-only mode.
A maintenance sheell will now be started.
After preforming system maintenance, press CONTROL-D
to terminate the maintence shell restart the system.
bash: no job control in this shell
bash: group: command not found
bash: lessipipe:command not found
bash: Command:command not found
bash: The:command not found
bash: discolors:command not found
bash: Command:command not found
bash: The:command not found
root@--------desktop:~#

I"m very new in using ubuntu.  Any suggustions will help.  Thanks

---

### Post by sharks on 2008-07-29
if u want to check the filesystem , type in terminal:

sudo fsck

---

### Post by witwolf on 2008-08-01
what do i do with it?  I don't really know what fsck is.. I did sudo fsck and the next row it gave me the version

fsck 1.40.8 (13-March-2008)

---

### Post by james_vanb on 2008-08-01
Have you looked at this for cloning?

[http://ubuntuforums.org/showthread.php?t=599599](http://ubuntuforums.org/showthread.php?t=599599)

---

