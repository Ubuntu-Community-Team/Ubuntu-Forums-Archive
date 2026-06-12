---
title: "just some minor problems...like booting..."
date: 2008-10-08
forum: New to Ubuntu
---

### Post by mandalorethx on 2008-10-08
I have wanted to try Linux for a long time now, and have finally gotten around to doing it.  However, I am experiencing some problems with Ubuntu 8.04  Any help would be greatly appreciated

1) booting - I cannot boot into Ubuntu after it is installed
I want to keep Vista on my system for a while, and have been trying to dual-boot Vista and Ubuntu.  First I tried Wubi (came on the Ubunut CD) and no entry was added to the boot menu.  I tried to configure it in FreeBCD, but could still not boot into it.
I then installed ubuntu from the CD (not through Wubi) which worked if I installed GRUB on the same drive as my Windows installation.  However, I could then not boot into Windows.  After I repaired the Windows boot loader through the Vista DVD, I could no longer boot into Ubuntu
I went back into FreeBCD and configured a NeoGRUB entry for Ubuntu.  Here is the Entry
```
title		Ubuntu 
root		(hd1,0)   	
kernel		/boot/vmlinuz-2.6.24-19-generic
initrd		/boot/initrd.img-2.6.24-19-generic


```

with this the boot process hangs at the following

```
[ 49.582314] sd 6:0:0:3: Attached scsi generic sg8 type 0

```

for a while, then i get the following error:

```
check root=bootarg cat /roc/cmdline
or missing modules, deviec: cat/proc/modules ls /dev
ALERT! does not exist!  dropping to a shell
```

and I end up in a command-line interface

2)wireless adapter driver
my second problem is with my USB wireless adapter.  it is a netgear WN111.  After reading about it on other forums, I downloaded ndiswrapper, a ndiswrapper utility pack, and a GUI for the program, ndisgtk.  I got the driver from my windows installation (netm214b.inf and the other associated files) and installed it, and wrote the alliases (the -m, -ma, and -mi commands)
ndiswrapper -l reported the device as being present and the driver being installed, but I still cannot access the internet
NOTE: on a different thread on this forum, I also saw the command "sudo modprobe ndiswrapper" which should be added, but which I did not.  However, I cannot find out if this will solve my problem because I cannot boot into Ubuntu.

Thanks for any help or advice you can offer

---

### Post by caljohnsmith on 2008-10-08
You can easily add an entry to boot Windows in your Grub menu, so personally I would recommend reinstalling Grub to the MBR (Master Boot Record), and then configuring your Grub's menu.lst to boot Windows. Another option is to install Grub to the boot sector of the Ubuntu partition, and then it's easy to boot Ubuntu from Vista's boot loader. If you would like help doing either of those techniques, please first post:
```
sudo fdisk -lu
```
And let me know which direction you want to go.

---

### Post by mandalorethx on 2008-10-08
```
sudo fdisk -lu

```

i hope thats wht you meant or that will look really stupid

if you could walk me throuhg reinstalling GRUB, that would be great
i have tried looking up how to do this, but everything i find seems to be solved from within linux

---

### Post by caljohnsmith on 2008-10-08
OK, first boot your Ubuntu Live CD, open a terminal (Applications > Accessories > Terminal), and type:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
See if you can get that far and we can work from there, or if you run into problems let me know. :)

---

### Post by mandalorethx on 2008-10-09
ok
here are the fdisk results:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes

240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x417b9b39



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *          63   488391119   244195528+   7  HPFS/NTFS



Disk /dev/sdb: 120.0 GB, 120034123776 bytes

255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x23213b72



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1              63   224829674   112414806   83  Linux

/dev/sdb2       224829675   234436544     4803435    5  Extended

/dev/sdb5       224829738   234436544     4803403+  82  Linux swap / Solaris



Disk /dev/sdc: 320.0 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x3d603f6d



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1   *          63   625137344   312568641    7  HPFS/NTFS



Disk /dev/sdh: 2021 MB, 2021654016 bytes

255 heads, 63 sectors/track, 245 cylinders, total 3948543 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System

/dev/sdh1   *          63     3948542     1974240    6  FAT16

Partition 1 has different physical/logical endings:

     phys=(244, 254, 63) logical=(245, 200, 18)


```

I have ubuntu installed on sdb1 and tried to enter the codes you suggested but got this:

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1/mnt 
mount: can't find /dev/sdb1/mnt in /etc/fstab or /etc/mtab 
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst 
cat: /mnt/boot/grub/menu.lst: No such file or directory 
ubuntu@ubuntu:~$  

```

---

### Post by caljohnsmith on 2008-10-09
Can you go into your BIOS and choose the Ubuntu drive sdb as the first to boot on start up? If you can do that, then from your Live CD again do:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
The above commands will install Grub to the MBR (Master Boot Record) of your Ubuntu drive so that it will be bootable. Next go ahead and reboot (make sure the Ubuntu drive is first in the BIOS boot order), and when you (hopefully) get the Grub menu, select Ubuntu, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. See if you can get that far and we'll go from there, or let me know if you run into problems again. :)

---

### Post by mandalorethx on 2008-10-09
OK, i can now get into ubnutu
thank you very much
the only question I have left in that regard is how to edit the menu.lst.  If i open it in gedit, i cannot save it (i "don't have permission")

my wireless adapter is still causing causing me troubles too
i ran the code (sudo modprobe ndiswrapper) but this did nothing.  is there anyhting else I can try to enable my wireless adapter?

---

### Post by caljohnsmith on 2008-10-09
OK, to edit your menu.lst, just do:
```
gksudo gedit /boot/grub/menu.lst
```
"sudo" and "gksudo" let you modify system files that require being the root user; sudo is for commands run in the terminal, and gksudo is for GUI programs. 

About your wireless problem, if doing "sudo modprobe ndiswrapper" does nothing, that is actually what you want; that means the command completed with no errors. Try doing: 
```
sudo iwlist wlan0 scan
```
And see if that shows any available networks.

---

### Post by mandalorethx on 2008-10-09
the menu.lst editing went perfectly

however, when i tried the other code, I got the following error:
```

wlan0     Interface doesn't support scanning.
```

is there anything else i can try?

---

