---
title: "Partition matter"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by czgirb on 2012-06-10
What is the **difference (advantage/disadvantage)** between **having / and /swap in a one (same) partition** and **having it separately (different partition)**?
And **how to make it placed to be one (same) partition**?
Please guide me ...
**Thanx**

---

### Post by wilee-nilee on 2012-06-10
> **czgirb said:**
> What is the **difference (advantage/disadvantage)** between **having / and /swap in a one (same) partition** and **having it separately (different partition)**?
And **how to make it placed to be one (same) partition**?
Please guide me ...
**Thanx**

Do you mean the root=/ and swap in a extended partition?

The / and swap can only be in the same partition if it is a extended. 

The advantage of a extended partition is that it is not held by the primary type partitions in a mbr type HD setup. Four primaries or three and a extended.

---

### Post by czgirb on 2012-06-11
Currently, I wish to **dual-boot** (**w/o Wubi**) my **Vista** and **Ubuntu**.
A partition that I've planned is: (start from beginning of the disk)

If a **one (same)** partition is possible, I would like to use:
* C ... Primary ..................................... **NTFS** .... **70GB** for **Vista**
* What is it? "**/**"? **Primary** or **Logical** ... **Ext4** ..... **30GB** for **Ubuntu**
* D ... Logical ...................................... **NTFS** ..... the remaining for **Data**

If the **separate** is required, I will switch to below:
* C ... Primary ..................................... **NTFS** .... **70GB** for **Vista**
* What is it? "**/**"? **Primary or Logical** ... **Ext4** .... **30GB** for **Ubuntu**
* D ... Logical ...................................... **NTFS** .... the remaining for **Data**
* /swap .............................................. **Ext4** .... for **Ubuntu's Swap**

Please guide me ...

---

### Post by wilee-nilee on 2012-06-11
> **czgirb said:**
> Currently, I wish to **dual-boot** (**w/o Wubi**) my **Vista** and **Ubuntu**.
A partition that I've planned is: (start from beginning of the disk)

If a **one (same)** partition is possible, I would like to use:
* C ... Primary ..................................... **NTFS** .... **70GB** for **Vista**
* What is it? "**/**"? **Primary** or **Logical** ... **Ext4** ..... **30GB** for **Ubuntu**
* D ... Logical ...................................... **NTFS** ..... the remaining for **Data**

If the **separate** is required, I will switch to below:
* C ... Primary ..................................... **NTFS** .... **70GB** for **Vista**
* What is it? "**/**"? **Primary or Logical** ... **Ext4** .... **30GB** for **Ubuntu**
* D ... Logical ...................................... **NTFS** .... the remaining for **Data**
* /swap .............................................. **Ext4** .... for **Ubuntu's Swap**

Please guide me ...

So in linux C and D don't exist to be honest they are all sda1, or sda2, or sdXX many variations. It gets really confusing to have that be part of a discussion to get you set up. The XX notations are in lieu of a HD and a partition letter and number.

I would rather see a picture of the hard drive using gparted from a Ubuntu live cd, and to go from there.

I would rather keep it simple.

/   just means a mount point of the root partition, and can be a primary or if inside a extended it would be a logical.

---

### Post by carl4926 on 2012-06-11
/ = root or where the system is installed

Many also use 
/home = your user files and settings

Eg, one of my machines

```
/dev/sda1              63   122093999    61046968+   7  HPFS/NTFS/exFAT
/dev/sda2       122094000   128230829     3068415   82  Linux swap / Solaris
/dev/sda3   *   128230891   488392064   180080587    5  Extended
/dev/sda5       128230893   169196579    20482843+  83  Linux / 
/dev/sda6       169196643   312560639    71681998+  83  Linux /home
/dev/sda7       312560703   354763394    21101346   83  Linux /
/dev/sda8       354763458   488392064    66814303+  83  Linux /home

```

I have two installations of Linux on this machine
Windows in sda1

---

### Post by fantab on 2012-06-11
Assuming you have only one Hard Disk (dev/sda) I would suggest:
C: Primary NTFS - Vista- 50GB (50gb will be more than enough unless you install loads of other space devouring Software )
D: Primary NTFS - Shared DATA (between Vista and Ubuntu)
/dev/sda3 Primary EXT4 20-25GB '/' Ubuntu
/dev/sda4 Extended
/dev/sda5 Logical SWAP 2-4GB

EDIT: When you use Linux to partition your Hard Disk you will notice that there is no C: or D: instead you will see them as /dev/sda1 and /dev/sda2. 

