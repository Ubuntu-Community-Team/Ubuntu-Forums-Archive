---
title: "usb"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by Anoop Jose on 2013-04-05
i am using ubuntu 12.04 LTS. I have removed my pen drive without ejecting . now its not getting detected. what to do? pls help

---

### Post by ibjsb4 on 2013-04-05
Open up "Disk Utility" and mount it :)

---

### Post by Anoop Jose on 2013-04-05
after opening disc utility wat to do?

---

### Post by Anoop Jose on 2013-04-05
in disc utility it doesnt show the affected pen drive

---

### Post by ibjsb4 on 2013-04-05
Ok, log out and back in with the drive plugged in.  Check Nautilus

---

### Post by Anoop Jose on 2013-04-05
i tried. still it doesnt come in disk utility. i even restarted the system. how to check nautilus?

---

### Post by ibjsb4 on 2013-04-05
Usually a pen drive in linux will not care if its not properly unmounted.  Lets see if your computer can see it.  Open a terminal and enter:

```
lsusb
```

---

### Post by Anoop Jose on 2013-04-05
result
Bus 004 Device 002: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 004 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by ibjsb4 on 2013-04-05
I (your computer) don't see it.  Have you tried a different usb port?  Do you have another machine to plug it into?

---

### Post by slickymaster on 2013-04-05
There could be a problem with the drive, or the partition/MBR is messed up.

After you plug it in, enter this in the terminal:
```
dmesg | tail
```
What does it say? Usually from the error message you can tell what the problem is.

---

### Post by Anoop Jose on 2013-04-05
arun@arun:~$ dmesg | tail
[    8.439381] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    8.484689] type=1400 audit(1365173995.561:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=850 comm="apparmor_parser"
[    8.484877] type=1400 audit(1365173995.561:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=851 comm="apparmor_parser"
[    8.485244] type=1400 audit(1365173995.561:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=851 comm="apparmor_parser"
[    8.485598] type=1400 audit(1365173995.561:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=851 comm="apparmor_parser"
[    8.492685] type=1400 audit(1365173995.569:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=854 comm="apparmor_parser"
[   10.010732] r8169 0000:03:00.0: eth1: link up
[   10.010922] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   32.591310] audit_printk_skb: 36 callbacks suppressed
[   32.591314] type=1400 audit(1365174019.665:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1935 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

---

### Post by Anoop Jose on 2013-04-05
i tried in a windows system. it just shows for a moment and goes off

---

### Post by ibjsb4 on 2013-04-05
Sorry, but I am out of ideas. :(

---

### Post by Anoop Jose on 2013-04-05
its alrgt.. thanks buddy

---

### Post by Bashing-om on 2013-04-05
Anoop Jose;
This may be a real problem as the system does not recognize the device. If you know the devices designation (as in sdc ??), there is a procedure to find the process ID and kill that process(fuser).
Maybe find the designation from:
```
mount ##or maybe
sudo blkid
``` with the device plugged in.[INDENT=3]
just a thought

[/INDENT]

---

### Post by slickymaster on 2013-04-05
Sorry, [COLOR=#000000]Anoop Jose, I'm stuck also. 
Can't figure a way out of it. Maybe someone else can devise a solution to solve it out, don give up just now.[/COLOR]

---

### Post by Anoop Jose on 2013-04-05
still it doesnt recognize pen drive

/dev/sda1: UUID="06e0fd13-2624-412f-a7ae-a9db210dfb4e" TYPE="ext4" 
/dev/sda5: LABEL="My Documents" UUID="B6A8B1D2A8B190FB" TYPE="ntfs" 
/dev/sda6: LABEL="Program Files" UUID="D230B73330B71E03" TYPE="ntfs" 
/dev/sda7: LABEL="Movies" UUID="967CBFF87CBFD0EB" TYPE="ntfs" 
/dev/sda8: LABEL="Home" UUID="48D8C46ED8C45C36" TYPE="ntfs" 
/dev/sda9: UUID="3dc5a8b1-88e5-477a-93f4-161624de281e" TYPE="swap"

---

### Post by Bashing-om on 2013-04-06
Anoop Jose;
As the device is not recognized by either operating system, All I can come up with is to see what the utility "testdisk" can come up with.
"testdisk" is available in the ubuntu repository.
[INDENT=4]
Good Luck !

[/INDENT]

---

