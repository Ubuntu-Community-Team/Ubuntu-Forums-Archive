---
title: "Symbolic links to Windows partition break at reboot"
date: 2015-10-29
forum: New to Ubuntu
---

### Post by enrico13 on 2015-10-29
Hello there,

I recently dual-booted a (Win10-preinstalled) computer with Ubuntu 14.04.3 LTS. AFAIK I added nothing funky in terms of packages / programs that should affect the system. That is my first personal computer with Linux on it, though I have had one at work for quite some time (but never really got my hands dirty with the maintenance). Since the Windows partitions (C and D drives) are accessible after a Ubuntu boot but not the other way round, my philosophy going into this was to save everything by default on the Windows part.

My question is how to make "shortcuts" to directories or files on the Ubuntu desktop that can open a file explorer at the desired location in the Win drive.

*Steps taken so far :*

Start Ubuntu. Mount desired drive (/media/me/DATA). Use file explorer and ctrl-shift-move to the desktop, or alternatively open a terminal at desktop location and use ```
ln /media/me/DATA/some_folder -s
``` The link is created and works in the intended way (double-click opens file explorer at target location).

EDIT: Right-click - properties say it is a "link to directory (inode/directory)".

Reboot. Link is still present but broken, and remains so even after mounting the drive (double-click yields "target does not exist" error). (ls-ing the "broken" symbolic link in terminal correctly lists the target directory, but nautilus fails, and anyways I would appreciate the ability to double-click.)

EDIT: Right-click - properties now say it is a "(broken) link (inode/symlink)".

I briefly considered the option to write a script at login that automatically mounts the device and re-creates the links (with an editable txt file with the shortcut targets/names), but (1) I am not sure that is feasible or at least feasible by me and (2) that surely does not look clean.

---

### Post by sandyd on 2015-10-29
There are two different issues:

a) Mounting the Windows partition automatically
This can be done by editing /etc/fstab.

If you post the output of
```

mount -l
```
I can probably provide you with the exact line to add.

b) Creating a symbolic link
Not really needed, Nautilus should be able to create shortcuts.

Right clicking on the folder should have an option called "Make Link", which should create a shortcut. You can drag that to the desktop. Don't know if that applies to 15.04 or 15.10 - switched to Kubuntu since 14.04.

---

### Post by enrico13 on 2015-10-30
For a), here we go:

```
me@me-X550JX:~$ mount -l
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot/efi type vfat (rw) [SYSTEM]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=me)
```

For b), there is indeed a "make link" option but it exhibits the same undesired behaviour (link breaks at reboot and remains broken even once the disk is mounted).

Anyways, if only for auto-mount, I appreciate your help.

---

### Post by sandyd on 2015-10-30
Forgot to mention that you need to run that when it is mounted :)

Also, can I have the output of
```

parted -l
```

---

### Post by Mark Phelps on 2015-10-31
A problem you're going to run into trying to link to files in Win10 from Linux is something known as Fast Startup.  

FastStartup forces Windows to go into hibernation even if you choose Shut Down and when this happens, all open partitions remain mounted, preventing access to those partitions from outside the Windows OS that was running.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

---

### Post by enrico13 on 2015-11-02
@Mark: thank you, but I already took care of that when installing Ubuntu.

@sandyd: OK, did some more homework, found [this tutorial]("https://help.ubuntu.com/community/MountingWindowsPartitions") and applied it to have D: (DATA) automatically mounted at boot. Now the links are working just fine with the methods I tried previously (see first post).

Thanks to all, I will mark that thread as solved.

---

