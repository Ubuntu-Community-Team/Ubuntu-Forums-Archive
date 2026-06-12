---
title: "Mount Issues and Wireless Issues"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by DigitalJediUK on 2008-10-27
Hi There

I've just made the permanent move to Ubuntu after a few years of lurking. It's brilliant and I don't regret it one bit. However, I am having a few issues. First of all, I am trying to mount a hard drive which I backed all my music up to before I installed Ubuntu. I know this drive was working perfectly fine in Windows, but when I try to mount the drive, I am returned with this error:

Unable to mount location

Can't mount file

I have tried adding a line to /etc/fstab for that drive and mounting that way but it doesn't seem to like it.

Second issue is that sometimes when I boot and my wireless connects to our WEP secured wireless network, Ubuntu locks up. I have to reboot with my wireless unplugged and plug the adapter back in when Ubuntu has booted for it to connect without locking up.

Any help would be appreciated. I am a technical person, so I don't mind how complex the resolution is.

Thanks :)

---

### Post by DigitalJediUK on 2008-10-27
*Bump*

---

### Post by wannadumpwindows on 2008-10-27
Next time, wait at least a few hours to bump your thread. Give people time to find it and help you. If you need help faster, use irc.

---

### Post by DigitalJediUK on 2008-10-27
Apologies. I was just thinking the post might have got lost in amongst all the high volume of new posts coming in.

---

### Post by inkrypted on 2008-10-27
Since you were in Windows i'm gonna guess this is a NTFS drive. Use add/remove to search for ntfs and install ntfs3g and try mounting it with that. Did you add your wireless network through the manager?

---

### Post by DigitalJediUK on 2008-10-27
Yes, it's an NTFS drive. However, when I try to mount with ntfs-3g I am given the following error:

ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type 'ntfs-3g --help' for more information.

Here is what I get from fdisk -l:

```
Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x577d0d04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4795    38515806   83  Linux
/dev/sda2            4796        5005     1686825    5  Extended
/dev/sda5            4796        5005     1686793+  82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce3fca97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4997    40138371    7  HPFS/NTFS

```

And also, yes, I added the wireless network via the packaged network manager (the one that comes with Ubuntu).

---

### Post by DigitalJediUK on 2008-10-27
*Bump*

Apologies in advance if my bumping annoys anyone.

---

### Post by lswest on 2008-10-27
try this:
```
sudo mkdir /media/Music\ Backup/
sudo mount -t ntfs-3g /dev/sdb1 /media/Music\ Backup/
```

If that works, let us know and we'll make it permanent.

If you don't want to mess with terminal commands you can try running "gksudo ntfs-config" (if it's not installed install it with ```
sudo apt-get install ntfs-config
``` to set up the mountpoint and drive with a GUI)

---

### Post by DigitalJediUK on 2008-10-27
Thanks. Unfortunately, I'm still getting the same problem. However, before on ntfs-config the top box which enabled write support was greyed out. I am now able to tick that, but it still doesn't allow me to mount the drive and access my files.

---

### Post by lswest on 2008-10-27
Could you post the exact output of the above specified terminal commands then?

Also, are you sure you safely removed the hardware in Windows before installing Ubuntu?

And about the wireless, what kind of network adaptor is it, and was it automatically detected?

---

### Post by DigitalJediUK on 2008-10-27
I am able to make the directory, however when I try to mount the drive with the command you suggested, I get this message:

```
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

```

The hard drive in question is internal, it is not external, and therefore does not require me (as far as I am aware, If I am wrong please tell me) to safely remove that drive.

Edit: The wireless adapter in question was automatically detected after install. It is a Philips SNU6500 USB wireless adapter.

---

### Post by lswest on 2008-10-27
Ah, I see, I had assumed it was an external drive, you're correct, safely removing it isn't necessary since it is internal.

Can you post the output of the following commands:
```
ls -la /dev/|grep sdb
sudo fdisk -l
```

About the wireless: I have no experience with that adaptor, and as such can't be much help there, sorry.  But output from the following commands could be useful for others:
```
lshw -C network
lsusb
sudo iwlist scan
sudo iwconfig
```

---

### Post by DigitalJediUK on 2008-10-27
Here is the output from the terminal commands you requested.

```
brw-rw----   1 root   disk      8,  16 2008-10-27 14:46 sdb

```

```
Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x577d0d04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4795    38515806   83  Linux
/dev/sda2            4796        5005     1686825    5  Extended
/dev/sda5            4796        5005     1686793+  82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce3fca97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4997    40138371    7  HPFS/NTFS

```

Edit: Output from the other commands
```
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1a:2a:05:42:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.4 multicast=yes wireless=IEEE 802.11b/g

```
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 0471:1237 Philips 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 145f:011a  
Bus 001 Device 004: ID 0b38:0003  
Bus 001 Device 001: ID 0000:0000  

```
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1A:2A:05:79:E9
                    ESSID:"ATF"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=94/100  
                    Extra: Last beacon: 8ms ago
          Cell 02 - Address: 00:02:CF:6E:64:D7
                    ESSID:"ZyXEL_9677ake"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=58/100  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 196ms ago
          Cell 03 - Address: 00:13:64:3B:28:B0
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=41/100  
                    Extra: Last beacon: 32ms ago
          Cell 04 - Address: 62:16:B7:3D:FE:ED
                    ESSID:"WASC-0016415f4ac7-PHILIPS"
                    Protocol:IEEE 802.11bg
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=41/100  
                    Extra: Last beacon: 40ms ago

```
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"ATF"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:2A:05:79:E9   
          Bit Rate=24 Mb/s   
          Encryption key:(Not going to give that out ;))   Security mode:open
          Link Quality=83/100  Signal level=36/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by lswest on 2008-10-27
Are you sure the output of ls -la|grep sdb is complete?  If so, it means that there's no file (link) to the actual partition.  You might be able to mount the drive using /dev/sdb instead of /dev/sdb1 but I'm not sure.  If possible please re-post the commands of the command without the grep (so it would read "ls -la /dev/") just in case.

---

### Post by DigitalJediUK on 2008-10-27
Here is the command without the grep switch

