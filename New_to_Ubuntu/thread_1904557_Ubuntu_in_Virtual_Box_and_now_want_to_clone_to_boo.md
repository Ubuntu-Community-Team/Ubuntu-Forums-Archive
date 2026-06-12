---
title: "Ubuntu in Virtual Box and now want to clone to bootable USB"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by jstaruf on 2012-01-05
Hi,

I am trying to search through the forums but i'm not having much luck finding threads to solve my issue.

My Goal:
I have ubuntu installed on a virtualbox image and i'd like to periodically clone the partition to a usb drive for when i'm on the road.

My Method:

1. Installed virtualbox on vista
2. created a new virtualbox partition and installed ubuntu 11.04 and got everything set up how i like it
4. mounted a 16gb usb
5. ran dd to make a copy of the image to a 16gb usb. took a LONG TIME! (side question, if i wanted to leave some space for a fat partition for copying files can i still edit the partitions later or should i have done that first?)

6. validate copy and i'm able to see all the files on the usb drive.

Problem:
except i cannot figure out how to get the USB drive to boot. if i just restart the computer with the drive, it's[U] not recognized as bootable.
[/U]
so i found this link:
[http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/](http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/)

and it mentions grub, so i created a new virtualbox image and boot using the ubuntu live cd iso, then "try ubuntu" and grub does not appear to be installed. so i sudo apt-get install grub, it installs ok, i can see my usb drive mounted but when i run grub:

$sudo grub
grub> find /boot/grub/stage1

Error 15: File not found

so i'm not really sure where to go from here. having trouble getting google to point me in the right direction.

Also, once i get the drive to boot, if i dd from the main image to the usb drive again, will i have to repeat whatever steps were required to make the drive bootable?

---

### Post by jstaruf on 2012-01-05
Ok issue is grub is no longer used in 11.04. It's now grub2 and there is no stage 1 file. Found some grub 2 documentation and will see what happens. Ill update with my solution once I figure out exact steps.

---

### Post by jstaruf on 2012-01-05
issue solved. i booted into a live CD, mounted the drive then ran boot-repair, selected the usb drive and let it do its thing.

Amazing...

also i was able to go backwards (using same process dd then boot-repair) from usb to hdd to clone either direction.

So now i have a ubuntu install that, with a little time carved out for the dd,  i can move to a bootable usb and take with me!

If anyone's interested in the whole process let me know, i could document it step by step, hopefully save someone else some time.

---

### Post by C.S.Cameron on 2012-01-05
Yes please, I would love to see a step by step of the process.

---

### Post by jstaruf on 2012-01-07
[SIZE=3]Goal: 
A virtual install of Ubuntu which can then be cloned to a bootable USB drive.
[/SIZE]

[SIZE=3]Why:[/SIZE]

[LIST]
[*]It's persistent
[*]The partitions/parition sizing is set up the way you want.
[*]The USB contains an exact copy of our ubuntu install. settings, programs, files... everything.
[*]USB drive is bootable for when you're on the go or want to keep a backup
[/LIST]

[SIZE=3]Process Overview:[/SIZE]
1. Main system is Windows (or whatever)

2. Create a VM using VirtualBox

3. Install Ubuntu 11.04 into a VirtualBox VM

4. Set up the installed ubuntu the way we want (settings/programs)

5. Prepare the USB Drive

6. Clone the ubuntu install to a USB drive 

7. Make the USB drive bootable

[SIZE=3]Disclaimer:
[/SIZE] i'm not an expert at this... in fact i'm not even very good... I used to have some fun way back in FreeBSD days but i've since forgotten just about everything i've learned except ls... i remember that one. i frequently have to google the syntax for such things as df -h and add-apt-repository and "how to change screen saver settings" (which btw is a menu item under system)... so... you know... WYSIWYG and mileage may vary n so forth.


you may want to read through this a few times before starting. the whole thing takes a few hours + however long the clone process takes

[SIZE=3] 1. The Main Host System[/SIZE]

You need a stable computer with:

[LIST]
[*] a few gig of space
[*]internet access
[*]usb port.
[/LIST]
 
[SIZE=3] 2. Create a VM using VirtualBox[/SIZE]

Download a few files that we'll need:


