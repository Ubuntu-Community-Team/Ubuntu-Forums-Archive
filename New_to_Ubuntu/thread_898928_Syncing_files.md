---
title: "Syncing files"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by furialis on 2008-08-23
How can I sync /etc/passwd and /etc/group?

---

### Post by SNuxoll on 2008-08-23
What do you mean? /etc/passwd and /etc/group are two completely different files, and do different things.

---

### Post by furialis on 2008-08-23
I'm using remastersys to make a backup of my system. 

From the FAQ:

mkisofs - Currently there is a file size limit of 4.0GB for iso9660 which means that the compressed filesystem must be below 4GB.

casper - the ubuntu livecd scripts are very picky about creating the livecd user.  If you have issues, please run pwck and grpck as root to fix /etc/passwd and /etc/group.  These have to be in sync in order for casper to create the livecd/dvd user.

I'm getting the error, "user not known to the underlying authentication module" when I try to install the image.

remastersys log
[php]
Source directory entry mnt already used! - trying mnt_1
Source directory entry dev already used! - trying dev_1
Source directory entry etc already used! - trying etc_1
Source directory entry sys already used! - trying sys_1
Source directory entry var already used! - trying var_1
Source directory entry proc already used! - trying proc_1
Source directory entry tmp already used! - trying tmp_1
Cannot stat dir/file //home/b/.gvfs because Permission denied, ignoringSource directory entry media already used! - trying media_1
File //home/b/.tor/cached-status/FFCB46DB1339DA84674C70D7CB586434C4370441 changed size while reading filesystem, attempting to re-read
------------------------------------------------------
Mount information
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/b/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=b)
------------------------------------------------------
Casper Script info
total 128
-rwxr-xr-x 1 root root  297 2008-05-27 15:33 01integrity_check
-rwxr-xr-x 1 root root  230 2008-05-27 15:33 02timezone
-rwxr-xr-x 1 root root  383 2008-05-27 15:33 05mountpoints
-rw-r--r-- 1 root root 2888 2008-05-27 15:33 10adduser
-rwxr-xr-x 1 root root  400 2008-05-27 15:33 12fstab
-rwxr-xr-x 1 root root  742 2008-05-27 15:33 13swap
-rwxr-xr-x 1 root root 1431 2008-05-27 15:33 14locales
-rw-r--r-- 1 root root 1938 2008-05-27 15:33 15autologin
-rwxr-xr-x 1 root root  577 2008-05-27 15:33 18hostname
-rwxr-xr-x 1 root root 6774 2008-05-27 15:33 19keyboard
-rwxr-xr-x 1 root root 1383 2008-05-27 15:33 20xconfig
-rwxr-xr-x 1 root root  668 2008-05-27 15:33 22gnome_panel_data
-rwxr-xr-x 1 root root  904 2008-05-27 15:33 22screensaver
-rwxr-xr-x 1 root root  380 2008-05-27 15:33 23etc_modules
-rwxr-xr-x 1 root root 2817 2008-05-27 15:33 23networking
-rwxr-xr-x 1 root root 1444 2008-05-27 15:33 24preseed
-rwxr-xr-x 1 root root 1696 2008-05-27 15:33 25configure_init
-rwxr-xr-x 1 root root 7442 2008-05-27 15:33 30accessibility
-rwxr-xr-x 1 root root  758 2008-05-27 15:33 31disable_update_notifier
-rwxr-xr-x 1 root root  808 2008-05-27 15:33 32disable_hibernation
-rwxr-xr-x 1 root root  570 2008-05-27 15:33 33enable_apport_crashes
-rwxr-xr-x 1 root root  305 2008-05-27 15:33 34disable_kwallet
-rwxr-xr-x 1 root root  562 2008-05-27 15:33 35fix_language_selector
-rwxr-xr-x 1 root root  407 2008-05-27 15:33 36disable_trackerd
-rwxr-xr-x 1 root root  660 2008-05-27 15:33 38disable_restricted_manager
-rwxr-xr-x 1 root root  739 2008-05-27 15:33 40install_driver_updates
-rwxr-xr-x 1 root root  246 2008-05-27 15:33 41apt_cdrom
-rwxr-xr-x 1 root root  377 2008-05-27 15:33 42disable_apparmor
-rwxr-xr-x 1 root root  563 2008-05-27 15:33 43disable_updateinitramfs
-rwxr-xr-x 1 root root  922 2008-05-27 15:33 44pk_allow_ubuntu
------------------------------------------------------
/etc/remastersys.conf info
#Remastersys Global Configuration File


# This is the temporary working directory and won't be included on the cd/dvd
WORKDIR="/home/remastersys"


# Here you can add any other files or directories to be excluded from the live filesystem
# Separate each entry with a space
EXCLUDES=""


# Here you can change the livecd/dvd username
LIVEUSER="custom"


# Here you can change the name of the livecd/dvd label
LIVECDLABEL="Custom Live CD"


# Here you can change the name of the ISO file that is created
CUSTOMISO="custom$1.iso"
------------------------------------------------------
/etc/casper.conf info
# This file should go in /etc/casper.conf
# Supported variables are:
# USERNAME, USERFULLNAME, HOST, BUILD_SYSTEM
 
export USERNAME="custom"
export USERFULLNAME="Live session user"
export HOST="custom"
export BUILD_SYSTEM="Ubuntu"
------------------------------------------------------
/etc/passwd info
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
dhcp:x:101:102::/nonexistent:/bin/false
syslog:x:102:103::/home/syslog:/bin/false
klog:x:103:104::/home/klog:/bin/false
hplip:x:104:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
gdm:x:106:114:Gnome Display Manager:/var/lib/gdm:/bin/false
pulse:x:107:116:PulseAudio daemon,,,:/var/run/pulse:/bin/false
messagebus:x:108:119::/var/run/dbus:/bin/false
avahi:x:109:120:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
polkituser:x:110:122:PolicyKit,,,:/var/run/PolicyKit:/bin/false
haldaemon:x:111:123:Hardware abstraction layer,,,:/var/run/hald:/bin/false
b:x:1000:1000:,,,:/home/b:/bin/bash
privoxy:x:112:65534::/etc/privoxy:/bin/false
debian-tor:x:113:124::/var/lib/tor:/bin/bash
------------------------------------------------------
/etc/group info
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:b
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:b
fax:x:21:
voice:x:22:
cdrom:x:24:b
floppy:x:25:b
tape:x:26:
sudo:x:27:
audio:x:29:pulse,b
dip:x:30:b
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:b
sasl:x:45:
plugdev:x:46:b
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
fuse:x:107:b
ssl-cert:x:108:
lpadmin:x:109:b
crontab:x:110:
mlocate:x:111:
ssh:x:112:
avahi-autoipd:x:113:
gdm:x:114:
admin:x:115:b
pulse:x:116:
pulse-access:x:117:
pulse-rt:x:118:
messagebus:x:119:
avahi:x:120:
netdev:x:121:
polkituser:x:122:
haldaemon:x:123:
b:x:1000:
debian-tor:x:124:
------------------------------------------------------
Command-line options = backup
------------------------------------------------------
[/php]

---

