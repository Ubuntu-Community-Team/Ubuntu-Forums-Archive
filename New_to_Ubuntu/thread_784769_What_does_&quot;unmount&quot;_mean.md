---
title: "What does &quot;unmount&quot; mean??"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by jamieh on 2008-05-06
Do I have to "unmount" a flash drive before removing it?
What happens if I unmount an internal drive?
Thanks!

---

### Post by Dark Aspect on 2008-05-06
> **jamieh said:**
> Do I have to "unmount" a flash drive before removing it?
What happens if I unmount an internal drive?
Thanks!

You don't have to but its a good idea to unmount a drive to prevent data lost.Its basically the equivalent to the "safe removal of device" that windows 2000/XP had.

---

### Post by PeterJS on 2008-05-06
Unmounting is the process of pushing out any pending write operations to a disk (this is especially problematic with flash disks that can be removed at any time), and disconnecting the files and directories listed on that disk from the rest of the file system (so other programs and things will know this disk isn't there anymore).

---

### Post by |{urse on 2008-05-06
It is advisable to use the 

```
sync
```

command before unmounting flash drives, ipod's psp's etc.

sync finishes up all pending data transfers to and from the flash drive
and is generally not necessary for non-removeable hard disks.

---

### Post by PeterJS on 2008-05-06
> **|{urse said:**
> It is advisable to use the 

```
sync
```

command before unmounting flash drives, ipod's psp's etc. but not necessary for hard disks.

Unmount doesn't automatically sync? I thought that was one of the things it did... learn something new everyday.

---

### Post by ditdot on 2008-05-06
how about the eject command ? I usually unmount the flash drive then eject it. Because if you only unmount it, its still show up in nautilus

---

### Post by glennric on 2008-05-06
> **PeterJS said:**
> Unmount doesn't automatically sync? I thought that was one of the things it did... learn something new everyday.

Drives are synced when they are unmounted.

---

### Post by PeterJS on 2008-05-06
> **glennric said:**
> Drives are synced when they are unmounted.

That's what I thought, thanks. It seems weird they wouldn't be, but stranger things have happened.

---

### Post by carloslosgrande on 2008-05-06
[FONT="Comic Sans MS"]You can unmount an internal drive so long as its not the OS drive - if you have only one don't unmount it.
If you have a flash drive with a display light you'll see this flicker after unmount.When that stops you can pull it out.- I believe this is sync occurring. 
However I could be completely wrong on that.
And the command in terminal is "umount" not unmount[/FONT]

---

### Post by LeoSolaris on 2008-05-06
I just unmount it, then pull it out. It automatically updates in Nautilus. I never even knew there was an eject command option for USB stuff. For me it always shows up as either mount or unmount, depending on if it's mounted or not.

It would be logical, given that Ubuntu tends to make things useful, that unmount would sync unwritten data and allow safe removal of USB devices all in one click (or command for those terminal freaks.)

Leo

---

### Post by |{urse on 2008-05-11
> **PeterJS said:**
> Unmount doesn't automatically sync? I thought that was one of the things it did... learn something new everyday.

ah ^^ I made a stripped down ubuntu livecd with very few progs on it strictly for recovery use with a 5gb seagate usb hd. I've noticed that when using it to pull images with partimage it does not automatically sync so I've just always included sync before exit in my scripts on the disc. Glad i don't have to keep doing this, thx for the info ^^

---

