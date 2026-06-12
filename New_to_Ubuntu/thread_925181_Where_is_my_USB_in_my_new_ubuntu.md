---
title: "Where is my USB in my new ubuntu?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by ftaw80 on 2008-09-20
I just installed Ubuntu to my laptop, I am newbie to LINUX. My USBs can be recognized by windows though. just terrified with this incident while i am learning the commands. I did install mountusb, but the drives just ight up, but never recognized. Any help please?

---

### Post by sayakb on 2008-09-20
What drive is it? (Flash disk, USB HDD?)
Plug it into the USB port and post the output of:
```
lsusb
```
...at a terminal (Applications->Accessories->Terminal)

---

### Post by ftaw80 on 2008-09-20
> **LinuxIsInnovation said:**
> What drive is it? (Flash disk, USB HDD?)
Plug it into the USB port and post the output of:
```
lsusb
```
...at a terminal (Applications->Accessories->Terminal)


Thanks for this, 

I tried both USBs and flash disks- none of them worked. The output to lsusb is:

Bus 002 Device 001: ID 0000:0000

Bus 001 Device 001: ID 0000:0000

What else should I do next?

---

### Post by GepettoBR on 2008-09-20
This output means that Ubuntu doesn't see your USB drives (you typed it with them plugged in, right?)

Please type ```
lsmod
``` in a Terminal and post the output here.

---

### Post by ftaw80 on 2008-09-20
> **GepettoBR said:**
> This output means that Ubuntu doesn't see your USB drives (you typed it with them plugged in, right?)

Please type ```
lsmod
``` in a Terminal and post the output here.
Thanks, I've posted the output of lsmod. More help?

Module                  Size  Used by
ipv6                  267780  8 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_ondemand        9740  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
lp                     12324  0 
battery                14212  0 
ac                      6916  0 
evdev                  13056  3 
parport_pc             36260  0 
parport                37832  3 ppdev,lp,parport_pc
serio_raw               7940  0 
psmouse                40336  0 
button                  9232  0 
pcspkr                  4224  0 
i2c_piix4               9612  0 
i2c_core               24832  1 i2c_piix4
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ohci_hcd               25348  0 
ehci_hcd               37900  0 
floppy                 59588  0 
usbcore               146028  3 ohci_hcd,ehci_hcd
ata_piix               19588  2 
pata_acpi               8320  0 
ata_generic             8324  0 
pcnet32                34820  0 
mii                     6400  1 pcnet32
libata                159344  3 ata_piix,pata_acpi,ata_generic
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

---

### Post by GepettoBR on 2008-09-20
That's very strange, usbcore is showing up fine...

I actually forgot to add this to the last post, but I'd also like to see your /etc/fstab file.

---

### Post by ftaw80 on 2008-09-20
> **GepettoBR said:**
> That's very strange, usbcore is showing up fine...

I actually forgot to add this to the last post, but I'd also like to see your /etc/fstab file.

Here is the output to /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cd929550-c53a-4407-bd6b-f9f9715c886d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5b9aa2c4-2285-426b-9fbf-fb0ad57ddc46 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