[LIST]
[*] Ubuntu LiveCD iso (or other bootable iso of your choice. i'll be using 11.04) [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
[*]download and install VirtualBox:[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
[*](optional) you may wish to install the extension pack (same link)
[/LIST]
 
Install VirtualBox.

Once it is installed we set up a new space. In VirtualBox select new (top left) and follow the wizard:


[LIST]
[*]1st screen, give it a name and select Linux for operating system and ubuntu (64bit) for version
[*] 2nd screen select memory available ( i arbitrarily selected 4G as i have tons on my host machine). Memory you select here will be unavailable for use by your host machine.
[*] 3rd screen leave defaults, we're creating a new disk.
[LIST]
[*]  -i chose to install as VDI (default),  -for storage details i chose a fixed size (not dynamic),
[*]  -for size consider the space you want to have left over on your USB for a windows partition. I'm using a 16GB flash drive so i'm going to use 12GB for my partition in virtualbox, (this leaves about ~3 for the FAT32 partition)
[*]  -create the disk. this will take about ten min
[/LIST]
 
[/LIST]
   
[SIZE=3] 3. Install Ubuntu 11.04 into a VirtualBox VM[/SIZE]

Now that the image is created you should see it listed in the VirtualBox window, select it and click start and a "First Run Wizard" will appear.


[LIST]
[*] 1st screen installation media, select the .iso of the liveCD that you've previously already downloaded in step 2. then next and the VM will start the LiveCD
[*] after it loads, select "install ubuntu", follow the wizard and once you get to allocate drive space, select "Something else" instead of the default.
[LIST]
[*] select the drive listed (should only be one /dev/sda) and click "new partition table" and a new entry will be created with the label "free space"
[*] select free space then click add, select logical, 512mb for partition size, swap area for "use as" and click ok
[*] select free space then click add, primary for partition type, all the rest of the space for the partition size and ext4 for use as, and select "/" for mount point. then click ok
[*] you should see the two partitions, now click "install now", this will take a little time, follow the wizard and enter in your username/etc
[/LIST]
 
[*].it will finally finish and say click to restart, go ahead and click and once the screen goes black and says "take media out and press enter",
[LIST]
[*]double check devices->cd and make sure the .iso is unchecked... then go ahead click on the screen and hit enter to reboot.
[/LIST]
 
[*] once the OS boots back up and settles, now might be a good time to close the VM session and make a copy of the folder which contains your image which is located
[LIST]
[*] in my case: C:\Users\YourUserName\VirtualBox VMs
[/LIST]
 
[/LIST]
          [SIZE=3]
4. Set up the installed ubuntu the way we want (settings/programs)[/SIZE]

install gparted for creating usb partitions:
sudo apt-get install gparted

.not sure what else to say here.. go to town... i installed the bitcoin client, flash and  a few other things plus some personal preference settings.

[SIZE=3]5. Prepare USB Drive[/SIZE]

Partition the USB drive:

[LIST]
[*]dig it out, plug it in and in virtualbox on the bottom you can right-click on the usb plug looking icon and select the drive to allow your ubuntu install to see it.
[*]run gparted system->administration-> gparted editor
[LIST]
[*]when it opens it will default to your sda drive, in the top right, select your usb drive from the drop down (mine was /dev/sdb)
[*]delete any existing partitions by right-clicking on the partition -> unmount. then right-click same partition-> delete. repeat for each partition until the only thing left is a row that says "unallocated"
[*]Create a new partition
[LIST]
[*]right-click on unallocated -> new,
[*]filesystem to FAT32, give it a label. The FAT partition has to be the first partition on the drive or windows will not recognize it.
[*]for  the size, we want it to be the size of the USB drive minus the size of our ubuntu install. since i have a 16 gig drive, and my install was 12 gig, i'm going to put 3000 Mib.
[*]if you want to double check, open a terminal window and type sudo fdisk -l, you can  see the exact size of your ubuntu partition
[/LIST]
 
[*]Create another new partition
[LIST]
[*]right-click on the unallocated -> new,
[*]the default should be the remaining space, leave this as is
[*]set filesystem to match (ext4) and give it a label
[/LIST]
 
[/LIST]
 
[/LIST]
 

[LIST]
[*]now click the green arrow top middle of gparted to apply all changes
[/LIST]
 
after it finishes close gparted. then double check everything from system->administration->disk utility . you should see both partitions, go ahead and mount them.

[SIZE=3]6. Clone the ubuntu install to a USB drive[/SIZE]


[LIST]
[*] Look up some important drive information. type in a terminal: df -h
[*]identify our source drive it will be the one that says "/" under "Mounted on". in my case it's /dev/sda2 (remember because we created the swap first so that got to be sda1)
[*]now identify our destination (the usb drive). mine was easy to identify because it had the label i gave it under the "Mounted on column" and in my case it listed as /dev/sdb1
[/LIST]
 IF YOU ARE NOT SURE..., shutdown the vm session and make a copy of the vm folder (just in case you mess up, you wont waste more time restoring)


[LIST]
[*] now type in a terminal window: sudo dd if=[yoursource] of=[yourdestination] bs=512k conv=noerror,sync
[LIST]
[*]the bs changes the byte size so it's much faster and the conv noerror allows us to account for potential bad sectors on our source disk.
[*]I typed: sudo dd if=/dev/sda2 of=/dev/sdb1 bs=512k conv=noerror,sync
[/LIST]
 
[/LIST]
 ONCE YOU COMMIT THIS COMMAND, it will take a long time and there is no progress bar. Mine took about 45 min to an hour.

[SIZE=3]7. Make the USB key bootable.[/SIZE]

Now that the clone is finished we will make the usb drive bootable.


[LIST]
[*]mount the live cd image from the virtualbox devices menu, restart the VM session and when the liveCD comes up select the "Try Ubuntu" option
[*]Open a terminal window and use the commands below to fix/install GRUB2
[LIST]
[*]sudo mount /dev/sda1 /mnt/myroot
[*]sudo mount --bind /dev /mnt/myroot/dev
[*] sudo mount --bind /proc /mnt/myroot/proc
[*] sudo mount --bind /sys /mnt/myroot/sys
[*] sudo chroot /mnt/myroot
[*] sudo grub-install /dev/sda
[/LIST]
 
[/LIST]

[LIST]
[*]now go into into gparted, right-click on the Ubuntu partition-> manage flags-> set the boot flag
[/LIST]
[SIZE=3][SIZE=1][SIZE=2]shutdown the liveCD session, and we're done. you should now have a bootable usb drive that is a clone of your ubuntu install.[/SIZE]
[/SIZE]
8. Boot your new drive and correct the system time.[/SIZE] 

Thanks for reading, sorry for the formatting and grammar, and i'd love to hear about your experience trying this. I'm still pretty noob so I'm also interested in any suggestions.


-jstaruf
BTC: 1419ERsKchvCbmG3r7SoQPeEgga7YSfeQY

---

### Post by C.S.Cameron on 2012-01-07
Thanks Jstaruf:
This was so well written that even I could follow it.
I never realized that you could dd an O/S that was operating.

> 1. windows doesnt seem to recognize the fat partition on the usb drive as formatted. it shows up fine in ubuntu but not windows. any thoughts?

Windows can only see the first partition on a flash drive.
Windows does not reconize swap or ext partitions.

> 
2. I'd like to find a solution for making the drive bootable that does not require loading live-cd, then downloading and installing boot-repair

Can this be done by simply setting the boot flag using gparted?

---

### Post by jstaruf on 2012-01-08
> **C.S.Cameron said:**
> 
Windows can only see the first partition on a flash drive.
Windows does not reconize swap or ext partitions.


This was right on, i repartitioned the drive making the FAT32 partition first and now it shows up in windows as expected.

> **C.S.Cameron said:**
> 
Can this be done by simply setting the boot flag using gparted?

while this is part of the process, there's more to it. you have to do a grub-install:

.Boot into a liveCD session

sudo mount /dev/sda1 /mnt/myroot
sudo mount --bind /dev /mnt/myroot/dev
sudo mount --bind /proc /mnt/myroot/proc
sudo mount --bind /sys /mnt/myroot/sys
sudo chroot /mnt/myroot

sudo grub-install /dev/sda

then go into gparted, right-click, manage flags, set the boot flag

and DONE! working flawlessly! i'll edit the OP when i have a little time.

---

### Post by Cheesemill on 2012-01-08
I use [Remastersys]("http://www.geekconnection.org/remastersys/ubuntu.html") to make Live DVD and USB copies of my installed Ubuntu.

---

### Post by C.S.Cameron on 2012-01-08
> [http://www.afterdawn.com/news/article.cfm/2012/01/03/transformer_prime_getting_android_4_0_on_january_12th_along_with_unlocked_bootloader](http://www.afterdawn.com/news/article.cfm/2012/01/03/transformer_prime_getting_android_4_0_on_january_12th_along_with_unlocked_bootloader)

Great job.
> 

I use Remastersys to make Live DVD and USB copies of my installed Ubuntu.

Does Remastersys work for cloning a virtual box install?

---

### Post by jstaruf on 2012-01-08
Guide updated and formatted. 

> **Cheesemill said:**
> I use [Remastersys]("http://www.geekconnection.org/remastersys/ubuntu.html") to make Live DVD and USB copies of my installed Ubuntu.

thanks for the tip, i'll give it a shot and see how it works.

---

