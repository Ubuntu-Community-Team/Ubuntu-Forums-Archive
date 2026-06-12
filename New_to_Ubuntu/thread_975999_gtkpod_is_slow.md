---
title: "gtkpod is slow"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by hanzj on 2008-11-08
Hi,
I've just installed gtkpod from ubuntu repository. Everytime I click on something in gtkpod, it takes up 100% of CPU power and is unresponsive for ten seconds or so. What's going on?


I need to manage (add/remove) songs on my iPod. Please advise.

---

### Post by stoogiebuncho on 2008-11-09
There are several things that could be happening.  If your files are in .ogg format (or another format that iPods can't read), gtkpod will have to change the format to something that can be read by your ipod.  It usually uses the whole processor to do this.  However, if it's doing this every time you click anything, there might be something up.

I've used gtkpod for a while without problems, but I've heard that a lot of people really like Amarok if you want to try something else.  I think it's a little more iTunes-ish, also, so that could be good depending on what you're looking for.

---

### Post by hanzj on 2008-11-09
I've used gtkpod before (in older ubuntu version), and i like it. I wish it could work.. 99.9 % of files on iPod are mp3. And, yes. The slowdown happens everytime I click something.

---

### Post by chrisod on 2008-11-09
I had the same problem with gtkPod and never did figure it out. Rhythmbox and my iPod play nice together though.

---

### Post by echo.whoami on 2008-11-09
Banshee rulezzzz

You can install it from a terminal typing:
```
sudo apt-get install banshee
```

Open it, import the folders with the tracks you want, plug in the ipod, and then just drag and drop the tracks in the ipod on the left bar...:D

Banshee is also my favorite player as it can load the winamp equalizer presets. 
[http://ubuntuforums.org/showthread.php?p=5536419](http://ubuntuforums.org/showthread.php?p=5536419)

---

### Post by stoogiebuncho on 2008-11-09
Hmmm.  Sorry, all you're getting are recommendations for other software.  I'm afraid I don't have many ideas for what could be going on.

You could try re-installing gtkpod if you haven't already.

You could also try running gtkpod from the terminal - maybe it will give you some error messages that will make it easier to narrow things down.  If it does, post them here.

---

### Post by hanzj on 2008-11-18
stoogiebuncho,
I've reinstalled gtkpod just now. 
And then I tried running gtkpod from the terminal. Here's the printout for both.
> 
:~$ sudo apt-get install gtkpod
[sudo] password for jeph: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mp3gain faad faac lame
The following NEW packages will be installed:
  gtkpod
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/844kB of archives.
After this operation, 3109kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  gtkpod
Install these packages without verification [y/N]? y
Selecting previously deselected package gtkpod.
(Reading database ... 102589 files and directories currently installed.)
Unpacking gtkpod (from .../gtkpod_0.99.12-3_i386.deb) ...
Processing triggers for man-db ...
Setting up gtkpod (0.99.12-3) ...

hanzj@hanzj-desktop:~$ gtkpod

(gtkpod:10887): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:10887): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:10887): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:10887): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:10887): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:10887): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:10887): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:10887): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:10887): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:10887): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:10887): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:10887): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

** (gtkpod:10887): CRITICAL **: sha1_sha1_exists: assertion `sha1' failed

** (gtkpod:10887): CRITICAL **: sha1_sha1_exists: assertion `sha1' failed

** (gtkpod:10887): CRITICAL **: sha1_sha1_exists: assertion `sha1' failed

** (gtkpod:10887): CRITICAL **: sha1_sha1_exists: assertion `sha1' failed

** (gtkpod:10887): CRITICAL **: sha1_sha1_exists: assertion `sha1' failed

** (gtkpod:10887): CRITICAL **: sha1_sha1_exists: assertion `sha1' failed


---

### Post by stoogiebuncho on 2008-11-19
Wow, I cannot find anything about this anywhere.

Maybe it's time to post a bug report. :(

You could try installing those suggested packages (mp3gain faad faac lame) just for giggles.  Maybe that would do something.

Sorry I couldn't be more help.

---

### Post by hanzj on 2008-11-26
Does anybody know if my problem is related to [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=391810](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=391810) ?

---

### Post by stoogiebuncho on 2008-11-26
That could be it, actually.  I seem to remember reading that gtkpod works much better with FAT formatted iPods.  Do you know if your iPod is formatted in the NFS format or the FAT format?

If it is in NFS format, you can reformat it to FAT and that might just fix your problem.  You'll need access to iTunes to do that, though.  And it will erase your songs so you'll have to load them again.

---

### Post by hanzj on 2008-11-27
when i plug in my iPod to ubuntu box, I check in Nautilus, and it says that the iPod is of "msdos" Filesystem type.


I've found out that my iPod is FAT. 

But that doesn't help. The debian link says the problem is with NFS.

So I'm still wondering why my iPod is extremely slow.

---

### Post by hanzj on 2008-11-27
Disk /dev/sdc: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20202020

   ```
Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          10       80293+   0  Empty
/dev/sdc2              11        3648    29222235    b  W95 FAT32
```

---

### Post by hanzj on 2008-11-29
I've installed banshee and it works fine. In other words, there is no slowdown with banshee, as there is with gtkpod.

---

### Post by stoogiebuncho on 2008-11-29
Sorry we couldn't help you.  I'm glad you found something that works.

---

### Post by coggz on 2008-12-01
Hmm, I'm also having this exact same issue... again Intrepid Ibex. I think it is Ibex related, but I cannot find any info either. If you still want a small program, I have used Floola and Yamipod before and they are very similar to gtkpod - although I prefer gtkpod. They are just ipod managers rather than being music players etc.,,,
If you do get a solution, please post it here, as I'd like to know...
Luke

---

### Post by coggz on 2008-12-02
Hey again, I think I have fixed it, and it is quite simple after all!
Go to your home folder, and view hidden files (CTRL+H in Nautilus) Then find .gtkpod - delete this folder (It is all your gtkpod settings btw..) After you have done that, try using gtkpod again.
It worked for me anyway, but we'll see if it works for anyone else...
Hope that helps,
Luke

---

