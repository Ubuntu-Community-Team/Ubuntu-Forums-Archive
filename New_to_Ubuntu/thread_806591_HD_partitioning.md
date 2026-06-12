---
title: "HD partitioning"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by x88a on 2008-05-25
i currently have Windows XP in my comp and i want to install Ubuntu 8.04.
My HD has 2 partitions (C and D)
Windows XP is installed into C.
At the installation part of Ubuntu, what option should i select so that Linux is installed into D?

thank you

---

### Post by bumanie on 2008-05-25
Personally, I always choose manual at the partitioning stage. If you do that, you can setup the mandatory / and swap partitions and also add a  separate /home. This way if you screw up your filesystem somehow, you only have to reinstall to / and all your data is safe. It should be quite clear once you choose manual and the partitioner opens up as to which partition is D:\ is. Highlight it and choose the edit button. Make yourself a 8-10g / a 2g swap and /home as large as you like.

---

### Post by lisati on 2008-05-25
> **x88a said:**
> i currently have Windows XP in my comp and i want to install Ubuntu 8.04.
My HD has 2 partitions (C and D)
Windows XP is installed into C.
At the installation part of Ubuntu, what option should i select so that Linux is installed into D?

thank you

Does D: have any kind of recovery data for Windows on it? if so, stay clear, as you might void your warranty

---

### Post by x88a on 2008-05-25
i did try the manual setup.
However, there were sooo many other different opions besides swapbytes.
Do i need to install them all?

TQ

---

### Post by x88a on 2008-05-25
> **lisati said:**
> Does D: have any kind of recovery data for Windows on it? if so, stay clear, as you might void your warranty

no, i reserved D just for Linux.
i want Linux to run 100% on D
Windows 100% on C

---

### Post by housam on 2008-05-25
Boot from ubuntu live cd and go for sys.>> admin.>> partition editor. this is the partitioning tool . delete the D partition which will leave an unallocated space. then create 3 partitions for ubuntu
- 10 GB for the root ext3 format with the sign ( / )
- 1 GB swap partition
- the rest for /home ext3 format
 and during installation when it comes to the partitioning choose the manual way and assign  the root partition( / )

---

### Post by bumanie on 2008-05-25
Installing any linux distro, requires two mandatory partitions, one being / where all the systemfiles are kept and swap which is partition where processes/programs can be held if you run out of ram. So you have to have those two partitions. It is a good idea to have a separate /home as described above as then your saved data is separate from the filesystem files. Once you do it, it's not that hard. As long as you are sure you are installing to your present D:\ and don't alter anything on C:\, even if you get it wrong, you can try a second time - again, I stress, as long as you don't get the partitioner to alter your present C:\ that's the main point to remember

---

### Post by lisati on 2008-05-25
That's ok - the reason I asked is that some systems come with a recovery partition instead of a Windows disk (on my desktop it's D:) - it could be a nuisance if some data got lost accidentally.
If you've set D: up specifically for Linux, I don't see a problem with using it for Linux.

---

### Post by x88a on 2008-05-25
> **housam said:**
> Boot from ubuntu live cd and go for sysy.>> admin.>> partition editor. this is the partitioning tool . delete the D partition which will leave an unallocated space. then create 3 partitions for ubuntu
- 10 GB for the root ext3 format with the sign ( / )
- 1 GB swap partition
- the rest for /home

may i know what the 10GB root is for?
is it for drivers?
if i install programs like Amarok into Linux, will it go to root or home?

tq

---

### Post by skymera on 2008-05-25
Root is like the C: in Windows.

It has everything. i have 10GB / and 2GB swap.

Although i've never ever touched the swap partition. Plus i have / and /home on the same partition.

---

### Post by x88a on 2008-05-25
> **skymera said:**
> Root is like the C: in Windows.

It has everything. i have 10GB / and 2GB swap.

Although i've never ever touched the swap partition. Plus i have / and /home on the same partition.

if root = C: in windows, then i would need more than 10GB, right?
if i install many programs, then 10GB wont be enough, correct?

---

