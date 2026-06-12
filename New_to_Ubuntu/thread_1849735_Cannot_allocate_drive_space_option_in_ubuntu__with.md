---
title: "Cannot allocate drive space option in ubuntu  with dynamic partitions windows7"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by sivacharan on 2011-09-25
hello friends ,

       i have 250gb hard disk in my notebook with windows 7,which has 4 parittions,
(1) 100mb reserved for windows7
(2)25gb for windows7
(3)25gb partitions for installing ubuntu(this is again shrinked to 2 volmues as 3gb ,and the remaining as unallocated space.I want to istall ubuntu in this unallocated space)
(4)and the remainging is for my data

now i am trying ti install ubuntu 11.04 from cd ,"when i am at the allocating drive space" option ,it is showing as 4 partitions,whose sizes are not same as i partitioned in windows7.it is showing the partitions as ,i will come from last,

(4)sda4 (**file system is ntfs**)  whose size is around 223gb
(3)sda3 (**file system is ntfs**)  whose size is around 26 gb
(2,1)for sda2 and sda1 i am unable to recall those partition sizes

now the question is which partition do i need choose for ubuntu installation.
if choose the the 26gb partition,if it is windows7,i loose my winodws7 os,
if i choose 226gb partition i loose my data.
so how to fild the unllocated space to install ubuntu.

please help me..........

---

### Post by MG&amp;TL on 2011-09-25
Are you choosing the 'manually select partitions' option, or the 'install alongside' option. I suggest that you probably need to partition manually. Don't worry, it's not as scary as it looks, just have a Backup FIRST.

Here's the official guide: but there are many on the web.

[https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning](https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning)

Am I reading what you're saying correctly?

---

### Post by sivacharan on 2011-09-25
let me try again and after that i can say my problem in a cleaner way.but for now the problem is "i am unable to find the unallocated space which i reserved for ubuntu installation"

---

### Post by sivacharan on 2011-09-25
one more thing is i am unable to find the "install alongside option".it is showing only two options 

(1)to clean windows7
(2)something else

is there in problem with my os it is general for ubuntu11.04

---

### Post by Elfy on 2011-09-25
something else - is the manual option now. You'll need to use that if you want to specify previously created partitions

Bit confused with your description of the partitions - can you either post a screenshot from gparted or run 

```
sudo fdisk -l
```

from a terminal and copy that here

---

### Post by sivacharan on 2011-09-25
is it possible to take the screen shot at installation time,being beginner of linux i don't know how to do that

---

### Post by MG&amp;TL on 2011-09-25
For a screenshot, boot into windows and find the partition manager. Then post screenshot of partitions.

Choose 'something else' at partition menu, then follow instructions in link. If you only have one computer, you may need to write it down or something first.

---

### Post by Blasphemist on 2011-09-25
When you boot the live cd choose try ubuntu. Then connect to the internet and come to these forums. 

You can then open a terminal and run the command that forestpiskie posted and post the results back here. You can take a screen shot and I believe all you'll have to do is press print screen and save the picture. The picture will not be available after a reboot though.

---

### Post by sivacharan on 2011-09-25
let me try to give a better explanation for this

in my windows i have 4 partitions they are

(1) c drive(24.32gb,in which used space is 15270mb)---this is where my windows7 is installed
(2) e drive(184.gb,in which used space is 62820mb)---this is where all my data is present
(3) g drive(99.9mb)---this reserved partition for windows7
(4) h drive(25gb)----this is where i want to install ubuntu

_h drive_:to install ubuntu i shrunk the volume of h drive.and now th eh drive has 3.05 gb and the remaining is unallocated space.so now the h drive become

(4) h drive(3.05gb,in which used space is 90mb)

in this unallocated space i want to install ubuntu.is it possible?????
  because if i install ubuntu in c drive i will loose windows7 if i install in e drive i will loose my data.
  So to install ubuntu i started with ubuntu cd.

till the "allocate drive space" everything is ok.in this "allocate drive space " i am very much confused.because ubuntu is showing that there are 4 partitions but those 4 partitions sizes are not same as the partitionsin windows,ther are completely different.the partitions that ubuntu is showing are 

