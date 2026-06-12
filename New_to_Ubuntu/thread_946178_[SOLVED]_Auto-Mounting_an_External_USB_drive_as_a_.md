---
title: "[SOLVED] Auto-Mounting an External USB drive as a directory in ~"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by drowner on 2008-10-13
Hi

I have a USB drive which has 4 partitions.

One of the partitions is ext3 and contains all my music. It is labelled linux-music. It automounts to /media/linux-music.

Now, it doesn't really matter, but what I would like to do is have it mount to /home/drowner/Music/linux-music so that all my music is always in the same folder. Its not a huge issue, but I would like to do it.

I tried using the 'mount point' option in the volume tag - but that doesn't work. That only can be used to specify the name of the point in /media. 

I don't really want to edit my fstab for a drive that is not always connected either.

This is not crucial, and it may very well be impossible, but I would like to know if it can't be done.

---

### Post by Orange_and_Green on 2008-10-13
Hi drowner :)

How about creating a symbolic link in your Music directory that points to the automount directory?

```
cd /home/drowner/Music
ln -s /media/linux-music linux-music
```

---

### Post by drowner on 2008-10-13
Ah! I forgot symlinks!

remind me - will that appear actually LIKE a folder, rather than just a 'shortcut' as it were?

Further, will it cause problems if the drive is not connected?

---

### Post by Orange_and_Green on 2008-10-13
> **drowner said:**
> will that appear actually LIKE a folder, rather than just a 'shortcut' as it were?

It will appear as a folder with a white arrow pointing up right (at least, if you are using icons from the "Human" set.)

> **drowner said:**
> Further, will it cause problems if the drive is not connected?

Well, yes and no. It will give you a message that the link is broken if you double-click on it, but if you leave it alone it will just peacefully sit there.

---

### Post by drowner on 2008-10-13
OK! Thankyou!

I will do it now, and then re-build my Banshee library. If it all goes well, i will mark as solved

---

### Post by drowner on 2008-10-13
> **Orange_and_Green said:**
> Hi drowner :)

How about creating a symbolic link in your Music directory that points to the automount directory?

```
cd /home/drowner/Music
ln -s /media/linux-music linux-music
```

Ok, all done - Banshee unfortunately didn't scan the symlink :(, so i just added the linux-music symlink manually, interestingly, that was OK?

Anyhow, the command i put in was

ln -s /media/linux-music

when i added the second linux-music it created a folder called linux-music, and then put the symlink in there!

---

