---
title: "at startup, it says, &quot;The disk drive for /dev/mapper/ubuntu--vg-swap_1 .."
date: 2014-01-22
forum: New to Ubuntu
---

### Post by monsterwizard on 2014-01-22
is not ready yet or not present.

then in Bold text it says,
"**Continue to wait, or Press S to skip mounting or M for manual recover****y**"

I'm not sure what that means, nor do I know what to do about it. I'm still able to use Ubuntu on my hp laptop just fine it seems though.

not sure if this will help, but I have 3.6 GiB of memory, my processor is an AMD E-300 APU with Radeon(tm) HD Graphics x 2,
Graphics are Gallium 0.4 on AMD PALM on my hp laptop. 

Maybe I installed Ubuntu wrong?

---

### Post by fantab on 2014-01-22
Post the output of:

```
cat /etc/fstab
sudo blkid
```

Looks like you either don't have a SWAP partition or the UUID of the SWAP partition must have changed... Lets see what the output to above command says...

---

### Post by monsterwizard on 2014-01-23
ok, the first command output is, 
:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=85fd5b71-39f0-4f9a-a1fe-5e0b0160835a /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

 and for the second command, the output is,
/dev/sda1: UUID="85fd5b71-39f0-4f9a-a1fe-5e0b0160835a" TYPE="ext2" 
/dev/sda5: UUID="682d1847-9d05-460d-9305-419059a54524" TYPE="crypto_LUKS" 
/dev/mapper/sda5_crypt: UUID="YQtIgR-Pgxc-8MF9-6zUy-txJG-QM0S-fAT1A5" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="9f16c90c-8ac6-454d-9978-c1aee8eea247" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="ec5ad80e-792c-4244-85c2-644a8cf8b9d0" TYPE="swap"

---

### Post by monsterwizard on 2014-01-23
Alright, there is the output for those commands, I can't tell from the output if I have a swap or if the swap was renamed, can someone help me? I really am a beginner at this stuff.

---

### Post by Bashing-om on 2014-01-23
monsterwizard; Hi! ,

The thing is, you have added a layer if complexity - encryption - that many here have no experience with. I for one do not know how to trouble shoot in such a situation. 
Patience, there may be few that can help who do see your thread.

[INDENT][INDENT]my regards
[/INDENT][/INDENT]

---

### Post by monsterwizard on 2014-01-23
ok, I'll keep that in mind :). Thank  you Bashing-om, hope someone can help me out soon

---

### Post by joe_beasley on 2014-01-23
**/dev/sda5: UUID="682d1847-9d05-460d-9305-419059a54524" TYPE="crypto_LUKS" **

You have an encrypted swap partition.  It is not available early in the boot process, which causes the error message.  It was probably encrypted with a "key" file, which becomes available later in the boot process.  The blkid output confirms your system sees the swap space.

Your swap partition should be at least 4GB (7GB would be better) for the "Resume" to work properly.

---

### Post by monsterwizard on 2014-01-24
OK, thank you joe_beasley. I think my question has been answered.  I'll mark this thread as answered, I now have a new question, but first I'll try and find the answer among the other threads.

---

### Post by G_Ajith_Kumar on 2014-02-06
@monsterwizard

i had the same problem after I installed Ubuntu 14.04. The same problem had surfaced on Ubuntu 12.04 too and hence i had switched to 14.04. i found the following solution working well for me in all aspects. I found this from [http://askubuntu.com/questions/364136/dev-mapper-ubuntu-vg-swap-1-is-not-ready-or-not-present](http://askubuntu.com/questions/364136/dev-mapper-ubuntu-vg-swap-1-is-not-ready-or-not-present) by Micheal Kearney


To get the moose, format the linear virtual block device:

  
[LIST]
[*]Boot into recovery mode (by pressing shift while the system begins to boot and the log is being dipslayed)
[*]Select Drop to root shell prompt (in the advance options)
[*]mount drive in read-write mode:  mount -o remount, rw /
[/LIST]
  Check it:
  $ dmsetup -v table /dev/mapper/ubuntu--vg-swap_1
  Turn off swap:
  $ swapoff -a
  Format the swapfile:
  $ mkswap /dev/mapper/ubuntu--vg-swap_1
  Edit /etc/fstab and Comment out any other swap files (by using nano, vi, vim or any other terminal editor):

  /dev/mapper/ubuntu--vg-swap_1 none swap sw 0 0
#/dev/mapper/cryptswap1 none swap sw 0 0
#/swapfile1 swap swap defaults 0 0

(Save the file)
  Reboot.
  Press CTRL-ALT-T
  Was the swap file allocated to swap by fstab? We should have 888MB:
  $ free

Swap:       909308      0     909308
  Is the linear virtual block device encrypted? dmsetup will return "crypt":
  $ dmsetup status

sda5_crypt: 0 624637944 crypt

---