(1) /dev/sda1------this partition size is 1mb
(2) /dev/sda2/-----this is partition size is 104mb.
(3) /dev/sda3/-----this partition size is 26109mb(in which used is 3221mb)
(4) /dev/sda4/-----this partition size is 223842mb(in which i used 67457mb)
    this is why i am confusing ubuntu is showing the different partition sizes
   if now i want install ubuntu which partition do i need to use.
if i choose,becase ubuntu needs alteast 5gb,/dev/sda3,if in that space windows7 is installed becase it is already used 3221mb,as i said i loose it,or if i select /dev/sda4,as it is clearly showing that there is 67457mb used space i.e data i loose all my data.so now which partition do i need to choose for ubuntu installation

             thanks for your reply.........

---

### Post by sivacharan on 2011-09-25
let me try to give a better explanation for this

in my windows i have 4 partitions they are

(1) c drive(24.32gb,in which used space is 15270mb)---this is where my windows7 is installed
(2) e drive(184.gb,in which used space is 62820mb)---this is where all my data is present
(3) g drive(99.9mb)---this reserved partition for windows7
(4) h drive(25gb)----this is where i want to install ubuntu

_h drive_:to install ubuntu i shrunk the volume of h drive.and now th eh drive has 3.05 gb and the remaining is unallocated space.so now the h drive become

(4) h drive(3.05gb,in which used space is 90mb)

in this unallocated space i want to install ubuntu.is it possible?????
  because if i install ubuntu in c drive i will loose windows7 if i install in e drive i will loose my data.
  So to install ubuntu i started with ubuntu cd.

till the "allocate drive space" everything is ok.in this "allocate drive space " i am very much confused.because ubuntu is showing that there are 4 partitions but those 4 partitions sizes are not same as the partitionsin windows,ther are completely different.the partitions that ubuntu is showing are 

(1) /dev/sda1------this partition size is 1mb
(2) /dev/sda2/-----this is partition size is 104mb.
(3) /dev/sda3/-----this partition size is 26109mb(in which used is 3221mb)
(4) /dev/sda4/-----this partition size is 223842mb(in which i used 67457mb)
    this is why i am confusing ubuntu is showing the different partition sizes
   if now i want install ubuntu which partition do i need to use.
if i choose,becase ubuntu needs alteast 5gb,/dev/sda3,if in that space windows7 is installed becase it is already used 3221mb,as i said i loose it,or if i select /dev/sda4,as it is clearly showing that there is 67457mb used space i.e data i loose all my data.so now which partition do i need to choose for ubuntu installation

             thanks for your reply.........

---

### Post by Elfy on 2011-09-25
There's a button on your keyboard somewhere - PrtScn, that would get you a screenshot.

I suspect you've got dynamic disks or something not 'normal' - or at least normal to me.

You would certainly appear to have more than 4 partitions - with none appearing to be extended. 

You will need to deal with that before you can install ubuntu - it won't afaik install to dynamic disks


