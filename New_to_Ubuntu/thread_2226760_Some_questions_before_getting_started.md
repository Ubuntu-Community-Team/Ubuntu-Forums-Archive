---
title: "Some questions before getting started"
date: 2014-05-28
forum: New to Ubuntu
---

### Post by codeybailey on 2014-05-28
Hello!

Before I get started with Ubuntu, I have a few questions:

1.Can I boot it on a 4gig USB flash drive?[INDENT]a. Does this affect anything,performance wise, like gaming?[/INDENT]

2. Since my main OS is win7,will it affect the files in anyway?[INDENT]a.Could I switch back and forth between both with ease?[/INDENT]

3.Do I need special drivers for my graphics card(Nividia GTX660) or any other hardware?

4. Do I need to get special software in general?

Thanks!\\:D/

-Codey

---

### Post by Bucky Ball on 2014-05-28
Welcome. I'll give it a shot:

1. Yes (but a dual-boot will be better, where Ubuntu is on its own partition on the hard drive, esp. for gaming);
1.a See last answer; USB slower;

2. No.
2.a You will need to restart the machine to change from one OS to another;

3. Possibly;

4. What kind of special software exactly?

Hope that helps.

---

### Post by codeybailey on 2014-05-28
> **Bucky Ball said:**
> Welcome. I'll give it a shot:

1. Yes (but a dual-boot will be better, where Ubuntu is on its own partition on the hard drive, esp. for gaming);
1.a See last answer; USB slower;

2. No.
2.a You will need to restart the machine to change from one OS to another;

3. Possibly;

4. What kind of special software exactly?

Hope that helps.
Thanks for answering. So if I boot on a usb then all of its files will be on that drive or in a folder somewhere on the HDD?

For the software,anything that maybe needed from the setup to startup.


I'm not very good with the partition thing. Can you explain this to me?

---

### Post by Bucky Ball on 2014-05-29
> **codeybailey said:**
> Thanks for answering. So if I boot on a usb then all of its files will be on that drive or in a folder somewhere on the HDD?

For the software,anything that maybe needed from the setup to startup.


I'm not very good with the partition thing. Can you explain this to me?

The OS will be on the USB in a partition '/'. Everything else will also be on the USB unless you set it up manually and put a separate /home (where your data and settings go) on the hard drive. 

You don't need any other software to install Ubuntu. Everything you need will be on the install disk. Best to 'Try Ubuntu' when you boot from the USB, get to a desktop and see what hardware works and what doesn't. Things can be fixed/drivers installed when you are installed to the hard drive, but problematic attempting to do that from a LiveCD boot. 

The first link on this search:

[https://duckduckgo.com/?q=manual+partitioning+ubuntu](https://duckduckgo.com/?q=manual+partitioning+ubuntu)

... will get you started, but there are plenty of others, as you can see. Even though that first link is for 11.04 the principles are the same and not much has really changed. Just look for 'Something Else' option when you get to the partitioning section of the install.

You will need some free space/unallocated space on the HDD if you intend to create a partition there. If you are using Win7 or above and need to shrink that partition (as Win installs often just use the entire disk), you will need to shrink the Win OS partition with the Win software, NOT using a Ubuntu LiveCD. The latter will screw things up royally. 

FYI: If you don't have the whole install on the USB the option to plug and boot your USB dongle on any other machine will not be available. If that is what you intend to do then the option of / on the USB and /home and /swap (2Gb) on the HDD is not for you. 

Unless there is a good reason you must have Ubuntu booting from USB, a dual-boot is the best way to go, if you have room on the internal hard drive to do one. You will need enough free space to create these partitions, just as basic, if you want a separate /home (not necessary but has its advantages):

/ = for the OS, 20Gb should be fine;
/home = for your data and settings, large as you like;
/swap = like a Win pagefile, 2Gb is fine unless you hibernate, in which case make it the same size as your installed RAM. 

If you don't create a separate /home partition then a /home folder will be created in / by default, if you get my drift ... You should create the 2Gb /swap though, regardless. 

Hope that helps get you started/thinking. Fire away with any further questions and good luck. ;)

