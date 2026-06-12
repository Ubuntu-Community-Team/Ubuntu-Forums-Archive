---
title: "Lubuntu 13.10 does not boot, corrupt filesystem?"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by Audiojack on 2014-01-17
I have been using Lubuntu on my laptop for some time now,  it's the first Linux based OS I have owned and I'm still not very well  versed with the finer aspects of the system.
  A couple of days ago the laptop was shutting down regularly when it  ran out of battery, after recharging I left it be until the next day.  Started the computer, it booted up into the passphrase screen for  accessing the encrypted partition (on which pretty much everything is  stored). When I input my password and press enter, it says "cryptsetup:  sda_5 crypt set up successfully", hesitates in that state for a while,  and then enters BusyBox v.1.20.2, the shell interface (with initramfs).
  As I didn't know what to do, I tried to input "exit" but it said> [INDENT]   /init:line 352: can't open /root/dev/console: no such file
 [/INDENT]
and went into Kernel panic.
  I booted into Live mode from my USB and tried accessing the files  thinking that I could just grab my files and reinstall lubuntu, as a  lazy and quick way out of the situation.
  But when I try to mount the main volume, it asks for the passphrase, I  input it and press Connect. It hesitates for a bit and says> [INDENT]   Error waiting for cleartext object after unlocking /dev/sda5Timed out   waiting for object
 [/INDENT]
I press OK and try accessing the volume again, this time it says> [INDENT]   Error mounting /dev/dm1 at /media/lubuntu/*...long filepath...* exited   with non-zero exit status 31: mount: wrong fs type, bad option, bad   superblock on /dev/mapper/lubuntu--vg-root, missing codepage or helper   program, or other error In some cases useful info is found in syslog -   try dmesg | tail or so
 [/INDENT]
After that I installed the Ubuntu Boot-Repair tool and used the "Recommended Repair" Here is the pastebin link for it: [Paste from boot-repair]("http://paste.ubuntu.com/6763482/")
  I tried booting up again and nothing seems to have changed. This is  the point where I ask for help because I cba to fight with it too much,  I'll probably only mess it up more :) Thanks in advance!

---

### Post by ka55o5 on 2014-01-17
> **Audiojack said:**
> encrypted partition (on which pretty much everything is  stored)
Geez.. FYI, next time, it's enough to just have encrypted swap (unless you're planning to have your computer stolen). 
Hope you can get this sorted..:-s

---

### Post by Audiojack on 2014-01-18
Hello... Still working on this. Checked some things in Gparted. It shows /dev/sda1, /dev/sda2 and /dev/sda5. But it doesn't show anything in the "Used" or "Unused" sections for sda2 and sda5...

For sda1 it says *Used 194,43MiB* and *Unused 48,57MiB* which I guess is normal.

I tried "sudo dumpe2fs /dev/sda2 | grep superblock" but it says

> Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2 Couldn't find valid filesystem superblock.

Then I tried "sudo e2fsck /dev/sda2" but it says the same as above plus this

> Could this be a zero-length partition?

Any tips? :)

E: Also tried "dmesg | tail" now, it produces this

> 
[ 3059.644288] Descriptor sense data with sense descriptors (in hex):
[ 3059.644290] 72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 3059.644302] 00 07 c0 1f
[3059.644308] sd 0:0:0:0: [sda]
[3059.644313] Add. Sense: Unrecovered read error - auto reallocate failed
[3059.644316] sd 0:0:0:0: [sda] CDB:
[3059.644318] Read(10): 28 00 00 07 c0 18 00 00 08 00
[3059.644329] end_request: I/O error, dev sda, sector 507935
[3059.644333] Buffer I/O error on device sda, logical block 63491
[3059.644348] ata1: EH complete


E2: Ran the Gpart rescue in Gparted, "No file systems found on /dev/sda - The disk scan by gpart did not find any recognizable file systems on this disk." Does this mean that everything is gone? :P

---

### Post by DuckHook on 2014-01-18
Not good. Yours is an example of the dangers in whole-disk encryption. Do you have backups? If not, I think you have to brace for the probability that your info is lost forever. It is effectively impossible to recover data from a truly borked encrypted disk/partition/directory.

Based on your description of events, it appears that a truncated shutdown (battery running out) corrupted either your partition table or your file structure. In an unencrypted disk, you just run fsck to repair the filesystem. However, this won't work with whole-disk encryption because the filesystem itself is encrypted.

I am not remotely qualified to help you here, but then, this is an Absolute Beginners forum. Perhaps you can ask one of the moderators to move this thread to "Security Discussions" where the real security gurus hang out. You may have better luck with a response there.

What I can tell you is that you should stop accessing the HDD if there is critical info on it that you must recover. Take it out of the computer until a security wizard helps you to decrypt it. On the other hand, if there is nothing much of value on it or you judge the problem to be past solving, then the easiest course of action for you at this point is to reinstall the system, but this time, do *not* select whole-disk encryption or even /home encryption. Instead, encrypt only selective directories post-install. I see that you used LUKS, which I am unfamiliar with. I just use the ecryptfs-setup-private option to set up an encrypted Private directory and dump all of my sensitive stuff in there. ecryptfs is already part of the Ubuntu Linux kernel. Instructions are [here]("https://help.ubuntu.com/community/EncryptedPrivateDirectory").

Last, but far from least, this should motivate you to enact a proper backup regimen.

---

### Post by robin7 on 2014-01-18
Could this happen in a power failure without one of those battery backups?  Or is this issue happening because of all that encryption?

---

### Post by Audiojack on 2014-01-19
Thanks for the replies. There was nothing *critically* important on the HDD which isn't also stored somewhere else... Only one month of data is lost (and most of that is also redoable by hand but it's a huge hassle for me :D). It's not a big deal as such but it would be neat to access the files. I'm always up for trying to fix things before I overwrite the whole system.

---

