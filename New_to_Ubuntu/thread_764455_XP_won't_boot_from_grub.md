---
title: "XP won't boot from grub"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by bt224 on 2008-04-23
I just did some updates to 8.04, rebooted to get into XP. After I select XP from the menu, screen goes blank and everything stops.

---

### Post by Can+~ on 2008-04-23
But the stuff is still there? Can you access it with the ubuntu partition?

Maybe you overwrote it, but if not, then you should try to edit the grub menu.lst to try another id:

```
gksudo gedit /boot/grub/menu.lst &
```

Look for
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

"(hd0,0)"
Make sure it points to the right partition (mine is 0,0, because it's the first hard disk (0) and the first partition of it, the only one (0).

Also notice, that on grub you can edit the line (but changes are not permanent), to try to get into the correct partition.

---

### Post by bt224 on 2008-04-23
Here's what it says:


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Can+~ on 2008-04-23
And did you check if the information on the windows partition is alright?

---

### Post by bt224 on 2008-04-23
How can I tell?

---

### Post by Can+~ on 2008-04-23
> **bt224 said:**
> How can I tell?

Well, ubuntu usually mounts the hard disks and puts icons on your desktop to see them.

Try this (Prints the current hard disks on the system):

```
sudo fdisk -l
```

print the output here. And, there must be a NTFS partition (the windows one), if it is, try mounting it

```
sudo mount /dev/xxx /mount/mywindows
```

(where /dev/xxx is the current hard disk that you find via the fdisk)

After mounting, navigate to the /mount/mywindows with your favorite file browser, and see if there are windows stuff inside, like "WINDOWS" folder "Programs Files" etc.

If there is, then your windows partition is fine, if not, then I guess you overwrote it :(.

If you still got doubts, here's a guide:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by malathion on 2008-04-23
Had a problem like this once, here's how I fixed it:



How to install Grub from a live Ubuntu cd. 
[http://sudan.ubuntuforums.com/showthread.php?t=224351](http://sudan.ubuntuforums.com/showthread.php?t=224351)

---

### Post by Can+~ on 2008-04-23
> **malathion said:**
> Had a problem like this once, here's how I fixed it:



How to install Grub from a live Ubuntu cd. 
[http://sudan.ubuntuforums.com/showthread.php?t=224351](http://sudan.ubuntuforums.com/showthread.php?t=224351)

I want to discard the possibility of overwriting before jumping on reinstalling grub.

---

### Post by bt224 on 2008-04-23
Yeah, ok feeling stupid. Yes they were mounted and yes everything is there.

---

### Post by Can+~ on 2008-04-23
> **bt224 said:**
> Yeah, ok feeling stupid. Yes they were mounted and yes everything is there.

Then try to do what Malation posted, or continue editing the menu.lst to hit with the right partition...

Or other possibility is the windows init got corrupted somehow?

I suggest backing up!

---

### Post by aimpau on 2008-04-23
Always remember that every update alters your grub menu.lst settings. It happened to me so all you have to do is to reconfigure it.

---

### Post by bt224 on 2008-04-24
nope, didn't work.

---

### Post by bt224 on 2008-04-24
Could hd0,0 be wrong? it shouldn't be, but now I'm not so sure of anything

---

### Post by bt224 on 2008-04-24
What would happen if I did a fresh install of Ubuntu? Would it fix this? It hurts to say it, but I have to get back into Windows.

---

### Post by Helios38 on 2008-04-24
shouldnt hurt.


as long as you use the same partition, u shouldnt harm windows, and when u reinstall grub, it will overwrite the old (broken) one.



also, if ALL else fails


and i really mean all else:


u can pop in your windows disk, and go into recovery mode, and type fixmbr.



if you do this, ubuntu WILL NOT BE BOOTABLE! and grub will be lost, but u will be able to boot into windows.


but seriously, use that as a last resort. maybe if it is a last resort, use it, back up all your data, and reinstall ubuntu.

---

### Post by bt224 on 2008-04-24
well, that's part of the issue, this machine is pretty old. It came with ME, and then later Dell sent the XP upgrad. Tried that disk first with no luck. Nothing to really lose off the Ubuntu install, just a pain to redo everything is all. Right now my A1 concern is getting back into windows. I can get the data, but I absolutely must be able to use my Office 2007 (specific work requirement).

---