'/' or '/home' are known as mountpoints they are used to tell the 'Installer' where to install System Files and User Files. During Installation of Ubuntu you will have to indicate the mountpoints. In my scheme above I did not indicated '/home' partition as you are planning to SHARE D: NTFS as your Data Partition. (Also NOTE that Ubuntu or Linux can see all your partitons but Windows will only see C: and D:  (NTFS Or FAT only) in your case because Windows is Linux Blind).

---

### Post by DingusFett on 2012-06-11
Ideally, you'd want (calling the HDD sda here)
sda1 - NTFS - 70GB - Windows C:\
sda2 - Ext4 - 30GB - Ubuntu / (root)
sda3 - NTFS - * - Data (say label in Windows as D:\)
sda4 - Ext4 - ~4GB - linux-swap

Personally I have a seperate HDD for Data, so use the 4th partition as Ubuntu /home. If you have hard drive limitations and a decent amount of RAM, you should be alright without a swap partition though.

---

### Post by wilee-nilee on 2012-06-11
[COLOR=White].[/COLOR]

---

### Post by czgirb on 2012-06-11
> **carl4926 said:**
> 
/ = root or where the system is installed
Many also use /home = your user files and settings


> **fantab said:**
> 
'/' or '/home' are known as mountpoints they are used to tell the 'Installer' where to install System Files and User Files. During Installation of Ubuntu you will have to indicate the mountpoints. In my scheme above I did not indicated '/home' partition as you are planning to SHARE D: NTFS as your Data Partition. (Also NOTE that Ubuntu or Linux can see all your partitons but Windows will only see C: and D:  (NTFS Or FAT only) in your case because Windows is Linux Blind).


> **DingusFett said:**
> 
sda1 - NTFS - 70GB - Windows C:\
sda2 - Ext4 - 30GB - Ubuntu / (root)
sda3 - NTFS - * - Data (say label in Windows as D:\)
sda4 - Ext4 - ~4GB - linux-swap
Personally I have a seperate HDD for Data, so use the 4th partition as Ubuntu /home. If you have hard drive limitations and a decent amount of RAM, you should be alright without a swap partition though.


SORRY ... I revised my statement:
Assumed 320GB = 297GB

If a **one (same)** partition is possible, I would like to use:
**sda1 ... 70GB NTFS **for** Vista **called**C**...............[B]Primary
sda2 ... [/B]**30GB Ext4 **for** Ubuntu **called**/home**...**Primary or **[B]Logical ???
sda3 ... [/B]**197GB NTFS **for** Data **called**D** ............. **Logical**

If the **separate** is required, I will switch to below:
**sda1 ... 70GB NTFS **for** Vista **called** "C" **...............[B] Primary
sda2 ... 5GB Ext4 [/B]for** Ubuntu **called** "/root" **.......**Primary/**[B]Logical ???
sda3 ... 25GB Ext4 [/B]for** Ubuntu **called** "/home" **...**Primary/Logical ???**[B]
sda4 ... 187GB NTFS [/B]for** Data **called** "D" **.............[B] Logical
sda5 ... 10GB Ext4 [/B]for** Ubuntu **called** "/swap"** ... **Logical**

Is the above statement is **RIGHT**? If yes, please describe the **advantage/disadvantage** of both partition
**Thank you**

---

### Post by carl4926 on 2012-06-11
```
sda1 70GB ntfs primary
sda2  2GB swap primary
sda3 (all the remaining space) Extended
sda5 20GB ext4 (for / )
sda6 100GB ext4 (for /home )
sda7 (all the remaining space) ntfs for  Data
```

Something like that
But you need to manually set the partition mount points etc.. in the installer
[http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10_go_advanced_partit.png](http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10_go_advanced_partit.png)

---

### Post by fantab on 2012-06-11
I am a bit confused as to what you mean by "one/same and separate", and my confusion stems from yours.

First of all, you seem confused about 'mountpoints' and SWAP. 

To Simplify lets say **SWAP** partition is an extension of your Memory (RAM). If and when your computer needs more memory it will use SWAP.  Considering that today RAM is big enough, more than 2GB easily, there is good probability that your computer will not hit SWAP. So a SWAP of about 2-4GB is more than enough. SWAP does not have a mountpoint, its is just Linux SWAP.

As pointed out to you earlier, mountpoint tells the installer which partition to use to install particular set of files. There are many but most common are "/boot", "/", and "/home". 
/boot------ is where your bootloader is installed. (Unless there is special requirement you don't need it).
/ ----------- is where your Ubuntu system files are installed.
/home ------------ is where the User DATA or your Documents, Pictures, Music, Video etc is installed. 

Assigning different mountpoints to different partitions is a matter of personal choice.

> **czgirb said:**
> If a **one (same)** partition is possible, I would like to use:
**sda1 ... 70GB NTFS **for** Vista **called**C**...............[B]Primary
sda2 ... [/B]**30GB Ext4 **for** Ubuntu **called**/home**...**Primary or **[B]Logical ???
sda3 ... [/B]**197GB NTFS **for** Data **called**D** ............. **Logical**

