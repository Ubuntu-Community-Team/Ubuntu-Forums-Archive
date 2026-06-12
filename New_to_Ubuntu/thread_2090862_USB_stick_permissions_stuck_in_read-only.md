---
title: "USB stick permissions stuck in read-only"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by sayofethos on 2012-12-03
Hi all,

I have a problem writing on my USB stick. It reads fine in both my Mac OS X and also Windows 7, even Linux Mint, but Ubuntu persists it is read-only. Below is the entry from the terminal after inserting the drive and typing command " mount ":

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sampsa/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sampsa)
/dev/sdb1 on /media/Cruzer type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

This is my first week of using Ubuntu, any ideas how to overcome this?

Thanks a lot!

---

### Post by Autodave on 2012-12-03
> **sayofethos said:**
> Hi all,

I have a problem writing on my USB stick. It reads fine in both my Mac OS X and also Windows 7, even Linux Mint, but Ubuntu persists it is read-only. Below is the entry from the terminal after inserting the drive and typing command " mount ":

This is my first week of using Ubuntu, any ideas how to overcome this?

Thanks a lot!

Have you tried highlighting the USB and then clicking on PROPERTIES and then PERMISSIONS and changing the settings?

---

### Post by techvish81 on 2012-12-03
type "gksu nautilus" without the quotes in terminal, give your password.  a nautilus window will open with administrator privilleges , go to your usb drive and right click it , go to properties>permissions , change the second permission to read and write for your username. done:-)

---

### Post by squakie on 2012-12-03
If you can read/write only via the super user (sudo......), then it might also be a couple of other things.

(1) did you create and are using another userid which does not have administrative rights?

(2) what brand/type of USB stick?  There used to be, and perhaps maybe still is for certain ones, a need to put an entry granting the r/w priviledges in a file in the udev rules for when the USB device is mounted.

---

### Post by sayofethos on 2012-12-04
> **squakie said:**
> If you can read/write only via the super user (sudo......), then it might also be a couple of other things.

(1) did you create and are using another userid which does not have administrative rights?

(2) what brand/type of USB stick?  There used to be, and perhaps maybe still is for certain ones, a need to put an entry granting the r/w priviledges in a file in the udev rules for when the USB device is mounted.

1) No, I only have one user account in Ubuntu.

2) The USB is an 8gb Scandisk Cruzer. I formatted it to FAT with Ubuntu a bunch of times trying to solve the issue, but this was not enough.

I did what techvish81 suggested above and the USB seems to be working fine now, even after ejecting it allows to write on the flash drive. However, I was prompted with an error screen after the terminal command " gksu nautilus " which I forgot the text of. I took a "print screen" picture of it, but can't find the file itself anywhere. Below is what the terminal said:

sampsa@1225C:~$ gksu nautilus
Initializing nautilus-gdu extension
Shutting down nautilus-gdu extension

(nautilus:2535): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs

et usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory


Does this mean anything of importance?

---

### Post by techvish81 on 2012-12-04
try sudo instead of gksu.

---

### Post by sayofethos on 2012-12-04
> **techvish81 said:**
> try sudo instead of gksu.

Done. Terminal prompts with the following:

[I]Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.[/I]

The USB drive seems to be working fine now, I'm just curious whether these messages give a hint to something that might need additional tweaking down the line.

---

### Post by techvish81 on 2012-12-04
> **sayofethos said:**
> Done. Terminal prompts with the following:

[I]Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.[/I]

The USB drive seems to be working fine now, I'm just curious whether these messages give a hint to something that might need additional tweaking down the line.

if you are 'logged in' as user other than the administrator , these things can happen.

---

### Post by sayofethos on 2012-12-04
Ok, gotcha. Thanks a lot, it's nice to have the external drives working again.

---

### Post by audiomick on 2012-12-04
> **techvish81 said:**
> try sudo instead of gksu.

No, don't do that. Nautilus is a graphical application, and so should be started with gksu, or gksudo. In fact, it will probably work with sudo, but there are good reasons not to start graphical application with sudo.

[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

Getting errors like this
```
mick@ubuntu-desktop:~$ gksu nautilus
Initializing nautilus-gdu extension

(nautilus:2915): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '2915'

(nautilus:2915): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
^Z
[1]+  Angehalten              gksu nautilus

```

seems to be normal with nautilus. I've seen mention of it numerous times on the forum, and I always get something similar. Nonetheless, the instance of Nautilus always works correctly. I believe it is safe to simply ignore the errors.

---

### Post by CaptainMark on 2012-12-05
+1 to audiomick, don't use sudo for graphical applications, alway gksu. 

Also vfat filesystems don't support permissions so logging in as root/sudo or a normal user to access a vfat usb won't make a difference, the problem is for some reason the usb must have been mounted specifically as read-only, there is a number of reason as why this could happen but if its not happening now I wouldn't worry about it, I have a sd card reader that sometimes/rarely mounts as read only, I just unplug it and try again and it usually works

---

