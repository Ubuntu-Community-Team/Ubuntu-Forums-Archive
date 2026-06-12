---
title: "[SOLVED] External HD not automounting after updates"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by roscal on 2008-11-29
Hi,
I have an external USB 250gig HD (formatted EXT3) which previously just auto-mounted, no problems.
After downloading a bunch of updates for Hardy , now I plug the USB drive in, and nothing happens?
Any hints on how to access this drive would be appreciated. 
Thanks.

---

### Post by taurus on 2008-11-29
Is it /dev/sdb1?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
You can try to see if you can mount it by hand from a terminal, assuming it is /dev/sdb1.

```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
df -h
```

---

### Post by Xiong Chiamiov on 2008-11-29
A nifty way of mounting things temporarily, which doesn't require creating folders or having root priviledges, is pmount (you may have to install it).  Using that, the previous suggestion would become:
```

pmount /dev/sdb1
df -h

```
and unmounting is simply
```

pumount /dev/sdb1

```
The /media/sdb1 folder will be automatically created when you mount and destroyed when you unmount.

---

### Post by roscal on 2008-11-29
sudo fdisk -l gives me this:

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15298   122881153+   7  HPFS/NTFS
/dev/sda2           15299       38913   189687487+   5  Extended
/dev/sda5           15299       38583   187036731   83  Linux
/dev/sda6           38584       38913     2650693+  82  Linux swap / Solaris


I think it should be sdb, 1 etc..., but nothing is showing.
It automounted before I updated, now, nothing shows?

---

### Post by taurus on 2008-11-29
Assuming the drive is on and plugged in, what's the output of this message from a terminal?

```
dmesg | tail
```

---

### Post by roscal on 2008-11-29
The drive is powered and plugged in.
Here's the output from dmesg | tail 


[ 6206.516106] usb 3-1: USB disconnect, address 4
[ 6816.195188] usb 3-1: new high speed USB device using ehci_hcd and address 5
[ 6816.330459] usb 3-1: configuration #1 chosen from 1 choice
[ 6816.331255] hub 3-1:1.0: USB hub found
[ 6816.331627] hub 3-1:1.0: 4 ports detected
[ 6816.453607] usb 3-1: USB disconnect, address 5
[ 6816.758902] usb 3-1: new high speed USB device using ehci_hcd and address 6
[ 6816.896748] usb 3-1: configuration #1 chosen from 1 choice
[ 6816.897533] hub 3-1:1.0: USB hub found
[ 6816.897911] hub 3-1:1.0: 4 ports detected

---

### Post by roscal on 2008-11-29
I've just downloaded a further 38 updates.
Going to reboot,and try the external again to see if there is
any luck.
Thank you all for replying, I'll be back in a while, I suspect.

---

### Post by roscal on 2008-11-29
I****t still doesn't work.

I have a new sdb1 file in my root /media/directory, although it's
empty
.
How can I mount this external HD?
It always just auto-mounted and showed a drive icon on the screen
.
No more, since updating I can't access it.
What's happened?

Here is sudo fdisk -l:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15298   122881153+   7  HPFS/NTFS
/dev/sda2           15299       38913   189687487+   5  Extended
/dev/sda5           15299       38583   187036731   83  Linux
/dev/sda6           38584       38913     2650693+  82  Linux swap / Solaris

**Where's my external drive gone??**

---

### Post by roscal on 2008-11-29
:)I've found somewhat of a solution thanks to a previous post by 
'corkscrew' :

[I]plug your drive in, then open a a terminal and type 
Quote:
 lsusb 
i think this forces pc to rescan usb ports a few seconds later and drives are mounted[/I]

This worked for me, my external got mounted right away...
:):lolflag:

---