Here you have not mentioned SWAP. You need to create SWAP.

> **czgirb said:**
> If the **separate** is required, I will switch to below:
**sda1 ... 70GB NTFS **for** Vista **called** "C" **...............[B] Primary
sda2 ... 5GB Ext4 [/B]for** Ubuntu **called** "/root" **.......**Primary/**[B]Logical ???
sda3 ... 25GB Ext4 [/B]for** Ubuntu **called** "/home" **...**Primary/Logical ???**[B]
sda4 ... 187GB NTFS [/B]for** Data **called** "D" **.............[B] Logical
sda5 ... 10GB Ext4 [/B]for** Ubuntu **called** "/swap"** ... **Logical**

HERE you don't need "/root" but "/" partition. And since you can SHARE D: NTFS between Windows and Ubuntu I suggest that you don't need separate "/home". 

Since Windows can't see Linux Partitions, I suggest you keep Vista C: and D: right next to each other, /dev/sda1 [C:] and /dev/sda2 [D:], Both PRIMARY partitions.

Then create another Primary partition of about 20-25GB for Ubuntu "/" system files and user data. When a separate '/home' is not used User Data is created in / partition only.

I have the following Set up on my other Desktop:

50GB Primary NTFS Vista C: (/dev/sda1)
?GB    Primary NTFS DATA D: (/dev/sda2)
20GB Primary EXT4 '/' Ubuntu (dev/sda3)
4GB Extended (/dev/sda4)
4GB  Logical SWAP (/dev/sda5)

I hope this helps you.

Also when managing Partitions I use [**Gparted Live**]("http://gparted.sourceforge.net/livecd.php") and manage Hdd from Boot.

---

### Post by czgirb on 2012-06-11
> **fantab said:**
> 
I am a bit confused as to what you mean by "one/same and separate", and my confusion stems from yours.

SORRY for making everybody to be confused ... SORRY ... Maybe it was caused from my Ubuntu knowledge is un-sufficient
What I mean by **one/same** is ... all Ubuntu 12.04 is installed in **one** partition only (incld. SWAP) ... dunno how to call it.
What I mean by **separate** is ... in one HDD we have / and **/boot** and **/home** and **/swap** 

> **fantab said:**
> 
... simplify lets say **SWAP** partition is an extension of your Memory (RAM). If and when your computer needs more memory it will use SWAP.  Considering that today RAM is big enough, more than 2GB easily, there is good probability that your computer will not hit SWAP. So a SWAP of about 2-4GB is more than enough. SWAP does not have a mountpoint, its is just Linux SWAP.

Yup! My lappie has 2GB ... and increase it to 4GB is planned