```
crw-rw-rw-   1 root   tty       2,  96 2008-10-27 14:46 ptyv0
crw-rw-rw-   1 root   tty       2,  97 2008-10-27 14:46 ptyv1
crw-rw-rw-   1 root   tty       2,  98 2008-10-27 14:46 ptyv2
crw-rw-rw-   1 root   tty       2,  99 2008-10-27 14:46 ptyv3
crw-rw-rw-   1 root   tty       2, 100 2008-10-27 14:46 ptyv4
crw-rw-rw-   1 root   tty       2, 101 2008-10-27 14:46 ptyv5
crw-rw-rw-   1 root   tty       2, 102 2008-10-27 14:46 ptyv6
crw-rw-rw-   1 root   tty       2, 103 2008-10-27 14:46 ptyv7
crw-rw-rw-   1 root   tty       2, 104 2008-10-27 14:46 ptyv8
crw-rw-rw-   1 root   tty       2, 105 2008-10-27 14:46 ptyv9
crw-rw-rw-   1 root   tty       2, 106 2008-10-27 14:46 ptyva
crw-rw-rw-   1 root   tty       2, 107 2008-10-27 14:46 ptyvb
crw-rw-rw-   1 root   tty       2, 108 2008-10-27 14:46 ptyvc
crw-rw-rw-   1 root   tty       2, 109 2008-10-27 14:46 ptyvd
crw-rw-rw-   1 root   tty       2, 110 2008-10-27 14:46 ptyve
crw-rw-rw-   1 root   tty       2, 111 2008-10-27 14:46 ptyvf
crw-rw-rw-   1 root   tty       2, 112 2008-10-27 14:46 ptyw0
crw-rw-rw-   1 root   tty       2, 113 2008-10-27 14:46 ptyw1
crw-rw-rw-   1 root   tty       2, 114 2008-10-27 14:46 ptyw2
crw-rw-rw-   1 root   tty       2, 115 2008-10-27 14:46 ptyw3
crw-rw-rw-   1 root   tty       2, 116 2008-10-27 14:46 ptyw4
crw-rw-rw-   1 root   tty       2, 117 2008-10-27 14:46 ptyw5
crw-rw-rw-   1 root   tty       2, 118 2008-10-27 14:46 ptyw6
crw-rw-rw-   1 root   tty       2, 119 2008-10-27 14:46 ptyw7
crw-rw-rw-   1 root   tty       2, 120 2008-10-27 14:46 ptyw8
crw-rw-rw-   1 root   tty       2, 121 2008-10-27 14:46 ptyw9
crw-rw-rw-   1 root   tty       2, 122 2008-10-27 14:46 ptywa
crw-rw-rw-   1 root   tty       2, 123 2008-10-27 14:46 ptywb
crw-rw-rw-   1 root   tty       2, 124 2008-10-27 14:46 ptywc
crw-rw-rw-   1 root   tty       2, 125 2008-10-27 14:46 ptywd
crw-rw-rw-   1 root   tty       2, 126 2008-10-27 14:46 ptywe
crw-rw-rw-   1 root   tty       2, 127 2008-10-27 14:46 ptywf
crw-rw-rw-   1 root   tty       2, 128 2008-10-27 14:46 ptyx0
crw-rw-rw-   1 root   tty       2, 129 2008-10-27 14:46 ptyx1
crw-rw-rw-   1 root   tty       2, 130 2008-10-27 14:46 ptyx2
crw-rw-rw-   1 root   tty       2, 131 2008-10-27 14:46 ptyx3
crw-rw-rw-   1 root   tty       2, 132 2008-10-27 14:46 ptyx4
crw-rw-rw-   1 root   tty       2, 133 2008-10-27 14:46 ptyx5
crw-rw-rw-   1 root   tty       2, 134 2008-10-27 14:46 ptyx6
crw-rw-rw-   1 root   tty       2, 135 2008-10-27 14:46 ptyx7
crw-rw-rw-   1 root   tty       2, 136 2008-10-27 14:46 ptyx8
crw-rw-rw-   1 root   tty       2, 137 2008-10-27 14:46 ptyx9
crw-rw-rw-   1 root   tty       2, 138 2008-10-27 14:46 ptyxa
crw-rw-rw-   1 root   tty       2, 139 2008-10-27 14:46 ptyxb
crw-rw-rw-   1 root   tty       2, 140 2008-10-27 14:46 ptyxc
crw-rw-rw-   1 root   tty       2, 141 2008-10-27 14:46 ptyxd
crw-rw-rw-   1 root   tty       2, 142 2008-10-27 14:46 ptyxe
crw-rw-rw-   1 root   tty       2, 143 2008-10-27 14:46 ptyxf
crw-rw-rw-   1 root   tty       2, 144 2008-10-27 14:46 ptyy0
crw-rw-rw-   1 root   tty       2, 145 2008-10-27 14:46 ptyy1
crw-rw-rw-   1 root   tty       2, 146 2008-10-27 14:46 ptyy2
crw-rw-rw-   1 root   tty       2, 147 2008-10-27 14:46 ptyy3
crw-rw-rw-   1 root   tty       2, 148 2008-10-27 14:46 ptyy4
crw-rw-rw-   1 root   tty       2, 149 2008-10-27 14:46 ptyy5
crw-rw-rw-   1 root   tty       2, 150 2008-10-27 14:46 ptyy6
crw-rw-rw-   1 root   tty       2, 151 2008-10-27 14:46 ptyy7
crw-rw-rw-   1 root   tty       2, 152 2008-10-27 14:46 ptyy8
crw-rw-rw-   1 root   tty       2, 153 2008-10-27 14:46 ptyy9
crw-rw-rw-   1 root   tty       2, 154 2008-10-27 14:46 ptyya
crw-rw-rw-   1 root   tty       2, 155 2008-10-27 14:46 ptyyb
crw-rw-rw-   1 root   tty       2, 156 2008-10-27 14:46 ptyyc
crw-rw-rw-   1 root   tty       2, 157 2008-10-27 14:46 ptyyd
crw-rw-rw-   1 root   tty       2, 158 2008-10-27 14:46 ptyye
crw-rw-rw-   1 root   tty       2, 159 2008-10-27 14:46 ptyyf
crw-rw-rw-   1 root   tty       2, 160 2008-10-27 14:46 ptyz0
crw-rw-rw-   1 root   tty       2, 161 2008-10-27 14:46 ptyz1
crw-rw-rw-   1 root   tty       2, 162 2008-10-27 14:46 ptyz2
crw-rw-rw-   1 root   tty       2, 163 2008-10-27 14:46 ptyz3
crw-rw-rw-   1 root   tty       2, 164 2008-10-27 14:46 ptyz4
crw-rw-rw-   1 root   tty       2, 165 2008-10-27 14:46 ptyz5
crw-rw-rw-   1 root   tty       2, 166 2008-10-27 14:46 ptyz6
crw-rw-rw-   1 root   tty       2, 167 2008-10-27 14:46 ptyz7
crw-rw-rw-   1 root   tty       2, 168 2008-10-27 14:46 ptyz8
crw-rw-rw-   1 root   tty       2, 169 2008-10-27 14:46 ptyz9
crw-rw-rw-   1 root   tty       2, 170 2008-10-27 14:46 ptyza
crw-rw-rw-   1 root   tty       2, 171 2008-10-27 14:46 ptyzb
crw-rw-rw-   1 root   tty       2, 172 2008-10-27 14:46 ptyzc
crw-rw-rw-   1 root   tty       2, 173 2008-10-27 14:46 ptyzd
crw-rw-rw-   1 root   tty       2, 174 2008-10-27 14:46 ptyze
crw-rw-rw-   1 root   tty       2, 175 2008-10-27 14:46 ptyzf
brw-rw----   1 root   disk      1,   0 2008-10-27 14:46 ram0
brw-rw----   1 root   disk      1,   1 2008-10-27 14:46 ram1
brw-rw----   1 root   disk      1,  10 2008-10-27 14:46 ram10
brw-rw----   1 root   disk      1,  11 2008-10-27 14:46 ram11
brw-rw----   1 root   disk      1,  12 2008-10-27 14:46 ram12
brw-rw----   1 root   disk      1,  13 2008-10-27 14:46 ram13
brw-rw----   1 root   disk      1,  14 2008-10-27 14:46 ram14
brw-rw----   1 root   disk      1,  15 2008-10-27 14:46 ram15
brw-rw----   1 root   disk      1,   2 2008-10-27 14:46 ram2
brw-rw----   1 root   disk      1,   3 2008-10-27 14:46 ram3
brw-rw----   1 root   disk      1,   4 2008-10-27 14:46 ram4
brw-rw----   1 root   disk      1,   5 2008-10-27 14:46 ram5
brw-rw----   1 root   disk      1,   6 2008-10-27 14:46 ram6
brw-rw----   1 root   disk      1,   7 2008-10-27 14:46 ram7
brw-rw----   1 root   disk      1,   8 2008-10-27 14:46 ram8
brw-rw----   1 root   disk      1,   9 2008-10-27 14:46 ram9
crw-rw-rw-   1 root   root      1,   8 2008-10-27 14:46 random
crw-rw----   1 root   audio    10, 135 2008-10-27 14:46 rtc
brw-rw----+  1 root   cdrom    11,   0 2008-10-27 14:46 scd0
brw-rw----+  1 root   cdrom    11,   1 2008-10-27 14:46 scd1
brw-rw----   1 root   disk      8,   0 2008-10-27 14:46 sda
brw-rw----   1 root   disk      8,   1 2008-10-27 14:46 sda1
brw-rw----   1 root   disk      8,   2 2008-10-27 14:46 sda2
brw-rw----   1 root   disk      8,   5 2008-10-27 14:46 sda5
brw-rw----   1 root   disk      8,  16 2008-10-27 14:46 sdb
cr--------   1 root   root      8,  17 2008-10-27 18:24 sdb1
crw-rw----+  1 root   audio    14,   1 2008-10-27 14:46 sequencer
crw-rw----+  1 root   audio    14,   8 2008-10-27 14:46 sequencer2
crw-rw----   1 root   disk     21,   0 2008-10-27 14:46 sg0
crw-rw----   1 root   disk     21,   1 2008-10-27 14:46 sg1
crw-rw----   1 root   cdrom    21,   2 2008-10-27 14:46 sg2
crw-rw----   1 root   cdrom    21,   3 2008-10-27 14:46 sg3
drwxrwxrwt   2 root   root          80 2008-10-27 18:28 shm
crw-rw----   1 root   root     10, 231 2008-10-27 14:46 snapshot
drwxr-xr-x   2 root   root         220 2008-10-27 14:46 snd
lrwxrwxrwx   1 root   root          24 2008-10-27 14:46 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx   1 root   root           4 2008-10-27 14:46 sr0 -> scd0
lrwxrwxrwx   1 root   root           4 2008-10-27 14:46 sr1 -> scd1
drwxr-xr-x   3 root   root          60 2008-10-27 14:46 .static
lrwxrwxrwx   1 root   root          15 2008-10-27 14:46 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root   root          15 2008-10-27 14:46 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root   root          15 2008-10-27 14:46 stdout -> /proc/self/fd/1
crw-rw-rw-   1 root   dialout   5,   0 2008-10-27 18:15 tty
crw-rw----   1 root   root      4,   0 2008-10-27 14:46 tty0
crw-------   1 root   root      4,   1 2008-10-27 14:46 tty1
crw-rw----   1 root   dialout   4,  10 2008-10-27 14:46 tty10
crw-rw----   1 root   dialout   4,  11 2008-10-27 14:46 tty11
crw-rw----   1 root   dialout   4,  12 2008-10-27 14:46 tty12
crw-rw----   1 root   dialout   4,  13 2008-10-27 14:46 tty13
crw-rw----   1 root   dialout   4,  14 2008-10-27 14:46 tty14
crw-rw----   1 root   dialout   4,  15 2008-10-27 14:46 tty15
crw-rw----   1 root   dialout   4,  16 2008-10-27 14:46 tty16
crw-rw----   1 root   dialout   4,  17 2008-10-27 14:46 tty17
crw-rw----   1 root   dialout   4,  18 2008-10-27 14:46 tty18
crw-rw----   1 root   dialout   4,  19 2008-10-27 14:46 tty19
crw-------   1 root   root      4,   2 2008-10-27 14:46 tty2
crw-rw----   1 root   dialout   4,  20 2008-10-27 14:46 tty20
crw-rw----   1 root   dialout   4,  21 2008-10-27 14:46 tty21
crw-rw----   1 root   dialout   4,  22 2008-10-27 14:46 tty22
crw-rw----   1 root   dialout   4,  23 2008-10-27 14:46 tty23
crw-rw----   1 root   dialout   4,  24 2008-10-27 14:46 tty24
crw-rw----   1 root   dialout   4,  25 2008-10-27 14:46 tty25
crw-rw----   1 root   dialout   4,  26 2008-10-27 14:46 tty26
crw-rw----   1 root   dialout   4,  27 2008-10-27 14:46 tty27
crw-rw----   1 root   dialout   4,  28 2008-10-27 14:46 tty28
crw-rw----   1 root   dialout   4,  29 2008-10-27 14:46 tty29
crw-------   1 root   root      4,   3 2008-10-27 14:46 tty3
crw-rw----   1 root   dialout   4,  30 2008-10-27 14:46 tty30
crw-rw----   1 root   dialout   4,  31 2008-10-27 14:46 tty31
crw-rw----   1 root   dialout   4,  32 2008-10-27 14:46 tty32
crw-rw----   1 root   dialout   4,  33 2008-10-27 14:46 tty33
crw-rw----   1 root   dialout   4,  34 2008-10-27 14:46 tty34
crw-rw----   1 root   dialout   4,  35 2008-10-27 14:46 tty35
crw-rw----   1 root   dialout   4,  36 2008-10-27 14:46 tty36
crw-rw----   1 root   dialout   4,  37 2008-10-27 14:46 tty37
crw-rw----   1 root   dialout   4,  38 2008-10-27 14:46 tty38
crw-rw----   1 root   dialout   4,  39 2008-10-27 14:46 tty39
crw-------   1 root   root      4,   4 2008-10-27 14:46 tty4
crw-rw----   1 root   dialout   4,  40 2008-10-27 14:46 tty40
crw-rw----   1 root   dialout   4,  41 2008-10-27 14:46 tty41
crw-rw----   1 root   dialout   4,  42 2008-10-27 14:46 tty42
crw-rw----   1 root   dialout   4,  43 2008-10-27 14:46 tty43
crw-rw----   1 root   dialout   4,  44 2008-10-27 14:46 tty44
crw-rw----   1 root   dialout   4,  45 2008-10-27 14:46 tty45
crw-rw----   1 root   dialout   4,  46 2008-10-27 14:46 tty46
crw-rw----   1 root   dialout   4,  47 2008-10-27 14:46 tty47
crw-rw----   1 root   dialout   4,  48 2008-10-27 14:46 tty48
crw-rw----   1 root   dialout   4,  49 2008-10-27 14:46 tty49
crw-------   1 root   root      4,   5 2008-10-27 14:46 tty5
crw-rw----   1 root   dialout   4,  50 2008-10-27 14:46 tty50
crw-rw----   1 root   dialout   4,  51 2008-10-27 14:46 tty51
crw-rw----   1 root   dialout   4,  52 2008-10-27 14:46 tty52
crw-rw----   1 root   dialout   4,  53 2008-10-27 14:46 tty53
crw-rw----   1 root   dialout   4,  54 2008-10-27 14:46 tty54
crw-rw----   1 root   dialout   4,  55 2008-10-27 14:46 tty55
crw-rw----   1 root   dialout   4,  56 2008-10-27 14:46 tty56
crw-rw----   1 root   dialout   4,  57 2008-10-27 14:46 tty57
crw-rw----   1 root   dialout   4,  58 2008-10-27 14:46 tty58
crw-rw----   1 root   dialout   4,  59 2008-10-27 14:46 tty59
crw-------   1 root   root      4,   6 2008-10-27 14:46 tty6
crw-rw----   1 root   dialout   4,  60 2008-10-27 14:46 tty60
crw-rw----   1 root   dialout   4,  61 2008-10-27 14:46 tty61
crw-rw----   1 root   dialout   4,  62 2008-10-27 14:46 tty62
crw-rw----   1 root   dialout   4,  63 2008-10-27 14:46 tty63
crw-rw----   1 root   root      4,   7 2008-10-27 14:46 tty7
crw-rw----   1 root   dialout   4,   8 2008-10-27 14:46 tty8
crw-rw----   1 root   dialout   4,   9 2008-10-27 14:46 tty9
crw-rw-rw-   1 root   tty       3, 176 2008-10-27 14:46 ttya0
crw-rw-rw-   1 root   tty       3, 177 2008-10-27 14:46 ttya1
crw-rw-rw-   1 root   tty       3, 178 2008-10-27 14:46 ttya2
crw-rw-rw-   1 root   tty       3, 179 2008-10-27 14:46 ttya3
crw-rw-rw-   1 root   tty       3, 180 2008-10-27 14:46 ttya4
crw-rw-rw-   1 root   tty       3, 181 2008-10-27 14:46 ttya5
crw-rw-rw-   1 root   tty       3, 182 2008-10-27 14:46 ttya6
crw-rw-rw-   1 root   tty       3, 183 2008-10-27 14:46 ttya7
crw-rw-rw-   1 root   tty       3, 184 2008-10-27 14:46 ttya8
crw-rw-rw-   1 root   tty       3, 185 2008-10-27 14:46 ttya9
crw-rw-rw-   1 root   tty       3, 186 2008-10-27 14:46 ttyaa
crw-rw-rw-   1 root   tty       3, 187 2008-10-27 14:46 ttyab
crw-rw-rw-   1 root   tty       3, 188 2008-10-27 14:46 ttyac
crw-rw-rw-   1 root   tty       3, 189 2008-10-27 14:46 ttyad
crw-rw-rw-   1 root   tty       3, 190 2008-10-27 14:46 ttyae
crw-rw-rw-   1 root   tty       3, 191 2008-10-27 14:46 ttyaf
crw-rw-rw-   1 root   tty       3, 192 2008-10-27 14:46 ttyb0
crw-rw-rw-   1 root   tty       3, 193 2008-10-27 14:46 ttyb1
crw-rw-rw-   1 root   tty       3, 194 2008-10-27 14:46 ttyb2
crw-rw-rw-   1 root   tty       3, 195 2008-10-27 14:46 ttyb3
crw-rw-rw-   1 root   tty       3, 196 2008-10-27 14:46 ttyb4
crw-rw-rw-   1 root   tty       3, 197 2008-10-27 14:46 ttyb5
crw-rw-rw-   1 root   tty       3, 198 2008-10-27 14:46 ttyb6
crw-rw-rw-   1 root   tty       3, 199 2008-10-27 14:46 ttyb7
crw-rw-rw-   1 root   tty       3, 200 2008-10-27 14:46 ttyb8
crw-rw-rw-   1 root   tty       3, 201 2008-10-27 14:46 ttyb9
crw-rw-rw-   1 root   tty       3, 202 2008-10-27 14:46 ttyba
crw-rw-rw-   1 root   tty       3, 203 2008-10-27 14:46 ttybb
crw-rw-rw-   1 root   tty       3, 204 2008-10-27 14:46 ttybc
crw-rw-rw-   1 root   tty       3, 205 2008-10-27 14:46 ttybd
crw-rw-rw-   1 root   tty       3, 206 2008-10-27 14:46 ttybe
crw-rw-rw-   1 root   tty       3, 207 2008-10-27 14:46 ttybf
crw-rw-rw-   1 root   tty       3, 208 2008-10-27 14:46 ttyc0
crw-rw-rw-   1 root   tty       3, 209 2008-10-27 14:46 ttyc1
crw-rw-rw-   1 root   tty       3, 210 2008-10-27 14:46 ttyc2
crw-rw-rw-   1 root   tty       3, 211 2008-10-27 14:46 ttyc3
crw-rw-rw-   1 root   tty       3, 212 2008-10-27 14:46 ttyc4
crw-rw-rw-   1 root   tty       3, 213 2008-10-27 14:46 ttyc5
crw-rw-rw-   1 root   tty       3, 214 2008-10-27 14:46 ttyc6
crw-rw-rw-   1 root   tty       3, 215 2008-10-27 14:46 ttyc7
crw-rw-rw-   1 root   tty       3, 216 2008-10-27 14:46 ttyc8
crw-rw-rw-   1 root   tty       3, 217 2008-10-27 14:46 ttyc9
crw-rw-rw-   1 root   tty       3, 218 2008-10-27 14:46 ttyca
crw-rw-rw-   1 root   tty       3, 219 2008-10-27 14:46 ttycb
crw-rw-rw-   1 root   tty       3, 220 2008-10-27 14:46 ttycc
crw-rw-rw-   1 root   tty       3, 221 2008-10-27 14:46 ttycd
crw-rw-rw-   1 root   tty       3, 222 2008-10-27 14:46 ttyce
crw-rw-rw-   1 root   tty       3, 223 2008-10-27 14:46 ttycf
crw-rw-rw-   1 root   tty       3, 224 2008-10-27 14:46 ttyd0
crw-rw-rw-   1 root   tty       3, 225 2008-10-27 14:46 ttyd1
crw-rw-rw-   1 root   tty       3, 226 2008-10-27 14:46 ttyd2
crw-rw-rw-   1 root   tty       3, 227 2008-10-27 14:46 ttyd3
crw-rw-rw-   1 root   tty       3, 228 2008-10-27 14:46 ttyd4
crw-rw-rw-   1 root   tty       3, 229 2008-10-27 14:46 ttyd5
crw-rw-rw-   1 root   tty       3, 230 2008-10-27 14:46 ttyd6
crw-rw-rw-   1 root   tty       3, 231 2008-10-27 14:46 ttyd7
crw-rw-rw-   1 root   tty       3, 232 2008-10-27 14:46 ttyd8
crw-rw-rw-   1 root   tty       3, 233 2008-10-27 14:46 ttyd9
crw-rw-rw-   1 root   tty       3, 234 2008-10-27 14:46 ttyda
crw-rw-rw-   1 root   tty       3, 235 2008-10-27 14:46 ttydb
crw-rw-rw-   1 root   tty       3, 236 2008-10-27 14:46 ttydc
crw-rw-rw-   1 root   tty       3, 237 2008-10-27 14:46 ttydd
crw-rw-rw-   1 root   tty       3, 238 2008-10-27 14:46 ttyde
crw-rw-rw-   1 root   tty       3, 239 2008-10-27 14:46 ttydf
crw-rw-rw-   1 root   tty       3, 240 2008-10-27 14:46 ttye0
crw-rw-rw-   1 root   tty       3, 241 2008-10-27 14:46 ttye1
crw-rw-rw-   1 root   tty       3, 242 2008-10-27 14:46 ttye2
crw-rw-rw-   1 root   tty       3, 243 2008-10-27 14:46 ttye3
crw-rw-rw-   1 root   tty       3, 244 2008-10-27 14:46 ttye4
crw-rw-rw-   1 root   tty       3, 245 2008-10-27 14:46 ttye5
crw-rw-rw-   1 root   tty       3, 246 2008-10-27 14:46 ttye6
crw-rw-rw-   1 root   tty       3, 247 2008-10-27 14:46 ttye7
crw-rw-rw-   1 root   tty       3, 248 2008-10-27 14:46 ttye8
crw-rw-rw-   1 root   tty       3, 249 2008-10-27 14:46 ttye9
crw-rw-rw-   1 root   tty       3, 250 2008-10-27 14:46 ttyea
crw-rw-rw-   1 root   tty       3, 251 2008-10-27 14:46 ttyeb
crw-rw-rw-   1 root   tty       3, 252 2008-10-27 14:46 ttyec
crw-rw-rw-   1 root   tty       3, 253 2008-10-27 14:46 ttyed
crw-rw-rw-   1 root   tty       3, 254 2008-10-27 14:46 ttyee
crw-rw-rw-   1 root   tty       3, 255 2008-10-27 14:46 ttyef
crw-rw-rw-   1 root   tty       3,   0 2008-10-27 14:46 ttyp0
crw-rw-rw-   1 root   tty       3,   1 2008-10-27 14:46 ttyp1
crw-rw-rw-   1 root   tty       3,   2 2008-10-27 14:46 ttyp2
crw-rw-rw-   1 root   tty       3,   3 2008-10-27 14:46 ttyp3
crw-rw-rw-   1 root   tty       3,   4 2008-10-27 14:46 ttyp4
crw-rw-rw-   1 root   tty       3,   5 2008-10-27 14:46 ttyp5
crw-rw-rw-   1 root   tty       3,   6 2008-10-27 14:46 ttyp6
crw-rw-rw-   1 root   tty       3,   7 2008-10-27 14:46 ttyp7
crw-rw-rw-   1 root   tty       3,   8 2008-10-27 14:46 ttyp8
crw-rw-rw-   1 root   tty       3,   9 2008-10-27 14:46 ttyp9
crw-rw-rw-   1 root   tty       3,  10 2008-10-27 14:46 ttypa
crw-rw-rw-   1 root   tty       3,  11 2008-10-27 14:46 ttypb
crw-rw-rw-   1 root   tty       3,  12 2008-10-27 14:46 ttypc
crw-rw-rw-   1 root   tty       3,  13 2008-10-27 14:46 ttypd
crw-rw-rw-   1 root   tty       3,  14 2008-10-27 14:46 ttype
crw-rw-rw-   1 root   tty       3,  15 2008-10-27 14:46 ttypf
crw-rw-rw-   1 root   tty       3,  16 2008-10-27 14:46 ttyq0
crw-rw-rw-   1 root   tty       3,  17 2008-10-27 14:46 ttyq1
crw-rw-rw-   1 root   tty       3,  18 2008-10-27 14:46 ttyq2
crw-rw-rw-   1 root   tty       3,  19 2008-10-27 14:46 ttyq3
crw-rw-rw-   1 root   tty       3,  20 2008-10-27 14:46 ttyq4
crw-rw-rw-   1 root   tty       3,  21 2008-10-27 14:46 ttyq5
crw-rw-rw-   1 root   tty       3,  22 2008-10-27 14:46 ttyq6
crw-rw-rw-   1 root   tty       3,  23 2008-10-27 14:46 ttyq7
crw-rw-rw-   1 root   tty       3,  24 2008-10-27 14:46 ttyq8
crw-rw-rw-   1 root   tty       3,  25 2008-10-27 14:46 ttyq9
crw-rw-rw-   1 root   tty       3,  26 2008-10-27 14:46 ttyqa
crw-rw-rw-   1 root   tty       3,  27 2008-10-27 14:46 ttyqb
crw-rw-rw-   1 root   tty       3,  28 2008-10-27 14:46 ttyqc
crw-rw-rw-   1 root   tty       3,  29 2008-10-27 14:46 ttyqd
crw-rw-rw-   1 root   tty       3,  30 2008-10-27 14:46 ttyqe
crw-rw-rw-   1 root   tty       3,  31 2008-10-27 14:46 ttyqf
crw-rw-rw-   1 root   tty       3,  32 2008-10-27 14:46 ttyr0
crw-rw-rw-   1 root   tty       3,  33 2008-10-27 14:46 ttyr1
crw-rw-rw-   1 root   tty       3,  34 2008-10-27 14:46 ttyr2
crw-rw-rw-   1 root   tty       3,  35 2008-10-27 14:46 ttyr3
crw-rw-rw-   1 root   tty       3,  36 2008-10-27 14:46 ttyr4
crw-rw-rw-   1 root   tty       3,  37 2008-10-27 14:46 ttyr5
crw-rw-rw-   1 root   tty       3,  38 2008-10-27 14:46 ttyr6
crw-rw-rw-   1 root   tty       3,  39 2008-10-27 14:46 ttyr7
crw-rw-rw-   1 root   tty       3,  40 2008-10-27 14:46 ttyr8
crw-rw-rw-   1 root   tty       3,  41 2008-10-27 14:46 ttyr9
crw-rw-rw-   1 root   tty       3,  42 2008-10-27 14:46 ttyra
crw-rw-rw-   1 root   tty       3,  43 2008-10-27 14:46 ttyrb
crw-rw-rw-   1 root   tty       3,  44 2008-10-27 14:46 ttyrc
crw-rw-rw-   1 root   tty       3,  45 2008-10-27 14:46 ttyrd
crw-rw-rw-   1 root   tty       3,  46 2008-10-27 14:46 ttyre
crw-rw-rw-   1 root   tty       3,  47 2008-10-27 14:46 ttyrf
crw-rw-rw-   1 root   tty       3,  48 2008-10-27 14:46 ttys0
crw-rw----   1 root   dialout   4,  64 2008-10-27 14:46 ttyS0
crw-rw-rw-   1 root   tty       3,  49 2008-10-27 14:46 ttys1
crw-rw----   1 root   dialout   4,  65 2008-10-27 14:46 ttyS1
crw-rw-rw-   1 root   tty       3,  50 2008-10-27 14:46 ttys2
crw-rw----   1 root   dialout   4,  66 2008-10-27 14:46 ttyS2
crw-rw-rw-   1 root   tty       3,  51 2008-10-27 14:46 ttys3
crw-rw----   1 root   dialout   4,  67 2008-10-27 14:46 ttyS3
crw-rw-rw-   1 root   tty       3,  52 2008-10-27 14:46 ttys4
crw-rw-rw-   1 root   tty       3,  53 2008-10-27 14:46 ttys5
crw-rw-rw-   1 root   tty       3,  54 2008-10-27 14:46 ttys6
crw-rw-rw-   1 root   tty       3,  55 2008-10-27 14:46 ttys7
crw-rw-rw-   1 root   tty       3,  56 2008-10-27 14:46 ttys8
crw-rw-rw-   1 root   tty       3,  57 2008-10-27 14:46 ttys9
crw-rw-rw-   1 root   tty       3,  58 2008-10-27 14:46 ttysa
crw-rw-rw-   1 root   tty       3,  59 2008-10-27 14:46 ttysb
crw-rw-rw-   1 root   tty       3,  60 2008-10-27 14:46 ttysc
crw-rw-rw-   1 root   tty       3,  61 2008-10-27 14:46 ttysd
crw-rw-rw-   1 root   tty       3,  62 2008-10-27 14:46 ttyse
crw-rw-rw-   1 root   tty       3,  63 2008-10-27 14:46 ttysf
crw-rw-rw-   1 root   tty       3,  64 2008-10-27 14:46 ttyt0
crw-rw-rw-   1 root   tty       3,  65 2008-10-27 14:46 ttyt1
crw-rw-rw-   1 root   tty       3,  66 2008-10-27 14:46 ttyt2
crw-rw-rw-   1 root   tty       3,  67 2008-10-27 14:46 ttyt3
crw-rw-rw-   1 root   tty       3,  68 2008-10-27 14:46 ttyt4
crw-rw-rw-   1 root   tty       3,  69 2008-10-27 14:46 ttyt5
crw-rw-rw-   1 root   tty       3,  70 2008-10-27 14:46 ttyt6
crw-rw-rw-   1 root   tty       3,  71 2008-10-27 14:46 ttyt7
crw-rw-rw-   1 root   tty       3,  72 2008-10-27 14:46 ttyt8
crw-rw-rw-   1 root   tty       3,  73 2008-10-27 14:46 ttyt9
crw-rw-rw-   1 root   tty       3,  74 2008-10-27 14:46 ttyta
crw-rw-rw-   1 root   tty       3,  75 2008-10-27 14:46 ttytb
crw-rw-rw-   1 root   tty       3,  76 2008-10-27 14:46 ttytc
crw-rw-rw-   1 root   tty       3,  77 2008-10-27 14:46 ttytd
crw-rw-rw-   1 root   tty       3,  78 2008-10-27 14:46 ttyte
crw-rw-rw-   1 root   tty       3,  79 2008-10-27 14:46 ttytf
crw-rw-rw-   1 root   tty       3,  80 2008-10-27 14:46 ttyu0
crw-rw-rw-   1 root   tty       3,  81 2008-10-27 14:46 ttyu1
crw-rw-rw-   1 root   tty       3,  82 2008-10-27 14:46 ttyu2
crw-rw-rw-   1 root   tty       3,  83 2008-10-27 14:46 ttyu3
crw-rw-rw-   1 root   tty       3,  84 2008-10-27 14:46 ttyu4
crw-rw-rw-   1 root   tty       3,  85 2008-10-27 14:46 ttyu5
crw-rw-rw-   1 root   tty       3,  86 2008-10-27 14:46 ttyu6
crw-rw-rw-   1 root   tty       3,  87 2008-10-27 14:46 ttyu7
crw-rw-rw-   1 root   tty       3,  88 2008-10-27 14:46 ttyu8
crw-rw-rw-   1 root   tty       3,  89 2008-10-27 14:46 ttyu9
crw-rw-rw-   1 root   tty       3,  90 2008-10-27 14:46 ttyua
crw-rw-rw-   1 root   tty       3,  91 2008-10-27 14:46 ttyub
crw-rw-rw-   1 root   tty       3,  92 2008-10-27 14:46 ttyuc
crw-rw-rw-   1 root   tty       3,  93 2008-10-27 14:46 ttyud
crw-rw-rw-   1 root   tty       3,  94 2008-10-27 14:46 ttyue
crw-rw-rw-   1 root   tty       3,  95 2008-10-27 14:46 ttyuf
crw-rw-rw-   1 root   tty       3,  96 2008-10-27 14:46 ttyv0
crw-rw-rw-   1 root   tty       3,  97 2008-10-27 14:46 ttyv1
crw-rw-rw-   1 root   tty       3,  98 2008-10-27 14:46 ttyv2
crw-rw-rw-   1 root   tty       3,  99 2008-10-27 14:46 ttyv3
crw-rw-rw-   1 root   tty       3, 100 2008-10-27 14:46 ttyv4
crw-rw-rw-   1 root   tty       3, 101 2008-10-27 14:46 ttyv5
crw-rw-rw-   1 root   tty       3, 102 2008-10-27 14:46 ttyv6
crw-rw-rw-   1 root   tty       3, 103 2008-10-27 14:46 ttyv7
crw-rw-rw-   1 root   tty       3, 104 2008-10-27 14:46 ttyv8
crw-rw-rw-   1 root   tty       3, 105 2008-10-27 14:46 ttyv9
crw-rw-rw-   1 root   tty       3, 106 2008-10-27 14:46 ttyva
crw-rw-rw-   1 root   tty       3, 107 2008-10-27 14:46 ttyvb
crw-rw-rw-   1 root   tty       3, 108 2008-10-27 14:46 ttyvc
crw-rw-rw-   1 root   tty       3, 109 2008-10-27 14:46 ttyvd
crw-rw-rw-   1 root   tty       3, 110 2008-10-27 14:46 ttyve
crw-rw-rw-   1 root   tty       3, 111 2008-10-27 14:46 ttyvf
crw-rw-rw-   1 root   tty       3, 112 2008-10-27 14:46 ttyw0
crw-rw-rw-   1 root   tty       3, 113 2008-10-27 14:46 ttyw1
crw-rw-rw-   1 root   tty       3, 114 2008-10-27 14:46 ttyw2
crw-rw-rw-   1 root   tty       3, 115 2008-10-27 14:46 ttyw3
crw-rw-rw-   1 root   tty       3, 116 2008-10-27 14:46 ttyw4
crw-rw-rw-   1 root   tty       3, 117 2008-10-27 14:46 ttyw5
crw-rw-rw-   1 root   tty       3, 118 2008-10-27 14:46 ttyw6
crw-rw-rw-   1 root   tty       3, 119 2008-10-27 14:46 ttyw7
crw-rw-rw-   1 root   tty       3, 120 2008-10-27 14:46 ttyw8
crw-rw-rw-   1 root   tty       3, 121 2008-10-27 14:46 ttyw9
crw-rw-rw-   1 root   tty       3, 122 2008-10-27 14:46 ttywa
crw-rw-rw-   1 root   tty       3, 123 2008-10-27 14:46 ttywb
crw-rw-rw-   1 root   tty       3, 124 2008-10-27 14:46 ttywc
crw-rw-rw-   1 root   tty       3, 125 2008-10-27 14:46 ttywd
crw-rw-rw-   1 root   tty       3, 126 2008-10-27 14:46 ttywe
crw-rw-rw-   1 root   tty       3, 127 2008-10-27 14:46 ttywf
crw-rw-rw-   1 root   tty       3, 128 2008-10-27 14:46 ttyx0
crw-rw-rw-   1 root   tty       3, 129 2008-10-27 14:46 ttyx1
crw-rw-rw-   1 root   tty       3, 130 2008-10-27 14:46 ttyx2
crw-rw-rw-   1 root   tty       3, 131 2008-10-27 14:46 ttyx3
crw-rw-rw-   1 root   tty       3, 132 2008-10-27 14:46 ttyx4
crw-rw-rw-   1 root   tty       3, 133 2008-10-27 14:46 ttyx5
crw-rw-rw-   1 root   tty       3, 134 2008-10-27 14:46 ttyx6
crw-rw-rw-   1 root   tty       3, 135 2008-10-27 14:46 ttyx7
crw-rw-rw-   1 root   tty       3, 136 2008-10-27 14:46 ttyx8
crw-rw-rw-   1 root   tty       3, 137 2008-10-27 14:46 ttyx9
crw-rw-rw-   1 root   tty       3, 138 2008-10-27 14:46 ttyxa
crw-rw-rw-   1 root   tty       3, 139 2008-10-27 14:46 ttyxb
crw-rw-rw-   1 root   tty       3, 140 2008-10-27 14:46 ttyxc
crw-rw-rw-   1 root   tty       3, 141 2008-10-27 14:46 ttyxd
crw-rw-rw-   1 root   tty       3, 142 2008-10-27 14:46 ttyxe
crw-rw-rw-   1 root   tty       3, 143 2008-10-27 14:46 ttyxf
crw-rw-rw-   1 root   tty       3, 144 2008-10-27 14:46 ttyy0
crw-rw-rw-   1 root   tty       3, 145 2008-10-27 14:46 ttyy1
crw-rw-rw-   1 root   tty       3, 146 2008-10-27 14:46 ttyy2
crw-rw-rw-   1 root   tty       3, 147 2008-10-27 14:46 ttyy3
crw-rw-rw-   1 root   tty       3, 148 2008-10-27 14:46 ttyy4
crw-rw-rw-   1 root   tty       3, 149 2008-10-27 14:46 ttyy5
crw-rw-rw-   1 root   tty       3, 150 2008-10-27 14:46 ttyy6
crw-rw-rw-   1 root   tty       3, 151 2008-10-27 14:46 ttyy7
crw-rw-rw-   1 root   tty       3, 152 2008-10-27 14:46 ttyy8
crw-rw-rw-   1 root   tty       3, 153 2008-10-27 14:46 ttyy9
crw-rw-rw-   1 root   tty       3, 154 2008-10-27 14:46 ttyya
crw-rw-rw-   1 root   tty       3, 155 2008-10-27 14:46 ttyyb
crw-rw-rw-   1 root   tty       3, 156 2008-10-27 14:46 ttyyc
crw-rw-rw-   1 root   tty       3, 157 2008-10-27 14:46 ttyyd
crw-rw-rw-   1 root   tty       3, 158 2008-10-27 14:46 ttyye
crw-rw-rw-   1 root   tty       3, 159 2008-10-27 14:46 ttyyf
crw-rw-rw-   1 root   tty       3, 160 2008-10-27 14:46 ttyz0
crw-rw-rw-   1 root   tty       3, 161 2008-10-27 14:46 ttyz1
crw-rw-rw-   1 root   tty       3, 162 2008-10-27 14:46 ttyz2
crw-rw-rw-   1 root   tty       3, 163 2008-10-27 14:46 ttyz3
crw-rw-rw-   1 root   tty       3, 164 2008-10-27 14:46 ttyz4
crw-rw-rw-   1 root   tty       3, 165 2008-10-27 14:46 ttyz5
crw-rw-rw-   1 root   tty       3, 166 2008-10-27 14:46 ttyz6
crw-rw-rw-   1 root   tty       3, 167 2008-10-27 14:46 ttyz7
crw-rw-rw-   1 root   tty       3, 168 2008-10-27 14:46 ttyz8
crw-rw-rw-   1 root   tty       3, 169 2008-10-27 14:46 ttyz9
crw-rw-rw-   1 root   tty       3, 170 2008-10-27 14:46 ttyza
crw-rw-rw-   1 root   tty       3, 171 2008-10-27 14:46 ttyzb
crw-rw-rw-   1 root   tty       3, 172 2008-10-27 14:46 ttyzc
crw-rw-rw-   1 root   tty       3, 173 2008-10-27 14:46 ttyzd
crw-rw-rw-   1 root   tty       3, 174 2008-10-27 14:46 ttyze
crw-rw-rw-   1 root   tty       3, 175 2008-10-27 14:46 ttyzf
drwxr-xr-x   6 root   root         140 2008-10-27 15:14 .udev
crw-rw-rw-   1 root   root      1,   9 2008-10-27 14:46 urandom
drwxr-xr-x   2 root   root          60 2008-10-27 14:46 usb
crw-rw----   1 root   root    254,   0 2008-10-27 14:46 usbdev1.1_ep00
crw-rw----   1 root   root    254,   1 2008-10-27 14:46 usbdev1.1_ep81
crw-rw----   1 root   root    254,  15 2008-10-27 14:46 usbdev1.4_ep00
crw-rw----   1 root   root    254,  16 2008-10-27 14:46 usbdev1.4_ep81
crw-rw----   1 root   root    254,  17 2008-10-27 14:46 usbdev1.4_ep82
crw-rw----   1 root   root    254,  18 2008-10-27 14:46 usbdev1.5_ep00
crw-rw----   1 root   root    254,  19 2008-10-27 14:46 usbdev1.5_ep81
crw-rw----   1 root   root    254,   2 2008-10-27 14:46 usbdev2.1_ep00
crw-rw----   1 root   root    254,   3 2008-10-27 14:46 usbdev2.1_ep81
crw-rw----   1 root   root    254,   4 2008-10-27 14:46 usbdev3.1_ep00
crw-rw----   1 root   root    254,   5 2008-10-27 14:46 usbdev3.1_ep81
crw-rw----   1 root   root    254,  11 2008-10-27 14:46 usbdev4.1_ep00
crw-rw----   1 root   root    254,  12 2008-10-27 14:46 usbdev4.1_ep81
crw-rw----   1 root   root    254,   7 2008-10-27 14:46 usbdev4.2_ep00
crw-rw----   1 root   root    254,   8 2008-10-27 14:46 usbdev4.2_ep01
crw-rw----   1 root   root    254,  14 2008-10-27 14:46 usbdev4.2_ep04
crw-rw----   1 root   root    254,   9 2008-10-27 14:46 usbdev4.2_ep82
crw-rw----   1 root   root    254,  10 2008-10-27 14:46 usbdev4.2_ep83
crw-rw----   1 root   root    254,   7 2008-10-27 14:48 usbdev4.5_ep00
crw-rw----   1 root   root    254,   8 2008-10-27 14:48 usbdev4.5_ep01
crw-rw----   1 root   root    254,  14 2008-10-27 14:48 usbdev4.5_ep04
crw-rw----   1 root   root    254,   9 2008-10-27 14:48 usbdev4.5_ep82
crw-rw----   1 root   root    254,  10 2008-10-27 14:48 usbdev4.5_ep83
crw-rw----   1 root   root    254,  13 2008-10-27 14:46 usbdev5.1_ep00
crw-rw----   1 root   root    254,   6 2008-10-27 14:46 usbdev5.1_ep81
crw-rw----   1 root   root      7,   0 2008-10-27 14:46 vcs
crw-rw----   1 root   root      7,   1 2008-10-27 14:46 vcs1
crw-rw----   1 root   root      7,   2 2008-10-27 14:46 vcs2
crw-rw----   1 root   root      7,   3 2008-10-27 14:46 vcs3
crw-rw----   1 root   root      7,   4 2008-10-27 14:46 vcs4
crw-rw----   1 root   root      7,   5 2008-10-27 14:46 vcs5
crw-rw----   1 root   root      7,   6 2008-10-27 14:46 vcs6
crw-rw----   1 root   root      7,   7 2008-10-27 14:46 vcs7
crw-rw----   1 root   root      7,   8 2008-10-27 14:46 vcs8
crw-rw----   1 root   root      7, 128 2008-10-27 14:46 vcsa
crw-rw----   1 root   root      7, 129 2008-10-27 14:46 vcsa1
crw-rw----   1 root   root      7, 130 2008-10-27 14:46 vcsa2
crw-rw----   1 root   root      7, 131 2008-10-27 14:46 vcsa3
crw-rw----   1 root   root      7, 132 2008-10-27 14:46 vcsa4
crw-rw----   1 root   root      7, 133 2008-10-27 14:46 vcsa5
crw-rw----   1 root   root      7, 134 2008-10-27 14:46 vcsa6
crw-rw----   1 root   root      7, 135 2008-10-27 14:46 vcsa7
crw-rw----   1 root   root      7, 136 2008-10-27 14:46 vcsa8
prw-r-----   1 syslog adm            0 2008-10-27 14:46 xconsole
crw-rw-rw-   1 root   root      1,   5 2008-10-27 14:46 zero

```

