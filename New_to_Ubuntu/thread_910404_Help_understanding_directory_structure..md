---
title: "Help understanding directory structure."
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Karrion on 2008-09-04
Ok I'm not having a problem figuring out the commands to move around and manipulate files.

However, i am having troubles locating stuff.  I am proficient with windows, dos etc. 

Example, i installed amule and wanted to go to the directory that it was installed in, now if this was a windows system i would know that it is in the C:\Program files directory. Or if i needed to replace a corrupted file in windows it would be in the C:\windows directory. So i was hoping someone could explain to me what's in each of these directories.

/bin
/boot
/dev
/etc
/home - That one is self explanatory lol.
/media - also self explanatory.
/mnt - assuming this is where other drives would typically be mounted.
/opt
/proc
/root
/sbin
/srv
/sys
/usr
/var

I know this all may be simplistic but doing a search for this info seems to be fruitless for me.

---

### Post by oldos2er on 2008-09-04
[http://www.ahinc.com/linux101/structure.htm](http://www.ahinc.com/linux101/structure.htm)

---

### Post by ronnielsen1 on 2008-09-04
> **< [B]/** >[/B]

 		The root directory. The starting point of your directory structure. This is where the Linux system begins. Every other file and directory on your system is under the root directory. Usually the root directory contains only subdirectories, so it's a bad idea to store single files directly under root.
 		Don't confuse the *root directory* with the root user account, root password (which obviously is the root user's password) or root user's home directory.
 		**< [B]/boot** >[/B]

 		As the name suggests, this is the place where Linux keeps information that it needs when booting up. For example, this is where the Linux kernel is kept. If you list the contents of /boot, you'll see a file called vmlinuz - that's the kernel.
 		**< [B]/etc** >[/B]

 		The configuration files for the Linux system. Most of these files are text files and can be edited by hand. Some interesting stuff in this directory:


More at:
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by ByteJuggler on 2008-09-04
Also see [here.]("http://tldp.org/LDP/intro-linux/html/sect_03_01.html")

---

### Post by philinux on 2008-09-04
Nice graphic.

---

### Post by bodhi.zazen on 2008-09-04
[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html) 

[http://freeos.com/articles/3102/](http://freeos.com/articles/3102/)

---

### Post by snowpine on 2008-09-04
Hi Karrion, it looks like you have some good links to keep you busy with reading material for a while. :) 

I just want to say, because nobody has mentioned it yet: Everything you need for day-to-day use is in the /home directory. That's (one of the reasons) why you must use 'sudo' to change anything outside of your /home--it's a reminder that you can mess up the system! Ubuntu has robust tools for administering most tasks, for example, if you have a corrupt package, you can fix it with Synaptic instead of digging through the C:\windows directory. 

Sorry if I am stating the obvious :) and good luck!

---

### Post by ice60 on 2008-09-04
you can find where the binary is running from like this -
```
which amule
```
and there should be an amule directory in your home directory, it's called **.aMule**, that's where you can configure stuff if you need to. all the directories with a . at the start are hidden, if you want to see all those hidden directories you can do that in the nautilus preferences, i'm using an old version of nautilus so the option to see hidden directories might not be in the same place - 
Edit>Preferences>Show hidden and backup files.

in a terminal you can run **ls -a** to see the hidden things.

---