> **fantab said:**
> 
/boot------ is where your bootloader is installed. (Unless there is special requirement you don't need it).
/ ----------- is where your Ubuntu system files are installed.
/home ------------ is where the User DATA or your Documents, Pictures, Music, Video etc is installed.
... HERE you don't need "/root" but "/" partition

What is /root ?

> **fantab said:**
> 
... Here you have not mentioned SWAP. You need to create SWAP.

As mentioned by you, "... today RAM is big enough, more than 2GB easily, there is good probability that your computer will not hit SWAP ... and currently was planned to add more RAM" that's why I do not put swap on it.

> **fantab said:**
> 
... since you can SHARE D: NTFS between Windows and Ubuntu I suggest that you don't need separate "/home".

OK! Thank you.

> **fantab said:**
> 
HERE you don't need "/root" but "/" partition
Since Windows can't see Linux Partitions, I suggest you keep Vista C: and D: right next to each other, /dev/sda1 [C:] and /dev/sda2 [D:], Both PRIMARY partitions.

Both of them are **PRIMARY** ??? Are you sure ???
Never done that ... will try! Thank you.

> **fantab said:**
> 
... when a separate '/home' is not used User Data is created in / partition only.

What it means ?? Don't understand !!

> **fantab said:**
> 
50GB Primary NTFS Vista C: (/dev/sda1)
?GB    Primary NTFS DATA D: (/dev/sda2)
20GB Primary EXT4 '/' Ubuntu (dev/sda3)
4GB Extended (/dev/sda4)
4GB  Logical SWAP (/dev/sda5)

**4GB Extended** ?? What is it ??

---

### Post by oldfred on 2012-06-11
One primary partition can be the extended which is just a container for many logical partitions. Swap is often installed to a logical just to not use the last primary partition and give some future flexibility.

Partitioning is very personal. I also find my own optimal partition plan is not so good a couple of years later. But I do not expect hard drives to last, so after a couple of years I have a new usually larger drive to repartition a new way.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
I think Herman also uses a swap file now also.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by fantab on 2012-06-11
> **czgirb said:**
> 
What I mean by **one/same** is ... all Ubuntu 12.04 is installed in **one** partition only (incld. SWAP) ... dunno how to call it.

> **czgirb said:**
> As mentioned by you, "... today RAM is big enough, more than 2GB easily,  there is good probability that your computer will not hit SWAP ... and  currently was planned to add more RAM" that's why I do not put swap on  it.

Okay. No you cannot have Only ONE partition including SWAP. SWAP has to be on a SEPARATE Partition. No matter how large or big your RAM is you still need SWAP, at least 2-4GB whether your computer uses it or not. We are being safe here.


> **czgirb said:**
> What it means ?? Don't understand !!

Your User DATA, like Documents, Pictures, Music, Videos are stored in /home, if you have /home partition. When you don't have /home partition then your User DATA is created or stored in "/" partition. In Windows the default is C: where your User DATA is stored along with your Vista System Files.

> **czgirb said:**
> **4GB Extended** ?? What is it ??

A Hard Disk can have ONLY FOUR Primary Partitions. If you need more than than 4 then you have a problem. To solve this we create an EXTENDED Partition instead of a fourth Primary Partition. The Extended Partition serves as a container within which you can create many (easily more than 4) Logical Partitions. In that way you can have your three primary partitions and say 4 more logical partitions which gives you Seven Partitions instead of only 4. 

Though Extended Partition is numbered as a separate partition it only serves as a container for Logical Partitions. If you create, say 100GB, Extended Partition then you have 100GB of Space to create your Logical Partitions like 25gb, 25gb, 25gb, 25gb or 20gb X 5, or 50GB X 2 , etc.

To be honest, in your case, you don't need an Extended Partition with a Logical SWAP. You can have SWAP as your fourth Primary. But in case, in future if  you need an additional Partition you cannot have one because of a 4 Primary Partitions only limitation. Having an Extended Partition will give you room to maneuverer. Also for you it will be good learning curve if you create an Extended Partition with a Logical SWAP.

I hope I am clear.

---

### Post by anewguy on 2012-06-12
It is possible to create a swap FILE in place of a swap PARTITION, in which case it would be within the system files - under the mount point of "/".  If you wish to do that instead we can provide more information.

The size of a swap partition or swap file is dependent on several things:

- is it a laptop or desktop
- how much actual memory do you actually have
- do you plan on using hibernate

Without those, it's not really possible to give you a good guide for swap size.

If you are just starting out, I would only create 2 linux partitions - one with the mount point of "/" and one for swap.  A seperate /home partition can help when doing an update of the OS or recovering the OS, but mainly just for storing data you don't want to lose across version updates/upgrades/clean installs.

I don't think there are the possible problem partition types (dynamic) associated with Windows 7 since you are using Windows Vista, but I have never been a Vista user so I can't guarantee that.

Before you actually go about changing partitions, be sure you run defrag a couple of times on the disk before hand.  This can help prevent (but no guarantee) data loss in Windows.

It would help greatly to know how your disk is currently partitioned.

And not to pick nits, but swap is actually not associated to a file system type, like the ext4 that has been shown in some of the posts.

So, to give you the best advice we can, please provide the following:

- a description of your current hardware and the amount of memory installed

- if you plan to use hibernation

- a printed list of the existing partitioning on your disk


Dave ;)

---

### Post by czgirb on 2012-06-12
So, is it means that:

If I just want to instal Vista and Ubuntu 12.04 only, my partition will be as follow:
**/dev/sda1 ... 50GB ... Primary NTFS for Vista** ... usually read by **Windows** as **C **drive[B]
/dev/sda2 ... ??GB ... Primary NTFS for Sharing Data[/B] ... usually read by **Windows **as **D **drive[B]
/dev/sda3 ... 20GB ... Primary EXT4 for Ubuntu ... "/"
/dev/sda4 ... 10GB ... Logical ......... for Ubuntu's SWAP[/B]
The above statement is **POSSIBLE**

But if I wish to instal Vista, Ubuntu 12.04, and 12.10, my partition will be as follow:
**/dev/sda1 ... 50GB ... Primary NTFS for Vista** ... usually read by **Windows **as** C **drive[B]
/dev/sda2 ... ??GB ... Primary NTFS for Sharing Data[/B] ... usually read by **Windows **as** D **drive[B]
/dev/sda3 ... 20GB ... Primary EXT4 for Ubuntu ... "/"
/dev/sda4 ... 20GB ... Extended ... reserve to install Ubuntu 12.10
/dev/sda5 ... 10GB ... Logical ...... for Ubuntu's SWAP[/B]
* is it possible to use 1-swap for 2-version of ubuntu ?????
The above statement is **POSSIBLE**

