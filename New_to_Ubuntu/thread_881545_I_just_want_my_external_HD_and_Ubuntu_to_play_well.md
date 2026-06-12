---
title: "I just want my external HD and Ubuntu to play well together!"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by fluffydanoob on 2008-08-06
Right, so here I am, walking along, all innocent-like, and I decide that I've had enough of Mandriva, and that someone has probably fixed the Hardy eee PC bugs by now. I install... several times... install the eee-PC kernel from array, load everything back up.

I had some torrents running. Naturally, this being an eee PC with a 4 gigabyte hard drive, it's impossible to be running these on the internal HD, so they're running on a 500 GB Maxtor external.

I notice that they aren't working at all (no actual data accumulating, DL/UL rates in the low-byte range, etc), so I rummage around, then decide perhaps the problem is that Ubuntu installed v1.06 of Transmission and I was using a more recent version on Mandriva.

Soooo... I go down to getdeb.net and install v1.22. For about a minute, everything suddenly starts streaming well... and then they all redline with "Permission denied." I check my HD permissions, and sure enough, it's mounted as ro, and won't let me change it. Curiously, it won't let me UNMOUNT it after I shut down all running programs, so I end up doing a hard reboot after trying to change the mount options to RW a couple times and looking (but not editing) fstab and mtab.

Once we're done rebooting, failing, and rebooting again, I now have an error message that pops up:

**Cannot mount volume.**
Invalid mount option when attempting to mount the volume 'UNTITLED.'

(Classy name I picked when I reformatted the thing, eh?)

Hm. How puzzling. I'm now at my wit's end and can't even get into my data, so I wind up, look at a few threads here, and try this:

sudo mkdir /media/UNTITLED
sudo mount -t /dev/sdc1 /media/UNTITLED

OK, now I have it mounted. It *says* it's mounted rw, but I'm still getting this "permission denied" error. Check mtab, it's there, listed as 'rw'. Check fstab, lingering cdrom assignment on another USB port that I comment out just in case.

Reboot. Back to the same "cannot mount volume" error message when I plug the HD back in, nothing in mtab, nothing in fstab. "Nothing" meaning:
[quote="fstab"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9f751886-9a41-4d25-93e9-66b8a10e37c3 /               ext2    relatime,errors=remount-ro 0       1
# /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/uote]
[quote="mtab"]/dev/sda1 / ext2 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/fluffy/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=fluffy 0 0
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0[/quote]
Now, /media/disk vfat works OK. It's an SD card. Unfortunately, not suitable for lots of data. It's not that big.

So, out comes external hard drive #2. Maxtor 100 GB. I haven't plugged this one in since I was running Mandriva, and I remember spending a good solid wasted day getting it to actually *work* then. It kept mounting as a [read-only] CDROM. I plug it in, it mounts as rw and change on /media/MINE without any trouble (another original volume name, I know.)

Now, once I command-line mount UNTITLED again (sudo mount -t /dev/sdc1 /media/UNTITLED), the last few lines of mtab are:
[quote="mtab"]/dev/sdb1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sdc1 /media/UNTITLED vfat rw 0 0
/dev/sdd1 /media/MINE vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0[/quote]
MINE, of course, is just fine. Transmission can access it just fine (DL'd one megabyte before stopping the test), although there's a little bit of oddity with file transfer. (It's a little finicky, the 100 GB Onetouch III. Chirps like a cricket at this point in its life. This is a Known Issue.)

UNTITLED is still messed up. Transmission can't play with it, and I can't help but notice that the mtab entry doesn't look too similar.

So, my question is:

How do I get my Ubuntu to treat my 500 GB external just like it treats my 100 GB external and my 16 GB card? I'm completely baffled.

---

### Post by natirips on 2008-08-06
If your external HD is in ext format than try```
sudo nautilus /media
```in the terminal and right-click your mounted UNTITLED, the open properties. Under permissions tab change the owner to youself and allow yourself (and maybe everyone else) RW rights.

If it's vfat or ntfs or something else than I'm unable to help you.

---

### Post by fluffydanoob on 2008-08-06
> **natirips said:**
> If your external HD is in ext format than try```
sudo nautilus /media
```in the terminal and right-click your mounted UNTITLED, the open properties. Under permissions tab change the owner to youself and allow yourself (and maybe everyone else) RW rights.

If it's vfat or ntfs or something else than I'm unable to help you.
Sorry, it's vfat. They're all vfat, actually.

---

### Post by silkstone on 2008-08-06
Unmount the drive, then...

Create a new folder as a mount point - let's say /media/UNTITLED

Then gksudo gedit /etc/fstab

Try changing the line to something like this :

/dev/sdc1/ /media/UNTITLED vfat users,auto,uid=user_name,gid=users,umask=007 0 0

(Obviously use your real user_name)

Then mount with

mount /media/UNTITLED

EDIT/ Oh whoops - that's for an internal drive of course, but maybe the format of the line will be of help to you.

---

### Post by fluffydanoob on 2008-08-06
Well, it worked anyway. I tried fiddling with mtab, got a few error messages and watched the thing hang for a while, but after putting that line in fstab, it tested clear.

---

### Post by fluffydanoob on 2008-08-06
> **fluffydanoob said:**
> Well, it worked anyway. I tried fiddling with mtab, got a few error messages and watched the thing hang for a while, but after putting that line in fstab, it tested clear.
Correction: Temporarily. Perhaps only for about a minute - I had to leave to do something. When I got back, the listed properties under "Volume" included "ro" in the string (they started with "rw" when I made the above post). And "rw" in the user-fillable box, but the "permission denied" error is back.

---

### Post by fluffydanoob on 2008-08-06
OK, I've rebooted, and now things are worse. /dev/sdc1 has somehow become my 100 GB external, which is being mounted as UNTITLED. 

Now they're BOTH read-only. So I suppose editing /etc/fstab has somehow made this worse.

What I want to know is this: I've looked at /etc/fstab and /etc/mtab. Where are these hidden default settings that kept getting applied to my 500 GB HD, and are now ALSO being applied to my 100 GB HD, and how can I *fix* this problem?

Why do the icons remain on my desktop, taunting me, after I unmount through the umount command in the terminal?

EDIT: I have rebooted, with the externals unplugged, and replugged. The 100 GB automatically mounted to MINE_ (apparently not liking the folder); the 500 GB pulled up an "invalid mount option" error. Looks like I'm back to square one...

---

### Post by natirips on 2008-08-06
In your place I would read all man pages I could think of being related to this (i.e. man mount) and remove the lines manually added to fstab and mtab.

Why an external vfat (or USB disk in general, I suppose it's USB) would mount as read-only is beyond me except if it has write lock jumper/switch somewhere on it. I know that all my USB sticks (both those with ext and vfat) mount properly in RW mode except when I lock them, than they are read-only.

---

