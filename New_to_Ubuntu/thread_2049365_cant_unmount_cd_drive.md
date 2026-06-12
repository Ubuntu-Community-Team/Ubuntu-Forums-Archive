---
title: "cant unmount cd drive"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by m3t3ors on 2012-08-28
when i put a dvd or cd in my cd drive i used to get a box asking what to do. ive noe set it to do nothing and not show that box again..
now when i want to burn a disc it says no burner ready, disc may be in use, please unmount drive.
i cant see any way to unmount the drive

please help

---

### Post by rukiaEnix on 2012-08-28
Have you checked in /media if there is a folder named cdrom or dvdrom or something similar? Or better post the result of this:

```

ls /media

```

Have you tried unmounting the CD manually?

---

### Post by Hadaka on 2012-08-28
Hi, its doing exactly what you told it to do...nothing

click System Settings....then Removable Media...then select how you want
a DVD or CD to be opened, which application, or..ask what to do.

and to "unmount" or eject...right click the cd icon in the launcher panel and 
choose...eject.

from terminal command line....

eject       #....to open
eject -t   #...to close
eject -T   #...to close..if open..   to open..if closed

man eject for more command and info.

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Have you checked in /media if there is a folder named cdrom or dvdrom or something similar? Or better post the result of this:

```

ls /media

```

Have you tried unmounting the CD manually?

john@john-ML3108b:-$ ls /media
Elements
john@john-ML3108b:-$


elements is my externel hdd

---

### Post by rukiaEnix on 2012-08-28
Did you typed the command with the CD inside?

If not please insert the CD and type again the command and post the result.

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Did you typed the command with the CD inside?

If not please insert the CD and type again the command and post the result.

john@john-ML3108b:$ ls /media
Elements
john@john:-$ ML3108b
after reboot and with blank dvd inserted

---

### Post by rukiaEnix on 2012-08-28
Please post the result of:

```

ls /dev

```

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Please post the result of:

```

ls /dev

```

john@john-ML3108b:~$ ls /dev
autofs           mem                 sda1      tty26  tty58      ttyS30
block            net                 sda2      tty27  tty59      ttyS31
bsg              network_latency     sda5      tty28  tty6       ttyS4
btrfs-control    network_throughput  sdb       tty29  tty60      ttyS5
bus              null                sdb1      tty3   tty61      ttyS6
cdrom            nvidia0             sg0       tty30  tty62      ttyS7
cdrw             nvidiactl           sg1       tty31  tty63      ttyS8
char             oldmem              sg2       tty32  tty7       ttyS9
console          port                shm       tty33  tty8       uinput
core             ppp                 snapshot  tty34  tty9       urandom
cpu              psaux               snd       tty35  ttyprintk  usbmon0
cpu_dma_latency  ptmx                sr0       tty36  ttyS0      usbmon1
disk             pts                 stderr    tty37  ttyS1      usbmon2
dvd              ram0                stdin     tty38  ttyS10     vcs
dvdrw            ram1                stdout    tty39  ttyS11     vcs1
ecryptfs         ram10               tty       tty4   ttyS12     vcs2
fb0              ram11               tty0      tty40  ttyS13     vcs3
fd               ram12               tty1      tty41  ttyS14     vcs4
full             ram13               tty10     tty42  ttyS15     vcs5
fuse             ram14               tty11     tty43  ttyS16     vcs6
hidraw0          ram15               tty12     tty44  ttyS17     vcsa
hpet             ram2                tty13     tty45  ttyS18     vcsa1
input            ram3                tty14     tty46  ttyS19     vcsa2
kmsg             ram4                tty15     tty47  ttyS2      vcsa3
log              ram5                tty16     tty48  ttyS20     vcsa4
loop0            ram6                tty17     tty49  ttyS21     vcsa5
loop1            ram7                tty18     tty5   ttyS22     vcsa6
loop2            ram8                tty19     tty50  ttyS23     vga_arbiter
loop3            ram9                tty2      tty51  ttyS24     watchdog
loop4            random              tty20     tty52  ttyS25     zero
loop5            rfkill              tty21     tty53  ttyS26
loop6            rtc                 tty22     tty54  ttyS27
loop7            rtc0                tty23     tty55  ttyS28
mapper           scd0                tty24     tty56  ttyS29
mcelog           sda                 tty25     tty57  ttyS3
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
OK, you have cdrom and dvd.

Mount the device, if it is CD use cdrom if it is DVD then use dvd..
In the example will use cdrom

```

mount /dev/cdrom

```

Please post any message the command may show you.

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> OK, you have cdrom and dvd.

Mount the device, if it is CD use cdrom if it is DVD then use dvd..
In the example will use cdrom

```

mount /dev/cdrom

```

Please post any message the command may show you.

john@john-ML3108b:~$ mount /dev/dvdrom
mount: can't find /dev/dvdrom in /etc/fstab or /etc/mtab
john@john-ML3108b:~$ mount /dev/dvd
mount: can't find /dev/dvd in /etc/fstab or /etc/mtab
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
Please post the your fstab file:

```

cat /etc/fstab

```

---

### Post by m3t3ors on 2012-08-28
dont know if this of any help but id just burnt 5 dvds then put a blank dvd in to burn next when xfburn froze, i had to reboot, and thats when the problem started

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Please post the your fstab file:

```

cat /etc/fstab

```

john@john-ML3108b:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fd642427-0fc0-43ac-834b-92c9999be3f5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ac6c238e-fdc6-4c4a-bc57-cc61d461fd20 none            swap    sw              0       0
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
Do this again as root or with sudo, but use dvd not dvdrom:

```

mount /dev/dvd

```

It says that such device doesn't exist because it's true, at /dev you have dvd not dvdrom

---

### Post by m3t3ors on 2012-08-28
this is strange?
when i try su
it says authentication failure when i enter password

---

### Post by rukiaEnix on 2012-08-28
Use sudo not su, su is for logging as a superuser, and its use is like this:

```

su *user*

```

So if you are putting something like this: su mount /dev/dvd it might be taking the mount command as a user you are trying to use to log in.

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Do this again as root or with sudo, but use dvd not dvdrom:

```

mount /dev/dvd

```

It says that such device doesn't exist because it's true, at /dev you have dvd not dvdrom

ohn@john-ML3108b:~$ sudo mount /dev/dvd
[sudo] password for john: 
mount: can't find /dev/dvd in /etc/fstab or /etc/mtab
john@john-ML3108b:~$

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Use sudo not su, su is for logging as a superuser, and its use is like this:

```

su *user*

```

So if you are putting something like this: su mount /dev/dvd it might be taking the mount command as a user you are trying to use to log in.

sorry was my mistake

---

### Post by rukiaEnix on 2012-08-28
First of all, your CD is still inside? All of this commands must be use if the CD is inside. If it was already inside proceed with this:

Create a directory at /media:

