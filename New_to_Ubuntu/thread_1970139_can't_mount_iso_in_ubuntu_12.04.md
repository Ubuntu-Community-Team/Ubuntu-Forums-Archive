---
title: "can't mount iso in ubuntu 12.04"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by suarez on 2012-04-30
[CENTER]I'm having a problem when trying to mount a .iso file.
See picture[/CENTER]

---

### Post by anewguy on 2012-04-30
I just use gmount-iso.

Dave ;)

---

### Post by williejones on 2012-04-30
Iso files are usually extracted and burned to CD or DVD.  Insert CD of DVD, Right click on the iso file and select wright to disk.  It will unpack the iso file to the disk as a program.

You can also mount an iso file by using loop if you want to see the files inside.

Link to two different ways to mount iso files 

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

---

### Post by Enigmapond on 2012-04-30
There is actually a nautilus extension that will allow mounting right in nautilus..:
[http://ubuntu.mindseeder.com/12.04/#naMountImage](http://ubuntu.mindseeder.com/12.04/#naMountImage)

---

### Post by anewguy on 2012-05-01
Hey, I've got to check that out.  I have ISO's I want to look at from time to time that I have saved out on flash drives.  Mounting them directly to nautilus would be much better for me.  I currently use gmount-iso to do it and it works - but it also creates some phantom drives that don't disapear until I reboot.  So, this would be much easier.  I hope the OP has good luck with it as well.

Dave ;)

---

### Post by Manyrootsofallevil on 2012-05-01
you could open a terminal and mount it like this:

```
sudo mount isofile.iso /directory -o loop
```where directory is a directory that currently exists

To unmount it, when finished

```
sudo umount /directory
```

---

### Post by Visitor.Q on 2012-05-01
I can right-click an .iso file and the first option says it can mount the iso with 'archive mounter'. When I do so, it creates a new mount point in $HOME/.gvfs but there are no files inside. I believe I've never seen this working on .iso files, so would this be a bug, anyone else has it? Is it supposed to work like that? I mean, the mount command works fine and all, but I didnt expect it still to not work...

---

