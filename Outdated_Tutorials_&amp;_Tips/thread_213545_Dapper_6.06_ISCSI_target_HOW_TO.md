---
title: "Dapper 6.06 ISCSI target HOW TO"
date: 2006-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by iduriduridur on 2006-07-11
This is for a clean install, since ISCSI is a task intensive process. It will use ISCSI enterprise target software from 

[http://iscsitarget.sourceforge.net/](http://iscsitarget.sourceforge.net/)

version iscsitarget-0.4.13.tar.gz. download it to your desktop. 
unarchive it to a folder on your desktop.

You will need 2 disk drives,  say /dev/hda for ubuntu OS

and /dev/sda for iscsi data 

first install dapper
then login and update the normal Software updates way. 

reboot because of the kernel update.

go to synaptic and install

**make**
**libssl-dev**
**linux-headers-2.6.15-26-386** - do a uname -r to make sure what you are running. 
**gcc**

install

then get a terminal window up and do sudo su to be root.
type:
ln -s /usr/src/linux-headers-2.6.15-26-386 /usr/src/linux

cd to your desktop iscsi folder you created previously from unarchiving
Example:
cd /home/user/Desktop/iscsi

make KERNELSRC=/usr/src/linux

then I had to type:

make KERNELSRC=/usr/src/linux install

Not exactly sure why i needed to do the make part 2x but it works

cp /home/user/Desktop/iscsi/etc/ietd.conf /etc

It is now installed. But we need to setup the ietd.conf file

vi /etc/ietd.conf

go to the line that says Lun 0 Path=

edit it to point to your iSCSI disk.

Lun 0 Path=/dev/sda

save

/etc/init.d/iscsi-target start

It should say:

Starting iSCSI enterprise target service: succeeded.

Now get the IP address of your box, install MS iscsi initiator free download and test away. 

I have an athlon 64 3000+ and 2 gb ram IDE disks, 1 Gig Ethernet with a crossover cable , jumbo frames set on both NICS to an XP box same specs and got 30-40 MBps on IDE and on a unbuntu ram disk i got 70MBps max. It seems on a 1 Gig ethernet the network is the limiting factor. 

Now i need to buy 4 PCI express gig nics from Dlink and bond them together to see what i can get. 

I have tested this in a VMWARE server session and it works but it is slow since it is a vm and no jumbo Frames as far as i can tell. :D

---

### Post by si285 on 2006-08-16
Hi,
I'm trying to install thie iscsi target but have problems when I follow the instructions here.

The problems start when I issue the command  

sudo make KERNELSRC=/usr/src/linux

Here is the output with error 

make -C usr
make[1]: Entering directory `/home/adam/Desktop/iscsi/usr'
cc -O2 -fno-inline -Wall -Wstrict-prototypes -g -I../include   -c -o ietd.o ietd.c
make[1]: cc: Command not found
make[1]: *** [ietd.o] Error 127
make[1]: Leaving directory `/home/adam/Desktop/iscsi/usr'
make: *** [progs] Error 2


I'm using a fresh install of Ubuntu 6.06.1 and installed 
make
libssl-dev
linux-headers-2.6.15-26-386 
gcc  -- I used gcc4 since it did not specify which version...

I must be missing something simple (or maybe not)...

Any help would be greatly appreciated

Thanks

---

### Post by iduriduridur on 2006-08-18
When you go to synaptic package manager choose to install 


gcc 

It will install these as dependencies. 

binutils
cpp
cpp-4.0
gcc-4.0


Yoiu can't just pick gcc-4.0 it leaves out gcc

hence you get this error. 

make[1]: [COLOR="Red"]**cc**[/COLOR]: Command not found



This should fix you up.

---

### Post by christhemonkey on 2006-08-18
<offtopic>ISCSI being?
Googling wouldnt tell me anything useful.
</offtopic>


EDIT: Should have searched more carefully, to answer my own question:
> iSCSI

(Internet SCSI) A protocol that serializes SCSI commands and converts them to TCP/IP


---

### Post by si285 on 2006-08-18
Boy do I feel stupid. but hey, I'm learning Ubuntu...

You got me "on-track", I followed the rest of your instructions and it worked perfectly.

Thank you so very much for your help!!!!

---

### Post by iduriduridur on 2006-08-18
Glad you got it working. 

What can ISCSI be used for?
I needed an ISCSI target to test a Windows cluster. It is also useful in MS Exchange situations :( It is used in large storage SAN environments. Anywhere you would need to add storage to a box but don't want to add a physical drive to it. Just install an ISCSI initiator and point it at the iscsi target and you have disks.

---

### Post by EmmEff on 2006-10-02
Here's minor update in the installation procedure that makes things a little simpler.

First off, to install the correct version of linux-headers for the currently booted kernel, do the following:

```
sudo apt-get install linux-headers-`uname -r`
```

Next, configure the symlink into the kernel source tree:

```
sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
```

Using this symlink instead of the suggested symlink means the KERNELSRC parameter to make isn't necessary.  From the top of the iscsitarget source tree, simply do the following:

```
make
make install

```

Following these steps keeps the installation procedure kernel version agnostic.

---

### Post by Yyrkoon on 2006-11-19
A little off topic, sorry:

Does anyone know what would be involved bonding NICs in Linux, and Windows for such a case ? I know that Linux can do it via software with two NICs, but AFAIK, in Windows, you would either need 802.11-a/d hardware (NICs, and a switch), or some sort of software that I'm un-aware of. nVidia DualNet does not offer true 802.11 link aggregation(outgoing packets only). At least, this is what I've been led to believe after about a weeks worth of "research".

I'm very interrested in iSCSI, have been for close to a year, the only thing that had me set back, was the "network speed issue". Although I dont own such, I'm under the impresion that Intel Pro cards have drivers/software to do 802.11 link aggregation in Windows, but this is what I've read, and have no personal experience.

iSCSI is deffinatly a very interresting technology, and now that it's possible my Favorite Linux Distro (Debian), I'm starting to get that Ole experimentation "tingle" all over again :)

---

### Post by iduriduridur on 2006-12-07
Intel Pro 1000 cards are the easist to bond in both Windows and linux boxes. I have 2 Intel pro 1000 PCI Express cards. They work well but bonding them together just gave me redundancy not a faster disk read and write for iscsi. I may not have it all figured out but here is a good writeup of nic bonding. 


[http://linux-ip.net/html/ether-bonding.html]("http://linux-ip.net/html/ether-bonding.html")

---

### Post by Yyrkoon on 2006-12-11
> **iduriduridur said:**
> Intel Pro 1000 cards are the easist to bond in both Windows and linux boxes. I have 2 Intel pro 1000 PCI Express cards. They work well but bonding them together just gave me redundancy not a faster disk read and write for iscsi. I may not have it all figured out but here is a good writeup of nic bonding. 


[http://linux-ip.net/html/ether-bonding.html]("http://linux-ip.net/html/ether-bonding.html")
Sounds like you set up for fail over instead, I've read A LOT on ethernet bonding, and I've probably read that same exact page (more than once). The thing is, once I learned that ethernet channel bonding would only work for Linux to Linux (peer to peer), I gave up on it for a while. I've since been told that you could do Linux->Windows if you had a switch that supported 802.3ad link aggregation.

For bonding of two machines, wouldnt you need 4 cards, and a switch for link aggregation ? I said 802.11 a/d in my first post, sorry, was tired (and I'm already a bit forgetful . . .) I actually mean 802.3ad. Anyhow, anyone have an idea of what exactly it would take to get link aggregation working between Linux, and windows ?

[EDIT]

Oh, and iduriduridur, I was actually considering the dual port PT cards in that same family :)

---

### Post by iduriduridur on 2006-12-17
I have 2 Intel pcie cards, one builtin nic on my isci inititiator and

on of these  smc switches

[http://www.smc.com/index.cfm?event=viewLargeImage&localeCode=EN_USA&pid=1485]("http://www.smc.com/index.cfm?event=viewLargeImage&localeCode=EN_USA&pid=1485")

I wish i would have bought a Dell they are cheap 

[http://www.dell.com/content/products/compare.aspx/small_workgroup_gig?c=us&cs=04&l=en&s=bsd]("http://www.dell.com/content/products/compare.aspx/small_workgroup_gig?c=us&cs=04&l=en&s=bsd")


 It seems to do 802.3ad or traffic aggregation. 

I do need 4 nics to really test out 802.3ad though,

---

### Post by Yyrkoon on 2006-12-17
> **iduriduridur said:**
> Intel Pro 1000 cards are the easist to bond in both Windows and linux boxes. I have 2 Intel pro 1000 PCI Express cards. They work well but bonding them together just gave me redundancy not a faster disk read and write for iscsi. I may not have it all figured out but here is a good writeup of nic bonding. 


[http://linux-ip.net/html/ether-bonding.html]("http://linux-ip.net/html/ether-bonding.html")

iduriduridur,

First let me say that I have done loads of research on Link aggregation, but have zero hands on experience, and that my knowledge of how it actually works may not be complete.

I was talking to another guy on another Forum and this is what he said:

Originally posted by: nightowl on Anandtech - Networking Forum

> 
802.3ad may not give you any benefit depending on the hash that is used between the host and the target.  Since you will only have one MAC-address on each end and one IP address then you cannot load balance via those.  Your only hope is there are multiple TCP connections going on at once and you can load balance via TCP port.  If not, even if you had a switch, it still would not give you any more usable bandwidth.

So maybe all this research I've done in the past on 802.3ad was in vain :(

---

### Post by iduriduridur on 2006-12-18
Yes it sounds like the other person was correct, that is what I have been finding.

The fastest i have seen gigE iscsi is linux to linux on the web in testing and not MS windows to linux and the speed was 70-90 MBs. So it was about 70 to 90% of the pipe was being used. 

I still have to test out multipathing. It would be nice if 10G was affordable.

---

### Post by Yyrkoon on 2006-12-18
> **iduriduridur said:**
> Yes it sounds like the other person was correct, that is what I have been finding.

The fastest i have seen gigE iscsi is linux to linux on the web in testing and not MS windows to linux and the speed was 70-90 MBs. So it was about 70 to 90% of the pipe was being used. 

I still have to test out multipathing. It would be nice if 10G was affordable.

Well, here, Windows, to Windows (Starwind to MS' Initiator) I've achieved a max of 85MB/s, using a cheap $20 PCI GbE NIC to nVidia onboard GbE (700MB RAM disk). I've done a lot of testing, and have posted my results on another forum. If you're interrested in my results, I can shoot you a link.

However, there is a bright side, quarter 3 next year, PCI-E 2.0 should be an option on motherboards. What I've read, is that they are trying to implement PCI-E peer to peer communications, but I'm not sure if this would implement TCP/IP yet, or not. If it does, PCI-E 2.0 specification is 5 MBit asynchronous, per lane, and from what I've read, it sounds as though they might put multiple ports on each device. Anyhow, well have to wait and see.

All this testing I've done with windows to windows ISCSI has pretty much convinced me into using iSCSI as a home solution for data backup. So, I'll probably be using your howto here very soon (Stawind works great, but I cant see spending $400usd, when I can do it for free in Linux). I'm still unsure why iSCSI hasn't been embraced by more people, but oh well . . . I see many uses for it :)

---

### Post by JJL79 on 2006-12-19
How can i make iscsi-target start automatically at boot?

---

### Post by iduriduridur on 2006-12-20
If I remember correctly, if installed without errors it should start on boot with no additional tweaks. 

\If you want a prebuilt ISCI target to go on a CD go to openfiler.com and give that a try. It is linux-based and FREE also. 


Or there is a gui gnome package you can install that shows startup processes with ability to add and edit.

---

### Post by JJL79 on 2006-12-23
It installed without errors but does not start on boot. Is it possible to show and edit startup processes without the gui?

---

### Post by Yyrkoon on 2006-12-26
Well, I'd like to point out that instead of having two drives you could also for example do:

1) mkdir /home/test
2)dd if=/dev/zero of=/home/test/test.img bs=1024k count=10000
3) Edit /etc/ietd.conf to Lun 0 Path=/home/test/test.img,Type=fileio

This will make a test.img file 10GB in size, in your /home/test directory. The main reason I chose this directory myself, is that  when I installed Dapper, I striped two disks for my /home partition, and set the block size to 4K. Now i need to experiment with dd, and make img file block sizes smaller, and see how well it does then.

---

### Post by dsanders79 on 2007-05-07
FYI I also had to "apt-get install patch" 

Other than that this guide was great.

---

### Post by Smico on 2007-07-12
Hi,

first of all thank you for your great detailed instructions. Also linux/ubuntu-newbies like me are able to understand everything.

But at the last step - starting the target-software - I receive an error-message:

[B]Starting iSCSI enterprise target service: [: 142: ==: unexpected operator
failed.[/B]

What am I doing wrong?

---

### Post by Smico on 2007-07-13
Hi,

figured out myself - had to replace the "=="-Operators with single "="'s.

But now there's a much more frustrating message:

**Starting iSCSI enterprise target service: failed.**

Just failed. :(
No explanation. What could it be?

---

### Post by kbradl1 on 2007-08-13
Did you get an answer to the 'Failed' message?  I am getting the same message.  No other information is available, no error codes nothing.

---

### Post by fepede on 2007-08-22
> **Smico said:**
> Hi,

first of all thank you for your great detailed instructions. Also linux/ubuntu-newbies like me are able to understand everything.

But at the last step - starting the target-software - I receive an error-message:

[B]Starting iSCSI enterprise target service: [: 142: ==: unexpected operator
failed.[/B]

What am I doing wrong?

I solved replacing the first line of the file /etc/init.d/iscsi-target with 

#!/bin/bash

Hope this help!

---

### Post by jadfer on 2007-09-24
I guess I am WAY new to ubuntu but I dont know what dapper is or how to install it.

Do you have instructions for the server command line?

If so I would appreciate it.

Otherwise do you know an easy way I can get a linux Iscsi target running asap?

Thanks

---

### Post by nge-jdeck on 2007-11-16
Hello,

I have posted a complete HOWTO for installing iSCSI Enterprise Target on Ubuntu 6.06LTS (Dapper Drake) here:

[http://www.nge.com.au/index.php?next_page=res/tech_articles/iscsi_enterprise_target_ubuntu_6.06_LTS.php]("http://www.nge.com.au/index.php?next_page=res/tech_articles/iscsi_enterprise_target_ubuntu_6.06_LTS.php")

Feedback can be provided by the "Contact Us" form on that site.

Cheers
james

---

### Post by vfclists on 2007-11-28
Question from iSCSI newbie.

If an iscsi target is mapped to an unformatted partition (not LVM or any such sysetm), and a Windows iSCSI client connects to it and formats it as NTFS, will the partition and it's data be available to Windows if the hard disk is plugged directory into a Windows machne?

Even if the disk is initially formatted as a Linux partition will the Windows connection convert it to NTFS?

---

### Post by barkeep8 on 2007-12-09
This tutorial worked great for me.   I did have to use the linux uname headers fix from a later post as well as apt-get install patch.

One thing I am curious about, how to configure dapper to use an initiator to connect to iscsi targets.   Anyone have suggestions?

Thanks!

---

### Post by barkeep8 on 2007-12-09
> **vfclists said:**
> Question from iSCSI newbie.

If an iscsi target is mapped to an unformatted partition (not LVM or any such sysetm), and a Windows iSCSI client connects to it and formats it as NTFS, will the partition and it's data be available to Windows if the hard disk is plugged directory into a Windows machne?

Even if the disk is initially formatted as a Linux partition will the Windows connection convert it to NTFS?

Yes, it will be because the iscsi target presents the disk to the client as a block device. To answer the second part of your question, if you mount the disk in linux, partition and format it with linux, it will be presented to windows hosts with that formatting.

I thought your question was interesting, and I decided to try a test.  I created a vmware virtual disk under an existing windows machine.  I copied some data to it, and then moved the disk to my VM running ubuntu iscsi target.  I configured that machine to present the imported disk as another lun.  I then mounted that lun with a different windows machine, and the data was accessable.   This is exciting because you can move physical disks between windows hosts and linux iscsi target servers preserving the data.  I was shocked at how easy it was.

---

### Post by hoangminh88 on 2008-02-20
> **fepede said:**
> I solved replacing the first line of the file /etc/init.d/iscsi-target with 

#!/bin/bash

Hope this help!


After this, I get faild:
```
:~$ sudo /etc/init.d/iscsi-target start
Starting iSCSI enterprise target service: failed
```

How to fix ?

---

### Post by souki on 2008-07-26
I had the same error, the service was already started by install script

---

