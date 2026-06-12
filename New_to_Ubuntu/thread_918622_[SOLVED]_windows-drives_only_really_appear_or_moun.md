---
title: "[SOLVED] windows-drives only really appear or mount when I browsed them once"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by hachel on 2008-09-13
hi there,
the thing is, my 3 windows partitions (ntsf on a scsi-drive) do appear under "places", but won't appear on my desktop until I clicked to browse them once under "places".
The problem with that is that I share a firefox-profile on one of those windows-partitions and thus ubuntu8-firefox won't start ("firefox is already running, please close running firefox etc", though firefox is not listed under running processes (ps -e)) until I clicked that particular partition once to make it appear on the desktop .

thanks

hachel

---

### Post by Pro-reason on 2008-09-13
You need to edit your [/etc/fstab]("https://help.ubuntu.com/community/MountDevicesTroubleshooting") file so that those partitions are marked to be mounted at start-up.

---

### Post by RomeReactor on 2008-09-13
You can change that behavior--in order to automount the partition ant boot--by finding your partition:
```
sudo fdisk -l
```
Then, create a mount point in /media:
```
sudo mkdir /media/disk
```
edit fstab:
```
gksudo gedit /etc/fstab
```
and add your partition there. For example, let's say I have an EXT3 partition (/dev/hda2) I want to mount at boot; I then edit /etc/fstab to add it at the end of the file like this:
```
/dev/hda2       /media/disk   ext3    defaults     0        0
```

I'm not absolutely sure this is the same procedure for ntfs partitions, but give it a try (change **etx3** to **ntfs** when adding the partition to fstab), then reboot to see if it automounts at boot.

---

### Post by Harisz750 on 2008-09-13
they are NTFS partitions ... not ext3

---

### Post by RomeReactor on 2008-09-13
The exact instructions [are here]("http://ubuntuforums.org/showthread.php?t=721776"), particularly the fifth post. Seems **ntfs-config** can do that.

---

### Post by hachel on 2008-09-13
thanks everyone, i used that link from RomeReactor and manualy configured my fstab (ntfs-config wouldn't let my mark any ntfs-drives), works fine now,
cheers

---

