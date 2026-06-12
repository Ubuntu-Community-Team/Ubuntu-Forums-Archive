---
title: "Mounting problems"
date: 2019-06-29
forum: New to Ubuntu
---

### Post by mwoosley on 2019-06-29
Hello everyone.  While I posted a related question earlier about mounting drives, I believe this new thread is necessary.

When this all started, I wanted to mount my thumb drives with the ext4 file system.  That process didn't work so I mounted them via vfat.  While mounting in vfat worked, it did not provide me the flexibility to backup from key folders without compromising permissions and such.  After receiving quite a few helpful hints, I'm back to trying to get my drives on ext4, however, with very little success.

I used 'parted' to change the drives to use ext4 with 'mkpart primary ext4 0% 100%' in order to change from vfat.  I updated my /etc/fstab file to reflect the updated file system and during the reboot, the mounts failed.

I was directed to enter the command 'systemctl status mnt-do1.mnt'.  

It loaded the fstab file and returned an active status of failed.  
The following additional info appeared as follows:

Where: /mnt/do1
What: /dev/disk/by-uuid/ABCD-1234
Docs: man:fstab(5)
         man:systemd-fstab-generator(8)
Process: 871 ExecMount=/bin/mount /dev/disk/by-uuid/ABCD-1234 /mnt/do1 -t ext4 [COLOR=#ff0000](code=exited status=32)[/COLOR]

Jun 29 14:40:25  me systemd[1]: mounting /mnt/do1...
Jun 29 14:40:25  me mount [871]: mount: /mnt/do1: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program or other error.
Jun 29 14:40:26  me systemd[1]: mnt-do1.mount: Mount process exited, code=exited status=32
Jun 29 14:40:27  me systemd[1]: mnt-do1.mount: Failed with result 'exit code'.
Jun 29 14:40:27  me systemd[1]: [COLOR=#ff0000]Failed to mount /mnt/do1[/COLOR].

Is my filesystem missing?  If so, how could this have happened? (I hope this is an over reaction)

Or is it something simpler that I am overlooking?

I apologize for not taking the necessary steps to view the man pages, but with my current work assignment, I have found it more helpful (not best) to solicit the fields help so  I can get this done in a timely manner.  I will look at the man pages today during my lunch break hopefully.  So far, you guys have been a huge help.

Thanks in advance for any advice you may provide.

---

### Post by Dennis N on 2019-06-29
It's not complicated. On new USB for Linux, I always make a new msdos partition table first. Then an ext4 partition. I give the file system a label and set ownership to my user. I let udisks2 automount them at /media/<myuser>/<label>. No fstab entry is used. This works fine when using rsync for backup. 
Example attached.

---

### Post by TheFu on 2019-06-29
I would caution against using ext4 on any flash media due to the journal aspects.  ext2 would be better if you can't or won't work with a flash-specific file system.  

For less than $25, you can get an external 160G USB3 spinning HDD to use for backups. If you already have an old spinning HDD, you can get an enclosure or "dock" for half that.  ext4 is designed for spinning disks.

But if you are willing to have backups fail without any advanced warning, then using flash media is an option.  When flash storage fails, it stops working completely. No warning.  

Update:
I suppose with weekly backups and not coming close to filling the flash storage, it should last a few years, so the file system wouldn't be an issue.

---

### Post by kpatz on 2019-06-29
After creating the partition you need to format it to the desired filesystem type such as ext2 or ext4.

**sudo mkfs.ext4 /dev/sdb1**

Or if you don't want journaling on your flash drive, use mkfs.ext2 instead.

Also, be careful you specify the correct partition, otherwise you may overwrite something you didn't intend to!

---

### Post by Morbius1 on 2019-06-29
> What: /dev/disk/by-uuid/ABCD-1234

Differnt filesystems have different forms of UUID's. XXXX-XXXX is for vfat or exfat not ext4.

Run this command to verify the uuid number for your partition:
```
sudo blkid -c /dev/null
```

---

### Post by mwoosley on 2019-06-29
TheFu, thanks for advice.  I do have a HD enclosure that I could use for my backups.  I originally purchased 2 128gb thumb drives thinking I could use them for Linux storage and backups.  From what I gather from you, USB sticks are not practical for use in Linux. Is there a good use case for using these?  I don't mind dumping the idea for USB sticks, just want to know if they can be used somewhere in Linux.

---

### Post by mwoosley on 2019-06-29
Morbius1, with that being said, how do you "change" the ID.  Thanks.

UPDATE:  Morbius, I figured out what I was doing wrong and I appreciate your bringing to my attention what I should have recognized right away.  Your offering of help steered me in a great direction.

Thanks.

---

### Post by TheFu on 2019-06-29
> **mwoosley said:**
> TheFu, thanks for advice.  I do have a HD enclosure that I could use for my backups.  I originally purchased 2 128gb thumb drives thinking I could use them for Linux storage and backups.  From what I gather from you, USB sticks are not practical for use in Linux. Is there a good use case for using these?  I don't mind dumping the idea for USB sticks, just want to know if they can be used somewhere in Linux.

When you recreate a new file system, that will change the UUID. Just rerun **blkid** to see the new name. Or you can look in the /dev/disk/by-uuid/ directory to see where the symlinks point.  For flash storage, I prefer to LABEL= instead of UUID= for my autofs mounts. Personal preference.

USB flash sticks have all sorts of practical uses in every OS. It is just the expectation around write cycles and wear levelling that should be considered.  That isn't Linux specific.  NTFS is also a journaled file system and would have the same issues as any other journaled file system with write cycles.  People run entire OSes off flash devices all the time.  The people concerned about write counts have the file systems that are written to constantly either in RAM or to some other media.  Having parts of the OS that seldom get modified, like /usr/ and /lib/ on flash isn't a big deal.

For backups, the question becomes which sort of backups are you doing?  If you are using versioned rsync files that use hardlinks to manage the versions, that isn't the same as using huge tgz files.  The issue with rsync is that storage which appears to be local gets a full copy with every rsync run, while remote rsync tasks get the famous read-diff comparison that rsync is known for.  There are options to change rsync into trusting timestamps instead of just re-copying the files. Check the manpage.  For any other backup tool you use, see if they just call rsync too.

Also, if you are doing daily re-writes of the entire OS, that would lead to failure before doing daily change-only backups.

If you are doing weekly versioned backups, that means about 52 smaller/tiny write cycles a year, so it would be much fewer than daily full copies.  If you are swapping the USB sticks every backup, then each would be used 50% less and should last 2x longer.

I suppose what is practical depends on how long you need/expect flash media to last.

I've destroyed some named brand flash drives in a tiny bit over a year a few times.  Corsair, Samsung, Sandisk ... all by writing data between 50% and 90% full with each cycle.  In theory, they should have lasted for 1,000-10,000 cycles, but on all three, I saw more like 300 cycles before failure.  That is really a different use than backups, at least I hope it is.

---

### Post by mwoosley on 2019-06-30
Dennis N, thank you for your attempt to assist... after a long weekend at my 9 to 5, I finally figured out what I was doing wrong... where I thought I was creating the file system with the utility parted, I was NOT.  I realized after further reading that I had to create my file system from within the shell.  Not sure why I couldn't get it done from parted, but the other way worked.

Thanks again.
Best

---

### Post by mwoosley on 2019-06-30
Thanks kpatz.  Your solution hit the nail on the head.  I was assuming that from within 'parted', my commands there to make file system were working.  Apparently and primarily due to my ignorance, I didn't see it happening.  Once I left 'parted' and performed the command from the shell, everything fell into place.

Thanks and I look forward to seeing more from ya.

Best,
Mike

---

