---
title: "script permission denied"
date: 2011-09-21
forum: Programming Talk
---

### Post by moijdikssekool on 2011-09-21
hello
i'm trying to execute a shell script, typing ./go, i'm said permission denied
as i could understand, i have to add /dev/sdb2 /media/STOK vfat umask=0,user,defaults 0 0
to my fstab (the script go is stored in /media/STOK) and type sudo mount -a. But no results
I have typed sudo chmod u+x go and go was created and recorded by kate without extension
any clue?

---

### Post by RJARRRPCGP on 2011-09-21
Try ```
chmod -X go
```

---

### Post by dethorpe on 2011-09-22
If the script is updating fstab then you will need to run it under sudo. However may be safer to see what it is trying to add and then do it manually in an editor. Either way backup your current fstab file first just in case it all goes horribly wrong!!
 
To run as sudo
 
```
 
sudo ./go

```
 
Failing that post the ouput of these commands and a copy of the "go" script and i can look into it further.
 
```
 
ls -l /media/STOK/go
id

```

---

### Post by ofnuts on 2011-09-22
> **moijdikssekool said:**
> hello
i'm trying to execute a shell script, typing ./go, i'm said permission denied
as i could understand, i have to add /dev/sdb2 /media/STOK vfat umask=0,user,defaults 0 0
to my fstab (the script go is stored in /media/STOK) and type sudo mount -a. But no results
I have typed sudo chmod u+x go and go was created and recorded by kate without extension
any clue?You can't chmod +x a file on VFAT since it has no support for that flag (IIRC there is some mount option to make the archive bit of FAT be used as an execute bit).

You can also often execute scripts without the execute flags by being more explicit. If it's a bash script you can source it ". the_script" even if it's not executable, and perl/python scripts can likely be started by calling the interpreter (python <file>...)

---

### Post by Lars Noodén on 2011-09-22
You can also try
```

sh ./go

```

---

### Post by moijdikssekool on 2011-09-29
sorry for the delay
in fact, i  was working on a media which had some problem (a partition on an USB key, available when mounted but not recognized with gparted and unavailable on windows)
now i only work with the persistent file or the main partition, so it easily works with chmod -x
thx

---

