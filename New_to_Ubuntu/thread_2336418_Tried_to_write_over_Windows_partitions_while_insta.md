---
title: "Tried to write over Windows partitions while installing"
date: 2016-09-08
forum: New to Ubuntu
---

### Post by alwaysalreadywas on 2016-09-08
I used UNetbootin to install Ubuntu 16.04 without a flash drive or CD. I stupidly selected both Windows 7 partitions (both the system partition and the C: drive) as the place to install Ubuntu, using file format ext4. Both of course failed, and now both my Windows partitions are corrupted and the only way I can use this computer is with UNetbootin to boot into Ubuntu but I don't think the installation is complete. I don't care about recovering any of the data lost in the Windows partitions. In fact I would prefer to have all my disk space allotted to this Ubuntu installation I am trying to complete and do away with Windows entirely. Thanks for any help, I am very noobish.

---

### Post by yancek on 2016-09-08
If you used the frugal install method which is putting Ubuntu on your hard drive rather than a flash drive, you need to create a separate partition on which to install it before running it.  You can't install to the same partition which you are booting from nor can you modify a partition from which you are running.  The simplest thing to have done before you started would be to have shrunk the windows 7 partition and left unallocated space on which to install Ubuntu.

How many partitions do you have and do you have any unallocated space.  Boot your Ubuntu and open a terminal and run the command and post the output:  sudo fdisk -l

---

### Post by alwaysalreadywas on 2016-09-08
Hi yancek, thanks so much for your response. I will keep that in mind for future reference. No unallocated space and I have 4 partitions as you'll see below. I had actually done a frugal install the way you recommended before but somehow got it in my mind this time that it was unnecessary. I ran the sudo command and got quite a lot of output; I'll post what I thought to be relevant here but also link a pastebin url to the entire output.

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    718844    716797   350M 83 Linux
/dev/sda2          718848 592371711 591652864 282.1G 83 Linux
/dev/sda3       604661760 625141759  20480000   9.8G 27 Hidden NTFS WinRE
/dev/sda4       592371712 604661759  12290048   5.9G 82 Linux swap / Solaris

Entire output:
[http://pastebin.com/HpEg59YM](http://pastebin.com/HpEg59YM)

---

### Post by yancek on 2016-09-08
The pastebin output doesn't show anything useful other than the fdisk output.  You've overwritten your windows and only have the Recovery partition.  Your Ubuntu frugal created with unetbootin must be on sda2 as the other partitions are too small or it is your windows recovery partition and a swap partition.  You can't modify a partition in use.  I've never tried this with an iso and don't think it would work but you could boot the Ubuntu frugal and open a terminal and run:  sudo gparted to open the gparted partition manager.  In the main window, click on sda2 and see if you can unmount it from the drop down menu.  Doubt it will work but if not, no harm done.

You should actually be able to determine which partition by running the command:  df -h  Look under the Mount point column for isodevice and then slide to the left under the Filesystem column and it should show the device:  /dev/sda2 for example.  

If you can't use a usb or DVD, you've got a problem.  Some possible options would be (if your Ubuntu frugal is actually one sda2) would be to use it to install the full Ubuntu to sda3 formatting your windows partition.  That's a pretty small partition for a full Ubuntu install.  You could also delete the swap partition and the windows partition (sda3) and extend the former windows to include the swap which would give you a partition of nearly 16GB which should be OK unless you plan to install a lot of software.  You could then create another Linux data partition as well as a swap partition to use from sda2.

Before getting into any of this, what exactly is on sda1, 350MB partition.  Is that a separate boot partition.
And why again are you not able to use a flash drive or DVD to boot?  This would greatly simplify things as they now stand.

---

### Post by alwaysalreadywas on 2016-09-08
I tried unmounting sda2 with gparted to no avail. I ran df -hook and indeed the device dev/sda2 was showing and no other partition was very large besides it. Here are the details:

Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           375M   11M  364M   3% /run
/dev/sda2       283G   38G  245G  14% /cdrom
/dev/loop0      1.4G  1.4G     0 100% /rofs
/cow            1.9G  676M  1.2G  37% /
tmpfs           1.9G  872K  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           1.9G   50M  1.8G   3% /tmp
tmpfs           375M  108K  375M   1% /run/user/999
/dev/sda1       331M  2.1M  308M   1% /media/ubuntu/3619cc88-3718-4820-8e98-cb7c62b1b370


I am not sure what is on that 1.35GB partition but maybe you can make sense out of the above information. I am more than willing to use a flash drive or a DVD now. I was just not using it before out of convenience. So if necessary I would take directions which would require either of those things.

---

### Post by yancek on 2016-09-08
> /dev/sda2       283G   38G  245G  14% /cdrom

The above indicates your frugal Ubuntu is on sda2.  If you are using GParted from the Ubuntu frugal install, you can't modify that partition in any way as it will be mounted. 


If you want to use a usb, you can boot the frugal Ubuntu and download unetbootin on it.  Have the flash drive plugged in and Select a Distribution from the drop down menu at the top of the unetbootin window.  At the bottom of the page, make sure under Type is says usb drive and in the Drive drop down menu, select the drive you want to install to.  If you currently have only the one drive (sda) then it should be /dev/sdb.  It will take some time to download and create the bootable flash.  When it finishes, you should see a pop-up window and you can then reboot and set the BIOS boot priority to boot the flash drive and install Ubuntu to your hard drive.  Instructions at the Unetbootin page below.

[https://unetbootin.github.io](https://unetbootin.github.io)

Instructions on installing Ubuntu are at the Ubuntu site below:

 [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

More on creating the bootable DVD at the link below:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by alwaysalreadywas on 2016-09-09
Thank you for the detailed instructions! I appreciate it. I will attempt this tomorrow.

---

### Post by mörgæs on 2016-09-09
If you want a Buntu-only system there is no need for wrangling with partitions. Just boot from the USB and select 'use entire drive for Buntu' during install, and off you go.

Best is to install using a wired internet connection.

---

### Post by yancek on 2016-09-09
> If you want a Buntu-only system there is no need for wrangling with  partitions. Just boot from the USB and select 'use entire drive for  Buntu' during install, and off you go.


That would be the simplest option, once he gets the usb created with unetbootin from the frugal install he now has.  Not having an actual installed OS creates a problem.

---

