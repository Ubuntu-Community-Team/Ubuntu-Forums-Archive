---
title: "Unable to hibernate in Ubuntu 12.10 / system not responding after hibernation"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by stelladeli on 2012-12-04
Hello!
After I installed Ubuntu 12.10 through CD and  "alongside Windows" I came across this problem.
 I didn't use Wubi (at least I think so). 
I  am not able to hibernate. Whenever I start the laptop from hibernation  ,a whole screen of "read-error on swap-device" appears. Also I  distinctly remember that the only partition that is mentioned is  /dev/sda5 (ext4) of 366.11 GiB. I do have a /dev/sda6 linux-swap  partition of 2 GiB (equal to size of RAM).

I'm quite worried. I recently replaced my hard drive and installed  Windows 7 and then Ubuntu 12.10. Is it a problem with the hard drive or  the installation???
What should I do? 
Is there a way to fix this?

Thank you very much for your time,effort and consideration in advance!!!

Release 12.10 (quantal) 32-bit, Kernel Linux 3.5.0-19-generic, GNOME 3.6.0

---

### Post by COMECON on 2012-12-04
I'm ***not*** sure if this is the cause of this, but you could try changing the swap partition size to 4GB (theoretically it has to be the double of the RAM, at least I read it on the old installation guides).
You can do it downloading a distribution like PartedMagic, burn it, boot it and then change the size. 
Hope it works to you!
Catbuntu

---

### Post by audiomick on 2012-12-04
> **COMECON said:**
> ...swap partition size to 4GB (theoretically it has to be the double of the RAM, at least I read it on the old installation guides).

This is obselete. These days, slightly bigger than the actual RAM is enough. The same size as RAM should actually work.

---

### Post by COMECON on 2012-12-04
> **audiomick said:**
> This is obselete. These days, slightly bigger than the actual RAM is enough. The same size as RAM should actually work.
Then perhaps it's a problem with fstab or swap isn't mounted OK?

---

### Post by squakie on 2012-12-04
> **audiomick said:**
> This is obselete. These days, slightly bigger than the actual RAM is enough. The same size as RAM should actually work.

If hibernate still works the way it used to, it takes a snapshot of all your physical memory, so you need at least your physical memory size plus some overhead space.  So, if things have changed since the old 2x memory size + overhead, then you would be correct on the bigger than ram size.

But more importantly, to the OP, unless you have processes open that you need to come right back to where you were when you went to hibernate, hibernate is becoming more and more a moot point with the common user and the more modern machines, since they boot almost as quickly.  Hibernate was originally designed such that active processes could be saved in their current state and then the wake from hibernate would be quicker than a full reboot with the old CPU's and memory sizes.  Most modern systems will boot almost as fast as recovering from hibernate.  I personally don't know too many users who actually have processes open when they hibernate.

There have been known issues with hibernate for quite some time.  Hibernate is no longer enabled by default to avoid those problems.  It can be a multitude of errors - maybe one of those generates the error message you are getting - that I don't know.

I just wouldn't use (EDIT: removed "swap" here - as I meant hibernate and didn't even realize I typed wronghere) unless you absolutely have a need for it other than quicker booting.

---

### Post by StinkySQL on 2012-12-05
> **squakie said:**
> I just wouldn't use hibernate unless you absolutely have a need for it other than quicker booting.

We regularly turn off hibernation in our WIndows systems also. It just is not that reliable.

---

### Post by stelladeli on 2013-05-30
Thanks to all of you for replying!!! :)

Should I just ignore the problem? 
It is true, though, that I would very much enjoy having the option of hibernation!!!...

COMECON how can I check if there's a problem with fstab or with mounting of swap?
Please let me know if there is a way to check the above issues. 'Cause changing the size of the partition is a bit drastic and I don't want to ruin my system by doing something wrong.

I already have Gparted Partition Editor. Would that do the work of increasing swap size as efficiently as PartedMagic? Will changing the size of swap interfere with the Ubuntu and Windows OSs and is there a possibility of data loss? If I am to do this, what are the risks?

---

### Post by stelladeli on 2013-05-30
If it's any help, the hibernate error screen shows something like this:

