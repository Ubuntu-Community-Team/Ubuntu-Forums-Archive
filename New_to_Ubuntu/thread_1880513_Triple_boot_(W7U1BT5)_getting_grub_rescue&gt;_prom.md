---
title: "Triple boot (W7/U1/BT5) getting grub rescue&gt; prompt  after attempted image restore.."
date: 2011-11-13
forum: New to Ubuntu
---

### Post by Markie76 on 2011-11-13
Hi Guys,

I'm a complete Linux newbie with a Dell M1710 laptop  which I setup with  Windows7, Ubuntu 10 and Backtrack 5. I mainly use W7  sometimes Ubuntu  and was just curious about BT5 and used it about 3  times.

Last night I have had enough of Windows 7 due to various  slowdowns and  device install issues and decided it was time to 'refresh'  my laptop by  restoring a virgin image of my W7 install saved in Ghost  format. I'm  quite a fan of the Dell 'hidden restore' partition but due  to the size  of my W7 image - I boot Symantec Ghost on CD then plug in a  USB hdd  with the image on it and restore it to my C: partition.

Now,  last night I was a complete plonker. I booted Ghost Cd, pointed it  to  the image and from the 'restore to' partition list I chose my W7   partition (going by its position in the list and reported size) without   thinking about and ignoring the triple boot other partitions in   the list. Ghost seemed to be working ok until it got to 99% complete and   remained there - I had to power button it after a couple of hours :sad:

When I powered on, after the post screen it just says;
***error: unknown filesystem. grub rescue>***
If  I try to get into the hidden restore partition by pressing CTRL +  F11  when the Dell logo appears on the post screen nothing happens and  it  displays the above message.

So it seems I have screwed  up/corrupted the MBR/bootloader used for the  triple boot setup, possibly  by not removing the triple boot setup  before restoring the backup image  or Ghost couldn't handle the triple  boot setup.

