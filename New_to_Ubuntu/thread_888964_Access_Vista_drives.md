---
title: "Access Vista drives"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-08-13
I can no longer access my Vista drives from hardy. This was all working from shortcuts without bother, but tonight I can no longer access them. I have installed a few updates since the last time I used them, so cant say exactly when this happened. How do I go about fixing it.

Couldn't display "/freedesktop/Hal/devices/volume_uuid_CCC4952CC4951A32".
There is no application installed for this kind of file.

Thats the error message I get.

---

### Post by WRDN on 2008-08-13
What file are you trying to open? I'm guessing the drive is mounted, so navigate to the actual file, right click on it and select Properties. Then, click "Open With" and select the Application you usually use to open the file.

---

### Post by celticbhoy on 2008-08-13
No its the drive not a file - No access to the drive

---

### Post by dacorr on 2008-08-13
is the drive detected?

---

### Post by WRDN on 2008-08-13
Ah, sorry. In that case, in the Terminal, type:

```
sudo fdisk -l
```

If the partition is recognised, then you can mount it manually:

```
sudo mount /dev/[drive] /media/[folder_to_mount_in]
```

---

### Post by celticbhoy on 2008-08-13
That worked and I can access after manual mounting, but will it now automount again, and why did it stop in the first place. I need this to automount as I am getting the wife to use Ubuntu more and more, but she needs to have the windows drive automounting to access her stuff.

---

### Post by WRDN on 2008-08-13
Was your last Vista shutdown/ restart a "dirty" shutdown/ restart (where the drive doesn't unmount properly)? If so, that may have caused the problem.

The drive should now automount, but if it doesn't, open the Terminal and type:

```
sudo gedit /etc/fstab
```

Then add the line:

```
/dev/[drive] /media/[folder] ntfs defaults 0 0
```

---

### Post by ooobuntooo on 2008-08-13
Hey, a fellow Scot!
I'm a Jambo BTW.
Sorry, i'm not being helpful!

---

