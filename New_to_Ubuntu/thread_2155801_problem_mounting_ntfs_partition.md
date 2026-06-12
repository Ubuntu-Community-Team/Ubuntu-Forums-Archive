---
title: "problem mounting ntfs partition"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by innn on 2013-06-19
While installing I mounted some ntfs partition in** /media/windows** and get these  errors in mounting it that I've becomed well acquainted with in these two  days.

It's about pressing  the S key to skip mounting.
Funny enough in PCManFM mount point** /media/windows** opens easily.
Here it is my** /etc/fstab**:

```
# / was on /dev/sdc1 during installation
UUID=bd94a982-85ac-454f-b974-34a0d9de9b9d /                  ext4    errors=remount-ro 0       1
# /home was on /dev/sdc3 during installation
UUID=2f17c229-d5d7-4d23-bf1f-31d3561bbd87 /home          ext4    defaults        0       2
# /windows was on /dev/sdc4 during installation
UUID=4C80717C80716CF8 /media/windows                                      ntfs     ro,umask=007,gid=46 0       0
# swap was on /dev/sdc2 during installation
UUID=866219ca-cf3d-4cfd-a757-f9b3afe927dc none             swap    sw              0       0

```
Ubuntu only at splash screen gives me the errors that I must skip.

---

### Post by oldfred on 2013-06-19
If you are having issue mounting it, run chkdsk from a Windows repairCD or your Windows install.

Suggested fstab entry uses these parameters:
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by innn on 2013-06-21
I have now 

```
4C80717C80716CF8 /media/windows  ntfs-3g  defaults,nls=utf8,umask=000,uid=1000,windows_names  0 0
```

and still get the error message 

Now I have it like this :

```
4C80717C80716CF8 /media/windows  ntfs ro,nls=utf8,windows_names  0 0
```

and still refuses to mount I get this when trying manually from PcManFM:

```
Error mounting /dev/sda4 at /media/myusername/4C80717C80716CF8: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda4" "/media/ubucos/4C80717C80716CF8"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume read-only with the 'ro' mount option.
```

And that's what I want to mount it read-only. And why it wants to mount it in **/media/username/UUID** mount point when I have **/media/windows** in /etc/fstab stated

PS: The Message I get when trying to mount by clicking /media/windows directory in PCManFM is :

```
mount: only &#8222;root&#8220; can mount 4C80717C80716CF8 in /media/windows

```

PS2: I was able to mount it from cli:

```
sudo ntfs-3g -o ro /dev/sda4 /media/windows
```

I chown /media/windows as my user and got to this version of fstab entry:

```
4C80717C80716CF8 /media/windows  ntfs-3g noauto,uid=1000,gid=users,ro,nls=utf8,windows_names  0 0
```

Reboot and no more error messages but I still have no right to manually mount the partition in file manager
What am I doing wrong?

---

### Post by oldfred on 2013-06-21
Windows has flags for hibernation and chkdsk needed. If the Linux NTFS driver sees either of those flags it will not mount the NTFS partition. I do not think it matters if you want to mount as read only or not. 

Generally better to use a shared NTFS data partition, but now with Windows 8 hibernation that has not always worked.

---

### Post by innn on 2013-06-27
ok, I've succeded in manually mounting it as read-only  now I will copy everything from there and using gparted delete the partion.

---

