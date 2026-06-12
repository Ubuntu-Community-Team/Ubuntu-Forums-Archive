---
title: "[SOLVED] want to create link to ramdisc"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by stinger30au on 2008-08-01
ubuntu has a ram disc built in

/dev/shm

im sure i would have to create a directory in the /media directory as a mount point

mkdir  /media/ramdisk

but how do i form a link to the /dev/shm from the /media/ramdisc

do i need to do it in fstab or what?
i assume if i do it in fstab it ill be there permanently and that is what i want but how???

Thanks

---

### Post by roquefilipe on 2008-08-01
I have a pc with a folder mapped into RAM. my idea was to use this special folder to speed up Audacity processing time, since Audacity only works on disk, but I found out that the bottleneck was somewhere else. 

Anyway, what I used in the fstab file was this
```

edicao    /home/tecnica/edicao    tmpfs    defaults,size=15G,nr_inodes=10k,mode=0770,gid=1001      0 0
```

---

### Post by stinger30au on 2008-08-02
here is what i have been told and i have tried it and it works

If you just want to link to it (and not create a whole new vfs mountpoint) the easy way is to do the following from the command line:

cd /media
sudo ln -s /dev/shm ramdisk

That will create a symbolic link. From there, you can make a bookmark in nautilus by clicking and dragging the location to the sidebar.

now in my nautilus i can see a directory called "ramdisc" and its all good!

---

### Post by stinger30au on 2008-08-02
the interesting thing i have found is i can save stuff to the ramdisc in nautilus in ubuntu and logout and login to kubuntu and the ram disc data is still intact. very cool:guitar:

---