---

### Post by squakie on 2014-05-29
If I may, I'll add a little something I hope doesn't muddy up the waters.

There is something called persistence - basically a way to make things you install while booted from USB "persistent", e.g "remembered" from one boot to the next.  To have that, you must select it when creating the USB flash drive.  To do so, allowing you to move from 1 PC to another, you're going to need something larger than a 4GB flash drive.  Without it, you can install whatever you want when running off the USB flash drive, but it will be lost everytime you shutdown.

Don't know for sure if you are looking for that, but I wanted to bring it up.  Most of the posts I have seen on this have recommended a minimum 16GB flash drive.  I don't know if 8GB would be enough or not.  I haven't had to do this in quite some time, so things may have changed some, but the persistence is still an option and won't be there by default.

---

### Post by jakke1975 on 2014-05-29
The above comment about persistence only applies to the LIVE function on your usb installer. If you actually install Ubuntu on your hard drive, please ignore the comment ;)
The persistence just creates space on your bootable usb so that you can save software and settings that you can re-use on other computers without having to re-set your configuration or download software again for use on your live installer.
Hope this clears up some of the muddied water :)

---

### Post by squakie on 2014-05-29
The OP was talking about using a USB flash drive - the only reason I mentioned persistence is some have a misunderstanding of using the "Try Ubuntu" option thinking that they can install things then take the flash drive to another computer.  I probably shouldn't have said "muddying up the water" as it brought a negative thought into what really is a relevant thing to know.

---

### Post by mastablasta on 2014-05-29
if you boot from live USB and select "try it" the system is loaded into RAM all files on disk are intact, it is difficult ot install extra drviers with no persistance availabel on live boot.

if however you decide to install the OS on USB then you need a bigger USB (8GB should do). it will be slow though.

best way is to setup a separate partition.

depending a bit on how windows 7 was installed - but generally all you need to do is create free (unformatted) space on disk and then on install select the option to use largest free disk space. the rest of partitioning is done automaticly. this is the easiest way and only work if windows has less than 4 primary partition (on MBR setup) and it works best if free space is at the end of disk i believe. free disk space can be created using widnows disk manager. you just shrink the partition you want to make smaller there.

---

### Post by squakie on 2014-05-29
And a slight but important addition when resizing a partition - always defrag the disk, preferably twice, in Windows prior to resizing.  As mastablasta said, use the windows tools, in this case disk management, to do the resizing.  After resizing, and prior to installing Ubuntu, reboot Windows.  Sometimes Windows needs to check the disk after resizing and best to find out if there is a problem prior to writing into the newly created free space.

---

### Post by stalkingwolf on 2014-05-29
is the install alongside option still available? sounds like that would be the way to go for the OP.

as far as software goes if you are talking about everything needed for a functioning operating system with the possible exception of additional drivers to get complete functionality of graphics or a wireless adapter, yes.  you can also install 3rd party software at install (flash comes to mind).

If you mean 'EVERYTHING" then no, and it definately will not go on a 4gb thumb drive as at current count on my mint install there are 41,000 packages available and many others not in the repositories.

I also suggest trying the live try ubuntu feature.  It will be a bit slower than when installed but gives you a chance to dig about a bit before making permanent changes.

id suggest also if your goal is to have it installed on a flash drive look at some of the lighter releases like lubuntu and kubuntu, maybe bodhi.   I have Mint 13 maya installed
with all the packages i need on a 16gb stick with plenty of room.

---

### Post by LastDino on 2014-05-29
Well, USB wont come close to performance of HD, unless we are talking about SSD. People generally *install* on USB in case they have some specific needs, not for general purpose as it will effect your Ubuntu experience considerably.  If you've spare HD or SDD, I would suggest installing on that, if not, do your research on partitioning and follow above mentioned tips to dual boot. 

Do not forget to take backups of your win7 Installation and other files.

---