Is two statement above is **RIGHT** ?????

---

### Post by deadflowr on 2012-06-12
> **czgirb said:**
> So, is it means that:

If I just want to instal Vista and Ubuntu 12.04 only, my partition will be as follow:
**/dev/sda1 ... 50GB ... Primary NTFS for Vista** ... usually read by **Windows** as **C **drive[B]
/dev/sda2 ... ??GB ... Primary NTFS for Sharing Data[/B] ... usually read by **Windows **as **D **drive[B]
/dev/sda3 ... 20GB ... Primary EXT4 for Ubuntu ... "/"
/dev/sda4 ... 10GB ... Logical ......... for Ubuntu's SWAP[/B]
The above statement is **POSSIBLE**

But if I wish to instal Vista, Ubuntu 12.04, and 12.10, my partition will be as follow:
**/dev/sda1 ... 50GB ... Primary NTFS for Vista** ... usually read by **Windows **as** C **drive[B]
/dev/sda2 ... ??GB ... Primary NTFS for Sharing Data[/B] ... usually read by **Windows **as** D **drive[B]
/dev/sda3 ... 20GB ... Primary EXT4 for Ubuntu ... "/"
/dev/sda4 ... 20GB ... Extended ... reserve to install Ubuntu 12.10
/dev/sda5 ... 10GB ... Logical ...... for Ubuntu's SWAP[/B]
* is it possible to use 1-swap for 2-version of ubuntu ?????
The above statement is **POSSIBLE**

Is two statement above is **RIGHT** ?????

Well when thinking of Extended partition, don't think of them as drives themselves, but rather something more like a shell which will contain various logical partitions.
If I were to lay out what I mean the partition scheme would look like this 

/dev/sda
     sda1=Primary = allotted drive space
     sda2=primary = allotted drive space
     sda3=primary = allotted drive space
then sda4=Extended = Space which can be divided multiple times
now within the extended goes
     sda5=logical
     sda6=logical
and so on and so on.
It is important to note that even though the extended partition will read as having drive space, you can only utilize that space through logical partitions.

---

### Post by deadflowr on 2012-06-12
Forgot to answer the swap question, but yes it is possible to have one swap partition used by two and or more linux OS'.

---

### Post by anewguy on 2012-06-12
And remember - if it's a laptop and if you plan to use hibernate on it while running Ubuntu, then you will probably need a swap file size of twice your physical memory - at least that used to be the guideline IF you were planning on using hibernate, since all of memory is copied to disk plus control structures.

This may have changed, but it's the last I knew.  Normally with today's memory size swap doesn't have to be as large in proportion to main system memory - sometimes swap can be very small.  The recommendations I have seen here seem adequate unless you want to hibernate.

Someone else with more up-to-date knowledge on the disk (swap) space needed ratio to main memory can give you the facts.  I just wanted to bring it up since it is a laptop, if I read your posts correctly.  This would change the swap partition size requirements.

Dave ;)

---

### Post by czgirb on 2012-06-12
> **anewguy said:**
> 
And remember - if it's a laptop and if you plan to use hibernate on it while running Ubuntu, then you will probably need a swap file size of twice your physical memory ...


Yes! I remember I ever read an article, which said the same as you.
I remember ... I remember ... but, how can we know what mode our Ubuntu to be?

Everything is DEFAULT
* If I leave my lappie for an hour ... what mode my lappie will be?
* If I closed my lappie (morning) and I opened back at night ... what mode my lappie will be?

Thank you.

---

### Post by anewguy on 2012-06-12
I believe that depends on your power settings, but cuurently I can't check that as I don't have Ubuntu on my new laptop yet.

dave ;)

---

### Post by oldfred on 2012-06-12
My laptop goes into suspend which is not hibernate. But I usually close all programs and shutdown. 

Learned a long time ago leaving anything open may have  corruption later. And power failure or battery worn down may close abnormally and  corrupt file. At the least it would need fsck for Ubuntu or chkdsk in Windows.

---

### Post by anewguy on 2012-06-12
> **oldfred said:**
> My laptop goes into suspend which is not hibernate. But I usually close all programs and shutdown. 

Learned a long time ago leaving anything open may have  corruption later. And power failure or battery worn down may close abnormally and  corrupt file. At the least it would need fsck for Ubuntu or chkdsk in Windows.

I've got to remember that! Just my opinion, but I really don't see a reason for hibernation now anyway.  Today's PC's save things, shutdown and boot so much faster that I personally just don't see a need for it.  On my old laptop I never used it either.

