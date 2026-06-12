---
title: "Dual boot problems"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by ubitauba on 2008-11-15
I recently I installed Kubuntu 8.04 (now I'm dual booting with Vista), then 8.10 came out so I updgraded Kubuntu.  After this upgrade, in the dual booting screen I see 3 OS. One is Vista, 2 are Kubuntu 8.10.  How do I remove one of those Kubuntu, so I can see 2 OS instead of 3; like it was before when I have 8.04.

---

### Post by Mardoct909 on 2008-11-15
What are the names of the two Kubuntu ones?

---

### Post by mapes12 on 2008-11-15
Are the 2 Ubuntu OS's different kernel versions?

How did you do the upgrade? Update Manager or fresh install?

---

### Post by MasterSander on 2008-11-15
pls post the output of
```
 cat /boot/grub/menu.lst 
```

---

### Post by XxX_VLAD_XxX on 2008-11-15
> **MasterSander said:**
> pls post the output of
```
 cat /boot/grub/menu.lst 
```

I think you need to run that with sudo, (I prefer gedit)

```
 sudo gedit /boot/grub/menu.lst 
```

but you need to be very careful with it, you safely change the time before it picks your OS automatically 
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

```

change the line
```
 timeout        15 
```

Also you can change the default OS at start, just change the line

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```

change the line to
```
default     4
```

I have done this it works, but I still have the other entries to Ubuntu


If you just don't wanna see the titles of the other entries to Kubuntu,   **MAYBE**   you just need to remove those entries (I use Ubuntu 8.04 LTS). You can change the titles, but I'm not sure about delete them

```

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a1c41db1-eef3-4cce-b3e7-a425e1afc9b7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

#title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a1c41db1-eef3-4cce-b3e7-a425e1afc9b7 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin


```

You just put the title as a comment, BUT I'm not sure, I'm also a beginner at this, I supposed it should work, but I've never tried.

I don't think it's a good idea delete those entries, 'cause they are useful when your system crashes, I actually have tried (recovery mode), you work in a terminal, but being a beginner there was not much I could do.:(

---

### Post by ubitauba on 2008-11-15
This is the output for the dual boot screen:

Ubuntu 8.10, kernel 2.6.27-7- generic
Ubuntu 8.10, kernel 2.6.27-7- generic (recovery mode)
Ubuntu 8.10, kernel 2.6.24-16- generic
Ubuntu 8.10, kernel 2.6.24-16- generic (recovery mode)
Ubuntu 8.10, memtest 86+
Other operating systems:
Windows Vista/Longhorn (loader)

How do I remove the 3 and 4 lines from this boot screen?
There are 3 OS. I used to see just 2. Thanks

---

### Post by Duck2006 on 2008-11-15
> I think you need to run that with sudo

Not if your only viewing the menu.lst, If your editing then,

gksudo gedit /boot/grub/menu.lst

---

### Post by Bartender on 2008-11-15
You refer to this as a problem, but it's not.  The previous kernels are supposed to be there, and as VLAD mentions, you might end up needing the previous version.

---

### Post by ubitauba on 2008-11-15
So,this is normal? Then, should I leave it like this? I'm been using kubuntu for like a week. I had installed kubuntu 8.04, then the very next day I upgraded to 8.10.

---

### Post by Duck2006 on 2008-11-15
> **ubitauba said:**
> So,this is normal? Then, should I leave it like this? I'm been using kubuntu for like a week. I had installed kubuntu 8.04, then the very next day I upgraded to 8.10.

If it all works then lever it as is.

---

