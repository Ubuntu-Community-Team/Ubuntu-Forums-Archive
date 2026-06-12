---
title: "Installing with Flash Drive on Mac"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by Acala on 2012-04-22
Hello, everyone.  I am a complete beginner (I have literally not used Linux), and I am trying to install Ubuntu on a Mac with a flash drive.

I have attached the installation guide to this post.  I am having trouble with the commands in the terminal that it requires.  I have opened the terminal and tried copying and pasting and modifying what they did in any way that I think would help, and I can't get anything out of it.  I also have never used the terminal until this.

I know it says on the installation guide that it does not recommend flash drives for Mac, but rather CDs.  If I cannot get this by tonight, I will get a CD tomorrow and do it the simple way.  Thanks for the help.

---

### Post by Curtis6767 on 2012-04-22
I'm using a PC and I just downloaded 12.04 and tried to install it on a USB, but it didn't work. 

Do a search of issues that come up with USB's and what you have to do to insure that you can load Ubuntu on to the USB. It can be done, but it's not as simple as it sounds.

I ended up using a CD.

---

### Post by pissedoffdude on 2012-04-22
> **Acala said:**
> Hello, everyone.  I am a complete beginner (I have literally not used Linux), and I am trying to install Ubuntu on a Mac with a flash drive.

I have attached the installation guide to this post.  I am having trouble with the commands in the terminal that it requires.  I have opened the terminal and tried copying and pasting and modifying what they did in any way that I think would help, and I can't get anything out of it.  I also have never used the terminal until this.

I know it says on the installation guide that it does not recommend flash drives for Mac, but rather CDs.  If I cannot get this by tonight, I will get a CD tomorrow and do it the simple way.  Thanks for the help.

You should be able to create a bootable flash drive by opening disk utility, going to restore, and selecting the ubuntu iso.  Then when you reboot, hold down the option key (or alt, not 100% sure which it is) and it'll detect your ubuntnu flash drive.  You can also make your flash drive bootable with unetbootin.  Once you get ubuntu running off of your flash drive, you have two options for booting it: rEFIt, or grub2.  I suggest you use rEFIt and place grub onto the partition you install ubuntu on.

---

### Post by Acala on 2012-04-22
> **pissedoffdude said:**
> You should be able to create a bootable flash drive by opening disk utility, going to restore, and selecting the ubuntu iso.  Then when you reboot, hold down the option key (or alt, not 100% sure which it is) and it'll detect your ubuntnu flash drive.  You can also make your flash drive bootable with unetbootin.  Once you get ubuntu running off of your flash drive, you have two options for booting it: rEFIt, or grub2.  I suggest you use rEFIt and place grub onto the partition you install ubuntu on.

I don't understand.  I went to disk utility and restore, and it has a source and destination.  Will the flash drive be the source or the destination?  And will it have the .iso file on it already?  And then, what will be in the other spot?  Thanks.

---

### Post by pissedoffdude on 2012-04-23
> **Acala said:**
> I don't understand.  I went to disk utility and restore, and it has a source and destination.  Will the flash drive be the source or the destination?  And will it have the .iso file on it already?  And then, what will be in the other spot?  Thanks.

You want your flash drive to be the destination.  Select the ubuntu iso as your source. This will put the contents of the ubuntu iso on your flash drive so that it becomes bootable.  If you get an error while trying to do this, select the name of your flash drive rather than the drive itself in the disk utility.

Then you must figure out how you will boot ubuntu once it is installed.  You need something called a boot loader to do this.  Ubuntu comes with one called grub, but I wouldn't recommend it as your default boot loader.  Instead, I recommend you use rEFIt and put grub on the same partition as your ubuntu installation. 

I also advise you to check out the ubuntu documentation concerning installation on macs: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation")

---