[23859.796020] done.
[23859.004491] video LNXVIDEO:01: Restoring backlight state
[23859.005495] Read-error on swap-device (0:0:31000)
[23859.005444] Read-error on swap-device (0:0:31000)
[23859.005440] Read-error on swap-device (0:0:31016)
[23859.005451] Read-error on swap-device (0:0:31024)
[23859.005455] Read-error on swap-device (0:0:31032)
[23859.005450] Read-error on swap-device (0:0:31040)
[23859.060519] Read-error on swap-device (0:0:0904)
[23859.060525] Read-error on swap-device (0:0:0920)
[...many numbers below in the same fashion...I'm also not really sure about the accuracy of the numbers]
[23859.063399] EXT4-fs (sda5): previous I/0 error to superblock detected
[23849.063408] EXT4-fs error (device sda5): ext4_find_entry:1209: inode #12109704L comm kworker/u:53: reading directory lblock 0
[23859.065360] Core dump to |/usr/share/apport/apport 2349 7 0 pipe failed
[23859.069327] Core dump to |/usr/share/apport/apport 3874 7 0 pipe failed
[23859.069430] Core dump to |/usr/share/apport/apport 2160 7 0 pipe failed
[23859.069667] Read-error on swap-device (8:0:23816)
[23859.069676] Read-error on swap-device (8:0:23824)
[numbers] Core dump to |/usr/share/apport/apport 2543 7 0 pipe failed
Core dump to |/usr/apport/apport 2941 7 9 pipe failed
Core dump to |/usr/apport/apport 2568 7 0 pipe failed
Core dump to |/ust/apport/apport 1 7 0 pipe failed
[23859.888708] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000007
[23850.888708]
[23859.888711] Pid: 1, comm: init Tainted: G            W I  3.5.0.26.generic #42-Ubuntu
[23859.888713] Call Trace:
[23859.888715]  [<c15be940>] panic+0x81/0x17b
[23859.888723]  [<c104ab25>] do_exit+0x745/0x7a0
[23859.888729]  [<c1056872>] ? __sigqueue_free+0x32/0x40
[23859.888732]  [<c104ae24>] do_group_exit+0xa0
[23859.888734]  [<c10591a5>] get_signal_to_deliver+0x175/0x5a0
[23859.888738]  [<c15bdfaa>] ? force_sig_info_fault+0x5a/0x60
[23859.888740]  [<c101091d>] do_signal+0x2d/0x890
[23859.888745]  [<c103e997>] ? kmap_atomic_prot+0xd7/0xf0
[23859.888749]  [<c15be009>] ? is_prefetch.isra.17+0x26/0x130
[23859.888751]  [<c15be7b8>] ? mm_fault_error+0x196/0x1d0
[23859.888754]  [<c15cc0c1>] ? do_page_fault+0x441/0x480
[23859.888759]  [<c114fc28>] ? vfs_write+0xe8/0x160
[23859.888764]  [<c114f070>] ? wait_on_retry_sync_kiocb+0x50/0x50
[23859.888766]  [<c15cbc80>] ? vmailoc_fault+0x176/0x176
[23859.888768]  [<c10113a5>] do_notify_resume+0x85/0xb0
[23859.888770]  [<c15c8c8d>] work_notifysig+0x30/0x37
_

---

### Post by stelladeli on 2013-05-31
More feedback:
I tried to "Suspend" and when I tried waking up the system, I got a frozen screen with the wallpaper, no unity!

Ctrl+Alt+T didn't bring up terminal, so I pressed Ctrl+Alt+f1 which showed a black screen with some kind of recurrent system-respond commands.

Bottom line, every 5-sec attempt to respond, it gave this:
> EXT4_fs error (device sda5): __ext4_get_inode_loc:3637: inode #1048727: block 4194345: comm acpid: unable to read itable block

Any thoughts?

---

### Post by stelladeli on 2013-06-01
Okay, I feel that it's a general bug (after doing some more research).

I receive an "Ubuntu 12.10 has experienced an internal error" reporting **apportcheckresume error**, after forcing restart when the system crashes (trying to suspend or by closing the lid).

I would appreciate any kind of help on the matter. Thank you.

---

### Post by westie457 on 2013-06-01
Have you tried booting into recovery mode and then running the option of a FSCK on the hard drive.

---

### Post by stelladeli on 2013-08-18
I went into recovery mode and into root shell prompt and type 
> mount |grep "/dev/sd*"
and received
> dev/sda5 on/type ext4 (rw,errors=remount -ro)
Does thin mean that sda5 is not mounted? Because that's the partition I want to check. That and also sda6 (the linux-swap partition).

If they're not mounted should my code be 
> fsck -R -n /dev/sad5 ?
Because I tried
> fsck -AR -M
> fsck -ARM
> fsck -M -R -n 
and nothing worked. It only showed me 
> fsck from util-linux 2.20.1

Thank you for your kind help, I am sorry I took so long. Bear in mind I'm a beginner.

---

