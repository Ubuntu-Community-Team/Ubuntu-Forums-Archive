---
title: "Can't double click to play CD on desktop...?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by jwkungfu on 2008-05-17
Hi all,
I'm trying to compile a CD for a friend of music in my CD collection....
I've been using Sound Juicer to extract songs into my music file where I check them out with Rhythmbox...

Now the problem...
Today, I select Extract in Soundjuicer and an error message came up...?
Something about VFS (I think) came up in the error message.
I checked the Ubuntu forums and I read something about downloading all GStreamer files from Applictions/Add/Remove Files... So I did that....

Still can't extract with Soundjuicer and now I noticed that I can't double click the CD icon on my desktop, or, right click and open with Rhythmbox.................

:confused:

Also, I read something that CDs might include a file (supposedly as copy protection) and that file may cause problems? Has anybody heard or know about anything like that?

---

### Post by shadow-of-sin on 2008-05-17
Hi,

Please run SoundJuicer from the terminal, and post the error you get when trying to extract.

---

### Post by jwkungfu on 2008-05-17
> **shadow-of-sin said:**
> Hi,

Please run SoundJuicer from the terminal, and post the error you get when trying to extract.

OK, what is the command?

---

### Post by shadow-of-sin on 2008-05-17
It's:
```
sound-juicer
```

---

### Post by jwkungfu on 2008-05-17
> **shadow-of-sin said:**
> It's:
```
sound-juicer
```

Sound Juicer could not extract this CD.
Reason: Access denied

john@john-laptop:~$ sound-juicer extract

** (sound-juicer:6710): WARNING **: Could not lock drive: Extracting audio from CD
sh: jackd: not found
gnome-mount 0.6
Device /dev/scd0 is in /etc/fstab with mount point "/media/cdrom0"
Ejected /dev/scd0 (using /etc/fstab).

---

### Post by shadow-of-sin on 2008-05-17
I don't normally recommend running an application as root unless necessary, but try running this command:
```
sudo sound-juicer
```

---

### Post by jwkungfu on 2008-05-17
> **jwkungfu said:**
> Sound Juicer could not extract this CD.
Reason: Access denied

john@john-laptop:~$ sound-juicer extract

** (sound-juicer:6710): WARNING **: Could not lock drive: Extracting audio from CD
sh: jackd: not found
gnome-mount 0.6
Device /dev/scd0 is in /etc/fstab with mount point "/media/cdrom0"
Ejected /dev/scd0 (using /etc/fstab).

john@john-laptop:~$ sound-juicer extract

** (sound-juicer:6710): WARNING **: Could not lock drive: Extracting audio from CD
sh: jackd: not found
gnome-mount 0.6
Device /dev/scd0 is in /etc/fstab with mount point "/media/cdrom0"
Ejected /dev/scd0 (using /etc/fstab).

---