[http://ubuntuforums.org/showpost.php?p=10112642&postcount=11](http://ubuntuforums.org/showpost.php?p=10112642&postcount=11)

---

### Post by Mark Phelps on 2011-09-25
Unless you use Wubi, you can't install using ANY of those partitions.  The installer is not showing you the side-by-side option because you already have the maximum number of allowed primary partitions - 4.

And do NOT use the Win7 Disk Management utility to shrink an existing partition and create another one.  Doing so will force the conversion of your partitions into Dynamic Disks -- something that Ubuntu can't use and more problems for you.

---

### Post by oldos2er on 2011-09-25
Post merged. Please don't start more than one thread per topic.

---

### Post by Blasphemist on 2011-09-25
To me the main thing is that you shouldn't prepare your partitions in windows for ubuntu as it can be confusing. See my screen shot from GParted in Ubuntu. I know, I have a bunch of partitions but compare this to what you see in windows disk management. Please use GParted or other linux methods as have been described to let us see your partition details. Another option would be to boot the live cd of ubuntu and use bootinfoscript to give us a boot information summary. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sarwiz on 2011-09-25
First, backup ALL your data on all your drives. Then, using a Gparted disc, restart your computer and shrink the sda4 down about 30 g  (leaving it at about 190g) and make that unallocated space. Remove disc, restart into windows and let win7 do its disccheck, etc, and rebuild it's tables. (Might have to restart a couple of times) Now you have a 30 gig partition to install Ubuntu. You would make that a boot partition for ubuntu (mount as /). Don't do anything until you Backup your data

---

### Post by dino99 on 2011-09-25
my way:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

note: first boot on windoz and clean it (ccleaner is helpfull), defrag it, then shrink the unnecessary partition(s) to make room for ubuntu. Remember that the number of primary partition cant be greater than 4, so limit them to 3 and add an extented partition where you'll be able to create the other partitions you need.

---

### Post by sivacharan on 2011-09-25
here is my windows7 disk partition printscreen,can you please tell me where is the wrong going on???

*****one more thing is when i am trying to "try ubuntu" is not goin g to the next step,it is keep on showing a rounded circle image as it represents "process going on message".why am i not going to next step after clicking on "try ubunu".is there any problem in windows partition????????

---

### Post by sivacharan on 2011-09-25
i am unable to move forward alfter clicking on the "try ubuntu" option.what could be the problem

---

### Post by Blasphemist on 2011-09-25
OK, a couple things I can help with and one that I can't yet. You may be having a video issue that is keeping you from being able to run the try ubuntu option. Since you apparently can get into the install directly but not the live session, that is probably it. More on that later. 

I'd delete the partition you have for Ubuntu from windows disk management. Then during the ubuntu installation process you should get an option to use available space. If that works, the installation will create the / and swap partitions in that space which is I believe what you have been trying to do.

This may not work and here is the issue that I don't know about. As you can see your partition types show as dynamic in windows. I'd be interested to know how they show in ubuntu but you'd have to be able to run the try ubuntu option or look at them in the allocate disk space screen during the installation. You'd get to that during the install by choosing "something else" to manually allocate disk space.

As for the video issue in try ubuntu, try setting boot parameters from the initial grub screen when booting the cd. I'd try nomodeset first but you may need to try others. The screen will direct you on how to do that.

---

### Post by sivacharan on 2011-09-26
hello friends,

      I have windows7 on my dynamic disk.now i want to install ubuntu alongside windows.
      please check the screen shot of windows 7 partitions which is given below.there at the widows partition pepresentation place,on the left most side you can find disk-0,which is of dynamic type.i wnat to install ubuntu in that ubuntu(h - drive) volume.but i am unable that because at the time of installation ubuntu is not recognizing that H-drive that may be because of this dynamic disk problem.
       what is a dynamic disk or dynamic disk.as far as i know it is a storage in wchich we can store data and we can create new voumes,delete volumes or change volumes without rebooting the computer.      
       when ever i am trying to convert the disk to basic it is showing an error that disk is not empty.can't i install ubuntu on a dynamic disk.to install ubuntu is basic disk compulsary.if so what do i need to do now??

---

### Post by sivacharan on 2011-09-26
can't we make basic type disk at the time of windows7 installation

---

### Post by sivacharan on 2011-09-26
can you please check out this.I used "diskpart" to get the details of my hard disk.but i am surprised after getting the results.please check the attachments that i attached to this 
in these first one is about my hard disk partitions and volumes and the second one is disk management screen shot of my current hard disk

just check out this,when i used list disk it is show showing only one disk which is disk-0
after that i selected disk-0 with this command

select disk=0

then i tried to get all the partitions with this command,

"list partition"
then it gave the following result

partition       type                size         offset
---------------------------------------------------------
partition1     dynamic data         992kb         31kb
partition2     dynamic data         100mb         1024kb
partition3     dynamic data         24gb          101mb
partition4     dynamic data         208gb         24gb

these are not same as that of the partition or volumes in second image.

then i tried to get the list of volumes with this command,
"list volume"
then the result was

volume    ltr   label    fs     type     size     status     info
-----------------------------------------------------------------
volume0    H    UBUNTU   NTFS   simple   24gb     healthy
volume1    E    DATA     NTFS   simple   184gb    healthy
volume2    C    WINDOWS  NTFS   simple   24gb     healthy    boot
volume3    G    SYSTEM   NTFS   simple   100mb    healthy    syst
volume4    F                    dvd-rom  0b       no media


as far as i know partitions and volumes are same in windows7 ,then why it is showing differently here
why all my volumes are showing dynamic thougn i didn't give dynamic or basic at the time installation.

can't we change the volume0 to basic type for ubuntu installation.
can we assign disk type as dynamic or basic at the time of windows 7 installation
can i change my disk type to basic now

why ubuntu is not reading the dynamic type disk

please help me.........

---

### Post by sivacharan on 2011-09-26
can you please check reply,can't i change any of my volume as basic for ubuntu installation.doesn't ubunut install on dynamic disk,do i need to reinstall my windows7 ,if so can i assign my my disk type to basci at the time of installation

---

### Post by Blasphemist on 2011-09-26
I'm doing some research and I'm starting here. [http://msdn.microsoft.com/en-us/library/windows/desktop/aa363785(v=vs.85).aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa363785(v=vs.85).aspx)

---

### Post by Blasphemist on 2011-09-26
Mark Phelps wrote earlier in this thread that creating a partition from Win 7 disk management can cause a conversion to dynamic disks. This would explain how this could happen, and it sounds like that is how you prepared the disk for Linux. It does look to me like win 7 defaults to basic at installation. It is possible that the OEM configured for dynamic disk.

I can't find an easy way to convert back to basic and it doesn't appear that Linux supports dynamic disks. I did find this non-free software ($30)that seems to be able to do the conversion.  [http://www.dynamic-disk.com/windows-7-convert-dynamic-disk-to-basic.html](http://www.dynamic-disk.com/windows-7-convert-dynamic-disk-to-basic.html)

You could copy your data to another media or create a backup, erase everything including partition tables and all and then re-install everything. This time using Ubuntu tools (GParted from the live cd) to do your partitioning for Linux. How to best proceed on this largely depends on windows current health, what you have installed in windows and it's mission criticality.

I learned more about dynamic disks but my research wasn't exhaustive so don't take this as the only options for you.

---

### Post by sivacharan on 2011-09-26
i too tried this
[http://www.easeus.com/download.htm(in](http://www.easeus.com/download.htm(in) this home addition is free and the rest are commercial)
but no use.this allows to select the option that to convert the dynamic disk to basic disk.but when it chages the c: partition i mean when it tries to convert the windows partition from dynamic to basic it raises an error the "if the process continues there would be boot problem".so now i am  also thinking for reinstallation.

---

### Post by sivacharan on 2011-09-26
in my 250 gb hard disk 232 gb is available for me.
first at the time of installation if i create a 25 gb drive and in that i intall windows7 what could be the type of my disk ???basic or dynamic?????????

---

### Post by westie457 on 2011-09-26
If this links is truthful it can be done for nothing through Windows. [http://www.techrepublic.com/article/revert-dynamic-disks-to-basic-disks-in-windows/6093291](http://www.techrepublic.com/article/revert-dynamic-disks-to-basic-disks-in-windows/6093291)

---

### Post by Blasphemist on 2011-09-26
Basic is what you want. Are you asking what will windows create? The answer as best I can tell is also basic, as the default.

As for the link above, it starts off sounding promising until you realize it demands you are not running windows from that disk.
> The steps I listed above are fairly easy…unless you’re trying tomove your system volume off a dynamic disk. In that case, simply moving dataisn’t going to do the trick. Instead, take a full system backup before you getstarted. Then, you’re in for a complete reinstall of the operating systemduring which you need to remove all of the existing volumes on the dynamicdisk.

---

### Post by oldos2er on 2011-09-26
You already have a thread opened for this issue here: [http://ubuntuforums.org/showthread.php?t=1849735](http://ubuntuforums.org/showthread.php?t=1849735), please don't start new ones.

---

### Post by oldfred on 2011-09-26
I merged threads & edited title so you will not get two sets of instructions.

Only wubi will  install to a NTFS partition. It is much better to only use Windows partition tools to shrink Windows 7 and use gparted or the installer to create partitions for Ubuntu.This works best if you have not really used the dynamic partitions and the underlying physical partition is still the same as the dynamic partition. If you have not used the new partition and it has not data, delete it before converting.

You may be able to convert from dynamic to basic without having to reinstall but please have good backups as this does not always work. Microsoft's official policy is to backup, delete everything, create new basic partition and restore data.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)

One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

---

