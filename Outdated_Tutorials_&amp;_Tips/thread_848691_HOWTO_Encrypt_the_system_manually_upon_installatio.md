---
title: "HOWTO: Encrypt the system manually upon installation"
date: 2008-07-03
forum: Outdated Tutorials &amp; Tips
---

### Post by hyper_ch on 2008-07-03
[SIZE="5"]Introduction[/SIZE]

Another howty by me concerning encryption. However this one will be pretty intens on graphics. I have a step-by-step guide on how to do a manual full encryption of the system.

Due to a bug current in the ubuntu installation, you cannot encrypt the swap partition directly during the manual install. The install will just hang. Here's a link to the bug report: [https://bugs.launchpad.net/ubuntu/+bug/231451](https://bugs.launchpad.net/ubuntu/+bug/231451)

Also the sizes used were just exemplary... please consider carefully how you want to size your partitions. I did this on a 15 GB virtual image, hence swap, root, home are quite small. As I've just told, I will make a seperate home partition. If you need to reinstall, you can just follow this guide again BUT leave the /home partition untouched during installation. Once you've setup then boot, swap and root, you can manually add the /home partition into the local filesystem and setup it up to automatically unlock by a key.

Because I used a virtual machine for creating this howto, I also set all partitions to be primary partitions. Remeber, you can only have 4 primary partitions on a harddisk. You could also create a logical partition and make partitions in there.

Due to the restrictions of 8 pics per post, I will split it up into multiple posts.

[SIZE="5"]Step 1: Getting to the partitioner[/SIZE]

So, once you reach the partitioner, select manual partitioning:
[IMG]http://www.sjau.ch/cryptosetup/01_manual.png[/IMG]

As I have a completely new harddisk (or rather virtual harddisk) I have to select it first:
[IMG]http://www.sjau.ch/cryptosetup/02_main.png[/IMG]

Then to create an empty partition list:
[IMG]http://www.sjau.ch/cryptosetup/03_emptypartition.png[/IMG]

Now we got a blank harddisk with an empty partition list:
[IMG]http://www.sjau.ch/cryptosetup/04_emptyspace.png[/IMG]

---

### Post by hyper_ch on 2008-07-03
[SIZE="5"]Step 2: Creating the boot partition[/SIZE]

Now we select to create a new partition on the harddisk:
[IMG]http://www.sjau.ch/cryptosetup/05_boot_newpartition.png[/IMG]

About 100 MB is a good size for a boot partition... that will be sufficent for multiple kernels. However it's up to you how big you want to make it.
[IMG]http://www.sjau.ch/cryptosetup/06_boot_100mb.png[/IMG]

Well, as said in the introduction I make all the partitions primary ones. If you want to create a logical one, make it as big as you want so that all other partitions will fit within.
[IMG]http://www.sjau.ch/cryptosetup/07_boot_primary.png[/IMG]

I set it at the beginning.  You could also set it at the ened... IMHO it doesn't matter much.
[IMG]http://www.sjau.ch/cryptosetup/08_boot_beginning.png[/IMG]

And then we finally get to the partition properties. Make sure to select as filesystem ext3, as mount point /boot and make it bootable.
[IMG]http://www.sjau.ch/cryptosetup/09_boot_properties.png[/IMG]

---

### Post by hyper_ch on 2008-07-03
[SIZE="5"]Step 3: Creating the swap partition[/SIZE]

Afterwards we end in the main partitioning menu again. Select the free space:
[IMG]http://www.sjau.ch/cryptosetup/10_swap_main.png[/IMG]

Make a new partition:
[IMG]http://www.sjau.ch/cryptosetup/11_swap_newpartition.png[/IMG]

I select here 256 MB ram because it's just a virtual drive. Generally you should make it about twice your ram size but not more than 4 GB, except if you want to hibernate and have more than 4 GB ram. You should make it then at least equal your ram size.
[IMG]http://www.sjau.ch/cryptosetup/12_swap_256mb.png[/IMG]

Again primary:
[IMG]http://www.sjau.ch/cryptosetup/13_swap_primary.png[/IMG]

Again at the beginning:
[IMG]http://www.sjau.ch/cryptosetup/14_swap_beginning.png[/IMG]