```

mkdir /media/new_folder

```Then try mounting like this:

```

mount -t iso9660 /dev/dvd /media/new_folder

```Also, when you introduce your CD does it opens a window at the graphic mode?

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> First of all, your CD is still inside? All of this commands must be use if the CD is inside. If it was already inside proceed with this:

Create a directory at /media:

```

mkdir /media/new_folder

```Then try mounting like this:

```

mount -t iso9660 /dev/dvd /media/new_folder

```Also, when you introduce your CD does it opens a window at the graphic mode?

john@john-ML3108b:~$ mkdir /media/new_folder
mkdir: cannot create directory `/media/new_folder': Permission denied
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
Create it as root or with sudo the directory.

Its the CD still inside?

---

### Post by m3t3ors on 2012-08-28
all commands with blank dvd in drive

no it doesnt open new window

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Create it as root or with sudo the directory.

Its the CD still inside?

john@john-ML3108b:~$ sudo mount -t iso9660 /dev/dvd /media/new_folder
mount: /dev/sr0 already mounted or /media/new_folder busy
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
Please post the result of:

```

mount

```

You don't need sudo or to be root for this.

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Please post the result of:

```

mount

```

You don't need sudo or to be root for this.

john@john-ML3108b:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
/dev/sdb1 on /media/Elements type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
Indeed it doesn't show the device dvd mounted, it's strange it says it's busy.

Try this, if it says something about permissions use sudo:

```

umount /dev/dvd

```

Please post any message it may show.

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Indeed it doesn't show the device dvd mounted, it's strange it says it's busy.

Try this, if it says something about permissions use sudo:

```

umount /dev/dvd

```

Please post any message it may show.

ohn@john-ML3108b:~$ umount /dev/dvd
umount: /dev/sr0 is not mounted (according to mtab)
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
Please become root:

```

sudo su root

```

And post the result of this:

```

ls /media

```

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Please become root:

```

sudo su root

```

And post the result of this:

```

ls /media

```

john@john-ML3108b:~$ sudo su root
[sudo] password for john: 
root@john-ML3108b:/home/john# ls /media
Elements  new_folder
root@john-ML3108b:/home/john#

---

### Post by rukiaEnix on 2012-08-28
Check if there is something inside new_folder with ls.

If there is something inside try umounting the folder:

```

umount /media/new_folder

```

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Check if there is something inside new_folder with ls.

If there is something inside try umounting the folder:

```

umount /media/new_folder

```

please send command for ls new folder
im new to command lines

---

### Post by rukiaEnix on 2012-08-28
```

ls /media/new_folder

```

With ls you list the files inside a folder, I put /media/new_folder because that is the path of the folder in this case new_folder where you want to list the files.
But if you were already inside /media you could just type ls new_folder. And if you where inside /media/new_folder just type ls.

To know in what directory you are at the moment type:

```

pwd

```

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> ```

ls /media/new_folder

```

With ls you list the files inside a folder, I put /media/new_folder because that is the path of the folder in this case new_folder where you want to list the files.
But if you were already inside /media you could just type ls new_folder. And if you where inside /media/new_folder just type ls.

To know in what directory you are at the moment type:

```

pwd

```

root@john-ML3108b:/home/john# ls /media/new_folder
root@john-ML3108b:/home/john#

---

### Post by rukiaEnix on 2012-08-28
Add this line to the end of /etc/fstab:

```

/dev/dvd   /media/new_folder   udf,iso9660   user,noauto,exec,utf8   0   0

```

And try again this:

```

mount /dev/dvd

```

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Add this line to the end of /etc/fstab:

```

/dev/dvd   /media/new_folder   udf,iso9660   user,noauto,exec,utf8   0   0

```

And try again this:

```

mount /dev/dvd

```
how do i get to /etc/fstab  or do
i just type the line in terminal?

---

### Post by rukiaEnix on 2012-08-28
Open it with a text editor, I recommend nano, you do it like this (as root or with sudo):

```

nano /etc/fstab

```

Write the line at the end and then press Ctrl+o to save and then Ctrl+x to close it.

---

### Post by m3t3ors on 2012-08-28
how do i save the modified file

---

### Post by rukiaEnix on 2012-08-28
..... I've typed before that it is with Ctrl+o

---

### Post by m3t3ors on 2012-08-28
thanks
john@john-ML3108b:~$ sudo nano /etc/fstab
[sudo] password for john: 
john@john-ML3108b:~$ mount /dev/dvd
mount: /dev/sr0 already mounted or /media/new_folder busy
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
Have you try introducing other CD? Not the blank one, try putting inside a CD with data inside or a music CD and see if it works in graphic mode without using any command.

Before you do all that remove the line I told you to add to /etc/fstab.

---

### Post by m3t3ors on 2012-08-28
nothing happens?
tried music cd, data dvd and movie dvd

---

### Post by rukiaEnix on 2012-08-28
Please post the result of this:

```

cat /etc/mtab

```

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Please post the result of this:

```

cat /etc/mtab

```

john@john-ML3108b:~$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/john/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=john 0 0
/dev/sdb1 /media/Elements fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
OK

Please post the result of this (if it doesn't work with messages try syslog):

```

cat /var/log/messages

```

Just post the lines for today date and the date when you have to reboot your computer when trying to burn the CD.

And also post the result of:

```

cat dmesg

```

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> OK

Please post the result of this (if it doesn't work with messages try syslog):

```

cat /var/log/messages

```

Just post the lines for today date and the date when you have to reboot your computer when trying to burn the CD.

And also post the result of:

```

cat dmesg