### Post by housam on 2008-05-25
ubuntu will be installed on the root partitions.
reed this [[COLOR="Red"]_guide_[/COLOR]]("http://www.linuxsa.org.au/tips/disk-partitioning.html") to know more about partitions

---

### Post by bumanie on 2008-05-25
At a very basic level, the partition marked / is for the filesystem that instructs your computer how to interact with the hardware and other software on the computer. That is why it is good to have it separate, as if it mucks up somehow, you only have to reinstall to / to get a working system again and all your data in /home is safe.

---

### Post by x88a on 2008-05-25
> **housam said:**
> ubuntu will be installed on the root partitions.
reed this [[COLOR="Red"]_guide_[/COLOR]]("http://www.linuxsa.org.au/tips/disk-partitioning.html") to know more about partitions

ok, so just to double check that i understand what i read.
if i install a program (eg. Adobe Photoshop), it will go to root, correct?

---

### Post by housam on 2008-05-25
yes.

> **x88a said:**
> if root = C: in windows, then i would need more than 10GB, right?
if i install many programs, then 10GB wont be enough, correct?

You can create a root partition as large as you can .

Also I can sujest ( if you have more GB ) to create a ntfs partition to be used as date and can be accessed from both systems.
But you have to know that you only allowed to have 4 primary partitions on a single HDD or 3 primary + 1 extended partition which can be devided to many logical partitions 
how to do it ? read [[COLOR="Red"]_this guide _[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition").

---

### Post by x88a on 2008-05-25
so lets say i use 10GB for root now.
And in the future, i think 10GB isnt enough, i can use Gnome Partition Editor to resize all my Linux partitions, is that correct?

---

### Post by x88a on 2008-05-25
i looked at the manual partitioning option.
And i see many many different options.

They are:-
1. Ext3 journaling file system
2. Ext2 file system
3. ReiserFS journaling file system
4. JFS journaling file system
5. XFS journaling file system
6. FAT16 file system
7. FAT32 file system
8. ntfs
9. swap area

which of them is the home and root?
i am very confused
pls help.

TQTQTQ

---

### Post by housam on 2008-05-25
ext3 for the root and home ( this is the format type )
swap for the swap ( this is the format type )

( / ) is the sign for the root
(/home ) for home
( swap ) for swap

---

### Post by x88a on 2008-05-25
so what are the others like Ext2 and JFS?
can i just ignore them?

sorry for asking soo many questions.
this is my 1st Linux experience and i want ot be 100% sure.

TQ

---

### Post by housam on 2008-05-25
Try to make the partitions in this order 
root
/home
swap 
this is to facilitate ( in the future ) the resizing of the home partition and add more space to the root partition 
And I sujest to create them all inside an extended partition.

---

### Post by x88a on 2008-05-25
> **housam said:**
> Try to make the partitions in this order 
root
/home
swap 
this is to facilitate ( in the future ) the resizing of the home partition and add more space to the root partition 
And I sujest to create them all inside an extended partition.

sorry, i dont understand what you are trying to say.
The thing is, i dont see any /home option when i am at step 4 of the installation (partitioning).

---

### Post by housam on 2008-05-25
> **x88a said:**
> so what are the others like Ext2 and JFS?
can i just ignore them?

TQ

Yes you can just ignore them ,ext2 is an older version of ext3. I don't know about JFS maybe for another linux operating system.

And don't hesitate to ask , we are all here in the forum to help each other.

---

### Post by x88a on 2008-05-25
so after successfully installing Linux in D, how will my computer load when i turn it on?
will i get a menu to choose whether to load Windows or Linux?
if yes, how do i install this menu?

thank you

---

### Post by housam on 2008-05-25
Now you'll not have a D partition . but sda1 , sda2 , ,,
after rebooting you'll get a grub menu to choose which operating system to boot. this menu is installed by default with installing ubuntu.
this menu named Grub and it is the ubuntu boot looder and it overwrite the MBR ( master boot record ) of windows. 
after rebooting go for applecations >> accessories >> terminal 
type : 
```
sudo fdisk -l
```
where -l is a small L . you will see your new partition table

---

### Post by x88a on 2008-05-25
ic
ok, i have tried to install Ubuntu 8.04 using manual at step 4 (partition)
i chose 10GB as root
then there is some process with a bar loading.
then an error message appeared and the process failed.
What is wrong?
TQ

---

### Post by housam on 2008-05-25
Boot from Hardy live cd. then go for sys >> admin >> partition editor . take a screen shot for the image of G parted and post it please.

---

### Post by x88a on 2008-05-25
it is ok already.
i tried it again and it worked.
now i have another problem.
During the installation, it failed to install GRUB.
it says fatal error:(:(
pls help

tq

---

### Post by housam on 2008-05-25
Are still able to boot windows?
when rebooting , do you get a grub menu to select between operating systems ?

---

### Post by x88a on 2008-05-25
my windows loaded like normal
no grub menu

---

### Post by housam on 2008-05-25
Ok , you need now to reinstall grub :
but first we have to know in which partition is ubuntu.

Boot from the live cd and type in the terminal :
```
sudo fdisk -l
```
where -l is a small L and post the results

---

### Post by x88a on 2008-05-25
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd127d127

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        6315     9767520    f  W95 Ext'd (LBA)
/dev/sda3            6316        6442     1020127+  82  Linux swap / Solaris
/dev/sda4            6443        9729    26402827+  83  Linux
/dev/sda5            5100        6315     9767488+   7  HPFS/NTFS

i now have another problem
i have 40 GB in D
when i am in windows, i couldnt access D
so i reformatted D and i can only reformat 10GB
i have lost 30 GB :(:(:(:(

---

### Post by housam on 2008-05-25
Why you reformated D ? it is just windows can not detect them. there is a small software to be downloaded and installed through windows that will make your 30 GB visable.[[COLOR="Red"]_http://www.fs-driver.org/_[/COLOR]]("http://www.fs-driver.org/")

now from your partition table your ubuntu is in the partition [COLOR="Blue"]sda4[/COLOR]
that means grub should be in [COLOR="Blue"](h0,3)[/COLOR]
you'll follow the steps on [[COLOR="Red"]_this link _[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?#head-ec3e41291c7a5a7b61d7827299415204067765de")to install grub ( there are two ways to do that ) I hope one of them will work . 
If not we will check the CD ( please tell me from where you got it ).

---

### Post by x88a on 2008-05-25
i tried it 1 more time and the installation is successful
i am now a Linux user!!!!
YAYYY!!!!
all thnx 2 u
TQTQTQTQTQ

btw, do u know how to check how much free space i have in the HD allocated for Linux?

TTTQQQQQQ:):):):)

---

### Post by housam on 2008-05-25
Congratulations :guitar:

you can go for the system monitor ( someware in the system >> admin./pref. )it'll give you what you ask for

Housam

---

### Post by x88a on 2008-05-25
btw, Filesystem = root, right?

---

### Post by housam on 2008-05-25
yes

---

### Post by Andavane on 2008-06-03
> **housam said:**
> Boot from ubuntu live cd and go for sys.>> admin.>> partition editor. this is the partitioning tool . delete the D partition which will leave an unallocated space. then create 3 partitions for ubuntu
- 10 GB for the root ext3 format with the sign ( / )
- 1 GB swap partition
- the rest for /home ext3 format
 and during installation when it comes to the partitioning choose the manual way and assign  the root partition( / )
Dear housam
A friend has built me a PC with a 250 GB Hard drive.
He made one partition of 50 GB on which
he has installed Windows Vista Home Premium OEM Edition. This is for the rarer occasions when I need to something quickly like synching my diary, a thing I struggle with in Ubuntu.
The remaining 200 GB he has left for me to install Ubuntu, and I plan to install Hardy.
I shall use the method you mention here.
Now my query:
What would be the best divisions for me to use when doing this. 

> - 10 GB for the root ext3 format with the sign ( / )
Should I increase this a bit, and if so what is the best size?

Any more information i should consider?
I am not sure what RAM he has put there, but will check carefully before installing as I am not very familiar with Vista.

Regards

John

---

### Post by housam on 2008-06-03
> **Andavane said:**
> 
Now my query:
What would be the best divisions for me to use when doing this. 
Should I increase this a bit, and if so what is the best size?
Any more information i should consider?
I am not sure what RAM he has put there, but will check carefully before installing as I am not very familiar with Vista.

Dear John,
You can increase your root partition to be 15 -20 GB and create a swap partition of about 2 GB ( it'll be enough. )
you can create also a /home partition ext3 format with some 50  GB or more and another ntsf format partition for data ,music ,,etc.
the last partition can be accessed from both systems.
I suggest your partition table :
50 GB ntfs for vista primary
70 GB ntfs for data primary
80 GB extended for ubuntu and this can be divided to :
      20 GB ext3 for the root (/) logical
      2  GB swap for the swap logical
      58 GB ext3 for / home logical

Good luck

---

### Post by Andavane on 2008-06-03
> **housam said:**
> Dear John,
You can increase your root partition to be 15 -20 GB and create a swap partition of about 2 GB ( it'll be enough. )
you can create also a /home partition ext3 format with some 50  GB or more and another ntsf format partition for data ,music ,,etc.
the last partition can be accessed from both systems.
I suggest your partition table :
50 GB ntfs for vista primary
70 GB ntfs for data primary
80 GB extended for ubuntu and this can be divided to :
      20 GB ext3 for the root (/) logical
      2  GB swap for the swap logical
      58 GB ext3 for / home logical

Good luck
errr, thank you housam.
I do all this using the partition editor when booting from the cd, right?
This is probably a simple matter basically, but I'm not a person who naturally thinks about partitions and what-not. It's the sort of thing I guess I'd understand if I did it all the time, but once it's done I just get on with my tasks. :-|
I have ubuntu gutsy on my laptop and I can tune that in to the instructions here once I am underway, and can print out too.
If only there were a guide which showed one exACTly what to do.
Members say "read this guide" and I get lost as it teaches so many ins and outs, whilst never quite explaining what I need to know.
Would it benefit me to tune the laptop into a chat facility to call for some help if things get stuck underway, and if so what would be the recommended method as I only have gmail chat working here.
It would be  a miracle if this worked.
Thank you anyway. I can take a deep plunge and see.
I say this with trepidation as I tried to do the same on my laptop using gparted over a period spanning two days and it certainly didn't go right. So I ended up going for option 1 and just let it get on with it.
On this desktop I selected to let Ubuntu use the largest empty space available, and again let it get on with it, which is exactly what it did.
Thank you for your help.
best wishes
John

---

### Post by housam on 2008-06-03
> **Andavane said:**
>  I do all this using the partition editor when booting from the cd, right?
Yes , you can do all this with the partition editor on the live cd if you have an empty HDD or only windows on it. because if you have any ubuntu version on the HDD it will be mounted and will not allow Gparted to partition the HDD.and in this case you will have to unmount the ubuntu system or download Gparted and burn it to a cd to create a live cd of it to do the partitioning( personally I prefer this way ).

---

### Post by housam on 2008-06-03
Here is a guide for installing a dual boot ubuntu/windows:
[[COLOR="Red"]_http://www.psychocats.net/ubuntu/installing_[/COLOR]]("http://www.psychocats.net/ubuntu/installing")
In this site at the left side bar there are many useful links that will help you Knowing more about ubuntu.

---

### Post by Andavane on 2008-06-12
> **housam said:**
> Dear John,
You can increase your root partition to be 15 -20 GB and create a swap partition of about 2 GB ( it'll be enough. )
you can create also a /home partition ext3 format with some 50  GB or more and another ntsf format partition for data ,music ,,etc.
the last partition can be accessed from both systems.
I suggest your partition table :
50 GB ntfs for vista primary
70 GB ntfs for data primary
80 GB extended for ubuntu and this can be divided to :
      20 GB ext3 for the root (/) logical
      2  GB swap for the swap logical
      58 GB ext3 for / home logical

Good luck
Thank you.
Drive is now partitioned according to these suggestions.
Next step is to try "manual", trusting that something awkward does not occur during the process.

Regards
John

---