Set the properties according to the picture:
[IMG]http://www.sjau.ch/cryptosetup/15_swap_properties.png[/IMG]
Remember, this will not be immediately setup due to the bug here: [https://bugs.launchpad.net/ubuntu/+bug/231451](https://bugs.launchpad.net/ubuntu/+bug/231451) - we'll setup swap once we installed the system.

---

### Post by hyper_ch on 2008-07-03
[SIZE="5"]Step 4: Creating the "/" folder[/SIZE]

Afterwards we end in the main partitioning menu again. Select the free space:
[IMG]http://www.sjau.ch/cryptosetup/16_root_main.png[/IMG]

Make a new partition:
[IMG]http://www.sjau.ch/cryptosetup/17_root_newpartition.png[/IMG]

I select here 5 GB as root. This is because of the virtual disk. Normally you should use at least 10 Gb.... better 20 Gb to have enough space to install all the apps you want.
[IMG]http://www.sjau.ch/cryptosetup/18_root_5gb.png[/IMG]

Again primary:
[IMG]http://www.sjau.ch/cryptosetup/19_root_primary.png[/IMG]

Again at the beginning:
[IMG]http://www.sjau.ch/cryptosetup/20_root_beginning.png[/IMG]

Set the properties according to the picture however you can change encryption, key size and algorithm according to your preferences. Make sure the encryption key is a passphrase.
[IMG]http://www.sjau.ch/cryptosetup/21_root_properties.png[/IMG]

---

### Post by hyper_ch on 2008-07-03
[SIZE="5"]Step 5: Creating the "/home" folder[/SIZE]

Afterwards we end in the main partitioning menu again. Select the free space:
[IMG]http://www.sjau.ch/cryptosetup/22_home_main.png[/IMG]

Make a new partition:
[IMG]http://www.sjau.ch/cryptosetup/23_home_newpartition.png[/IMG]

use all the remaining disk space for your home folder. That's where you normally want to store most of your data.
[IMG]http://www.sjau.ch/cryptosetup/24_home_restspace.png[/IMG]

Again primary:
[IMG]http://www.sjau.ch/cryptosetup/25_home_primary.png[/IMG]

Set the properties according to the picture however you can change encryption, key size and algorithm according to your preferences. Make sure the encryption key is a passphrase.
[IMG]http://www.sjau.ch/cryptosetup/26_home_properties.png[/IMG]

---

### Post by hyper_ch on 2008-07-03
[SIZE="5"]Step 6: Configure the encrypted devices[/SIZE]

Afterwards we end in the main partitioning menu again. Select the encrypted volumes:
[IMG]http://www.sjau.ch/cryptosetup/27_configureencrypted.png[/IMG]

Select here yes:
[IMG]http://www.sjau.ch/cryptosetup/28_configureencrypted_yes.png[/IMG]

Then enter the password for the root device (partition #3 sda):
[IMG]http://www.sjau.ch/cryptosetup/29_configure_password1.png[/IMG]

Verify the password for the root device:
[IMG]http://www.sjau.ch/cryptosetup/30_configure_password1_confirm.png[/IMG]

If your password is too weak you will get this error message. Either go back and fix it or accept it. However a weak password defeats the purpose of having encryption. I only selected yes, because it's a demo setup on a virtual machine. So once I'm done it gets deleted anyway.
[IMG]http://www.sjau.ch/cryptosetup/31_configure_password1_weak.png[/IMG]

Then enter the password for the home device (partition #4 sda):
[IMG]http://www.sjau.ch/cryptosetup/32_configure_password2[/IMG]

Verify the password for the home device:
[IMG]http://www.sjau.ch/cryptosetup/33_configure_password2_confirm[/IMG]

Again the week password message:
[IMG]http://www.sjau.ch/cryptosetup/34_configure_password2_weak.png[/IMG]

---

### Post by hyper_ch on 2008-07-03
[SIZE="5"]Step 7: Set the encrypted devices up[/SIZE]

Afterwards we end in the main partitioning menu again. You can see that we have two new devices there. We need to set those up now and start with the root partition:
[IMG]http://www.sjau.ch/cryptosetup/35_main_root.png[/IMG]

Set the properties according to this. Make sure to select "/" as mount point.
[IMG]http://www.sjau.ch/cryptosetup/36_root_properties.png[/IMG]

We end up again in the main partition menu and select now the home partition:
[IMG]http://www.sjau.ch/cryptosetup/37_main_home.png[/IMG]

Set the properties according to this. Make sure to select "/home" as mount point.
[IMG]http://www.sjau.ch/cryptosetup/38_home_properites.png[/IMG]

---

### Post by hyper_ch on 2008-07-03
[SIZE="5"]Step 8: Finish the partitioner[/SIZE]

For the last time we are now in the partitioner main menu. Select finish partitioning and write changes to disk:
[IMG]http://www.sjau.ch/cryptosetup/39_main_finish.png[/IMG]

You will get then a warning about swap. Just ignore it and go on:
[IMG]http://www.sjau.ch/cryptosetup/40_swap_warning.png[/IMG]

Write changes to disk and the let install continue:
[IMG]http://www.sjau.ch/cryptosetup/41_confirm_partitions.png[/IMG]

---

### Post by hyper_ch on 2008-07-03
[SIZE="5"]Step 9: Enable swap and setup key unlocking of /home[/SIZE]

Now after the system has finished installed, start it. You will be prompted to enter the crypto password twice. Once for the root partition and then a bit later for the /home partition. Once the computer has booted up run the commands
```

df -l
sudo fdisk -l

```
You should get an output similar to this one:
[IMG]http://www.sjau.ch/cryptosetup/42_systemstat.png[/IMG]

Enabling swap is pretty simple. You first need to edit the crypttab:
```

sudo nano /etc/crypttab

```

and there you need to add a line like this:
```

cswap	/dev/sda2	/dev/urandom	swap

```

Save and close it with ctrl-x (follow the instructions) and then open
```

sudo nano /etc/fstab

```

and add this line:
```

/dev/mapper/cswap	none	swap	sw	0	0

```

So, if you don't want to enter the password twice for unlocking the root and the home partition, follow this guide here: [http://ubuntuforums.org/showthread.php?t=837416](http://ubuntuforums.org/showthread.php?t=837416)

After you set that up accordingly, you can reboot and then you will have to enter the password only once and you will also have an encrypted swap at your disposal. Enjoy!

---

### Post by kevdog on 2008-07-03
Great tutorial -- I liked that a lot.  100mb boot partition is pretty stingy.  If you ever compile your own kernel, that space is going to fill up fast.  I see the value of separate home and swap partitions, however boot??  Seems like that should be on the root partition as well?

---

### Post by hyper_ch on 2008-07-04
try to encrypt the boot partition ;) that's not possible... however you could have the /boot partition on a cd-rom or something ;)

and for compiling own kernel.... well, I guess you got a point there ;)

---

### Post by kevdog on 2008-07-04
If you got the space -- most people do since HD space is cheap, I would recommend at least 500 Mb for boot if you plan on either keeping a bunch of old kernels or think you might ever roll your own vanilla kernel.  Maybe I just flat out suck at compiling kernels, however I can never make them as small as the kernels compiled by the ubuntu team.  I guess thats the difference between a neophyte and professionals.  I haven't compiled a kernel in a while, but at least 30-40 Mb of the /boot partition was taken up with my one custom kernel.  Everytime I recompiled -- trust me you will need to do the recompilation about 4-5 times the initial attempt to get things right -- I had to delete the previous compiled version first since I was running out of space on the /boot partition.

If you are not into experimenting, then forget everything I'm saying.  If you are into experimenting -- make the boot partition bigger than 100 Mb!!

---

### Post by hyper_ch on 2008-07-04
one can also recompile a kernel in a chroot ;) anyway, as I've pointed out, my guide is not so much about how to partition and what size each one shall have than rather doing a manual encrypted install ;)

---

### Post by kevdog on 2008-07-04
Yeah, I know I wandered off topic.

---

### Post by Thoralyon on 2010-05-29
I followed this guide way back and I did so now for a complete reinstall of lucid.

Last time it worked like a charm, but this time I thought I'd mount 2 physical harddrives to /media/xyz and /media/abc
Now i cannot create new folders on those drives, and all the encrypted drives show up in my places folder as locked driveicons, clicking on them nets me an error "unable to mount xGB filesystem, sdy_crypt is mounted"
this is the same behaviour than what appeared after an upgrade to 9.04 or 9.10 I don't quite remember.
How do I get rid of it?
And how to properly mount physical drives if i dont want to mount them as /home, where is the proper place to mount them?

thanks

---

