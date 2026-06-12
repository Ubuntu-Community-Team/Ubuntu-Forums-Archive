---
title: "Error when mount any usb device"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by LightRaven on 2008-09-02
Hello all. 

I am sadly encountering the following error when I try to mount any usb device (usb memory block, digital camera etc.):

"Cannot mount device"
"Error: org.freedesktop.DBus.Error.AccessDenied."

Details include:
A Security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface org.freedesktop.Hal.Device.Volume member "Mount" error name (unset) destination org.freedesktop.Hal

This is a new error. I never had this problem before. How to solve it?

Edit: It seems that I cant even edit the User and Groups tab (wont show).

---

### Post by wolfen69 on 2008-09-02
i found [this]("http://www.networknet.nl/apps/wp/archives/457"). hope it helps.

---

### Post by LightRaven on 2008-09-02
> **wolfen69 said:**
> i found [this]("http://www.networknet.nl/apps/wp/archives/457"). hope it helps.

I tried following it but i got this error:

sudo mount -t vfat /dev/sdb /mnt/sdb -o force
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error

---

### Post by LightRaven on 2008-09-03
Still a problem up

---

### Post by alphaniner on 2008-09-03
> sudo mount -t vfat /dev/**sdb** /mnt/sdb -o force

You need a number to denote the partition.  For example, when I plug in a thumb drive and run 'sudo fdisk -l' I get

> Disk /dev/sdb: 1017 MB, 1017118720 bytes
32 heads, 32 sectors/track, 1940 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Disk identifier: 0xfd8aba28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb4   *           1         128       65520    6  FAT16


so in my case the command would be

> sudo mount -t vfat /dev/**sdb4** /mnt/sdb -o force

and keep in mind whatever folder you are mounting it to (in this case /mnt/sdb) has to exist before you can mount anything there.  Also I would recommend using /media/*** rather than /mnt/***.

---

### Post by LightRaven on 2008-09-04
That didn't work either. 

I would also like to fix this problem, because it never occured before. Or at least know if it's a bug or something

---

### Post by bobnutfield on 2008-09-04
Open a terminal and type:

> gedit /etc/group

Look down the list for "plugdev" and see if your user name is shown (for example:
plugdev:x:46:<your username>)

If it is not, add it by again opening gedit /etc/group as sudo.  Reboot and try again to plug in a usb dev.

---

### Post by LightRaven on 2008-09-05
plugdev:x:46:myusername

is indeed there. However I can't access users and groups tab from the system -> administration

---

### Post by Crafty Kisses on 2008-09-05
Just for the heck of it, are you on the LiveCD? I've known people with issues like this on the LiveCD.

---

### Post by LightRaven on 2008-09-05
No. I'm no. I have used Ubuntu some time now, and it happend recently this problem. I do not know what caused it

---

### Post by philinux on 2008-09-05
Post the output of

```
cat /etc/group
```

---

### Post by LightRaven on 2008-09-05
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:raven
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:raven
fax:x:21:
voice:x:22:
cdrom:x:24:raven
floppy:x:25:raven
tape:x:26:
sudo:x:27:
audio:x:29:pulse,raven
dip:x:30:raven
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:raven
sasl:x:45:
plugdev:x:46:raven
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
dhcp:x:102:
syslog:x:103:
klog:x:104:
scanner:x:105:hplip
nvram:x:106:
fuse:x:107:raven
ssl-cert:x:108:
lpadmin:x:109:raven
crontab:x:110:
mlocate:x:111:
ssh:x:112:
avahi-autoipd:x:113:
gdm:x:114:
admin:x:115:raven
pulse:x:116:
pulse-access:x:117:
pulse-rt:x:118:
messagebus:x:119:
avahi:x:120:
netdev:x:121:
polkituser:x:122:
haldaemon:x:123:
raven:x:1000:

---

### Post by LightRaven on 2008-09-07
Any news?

---

### Post by LightRaven on 2008-09-10
I guess Im gonna need to re format

---

### Post by angelofhope on 2008-09-25
Just an FYI, I had the same problem, but I knew I did something wrong by using usermod -G instead of usermod -aG.
Adding my user to the group plugdev did it for me.
```
usermod -aG plugdev username
```

Just for future reference ;)

---

