---
title: "Lost with Permissions"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by HooctAwnFonix on 2012-06-25
I have an AVRISP MKII programmer that wasn't working in the Arduino IDE unless I opened the program up as sudo.

[This stack overflow post]("http://stackoverflow.com/questions/5412727/avrisp-mkii-doesnt-work-with-avrdude-in-linux") seemed to offer a nice solution but it didn't work for me. At that time, I could see the programmer when I went to /dev/ listed under dialout but it still wouldn't work without me being sudo!

So, I kept googling around and I also found [this post]("http://ubuntuforums.org/showthread.php?t=901891") in this forum which seemed to offer a broader discussion of the specific problem the stack overflow post solved. I played around with some things they talked about but to no avail. The only headway was actually negative: I can't even find the device when I go to /dev/ anymore, although it still works within the Arduino IDE when I'm sudo (seems weird to me!).

Anyway, here are a few things that I think might help you guys diagnose my illness:

A file /etc/udev/avrisp.rules exists with the following:

```
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="avrisp_end"

# Atmel Corp. JTAG ICE mkII
ATTR{idVendor}=="03eb", SYSFS{idProduct}=="2103", MODE="660", GROUP="dialout"
# Atmel Corp. AVRISP mkII
ATTR{idVendor}=="03eb", SYSFS{idProduct}=="2104", MODE="660", GROUP="dialout"
# Atmel Corp. Dragon
ATTR{idVendor}=="03eb", SYSFS{idProduct}=="2107", MODE="660", GROUP="dialout"

LABEL="avrisp_end"
```Also, the link exists in udev/rules:
```
louis@Hades:/etc/udev/rules.d$ ls
60-avrisp.rules  70-persistent-cd.rules  70-persistent-net.rules  README
```When I type, "lsusb -v -d 03eb:2104", I get  "Couldn't open device, some information will be missing" which doesn't happen when I sudo the same command (although I get lots of device details with both). This seems to correlate with the Arduino IDE behavior...

Any ideas?

---

### Post by HooctAwnFonix on 2012-06-26
PS: It's on Ubuntu 12.04

---

### Post by TheFu on 2012-06-26
I don't know anything about Arduino, but it if runs Linux with a normal file system, then we can help.  

You have a classic permissions problem - sudo makes your effective userid "0" or (root), so reading almost any file on a system is possible.  If your normal account does not have appropriate permissions to the directory and/or file, then you can't read it.  This is common in multi-user operating systems.

You need to understand Linux/UNIX file and directory permissions to get the issue solved.  There are 2 types of permissions - ACLs and standard file permissions. I can't imagine that ACLs will be use on Arduino, so just start here to learn about normal file/directory permissions. They can be very complex and have subtle capabilities when setup carefully - for example, you can modify an existing file, but not create a new one or get a list of files inside a directory.

Google found this tutorial: [http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html) which seemed to cover most of the main things you need to understand.

Good luck - if you could post the output of 'ls -l {filename}' then someone might explain exactly what is needed to make your specific userid have access that you want.

---

### Post by audiomick on 2012-06-26
This is along the lines of a wild guess, but it might help.

I had trouble with udev rules and a phone a while back. To get access to the phone, I had to add a new udev rule. Based on this experience

