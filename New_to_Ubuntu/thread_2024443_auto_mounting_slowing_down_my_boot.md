---
title: "auto mounting slowing down my boot"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by degarb on 2012-07-13
I noticed my bootup to ubuntu is hanging trying to auto mount all 8 partitions.  I only need to mount the linux on boot.  No idea how to disable this.  If I am infront of computer I can hit s to skip the mounting.  But this is not practical on a a day to day basis.

fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda5 during installation
UUID=ff11fbaa-94bb-4f80-a931-445a2f224432 /               ext4    errors=remount-ro 0       1

# /windows was on /dev/sda1 during installation
#UUID=3ECC2741CC26F337 /windows        ntfs    defaults,umask=007,gid=46 0       0

# swap was on /dev/sda2 during installation
UUID=fa0ac7e1-6154-4e96-afc7-37865af56e71 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by drs305 on 2012-07-13
You can add the 'noauto' option to any extra partition listed in fstab, or you can turn off automounting in general with:
```

gsettings set org.gnome.desktop.media-handling automount "false"
```
If you would like to explore this option via a GUI, install dconf-tools and then open dconf-editor.

---

### Post by NikTh on 2012-07-13
> **drs305 said:**
> You can add the 'noauto' option to any extra partition listed in fstab, or you can turn off automounting in general with:
```

gsettings set org.gnome.desktop.media-handling automount "false"
```If you would like to explore this option via a GUI, install dconf-tools and then open dconf-editor.

Hi , 
i thought that correct command was 
```
dconf write /org/gnome/desktop/media-handling/automount '"false"'
```Am i wrong ? 
Or its the same ? 
Thanks

---

### Post by drs305 on 2012-07-13
> **NikTh said:**
> Hi , 
i thought that correct command was 
```
dconf write /org/gnome/desktop/media-handling/automount '"false"'
```Am i wrong ? 
Or its the same ? 
Thanks

When I run the command as I posted it ticks/unticks the settings box in dconf-editor, which is what it should do.

When I ran your command, it changed the tickbox to the word "false". I don't know if that does the same thing or not, but in dconf-editor the true/false items are all tickboxes, unlike gconf-editor, where there are 'true/false' entries. I tried your command (altered) on the confirm-trash setting. It changed from a tickbox to 'false' but it didn't appear to work as it still asked for confirmation.

---

### Post by NikTh on 2012-07-14
> **drs305 said:**
> When I run the command as I posted it ticks/unticks the settings box in dconf-editor, which is what it should do.

When I ran your command, it changed the tickbox to the word "false". I don't know if that does the same thing or not, but in dconf-editor the true/false items are all tickboxes, unlike gconf-editor, where there are 'true/false' entries. I tried your command (altered) on the confirm-trash setting. It changed from a tickbox to 'false' but it didn't appear to work as it still asked for confirmation.

Ok . Thanks for info @drs305 
:)

I saw that myself. When reboot pc , it resets the values . Tick-boxes again , no matter if changed before in false or true.
Gsettings do the right "job" .

---

