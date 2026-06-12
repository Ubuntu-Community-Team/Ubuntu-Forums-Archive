---
title: "Fstab issue with securing /tmp and /var/tmp"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by bronky on 2013-04-02
Dear Users,

I run a small Ubuntu server 12.04 LTS and want to secure the /tmp and /var/tmp

I followed this tutorial:
[http://www.cyberciti.biz/faq/howto-mount-tmp-as-separate-filesystem-with-noexec-nosuid-nodev/](http://www.cyberciti.biz/faq/howto-mount-tmp-as-separate-filesystem-with-noexec-nosuid-nodev/)


but I did something wrong (or i think) because when i restart the server i needed to skip the /tmp mount:
```

fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
/dev/md0: clean, 105386/90816512 files, 29678902/363248592 blocks
mount: Not a directory
mountall: mount /tmp [774] terminated with status 32
mountall: Filesystem could not be mounted: /tmp
/dev/sda1: clean, 236/73152 files, 69584/291840 blocks
Skipping /tmp at user request
 * Stopping Failsafe Boot Delay[122G[ OK ]
 * Starting System V initialisation compatibility[122G[ OK ]
...

```


So i double checked my /etc/fstab  and it looks like this now:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=3be44300-a359-4331-aeaf-66ea5d34af2f /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=e4e854ae-dbed-4d75-8a73-db4ddf9079dc /boot           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=d2488844-5ab7-45d6-bd39-c016b1790267 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=c89d20e4-e028-442d-a854-df6c04e4262c none            swap    sw              0       0
/root/images/tmpfile.bin   /tmp   ext4    rw,noexec,nosuid,nodev,bind    0 0
/tmp /var/tmp none rw,noexec,nosuid,nodev,bind 0 0

```


Now I thought... mmh perhaps i need the UUID from this last lines i added? I found that /dev/loop0 is the tmp (or that is what i think)

```

root@Linoa4:~# blkid
/dev/loop0: UUID="adc7764a-b9c0-4a67-b21b-e423241059cd" TYPE="ext4"
/dev/sda1: UUID="e4e854ae-dbed-4d75-8a73-db4ddf9079dc" TYPE="ext4"
/dev/sda5: UUID="d2488844-5ab7-45d6-bd39-c016b1790267" TYPE="swap"
/dev/sda6: UUID="7b56dfa9-202f-b116-fbda-baa98f9c4180" UUID_SUB="4dc96268-8c65-60da-95d0-a25254de6d76" LABEL="ubuntu12:0" TYPE="linux_raid_member"
/dev/sdb1: UUID="b70d9aed-9af1-4b02-aec2-4010e144b36b" TYPE="swap"
/dev/sdb5: UUID="c89d20e4-e028-442d-a854-df6c04e4262c" TYPE="swap"
/dev/sdb6: UUID="7b56dfa9-202f-b116-fbda-baa98f9c4180" UUID_SUB="892c7c8a-c793-278f-c7e4-a64246a4f6c0" LABEL="ubuntu12:0" TYPE="linux_raid_member"
/dev/md0: UUID="3be44300-a359-4331-aeaf-66ea5d34af2f" TYPE="ext3"

```

So should i now make the /tmp line as following in fstab:
```

UUID=adc7764a-b9c0-4a67-b21b-e423241059cd /root/images/tmpfile.bin   /tmp   ext4    rw,noexec,nosuid,nodev,bind    0 0
/tmp /var/tmp none rw,noexec,nosuid,nodev,bind 0 0

```


(what about that last line "/tmp /var/tmp" does this need UUID also?)

Unfortunately I can't test to much because the server is live, so I would like to have it right and correct the next time on reboot...


When i followed the instructions from the tutorial, there are no issues only after reboot (so it must be the fstab) and my tmp seems to be secure, these lines i used:
```

mount -o loop,rw,nodev,nosuid,noexec /root/images/tmpfile.bin /tmp
chmod 1777 /tmp
mount -o rw,noexec,nosuid,nodev,bind /tmp /var/tmp

```

---

### Post by schragge on 2013-04-02
The first line is loop-mount, not bind-mount.
```

/root/images/tmpfile.bin   /tmp   ext4    [COLOR=#ff0000]loop[/COLOR],rw,noexec,nosuid,nodev    0 0
/tmp /var/tmp none rw,noexec,nosuid,nodev,bind 0 0

```
Or omit it altogether. Recent *mount* versions are smart enough to understand that it should loop-mount a regular file:
```

/root/images/tmpfile.bin   /tmp   ext4    rw,noexec,nosuid,nodev    0 0
/tmp /var/tmp none bind 0 0

``` Also, bind-mount always inherits mount options of the original mount point, so there's no point in repeating them in the second line.

[highlight]Update.[/highlight]
*dpkg* caches post-installation scripts in */tmp* and executes them from there. So it needs */tmp* to be mounted exec, otherwise you'll get warnings from dpkg during upgrades. To make *dpkg* happy, add the following to the file */etc/apt/apt.conf*:
```

DPkg::Pre-Invoke {"mount -o remount,exec /tmp";};
DPkg::Post-Invoke {"mount -o remount /tmp";};

```

---

### Post by bronky on 2013-04-02
@ Schragge, thx for the clear answer! it seems that the tutorial is then wrong... because there he writes the "bind" mount for /tmp
Thx again!

next you write about changing/adding the  apt.conf
I checked my server but i don't seem to have a apt.conf  i do have a /etc/apt/apt.conf.d/ with some files in it... and I have a /etc/apt/preferences.d/ directory
What do you suggest? should i create a apt.conf in /etc/apt/apt.conf ? (/etc/apt/apt.conf.d has no apt.conf)

**Update, found the answer:**
[http://askubuntu.com/questions/196059/how-to-modify-settings-in-apt-conf-file-that-no-longer-exists-in-12-04](http://askubuntu.com/questions/196059/how-to-modify-settings-in-apt-conf-file-that-no-longer-exists-in-12-04)

[COLOR=#333333][FONT=Ubuntu Beta]It is best to create your own user file in /etc/apt/apt.conf.d so you can guarantee that it won't be overwritten by package updates. Rather than adding to existing files in the directory, create your own general file called 99mysettings with[/FONT][/COLOR]

sudo touch /etc/apt/apt.conf.d/99mysettings [COLOR=#333333][FONT=Ubuntu Beta]It is labelled with a 99 so that your settings are run last and so override any of the same values for the specified settings present in other files in the directory.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Then to edit your file run[/FONT][/COLOR]

sudo nano /etc/apt/apt.conf.d/99mysettings [COLOR=#333333][FONT=Ubuntu Beta]and then:
[/FONT][/COLOR]```


DPkg::Pre-Invoke {"mount -o remount,exec /tmp";};
DPkg::Post-Invoke {"mount -o remount /tmp";};
```

---

