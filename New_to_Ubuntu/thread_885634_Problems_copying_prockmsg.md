---
title: "Problems copying /proc/kmsg"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by BetterSense on 2008-08-10
I bought a new 1TB hdd. Since I didn't want to reinstall, I used a Livecd to partition it into a 12GB bootable and the rest normal, both ext3.

Then I booted from my old hdd, mounted the the big partition on a directory in my /home, and 

```
sudo cp -rv /home/* ~/petanybblehomemnt
```

So this copied my whole home over to the new drive. Then I tried to do the same with the rest of my install, this time I mounted the small partition

```
sudo cp -rv /bin /boot /proc ...(everything but /home)...  ~/petanybblerootmnt
```

The problem is this time it didn't work, but stalled on /proc/kmsg. All night. 

I tried 
```
less /proc/kmsg
```
and that also froze. I can't even cntrl+C to get out of less. 

is /proc/kmsg like some black hole file or something?

---

### Post by ingeva on 2008-08-10
> **BetterSense said:**
> is /proc/kmsg like some black hole file or something?

Something like that!

Something like a virtual (non-existent) directory containing information about currently running processes.

Please excuse me if it isn't 100% correct, but I think it's close enough for the purpose.

Naturally, it's not copyable. Too bad you don't get a warning message.

---

### Post by stumac on 2008-08-10
/proc is a pseudo file system that resides in ram.  You do not need to back it up.

for more info
```
  man proc 
```

---

### Post by hyper_ch on 2008-08-10
I would have run from the live cd

```

sudo dd if=/dev/sdX of=/dev/sdY

```

where sdX is your old drive and sdY the new one.

---

### Post by BetterSense on 2008-08-10
thanks for the info about /proc. So I can fail to copy the whole /proc directory and my install will work, once I boot from the new drive? I also have to figure out how to install grub on it.


 And the suggestion

```
sudo dd if=/dev/sdX of=/dev/sdY
```

Why would you do that, instead of copying? The manpage says 'dd-convert and copy a file'. I'm not sure I understand what makes this practically different from cp. 

Also, would this copy the whole drive (both partitions at once)? Do you mean you would have skipped the format and partition step I did?

---

### Post by hyper_ch on 2008-08-10
dd will make a 1:1 copy of the harddisk... including partitioning scheme - which you would have to alter afterwards.

---

### Post by BetterSense on 2008-08-10
Why would I have to alter it? Only if I want a partitioning scheme different than the source disk, right? I suppose if it copied the partitioning scheme exactly, I would be left with a lot of free space on my new  bigger hdd, is that what you mean?

---

### Post by hyper_ch on 2008-08-10
it would be unpartitioned space

---

### Post by BetterSense on 2008-08-10
ok roxxorz. kthx.

---

### Post by BetterSense on 2008-08-10
Actually, if I use dd I can't change my filesystem then, right? Because I had planned to switch from ReiserFS(3) to like xfs just for giggles. But, it's no big deal if I have to have my /home in ReiserFS again, I guess.

---

