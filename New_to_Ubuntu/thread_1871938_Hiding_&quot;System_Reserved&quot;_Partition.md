---
title: "Hiding &quot;System Reserved&quot; Partition"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by antoinethewiz on 2011-10-29
I have xubuntu installed through wubi and there's a partition labeled "System Reserved" that's mounted under /media. I'm a command line kind of guy so I'm not sure how to get rid of that annoying icon on the desktop. I tried unmounting it via terminal with "umount /dev/sda1". But the icon is still there (though it IS faded on the file manager).  ](*,) I guess it stays there because the device is still "plugged in". But it's not actually removable media, it's the partition to boot Windows 7.

Oh, and don't tell me "Settings > Settings Manager > Desktop > Icons, untick 'Removable Devices'" because I still want to see removable devices, just not this one. Thank you for taking your time to help me with this minor annoyance. ):P

---

### Post by coffeecat on 2011-10-29
That's what I don't like about the Xfce desktop - icons for all your partitions appear on the desktop, unless you switch them off and then the ones you do want don't appear. You should have seen my desktop on the machine I am posting from when I put Xubuntu on a spare partition, one of about a dozen. I could barely see the wallpaper! :wink:

However, the partitions are not mounted by default - it's just that the icons are there making it easy for you to mount them. When you next boot up, don't double-click the System Reserved icon, but open your home folder and look at the list in the left pane. The System Reserved partition will probably be there but shouldn't be mounted unless you click on it.

By the way, this is all from memory - so I may have got some of the details wrong. Hopefully, someone with more experience of the Xfce/Xubuntu desktop will comment, and may know of a way round this. In which case I'll be very interested. But the thought of being able to easily mount the Windows System Reserved partition fills me with horror.

---

### Post by coffeecat on 2011-10-29
Hi - I've rebooted into Xubuntu (11.10) to check and I got it almost right. Don't double-click on the System Reserved icon and open a Thunar window - your home folder. The icon in the left pane for System Reserved will be grey - as you say - and the partition will not be mounted until you click on it. It will then be mounted on a dynamic mountpoint in /media as you have discovered.

However, this does not answer your question as to how to get the icon off the desktop without losing icons for true removable media. Let's hope an Xubuntu expert will be able to answer.

And a belated welcome to the forum! :)

---

### Post by antoinethewiz on 2011-10-29
[SIZE=1]Thanks for responding in such a timely manner. So this is only with Xfce then? That's a shame, Xfce is so pretty.:KS I suppose I'll just have to wait for a Xubuntu expert to come around then... or at least someone that knows some fancy hackery which I can apply. It's scary how easily you can mount this drive. I didn't even know the differ, all I did was open the drive on the desktop (which appears like any other mounted drive). In any case, I'm not going to touch that drive (or let any "guests" touch it).
[/SIZE]

---

### Post by JKyleOKC on 2011-10-29
Post your /etc/fstab file here, surrounded by "code" tags (highlight all lines of the file after pasting them into a message, then click the "#" icon at the top of the editor) so we can see exactly where the problem drive is being mounted. In every version of XFCE that I've used, the only icons automatically displayed on the desktop are for drives mounted in the /media directory. If your "System Reserved" partition's mount point in the fstab file is a folder in "/media" you should be able to create a mount point of the same name in the "/mnt" directory, then change fstab's mount point from "media" to "mnt" and reboot to achieve exactly what you want (although you may need to remove the old mount point from /media; **don't** do it with the drive mounted however or you might erase all its content).

---

### Post by antoinethewiz on 2011-10-29
**cat /etc/fstab**::
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```"System Reserved" doesn't appear to be here, only the stuff on loop0.
[B]
cat /proc/partitions[/B]::
```

major minor  #blocks  name

   7        0   18169856 loop0
   8        0  244198584 sda
   8        1     102400 sda1
   8        2  244093952 sda2

```**mount**::
```

/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wizard/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wizard)
/dev/sda1 on /media/System Reserved type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

---

### Post by JKyleOKC on 2011-10-30
Apparently it's being mounted by the gvsf utility; I don't know enough about that to be able to tell you how to change its mount point. Hopefully some one else will show up with that information!

---

### Post by antoinethewiz on 2011-10-30
> **JKyleOKC said:**
> Apparently it's being mounted by the gvfs utility; I don't know enough about that to be able to tell you how to change its mount point. Hopefully some one else will show up with that information!

Thank you for the effort. GVFS must be the virtual file system used by Wubi to host itself onto Windows. I'll probably end up upgrading Wubi Xubuntu to a real partition anyway as soon as I figure out all my Windows app replacements (Wine?). Still, the knowledge of this solution would be very satisfying (plus, I most likely won't find app replacements soon due to procrastination) and probably helpful to a lot of other Wubi users.

---

### Post by coffeecat on 2011-10-30
I believe the functionality of mounting internal partitions from the GUI is the same in Xfce as in Gnome. You get the clickable entries in the left pane of the file browser in both, and in both the system automounts partitions to dynamic mountpoints in /media. The difference is that Gnome only shows desktop icons (or launcher icons in Unity) for mounted partitions. I'm afraid you'll see the same with Xubuntu installed natively to its own partition (which is what I have). In fact, it'll be worse. Your Windows C: partition will have its own icon on the desktop as well

---

### Post by Elfy on 2011-10-30
This might help.

[http://goodies.xfce.org/projects/panel-plugins/xfce4-gvfs-mount](http://goodies.xfce.org/projects/panel-plugins/xfce4-gvfs-mount)

I've not used it as I am happy to have no drives at all on the desktop - used to do the same in gnome.

---

### Post by antoinethewiz on 2011-10-30
> **forestpiskie said:**
> This might help.

[http://goodies.xfce.org/projects/panel-plugins/xfce4-gvfs-mount](http://goodies.xfce.org/projects/panel-plugins/xfce4-gvfs-mount)

I've not used it as I am happy to have no drives at all on the desktop - used to do the same in gnome.
Nah, it does the same as umount.
```
gvfs-mount -u "/media/System Reserved"
```

---

### Post by JKyleOKC on 2011-10-30
I looked for the code on that link but could not find it. However this panel plugin seems to have not been touched since 2009, and the description sounds as if it might do the same thing as "gigolo" which is what I use to manage mounting of remote systems. Like forestpiskie, I have my desktop configured not to show file systems automatically, just any launchers in my ~/Desktop directory...

---