Dave ;)

---

### Post by buzzingrobot on 2012-06-13
> **czgirb said:**
> What is the **difference (advantage/disadvantage)** between **having / and /swap in a one (same) partition** and **having it separately (different partition)**?
And **how to make it placed to be one (same) partition**?
Please guide me ...
**Thanx**


I'm assuming you're asking prior to an install, not about an existing system.

On a single disk?  None that I can think of.

If you are using more than one disk, then you need to use manual partitioning during the install, which will allow you to create your partitions as you wish. Unless you know you will be using swap space a great deal (unlikely these days)  I don't think it makes much difference where you put it.  If you will be using it a lot, put swap on a faster drive.

If you are, in fact, talking about an existing system, I can't think of any reason to move swap. If you only have one disk, you can't move it.

---

### Post by buzzingrobot on 2012-06-13
> **czgirb said:**
> 
What I mean by **one/same** is ... all Ubuntu 12.04 is installed in **one** partition only (incld. SWAP) ... dunno how to call it.
What I mean by **separate** is ... in one HDD we have / and **/boot** and **/home** and **/swap** 


With one HDD, those two scenarios amount to the same thing. 

 A filesystem in Linux is often described as a tree.  It is, but it helps if you think of the tree as upside down. The beginning is the "/" directory. All other directories and files are branches of "/". Things go from there with many, many directories branching out underneath "/". A filesystem and the directories in it have no pre-determined size.

Partitions are distinct  sections of your drive of specific pre-determined sizes. The filesystem resides in one or more partitions. They are "mapped" to those partitions.  The data outlining that is contained in a file that the system reads each time it boots.
 
Now, if you use more than one HDD, you can tell the partitioner during the install process to map a directory to a specific partition.  The jargon for this is "mount" because the system needs to "mount" a partition before it can do anything with it.

For example, I use multiple HDD's.  I have "/home" mounted on one HDD all by itself.

When you install Ubuntu on a single disk, and let it handle all the partitioning -- the default option -- it will create the entire filesystem on that HDD, beginning with "/". Swap will be there, too. (Technically, swap is not part of the filesystem, but just  space on the disk.  It is not mounted.)

If you choose to manually partition a single disk for Ubuntu,  you can,  if you wish, create separate partitions for "/home" or any other directory.  Unless you have a reason to tightly control how much space they use, I don't think there's an advantage in doing that.

If you do, in fact, need to use multiple HDD, you must use manual partitioning during the install.  The partitioner can't do that automatically.

> 
What is /root ?
In essence, it is the home directory of the root user.  It is part of the filesystem tree underneath "/'. "/" is often called "root", but it isn't.  Actually, I believe "/" has never been given a name; it's just "/". "/root" is an important system directory, not to be messed with idly.  (Linux inherited this quirk from Unix, along with the filesystem structure.)

Drives that use the architecture that began years ago with MSDOS can use a maximum of 4 Primary partitions.  However, you can create an "Extended Partition" and then create more than four partitions inside it. You don't need to worry about that unless you need to manually partition.

If you do need to manually partition, don't worry if it takes a few attempts to get it right. Map your partitions and the directories you want to mount on them on paper before you start.  If you have other files, etc.,  on the drive, those partitions will appear in the partitioner and you must be careful not to delete them. Also, if you install with a USB stick, the system sees it as an HDD and it will appear in the partitioner, too, as something like "/dev/sdc".  Don't mess with that, either

---

### Post by czgirb on 2012-06-18
yesterday, my friends give me a suggestion as follow:

> **/dev/sda1 - NTFS Primary** for **Vista (C drive)**
**/dev/sda2 - Extended** with **3 logical partition:**
*** sda5 - NTFS - Logical** for **Sharing Data (D drive)**
*** sda6 - /swap - Logical**
*** sda7 - Ext4 - Logical** for **Ubuntu "/"**
it's rather wired, cos the /swap was located before "/"
The above suggestion is farry differ from the one which I obtained from this forum:
> **/dev/sda1 - NTFS Primary** - for **Vista (C drive)**
**/dev/sda2 - NTFS Primary** - for **Data (D drive)**
**/dev/sda3 - Ext4 Primary** - for **Ubuntu "/"**
**/dev/sda4 - /swap** - for **Ubuntu's SWAP**
Would you mind to tell me, which one is better?
What is the advantage/disadvantage from both partition's structure?

---

### Post by carl4926 on 2012-06-18
It really doesn't matter

---

### Post by czgirb on 2012-06-18
> **carl4926 said:**
> It really doesn't matter