Edit: Tried to mount as suggested with /dev/sdb, no luck on that one unfortunately.

---

### Post by lswest on 2008-10-27
judging by the ownership of the drive that might be the problem, but I don't know for sure.

I would suggest trying this:
```
sudo chown root:disk /dev/sdb1
``` (which, if it doesn't fix it, can be undone by using the same command but substituting disk with root)
and running ```
sudo chmod g+rw /dev/sdb1
``` (which, again, can be undone by changing the + to a -)

This should give users in the "disk" group permission to read the file (since it can't seem to be found) and change the group ownership to disk (as it is with all the other disk labels).

Try these two options (together) and if they don't fix it, undo them as they may cause other problems (I do not know what it might affect, but it's the only thing I can think of doing).

If it does not work, then hopefully some mod or developer will be able to shed some light on the matter.

---

### Post by DigitalJediUK on 2008-10-27
That did not work unfortunately. However, when mounting this time, I was given this message:

```
Error opening partition device: No such device or address
Failed to mount '/dev/sdb1': No such device or address
You seem to have a SoftRAID/FakeRAID hardware and must use an activated,
different device under /dev/mapper/, (e.g. /dev/mapper/nvidia_eahaabcc1)
to mount NTFS. Please see the 'dmraid' documentation for help.

```

I am somewhat confused by this as I have never used a Raid Array on this system. However, if this is what is causing the problem I figured I should probably put it up.

I am also mounting with this command:

```
 sudo mount /dev/sdb1 /media/sdb1/ -t ntfs -o nls=utf8,umask=0222

```

Note: I did create /media/sdb1/ earlier so it does exist.

Is this right? If not, what should I be using.

Thank you for all your help on this matter :).

