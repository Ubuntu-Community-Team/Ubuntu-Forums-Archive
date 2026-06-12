---
title: "Howto Boot Ubuntu From Live USB using extlinux Bootloader"
date: 2008-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by mick8985 on 2008-03-31
Existing tutorials on the internet that cover this subject all seem to describe using the syslinux bootloader which uses the FAT filesystem, which being a Windows filesystem doesn't have support for symlinks or user permissions. This means files need to be moved around to account for the lack of symlinks and even suggest that you need to use Windows to accomplish this, all of this is completely unnecessary.
You will need to download the ISO for the livecd you wish to use from [ubuntu.com]("http://www.ubuntu.com/getubuntu/download")

First things first we want to format the partition, [so we will use gparted, which means we need to install it ]("apt:gparted") (<-- Please take advantage of these links, it is a tool called apturl, and will automatically download and installed from the repositories in your sources.list with gdebi)

```
sudo apt-get install gparted
```Ok? so fire up gparted in System > Administration > Partition Editor, change to the usb drive, for me this is /dev/sdb. right click the partition /dev/sdb1, format to > ext2

[IMG]http://web.promethix.com/mick/gparted1.png[/IMG]

Then click apply, it shouldn't take long.

[IMG]http://web.promethix.com/mick/gparted2.png[/IMG]

Now right click on your freshly formatted partition and go to "Manage Flags", select the boot flag
[IMG]http://web.promethix.com/mick/gparted3.png[/IMG]
Does your disk now look like this?
[IMG]http://web.promethix.com/mick/gparted4.png[/IMG]
Good you can close gparted.

Now we need to copy the files from the livecd to usb disk, but before we can do that we need to mount the ISO you downloaded

Before we can mount it we need a directory to mount it to..
```
mkdir iso
```
Replace myiso with the name of the livecd iso you downloaded.
```
sudo mount myiso.iso ./iso/ -t iso9660 -o ro,loop=/dev/loop0
```
Now we can just copy over the files to the USB disk in root nautilus (run "gksu nautilus"), to mount the USB disk again just unplug it and plug it back in ;) MAKE SURE YOU SHOW HIDDEN FILES IN NAUTILUS (ctrl + H) as there is a hidden folder called .disk.

or you could do it in the console

```
sudo cp -r ./iso/* /media/disk/
```

Done? alright, we don't need the ISO anymore so you can unmount it and delete the folder if you like.
```
sudo umount ./iso && rm -r ./iso
```

We're nearly done just another few steps. 

Next we need to install the bootloader, extlinux is part of the [syslinux package, so thats what we need to install]("apt:syslinux")

```
sudo apt-get install syslinux
```

Unlike LILO which installs entirely to the MBR(master boot record), extlinux is like Grub and installs itself to the file system.
```
sudo extlinux --install /media/disk/isolinux
```

extlinux and isolinux are part of the syslinux family and speak the same language, ie there configuration files are the same, but just have a different name, the ubuntu livecd uses isolinux because it uses the iso9660 filesystem. We're using ext3 so we use extlinux. 
Open up your USB drive in nautilus and in isolinux/ rename isolinux.cfg to extlinux.conf 

or in the console

```
sudo mv /media/disk/isolinux/isolinux.cfg /media/disk/isolinux/extlinux.conf
```