My lappie, out-of-the-box, installed with Vista and the availabkle partition was as follow:
> * C: 221GB ... NTFS Primary for Vista.
* D: 12GB ... Recovery Partition.
In order to install Ubuntu, now I wish to resize the C drive to be:
> /dev/sda1 - NTFS Primary for Vista (C drive)
/dev/sda2 - Extended with 3 logical partition:
* sda5 - NTFS - Logical for Sharing Data (D drive)
* sda6 - /swap - Logical
* sda7 - Ext4 - Logical for Ubuntu "/"
and 12GB Recovery Manager (remains untouched)... it should be sda8 (maybe)
Is it possible?

---

### Post by carl4926 on 2012-06-18
Depends
How much space is in use in Vista now?

You absolutely must backup important files. AND defrag windows.
I only ever shrink by half of the free space. So....
If you had 100GB free in Vista, I would only recommend you grab 50GB of that

Of course, other people may have a different opinion.

The recovery partition is probably sda2, but whatever it is now, will not change.

---

### Post by fantab on 2012-06-18
Also remember with some laptop makers the Recovery Partition will not work if you change the HDD partition Scheme. So I suggest you find out about that and if I am correct then be prepared to abdicate Recovery Option. 

Personally, I will never keep anything WINDOWS on a LOGICAL Partition. That is why I recommend Logical Partitions for Windows. 

> **/dev/sda1 - NTFS Primary** - for **Vista (C drive)**
**/dev/sda2 - NTFS Primary** - for **Data (D drive)**
**/dev/sda3 - Ext4 Primary** - for **Ubuntu "/"**
**/dev/sda4 - /swap** - for **Ubuntu's SWAP**This will not work because it does not take into account the recovery Partition. If Recovery Partition is taken into account it comes to 5 FIVE Primary Partitions and as explained earlier it will not work. 

Again what your friends suggest does not take into account the Recovery Partition. Are you planning on loosing Recovery Partition Completely?

If not then:
/dev/sda1 - NTFS - Primary - Win C:
/dev/sda2 - Recovery - Primary
/dev/sda3 - NTFS - Primary - Win D: or Shared DATA
/dev/sda4 - EXTENDED
/dev/sda5- EXT4 - Logical - / - ubuntu
/dev/sda6 - LINUX SWAP

Previously it mattered where you placed your SWAP Partition, but NOT anymore.

---

### Post by czgirb on 2012-06-18
SORRY! Maybe my english is not good. Let me try to explained again.

In my lappie, the default partition is:

> * C: 221GB ... NTFS Primary for Vista.
* D: 12GB ... Recovery Partition.

In order to install Ubuntu, I wish to resize the C drive only.
**The Recovery Manager partition remain untouch!**
And the C drive will be:

> 60GB NTFS Primary for Vista
136GB NTFS Logical for Data
20GB Ext4 for Ubuntu "/"
5GB /swap

If The Recovery Manager partition remain untouched, after changed partition will be as follow: (maybe)

> /dev/sda1 - 60GB NTFS Primary for Vista (C drive)
/dev/sda2 - Extended with 3 logical partition:
* sda5 - 136GB NTFS - Logical for Sharing Data (D drive)
* sda6 - 5GB /swap - Logical
* sda7 - 20GB Ext4 - Logical for Ubuntu "/"
* sda8 - 12GB NTFS - Logical for Recovery Manager

Is it allowed for having **NTFS partition** after **Ubuntu Partition**?

---

### Post by carl4926 on 2012-06-18
Your English is fine
But your understanding of partitioning is not.

To shrink Vista to 60GB is not realistic or advisable IMO.
Yes, you can have NTFS partitions after Linux file systems. The only requirement you need to meet is having a NTFS primary (which you do).

Honestly, I think you should consider either a clean install of Vista or just don't use windows.

---

### Post by oldfred on 2012-06-19
Your recovery will probably remain as a primary partition, but that does not change your partitions otherwise. The extended can be in the middle of two primary as the extended is really just another primary. But only the extended can hold additional logical partitions.

Vista does not shrink as well as other Windows. And all NTFS partitions work best with 30% free space. Linux partitions also need some free space but can get by with somewhat less. Linux also hides 5% to prevent system from locking up if all space is used.

Windows Disk Cleanup tool to houseclean
defrag at least twice
#Shrinking partitions generally better for NTFS with Windows tools
Windows Vista - partition your hard drive using Disk Management, if XP use Gparted since no built in tools.
25GB at an absolute minimum 
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by czgirb on 2012-06-19
> **carl4926 said:**
> 
Your English is fine
But your understanding of partitioning is not.

Thank you.
Yup! My Partitioning knowledge is very very poor
Thank you for your effort to understanding.

> **carl4926 said:**
>  To shrink Vista to 60GB is not realistic or advisable IMO. 
Why is not realistic or advisable?
Cos I had a friend, which operate Vista in 40GB disk space.