```

Aug 28 18:15:43 john-ML3108b NetworkManager[866]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:10.0/0000:06:09.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 28 18:15:43 john-ML3108b NetworkManager[866]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Aug 28 18:15:43 john-ML3108b NetworkManager[866]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 28 18:15:43 john-ML3108b NetworkManager[866]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 28 18:15:43 john-ML3108b NetworkManager[866]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 28 18:15:43 john-ML3108b NetworkManager[866]:    SCPlugin-Ifupdown: end _init.
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 28 18:15:43 john-ML3108b NetworkManager[866]:    Ifupdown: get unmanaged devices count: 0
Aug 28 18:15:43 john-ML3108b NetworkManager[866]:    SCPlugin-Ifupdown: (152515896) ... get_connections.
Aug 28 18:15:43 john-ML3108b NetworkManager[866]:    SCPlugin-Ifupdown: (152515896) ... get_connections (managed=false): return empty list.
Aug 28 18:15:43 john-ML3108b NetworkManager[866]:    keyfile: parsing tonijoan ... 
Aug 28 18:15:43 john-ML3108b NetworkManager[866]:    keyfile:     read connection 'tonijoan'
Aug 28 18:15:43 john-ML3108b NetworkManager[866]:    Ifupdown: get unmanaged devices count: 0
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> modem-manager is now available
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:10.0/0000:06:09.0/ieee80211/phy0/rfkill0) (driver (unknown))
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> Networking is enabled by state file
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8180' ifindex: 3)
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> (wlan0): now managed
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 28 18:15:43 john-ML3108b NetworkManager[866]: <info> (wlan0): bringing up device.
Aug 28 18:15:43 john-ML3108b kernel: [   25.276365] type=1400 audit(1346174143.290:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=884 comm="apparmor_parser"
Aug 28 18:15:43 john-ML3108b kernel: [   25.321942] vesafb: mode is 1024x768x32, linelength=4096, pages=0
Aug 28 18:15:43 john-ML3108b kernel: [   25.321948] vesafb: scrolling: redraw
Aug 28 18:15:43 john-ML3108b kernel: [   25.321953] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Aug 28 18:15:43 john-ML3108b kernel: [   25.322381] vesafb: framebuffer at 0xc0000000, mapped to 0xdde80000, using 3072k, total 3072k
Aug 28 18:15:43 john-ML3108b kernel: [   25.322638] Console: switching to colour frame buffer device 128x48
Aug 28 18:15:43 john-ML3108b kernel: [   25.322672] fb0: VESA VGA frame buffer device
Aug 28 18:15:43 john-ML3108b kernel: [   25.512755] ppdev: user-space parallel port driver
Aug 28 18:15:44 john-ML3108b kernel: [   26.497249] init: failsafe main process (799) killed by TERM signal
Aug 28 18:15:44 john-ML3108b anacron[967]: Anacron 2.3 started on 2012-08-28
Aug 28 18:15:44 john-ML3108b acpid: starting up with proc fs
Aug 28 18:15:44 john-ML3108b cron[957]: (CRON) INFO (pidfile fd = 3)
Aug 28 18:15:44 john-ML3108b cron[972]: (CRON) STARTUP (fork ok)
Aug 28 18:15:44 john-ML3108b kernel: [   26.532447] init: apport pre-start process (952) terminated with status 1
Aug 28 18:15:44 john-ML3108b kernel: [   26.540468] init: apport post-stop process (974) terminated with status 1
Aug 28 18:15:44 john-ML3108b udev-configure-printer: add /module/lp
Aug 28 18:15:44 john-ML3108b udev-configure-printer: Failed to get parent
Aug 28 18:15:44 john-ML3108b cron[972]: (CRON) INFO (Running @reboot jobs)
Aug 28 18:15:44 john-ML3108b acpid: 32 rules loaded
Aug 28 18:15:44 john-ML3108b acpid: waiting for events: event logging is off
Aug 28 18:15:44 john-ML3108b anacron[967]: Normal exit (0 jobs run)
Aug 28 18:15:45 john-ML3108b acpid: client connected from 991[0:0]
Aug 28 18:15:45 john-ML3108b acpid: 1 client rule loaded
Aug 28 18:15:45 john-ML3108b bluetoothd[1017]: Bluetooth daemon 4.96
Aug 28 18:15:45 john-ML3108b bluetoothd[1017]: Starting SDP server
Aug 28 18:15:45 john-ML3108b bluetoothd[1017]: opening L2CAP socket: Address family not supported by protocol
Aug 28 18:15:45 john-ML3108b bluetoothd[1017]: Server initialization failed
Aug 28 18:15:45 john-ML3108b kernel: [   27.283279] Bluetooth: Core ver 2.16
Aug 28 18:15:45 john-ML3108b kernel: [   27.283338] NET: Registered protocol family 31
Aug 28 18:15:45 john-ML3108b kernel: [   27.283341] Bluetooth: HCI device and connection manager initialized
Aug 28 18:15:45 john-ML3108b kernel: [   27.283345] Bluetooth: HCI socket layer initialized
Aug 28 18:15:45 john-ML3108b kernel: [   27.283347] Bluetooth: L2CAP socket layer initialized
Aug 28 18:15:45 john-ML3108b kernel: [   27.285266] Bluetooth: SCO socket layer initialized
Aug 28 18:15:45 john-ML3108b kernel: [   27.292681] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 28 18:15:45 john-ML3108b kernel: [   27.292687] Bluetooth: BNEP filters: protocol multicast
Aug 28 18:15:45 john-ML3108b kernel: [   27.315366] Bluetooth: RFCOMM TTY layer initialized
Aug 28 18:15:45 john-ML3108b kernel: [   27.315375] Bluetooth: RFCOMM socket layer initialized
Aug 28 18:15:45 john-ML3108b kernel: [   27.315378] Bluetooth: RFCOMM ver 1.11
Aug 28 18:15:45 john-ML3108b anacron[1102]: Anacron 2.3 started on 2012-08-28
Aug 28 18:15:45 john-ML3108b anacron[1102]: Normal exit (0 jobs run)
Aug 28 18:15:46 john-ML3108b kernel: [   28.342258] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Aug 28 18:15:46 john-ML3108b acpid: client connected from 991[0:0]
Aug 28 18:15:46 john-ML3108b acpid: 1 client rule loaded
Aug 28 18:15:49 john-ML3108b dbus[830]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Aug 28 18:15:49 john-ML3108b dbus[830]: [system] Successfully activated service 'org.freedesktop.Accounts'
Aug 28 18:15:49 john-ML3108b accounts-daemon[1126]: started daemon version 0.6.14
Aug 28 18:15:49 john-ML3108b dbus[830]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Aug 28 18:15:49 john-ML3108b dbus[830]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (wlan0): preparing device.
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (wlan0): deactivating device (reason 'managed') [2]
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (eth0): carrier is OFF
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (eth0): now managed
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (eth0): bringing up device.
Aug 28 18:15:49 john-ML3108b kernel: [   31.752125] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 28 18:15:49 john-ML3108b kernel: [   31.755835] forcedeth 0000:00:14.0: eth0: no link during initialization
Aug 28 18:15:49 john-ML3108b dbus[830]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Aug 28 18:15:49 john-ML3108b kernel: [   31.762986] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (eth0): preparing device.
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:14.0/net/eth0
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <warn> bluez error getting default adapter: No such adapter
Aug 28 18:15:49 john-ML3108b dbus[830]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Aug 28 18:15:49 john-ML3108b dbus[830]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> wpa_supplicant started
Aug 28 18:15:49 john-ML3108b dbus[830]: [system] Successfully activated service 'org.freedesktop.UPower'
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (wlan0): supplicant interface state: starting -> ready
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Aug 28 18:15:49 john-ML3108b kernel: [   31.941684] init: plymouth-stop pre-start process (1263) terminated with status 1
Aug 28 18:15:49 john-ML3108b NetworkManager[866]: <info> (wlan0): supplicant interface state: ready -> inactive
Aug 28 18:15:50 john-ML3108b anacron[1322]: Anacron 2.3 started on 2012-08-28
Aug 28 18:15:50 john-ML3108b anacron[1322]: Normal exit (0 jobs run)
Aug 28 18:15:50 john-ML3108b dbus[830]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Aug 28 18:15:50 john-ML3108b dbus[830]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Aug 28 18:15:51 john-ML3108b kernel: [   33.078948] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Aug 28 18:15:51 john-ML3108b dbus[830]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Aug 28 18:15:51 john-ML3108b dbus[830]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Aug 28 17:15:51 john-ML3108b rtkit-daemon[1382]: Successfully called chroot.
Aug 28 17:15:51 john-ML3108b rtkit-daemon[1382]: Successfully dropped privileges.
Aug 28 17:15:51 john-ML3108b rtkit-daemon[1382]: Successfully limited resources.
Aug 28 17:15:51 john-ML3108b rtkit-daemon[1382]: Running.
Aug 28 17:15:51 john-ML3108b rtkit-daemon[1382]: Watchdog thread running.
Aug 28 17:15:51 john-ML3108b rtkit-daemon[1382]: Canary thread running.
Aug 28 17:15:51 john-ML3108b rtkit-daemon[1382]: Successfully made thread 1380 of process 1380 (n/a) owned by '104' high priority at nice level -11.
Aug 28 17:15:51 john-ML3108b rtkit-daemon[1382]: Supervising 1 threads of 1 processes of 1 users.
Aug 28 17:15:51 john-ML3108b rtkit-daemon[1382]: Successfully made thread 1387 of process 1380 (n/a) owned by '104' RT at priority 5.
Aug 28 17:15:51 john-ML3108b rtkit-daemon[1382]: Supervising 2 threads of 1 processes of 1 users.
Aug 28 17:15:51 john-ML3108b rtkit-daemon[1382]: Successfully made thread 1388 of process 1380 (n/a) owned by '104' RT at priority 5.
Aug 28 17:15:51 john-ML3108b rtkit-daemon[1382]: Supervising 3 threads of 1 processes of 1 users.
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Auto-activating connection 'tonijoan'.
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) starting connection 'tonijoan'
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Activation (wlan0/wireless): connection 'tonijoan' has security, and secrets exist.  No new secrets needed.
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Config: added 'ssid' value 'tonijoan'
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Config: added 'scan_ssid' value '1'
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Config: added 'auth_alg' value 'OPEN'
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Config: added 'psk' value '<omitted>'
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> Config: set interface ap_scan to 1
Aug 28 18:15:52 john-ML3108b NetworkManager[866]: <info> (wlan0): supplicant interface state: inactive -> scanning
Aug 28 18:15:53 john-ML3108b wpa_supplicant[1235]: Trying to authenticate with 00:26:5a:27:d9:94 (SSID='tonijoan' freq=2432 MHz)
Aug 28 18:15:53 john-ML3108b NetworkManager[866]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 28 18:15:54 john-ML3108b wpa_supplicant[1235]: Trying to associate with 00:26:5a:27:d9:94 (SSID='tonijoan' freq=2432 MHz)
Aug 28 18:15:54 john-ML3108b kernel: [   36.020066] wlan0: authenticate with 00:26:5a:27:d9:94 (try 1)
Aug 28 18:15:54 john-ML3108b kernel: [   36.021728] wlan0: authenticated
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> (wlan0): supplicant interface state: authenticating -> associating
Aug 28 18:15:54 john-ML3108b kernel: [   36.116068] wlan0: associate with 00:26:5a:27:d9:94 (try 1)
Aug 28 18:15:54 john-ML3108b kernel: [   36.119775] wlan0: RX AssocResp from 00:26:5a:27:d9:94 (capab=0xc31 status=0 aid=1)
Aug 28 18:15:54 john-ML3108b kernel: [   36.119779] wlan0: associated
Aug 28 18:15:54 john-ML3108b kernel: [   36.120438] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 28 18:15:54 john-ML3108b kernel: [   36.120511] cfg80211: Calling CRDA for country: GB
Aug 28 18:15:54 john-ML3108b wpa_supplicant[1235]: Associated with 00:26:5a:27:d9:94
Aug 28 18:15:54 john-ML3108b kernel: [   36.125769] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125776] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125779] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125783] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125786] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125790] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125793] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125796] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125799] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125803] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125806] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125809] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125812] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125816] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125819] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125822] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125825] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125829] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125831] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125835] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125838] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125841] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125844] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125848] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125851] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Aug 28 18:15:54 john-ML3108b kernel: [   36.125854] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125857] cfg80211: Disabling freq 2484 MHz
Aug 28 18:15:54 john-ML3108b kernel: [   36.125861] cfg80211: Regulatory domain changed to country: GB
Aug 28 18:15:54 john-ML3108b kernel: [   36.125863] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125866] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125870] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125873] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 28 18:15:54 john-ML3108b kernel: [   36.125876] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Aug 28 18:15:54 john-ML3108b wpa_supplicant[1235]: WPA: Key negotiation completed with 00:26:5a:27:d9:94 [PTK=CCMP GTK=TKIP]
Aug 28 18:15:54 john-ML3108b wpa_supplicant[1235]: CTRL-EVENT-CONNECTED - Connection to 00:26:5a:27:d9:94 completed (auth) [id=0 id_str=]
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'tonijoan'.
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> dhclient started with pid 1393
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Beginning IP6 addrconf.
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 28 18:15:54 john-ML3108b dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Aug 28 18:15:54 john-ML3108b dhclient: Copyright 2004-2010 Internet Systems Consortium.
Aug 28 18:15:54 john-ML3108b dhclient: All rights reserved.
Aug 28 18:15:54 john-ML3108b dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Aug 28 18:15:54 john-ML3108b dhclient: 
Aug 28 18:15:54 john-ML3108b dhclient: Listening on LPF/wlan0/00:c0:a8:ec:cd:e6
Aug 28 18:15:54 john-ML3108b dhclient: Sending on   LPF/wlan0/00:c0:a8:ec:cd:e6
Aug 28 18:15:54 john-ML3108b dhclient: Sending on   Socket/fallback
Aug 28 18:15:54 john-ML3108b dhclient: DHCPREQUEST of 192.168.0.102 on wlan0 to 255.255.255.255 port 67
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Aug 28 18:15:54 john-ML3108b dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
Aug 28 18:15:54 john-ML3108b dhclient: bound to 192.168.0.102 -- renewal in 234866 seconds.
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info>   address 192.168.0.102
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info>   prefix 24 (255.255.255.0)
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info>   gateway 192.168.0.1
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info>   nameserver '192.168.0.1'
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info>   domain name 'cable.virginmedia.net'
Aug 28 18:15:54 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug 28 18:15:54 john-ML3108b avahi-daemon[842]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Aug 28 18:15:54 john-ML3108b avahi-daemon[842]: New relevant interface wlan0.IPv4 for mDNS.
Aug 28 18:15:54 john-ML3108b avahi-daemon[842]: Registering new address record for 192.168.0.102 on wlan0.IPv4.
Aug 28 18:15:55 john-ML3108b avahi-daemon[842]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::2c0:a8ff:feec:cde6.
Aug 28 18:15:55 john-ML3108b avahi-daemon[842]: New relevant interface wlan0.IPv6 for mDNS.
Aug 28 18:15:55 john-ML3108b avahi-daemon[842]: Registering new address record for fe80::2c0:a8ff:feec:cde6 on wlan0.*.
Aug 28 18:15:55 john-ML3108b NetworkManager[866]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Aug 28 18:15:55 john-ML3108b NetworkManager[866]: <info> Policy set 'tonijoan' (wlan0) as default for IPv4 routing and DNS.
Aug 28 18:15:55 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) successful, device activated.
Aug 28 18:15:55 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 28 18:15:55 john-ML3108b dbus[830]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug 28 18:15:55 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 28 18:15:55 john-ML3108b dbus[830]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 28 17:15:59 john-ML3108b rtkit-daemon[1382]: Successfully made thread 1623 of process 1623 (n/a) owned by '1000' high priority at nice level -11.
Aug 28 17:15:59 john-ML3108b rtkit-daemon[1382]: Supervising 4 threads of 2 processes of 2 users.
Aug 28 17:15:59 john-ML3108b rtkit-daemon[1382]: Successfully made thread 1633 of process 1623 (n/a) owned by '1000' RT at priority 5.
Aug 28 17:15:59 john-ML3108b rtkit-daemon[1382]: Supervising 5 threads of 2 processes of 2 users.
Aug 28 17:16:00 john-ML3108b rtkit-daemon[1382]: Successfully made thread 1634 of process 1623 (n/a) owned by '1000' RT at priority 5.
Aug 28 17:16:00 john-ML3108b rtkit-daemon[1382]: Supervising 6 threads of 2 processes of 2 users.
Aug 28 18:16:00 john-ML3108b dbus[830]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Aug 28 18:16:00 john-ML3108b dbus[830]: [system] Successfully activated service 'org.freedesktop.UDisks'
Aug 28 18:16:03 john-ML3108b ntfs-3g[1678]: Version 2011.4.12AR.4 external FUSE 28
Aug 28 18:16:03 john-ML3108b ntfs-3g[1678]: Mounted /dev/sdb1 (Read-Write, label "Elements", NTFS 3.1)
Aug 28 18:16:03 john-ML3108b ntfs-3g[1678]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Aug 28 18:16:03 john-ML3108b ntfs-3g[1678]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096,default_permissions
Aug 28 18:16:03 john-ML3108b ntfs-3g[1678]: Global ownership and permissions enforced, configuration type 7
Aug 28 18:16:04 john-ML3108b kernel: [   46.344019] wlan0: no IPv6 routers present
Aug 28 18:14:24 john-ML3108b ntpdate[1439]: step time server 91.189.94.4 offset -101.168244 sec
Aug 28 18:14:32 john-ML3108b NetworkManager[866]: <info> (wlan0): IP6 addrconf timed out or failed.
Aug 28 18:14:32 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Aug 28 18:14:32 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Aug 28 18:14:32 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug 28 18:14:32 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 28 18:14:32 john-ML3108b NetworkManager[866]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Aug 28 18:15:24 john-ML3108b dbus[830]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Aug 28 18:15:25 john-ML3108b dbus[830]: [system] Successfully activated service 'com.ubuntu.SystemService'
Aug 28 18:15:31 john-ML3108b dbus[830]: [system] Activating service name='org.debian.apt' (using servicehelper)
Aug 28 18:15:38 john-ML3108b AptDaemon: INFO: Initializing daemon
Aug 28 18:15:38 john-ML3108b dbus[830]: [system] Successfully activated service 'org.debian.apt'
Aug 28 18:15:38 john-ML3108b AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Aug 28 18:15:38 john-ML3108b AptDaemon.Trans: INFO: Simulate was called
Aug 28 18:15:38 john-ML3108b AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/c3d9e82f24124674877173841e63ae89
Aug 28 18:15:51 john-ML3108b AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Aug 28 18:17:01 john-ML3108b CRON[1996]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 28 18:20:38 john-ML3108b AptDaemon: INFO: Quitting due to inactivity
Aug 28 18:20:38 john-ML3108b AptDaemon: INFO: Quitting was requested
Aug 28 18:23:34 john-ML3108b wpa_supplicant[1235]: WPA: Group rekeying completed with 00:26:5a:27:d9:94 [GTK=TKIP]
Aug 28 18:33:34 john-ML3108b wpa_supplicant[1235]: WPA: Group rekeying completed with 00:26:5a:27:d9:94 [GTK=TKIP]
Aug 28 18:43:34 john-ML3108b wpa_supplicant[1235]: WPA: Group rekeying completed with 00:26:5a:27:d9:94 [GTK=TKIP]
Aug 28 18:53:34 john-ML3108b wpa_supplicant[1235]: WPA: Group rekeying completed with 00:26:5a:27:d9:94 [GTK=TKIP]
Aug 28 19:03:34 john-ML3108b wpa_supplicant[1235]: WPA: Group rekeying completed with 00:26:5a:27:d9:94 [GTK=TKIP]
Aug 28 19:13:34 john-ML3108b wpa_supplicant[1235]: WPA: Group rekeying completed with 00:26:5a:27:d9:94 [GTK=TKIP]
Aug 28 19:17:01 john-ML3108b CRON[2262]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 28 19:23:34 john-ML3108b wpa_supplicant[1235]: WPA: Group rekeying completed with 00:26:5a:27:d9:94 [GTK=TKIP]
Aug 28 19:33:35 john-ML3108b wpa_supplicant[1235]: WPA: Group rekeying completed with 00:26:5a:27:d9:94 [GTK=TKIP]
Aug 28 19:43:35 john-ML3108b wpa_supplicant[1235]: WPA: Group rekeying completed with 00:26:5a:27:d9:94 [GTK=TKIP]
Aug 28 19:53:35 john-ML3108b wpa_supplicant[1235]: WPA: Group rekeying completed with 00:26:5a:27:d9:94 [GTK=TKIP]
Aug 28 20:03:35 john-ML3108b wpa_supplicant[1235]: WPA: Group rekeying completed with 00:26:5a:27:d9:94 [GTK=TKIP]
Aug 28 20:13:35 john-ML3108b wpa_supplicant[1235]: WPA: Group rekeying completed with 00:26:5a:27:d9:94 [GTK=TKIP]
john@john-ML3108b:~$ 
john@john-ML3108b:~$ cat dmesg
cat: dmesg: No such file or directory
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
Sorry, my mistake it is just dmesg

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Sorry, my mistake it is just dmesg

[    0.175894] pci_bus 0000:06: resource 4 [io  0x0000-0xffff]
[    0.175897] pci_bus 0000:06: resource 5 [mem 0x20000000-0xffffffff]
[    0.175901] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.175959] NET: Registered protocol family 2
[    0.176046] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.176275] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.176384] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.176486] TCP: Hash tables configured (established 16384 bind 16384)
[    0.176489] TCP reno registered
[    0.176493] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.176502] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.176608] NET: Registered protocol family 1
[    0.176638] pci 0000:00:00.0: Found disabled HT MSI Mapping
[    0.176644] pci 0000:00:00.0: Enabling HT MSI Mapping
[    0.176686] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.176694] pci 0000:00:05.0: Boot video device
[    0.656090] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.656141] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.656158] PCI: CLS 64 bytes, default 64
[    0.656212] Simple Boot Flag at 0x31 set to 0x1
[    0.656556] audit: initializing netlink socket (disabled)
[    0.656570] type=2000 audit(1346174117.652:1): initialized
[    0.682899] Trying to unpack rootfs image as initramfs...
[    0.716170] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.724399] VFS: Disk quotas dquot_6.5.2
[    0.724500] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.725391] fuse init (API version 7.16)
[    0.725514] msgmni has been set to 837
[    0.736568] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.736607] io scheduler noop registered
[    0.736610] io scheduler deadline registered
[    0.736629] io scheduler cfq registered (default)
[    0.736786] pcieport 0000:00:03.0: setting latency timer to 64
[    0.736819] pcieport 0000:00:03.0: irq 40 for MSI/MSI-X
[    0.736905] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.736943] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.737722] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.738357] ACPI: AC Adapter [AC] (on-line)
[    0.738454] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.738461] ACPI: Power Button [PWRB]
[    0.738511] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.738516] ACPI: Sleep Button [SLPB]
[    0.738575] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.738767] ACPI: Lid Switch [LID]
[    0.738835] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.738840] ACPI: Power Button [PWRF]
[    0.738874] ACPI: acpi_idle registered with cpuidle
[    0.738906] Marking TSC unstable due to TSC halts in idle
[    0.741035] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.741106] ERST: Table is not found!
[    0.741230] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.742850] Linux agpgart interface v0.103
[    0.748996] isapnp: Scanning for PnP cards...
[    0.798342] brd: module loaded
[    0.799082] loop: module loaded
[    0.799395] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.799888] Fixed MDIO Bus: probed
[    0.799923] PPP generic driver version 2.4.2
[    0.799993] tun: Universal TUN/TAP device driver, 1.6
[    0.800027] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.804231] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.804471] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 23
[    0.804496] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 23 (level, high) -> IRQ 23
[    0.804517] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.804521] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.804566] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.804598] ehci_hcd 0000:00:0b.1: debug port 1
[    0.804607] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.804637] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xb0005000
[    0.816201] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.816439] hub 1-0:1.0: USB hub found
[    0.816446] hub 1-0:1.0: 8 ports detected
[    0.816547] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.816819] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    0.816841] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    0.816863] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.816867] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.816925] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.816968] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xb0004000
[    0.852975] ACPI: Battery Slot [BAT0] (battery present)
[    0.988537] hub 2-0:1.0: USB hub found
[    0.988548] hub 2-0:1.0: 8 ports detected
[    0.988665] uhci_hcd: USB Universal Host Controller Interface driver
[    0.988792] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.992281] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.996050] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.996260] mousedev: PS/2 mouse device common for all mice
[    0.999552] rtc_cmos 00:07: RTC can wake from S4
[    0.999687] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.999731] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.999892] device-mapper: uevent: version 1.0.3
[    0.999990] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.000074] EISA: Probing bus 0 at eisa.0
[    1.000078] EISA: Cannot allocate resource for mainboard
[    1.000082] Cannot allocate resource for EISA slot 1
[    1.000084] Cannot allocate resource for EISA slot 2
[    1.000087] Cannot allocate resource for EISA slot 3
[    1.000090] Cannot allocate resource for EISA slot 4
[    1.000093] Cannot allocate resource for EISA slot 5
[    1.000095] Cannot allocate resource for EISA slot 6
[    1.000098] Cannot allocate resource for EISA slot 7
[    1.000101] Cannot allocate resource for EISA slot 8
[    1.000103] EISA: Detected 0 cards.
[    1.000116] cpufreq-nforce2: No nForce2 chipset.
[    1.000163] cpuidle: using governor ladder
[    1.000236] cpuidle: using governor menu
[    1.000239] EFI Variables Facility v0.08 2004-May-17
[    1.000548] TCP cubic registered
[    1.000726] NET: Registered protocol family 10
[    1.001363] NET: Registered protocol family 17
[    1.001388] Registering the dns_resolver key type
[    1.001422] Using IPI No-Shortcut mode
[    1.001548] PM: Hibernation image not present or could not be loaded.
[    1.001561] registered taskstats version 1
[    1.190104] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.283731] isapnp: No Plug & Play device found
[    1.296377] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.464657] Freeing initrd memory: 13300k freed
[    1.484839]   Magic number: 8:639:290
[    1.484892] tty tty23: hash matches
[    1.484968] rtc_cmos 00:07: setting system clock to 2012-08-28 17:15:19 UTC (1346174119)
[    1.484974] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3400+ (1 cpu cores) (version 2.20.00)
[    1.485017] powernow-k8: fid 0xa (1800 MHz), vid 0xe
[    1.485020] powernow-k8: fid 0x8 (1600 MHz), vid 0x10
[    1.485023] powernow-k8: fid 0x0 (800 MHz), vid 0x18
[    1.485079] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.485081] EDD information not available.
[    1.485218] Freeing unused kernel memory: 696k freed
[    1.485751] Write protecting the kernel text: 5332k
[    1.485793] Write protecting the kernel read-only data: 2188k
[    1.511905] udevd[77]: starting version 173
[    1.731153] pata_amd 0000:00:0d.0: version 0.4.1
[    1.731213] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.753075] scsi0 : pata_amd
[    1.756911] scsi1 : pata_amd
[    1.757518] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.757522] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    1.763204] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.763450] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[    1.763473] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, high) -> IRQ 21
[    1.763479] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.771842] usbcore: registered new interface driver uas
[    1.792090] usb 2-2: new low speed USB device number 2 using ohci_hcd
[    1.920477] ata1.00: ATA-6: ST960815A, 3.ALC, max UDMA/100
[    1.920483] ata1.00: 117210240 sectors, multi 16: LBA48 
[    1.920494] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc600c000) ACPI=0x3f01f (20:600:0x13)
[    1.936418] ata1.00: configured for UDMA/100
[    1.936569] scsi 0:0:0:0: Direct-Access     ATA      ST960815A        3.AL PQ: 0 ANSI: 5
[    1.936802] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.937009] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.937066] sd 0:0:0:0: [sda] Write Protect is off
[    1.937070] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.937094] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.969536]  sda: sda1 sda2 < sda5 >
[    1.969955] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.100342] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WG02, max UDMA/33
[    2.100355] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc600c000) ACPI=0x7001 (60:600:0x11)
[    2.116264] ata2.00: configured for UDMA/33
[    2.121667] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WG02 PQ: 0 ANSI: 5
[    2.126528] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.126533] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.126682] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.126768] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.132881] Initializing USB Mass Storage driver...
[    2.138811] scsi2 : usb-storage 1-1:1.0
[    2.139732] usbcore: registered new interface driver usb-storage
[    2.139737] USB Mass Storage support registered.
[    2.145477] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2:1.0/input/input5
[    2.145637] generic-usb 0003:15D9:0A4C.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:0b.0-2/input0
[    2.145663] usbcore: registered new interface driver usbhid
[    2.145674] usbhid: USB HID core driver
[    2.285084] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:03:25:47:e6:d6
[    2.285091] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    2.537894] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.537901] EXT4-fs (sda1): write access will be enabled during recovery
[    3.141955] scsi 2:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[    3.145939] sd 2:0:0:0: [sdb] 1953519616 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.146331] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    3.147437] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    3.149200] sd 2:0:0:0: [sdb] Asking for cache data failed
[    3.149207] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.151183] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    3.152190] sd 2:0:0:0: [sdb] Asking for cache data failed
[    3.152193] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.159558]  sdb: sdb1
[    3.163573] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    3.166179] sd 2:0:0:0: [sdb] Asking for cache data failed
[    3.166183] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.166187] sd 2:0:0:0: [sdb] Attached SCSI disk
[    4.951301] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.951314] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364486
[    4.951422] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364285
[    4.951441] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364483
[    4.951457] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364319
[    4.951474] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364251
[    4.951491] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364316
[    4.951507] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364318
[    4.951523] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364308
[    4.951539] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364269
[    4.951557] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364293
[    4.951579] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364284
[    4.951595] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364282
[    4.951612] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364235
[    4.951628] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364259
[    4.951644] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364250
[    4.951660] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364246
[    4.951676] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364244
[    4.951692] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364203
[    4.951708] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364196
[    4.951723] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364201
[    4.951739] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364199
[    4.951755] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364236
[    4.951772] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 526796
[    4.951795] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 526696
[    4.951811] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364241
[    4.951827] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2362008
[    4.951844] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364197
[    4.951859] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364192
[    4.951876] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2363727
[    4.951894] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2634703
[    4.951911] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2363935
[    4.951928] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2362557
[    4.951944] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364317
[    4.951960] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2364469
[    4.951975] EXT4-fs (sda1): 34 orphan inodes deleted
[    4.951978] EXT4-fs (sda1): recovery complete
[    5.225172] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   18.285841] udevd[312]: starting version 173
[   18.716528] Adding 455676k swap on /dev/sda5.  Priority:-1 extents:1 across:455676k 
[   18.739208] lp: driver loaded but no devices found
[   19.016332] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS
[   19.016410] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.018096] acpi device:03: registered as cooling_device1
[   19.018210] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   19.018320] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.185659] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   19.220365] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   19.220441] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   19.236416] cfg80211: Calling CRDA to update world regulatory domain
[   19.242708] NV_TCO: NV TCO WatchDog Timer Driver v0.01
[   19.242931] NV_TCO: Watchdog reboot not detected.
[   19.243049] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
[   19.775539] cfg80211: World regulatory domain updated:
[   19.775546] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.775551] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.775555] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.775559] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.775562] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.775566] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.832200] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   19.832220] rtl8180 0000:06:09.0: PCI INT A -> Link[LNK1] -> GSI 11 (level, high) -> IRQ 11
[   19.832233] rtl8180 0000:06:09.0: setting latency timer to 64
[   19.907820] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008/0x0
[   19.954172] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   19.954178] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954182] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   19.954186] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954189] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   19.954193] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954195] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   19.954199] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954202] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   19.954206] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954209] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   19.954212] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954215] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   19.954219] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954222] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   19.954225] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954228] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   19.954232] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954235] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   19.954238] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954241] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   19.954245] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954248] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   19.954251] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954254] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   19.954258] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.954261] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   19.954265] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   19.960161] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   20.270278] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   20.270965] ieee80211 phy0: hwaddr 00c0a8eccde6, RTL8185vD + rtl8225
[   20.926846] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   21.097756] nvidia: module license 'NVIDIA' taints kernel.
[   21.097763] Disabling lock debugging due to kernel taint
[   22.871468] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 20
[   22.871495] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 20 (level, high) -> IRQ 20
[   22.871505] nvidia 0000:00:05.0: setting latency timer to 64
[   22.871511] vgaarb: device changed decodes: PCI:0000:00:05.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   22.872992] NVRM: loading NVIDIA UNIX x86 Kernel Module  280.13  Wed Jul 27 16:55:43 PDT 2011
[   22.887522] type=1400 audit(1346174140.898:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=695 comm="apparmor_parser"
[   22.888094] type=1400 audit(1346174140.902:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=695 comm="apparmor_parser"
[   22.888442] type=1400 audit(1346174140.902:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=695 comm="apparmor_parser"
[   22.889322] type=1400 audit(1346174140.902:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=590 comm="apparmor_parser"
[   22.889867] type=1400 audit(1346174140.902:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=590 comm="apparmor_parser"
[   22.890214] type=1400 audit(1346174140.902:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=590 comm="apparmor_parser"
[   22.891090] type=1400 audit(1346174140.902:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=596 comm="apparmor_parser"
[   22.891630] type=1400 audit(1346174140.902:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=596 comm="apparmor_parser"
[   22.891979] type=1400 audit(1346174140.902:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=596 comm="apparmor_parser"
[   23.075346] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 19
[   23.075372] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 19 (level, high) -> IRQ 19
[   23.075377] hda_intel: Disabling MSI
[   23.075423] HDA Intel 0000:00:10.1: setting latency timer to 64
[   24.752378] input: HDA NVidia Mic at Ext Front Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input8
[   25.276365] type=1400 audit(1346174143.290:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=884 comm="apparmor_parser"
[   25.321942] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   25.321948] vesafb: scrolling: redraw
[   25.321953] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   25.322381] vesafb: framebuffer at 0xc0000000, mapped to 0xdde80000, using 3072k, total 3072k
[   25.322638] Console: switching to colour frame buffer device 128x48
[   25.322672] fb0: VESA VGA frame buffer device
[   25.512755] ppdev: user-space parallel port driver
[   26.497249] init: failsafe main process (799) killed by TERM signal
[   26.532447] init: apport pre-start process (952) terminated with status 1
[   26.540468] init: apport post-stop process (974) terminated with status 1
[   27.283279] Bluetooth: Core ver 2.16
[   27.283338] NET: Registered protocol family 31
[   27.283341] Bluetooth: HCI device and connection manager initialized
[   27.283345] Bluetooth: HCI socket layer initialized
[   27.283347] Bluetooth: L2CAP socket layer initialized
[   27.285266] Bluetooth: SCO socket layer initialized
[   27.292681] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.292687] Bluetooth: BNEP filters: protocol multicast
[   27.315366] Bluetooth: RFCOMM TTY layer initialized
[   27.315375] Bluetooth: RFCOMM socket layer initialized
[   27.315378] Bluetooth: RFCOMM ver 1.11
[   28.342258] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   31.752125] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.755835] forcedeth 0000:00:14.0: eth0: no link during initialization
[   31.762986] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.941684] init: plymouth-stop pre-start process (1263) terminated with status 1
[   33.078948] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   36.020066] wlan0: authenticate with 00:26:5a:27:d9:94 (try 1)
[   36.021728] wlan0: authenticated
[   36.116068] wlan0: associate with 00:26:5a:27:d9:94 (try 1)
[   36.119775] wlan0: RX AssocResp from 00:26:5a:27:d9:94 (capab=0xc31 status=0 aid=1)
[   36.119779] wlan0: associated
[   36.120438] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   36.120511] cfg80211: Calling CRDA for country: GB
[   36.125769] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   36.125776] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125779] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   36.125783] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125786] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   36.125790] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125793] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   36.125796] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125799] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   36.125803] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125806] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   36.125809] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125812] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   36.125816] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125819] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   36.125822] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125825] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   36.125829] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125831] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   36.125835] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125838] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   36.125841] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125844] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   36.125848] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125851] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   36.125854] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   36.125857] cfg80211: Disabling freq 2484 MHz
[   36.125861] cfg80211: Regulatory domain changed to country: GB
[   36.125863] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   36.125866] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   36.125870] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   36.125873] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   36.125876] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   46.344019] wlan0: no IPv6 routers present
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
Use all commands as root or with sudo

Please try this first:

```