---

### Post by lswest on 2008-10-27
the command is fine the way I see it, and if it did not work then I suggest undoing what was done and hopefully someone with more knowledge in this area can help?

---

### Post by blackened on 2008-10-27
> **DigitalJediUK said:**
> 

I am also mounting with this command:

```
 sudo mount /dev/sdb1 /media/sdb1/ -t ntfs -o nls=utf8,umask=0222

```

Note: I did create /media/sdb1/ earlier so it does exist.

Is this right? If not, what should I be using.

Thank you for all your help on this matter :).

I could be wrong, but I've always used the syntax thusly:

```
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sdb1 /media/sdb1
```

Maybe I'm misreading the man page and you can format it the way you did just fine.

---

### Post by DigitalJediUK on 2008-10-27
OK thank you for all of your help :). I shall check back here later and see if anyone else is able to help me on this one.

---

### Post by DigitalJediUK on 2008-10-27
@blackened: Thanks. But still get the same command. By the looks of it I guess that it doesn't matter too much (again, if I am wrong please correct me).

---

### Post by DigitalJediUK on 2008-10-28
*Bump*

---

### Post by sacauntos on 2008-10-28
> **DigitalJediUK said:**
> That did not work unfortunately. However, when mounting this time, I was given this message:

```
Error opening partition device: No such device or address
Failed to mount '/dev/sdb1': No such device or address
You seem to have a SoftRAID/FakeRAID hardware and must use an activated,
different device under /dev/mapper/, (e.g. /dev/mapper/nvidia_eahaabcc1)
to mount NTFS. Please see the 'dmraid' documentation for help.

```


I was having the same problem as you, with very similar outputs for fdisk and even the same error you had. I tried to solve it by following the advices from this thread and nothing. Trying to mount the device manually I got a message in the terminal telling me to chkdsk /f the HDD in windows and then rebooting twice before switching back to ubuntu.

I did that and now my HDD is working again! I'm not an expert as you see... so maybe somebody else could bring some light here as well...

---