Now create a master boot record on the usb disk.

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/*YOUR USB DRIVE* 
```
(where *YOUR USB DRIVE* should be replaced with the path of your drive eg sda or sdb, but NOT sda1 or sdb1)

When you boot from the usb you will be presented with a prompt like this

```
boot:
```

Just hit enter and the live session will boot.

---

### Post by wieman01 on 2008-04-01
Excellent. I will try this out soon. Looks neat!

---

### Post by mick8985 on 2008-04-01
Well give some feedback when you do give it a try, So I know I haven't missed something.

---

### Post by chochem on 2008-04-02
Thanks for this - I've been looking for something like it for a while now. One or two things, though....

The bit with mbr.bin had me a bit confused: As the extlinux install reported that my device was sda1, I substituted sda1 for sdb in the 'sudo cat mbr.bin > ...' line, untill after a false start or two, I realized that it should be just '/dev/sda'. Probably a noob mistake but maybe you should be a bit more uhm abstract about it? 

Secondly when it finally did boot my Hardy Beta livecd USB, it reported a few 'bad keywords' in extlinux.conf and after seeing the orange spirit level animation for a couple of seconds I was dumped into something called busybox. None of this is to fault your tutorial, I guess it's just a warning that there might be more to it than just this.

EDIT: Checked out the extlinux.conf file which contains a number of references to /cdrom/... might this be an issue?```
DEFAULT /casper/vmlinuz
GFXBOOT bootlogo
APPEND  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
LABEL memtest
  menu label Test ^memory
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```

---

### Post by mick8985 on 2008-04-02
Sorry, you are right I should have made that more clear with the cat command, I will correct that. As for being dumped into busybox, I have never had this problem. It just booted straight into ubuntu for me and all the tutorials for using syslinux and FAT advise the same, to make no changes. I have been experimenting [here]("http://ubuntuforums.org/showthread.php?t=740799&page=3"). Where I place the kernel on the hard drive to give USB support before booting the liveusb, you could try replacing the references to cd with /dev/sda1 as shown. (in extlinux.conf on the usb), Note that with this setup only choice is "LABEL live" you should comment out all the other options that way any errors they cause, won't confuse the situation.
--edit
I have noticed that damn smalls isolinux.cfg, uses relative, rather than absolute paths. ie if extlinux.sys is in the root directory as it is in my tutorial, instead of ```
/cdrom/preseed/ubuntu.seed
``` you should be able to do ```
preseed/ubuntu.seed
```
I will experiment more with this..

---

### Post by chochem on 2008-04-02
Okay, I tried shaving it down to this:

```
DEFAULT /casper/vmlinuz
GFXBOOT bootlogo
APPEND  file=preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz
LABEL live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```

but I still get 'unknown keyword' and no menu, just a command line, saying 'boot'. Hitting enter starts the default live cd behaviour but as I said, I end up in BusyBox. As it's exactly the same behaviour as before, I guess you're right that the cdrom thing is not to blame. Other than that I have no clue.

---

### Post by mick8985 on 2008-04-02
Yes with this method, and also the syslinux/FAT method you will only get the boot: prompt. but when you hit enter, it should boot straight to livecd, that isn't an issue (Although I do plan on trying to implement it so you get the full boot menu as on the livecd in future). I think since you are changing the path to /preseed/ubuntu.seed and getting the same error as before, that it isn't loading ubuntu.seed correctly. Can you compare the directory structure on the livecd is the same as the USB and nothing has gone wrong when you copied the files?

---

### Post by themusicwave on 2008-04-02
Hello,

I've been wanting to try this for awhile now, especially since I have a friend who wants Ubuntu, but has a finicky CD Drive.  It always drops out during the install and something gets corrupted. So thanks!

Anyways, I was wondering if it is possible to still maintain a data partition on the USB Drive.  I have a 4GB drive with some data on it and would like to turn part of it into a live CD and leave the rest as a FAT partition for data use.

I assume this is just a matter of making 2 partitions with gparted one for the live cd and one for the data and then copying the data over.  

Do you see any issues with this idea?

---

### Post by mick8985 on 2008-04-02
Musicwave, Yeah go for it, make the first partition ext3, and about 1gb for good measure

---

### Post by mick8985 on 2008-04-02
chochem, I just downloaded the hardy cd from ubuntu.com, and it appears to be defective, as even when you burn to cd and try to boot the live session from the menu, it says IO error, Reboot? have tried on 3 computers. Can you test your iso on a cd?

---

### Post by chochem on 2008-04-03
> **mick8985 said:**
> chochem, I just downloaded the hardy cd from ubuntu.com, and it appears to be defective, as even when you burn to cd and try to boot the live session from the menu, it says IO error, Reboot? have tried on 3 computers. Can you test your iso on a cd?

I would if I could but my laptop's dvd drive isn't working very well - reading is load&pray and burning is out, I'm afraid :(

---

### Post by mick8985 on 2008-04-08
Chochem: I believe the problem you have is related to ext3, If you use ext2 this should work correctly. I now recommend ext2 in my tutorial

---

### Post by chochem on 2008-04-08
Thanks - I'll try that when I'm more awake :)

---

### Post by chochem on 2008-04-09
Sorry to say that it didnt change anything. But I'm feeling slightly sheepish because reformatting the usb drive, I realized that I could just remove the 'quiet splash' arguments and see what was causing it to fail. Everything goes well (apart from the noted missing keywords but I don't think they're related to the issue) untill the process gets caught up in this loop going (from memory):

```
EXT3-fs mounted file system with ordered data mode
kjournald starting commit interval 5 seconds
```

which is repeated some twenty tims or so before failing and busybox comes up. I don't know if this is relevant to mention - I'd kinda forgotten about it - but when I installed 7.10, I formatted the main partition using the reiserfs system on a whim - had read an article touting its superiority. Does the install process try to read my current root partition and fails because it's not ext?

---

### Post by mick8985 on 2008-04-09
Yeah I got that same error, apparently kjournald is a kernel process thingy related to journaled filesystems, which is what prompted me to switch to ext2. When I switched to ext2 it booted.
Strangely, it did still come up with```
EXT3-fs mounted file system with ordered data mode
kjournald starting commit interval 5 seconds
```
but it continued to boot just fine anyway.

Would be good to get this one ironed out before the release of Hardy as alot of people may have to use this method to upgrade.

---

### Post by chochem on 2008-04-09
Got it! Thanks to [this post]("http://ubuntuforums.org/showpost.php?p=3674167&postcount=7"), I went back and checked and sure enough, the .disk directory was mssing. Copied it and everything went smoothly.

Apologies for the many false leads and mucking up your new thread :)

---

### Post by mick8985 on 2008-04-09
I'm just glad the problem is solved I might capitalise the "show hidden files" part of my howto so no-one does it again.

---

### Post by Huss on 2008-04-18
Does this method make a persistent live usb? Could I use the system normally, (installing new programs, saving files in the home drive) and then take the USB out over to another computer and still have the same programs installed, homedrive and similar settings? 

Also, if booting from the same computer each time, will it go through hardware configuration procedures each time?

I'm very interested in this method, it looks promising.

---

### Post by mick8985 on 2008-04-18
No unfortunately this method like the livecd mounts an image of the ubuntu system in a read-only compressed filesystem called squashfs, and as such the image cannot be altered in any way. You could have another partition on the usbkey for data which would automount to your desktop.
What you want to do is merely run the installer from the cd and install it onto your usbdrive, of course a standard ubuntu install will take up over 4 gigs uncompressed... so you'll need a big usbdrive.

---

### Post by Huss on 2008-04-18
Mmm. I have my gutsy installed on an external USB hard drive at the moment which works beautifully. It would be great though, to load up grub and have an option of loading the home computer (the one used the most) and then another option to boot to a new system. The second option could go through a similar process to the live CD in configuring the hardware, while keeping your programs and home drive persistent. 

Any thoughts or how tos? 

P.S. You might like this how to: creating a custom live iso
[http://howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

---

### Post by mick8985 on 2008-04-18
I don't think the livecd does alot in the way of hardware configuration, it just loads a stock kernel with loads of hardware support in the form of modules and loads autoloads the modules depending on the detected hardware just like a standard ubuntu install does. The difference is a standard install you configure your xorg.conf to use a specific display driver, which will change from machine to machine, where as a livecd will pick either nv or radeon or vesa (this will not be necessary for hardy with bulletproof X though). Basically the install you have on the usb drive now should be just as portable between pc's if you enable a generic driver in the xorg.conf like vesa (again not necessary in hardy). The advantage of having the livecd on a partition though is you can use it for installs on other computers if you like.
If you would like me to show you how to add a grub entry to the grub menu to boot the livecd (non persistant) I will help you with that. It would be somewhat similar to what I recommend [here]("http://ubuntuforums.org/showthread.php?t=740799&page=3")

---

### Post by Huss on 2008-04-18
Ha, it can be the evangelise grub entry. 

P.S. I've set my driver to vesa and will test out a boot on another computer ;)

---

### Post by mick8985 on 2008-04-19
Yeah, Its faster than installing from a livecd so you can surreptitiously install it on your friends pc while there back is turned :twisted:

---

### Post by oedipuss on 2008-04-19
Why isn't this an officially supported option for installing yet ?? It worked flawlesly, booted up faster than my (admittedly kinda bloated) gutsy install, and installed in approx the same time it took to copy the image to the usb stick .. 
The only extremely minor issue was that grub had the disk number wrong, which can be corrected on the fly. 

Thanks for the instructions =D

---

### Post by Craigy90 on 2008-04-19
Thanks for this How-to, it appears to be just what I am looking for!

All of the steps work up until the "cat" command:

```


sudo cat /usr/lib/syslinux/mbr.bin > /dev/sdb
bash: /dev/sdb: Permission denied


```

Any ideas about this problem? I am using a 40GB USB 2.0 hard disk, and trying to put the Hardy Heron release candidate image on it. Am I making a simple mistake?

Thanks.

---

### Post by mick8985 on 2008-04-19
On your system /dev/sdb isn't the address of your usb hard drive, its most probably /dev/sda, in gparted you select whcih hard dirve you want to use from the drop down list, use the same address as it appears in that drop down list.
If you are still unsure do
```
sudo fdisk -l
```
and paste the results here, and I'll  give you a hand.

---

### Post by Craigy90 on 2008-04-19
Here's the results:

```
 sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e9e565f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51ef551c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39070048+  83  Linux

```

I checked in gparted before running the cat, but it gives permission denied on sdb anyway. Thanks for the quick reply.

---

### Post by mick8985 on 2008-04-19
I don't understand why, but perhaps for some reason root has been denied write access to /dev/sdb
try
```
sudo chmod +w /dev/sdb
```
then try again.

---

### Post by Craigy90 on 2008-04-19
That command executed, but I still get permission denied. How can that be?

---

### Post by mick8985 on 2008-04-19
Hmm, When I try it and /dev/sdb doesn't exist this is what I get
```
chmod: cannot access `/dev/sdb': No such file or directory
```
I have no idea
try
```
sudo chmod 774 /dev/sdb
```

---

### Post by mick8985 on 2008-04-19
Another thing to check is that /usr/lib/syslinux/mbr.bin actually exists.

You can also try using dd instead of cat 

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb
```

---

### Post by Craigy90 on 2008-04-19
The other chmod didn't work either, and mbr.bin does exist.

Here is the result of running dd:

```

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb
0+1 records in
0+1 records out
410 bytes (410 B) copied, 0.0145719 s, 28.1 kB/s

```

That looks like success! I will try booting it now. Wish me luck!

---

### Post by mick8985 on 2008-04-19
Good luck

---

### Post by Craigy90 on 2008-04-19
It works!

I can now run the livecd... without a cd! Very nice guide mick!

Just curious, has anyone else had the problem with the cat command or know why I get an error?

---

### Post by mick8985 on 2008-04-19
No-one has mentioned it so far, perhaps I will replace the command with dd instead of cat in the guide.

---

### Post by Huss on 2008-04-24
Hi Mick

Thanks for the roaming boot advice. I managed to get my external HD booting of another computer. It took a bit of fiddling around but I got it. If interested, I wrote about my experience.

[http://ubuntuforums.org/showthread.php?t=762657](http://ubuntuforums.org/showthread.php?t=762657)

All the best!

---

### Post by camurgo on 2008-04-27
> **mick8985 said:**
> chochem, I just downloaded the hardy cd from ubuntu.com, and it appears to be defective, as even when you burn to cd and try to boot the live session from the menu, it says IO error, Reboot? have tried on 3 computers. Can you test your iso on a cd?


Similar problem here(ubuntu 8.04 LTS)... at boot time with the usb stick I was getting "could not find kernel image: linux" 
I tried editing /media/disk/isolinux/isolinux.conf, and other several workarounds, and and nothing...

Finally I gave up and tried burning the CD.. All the options of the live CD menu give me: "IO error, Reboot".

My downloaded .iso md5 matches the one on ubuntu.com site... :(
I don't think the problem is on my dvd-drive, could be though..

---

### Post by mick8985 on 2008-04-27
Hi Cameigons, I never did work out why I got that error on the cd (I only downloaded to try and figure out chochems problem) however I did get the same iso working on the usb key. (I myself made the same error as chochem and forgot for copy over the .disk folder) I put that error down to the cd burning incorrectly.
Sorry I can't be of more help on that one.

--edit
I noticed you put the path
```
/media/disk/isolinux/isolinux.conf
```
it should be
```
/media/disk/isolinux/extlinux.conf
```
perhaps thats your problem

---

### Post by camurgo on 2008-05-10
> **mick8985 said:**
> 
--edit
I noticed you put the path
```
/media/disk/isolinux/isolinux.conf
```
it should be
```
/media/disk/isolinux/extlinux.conf
```
perhaps thats your problem

Thanks Mick, I came back to report that was in fact the problem. Am I dumb or what? :p 

I couldn't figure out the burned cd problem though, but who cares, now I'm never going back to liveCD installs again :)

---

### Post by mick8985 on 2008-05-11
> **Cameigons said:**
> Am I dumb or what? :p 
No comment :p

Glad you got it working.

---

### Post by smeck on 2008-08-27
Nice howto :-)

Is it possible to have two partitions on the USBdrive and have Ubuntu Live-system on the second partition? That way I could use the first partition as storage compatible with operatins systems that onlys spots the first partition.

I tried this, but extlinux gave me an erroe message:
sudo extlinux --install /media/disk/isolinux
/media/disk/isolinux is device /dev/sdh2

---

### Post by mick8985 on 2008-08-27
The extlinux --install command needs to be pointed at a mounted filsystem not the device.
other than that everything else should be the same
make sure the dd command points at /dev/sdh (you have alot of drives!)

---

### Post by smeck on 2008-08-29
I have made two partitions on the USB drive, nr1 is FAT32 and nr2 is ext2, I have set the boot-flag on nr2 and copied all the files from the iso to partition nr2. I have set the permissions so that I can write to the second ext2 partition as normal user as well. The partition is mounted, I have it open in nautilus, and then i type

> extlinux --install /media/disk/isolinux
I have given the first partition a namne using mtools and I guess that's why it doens't mount in the /media/disk folder. The response I get is as before
> /media/disk/isolinux is device /dev/sdh2

A note about my many devices, I have a nonamne multicard reader that takes sdd - sdg wether or not there is any memory card inserted or not.

---

### Post by mick8985 on 2008-08-29
That's not an error it's just verbose output, all it does is write extlinux.sys to the target directory.
```
sudo mv /media/disk/isolinux/isolinux.cfg /media/disk/isolinux/extlinux.conf
```
All you need to do is rename the conf file as per my tutorial and do the dd command to sdh
```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdh
```

You have done nothing wrong so far, just follow the tutorial and reboot your computer and it will work, trust me.

---

### Post by smeck on 2008-08-29
Thank you very much. When I got that verbose output I thought something was wrong and stoped. Well well... som days I feel smart and som days I don't ;-)

Anyway it's just finished booting, it's as fast as the 5400rpm hard drive.

---

### Post by mick8985 on 2008-08-29
Yeah, with linux commands you kind of get used to no output being good and output being bad so I can see where your coming from. You'll be braver next time ;)

---

### Post by smeck on 2008-09-03
it's me again, I'm wondering if there's any way to make this persistent? I searched all over the web but haven't found anything that apply to extlinux. I tried som things for syslinux, but they didn't work. I tried the init.rd.8.04.1.casper.fixed but my system didn't boot with that.

So, is there a way to make it persistent?

---

### Post by mick8985 on 2008-09-03
extlinux isn't the problem, that bug is in casper, I tried the fixed version too and it didn't work for me (I think that is perhaps because I use x64). Basically I think the last version to work with peristant is Feisty. Hopefully Intrepid will work. But which bootloader you use shouldn't make a difference.

---

### Post by smeck on 2008-09-03
I use the 32bit LiveCD, the fixed casper first gave me the Kubuntu (i used Ubuntu LiveCD) splash and the it tried to acces fd0, but I have no floppy. The I tried to use the fixed casper-script in my original initrd but it didn't work.

However, with the LiveUSB-tool there is a Persistent Home -option
[http://3.bp.blogspot.com/_JGCUC3b0VFQ/SLfxyUpAhOI/AAAAAAAAA5k/CTUXzJzesBU/s1600-h/Sk%C3%A4rmbild-Create+Live+USB+system.png](http://3.bp.blogspot.com/_JGCUC3b0VFQ/SLfxyUpAhOI/AAAAAAAAA5k/CTUXzJzesBU/s1600-h/Sk%C3%A4rmbild-Create+Live+USB+system.png)

[https://launchpad.net/liveusb](https://launchpad.net/liveusb)

Well well, Intrepid isn't that far away :-)

---

### Post by mick8985 on 2008-09-03
Yeah I have seen that blueprint, it looks brilliant :)

---

### Post by monaro800 on 2008-10-24
Followed this to a T, get ERROR 15 when i try to boot. Please Help. Befor my poor laptop becomes a minature Airbus A380 out the hotel Window

---

### Post by mick8985 on 2008-10-24
Grub should not come into the equation, did the liveusb drive work, and then you proceeded to do an install from it?

---

### Post by monaro800 on 2008-10-24
Followed the Guide, told Bios to boot from USB PEN DRIVE and it instantly comes up ERROR 15
 i press enter and it simply reboots in a circle i have tryed this a few time, i might give it one more bash, and get a diffrent ISO maybe mine is corrupt

---

### Post by mick8985 on 2008-10-24
That's odd, I am guessing you have used the Intrepid rc, perhaps the way they do the bootloader on the livecd has changed, did you get the boot: prompt from the extlinux bootloader?

---

### Post by monaro800 on 2008-10-24
No i litterally got ERROR15

the pen light flashed as it was being accessed then bang, ERROR 15 nothing else. what ISO Should i download, i can always apt-get upgrade afterwards :P

---

### Post by mick8985 on 2008-10-24
It's hard for me to say since I cant really diagnose your problem, if your bios is set to boot from the usb drive it should not encounter grub at all. just so i know i am getting this right does it say GRUB: Error 15?.
It could be that rather than setting to boot device priority to usb you made a mistake and changed the mapping of the drives in your BIOS

---

### Post by monaro800 on 2008-10-24
My Screen just shows ERROR 15 on the top right first line. thats it.

---

### Post by mick8985 on 2008-10-24
In that case it could be an error extlinux is spitting out, its not an error I have seen before, I'll have to try and recreate before I can be of any help, and its 19:20 on a Friday night for me so I will be heading out in a little bit, I will download the RC now and I can help you out tomorrow. Sorry I cant be of more immediate help.
Have you definately renamed isolinux.cfg to extlinux.conf?

---

### Post by monaro800 on 2008-10-25
Yes i checked and doubble checked everything.

But i did notice, i had to do somthing diffrent, after formatting the pen drive, i coulndt put data on it, as it was owned by "root" so i had to chown user:user /media/disk to write data on the pen. could this be the problem/? ether way i still get 
"ERROR 15"

---

### Post by mick8985 on 2008-10-25
I don't think that would make a difference, in the guide i just suggest copying the files as root user.

---

### Post by monaro800 on 2008-10-25
I cant copy as the root user though, i still get an access denied error, im using the Linpus Linux OS provided with my Acer Aspire One, i noticed from your post last night where you mentioned the time ur in the UK prolly to much to hope ur local to me, but would you be willing to sell me a USB Pen Drive with Ubuntu on it, id be happy to paypal or summing. this is getting to me now, ive tryed 3 more times this morning to no joy ive checked the bash history against your guide and still no joy.

Or even with SSH to my machine, i have the files here, theres nothin on it i wanna keep i just want rid of this poxy linpus *PULLS OUT MORE HAIR*

&#65283;&#65283;&#65283;&#65283;&#65283;&#65283;&#65283;&#65283;**EDIT**&#65283;&#65283;&#65283;&#65283;&#65283;&#65283;&#65283;&#65283;&#65283;&#65283;&#65283;&#65283;
I now know what ERROR15 is for the record.

I reformatted the pen drive and rebooted to install an application, the BLANK PEN attempted to boot and there was error 15, so somthing with the copying of files seems to fail for me. but theres no failures reported

---

### Post by mick8985 on 2008-10-25
I am in the UK yeah, I guess I could do that. You can add me on MSN to discuss it as the forums aren't exactly the best place.

Edit: you can see my address by clicking the msn butterfly icon

---

### Post by monaro800 on 2008-10-27
First of all thanks to mick for his help just some notes for users of so called web books

1: Acer Aspire One, WILL NOT BOOT THE PEN DRIVE FROM THE USB ON THE LEFT SIDE (Dosnt on this one anyways)

2; Intel Atom CPU's from 1.2Ghz to the Current 1.6Ghz if you have the Atom CPU you will be taken to busybox (Ubuntu are working on a version Compiled Specifically for the Atom CPU as i understand it.

3: This guide works for other distros, so far ive tested it with: OpenSolaris 10 (LiveCD) DreamLinux 

Just thaught id let you all know. 
CHEERS

---

### Post by clay_glenn on 2009-05-26
This thread comes VERY close to what I want, but I still seem to be missing something.  Here is what I want to do.  I have an 8GB USB memory stick and I want to partition it up so that I have a 2GB FAT partition for sharing data and documents, then I want a bunch of Linux (ext2) partitions into which I can install various LIVE CDs.  I want each to be fully bootable within its own partition.  That is, if I set the boot flag on partition sdx3, I want to be able to boot the Ubuntu Live CD that is in that partition.

THEN, I want to be able to install GRUB to the first (FAT) partition, and set up my menu.lst to be able to boot into any of the partitions on the stick by simply using the chainloader command.  Then I can load multiple bootable Live CDs into separate ext2 partitions until I run out of room on the USB stick.  Since each Live CD is only about 700 MB max, I should be able to get quite a few, plus some utility CDs (System Rescue CD, Super GRUB CD, etc.) onto one USB stick on my keychain.

So far, I have the first (FAT) partition working with GRUB installed.  I have Puppy Linux installed in the next partition, and it is working with the chainloader command in GRUB.  But when I try to install the Ubuntu Live CD into the next partition, and use the extlinux, it just hangs at a blank screen when I try to boot into it, either directly by setting the boot flag to that partition, or by booting from GRUB and chainloading that partition.

I think that I am VERY close to success here, but something just isn't quite connecting the dots here.

Has anyone had any success with something like this?  I think that if I can get the Live CD to successfully boot from the third partition, then I should be able to get it to load from GRUB using the chainloader, just as I can do with Puppy Linux in the second partition.

---

### Post by mick8985 on 2009-05-26
I didn't know that you could install grub to a FAT partition, but evidently seems you have done so successfully so I guess you can...

To do this the chainloader way you need to mount the partition /dev/sda3 or whatever. and do extlinux --install to wherever you mounted it and change the names of the config files as per my tutorial.
And then you'd need to put the mbr image on that particular partition.
ie (sda3 rather than sda)
```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda3
```

Then as long as you have grub correctly installed you'd just need to have the chainloader command in menu.lst point to the correct partition ie (hd1,2) or similar.

---

### Post by clay_glenn on 2009-05-26
> **mick8985 said:**
> 
```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda3
```


So the mbr.bin for syslinux is the same as for extlinux?  Just confirming.

I didn't know that the individual partitions each had an MBR.  I thought there was just one for the whole device.  Since I didn't want to risk borking up GRUB, I didn't want to mess with the MBR.  But if there is a separate MBR in each partition, then I could give that a shot.

If this works, I should be able to pretty much set up a bunch of empty partitions, and preload them with extlinux, and then just dump Live CDs into each partition as desired, changing the isolinux names to extlinux.  Then the chainloaders in GRUB would all stay consistent, addressing each partition individually.

Cool!

---

### Post by mick8985 on 2009-05-26
Well usually there isn't but in this care you're gonna make one. I'm not sure of the academic side of things, but I know that it works as I have played around with something similar before.
remember you still need to install grub to the main mbr of the device and point it at the FAT partition containing your menu.lst
```
sudo grub
```
then in the grub shell assuming your usb drive is hd1 do
```
grub> root (hd1,0)    (Specify where your /boot partition resides)
grub> setup (hd1)     (Install GRUB in the MBR)
grub> quit       
```
I'm presuming you already have that set up, but just clarifying.

---

### Post by clay_glenn on 2009-05-26
> **mick8985 said:**
> Well usually there isn't but in this care you're gonna make one. I'm not sure of the academic side of things, but I know that it works as I have played around with something similar before.
remember you still need to install grub to the main mbr of the device and point it at the FAT partition containing your menu.lst
```
sudo grub
```
then in the grub shell assuming your usb drive is hd1 do
```
grub> root (hd1,0)    (Specify where your /boot partition resides)
grub> setup (hd1)     (Install GRUB in the MBR)
grub> quit       
```
I'm presuming you already have that set up, but just clarifying.
Yes, I already installed GRUB to the stick so that when I set the boot flag on the first partition, GRUB starts up and gives me my menu.  My first menu selection is Puppy Linux which is in the second partition, using the chainloader.  My next menu item is for Ubuntu in the third partition.  I can get Ubuntu Live CD to start if I use the traditional entry of "title", "root", "kernel", and "initrd" in the menu entry.  But I want to use the simple chainloader command instead.  To do that, the Live CD needs to be fully bootable within its own partition, which I think means that I need to get extlinux working (in place of the isolinux that comes on the Live CD).  Somehow, Puppy Linux just installed everything it needed in its partition automatically.

I'll try loading the MBR in partition #3 tonight and see if that gets things going.

Thanks!

---

### Post by mick8985 on 2009-05-26
I believe it should fix the issue, then its the simple matter of repeating for any other livecd distros you wish to use. however bear in mind that this way you can only use the apps installed on the livecd and not additional ones, which will be annoying.
There are numerous other options available to you however and using a chainloader I find is almost always the most versatile way to do things.

---

### Post by clay_glenn on 2009-05-26
> **mick8985 said:**
> I believe it should fix the issue, then its the simple matter of repeating for any other livecd distros you wish to use. however bear in mind that this way you can only use the apps installed on the livecd and not additional ones, which will be annoying.
There are numerous other options available to you however and using a chainloader I find is almost always the most versatile way to do things.

For normal everyday use on my Asus mini-laptop/netbook, I do full installs to SD cards.  This allows me the flexibility to startup and completely configure the distro for use on that computer.  But for the USB stick, I'm looking for more of a "Swiss Army Knife" that I can use on any computer to either do emergency repairs and recovery, or to demonstrate Ubuntu/Kubuntu/CrunchBang, etc.  Since performance isn't a big issue, and I don't need to save configurations or install applications to the distros, the read-only Live CD seems like a pretty easy solution to carry around about a dozen distros and utility disks on my keychain.  

Since the actual CD is bootable, it has all of the configuration files that are required. I just need to convert from isolinux to extlinux for use on the USB stick.  Renaming the file and directory is pretty straightforward.  I just need that last bit on getting it to boot within the partition, so that I can then use the chainloader in GRUB.  That way, I can keep all my GRUB stanzas uniform, only changing the Title and the partition that it points to.

---

### Post by clay_glenn on 2009-05-27
> **mick8985 said:**
> 

To do this the chainloader way you need to mount the partition /dev/sda3 or whatever. and do extlinux --install to wherever you mounted it and change the names of the config files as per my tutorial.
And then you'd need to put the mbr image on that particular partition.
ie (sda3 rather than sda)
```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda3
```


Yep, that worked!  I needed that to go into the boot block of each partition.  Now I'm rolling!

Thanks for the help!

---

### Post by staticanime on 2009-05-31
I'm getting a "boot error" message when trying to boot Ubuntu from /dev/sdb3. I'm trying to set up Ubuntu in partition 3 and windows Vista in partition 4, with Mac OS X in partition 2

---

### Post by clay_glenn on 2009-06-01
> **staticanime said:**
> I'm getting a "boot error" message when trying to boot Ubuntu from /dev/sdb3. I'm trying to set up Ubuntu in partition 3 and windows Vista in partition 4, with Mac OS X in partition 2
Sadly, I am also now getting the "boot error" message.  I have an 8GB USB stick.  The first partition is a 2GB FAT partition for shared data, with GRUB installed to boot the other partitions, which are all ext2.  

Partition 2 has Puppy linux.  It is booting fine using the chainloader.

Partition 3 has the System Rescue CD, a bootable "live" CD.  It is booting fine using the chainloader.

Partition 5 has the Ubuntu Live CD.  It was booting fine with the chainloader, but now it is getting the "boot error".

Partition 6 has the Ultimate Boot CD "live" bootable CD.  It is getting the "boot error" when using the chainloader.

Partition 7 has the Clonezilla Live CD.  It is also getting the "boot error" when using the chain loader.

The part that distresses me is that the Ubuntu Live CD partition was booting fine, then stopped for no apparent reason.  Partition 2 and 3 are both starting with the chainloader just fine.

Looking for suggestions....

---

### Post by dipaish on 2009-06-01
The easiest way to boot from live usb is to install Unetbootin which has better GUI and is easy to create live usbs...

---

### Post by clay_glenn on 2009-06-01
> **dipaish said:**
> The easiest way to boot from live usb is to install Unetbootin which has better GUI and is easy to create live usbs...

Couldn't figure out how to get Unetbootin to install to Partition #5 on my USB stick.

---

### Post by mick8985 on 2009-06-02
I wouldn't have thought Unetbootin was flexible enough for what you're doing clay.

Does the boot error not carry a number, like "boot error 3" or something. It doesn't seem to be a grub produced error, as grub errors are clearly marked and numbered. Is there anything else you have done, have you resized or moved partitions as you have added more distros to your usb?
I'm afraid with nothing to go on, and unable to see the problem myself I have no clue what might be happening to either of your disks.

---

### Post by staticanime on 2009-06-02
> **mick8985 said:**
> I wouldn't have thought Unetbootin was flexible enough for what you're doing clay.

Does the boot error not carry a number, like "boot error 3" or something. It doesn't seem to be a grub produced error, as grub errors are clearly marked and numbered. Is there anything else you have done, have you resized or moved partitions as you have added more distros to your usb?
I'm afraid with nothing to go on, and unable to see the problem myself I have no clue what might be happening to either of your disks.

I'm having the same Boot Error as clay. There's no numbers, and I'm not using GRUB, so it's not an error with GRub, it's something with extlinux

---

### Post by mick8985 on 2009-06-02
> **staticanime said:**
> I'm having the same Boot Error as clay. There's no numbers, and I'm not using GRUB, so it's not an error with GRub, it's something with extlinux

Well the most logical cause for the error is for whatever reason the extlinux.conf file cannot be found.
causes for this could be:
[LIST]
[*]incorrectly named file/filepath.
[*]unreadable filesystem (perhaps you formatted to something other than ext2/ext3, I'm not sure whether ext4 will work)
[*]That's all I got, perhaps the bullet points werent really necessary... but any reason you could think of why extlinux.conf could not be found.
[/LIST]
Also it's hard to imagine you are going to be able to get that disk to be of any use without using the grub and chainloader method to be able to select which OS you want to use.

---

### Post by staticanime on 2009-06-02
> **mick8985 said:**
> Well the most logical cause for the error is for whatever reason the extlinux.conf file cannot be found.
causes for this could be:
[LIST]
[*]incorrectly named file/filepath.
[*]unreadable filesystem (perhaps you formatted to something other than ext2/ext3, I'm not sure whether ext4 will work)
[*]That's all I got, perhaps the bullet points werent really necessary... but any reason you could think of why extlinux.conf could not be found.
[/LIST]
Also it's hard to imagine you are going to be able to get that disk to be of any use without using the grub and chainloader method to be able to select which OS you want to use.

I'm using a bootloader called Chameleon to allow me to boot MAC OS X (I'm using a hybrid GUID+MBR partitioned drive). I have 4 partitions,
200MB - EFI Partition (EFI)
10GB - Mac OS X (active partition containing the Chameleon bootloader) (HFS+)
5GB - Ubuntu with Extlinux (EXT3)
10GB - Windows Vista (using default bootsect /nt60 and bootmgr)

Chameleon will just look at whatever boot code is in each partition and chainload that, so that's how I'm trying to boot ubuntu. I followed your guide exactly, so extlinux.conf is in the isolinux folder. Could you post the extlinux.conf needed for Ubuntu 9.04 so I can make sure it's got the right contents, that could be the issue?

---

### Post by mick8985 on 2009-06-02
I don't believe that is the problem, ```
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo
```
You see it includes menu.cfg, which contents are```
menu hshift 13
menu width 49
menu margin 8

menu title Installer boot menu
include stdmenu.cfg
include text.cfg
include amd.cfg
include gtk.cfg
include amdgtk.cfg
menu begin advanced
	menu title Advanced options
	label mainmenu
		menu label ^Back..
		menu exit
	include stdmenu.cfg
	include adtext.cfg
	include adamd.cfg
	include adgtk.cfg
	include adamdgtk.cfg
menu end
label help
	menu label ^Help
	config prompt.cfg
```
text.cfg
```
default live
label live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
label live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
label install
  menu label ^Install Ubuntu in text mode
  kernel /install/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed initrd=/install/initrd.gz quiet --
label check
  menu label ^Check disc for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
label memtest
  menu label Test ^memory
  kernel /install/mt86plus
label hd
  menu label ^Boot from first hard disk
  localboot 0x80
```
I could go on but text.cfg is the most important, infact you could just rename text.cfg to extlinux.conf and it would work, so you could try doing that.

---

### Post by staticanime on 2009-06-02
> **mick8985 said:**
> I don't believe that is the problem, ```
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo
```
You see it includes menu.cfg, which contents are```
menu hshift 13
menu width 49
menu margin 8

menu title Installer boot menu
include stdmenu.cfg
include text.cfg
include amd.cfg
include gtk.cfg
include amdgtk.cfg
menu begin advanced
	menu title Advanced options
	label mainmenu
		menu label ^Back..
		menu exit
	include stdmenu.cfg
	include adtext.cfg
	include adamd.cfg
	include adgtk.cfg
	include adamdgtk.cfg
menu end
label help
	menu label ^Help
	config prompt.cfg
```
text.cfg
```
default live
label live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
label live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
label install
  menu label ^Install Ubuntu in text mode
  kernel /install/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed initrd=/install/initrd.gz quiet --
label check
  menu label ^Check disc for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
label memtest
  menu label Test ^memory
  kernel /install/mt86plus
label hd
  menu label ^Boot from first hard disk
  localboot 0x80
```
I could go on but text.cfg is the most important, infact you could just rename text.cfg to extlinux.conf and it would work, so you could try doing that.

I found the problem. See, my bootloader is on /dev/sdb2 (active) and Ubuntu is on /dev/sdb3. If I set /dev/sdb3 active, my bootloader doesn't load, instead it loads straight into the ubuntu install. So, the active flag was the problem.

So, now I need a way to have my [Chameleon]("http://chameleon.osx86.hu") bootloader appear first and somehow set the ubuntu partition active. Is it possible to set more than one active partition, and mark one of those as the main bootable one?

---

### Post by mick8985 on 2009-06-02
I don't believe so, hmm thats really annoying. 
This must be a limitation of the mbr.bin, I wonder if there is an alternative mbr that could be used which doesn't rely on using the boot flag to find the correct partition to load the bootloader from, I know grub does this.
I'll look into it, the alternative of course is to just use grub instead of extlinux, will mean installing grub to the partition
Do a grub entry something like..
```
title		Ubuntu
kernel	/casper/vmlinuz root=/cdrom/preseed/ubuntu.seed ro boot=casper
initrd /casper/initrd.gz
```

---

### Post by clay_glenn on 2009-06-02
> **mick8985 said:**
> I wouldn't have thought Unetbootin was flexible enough for what you're doing clay.


That is why I'm not using Unetbootin, it wouldn't do what I wanted.  It looks like EXTLINUX should do it.  In fact, EXTLINUX did work for my Ubuntu in partition #5.  But then I added a couple more partitions and loaded in some additional Live CDs (Clonezilla and Ultimate Boot CD) and couldn't get them to work, and Ubuntu stopped working too.  But I can still chainload Puppy in partition #2 and System Rescue CD in partition #3.

I went through the process of copying the files from the Live CD ISO file to the individual partitions, renamed files from ISOLINUX to EXTLINUX and then installed EXTLINUX to each partition.  If each partition is bootable from EXTLINUX, then I should be able to boot them all from one GRUB using chainloaders.  But it tells me that it is starting, then immediately gives "Boot Error" with no codes nor explanations.

I can replace the EXTLINUX in each partition and install GRUB in each partition and everything works.  Then I can use the GRUB in partition #1 to chainload the GRUB's in the other partitions.  I just want to know why I can't get EXTLINUX to work, and in fact, why it did work and then stopped working.  I suspect that one of the pointers in the .conf file is off, but I haven't been able to figure which one.

---

### Post by mick8985 on 2009-06-02
The reason as staticanime discovered is that the MBR supplied with syslinux will only ever boot the partition marked with the boot flag, so the partition that the mbr is on has no impact on which is partition is booted from. So even if you chainload the correct partition the chainloader loads the mbr which loads the incorrect partition (in your case clay the grub partition).
I wasn't aware of this behaviour when I advised you to do it this way, sorry.
I found an alternative MBR called [boot control]("http://www.xs4all.nl/~gklein/bcpage.html"), although the warning at the top of the page is pretty off putting.
There must be a nice simple solution to this. I'll give it more thought, and some googling.

---

### Post by clay_glenn on 2009-06-02
> **mick8985 said:**
> The reason as staticanime discovered is that the MBR supplied with syslinux will only ever boot the partition marked with the boot flag, so the partition that the mbr is on has no impact on which is partition is booted from. So even if you chainload the correct partition the chainloader loads the mbr which loads the incorrect partition (in your case clay the grub partition).
I wasn't aware of this behaviour when I advised you to do it this way, sorry.
There is a simple alternative I have found after a bit of googling. There is an MBR system called boot control which allows you to manually select which partition to boot from.
It seems like a pretty neat solution.
That doesn't seem to explain why I am still able to chainload Puppy in partition #2 and System Rescue CD in partition #3, and for a few days, was even chainloading Ubuntu Live CD in partition #5.  I really thought I went through the same conversion process from ISOLINUX to EXTLINUX for each, yet some work, some don't, and one did work but now doesn't.

---

### Post by staticanime on 2009-06-02
> **clay_glenn said:**
> That doesn't seem to explain why I am still able to chainload Puppy in partition #2 and System Rescue CD in partition #3, and for a few days, was even chainloading Ubuntu Live CD in partition #5.  I really thought I went through the same conversion process from ISOLINUX to EXTLINUX for each, yet some work, some don't, and one did work but now doesn't.

I have a feeling I can explain that for you clay. Partitions 2 and 3 are primary, right? and 5+ are in an extended partition?
I think that becuase your Ubuntu CD is in an extended partition, it won't boot, becuase the extended partition needs a psuedo-MBR (it might be possible to write a bootable MBR to /dev/sdX4 (where X is your USB device) and maybe then it will work?

---

### Post by mick8985 on 2009-06-02
> **clay_glenn said:**
> That doesn't seem to explain why I am still able to chainload Puppy in partition #2 and System Rescue CD in partition #3, and for a few days, was even chainloading Ubuntu Live CD in partition #5.  I really thought I went through the same conversion process from ISOLINUX to EXTLINUX for each, yet some work, some don't, and one did work but now doesn't.

You're right, it doesn't explain why it works for you. It seems like the MBR is behaving differently for each of you... :confused:

---

### Post by staticanime on 2009-06-02
> **mick8985 said:**
> You're right, it doesn't explain why it works for you. It seems like the MBR is behaving differently for each of you... :confused:

I can answer that possibly lol. My disc is a GUID partitioned disc with a hybrid GPT+MBR partition table (it's for booting Macs and PC's, hence the need for Chameleon). My disc's main boot code is b oot0 from chameleon, and my Mac OS X partition's MBR is boot1h from Chameleon. I might try and see if boot1h can make the other partitions work too?

---

### Post by clay_glenn on 2009-06-02
And mine is an 8Gb USB memory stick.  I used GPARTED to create, size and format the partitions.  The first partition is FAT for sharing data, and the rest are EXT2.  My main GRUB is also in the first partition.

---

### Post by mick8985 on 2009-06-02
clay: reading the documentation of syslinux I have found a very interesting alternative since you only intend on using images of linux livecd's it should work very well for you, and allow you to add as many images as you like without needing to create partitions
[http://syslinux.zytor.com/wiki/index.php/SYSLINUX#KERNEL_file]("http://syslinux.zytor.com/wiki/index.php/SYSLINUX#KERNEL_file")
You can use isolinux to chainload a livecd image.
So you can format the entire disk in FAT, add as many images as you like, and just create your own isolinux.cfg with entries for each livecd iso you wish to use. You could make a nice menu similar to the ubuntu livecd with each distro on it.

---

### Post by staticanime on 2009-06-02
> **mick8985 said:**
> clay: reading the documentation of syslinux I have found a very interesting alternative since you only intend on using images of linux livecd's it should work very well for you, and allow you to add as many images as you like without needing to create partitions
[http://syslinux.zytor.com/wiki/index.php/SYSLINUX#KERNEL_file]("http://syslinux.zytor.com/wiki/index.php/SYSLINUX#KERNEL_file")
You can use isolinux to chainload a livecd image.
So you can format the entire disk in FAT, add as many images as you like, and just create your own isolinux.cfg with entries for each livecd iso you wish to use. You could make a nice menu similar to the ubuntu livecd with each distro on it.

Any chance of a guide on using Syslinux to do just that? *hint hint* lol

---

### Post by mick8985 on 2009-06-02
Yeah sure, I am looking into it now actually, seems like the best possible method, and not something I have seen done elsewhere on the net.

---

### Post by staticanime on 2009-06-02
> **mick8985 said:**
> Yeah sure, I am looking into it now actually, seems like the best possible method, and not something I have seen done elsewhere on the net.

Sweet. I'm looking into Grub4DOS (becuase I can use it to chainload XP setup) which is part of a program called WinSetupForUSB. Might see if using Grub4Dos might help me out some, as I think it doesn't need to know the exact disk number, only the partition on the disk you want to boot

---

### Post by clay_glenn on 2009-06-02
> **mick8985 said:**
> clay: reading the documentation of syslinux I have found a very interesting alternative since you only intend on using images of linux livecd's it should work very well for you, and allow you to add as many images as you like without needing to create partitions
[http://syslinux.zytor.com/wiki/index.php/SYSLINUX#KERNEL_file]("http://syslinux.zytor.com/wiki/index.php/SYSLINUX#KERNEL_file")
You can use isolinux to chainload a livecd image.
So you can format the entire disk in FAT, add as many images as you like, and just create your own isolinux.cfg with entries for each livecd iso you wish to use. You could make a nice menu similar to the ubuntu livecd with each distro on it.
I only want the shared data partition to be a FAT partition.  I want the others to be ext2, so they are not visible in Windows.  I want a separate container (partition) for each Live CD so that I can easily update them or add new ones without borking up the rest of them in any way.

I will try an experiment tonight.  I will install Puppy linux to a new partition #9 and see if it will chainload.  Since it installs its own bootloader, it should install it correctly as it did in Partition #2.  If it chainloads fine from partition #9, then I can conclude my problem is not with Primary vs. Logical partitions.

---

### Post by mick8985 on 2009-06-02
clay the way I am suggesting would function exactly the same way as having individual partitions, without actually using partitions, each distro would be self contained in its own image containing it's own filesystem

---

### Post by clay_glenn on 2009-06-02
> **mick8985 said:**
> clay the way I am suggesting would function exactly the same way as having individual partitions, without actually using partitions, each distro would be self contained in its own image containing it's own filesystem

That does sound interesting.  Each Live CD is downloaded as an .iso file.  If I put a bunch of .iso files into my FAT partition, how would I load those environments?  Can I somehow call up the .iso file directly from GRUB and have it chainload the ISOLINUX that is inside the .iso file?

In addition to the Live CDs, I'm also doing actual installs of a couple of small linux distros: Puppy and maybe Damn Small Linux.  So I probably still need the individual partitions there.

---

### Post by clay_glenn on 2009-06-03
> **clay_glenn said:**
> 
I will try an experiment tonight.  I will install Puppy linux to a new partition #9 and see if it will chainload.  Since it installs its own bootloader, it should install it correctly as it did in Partition #2.  If it chainloads fine from partition #9, then I can conclude my problem is not with Primary vs. Logical partitions.

I tried the Puppy Linux experiment above, installing it directly into partition #9 the same way that I had installed it into partition #2 previously.  When attempting to start it from GRUB using the chainloader, I got the "Boot error" on Logical Parition #9, where on Primary Partition #2, the chainloader loads Puppy linux just fine.

I'm starting to think that it is not something inside the Logical Partitions that is causing the "Boot error", but rather something in the way the MBR or GRUB accesses the logical partitions that is causing the problem.  It feels like I am getting very close to getting everything working, but I'm missing something key that makes everything play together.

Anyone else having any luck using the chainloader to boot from logical partitions?

---

### Post by mick8985 on 2009-06-03
Clay, I imagine the reason is that the drivers for dealing with logical partitions are part of the linux kernel. ie you need to load the kernel before you can access a logical partition.
That can be done, but not by using chainloader.

---

### Post by ellipsic on 2010-05-20
I just tried to boot 10.4 LTS for amd64 following this Howto. When I try to boot from USB, I don't even get to "boot :", but there's an error message : 
> EXTLINUX 3.53 Debian-2009-03-09 EBIOS Copyright (C) 1994-2007 H. Peter Anvin
Unknown keyword in syslink.cfg
And then nothing happens. 

So I'm not really sure what's going on... any ideas?

---

### Post by mick8985 on 2010-05-20
I don't have an ISO for 10.04, I do have one for Alpha 5 but I can't find a file named syslink.cfg. I will download the ISO and get back to you.
Incidentally this tutorial is pretty old and I haven't used this method for some time now. I just assumed everyone would just be using the graphical tool ubuntu provides. Why have you not opted to use that tool, just a general hatred of Microsoft filesystems?

---