> **carl4926 said:**
>  Yes, you can have NTFS partitions after Linux file systems. The only requirement you need to meet is having a NTFS primary (which you do). 
If it allowed for having NTFS partitions after Linux file system.
What about:
sda1 ... 60GB NTFS Primary Vista's "C"
sda2 ... Extended
* sda5 ... 20GB Ext4 ... Ubuntu's "/"
* sda6 ... 5GB /swap
* sda7 ... 134GB NTFS ... Sharing Data "D"
* sda8 ... 12GB NTFS ... Recovery Partition "E"

>  Honestly, I think you should consider either a clean install of Vista or just don't use windows. 
At first, maybe! But know, NO! Cos my Ubuntu's knowledge is very very poor. I have NO gut to leave Windows 100%.
There are so much I should learned about Ubuntu.

---

### Post by carl4926 on 2012-06-19
> Why is not realistic or advisable?
Cos I had a friend, which operate Vista in 40GB disk space.

Because windows currently uses so much more than that. And it spreads it's files all over that space, hence the advice to backup and defrag.

Why not just keep windows bigger, forget the extra data partition and set some space aside for that data.

Shrink windows to 100GB and use the rest for Ubuntu

---

### Post by oldfred on 2012-06-19
While carl4926 is correct on the way Windows works and its need for lots of space, it still is better to have a shared NTFS partition for any data you may want to use in both systems. Windows does not like too much writing into its system partition and LInux exposes all the hidden files & folders that Windows normally hides. That can lead to major errors which I have done even in Windows as I usually unhide them in Windows.

With XP I only had a 20GB shared NTFS partition for photos, Firefox profile & Thunderbird profile. Then my Picasa, Firefox & Thunderbird in either system had the same data.

---

### Post by czgirb on 2012-06-27
> **carl4926 said:**
> 
Honestly, I think you should consider either a clean install of Vista or just don't use windows.


I heard you Carl4926!

Default Partition:
[B]* 237GB ... for Vista ... known as C:
* 012GB ... for Recover ... known as D:[/B]
Today I make partition as follow:
[B]* sda1 ... 20GB ... Primary ... /
* sda3 ... 10GB ... swap
* sda4 ... 207GB ... Primary ... /home
* unallocated ... 1MB
* sda2 ... 12GB ... Recovery (remain untouched ... default)
* unallocated ... 3MB[/B]
Is it right?

If in **"Windows Explorer"** (*it should be called **Nautilus**, right?*) I put some files there, it should be placed in sda5 (/home), right? So ... if I want to upgrade 12.04 to 12.10, the upgarde only affect the sda1 (/) only, right?

I remember I used all left size for /home, but why there will be unallocated space 1MB?

---

### Post by czgirb on 2012-06-27
Somebody ... please help

---

### Post by oldfred on 2012-06-27
You were closer back in post 31.

You should have Vista in sda1 and all the Ubuntu partitions  in the extended  which can be either sda2 or sda3, recovery in whatever it is sda4?. All logical partitions then in the extended start at sda5, so / is sda5 and so forth.

---

### Post by czgirb on 2012-06-27
> **oldfred said:**
> You were closer back in post 31.

You should have Vista in sda1 and all the Ubuntu partitions  in the extended  which can be either sda2 or sda3, recovery in whatever it is sda4?. All logical partitions then in the extended start at sda5, so / is sda5 and so forth.

Sorry! **oldfred**,
**Vista partition was erased!**
Now, regarding to **/home** ... what it should be?
**Primary** or **Logical**?

As ask previously, if I download a file, by default, it was stored under **Downloads** section within Nautilus ... is it means that the file was placed on **/home/Downloads/**? And if I installed the other OS to replace my Ubuntu, it will stored in **/** and would affect **/home**, right?
If so, today I downloaded **82MB**, but when I opened **GParted**, it said **/home** was filled by **3GB**? What is the other **2GB+**?

---

### Post by oldfred on 2012-06-27
/home has two purposes. One is all your user settings for each user( Linux is multiuser so each user may have different settings). And a place for each user to store his own data. My /home is between 1 & 2GB but the vast majority is .wine and the rest system settings. I move all data to other partitions, one NTFS for sharing data with Windows and the other Linux for almost all my new data, but that is more advanced.

Most of the user settings are hidden but can be seen by changing the view in Nautilus. Firefox & Thunderbird by default save settings & data in hidden folders in /home as to almost all applications as well as Ubuntu's internal settings

/home can be primary or logical. All Linux partitions can be either. Windows and a few other systems require primary partitions to boot from or install to, so I like to reserve one or two primary partitions just for future use, but for most users it really does not matter.

---

