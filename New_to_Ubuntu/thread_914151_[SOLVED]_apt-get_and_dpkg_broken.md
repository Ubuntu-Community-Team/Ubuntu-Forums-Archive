---
title: "[SOLVED] apt-get and dpkg broken"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by dfullbrook on 2008-09-08
Hi,

I tried installing the GUI on my 8.0.4 server using

$ sudo apt-get install ubuntu-desktop

Unfortunately, it filled my disk partition and bombed out (I didn't note the specific errors but it was trying to write to disk and reported disk full).. So I increased the parition size and tried again. Now it says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -' to correct the problem.

When I run this command I get the error:

dpkg: too many errors, stopping
dpkg: ../..src/packages.c:252: process_queue: Assertion '!queuelen' failed.
Aborted.

(I've searched the forums and tried "sudo apt-get update" and "sudo apt-get upgrade" but they all give the same original error message "dpkg was interrupred, you must .... etc".)

Any ideas?

Appreciate any help you can provide.

---

### Post by Elfy on 2008-09-08
Run it with sudo

```
sudo dpkg --configure -a
```

---

### Post by bumanie on 2008-09-08
In terminal > sudo dpkg --configure -aAny packages not completely downloaded should start from where they were interrupted. If it persists, try a different server.

---

### Post by dfullbrook on 2008-09-08
Sorry, forgot to say that I ran the commands with sudo. It didn't help.

---

### Post by overdrank on 2008-09-08
> **dfullbrook said:**
> Sorry, forgot to say that I ran the commands with sudo. It didn't help.

Ok you may try the command ```
sudo apt-get install -f
```

---

### Post by bumanie on 2008-09-08
May be you should try a filesystem check. Do this to force a check on reboot > sudo touch /forcefsck > sudo shutdown -r nowAlso, would like to look at the output of > df -h / and > df -h /home

---

### Post by dfullbrook on 2008-09-09
Ran the commands you suggested bu the problem remains. Here is the output of df -h / and df -h /home
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             4.5G  2.2G  2.2G  50% /

```
and
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              15G  165M   14G   2% /home

```

---

### Post by Rocket2DMn on 2008-09-09
Can you please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
sudo apt-get install -f
```

---

### Post by dfullbrook on 2008-09-09
output from sudo fdisk -l
```

Disk /dev/sda: 20.4 GB, 20496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba70ba70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        2491    20008926    5  Extended
/dev/sda5               1         583     4682884+  83  Linux
/dev/sda6            2445        2491      377496   82  Linux swap / Solaris
/dev/sda7             584        2444    14948451   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3fbc3fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1826    14667313+   7  HPFS/NTFS

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=fe9a0a90-f85e-4d71-b284-03c1462d6205 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e0dad9d3-03ca-4623-bf8e-68ba21f158b2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# Added by DMF
/dev/sda7       /home           ext3    defaults        1       1

```
sudo blkid
```

/dev/sda5: UUID="fe9a0a90-f85e-4d71-b284-03c1462d6205" TYPE="ext3"
/dev/sda6: TYPE="swap" UUID="391ddb8d-3f58-475f-86b8-d5e1bcc45b57"
/dev/sdb1: UUID="98EA06AFEA0689A8" LABEL="Backup" TYPE="ntfs"
/dev/sda7: UUID="1822571f-8cbd-4e45-a68a-1d695a121808" SEC_TYPE="ext2" TYPE="ext3"

```
sudo apt-get install -f
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```

---

### Post by Rocket2DMn on 2008-09-09
OK, I don't think this is quite related to your problem, but it looks like at some point you resized partitions, and now the UUID of your swap doesn't match what is in fstab, so we'll fix that.
```
gksudo gedit /etc/fstab
```
Now change the line
```
# /dev/sda6
UUID=e0dad9d3-03ca-4623-bf8e-68ba21f158b2 none            swap    sw              0       0
```
replacing the UUID, so that the line looks like
```
# /dev/sda6
UUID=391ddb8d-3f58-475f-86b8-d5e1bcc45b57 none            swap    sw              0       0
```
Save and close, then run
```
sudo mount -a
```

----------------

Back to the original problem.  Can you now please post the output of
```
sudo dpkg --configure -a
```
so that we can see what's happening (if anything).  If it doesn't output anything, the problem should be fixed...

---

### Post by dfullbrook on 2008-09-10
Thanks for fixing the swap UUID. Here's the full output of sudo dpkg --configure -a
```

Setting up dbus (1.1.20-1ubuntu2) ...
Warning: The home dir /var/run/dbus you specified can't be accessed: No such file or directory
The user `messagebus' already exists. Exiting.
chown: cannot access `/var/run/dbus': No such file or directory
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hal:
 hal depends on dbus (>= 0.61); however:
  Package dbus is not configured yet.
dpkg: error processing hal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dhcdbd:
 dhcdbd depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
dpkg: error processing dhcdbd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on gnome-mount; however:
  Package gnome-mount is not configured yet.
 gnome-volume-manager depends on hal (>= 0.5.5.1); however:
  Package hal is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.14-19:
 libgtkhtml3.14-19 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.14-19 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution-plugins depends on libgtkhtml3.14-19 (>= 3.18.2); however:
  Package libgtkhtml3.14-19 is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail-gnome-module:
 libgail-gnome-module depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgail-gnome-module (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on dbus; however:
  Package dbus is not configured yet.
 evolution depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution depends on libgtkhtml3.14-19 (>= 3.18.2); however:
  Package libgtkhtml3.14-19 is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of f-spot:
 f-spot depends on dbus; however:
  Package dbus is not configured yet.
 f-spot depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing f-spot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-vfs2.0-cil:
 libgnome-vfs2.0-cil depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-vfs2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-utils:
 bluez-utils depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing bluez-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-spell:
 gnome-spell depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-spell depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-spell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-applets depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit-gnome:
 policykit-gnome depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
 policykit-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing policykit-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tracker:
 tracker depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing tracker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-bin:
 libgnomevfs2-bin depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomevfs2-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 compiz-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ekiga:
 ekiga depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 ekiga depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing ekiga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avahi-daemon:
 avahi-daemon depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
dpkg: error processing avahi-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gimp-gnomevfs:
 gimp-gnomevfs depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gimp-gnomevfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on hal (>= 0.5.10); however:
  Package hal is not configured yet.
 gnome-power-manager depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-power-manager depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 eog depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf-editor:
 gconf-editor depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing gconf-editor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-settings-daemon depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-settings-daemon depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-gnome; however:
  Package compiz-gnome is not configured yet.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2.0-cil:
 libgnome2.0-cil depends on libgnome-vfs2.0-cil (>= 2.20.0); however:
  Package libgnome-vfs2.0-cil is not configured yet.
 libgnome2.0-cil depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libgnome2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.16-cil:
 libgtkhtml3.16-cil depends on libgtkhtml3.14-19 (>= 3.18.0); however:
  Package libgtkhtml3.14-19 is not configured yet.
dpkg: error processing libgtkhtml3.16-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit:
 policykit depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing policykit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgweather1:
 libgweather1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgweather1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of brasero:
 brasero depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 brasero depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 brasero depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing brasero (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libexchange-storage1.2-3:
 libexchange-storage1.2-3 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libexchange-storage1.2-3 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libexchange-storage1.2-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-gnome:
 bluez-gnome depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing bluez-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-panel depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-panel depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-panel depends on libgweather1; however:
  Package libgweather1 is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gedit depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtotem-plparser10:
 libtotem-plparser10 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libtotem-plparser10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-window-settings1:
 libgnome-window-settings1 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-window-settings1 (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted

```

---

### Post by handydan918 on 2008-09-10
From looking at the last dpkg output, I think you may be screwed. as good as the Debian package management system is, it is possible to bork it so badly that it can't recover. An interupted config is a great way to do it, especially with a lot of packages. 
If you have important data on that drive, get it backed up to another drive (using a live CD if necessary) and reinstall. It will be a lot quicker than fighting the packager...

---

### Post by Elfy on 2008-09-10
That is possible and I've given up in the past, but before you do that make the folder for it to use. It looks like hal depends on dbus and then the dependencies cascade.

Boot in recovery mode, perhaps not needed but..
Once you have booted - use the little menu to got to a root prompt, then

```
mkdir /var/run/dbus
```

then once that's made run the command again

```
sudo dpkg --configure -a
```

---

### Post by bumanie on 2008-09-10
Would still like to see the output of > df -h / > df -h /homeErrors similar to what you are getting sometimes happen if the filesystem has no room.

---

### Post by Elfy on 2008-09-10
They're in post 7 lol

50% free on / and loads on /home

---

### Post by dfullbrook on 2008-09-10
Thanks forestpixie - I created the directory and re-ran "sudo dpkg -- configure -a" and it all worked! Then I repeated the "sudo apt-get install ubuntu-desktop" and that went through ok as well. So I now have Ubuntu desktop on my server. Thanks again.

---

### Post by Elfy on 2008-09-10
Excellent - perhaps you could mark the thread solved, easier for people searching for remedies.

---

