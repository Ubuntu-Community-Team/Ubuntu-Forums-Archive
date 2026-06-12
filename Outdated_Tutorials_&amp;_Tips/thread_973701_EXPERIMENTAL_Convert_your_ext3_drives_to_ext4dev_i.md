---
title: "EXPERIMENTAL: Convert your ext3 drives to ext4dev in Intrepid"
date: 2008-11-06
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2008-11-06
**BIG BOLD WARNING**:

Using ext4/ext4dev at this point is **EXPERIMENTAL** and **ENTIRELY UNSUPPORTED** by Ubuntu developers or the general support community. You are likely **ON YOUR OWN** if anything goes horribly wrong. Please note that this procedure may cause data loss, instability, unbootable systems, or other unforeseen disasters regardless of whether or not you follow these procedures correctly. Since ext4 is still an in-development technology and Intrepid only contains an in-progress snapshot of this development, these instructions may become inaccurate quickly, and existing ext4dev filesystems may require further intervention down the road  to bring to the final "revision" of ext4. Or you might not be able to do that at all. **PROCEED AT YOUR OWN RISK. YOU HAVE BEEN CLEARLY WARNED.** This is intended as a technology preview/overview for daring souls and technically inclined testers.



**Introduction**

Ext4 is the next revision of the extended filesystem, and is designed as an easy migration from existing ext3 systems. It is designed to scale to new storage needs, improve reliability and integrity, and improve performance, particularly with large files. In my experience, I have felt a modest performance improvement on heavy IO loads and a significant performance improvement on manipulating multi-GB large files such as torrents or virtual machine disk images. More information about ext4 can be found at [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4) and [http://ext4.wiki.kernel.org/index.php/Main_Page](http://ext4.wiki.kernel.org/index.php/Main_Page). This guide will assume basic familiarity with the changes. When done properly, this guide allows you to migrate your system to ext4 in-place without the need to reformat.

** What you'll need to do**

First off, GRUB cannot boot off ext4, primarily due to it not being able to read extents. As a result, you **MUST have a separate /boot partition**. Setting up a boot partition is outside the scope of this guide.

This guide is meant to progressively enable ext4 until we are confident the system will boot properly on this new filesystem, before "sealing your fate" by enabling ext4 features that cannot be reversed to ext3 nondestructively.

We will:
[LIST]
[*]Enable the TEST_FS flag to mark the filesystem as ext4
[*]Edit fstab to indicate the filesystem is ext4dev
[*]Ensure ext4dev.ko is added to the initramfs so it can be mounted at boot time
[*]reboot into recovery mode for the first test run
[*]turn on ext4 extents, journal checksumming, and other enhancements of ext4 that are not backwards-compatible (POINT OF NO RETURN)
[*]reboot one last time to activate said features.
[*]Optionally, migrate all files onto extents by a bunch of copy operations
[/LIST]


** Enabling ext4dev flag**
Currently for ext4dev.ko to agree to mounting your filesystem, you must mark the filesystem as "okay to run testing filesystems". This is accomplished by:
```

tune2fs -E test_fs /dev/sda2

```

where /dev/sda2 is your root filesystem. Repeat for each filesystem you intend on changing. **DO NOT DO THIS FOR YOUR BOOT PARTITION,** the reason should be obvious :)

** Edit fstab, regenerate initramfs**
Now, we need to acknowledge in /etc/fstab that these filesystems are ext4dev. In /etc/fstab, change the fstype column of every filesystem you marked  test_fs above, from type **ext3** to **ext4dev**. Do not change any mount options for now.

Next, open **/etc/initramfs-tools/modules** and add **ext4dev** to the list. This ensures that ext4dev.ko and its dependencies are available at boot time to mount the root filesystem. Run:
```

update-initramfs -u

```

to apply those changes to initramfs.

**Reboot into recovery mode**

At this point, we will reboot to make sure that your system can mount ext4dev correctly. Note that although we told the system it's okay to mount these drives as ext4, we have not told the system to apply any non-backwards-compatible changes. That is, currently, your filesystem can be mounted as either ext3 or ext4, so we can go back if something goes wrong (**tune2fs -E ^test_fs /dev/sda2**), but in this state we do not reap the most significant benefits of ext4.

Reboot into recovery mode, and choose a root shell. If you get here, then we're all set to continue.

**Turning on extents and fstab options**

Now comes the good stuff, we will enable ext4-only extents (more efficient representation of large files) and journal async commits and checksums (improves journaling performance and also resists journal corruption):

At your recovery root shell, run
```

tune2fs -O extents /dev/sda2

```

for each filesystem that was marked test_fs originally. Now, all newly created files will be made using the extents format (yes, only newly created file. See last optional step if you're upset about this).

Next, edit **/etc/fstab** again and for each ext4dev mountpoint, append "**,journal_async_commit**" to the options. This option enables journal checksumming, which detects and discards corrupted journal entries so junk isn't tried to be replayed on bad shutdowns. It also reduces the number of sync() calls and barrier (i.e. disk cache) flushes required for write operations, which leads to better write performance.

Reboot to apply these changes too. (Ok technically you don't need to reboot, you can just remount with these options)

**You're now at your final destination**

Congrats! Your filesystems are now fully ext4dev. Continue below for optional stuff.

**OPTIONAL: Converting all files to extent format**

As stated, only new files are created in the extents format. In general, if you have any directories with large files, you probably want to convert them to extents forcibly by copying the directory, and replacing the original directory with the copy. For example, if /srv/torrents is a directory of big torrent files:

```

mkdir /srv/torrents.new
rsync -avHx --progress /srv/torrents/. /srv/torrents/new/.
mv /srv/torrents /srv/torrents.old
mv /srv/torrents.new /srv/torrents
rm -rf /srv/torrents.old

```

I don't expect doing this blindly over the whole system will yield any significant performance improvements, but if you so insist you can perform this procedure on /var /usr /home and /lib too. **CAUTION: PERFORMING THIS ON /usr and /lib and of course /bin MAY LEAD YOU INTO A CATCH-22 WHERE YOU LOSE ACCESS TO THE mv COMMAND. SHUFFLE VERY CAREFULLY, OR DO IT FROM AN INTREPID LIVECD**. Or don't do it at all (recommended). If you're really courageous, here's a procedure that I've used successfully on two of my systems without the need for extra boot media:

[LIST=1]
[*]In recovery mode root shell, use the same rsync commands above to create the /usr.new folder
[*]Repeat for each directory you want to shuffle (or have the space to duplicate in one go). Again, just copy it to the directory.new location. DO NOT DO ANY MOVING AROUND YET
[*]Boot into a busybox shell by appending **break=bottom** to your GRUB kernel boot parameters, from the boot menu
[*]This drops you into a busybox shell after your root filesystem is mounted. Your actual root is at **/root**
[*]Remount your root read-write by **mount -o remount,rw /root**
[*]Run something like 
```
cd /root
mv usr usr.old
mv usr.new usr

```

[*] Repeat that for each directory to shuffle
[*] When done, press CTRL-D to continue bootup.
[*] When you finish booting, remember to remove the *.old directories with rm -rf /usr.old and such.
[/LIST]


**Concluding remarks and stuff to watch out for in the future**

At some point, probably Jaunty's release, **ext4dev** will be renamed **ext4**. Make sure you update **/etc/fstab** and **/etc/initramfs-tools/modules** accordingly at that time!

---

### Post by Penguin Guy on 2010-07-16
The original post is badly out of date, ext4 is now quite stable.

---