and this
[http://manpages.ubuntu.com/manpages/hardy/man7/udev.7.html](http://manpages.ubuntu.com/manpages/hardy/man7/udev.7.html)

and the bit about permissions with numbers here
[https://help.ubuntu.com/community/FilePermissions#chmod_with_Numbers]("https://help.ubuntu.com/community/FilePermissions#chmod_with_Numbers")

I reckon your udev rule is mounting the jigger so that you don't have permission to get at it. 

My guess is, if you change the  "MODE" number in the udev rule to 666, you might be able to work without sudo. 

As I said, this is a guess. Do back up your existing udev rule before changing it. Do read all of that stuff yourself before messing around with it. Hope that puts you on the right track.

---

### Post by HooctAwnFonix on 2012-06-26
Well, from what I understand from those rules is that owner and group can read and write to the device.

The group is dialout which I am a member of.

I think the strangest thing I am facing now is that I can't even see the device under /dev although I can still use it as sudo and see it when I do lsusb...

Here is the output from lsusb:

```
Bus 002 Device 010: ID 03eb:2104 Atmel Corp. AVR ISP mkII
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x03eb Atmel Corp.
  idProduct          0x2104 AVR ISP mkII
  bcdDevice            2.00
  iManufacturer           1 ATMEL
  iProduct                2 AVRISP mkII
  iSerial                 3 000200122175
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
Device Status:     0x0001
  Self Powered

```

---

### Post by TheFu on 2012-06-26
What are the device file permissions **exactly**? 'ls -al FILE'

Also the output from 'id' would be helpful.

---

### Post by HooctAwnFonix on 2012-06-26
Well that's the most confusing thing for me right now:

The device works as sudo

BUT I **cannot** see the file under /dev. I unplug and plug the thing back in and check the time stamps and nothing shows up! I grep dialout group just to see if my eyes are fooling me and I don't see it.

So unless there's another way for me to find the device (lsusb see it but can I check permissions that way?), I don't know how to show the device file permissions to you...

---

### Post by TheFu on 2012-06-26
Sorry, 

'sudo ls -al /dev/FILE'

or type 'sudo -s' to get into root mode and then type 'ls -al /dev/FILE'. Be certain to cntl-d out of the root shell. Not a good idea to be root all the time.


Please do an 'id' as yourself - not under sudo or root.

---

### Post by HooctAwnFonix on 2012-06-27
OK - I tried ls -al again as sudo but the problem still remains: there is no file representing the programmer (despite it working?!).

Here's what I did:

```

louis@Hades:/dev$ sudo ls -al
total 4
drwxr-xr-x  15 root root        4560 Jun 27 10:30 .
drwxr-xr-x  24 root root        4096 Jun 14 09:21 ..
crw------T   1 root root     10, 235 Jun 27 09:50 autofs
drwxr-xr-x   2 root root         760 Jun 27 09:50 block
drwxr-xr-x   2 root root         180 Jun 27 09:50 bsg
crw------T   1 root root     10, 234 Jun 27 09:50 btrfs-control
drwxr-xr-x   3 root root          60 Jun 27 05:50 bus
lrwxrwxrwx   1 root root           3 Jun 27 09:50 cdrom -> sr0
lrwxrwxrwx   1 root root           3 Jun 27 09:50 cdrw -> sr0
drwxr-xr-x   2 root root        4420 Jun 27 10:30 char
crw-------   1 root root      5,   1 Jun 27 09:50 console
lrwxrwxrwx   1 root root          11 Jun 27 09:50 core -> /proc/kcore
drwxr-xr-x   2 root root          60 Jun 27 09:50 cpu
crw-------   1 root root     10,  60 Jun 27 09:50 cpu_dma_latency
drwxr-xr-x   7 root root         140 Jun 27 05:50 disk
lrwxrwxrwx   1 root root           3 Jun 27 09:50 dvd -> sr0
lrwxrwxrwx   1 root root           3 Jun 27 09:50 dvdrw -> sr0
crw-------   1 root root     10,  61 Jun 27 09:50 ecryptfs
crw-rw----   1 root video    29,   0 Jun 27 09:50 fb0
lrwxrwxrwx   1 root root          13 Jun 27 09:50 fd -> /proc/self/fd
crw-rw-rw-   1 root root      1,   7 Jun 27 09:50 full
crw-rw-rwT   1 root fuse     10, 229 Jun 27 09:50 fuse
crw-------   1 root root    251,   0 Jun 27 09:50 fw0
crw-------   1 root root    249,   0 Jun 27 09:50 hidraw0
crw-------   1 root root    249,   1 Jun 27 09:50 hidraw1
crw-------   1 root root    249,   2 Jun 27 09:50 hidraw2
crw-------   1 root root     10, 228 Jun 27 09:50 hpet
lrwxrwxrwx   1 root root          14 Jun 27 05:50 .initramfs -> /run/initramfs
drwxr-xr-x   4 root root         460 Jun 27 09:50 input
crw-------   1 root root      1,  11 Jun 27 09:50 kmsg
srw-rw-rw-   1 root root           0 Jun 27 09:50 log
brw-rw----   1 root disk      7,   0 Jun 27 09:50 loop0
brw-rw----   1 root disk      7,   1 Jun 27 09:50 loop1
brw-rw----   1 root disk      7,   2 Jun 27 09:50 loop2
brw-rw----   1 root disk      7,   3 Jun 27 09:50 loop3
brw-rw----   1 root disk      7,   4 Jun 27 09:50 loop4
brw-rw----   1 root disk      7,   5 Jun 27 09:50 loop5
brw-rw----   1 root disk      7,   6 Jun 27 09:50 loop6
brw-rw----   1 root disk      7,   7 Jun 27 09:50 loop7
crw-------   1 root root     10, 237 Jun 27 09:50 loop-control
crw-rw----   1 root lp        6,   0 Jun 27 09:50 lp0
drwxr-xr-x   2 root root          60 Jun 27 05:50 mapper
crw-------   1 root root     10, 227 Jun 27 09:50 mcelog
crw-------   1 root root    250,   1 Jun 27 09:50 mei
crw-r-----   1 root kmem      1,   1 Jun 27 09:50 mem
drwxr-xr-x   2 root root          60 Jun 27 05:50 net
crw-------   1 root root     10,  59 Jun 27 09:50 network_latency
crw-------   1 root root     10,  58 Jun 27 09:50 network_throughput
crw-rw-rw-   1 root root      1,   3 Jun 27 09:50 null
crw-rw-rw-   1 root root    195,   0 Jun 27 09:50 nvidia0
crw-rw-rw-   1 root root    195, 255 Jun 27 09:50 nvidiactl
crw-------   1 root root      1,  12 Jun 27 09:50 oldmem
crw-rw----   1 root lp       99,   0 Jun 27 09:50 parport0
crw-r-----   1 root kmem      1,   4 Jun 27 09:50 port
crw-------   1 root root    108,   0 Jun 27 09:50 ppp
crw-------   1 root root     10,   1 Jun 27 09:50 psaux
crw-rw-rw-   1 root tty       5,   2 Jun 27 10:30 ptmx
drwxr-xr-x   2 root root           0 Jun 27 05:50 pts
brw-rw----   1 root disk      1,   0 Jun 27 09:50 ram0
brw-rw----   1 root disk      1,   1 Jun 27 09:50 ram1
brw-rw----   1 root disk      1,  10 Jun 27 09:50 ram10
brw-rw----   1 root disk      1,  11 Jun 27 09:50 ram11
brw-rw----   1 root disk      1,  12 Jun 27 09:50 ram12
brw-rw----   1 root disk      1,  13 Jun 27 09:50 ram13
brw-rw----   1 root disk      1,  14 Jun 27 09:50 ram14
brw-rw----   1 root disk      1,  15 Jun 27 09:50 ram15
brw-rw----   1 root disk      1,   2 Jun 27 09:50 ram2
brw-rw----   1 root disk      1,   3 Jun 27 09:50 ram3
brw-rw----   1 root disk      1,   4 Jun 27 09:50 ram4
brw-rw----   1 root disk      1,   5 Jun 27 09:50 ram5
brw-rw----   1 root disk      1,   6 Jun 27 09:50 ram6
brw-rw----   1 root disk      1,   7 Jun 27 09:50 ram7
brw-rw----   1 root disk      1,   8 Jun 27 09:50 ram8
brw-rw----   1 root disk      1,   9 Jun 27 09:50 ram9
crw-rw-rw-   1 root root      1,   8 Jun 27 09:50 random
crw-rw-r--+  1 root root     10,  62 Jun 27 09:50 rfkill
lrwxrwxrwx   1 root root           4 Jun 27 09:50 rtc -> rtc0
crw-------   1 root root    254,   0 Jun 27 09:50 rtc0
brw-rw----   1 root disk      8,   0 Jun 27 09:50 sda
brw-rw----   1 root disk      8,   1 Jun 27 09:50 sda1
brw-rw----   1 root disk      8,   2 Jun 27 09:50 sda2
brw-rw----   1 root disk      8,   3 Jun 27 09:50 sda3
brw-rw----   1 root disk      8,  16 Jun 27 09:50 sdb
brw-rw----   1 root disk      8,  17 Jun 27 09:50 sdb1
brw-rw----   1 root disk      8,  18 Jun 27 09:50 sdb2
brw-rw----   1 root disk      8,  32 Jun 27 09:50 sdc
brw-rw----   1 root disk      8,  48 Jun 27 09:50 sdd
brw-rw----   1 root disk      8,  64 Jun 27 09:50 sde
brw-rw----   1 root disk      8,  80 Jun 27 09:50 sdf
crw-rw----   1 root disk     21,   0 Jun 27 09:50 sg0
crw-rw----   1 root disk     21,   1 Jun 27 09:50 sg1
crw-rw----+  1 root cdrom    21,   2 Jun 27 09:50 sg2
crw-rw----   1 root disk     21,   3 Jun 27 09:50 sg3
crw-rw----   1 root disk     21,   4 Jun 27 09:50 sg4
crw-rw----   1 root disk     21,   5 Jun 27 09:50 sg5
crw-rw----   1 root disk     21,   6 Jun 27 09:50 sg6
lrwxrwxrwx   1 root root           8 Jun 27 09:50 shm -> /run/shm
crw-------   1 root root     10, 231 Jun 27 09:50 snapshot
drwxr-xr-x   3 root root         400 Jun 27 09:50 snd
brw-rw----+  1 root cdrom    11,   0 Jun 27 09:50 sr0
lrwxrwxrwx   1 root root          15 Jun 27 09:50 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root root          15 Jun 27 09:50 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root root          15 Jun 27 09:50 stdout -> /proc/self/fd/1
crw-rw-rw-   1 root tty       5,   0 Jun 27 10:26 tty
crw--w----   1 root tty       4,   0 Jun 27 09:50 tty0
crw-rw----   1 root tty       4,   1 Jun 27 09:50 tty1
crw--w----   1 root tty       4,  10 Jun 27 09:50 tty10
crw--w----   1 root tty       4,  11 Jun 27 09:50 tty11
crw--w----   1 root tty       4,  12 Jun 27 09:50 tty12
crw--w----   1 root tty       4,  13 Jun 27 09:50 tty13
crw--w----   1 root tty       4,  14 Jun 27 09:50 tty14
crw--w----   1 root tty       4,  15 Jun 27 09:50 tty15
crw--w----   1 root tty       4,  16 Jun 27 09:50 tty16
crw--w----   1 root tty       4,  17 Jun 27 09:50 tty17
crw--w----   1 root tty       4,  18 Jun 27 09:50 tty18
crw--w----   1 root tty       4,  19 Jun 27 09:50 tty19
crw-rw----   1 root tty       4,   2 Jun 27 09:50 tty2
crw--w----   1 root tty       4,  20 Jun 27 09:50 tty20
crw--w----   1 root tty       4,  21 Jun 27 09:50 tty21
crw--w----   1 root tty       4,  22 Jun 27 09:50 tty22
crw--w----   1 root tty       4,  23 Jun 27 09:50 tty23
crw--w----   1 root tty       4,  24 Jun 27 09:50 tty24
crw--w----   1 root tty       4,  25 Jun 27 09:50 tty25
crw--w----   1 root tty       4,  26 Jun 27 09:50 tty26
crw--w----   1 root tty       4,  27 Jun 27 09:50 tty27
crw--w----   1 root tty       4,  28 Jun 27 09:50 tty28
crw--w----   1 root tty       4,  29 Jun 27 09:50 tty29
crw-rw----   1 root tty       4,   3 Jun 27 09:50 tty3
crw--w----   1 root tty       4,  30 Jun 27 09:50 tty30
crw--w----   1 root tty       4,  31 Jun 27 09:50 tty31
crw--w----   1 root tty       4,  32 Jun 27 09:50 tty32
crw--w----   1 root tty       4,  33 Jun 27 09:50 tty33
crw--w----   1 root tty       4,  34 Jun 27 09:50 tty34
crw--w----   1 root tty       4,  35 Jun 27 09:50 tty35
crw--w----   1 root tty       4,  36 Jun 27 09:50 tty36
crw--w----   1 root tty       4,  37 Jun 27 09:50 tty37
crw--w----   1 root tty       4,  38 Jun 27 09:50 tty38
crw--w----   1 root tty       4,  39 Jun 27 09:50 tty39
crw-rw----   1 root tty       4,   4 Jun 27 09:50 tty4
crw--w----   1 root tty       4,  40 Jun 27 09:50 tty40
crw--w----   1 root tty       4,  41 Jun 27 09:50 tty41
crw--w----   1 root tty       4,  42 Jun 27 09:50 tty42
crw--w----   1 root tty       4,  43 Jun 27 09:50 tty43
crw--w----   1 root tty       4,  44 Jun 27 09:50 tty44
crw--w----   1 root tty       4,  45 Jun 27 09:50 tty45
crw--w----   1 root tty       4,  46 Jun 27 09:50 tty46
crw--w----   1 root tty       4,  47 Jun 27 09:50 tty47
crw--w----   1 root tty       4,  48 Jun 27 09:50 tty48
crw--w----   1 root tty       4,  49 Jun 27 09:50 tty49
crw-rw----   1 root tty       4,   5 Jun 27 09:50 tty5
crw--w----   1 root tty       4,  50 Jun 27 09:50 tty50
crw--w----   1 root tty       4,  51 Jun 27 09:50 tty51
crw--w----   1 root tty       4,  52 Jun 27 09:50 tty52
crw--w----   1 root tty       4,  53 Jun 27 09:50 tty53
crw--w----   1 root tty       4,  54 Jun 27 09:50 tty54
crw--w----   1 root tty       4,  55 Jun 27 09:50 tty55
crw--w----   1 root tty       4,  56 Jun 27 09:50 tty56
crw--w----   1 root tty       4,  57 Jun 27 09:50 tty57
crw--w----   1 root tty       4,  58 Jun 27 09:50 tty58
crw--w----   1 root tty       4,  59 Jun 27 09:50 tty59
crw-rw----   1 root tty       4,   6 Jun 27 09:50 tty6
crw--w----   1 root tty       4,  60 Jun 27 09:50 tty60
crw--w----   1 root tty       4,  61 Jun 27 09:50 tty61
crw--w----   1 root tty       4,  62 Jun 27 09:50 tty62
crw--w----   1 root tty       4,  63 Jun 27 09:50 tty63
crw--w----   1 root tty       4,   7 Jun 27 09:50 tty7
crw--w----   1 root tty       4,   8 Jun 27 09:50 tty8
crw--w----   1 root tty       4,   9 Jun 27 09:50 tty9
crw-------   1 root root      5,   3 Jun 27 09:50 ttyprintk
crw-rw----   1 root dialout   4,  64 Jun 27 09:50 ttyS0
crw-rw----   1 root dialout   4,  65 Jun 27 09:50 ttyS1
crw-rw----   1 root dialout   4,  74 Jun 27 09:50 ttyS10
crw-rw----   1 root dialout   4,  75 Jun 27 09:50 ttyS11
crw-rw----   1 root dialout   4,  76 Jun 27 09:50 ttyS12
crw-rw----   1 root dialout   4,  77 Jun 27 09:50 ttyS13
crw-rw----   1 root dialout   4,  78 Jun 27 09:50 ttyS14
crw-rw----   1 root dialout   4,  79 Jun 27 09:50 ttyS15
crw-rw----   1 root dialout   4,  80 Jun 27 09:50 ttyS16
crw-rw----   1 root dialout   4,  81 Jun 27 09:50 ttyS17
crw-rw----   1 root dialout   4,  82 Jun 27 09:50 ttyS18
crw-rw----   1 root dialout   4,  83 Jun 27 09:50 ttyS19
crw-rw----   1 root dialout   4,  66 Jun 27 09:50 ttyS2
crw-rw----   1 root dialout   4,  84 Jun 27 09:50 ttyS20
crw-rw----   1 root dialout   4,  85 Jun 27 09:50 ttyS21
crw-rw----   1 root dialout   4,  86 Jun 27 09:50 ttyS22
crw-rw----   1 root dialout   4,  87 Jun 27 09:50 ttyS23
crw-rw----   1 root dialout   4,  88 Jun 27 09:50 ttyS24
crw-rw----   1 root dialout   4,  89 Jun 27 09:50 ttyS25
crw-rw----   1 root dialout   4,  90 Jun 27 09:50 ttyS26
crw-rw----   1 root dialout   4,  91 Jun 27 09:50 ttyS27
crw-rw----   1 root dialout   4,  92 Jun 27 09:50 ttyS28
crw-rw----   1 root dialout   4,  93 Jun 27 09:50 ttyS29
crw-rw----   1 root dialout   4,  67 Jun 27 09:50 ttyS3
crw-rw----   1 root dialout   4,  94 Jun 27 09:50 ttyS30
crw-rw----   1 root dialout   4,  95 Jun 27 09:50 ttyS31
crw-rw----   1 root dialout   4,  68 Jun 27 09:50 ttyS4
crw-rw----   1 root dialout   4,  69 Jun 27 09:50 ttyS5
crw-rw----   1 root dialout   4,  70 Jun 27 09:50 ttyS6
crw-rw----   1 root dialout   4,  71 Jun 27 09:50 ttyS7
crw-rw----   1 root dialout   4,  72 Jun 27 09:50 ttyS8
crw-rw----   1 root dialout   4,  73 Jun 27 09:50 ttyS9
drwxr-xr-x   3 root root          60 Jun 27 09:50 .udev
crw-r-----   1 root root     10, 223 Jun 27 09:50 uinput
crw-rw-rw-   1 root root      1,   9 Jun 27 09:50 urandom
drwxr-xr-x   2 root root          60 Jun 27 09:50 usb
crw-------   1 root root    252,   0 Jun 27 09:50 usbmon0
crw-------   1 root root    252,   1 Jun 27 09:50 usbmon1
crw-------   1 root root    252,   2 Jun 27 09:50 usbmon2
crw-------   1 root root    252,   3 Jun 27 09:50 usbmon3
crw-------   1 root root    252,   4 Jun 27 09:50 usbmon4
crw-------   1 root root    252,   5 Jun 27 09:50 usbmon5
crw-------   1 root root    252,   6 Jun 27 09:50 usbmon6
crw-rw----   1 root tty       7,   0 Jun 27 09:50 vcs
crw-rw----   1 root tty       7,   1 Jun 27 09:50 vcs1
crw-rw----   1 root tty       7,   2 Jun 27 09:50 vcs2
crw-rw----   1 root tty       7,   3 Jun 27 09:50 vcs3
crw-rw----   1 root tty       7,   4 Jun 27 09:50 vcs4
crw-rw----   1 root tty       7,   5 Jun 27 09:50 vcs5
crw-rw----   1 root tty       7,   6 Jun 27 09:50 vcs6
crw-rw----   1 root tty       7, 128 Jun 27 09:50 vcsa
crw-rw----   1 root tty       7, 129 Jun 27 09:50 vcsa1
crw-rw----   1 root tty       7, 130 Jun 27 09:50 vcsa2
crw-rw----   1 root tty       7, 131 Jun 27 09:50 vcsa3
crw-rw----   1 root tty       7, 132 Jun 27 09:50 vcsa4
crw-rw----   1 root tty       7, 133 Jun 27 09:50 vcsa5
crw-rw----   1 root tty       7, 134 Jun 27 09:50 vcsa6
crw-------   1 root root     10,  63 Jun 27 09:50 vga_arbiter
crw-rw-rw-   1 root root      1,   5 Jun 27 09:50 zero

```


From what I can tell, none of those look like the programmer :S

---

### Post by HooctAwnFonix on 2012-06-28
So no ideas on how something works but doesn't have a file under /dev?

---

