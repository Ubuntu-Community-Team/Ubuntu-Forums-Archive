---
title: "The update erased all my files"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by m1gas on 2008-11-24
I have just updated my xubuntu by the usual system updates, with system update manager, and the system just erase all my files. Although all linux programs, installed with add|remove programs, remain the same.
Can anyone explain me what is happennig? thanks

---

### Post by diablo75 on 2008-11-24
If you can remember the name of one of those files you're missing, open a Terminal window (Applications>Terminal) and type:

```
locate theexactorpartialnameofyour.file
```

So for instance if you're looking for a bunch of mp3's, you could type ```
locate *.mp3
```  If you're trying to find a file that was called Letter to John, I'd type ```
locate John
```  (Remember, linux is Case-Sensitive).

---

### Post by jemate18 on 2008-11-24
you may also try
```
find / -name "fileIwantToFind.mpr" 
```

---

### Post by m1gas on 2008-11-25
i cannot locate any of my old files. how could this happen? the restart was real quick and erased gigas of files. thanks

---

### Post by alienexplorers on 2008-11-25
Don't you believe in backing up your files just incase something like this happens.

---

### Post by LowSky on 2008-11-25
system update has never, ever, erased any of my old files.
that even including an distro upgrade

What folder were the files kept in?

---

### Post by Sarmacid on 2008-11-25
Are the hard drives mounted? Maybe the update messed up your fstab.

---

### Post by m1gas on 2008-11-25
the files were in my desktop and in other folders and they were all erased.

---

### Post by rustutzman on 2008-11-25
Did you look under /home to see if it might have created a new user directory for you?

Russ

Be sure to check for hidden files too.

---

### Post by mapes12 on 2008-11-25
It looks like the Update session has some how lost where your /home directory is located. You will need to figure out where you had previously installed /home. For example, some systems install /home on a separate partition (which is always wise).

To have a look at what partitions you have on your machine go to Terminal and run ```
sudo fdisk -l
```or for a GUI option boot your system with a Live CD and run Gparted. The GParted website will also let you download a bootable CD iso if you need one.

Once you have discovered where /home is located you will need to check the fstab file. This is located in Places>etc>fstab. You will see a line like this: > UUID=746191cd-8544-4b76-bd04-01f307587e80 /home           ext3    relatime        0       2
# /dev/sda5

You will need to edit it so that it points to the correct /home partition for your machine.

---

### Post by starcannon on 2008-11-25
If the files were some how erased, it may be possible to get them back with testdisk's photorec.

You can find this package in the Synaptic Package Manager, just search for testdisk, or alternately you can install it from the command line:
```
sudo apt-get install testdisk
```
Or you can download the latest version from:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

A step by step guide to Photrec is available here:
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

I have no idea how your files were erased, indeed this is the first time I've read about a simple upgrade being involved, and would be very interested in the steps leading up to the catastrophe.

GL hope the data recovery links I posted help.

---

