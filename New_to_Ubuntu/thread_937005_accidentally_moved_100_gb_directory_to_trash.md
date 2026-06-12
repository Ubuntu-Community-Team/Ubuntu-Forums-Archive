---
title: "accidentally moved 100 gb directory to trash"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by energy. on 2008-10-03
the system won't let me remove said directory from the trash, it says that there isn't enough space on the disk.  I haven't written to the disk since I accidentally moved this directory into the trash, it's basically counting the size of that directory twice.  what do I do?

---

### Post by silverglade00 on 2008-10-03
If you have an external drive, you could try booting from a live CD and copying the folder to the external drive then deleting it from the trash when done. You could also try to set up an SSH or FTP connection to transfer it over the network.

---

### Post by energy. on 2008-10-03
> **silverglade00 said:**
> If you have an external drive, you could try booting from a live CD and copying the folder to the external drive then deleting it from the trash when done. You could also try to set up an SSH or FTP connection to transfer it over the network.

I don't have an external drive.  Why would it matter if it is external?  I do have two internal disks.  

Only one pc on the lan here.

---

### Post by DArtagnon on 2008-10-03
I think you have a .trash directory in your home folder.  You should be able to open it with a file browser and just move the files out, without the computer automatically trying to copy them.

---

### Post by iponeverything on 2008-10-03
Are you trying to get the data back?

if so:

cd ~/.local/share/Trash
mv <dirname> ~/Desktop

that will drop it on your Desktop.

also if want to make some space do:

sudo apt-get clean

---

### Post by germanix on 2008-10-03
I am no expert, but I would try the following:
Go to trash, right click on the file, copy the file. Go to where you have space and paste. Then go back to trash, again right click on file, choose "delete" (I think when you just empty it is still there, when you delete its gone) Then go back to where you pasted the file, copy it and paste it again where it used to be.

---

### Post by energy. on 2008-10-03
> **iponeverything said:**
> Are you trying to get the data back?

if so:

cd ~/.local/share/Trash
mv <dirname> ~/Desktop

that will drop it on your Desktop.

also if want to make some space do:

sudo apt-get clean

I'm not sure what to substitute for <dirname>

---

### Post by gpsmikey on 2008-10-03
<dirname> would be the name of the directory you accidentally moved to trash -- you want to MOVE it somewhere else, not COPY it (which would double the space used).

mikey

---

### Post by DArtagnon on 2008-10-03
> **energy. said:**
> I'm not sure what to substitute for <dirname>

<dirname> will be whatever directory you accidentally deleted.

the command essentially means 
```

# Get to my trash folder
cd ~/.local/share/Trash
# Move <100gb Deleted Stuff> to my desktop
mv <dirname> ~/Desktop

```

---

### Post by iponeverything on 2008-10-03
ls ~/.local/share/Trash

will show you what is there

---

