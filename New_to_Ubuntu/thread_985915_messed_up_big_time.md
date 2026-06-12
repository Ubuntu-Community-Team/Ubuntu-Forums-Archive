---
title: "messed up big time"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by kratos_prakhar on 2008-11-18
hello everyone...

i was installing a gnome windows decoration package the other day... and it cropped up an error saying broken dependencies after the installation.

i did the sudo apt-get install -f in the terminal... and it found 12 packages needed to be removed... among which were nautilus and gnome essential packages.

so i clicked cancel... and decided to do away wid the new package. however, this time it said that uninstalling it wuld affect the above mentioned packages.

with no choice left... i ran the command in the terminal. and as expected ubuntu failed to boot up after that. :(

this has happened for the second time and is really annoying as i will have to install everything again. i tried the sessions>failsafe gnome thing but even that doesnt help .. it only runs failsafe xterm to which i know nothing about..

can someone plz shed some light on how to go to get my old ubuntu with the essential packages back. 

the faulty package was nt installed frm synaptic.. i took it frm a repository maintained in my college. since i dont have net connection always i install new packages frm that repository only. and such a problem forces me to use synaptic (ubuntu repo) and makes me helpless in the absence of a net connection. 

Any help would be greatly apprecaited...

---

### Post by Peter09 on 2008-11-18
If you know what packages you uninstalled you can install them at the recovery mode command line with the command

```
sudo apt-get install nautilus
```

The above line will install nautilus. Substitute into that line any other packages that you removed as well.

You may find some packages are automatically installed as they are dependencies of the package you are installing.

---

### Post by mapes12 on 2008-11-18
You could also try

```
sudo apt-get install ubuntu-desktop
```

which should reinstall all the dependancy packages for your desktop environment.

TIP: Next time you change anything in your file system take a backup before you make any changes. This will save you having to re install and going online for all your updates again. Here's a HowTo: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) You would also need to --exclde=/home if you have it on a separate partition.

Also have a look at aptoncd for the packages you need access to without full internet connection. Search for it in Synaptic Package Manager.

---

### Post by spiderbatdad on 2008-11-18
It may be quite difficult to recover your old installation, as we don't have a complete list of the packages you removed. You may have removed libc6, for example.

You could boot the live cd and try to mount what remains of your existing file system: ```
sudo mount /dev/sda /mnt
``` (that may take some trial and error to get the command to work...like specifying the filesystem or correct partition) From there you could recover files from your /home. Or you could edit sources.list to install packages from the live cd to try to fix your system. When you are done: sudo umount /dev/sda

Instead you might consider re-partitioning creating a separate /home to protect your personal files from future re-installations. It sounds like you don't have access to ubuntu repos. Maybe a straight debian installation would be better for you to build upon.

---

### Post by kratos_prakhar on 2008-11-18
thanx peter.... but i think many more were uninstalled in the process... atleast nxt time. i can write down which ones were removed... 

thanx :)

---

### Post by kratos_prakhar on 2008-11-18
i have installed the apton cd.. and made a backup. but the problem is that i need the gui to mount the partition and install the packages and since there is no gnome or nautilus i cant seem to find a solution.

i can however reinstall ubuntu and then use the iso... but i dont wanna sit and install ubuntu again...

thanx for the tip and the help...

---

### Post by Peter09 on 2008-11-18
You will find that doing what everyone has suggested will bring back these packages, do try before you do much else. A lot of what was removed will have been dependencies, which will automatically be brought back in.

---

### Post by hyper_ch on 2008-11-18
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by kratos_prakhar on 2008-11-18
next time i'll keep that in mind ;-)

---