umount /dev/sr0

```

If it insists that it is busy then add this line to /etc/fstab:

```

/dev/sr0  /media/new_folder  iso9660  ro,user,noauto,unhide

```

And then:

```

mount /dev/sr0

```

---

### Post by m3t3ors on 2012-08-28
> **rukiaEnix said:**
> Use all commands as root or with sudo

Please try this first:

```

umount /dev/sr0

```

If it insists that it is busy then add this line to /etc/fstab:

```

/dev/sr0  /media/new_folder  iso9660  ro,user,noauto,unhide

```

And then:

```

mount /dev/sr0

```

john@john-ML3108b:~$ sudo unmount /dev/sr0
[sudo] password for john: 
sudo: unmount: command not found
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
It is umount

---

### Post by m3t3ors on 2012-08-28
john@john-ML3108b:~$ sudo umount /dev/sr0
umount: /dev/sr0: not mounted
john@john-ML3108b:~$ 
> **rukiaEnix said:**
> It is umount

---

### Post by m3t3ors on 2012-08-28
do i still need to add the line to etc/fstab even though it not mounted?

---

### Post by rukiaEnix on 2012-08-28
Yes, please proceed with the other two steps I told you. It is /etc/fstab the path not etc/fstab

---

### Post by m3t3ors on 2012-08-28
john@john-ML3108b:~$ sudo nano /etc/fstab
john@john-ML3108b:~$ sudo mount /dev/sr0
mount: /dev/sr0 already mounted or /media/new_folder busy
john@john-ML3108b:~$

---

### Post by rukiaEnix on 2012-08-28
You know, this is starting to get annoying. So let's do something on the hardware now.


[LIST]
[*]Turn off the computer, disconnect the DVD device cable.
[*]Turn on the computer, log in and everything.
[*]Turn it off again, connect the DVD device cable again.
[*]Turn on the computer again and put inside the @$%&" CD.
[/LIST]

Let's see if it works -.- sorry for the insults but it is against your DVD device not you -.-

---

### Post by m3t3ors on 2012-08-28
no problem, its annoying me
right first its a laptop so disconnecting is not possible.
second, ive rebooted twice both times with no disc in the drive

what if i just reinstall ubuntu

---

### Post by rukiaEnix on 2012-08-28
That will arrange everything (reinstalling) even though I didn't want to arrive to that solution -.-. It is really weird your problem, I even googled for it and it has happened to other people but it looks like nobody hast got already the answer to this.

---

### Post by m3t3ors on 2012-08-28
id like to thank you for all the help and advice, i really appreciate it
think il just re-install and start a fresh
once again thanks

---

### Post by rukiaEnix on 2012-08-28
You're welcome even though I didn't give a solution -.-

---

### Post by Hadaka on 2012-08-28
Hi, I have been following this thread to see how it would be resolved.
Then as an experiment i repeated the steps in media settings to see if
i could repeat the problem, well..it sure did. I set dvd and cd in removable
media to "do nothing" and checked the box on the bottom of the media
box...the dont ask..or notify me. I then inserted a dvd..and as expected it
did..nothing...just as requested...I also took a look at dev/sr0   it showed
busy...so by do nothing..it must set some bit that basically "busy's it out.
i then rebooted..reset the dvd and cd to VLC player . Inserted a dvd and it
played on vlc player...as expected. I then rebooted to save my settings
check them out...and NOPE, all settings back to default players, so i tried
to reset to VLC again...it looked like it took it..but as soon as a reopened
the settings..media player..they were back to default, now no matter what i
attempt to do to change from default settings...it refuses. so there must be
a bit of a bug in 12.04, ....I also have 11.10 on this machine and it does not do
this...i can change any setting i want..or do nothing..and then reset to vlc no
problem, Looks like now i also am going to have to do a reload...interesting.

---

### Post by m3t3ors on 2012-08-28
thanks for that, ive never seen this problem until it happend.
hope they sort the bug out

---

### Post by m3t3ors on 2012-08-30
ok, i re-installed the laptop and decided to go back to ubuntu 11.10
installed xfburn and devede along with samba. that is all i ever install. and i still get the error message 
"no burners are currently available
possibly the disc are in use and cannot get accessed
please unmount and start the application"

---

### Post by Hadaka on 2012-08-30
Hi, did you wipe the drive and do a clean install of 11.10?
or just allow the install to nuke the drive?

---

### Post by m3t3ors on 2012-08-30
> **Hadaka said:**
> Hi, did you wipe the drive and do a clean install of 11.10?
or just allow the install to nuke the drive?

clean install, low level format

---

### Post by m3t3ors on 2012-08-30
ive just put windows xp pro on the laptop and alls good. so im now re-installing ubuntu 11.10 and will post the out come

---

### Post by m3t3ors on 2012-08-30
alls good again
thanks for all the help and advice

---

### Post by rukiaEnix on 2012-08-31
Good to hear it is solved! Even though is really strange that error.

---

