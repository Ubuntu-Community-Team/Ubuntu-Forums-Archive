---
title: "Cant make shortcuts from my data SSD to desktop"
date: 2021-04-24
forum: New to Ubuntu
---

### Post by danezeq2 on 2021-04-24
i actually CAN make shortcuts ("links"??) but after restart they all get disabled (red X icon)
but if i again make a shortcut they all get fixed! what is that?

[https://www.youtube.com/watch?v=R73ugjl-H48](https://www.youtube.com/watch?v=R73ugjl-H48)

---

### Post by oldfred on 2021-04-24
You need to make sure you mount partition with fstab, not using your file browser which creates a default mount but after boot.

You need to define mount point, give yourself ownership & permissions (which you probalby have done).
I prefer to copy a working mount of my data partition into fstab, editing for correct UUID and if different mount edit that.

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by CatKiller on 2021-04-24
> **danezeq2 said:**
> i actually CAN make shortcuts ("links"??) but after restart they all get disabled (red X icon)
but if i again make a shortcut they all get fixed! 
So, a couple of things.

Links aren't shortcuts in the way you're thinking of them. They're a file that points to a different file, like a copy that's always up to date and takes no space. In case you want to read more about them, "symbolic links" or "symlinks" would be the terms you'd look for. There are also "hard links," which are when you have two files that point to the same data, without either being the "true" one. 

The other thing is that Linux doesn't use "drives" in the way that you're thinking of, either. What Windows calls a drive is actually a partition, and on Linux you access the data on a partition by mounting it somewhere in the filesystem tree: its *mount point*. Then it's a directory just like any other, wherever the data might happen to reside. The GUI tools are just for temporary mounts, like thumb drives and so on. To have a partition mounted to the same place every time when you boot, you add an entry into the filesystem table (/etc/fstab) saying what you want mounted where, as oldfred says. It doesn't matter that much *where* you mount it to, although a directory under /mnt is traditional. Once you've got it so that it mounts automatically you can create a symlink to it from wherever is convenient. 

So, as an example, I've got a NAS that holds all kinds of stuff. It gets mounted to /mnt/nfs through an entry in fstab. I've got symlinks to the relevant NAS locations for music, videos, downloads, and so on, in the places that are easy to access when I want those things.

---

### Post by danezeq2 on 2021-04-25
oh dear, am i gonna need to read articles just to make a shortcut?
once on every 5 years im trying to install ubuntu trying to replace windows with it, hoping there's a real user friendly OS alternative to window and i always get disappointed.

---

### Post by CelticWarrior on 2021-04-25
> **danezeq2 said:**
> oh dear, am i gonna need to read articles just to make a shortcut?
once on every 5 years im trying to install ubuntu trying to replace windows with it, hoping there's a real user friendly OS alternative to window and i always get disappointed.

I'm afraid you'll be eternally disappointed if you keep equating "user-friendliness" with "Windows drop-in replacement". Ubuntu isn't and will never be Windows and we like it this way (even when we exchange insults over the smallest and least important detail).

---

### Post by CatKiller on 2021-04-25
> **danezeq2 said:**
> once on every 5 years im trying to install ubuntu trying to replace windows with it, hoping there's a real user friendly OS alternative to window and i always get disappointed.
I mean this question sincerely; why do you do that?

Linux is extremely user-friendly in ways that Windows isn't. If it was exactly the same as Windows, it wouldn't be an alternative, would it? If what you really want is Windows, then just use Windows. If you want something that's different than Windows, then it's going to be different to Windows.

You aren't born knowing how to use Linux, just as you weren't born knowing how to use Windows, so you'll need to learn how to use it, just as you learned how to use Windows. One of the most important lessons to learn is *unlearning* the habits you've built up from using Windows; the more of those habits you have, the more painful the process. If you don't actually have any reason to do so, why bother?

---

### Post by coffeecat on 2021-04-25
> **danezeq2 said:**
> oh dear, am i gonna need to read articles just to make a shortcut?

Yes, but in the short term there is a solution to your original stated problem while you are in the steep part of your learning curve for a completely different operating system to Windows.

I believe what has happened is that you mounted your data SSD (specifically, as others have pointed out, a partition in your data SSD, **NOT** the whole drive) using the file manager by clicking on it in the left pane of the file manager. The system creates a mounpoint and mounts it for you as a temporary measure. When you restarted the system and found that your "shortcuts" had a red X, that was because you had not remounted the partition in the same way - using the file manager. If you had simply clicked on the partition you wanted to access with a "shortcut", before trying to use the "shortcut", you would probably have found that it would have worked. (And, as others have pointed out - in Linux it's a symlink not a shortcut.)

I say probably because although the system usually creates the same mountpoint in the situation you describe, this is not always so. There are circumstances when it might create a different mountpoint, and then your symlink will fail. This is why oldfred recommended mounting regularly used partitions in /etc/fstab. This guarantees that the mountpoint will be the same and that your symlinks will be robust.

I offer this only as a temporary measure until you are more familiar with Ubuntu as an operating system. It's a clunky workaround, and it may fail, but it might do until you have more confidence in being able to configure your system.

Last point, re-iterating what others have said. Don't expect Ubuntu, or any Linux distro, to be a drop-in replacement for Windows. It isn't, it never was meant to be, and never will be. Personal note - I recently installed Windows 10 after not having used a Windows desktop for many years. I felt utterly lost at times and with relief fled back to my familiar Ubuntu desktop.

**Edit:** a further thought. You don't specify whether your data SSD is an internal drive or an external USB device. If the latter, it would have been automounted as soon as you plugged it in, and what I said earlier does not apply - unless you clicked on the eject icon. If it's an internal drive, then what I said earlier does apply - it needs mounting either by clicking in the appropriate place in the left pane of the file manager or by means of /etc/fstab.

---

