---
title: "Mounting dynamic spanned disks at boot time and binding through fstab"
date: 2013-11-25
forum: New to Ubuntu
---

### Post by rogiervandam on 2013-11-25
I have managed to mount two disks as a dynamic spanned NTFS volume.
With the commands:
[COLOR=#0000ff][FONT=courier new]sudo dmsetup create ntfs-spanned /etc/ntfs-spanned
sudo mount -t ntfs-3g /dev/mapper/ntfs-spanned /mnt/ntfs-spanned[/FONT]
[/COLOR]I get the disk working correctly.

But now I want the disk to come up at boot time
and want to mount-bind some directories in fstab.
I tried this fstab:

/dev/mapper/ntfs-spanned ntfs-3g defaults,windows_names,locale=en_US.utf8 0 0
/mnt/ntfs-spanned/video /home/share/video none bind 0 0
/mnt/ntfs-spanned/music /home/share/music none bind 0 0 

but i have to get my dmsetup up and running before fstab.
I tried putting the dmsetup command in 
/etc/rc.local
/etc/init/mountall.conf
/etc/init/ntfs-spanned.conf with a script found here: [http://blog.kylemanna.com/linux/2013/06/30/ssd-caching-using-dmcache-tutorial/](http://blog.kylemanna.com/linux/2013/06/30/ssd-caching-using-dmcache-tutorial/)

but none of this works: On startup, Ubuntu server complains some fstab mappings are not ready or available.

What am I doing wrong? Is this a timing problem? What is the proper place for dmsetup? Or should I use another method in the first place?

---

### Post by DuckHook on 2013-11-25
Some guru might get this working for you, but for absolute beginners, even if it is eventually achieved, it will always be extremely fragile. It goes without saying that fragility is not a desirable trait when dealing with something as critical as HDDs.

I'm not an expert here&#8213;wish a guru would step in&#8213;but to my knowledge, dynamic spanning is a MS technology that suffers from the usual drawbacks of proprietary jailware: it is closed source and therefore obscure, and any attempt by Linux to work with it must be done through reverse engineering and a large amount of guess-and-golly. Those are not the foundations that I would want to rely on for my disk access.

The Linux equivalent is LVM, which is open-source and conforms to open standards. I can tell you from personal experience that LVM is robust and extremely versatile. But it works on Linux formats (don't know if it will work on NTFS, and even if it did, Windows can't read it).

Perhaps we could better advise you if you told us what you are trying to ultimately achieve. I note again that you should take what I say with a grain of salt, but with that warning in mind: it is generally unwise to mix Windows infrastructure with Linux apps/utils/system tools.

---

### Post by rogiervandam on 2013-11-25
I got the dynamic disk spanning working perfectly. Just a bit of sector calculations and trial and error.
I'm trying to migrate from a windows 7 dedicated home server to a ubuntu based zpool server.
I'm not ready yet for zpool, so i want to reuse the current structure on the ubuntu services.
I still have my old windows startup drive and it is nice to know i'll have a fallback.

---

### Post by DuckHook on 2013-11-25
If you are prepared to take the chance and you backup your drives religiously, then this is what I know:

I often also run into the problem of NAS drives not being ready for fstab. I don't use NTFS or SAMBA&#8213;everything is NFS around here&#8213;but I suspect that the root causes are similar: automount fails either because the drives aren't ready or the drivers have not yet loaded. With NFS there is an option *_netdev* that tells the automounter to wait until network modules are loaded before forging ahead in its brainless determination to complete the mount. Even when the system waits for the network modules to load, my automounts will still often fail because my NAS has gone into sleep mode (which I want) and it takes a quite a few seconds for the disks to spin back up and the NAS to waken. This also caused an even bigger problem on powerdown: if my NAS went to sleep while the system still had an NFS link open, then it would wait forever for a formal dismount before finishing the powerdown. This had the effect of not only freezing the powerdown, but possibly not flushing my caches properly, which was potentially disasterous.

I lived with the problem for years until these very forums pointed me to a truly elegant solution. Instead of mounting in fstab, I now mount all remote drives using *autofs*. Since *autofs* only mounts a volume when the user makes a call to it, it:

1. will not attempt to mount anything during the boot process, thus giving your system all the time it needs to load whatever drivers that it needs,
2. will automatically dismount the same drive after 10 minutes of inactivity, which forces a cache flush and ensures that no unresponsive mounts are still hooked into my system at powerdown.

Since *autofs* works with CIFS, you should be able to delete your fstab entries and rely on it for all of your NTFS filesystems. Since I don't work with Windows formats, you will have to Google for further instructions, but it should not be hard to configure your system that way.

---

