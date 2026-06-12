---
title: "Hardy 64 Refuses to Boot"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by napzilla on 2008-05-13
I inherited a slick 64-bit workstation from a colleague who just graduated. He convinced my adviser that I was the one most worthy of the machine, and he recommended that I rebuild the system with a fresh Ubuntu installation. I'm afraid I'm not worthy. I've encountered a couple errors that I'm at a loss to explain. I tried installing Hardy 64 from a LiveCD only to end up in the BusyBox. After finding a post on it, I turned one of my flash drives into a LiveDistro and installed from there. My colleague had opted for the fastest but smallest Hard Drive available, so I only had 73 GB to work with. I manually partitioned the entire drive into a single extended partition, and then created 5 logical partitions:

  /boot -- 1.5GB, ext3
  / -- 15GB, ext3
  /usr -- 10GB, ext3
  swap -- 6GB, linux-swap
  /home -- ~35GB, ext3

Everything installed smoothly, with one major hitch. If I try to boot to the Hard Drive, Grub gives me an Error 15. I tried letting Ubuntu do the partitioning itself, but I still had this problem. If I boot to the USB drive, however, the system boots into the newly installed OS just fine. While I've learned as much as possible about Ubuntu and the Linux kernel over the past year-and-a-half, I haven't spent much time fighting with Grub. Here's what I have been able to discern:

1) The system is a Precision Workstation 380 by Dell, and the BIOS is rather confusing. It seems to be set up with some sort of RAID configuration. It has 4 SATA slots listed (0-3), but the drive has been turned off for each one. Turning any one on only yields a "Drive Not Found" message. It also has two "PATA" drives, which appear to be the (unbootable) CD/DVD drives. Finally, the "SATA Operation" is setg to RAID Autodetect / AHCI, which uses RAID if signed drives, otherwise AHCI (I haven't found out what that means yet). I turned off the "Execute Disable" feature, but that didn't help. The actual drive (with the OS and boot sector) is listed in the BIOS Boot Sequence as "03,39320 B: 0 SEAGATE ST373454".

2) If I try to boot to the hard drive, I get

```

GRUB Loading stage1.5

GRUB loading, please wait...
Error 15

```

If I boot using the USB drive and press 'Esc' to access the GRUB menu and 'e' to modify the first option, I see this for root:

```
root  (hd1,4)
```
If I change this to (hd0,0), I get 
```
Error 15, File not found
```

If I change this to (hd1,0), I get
```
Error 17, Cannot mount selected partition
```

If I change this to (hd0,1) or any other permutation, I get
```
Error 22: No such partition
```

I am deducing from this that GRUB is being pointed to the boot partition on the USB drive instead of the Hard Drive. If I could figure out what the address of the Hard Drive's boot partition is, I could try to change that and see if that fixes it.

My question is twofold: 1) Am I on the right path here, and 2) What do I do next? Any input would be greatly appreciated. Thanks,

  --Brian

UPDATE: I managed to get the behemoth online and install gparted, where I learned that the boot sector on the hard disk is at sda5 inside the extended partition sda1. I also noticed that the boot partition didn't have a boot flag, but adding it didn't do any good.

---

### Post by meierfra. on 2008-05-14
Boot from the USB drive and press "esc" to get to the grub menu. Press "c" to get to  the grub command line. Type

```
 find /grub/stage1 
```

The output should be something of the form (hdx,y)  where x and y  are some numbers.

Press "esc" to get back to the grub menu.   Change

root (hd1,4) 


to 

root (hdx,y)


the same way  you changed (hd1,4) to (hd0,O),...


(If " find /grub/stage1" gives "file not found", try "find /boot/grub/stage1" instead)

---

### Post by napzilla on 2008-05-14
> **meierfra. said:**
> Boot from the USB drive and press "esc" to get to the grub menu. Press "c" to get to  the grub command line. Type

```
 find /grub/stage1 
```

The output should be something of the form (hdx,y)  where x and y  are some numbers.


Thanks for the advice, meierfra. When I use

```
 find /grub/stage1 
```

it returns (hd1,4). If I look for /boot/grub/stage1, it tells me it can't find it. Are there any other possible paths?

---

### Post by meierfra. on 2008-05-14
I don't really know much about raid, but I suggest to install grub to the MBR of the ubuntu drive

Boot from the live cd. In a terminal:

```
sudo grub
```

and at the grub prompt:


```
find /boot/grub
```

The output should be (hdx,4), probably (hd1,4) .

```
root (hdx,4)

setup (hdx) 
```


(so if x=1: "root (hd1,4)         setup (hd1)")

Reboot but set your bios to boot from the ubuntu drive.

At the grub menu change (in the usual way):

root (hd1,4)

to 

root (hd0,4)

---

### Post by napzilla on 2008-05-14
grub launches successfully, but when I try
```
 find /boot/grub 
```
it returns another 'Error 15: File not found'
The /boot directory does exist, though, as I can get at it from the bash terminal.

---

### Post by meierfra. on 2008-05-14
Sorry I meant

find /grub/stage1

---

### Post by napzilla on 2008-05-16
Oddly enough, it returns (hd1,4). Is it possible that it's still reading the USB drive?

---

### Post by meierfra. on 2008-05-16
>  Is it possible that it's still reading the USB drive?

yes, why not?  Or did you have the usb drive unplugged?

Did you try 

root (hd1,4)
setup (hd1)

?

---

### Post by napzilla on 2008-05-19
First, let me say that I appreciate your help on this. While I have made some progress in understanding Linux, GRUB is still pretty much a mystery to me.

I think this computer's having abandonment issues. I didn't change anything, and now grub is returning "Not Found" when I search for "/grub/stage1". It also returns "Command Not Found" when I try
```
 setup(hd1,4) 
```
](*,)
Is there a way to tell GRUB to print exactly what it's doing to the screen when it's booting?

I threatened to reprogram it with an electromagnet, but that didn't get me anywhere. In the meantime, I have adopted the "Brian" solution, which was to buy a $10.00 USB stick, set it up as a LiveCD, and boot from there.

---

### Post by meierfra. on 2008-05-19
> setup(hd1,4)

You are missing a space between setup and (hd1,4).

No  idea  why "find /grub/stage1"  no longer works. You might try again.

Did you ever try "setup (hd1)"?


Sorry, I don't have any real advise. Lets hope somebody who knows more about "raid"   reads this thread.

---

### Post by napzilla on 2008-05-27
Sorry, I almost missed your question there. Yes, I did try 'setup(hd1)', and it returned 'Device Not Valid'. I really don't think the thing likes me. Thanks again for all your help. The 'Brian solution' appears to be relatively stable for now, and will hopefully last long enough for me to find the time to find someone who knows 'raid'. I'm also giving the previous custodian of this machine an account on it; perhaps he can shed some insight into the problem.

---

