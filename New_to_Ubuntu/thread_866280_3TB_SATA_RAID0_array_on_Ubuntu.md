---
title: "3TB SATA RAID0 array on Ubuntu"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by abriejo on 2008-07-21
Hi

I have purchased a 4 port SATA RAID controller card with the intention of setting up a raid0 data repository on an Ubuntu machine.

[http://www.siliconimage.com/support/supportsearchresults.aspx?pid=28&cid=3&ctid=2&osid=2&](http://www.siliconimage.com/support/supportsearchresults.aspx?pid=28&cid=3&ctid=2&osid=2&)

I downloaded Ubuntu 2 weeks ago and installed it on a seperate SATA drive, connected directly to the motherboard.
I have plugged 3 1TB disks into the SATA controller, which I physically installed into the machine afterwards and set them up in a RAID0 configuration in the SATA controller's RAID card configuration utility which displays first on startup.

Ubuntu does not detect the RAID0 set that was created , but instead displays the 3 disks seperately when I do a 
sudo fdisk -l.

How can I get Ubuntu to display the 3Terrabyte raid0 virtual disk instead of 3 seperate 1TB disks?How do I go about installing the driver for this card in Ubuntu?I assume there is not function in Ubuntu to auto detect and install the driver?I know it is supported in Linux and that the driver should be part of Ubuntu.


thanks

---

### Post by markjensen on 2008-07-21
It's a Silicon Image RAID card?

Here is a link from [the Linux ATA site](http://linux-ata.org/faq-sata-raid.html#sii), and it seems that your card is unflatteringly (but accurately) called a "fakeraid", or software RAID.

Much of the information [here at Linux Mafia](http://linuxmafia.com/faq/Hardware/sata.html) leads me to believe this is the case, too (though it seems that some SI models may present a real Hardware RAID solution).

If you can give the specific model, it might help narrow down if your chipset is supported as a real RAID.

---

### Post by abriejo on 2008-07-22
Thankw for the reply.
Yes, it is a Silicon Image SiI3114 SATA controller and I checked the links you sent.It is indeed fakeraid.It explains a few things.

I tried to follow this link earlier to get the fakeraid0 working, but got stuck at no.3 where I have to run "sudo make install" , right after running ./configure."sudo make install" did not seem to do anything.

[http://ubuntuforums.org/showthread.php?t=2557](http://ubuntuforums.org/showthread.php?t=2557)

Below is the result of "sudo make install".I think no.3 is supposed to create a a "make" directory, which it does not do in my case because I am unable to successfully execute ls /dev/mapper/ later, in step5.


root@REPOS1:/home/abriejo/Documents/device-mapper.1.02.27# sudo make install
make -C include
make[1]: Entering directory `/home/abriejo/Documents/device-mapper.1.02.27/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/abriejo/Documents/device-mapper.1.02.27/include'
make -C man
make[1]: Entering directory `/home/abriejo/Documents/device-mapper.1.02.27/man'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/abriejo/Documents/device-mapper.1.02.27/man'
make -C lib
make[1]: Entering directory `/home/abriejo/Documents/device-mapper.1.02.27/lib'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/abriejo/Documents/device-mapper.1.02.27/lib'
make -C dmsetup
make[1]: Entering directory `/home/abriejo/Documents/device-mapper.1.02.27/dmsetup'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/abriejo/Documents/device-mapper.1.02.27/dmsetup'
make -C include install
make[1]: Entering directory `/home/abriejo/Documents/device-mapper.1.02.27/include'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/abriejo/Documents/device-mapper.1.02.27/include'
make -C man install
make[1]: Entering directory `/home/abriejo/Documents/device-mapper.1.02.27/man'
*** Installing  in /usr/share/man/man8 ***
make[1]: Leaving directory `/home/abriejo/Documents/device-mapper.1.02.27/man'
make -C lib install
make[1]: Entering directory `/home/abriejo/Documents/device-mapper.1.02.27/lib'
/usr/bin/install -c -D -o root -g root -m 555  ioctl/libdevmapper.so \
		/lib/libdevmapper.so.1.02
ln -s -f libdevmapper.so.1.02 \
		/lib/libdevmapper.so
/usr/bin/install -c -D -o root -g root -m 444 libdevmapper.h \
		/usr/include/libdevmapper.h
make[1]: Leaving directory `/home/abriejo/Documents/device-mapper.1.02.27/lib'
make -C dmsetup install
make[1]: Entering directory `/home/abriejo/Documents/device-mapper.1.02.27/dmsetup'
/usr/bin/install -c -D -o root -g root -m 555  dmsetup /sbin/dmsetup
make[1]: Leaving directory `/home/abriejo/Documents/device-mapper.1.02.27/dmsetup'
root@REPOS1:/home/abriejo/Documents/device-mapper.1.02.27#

---

### Post by Bachstelze on 2008-07-22
Why not just make a software RAID using mdadm? It will be much easier, and the performance loss would be insignificant.

---

### Post by abriejo on 2008-07-22
Thanks for all the replies.
Because I will have to make do with what I have, I followed your advice HymnToLife and used mdadm.I created a 2.73GB partition, which was the sum total of the three 3TB drives.

When I want to create one partition out of all the available space, I am now having another problem.It only allows me to create a 746GB partition.I attached the screenshot.

I don't need a high performance storage system at this stage, but it is crucial that I am able to create one big 2.73TB partition.I found this page

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

How do I recompile the kernel and how do i "Set CONFIG_EFI_PARTITION to y to compile with GPT Kernel Support"

---

### Post by Bachstelze on 2008-07-22
> **abriejo said:**
> 
How do I recompile the kernel and how do i "Set CONFIG_EFI_PARTITION to y to compile with GPT Kernel Support"

You don't need to, this option is activated in the default Ubuntu kernel. Try using another too than Gparted, like fdisk for example.

---

### Post by abriejo on 2008-07-22
Thank You.I used fdisk and got it done.

---

