---
title: "Free space on filesystem 0MB after &quot;grep&quot; command ?"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by vijikey2 on 2011-12-15
Hi folks,
yesterday I've tun this command in terminal:

grep -a -A17000 -B17000 localhost /dev/sda2 | strings > recovered_file

but without to "unmount /home"

after that the ubuntu warned me that there is not enought disk space on file system partition. Now I've deleted a file of 2 gb and the system calculated only 50 mb free space, which in about minutes were gone and again the free size was 0 mb. I've tried to remove one more file of 3 GB and the same thing happened again. I don't know what to do folks, please help me! :(

---

### Post by Elfy on 2011-12-15
Deleted or sent to trash?

If you deleted as root did you empty root's trash?

Try running ```
sudo apt-get clean
``` - that will clear some real room - perhaps enough to get into the system with no issue so you can check properly.


[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by Paqman on 2011-12-15
You've obviously dumped truckloads of data into recovered_file. If you deleted that in the GUI go into your rubbish bin and empty it. If it's still there you can completely get rid of it with a Shift-Delete or using the rm command in the terminal.

If you're still havign trouble try running the Disk Usage Analyser as root byt hitting Alt-F2 and entering:
```
gksudo baobab
```
Let it scan the whole filesystem. This will show exactly what files are taking up the most space on your system so you can do delete any that are spurious.

---

### Post by vijikey2 on 2011-12-15
Thanks to both of you so quick! BUT

> **Paqman said:**
> You've obviously dumped truckloads of data into recovered_file. If you deleted that in the GUI go into your rubbish bin and empty it. If it's still there you can completely get rid of it with a Shift-Delete or using the rm command in the terminal.

If you're still havign trouble try running the Disk Usage Analyser as root byt hitting Alt-F2 and entering:
```
gksudo baobab
```Let it scan the whole filesystem. This will show exactly what files are taking up the most space on your system so you can do delete any that are spurious.

So you are suggesting me to delete the file "recovered_file" ?

---

### Post by Paqman on 2011-12-15
> **vijikey2 said:**
> 
So you are suggesting me to delete the file "recovered_file" ?

Or move it somewhere where it's causing less trouble. It sounds like it's gobbled up all the free space on your root partition.

What exactly were you trying to achieve with your grep command? If it's going to produce a lot of output you'll need to direct it to somewhere that has enough storage. Dumping it all in your system's root will bring everything to a grinding halt.

I'm no grep guru by any means, but should -A and -B be the same number? That might be why it's gone haywire.

---

### Post by vijikey2 on 2011-12-15
Ok i've deleted the receovered_file and rebooted tge system, now with the start of the system there are 3 messages poped up :

> 
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10706000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


Then:

> 
The panel encountered a problem while loading "OAFIID:GNOME_WorkspaceSwitcherApplet".
Do you want to delete the applet from your configuration? (Options: Don't delete, Delete)


And of course:

> 
This computer has only 0 bytes disk space remaining!


Now what should I do next?

---

### Post by Paqman on 2011-12-15
How exactly did you delete the file?

---

### Post by vijikey2 on 2011-12-15
Shift + del

---

