---
title: "HELP: Problems accessing hard drive from live cd"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by kiroshafeek on 2008-07-02
Hello Ubuntuers,

Been using Ubuntu live cd for a while, love it, but not to the point of installing it on my hard drive, always used it to access the internet and stuff and always had the problem of not having access to files on my NTFS hard drive.

Now I need to access these files more than ever, I screwed up windows vista, and I have got to access the hard drive in order to fix this thing.

Problem is every time I try to click on it, it says this:

error: device /dev/hda1 is not removable

error: could not execute pmount

Is there a way to access the hard drive? note: I'm a complete newbie when it comes to linux, so details people

---

### Post by tjwoosta on 2008-07-02
hmm...
first

install ntfs-config from synaptic package manager (or do)
```
sudo apt-get install ntfs-config
```
then try rebooting and see if you can mount it now

if still no luck try this
first
```
sudo mkdir /media/Windows
``` (this makes a mountpoint directory named Windows in /media)

then  mount /dev/whatever partition windows is on

**MINE** is /dev/sda3 for windows so **I** would do 
```
sudo mount /dev/sda3 /media/Windows
```

to find out which partition windows is on do this
```
sudo fdisk -l
```

if this still doesnt work let me know what it gives for an error when you try to mount

---

