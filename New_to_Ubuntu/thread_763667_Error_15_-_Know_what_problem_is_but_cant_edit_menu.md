---
title: "Error 15 - Know what problem is but cant edit menu.lst"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by xchagger on 2008-04-23
Hi,

I've been having a lot of trouble getting grub working. I did a Adept update, and since then I cant boot into my Kubuntu 7.10 installation. I get "Error 15: File not found error"

Now, Ive managed to find out that my initrd.img-2.6.22-14-generic file has been renamed to initrd.img-2.6.22-14-generic.bak. When booting in with grub, i can view the /boot/grub/menu.lst file, and it is pointing to initrd.img-2.6.22-14-generic. 

Is there anyway to change the value from the grub commandline utility? I can cat to view the file, but cant vi to edit, etc. 

I also tried booting up from the 7.10 LiveCD. If i go to /boot, there is no grub directory?! Ive also tried copying the .dat file to the correct file name, but then I get a Input/Output error

Any help would be greatly appreciated!

Peter

---

### Post by philinux on 2008-04-23
You need to preface your vi command with gksudo equivalent, think it's kdsu

---

### Post by xchagger on 2008-04-23
Thanks for your quick reply.

However, I do not think it is a permissions problem. When I boot up with the liveCD, I cannot even see the grub directory in /boot. When I run "sudo /boot/grub/menu.lst" it just brings up a blank page...

Sorry if I misunderstood your reply, I am quite new Linux.

Thanks

Peter

---

### Post by philinux on 2008-04-23
I'd try reinstalling grub then from the live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by xchagger on 2008-04-23
I have tried that a few time. Grub is installed and working, except that it still points to initrd.img-2.6.22-14-generic and my file is named initrd.img-2.6.22-14-generic.bak.

When editing in grub, i can see /boot/grub/*, when booting with LiveCD there is no /boot/grub directory...

When booting with the LiveCD, does it show me the contents of my Linux partition or the contents of the LiveCD... So, does "ls -lrt /" show me my actual linux partition? Do I perhaps have to mount my Linux partition? And if so, how do I do that?

---

### Post by Joeb454 on 2008-04-23
You need to mount the file system from the Live CD, this is why you cannot see the /boot directory :)

Hope this helps (a simple right click > mount should do the trick)

---

### Post by xchagger on 2008-04-23
Was not quite as easy as that to mount the drive, it gave some permissions problem (hal-storage-fixed-mount refused uid 999). Here is what I did incase someone else has the same problem:

sudo mkdir /media/sda3
sudo mount -t ext3 /dev/sda3 media/sda3

After that, I went to the correct /boot directory and renamed my initrd.img-2.6.22-14-generic.bak to initrd.img-2.6.22-14-generic. Rebooted and it worked!

Thanks to everyone for taking the time to help!

Pieter

---

### Post by candtalan on 2008-04-23
I have just taken a 7.10 shipit Kubuntu live cd and run it in two machines. It did not show or mount any existing drives in the machine, but ran ok otherwise. Whereas a live CD burned from my own iso download worked as expected - all drives shown.
I am looking further at the possible faulty kubuntu shipit cd  but it may be worth checking the live cd for errors (cd boot menu)?
further- machines 1 and 2 initially showed trouble. I ran an md5sum in machine 3 result ok I then ran the live cd in machine 2 using the check cd for errors - result ok. I then ran the cd in machine 2 fully as a live cd and all the internal drives were now shown.

conclusion:looks like the cd is ok, maybe my cd drive/s are sticky or ageing. Maybe a marginal quality live cd (?)

---