From memory my 120gb hdd had the following partitions;
0 - some tiny unused space
1 - Dell restore partition - 4gb or so
2 - Main partition - W7 76gb or so
3 - U10 - 20gb or so 
4 - BT5 - 15gb or so
5 - Dell Diagnostics - don't know the size but was mb's rather than gb's
6  - Dell media centre partition - I think it was 2gb and was at the end   of the hdd (you could boot into a version of Media Centre without  having  to boot the OS.

From doing some research booting from a Live CD  should be able to help -  however I have tried a Ubuntu 11 CD & USB  boot but get errors  (flashing caps & num lock lights). I then tried a  Knoppix CD I had  and it booted ok - I then opened a Terminal window and  did 'sudo fdisk  -l' and it said the following;

```

Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12        9306    74662052    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            9307       13987    37599602+   f  W95 Ext'd (LBA)
/dev/sda4           13988       14593     4867695   db  CP/M / CTOS / ...
/dev/sda5           13727       13987     2096451   dd  Unknown
/dev/sda6           11959       14495    20370432   83  Linux
/dev/sda7           11843       13530    13555712   83  Linux
/dev/sda8           13646       13726      644096   82  Linux swap / Solaris
/dev/sda9            9307       11843    20370432   83  Linux
/dev/sda10          11843       13530    13555712   83  Linux
/dev/sda11          13646       13726      644096   82  Linux swap / Solaris
/dev/sda12           9307       11843    20370432   83  Linux
/dev/sda13          11843       13530    13555712   83  Linux
/dev/sda14          13646       13726      644096   82  Linux swap / Solaris
/dev/sda15           9307       11843    20370432   83  Linux
/dev/sda16          11843       13530    13555712   83  Linux
/dev/sda17          13646       13726      644096   82  Linux swap / Solaris
/dev/sda18           9307       11843    20370432   83  Linux
/dev/sda19          11843       13530    13555712   83  Linux
/dev/sda20          13646       13726      644096   82  Linux swap / Solaris
/dev/sda21           9307       11843    20370432   83  Linux
/dev/sda22          11843       13530    13555712   83  Linux
/dev/sda23          13646       13726      644096   82  Linux swap / Solaris
/dev/sda24           9307       11843    20370432   83  Linux
/dev/sda25          11843       13530    13555712   83  Linux
/dev/sda26          13646       13726      644096   82  Linux swap / Solaris
/dev/sda27           9307       11843    20370432   83  Linux
/dev/sda28          11843       13530    13555712   83  Linux
/dev/sda29          13646       13726      644096   82  Linux swap / Solaris
/dev/sda30           9307       11843    20370432   83  Linux
/dev/sda31          11843       13530    13555712   83  Linux
/dev/sda32          13646       13726      644096   82  Linux swap / Solaris
/dev/sda33           9307       11843    20370432   83  Linux
/dev/sda34          11843       13530    13555712   83  Linux
/dev/sda35          13646       13726      644096   82  Linux swap / Solaris
/dev/sda36           9307       11843    20370432   83  Linux
/dev/sda37          11843       13530    13555712   83  Linux
/dev/sda38          13646       13726      644096   82  Linux swap / Solaris
/dev/sda39           9307       11843    20370432   83  Linux
/dev/sda40          11843       13530    13555712   83  Linux
/dev/sda41          13646       13726      644096   82  Linux swap / Solaris
/dev/sda42           9307       11843    20370432   83  Linux
/dev/sda43          11843       13530    13555712   83  Linux
/dev/sda44          13646       13726      644096   82  Linux swap / Solaris
/dev/sda45           9307       11843    20370432   83  Linux
/dev/sda46          11843       13530    13555712   83  Linux
/dev/sda47          13646       13726      644096   82  Linux swap / Solaris
/dev/sda48           9307       11843    20370432   83  Linux
/dev/sda49          11843       13530    13555712   83  Linux
/dev/sda50          13646       13726      644096   82  Linux swap / Solaris
/dev/sda51           9307       11843    20370432   83  Linux
/dev/sda52          11843       13530    13555712   83  Linux
/dev/sda53          13646       13726      644096   82  Linux swap / Solaris
/dev/sda54           9307       11843    20370432   83  Linux
/dev/sda55          11843       13530    13555712   83  Linux
/dev/sda56          13646       13726      644096   82  Linux swap / Solaris
/dev/sda57           9307       11843    20370432   83  Linux
/dev/sda58          11843       13530    13555712   83  Linux
/dev/sda59          13646       13726      644096   82  Linux swap / Solaris
/dev/sda60           9307       11843    20370432   83  Linux

Partition table entries are not in disk order
```sda1 looks like the Dell Diagnostics
sda2 looks like my main W7 partition
sda3 ?
sda4 ?
sda5 looks like the 'Media Centre' partition
sda 6 & 7 - U10 & BT5?
sda8 to 60 ?

Thats about as far as my knowledge gets me :(

Any  further help much appreciated - I would like to restore/rescue my 'hidden restore'   partition as well as the dell diagnostics and media centre partitions. 

Thanks,

Mark.

---

### Post by oldfred on 2011-11-13
Did you restore a partition table that was an old one, after you created new one's?

You will note the table entries repeat every 3. Logical partitions are a linked list so the linked list is corrupted.

Someone had this before, but I do not remember exact solution.

I would first back up partition table.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

I might look at it and see what it says.

You can try this but if it does not look correct do not hit w.

this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit
else if it is not ok
then post the output of option p and v

And this program may work, but not sure about this type of problem.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Edit
This user had same issue and used testdisk, and it worked from him.
[http://ubuntuforums.org/showthread.php?t=1640478](http://ubuntuforums.org/showthread.php?t=1640478)
Another user that used testdisk, but then testdisk created another issue.
[http://ubuntuforums.org/showthread.php?t=1849060](http://ubuntuforums.org/showthread.php?t=1849060)

---

### Post by drs305 on 2011-11-13
As with *oldfred*, I recall seeing a similar issue. This is the thread I recalled. I think the two threads take a similar approach, but if the first one doesn't solve things, see if there is something in this one that you might be able to use. Note the error about 'physical sector boundaries' isn't really important to the issue at hand.
[http://ubuntuforums.org/showthread.php?t=1849060&highlight=hundreds+partitions]("http://ubuntuforums.org/showthread.php?t=1849060&highlight=hundreds+partitions")

---

### Post by Markie76 on 2011-11-14
Thank you for your replies. I have read the other threads and as an M$ gui zombie  please bear with me if I'm going round in circles...

> **oldfred said:**
> Did you restore a partition table that was an old one, after you created new one's?
To clarify, when I originally setup the triple boot I only used the tools on the livecd's - going with the default options, can't remember if I setup separate swap partitions for both the linux environments, but it has worked flawlessly since Nov 10.
When I tried my image restore 2 nights ago I didn't 'manually' make any partition changes or restore an older table - all I did was in the list of partitions displayed in Ghost I went into what looked like my W7 partition to check the summary info.
The restore image shouldn't have any partition table info or shouldn't make any changes as it is simply the image of the contents and when you restore it just warns you the contents of the target partition will be overwritten - which is why I'm still puzzled about why I'm in this situation - Ghost should have just restored the files & folders & FAT(?) in the image to the C: drive/partition (c partition is 70gb or so & image is 14gb) without making any changes to the triple boot because all that is handled by grub/Linux and stored in another partition?

> **oldfred said:**
> Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt
I have tried this, gave a warning message but produced the txt file;
```
TERMINAL WINDOW MESSAGE;

knoppix@Knoppix:~$ sudo sfdisk -d /dev/sda > PTsda.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
too many partitions - ignoring those past nr (507)

PTsda.txt;

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   176652, Id=de
/dev/sda2 : start=   176715, size=149324104, Id= 7, bootable
/dev/sda3 : start=149501950, size= 75199205, Id= f
/dev/sda4 : start=224701155, size=  9735390, Id=db
/dev/sda5 : start=220508253, size=  4192902, Id=dd
/dev/sda6 : start=192105271, size= 40740864, Id=83
/dev/sda7 : start=190244042, size= 27111424, Id=83
/dev/sda8 : start=219219968, size=  1288192, Id=82
/dev/sda9 : start=149501952, size= 40740864, Id=83
/dev/sda10: start=190244042, size= 27111424, Id=83
/dev/sda11: start=219219968, size=  1288192, Id=82
/dev/sda12: start=149501952, size= 40740864, Id=83
/dev/sda13: start=190244042, size= 27111424, Id=83
/dev/sda14: start=219219968, size=  1288192, Id=82
/dev/sda15: start=149501952, size= 40740864, Id=83
/dev/sda16: start=190244042, size= 27111424, Id=83
/dev/sda17: start=219219968, size=  1288192, Id=82
/dev/sda18: start=149501952, size= 40740864, Id=83
/dev/sda19: start=190244042, size= 27111424, Id=83
/dev/sda20: start=219219968, size=  1288192, Id=82
/dev/sda21: start=149501952, size= 40740864, Id=83
/dev/sda22: start=190244042, size= 27111424, Id=83
/dev/sda23: start=219219968, size=  1288192, Id=82
/dev/sda24: start=149501952, size= 40740864, Id=83
/dev/sda25: start=190244042, size= 27111424, Id=83
/dev/sda26: start=219219968, size=  1288192, Id=82
/dev/sda27: start=149501952, size= 40740864, Id=83
/dev/sda28: start=190244042, size= 27111424, Id=83
/dev/sda29: start=219219968, size=  1288192, Id=82
/dev/sda30: start=149501952, size= 40740864, Id=83
/dev/sda31: start=190244042, size= 27111424, Id=83
/dev/sda32: start=219219968, size=  1288192, Id=82
/dev/sda33: start=149501952, size= 40740864, Id=83
/dev/sda34: start=190244042, size= 27111424, Id=83
/dev/sda35: start=219219968, size=  1288192, Id=82
/dev/sda36: start=149501952, size= 40740864, Id=83
/dev/sda37: start=190244042, size= 27111424, Id=83
/dev/sda38: start=219219968, size=  1288192, Id=82
/dev/sda39: start=149501952, size= 40740864, Id=83
/dev/sda40: start=190244042, size= 27111424, Id=83
/dev/sda41: start=219219968, size=  1288192, Id=82
/dev/sda42: start=149501952, size= 40740864, Id=83
/dev/sda43: start=190244042, size= 27111424, Id=83
/dev/sda44: start=219219968, size=  1288192, Id=82
/dev/sda45: start=149501952, size= 40740864, Id=83
/dev/sda46: start=190244042, size= 27111424, Id=83
/dev/sda47: start=219219968, size=  1288192, Id=82
/dev/sda48: start=149501952, size= 40740864, Id=83
/dev/sda49: start=190244042, size= 27111424, Id=83
/dev/sda50: start=219219968, size=  1288192, Id=82
/dev/sda51: start=149501952, size= 40740864, Id=83
/dev/sda52: start=190244042, size= 27111424, Id=83
/dev/sda53: start=219219968, size=  1288192, Id=82
/dev/sda54: start=149501952, size= 40740864, Id=83
/dev/sda55: start=190244042, size= 27111424, Id=83
/dev/sda56: start=219219968, size=  1288192, Id=82
/dev/sda57: start=149501952, size= 40740864, Id=83
/dev/sda58: start=190244042, size= 27111424, Id=83
/dev/sda59: start=219219968, size=  1288192, Id=82
/dev/sda60: start=149501952, size= 40740864, Id=83
/dev/sda61: start=190244042, size= 27111424, Id=83
/dev/sda62: start=219219968, size=  1288192, Id=82
/dev/sda63: start=149501952, size= 40740864, Id=83
/dev/sda64: start=190244042, size= 27111424, Id=83
/dev/sda65: start=219219968, size=  1288192, Id=82
/dev/sda66: start=149501952, size= 40740864, Id=83
/dev/sda67: start=190244042, size= 27111424, Id=83
/dev/sda68: start=219219968, size=  1288192, Id=82
/dev/sda69: start=149501952, size= 40740864, Id=83
/dev/sda70: start=190244042, size= 27111424, Id=83
/dev/sda71: start=219219968, size=  1288192, Id=82
/dev/sda72: start=149501952, size= 40740864, Id=83
/dev/sda73: start=190244042, size= 27111424, Id=83
/dev/sda74: start=219219968, size=  1288192, Id=82
/dev/sda75: start=149501952, size= 40740864, Id=83
/dev/sda76: start=190244042, size= 27111424, Id=83
/dev/sda77: start=219219968, size=  1288192, Id=82
/dev/sda78: start=149501952, size= 40740864, Id=83
/dev/sda79: start=190244042, size= 27111424, Id=83
/dev/sda80: start=219219968, size=  1288192, Id=82
/dev/sda81: start=149501952, size= 40740864, Id=83
/dev/sda82: start=190244042, size= 27111424, Id=83
/dev/sda83: start=219219968, size=  1288192, Id=82
/dev/sda84: start=149501952, size= 40740864, Id=83
/dev/sda85: start=190244042, size= 27111424, Id=83
/dev/sda86: start=219219968, size=  1288192, Id=82
/dev/sda87: start=149501952, size= 40740864, Id=83
/dev/sda88: start=190244042, size= 27111424, Id=83
/dev/sda89: start=219219968, size=  1288192, Id=82
/dev/sda90: start=149501952, size= 40740864, Id=83
/dev/sda91: start=190244042, size= 27111424, Id=83
/dev/sda92: start=219219968, size=  1288192, Id=82
/dev/sda93: start=149501952, size= 40740864, Id=83
/dev/sda94: start=190244042, size= 27111424, Id=83
/dev/sda95: start=219219968, size=  1288192, Id=82
/dev/sda96: start=149501952, size= 40740864, Id=83
/dev/sda97: start=190244042, size= 27111424, Id=83
/dev/sda98: start=219219968, size=  1288192, Id=82
/dev/sda99: start=149501952, size= 40740864, Id=83
/dev/sda100: start=190244042, size= 27111424, Id=83
/dev/sda101: start=219219968, size=  1288192, Id=82
/dev/sda102: start=149501952, size= 40740864, Id=83
/dev/sda103: start=190244042, size= 27111424, Id=83
/dev/sda104: start=219219968, size=  1288192, Id=82
/dev/sda105: start=149501952, size= 40740864, Id=83
/dev/sda106: start=190244042, size= 27111424, Id=83
/dev/sda107: start=219219968, size=  1288192, Id=82
/dev/sda108: start=149501952, size= 40740864, Id=83
/dev/sda109: start=190244042, size= 27111424, Id=83
/dev/sda110: start=219219968, size=  1288192, Id=82
/dev/sda111: start=149501952, size= 40740864, Id=83
/dev/sda112: start=190244042, size= 27111424, Id=83
/dev/sda113: start=219219968, size=  1288192, Id=82
/dev/sda114: start=149501952, size= 40740864, Id=83
/dev/sda115: start=190244042, size= 27111424, Id=83
/dev/sda116: start=219219968, size=  1288192, Id=82
/dev/sda117: start=149501952, size= 40740864, Id=83
/dev/sda118: start=190244042, size= 27111424, Id=83
/dev/sda119: start=219219968, size=  1288192, Id=82
/dev/sda120: start=149501952, size= 40740864, Id=83
/dev/sda121: start=190244042, size= 27111424, Id=83
/dev/sda122: start=219219968, size=  1288192, Id=82
/dev/sda123: start=149501952, size= 40740864, Id=83
/dev/sda124: start=190244042, size= 27111424, Id=83
/dev/sda125: start=219219968, size=  1288192, Id=82
/dev/sda126: start=149501952, size= 40740864, Id=83
/dev/sda127: start=190244042, size= 27111424, Id=83
/dev/sda128: start=219219968, size=  1288192, Id=82
/dev/sda129: start=149501952, size= 40740864, Id=83
/dev/sda130: start=190244042, size= 27111424, Id=83
```> **oldfred said:**
> ...this occasionally fixes issues and is worth trying:
you do the following : fdisk /dev/sda
It also didn't like this;
```
knoppix@Knoppix:~$ fdisk /dev/sda

Unable to open /dev/sda
```I also tried sudo fdisk -lu;
```
knoppix@Knoppix:~$ sudo fdisk -lu
Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      176714       88326   de  Dell Utility
/dev/sda2   *      176715   149500818    74662052    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3       149501950   224701154    37599602+   f  W95 Ext'd (LBA)
/dev/sda4       224701155   234436544     4867695   db  CP/M / CTOS / ...
/dev/sda5       220508253   224701154     2096451   dd  Unknown
/dev/sda6       192105271   232846134    20370432   83  Linux
/dev/sda7       190244042   217355465    13555712   83  Linux
/dev/sda8       219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda9       149501952   190242815    20370432   83  Linux
/dev/sda10      190244042   217355465    13555712   83  Linux
/dev/sda11      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda12      149501952   190242815    20370432   83  Linux
/dev/sda13      190244042   217355465    13555712   83  Linux
/dev/sda14      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda15      149501952   190242815    20370432   83  Linux
/dev/sda16      190244042   217355465    13555712   83  Linux
/dev/sda17      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda18      149501952   190242815    20370432   83  Linux
/dev/sda19      190244042   217355465    13555712   83  Linux
/dev/sda20      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda21      149501952   190242815    20370432   83  Linux
/dev/sda22      190244042   217355465    13555712   83  Linux
/dev/sda23      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda24      149501952   190242815    20370432   83  Linux
/dev/sda25      190244042   217355465    13555712   83  Linux
/dev/sda26      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda27      149501952   190242815    20370432   83  Linux
/dev/sda28      190244042   217355465    13555712   83  Linux
/dev/sda29      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda30      149501952   190242815    20370432   83  Linux
/dev/sda31      190244042   217355465    13555712   83  Linux
/dev/sda32      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda33      149501952   190242815    20370432   83  Linux
/dev/sda34      190244042   217355465    13555712   83  Linux
/dev/sda35      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda36      149501952   190242815    20370432   83  Linux
/dev/sda37      190244042   217355465    13555712   83  Linux
/dev/sda38      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda39      149501952   190242815    20370432   83  Linux
/dev/sda40      190244042   217355465    13555712   83  Linux
/dev/sda41      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda42      149501952   190242815    20370432   83  Linux
/dev/sda43      190244042   217355465    13555712   83  Linux
/dev/sda44      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda45      149501952   190242815    20370432   83  Linux
/dev/sda46      190244042   217355465    13555712   83  Linux
/dev/sda47      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda48      149501952   190242815    20370432   83  Linux
/dev/sda49      190244042   217355465    13555712   83  Linux
/dev/sda50      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda51      149501952   190242815    20370432   83  Linux
/dev/sda52      190244042   217355465    13555712   83  Linux
/dev/sda53      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda54      149501952   190242815    20370432   83  Linux
/dev/sda55      190244042   217355465    13555712   83  Linux
/dev/sda56      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda57      149501952   190242815    20370432   83  Linux
/dev/sda58      190244042   217355465    13555712   83  Linux
/dev/sda59      219219968   220508159      644096   82  Linux swap / Solaris
/dev/sda60      149501952   190242815    20370432   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7856126     3928032    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(488, 254, 63) logical=(489, 5, 27)
```I also tried the boot_info_script.sh - it sat there for about 15 minutes, the CD span up a few times and eventually it said;
```
knoppix@Knoppix:~$ sudo bash ~/Desktop/boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Segmentation fault
```I then tried testdisk which looks more promising but I would like an expert to cast their eye over it and advise the safest way to proceed to avoid what happened to the other user if poss :)
I ran the program, selected the 120gb hdd and then did analyse, saved a backup(postaed as attachment), then quick search then deep search. It completed but then gave an error(similar to the other user problem);

backup.log & testdisk.log - saved as attachments

The quick search results; (from memory look good)
```
TestDisk 6.13-WIP, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
>D FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
 D HPFS - NTFS             11   0  1  9305 253 55  149324104
 D Linux                 9306  16 55 11842  17 15   40740864
 D Linux Swap           11842  49 48 11957 241 44    1859568
 D Linux                11958  19 30 13645 174 33   27111424
 D Linux Swap           13645 207  3 13725 254 17    1288176
 D FAT32 LBA            13726   1  1 13986 254 63    4192902 [MEDIADIRECT]
 D FAT32 LBA            13987   0  1 14592 254 63    9735390 [DellRestore]

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 90 MB / 86 MiB 
```So the outcome of the 'quick search' looks quite familiar, it seems to show the hidden partition, the main 70ish-gb main W7 partition (when I browsed files they looked like the W7 image I was restoring), the media centre partition, the dell diagnostics partition and the tiny unused partition - but not sure about the order of them.

So what do I do now? Run the quick search and 'write' the results to the disk?

I'm away from home for a few days but I have the hdd with me and I can boot it up in another laptop which should run U10 live cd.

Thanks,

Mark.

---

### Post by oldfred on 2011-11-14
The boot script has problems trying to run as it opens every partition and reviews it. With the loop in the partition table it will try to reopen the partitions over & over.

See if testdisk will write a partition table. Testdisk has been know to write the end to the extended partition beyond the end of the drive (so math bug) but that is easily fixed with a program fixparts.

---

