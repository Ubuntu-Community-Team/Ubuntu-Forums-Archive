---
title: "HOWTO: mount windows partition as home directory"
date: 2009-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Evgeny on 2009-08-04
**To mount windows partition as home directory**
[COLOR="Red"]
**ACHTUNG! ACHTUNG!**[/COLOR]
These things add security hole in the system. Don't apply this in multiuser environments.
This howto only for personal use.

*(tested in Ubuntu 9.04 Jaunty)*

1. install latest ntfs-3g package (if partition is NTFS) from debian repo:

[http://packages.debian.org/unstable/otherosfs/ntfs-3g](http://packages.debian.org/unstable/otherosfs/ntfs-3g)
[http://packages.debian.org/sid/libntfs-3g54](http://packages.debian.org/sid/libntfs-3g54)

or from command line:
```

cd /tmp
wget http://ftp.ee.debian.org/debian/pool/main/n/ntfs-3g/ntfs-3g_2009.4.4-1_i386.deb http://ftp.cz.debian.org/debian/pool/main/n/ntfs-3g/libntfs-3g54_2009.4.4-1_i386.deb
sudo dpkg -i libntfs-3g54_2009.4.4-1_i386.deb ntfs-3g_2009.4.4-1_i386.deb

```

2. add to /etc/fstab:
```

# windows partition 
UUID=<disk uuid>  /home  <fs driver>  uid=1000,gid=1000  0  1

```
where fs driver is vfat or ntfs-3g and to get disk uuid (X, Y depend on your configuration):
```

sudo vol_id --uuid /dev/sdXY

```

3. Next problem is Pulseaudio daemon as it's need POSIX file system to keep configuration files.
As workaround of this we will tell to daemon to keep these files in /var/lib/pulse directory:
```

sudo mkdir /var/lib/pulse
sudo chmod 777 /var/lib/pulse
```

another way is to replace pulseaudio with [OSS ]("http://www.opensound.com/download.cgi") but it's a bit complicated way.

Then create two files in home directory: *.xinitrc* and *.xsession* and paste this code
```

export PULSE_HOME=/var/lib/pulse/$USER
export PULSE_STATE_PATH=$PULSE_HOME
export PULSE_RUNTIME_PATH=$PULSE_HOME
```

and add additional string in .xsession
```
gnome-session > $HOME/.xsession-errors 2>&1
```
replace gnome-session with kde-session if used KDE.

4. to get rid of GDM warnings set these values in /etc/gdm/gdm.conf:
```

RelaxPermissions=2
CheckDirOwner=false

```

**It's all!**

In general it works fine, but operations like copying big files may eat 90% of CPU time.

---

### Post by wieman01 on 2009-08-04
It's "Achtung" by the way, unless that is Chinese. :-)

---

