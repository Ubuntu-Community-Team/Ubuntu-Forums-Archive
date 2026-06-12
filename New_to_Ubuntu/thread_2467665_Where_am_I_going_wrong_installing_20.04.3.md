---
title: "Where am I going wrong installing 20.04.3"
date: 2021-10-03
forum: New to Ubuntu
---

### Post by loybanks on 2021-10-03
Wanting to install Ubuntu 20.04.3 into my older HP Laptop. But so far doing everything wrong. Am attaching a pic of my HP Laptop. This machine does not have any OS in it. Hence that's why I want to install Ubuntu. So far everything I try has gone down the tubes. I have been trying to learn Linux Hard Drive System. Trying to learn gparted and using live gparted, but so far that has not helped either. Bearing in mind I am 81 years old, which doesn't make concentration any easier. But I am trying! I have LinuxMint 20.02 on my Primary HP Desktop Machine. However I sure could use some help with the current install mess. So hope someone out there will lead me down the proper path. Thanks so much in advance.     Loy Banks

---

### Post by Skaperen on 2021-10-03
i would recommend limiting your use of partitions to just 1, 2, 3, and/or 4.  using extended partitions complicates the addresses because it adds an extra table to define each partition after number 4.  if you want to have 2 operating systems on there, you may well have to use extended partitions to have enough of them.

my own partition strategy is partition 1 is for the system ([FONT=courier new]**/**[/FONT]), partition 2 is swap space (sometimes i put swap on partition 3), partition 4 is for my data ([FONT=courier new]**/home**[/FONT]).  i usually have 16GB to 32GB for partition 1, 16GB for swap, and all of the remainder for [FONT=courier new]**/home**[/FONT].  i don't want more swap even for a giant machine.  using swap just slows down the system.  however much time you can tolerate waiting for some action like a click or command to happen, see how much data your computer can read from disk in that much time.  triple that amount.  you don't need any more swap than that final number.  if your programs might need more, go ahead and make more swap but work on getting more RAM if you can.  if you can't expand RAM then you will need larger swap and expect a slower machine.

---

### Post by grahammechanical on 2021-10-03
First, the hard drive has the Master Boot Record partitioning (MBR) scheme. This limits us to four primary partitions. To have more than four partitions we need to use one of the primary partitions as an Extended partition and inside the Extended partition we can create other partitions. They are called Logical partitions. This is the set up you have already. It complicates installing any Linux Distribution.

Seeing as there is nothing on that hard drive that you want to keep you can use the Installer's option to erase disk and install Ubuntu. If you are given a option to set the partitioning scheme and the choice is between MRB and GPT, then choose GPT. it is modern and we can have as many partitions as we like. I have not explained what GPT is. It will only complicate the matter.

You do not tell us what is going wrong. Have you read the official Ubuntu installation guides? The simplest method of installing Ubuntu is to load the Ubuntu live session from DVD or USB memory stick and select Install Ubuntu and then select Erase Disk and Install Ubuntu. Let the installer have its way with the hard drive. Answer the questions and do not for get your user password.

You are using this machine for training. So, once you have mastered this method of installing Ubuntu you can then try out the more complicated methods that you might need to use on your main PC.

Regards

---

### Post by Skaperen on 2021-10-03
if you are doing first install on this machine and don't need it right now for other than learning, then make use of the fact that you don't need to make backups to learn different ways to do the install such as "something else" during disk setup.  i always go there, myself, to do the setup i mentioned in my previous post.

years ago at a job i had where i used Windows, Solaris and Linux, they had everyone upgrade to a new version of Windows.  instead of an in-place upgrade, i got the install CDs and did a fresh install.  i repeated the fresh install with changes decided from the previous install. in about 5 days i finally had it the way i wanted it.  mine never crashed and everyone (everyone) else had 1 or 2 crashes a day.  a few had 3 or 4.  the people running the Windows network (i was the internet admin) depended on those crashes to eventually get everyone off certain file servers so they could back them up.  turns out my Windows box locked out their backups for almost a month until they figured out it was me.  i agreed to reboot it every morning.  they also wanted me to be a Windows admin.  i told them it worked like that as an accident.

---

### Post by poorguy on 2021-10-03
Just follow the how to in the links and let the Ubuntu installer do the partitioning and install the distro.

[https://www.tecmint.com/install-ubuntu-20-04-desktop/](https://www.tecmint.com/install-ubuntu-20-04-desktop/)

[https://itsfoss.com/install-ubuntu/](https://itsfoss.com/install-ubuntu/)

---

### Post by oldfred on 2021-10-03
What model HP?

If before 2012 then it is an older BIOS based system.
If after 2012, it will be UEFI (even if called BIOS by vendor) as Microsoft required all vendors to install Windows in UEFI boot mode to gpt partitioned drives.
Partitioning gpt or MBR and install are different if UEFI or BIOS.
With Ubuntu you even can use gpt partitioning with a BIOS install. (I have since about 2010 on my BIOS systems).

But if using gpt, you need extra partitions for it to install correctly. 
If UEFI, you need an ESP - efi system partition as FAT32.
If BIOS and gpt partitioned, you need a tiny 1 or 2MB unformatted partiton with the bios_grub flag.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

Once we know if UEFI or BIOS based system, we can give better details on how to install.

---

### Post by loybanks on 2021-10-04
Model HP-dv7-6157cl Entertainment Laptop PC. Shows [with Legacy BIOS]("http://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/HP-dv7-6157cl-Laptop-with-Legacy-BIOS-in-Windows-10Pro/m-p/6114774#M396202"). Which I would assume is not the UEFI.

---

### Post by loybanks on 2021-10-04
So I just checked the BIOS and it is the old legacy version. No UEFI at al. So what must I do to get Ubuntu installed to this older machine? As for the Ubuntu file I earlier downloaded the ISO and copied over to CD. The CD is what I have been using to install all along. Just went thru the install again and it did not install. This time stopped install at message ....Executing grub_install/dev/mmcblko FAILED! So where do I go from here to get this installed. Thanks in advance. Still should have the files installed per my original message image.

---

### Post by Dennis N on 2021-10-05
> Executing grub_install/dev/mmcblko FAILED!

This looks like grub will be installed by default to a multi-media card (mmc) which may be present. In a BIOS install, you should to select **sda** for the grub installation. To do that, you use the "Something Else" option at the "Installation type" screen, and select **sda** in "Device for boot loader installation" at bottom of the next screen. 

Besides that, on the same screen, you also need to specify which partition to use for installing the OS itself. Select the partition to use, then use the "Change" button and tell the installer in the popup window that this is used for the root (/) partition and formatted ext4.

---

### Post by loybanks on 2021-10-05
Well I went thru the install procedure again this morning, but still came up Boot Device Not Found. I tried to follow Dennis N. instructions, but some of what he related to specifically is not included in actual instructions. IE there was no mention of Grub anyplace in the install. Also is the Ext 4 journalizing file system where I should install the main files? What about the Boot Loader. Where does it come into being? Also I am wondering if this older machine with a Legacy BIOS is really meant to have Ubuntu installed? 

[B]I wonder is there a Page out there in Internet Land that applies directly to installing Ubuntu 20.04, with comments about what one might expect to find, what will you find and what has to be there to make the whole thing work? So many turns and in and outs it just boggles the mind.

[/B]Well still needing help with this problem. Many thanks to all.

---

### Post by GhX6GZMB on 2021-10-05
Normally, the installer will do the job for you. But not always.
First a Disclaimer: I'm very experienced with Lubuntu (four old HP laptops running 20.04), but it has a different installer (Calamares). Still, the functionality is approximately the same.

You've gotten past the BIOS, and are booting from the DVD/USB. That's the first step mastered.

After the select region, language, keyboard, blabla etc., select Manual Partitioning.

1st partition: 20...30 GB, format, ext4, mount point: /, boot flag
2nd partition: SWAP (this is optional)
3rd partition: rest of disk, format, ext4, mount point: /home, no flag.

This works every time. And I've done it at least 50 times.

PS: Ubuntu is a bit heavy for older HPs. But if you want to try Lubuntu or other dialects, PLEASE go through ubuntu.com, There are a couple of cybersquatter sites active.

---

### Post by Dennis N on 2021-10-05
> **loybanks said:**
> Well I went thru the install procedure again this morning, but still came up Boot Device Not Found. I tried to follow Dennis N. instructions, but some of what he related to specifically is not included in actual instructions. IE there was no mention of Grub anyplace in the install. Also is the Ext 4 journalizing file system where I should install the main files? What about the Boot Loader. Where does it come into being? Also I am wondering if this older machine with a Legacy BIOS is really meant to have Ubuntu installed? 

[B]I wonder is there a Page out there in Internet Land that applies directly to installing Ubuntu 20.04, with comments about what one might expect to find, what will you find and what has to be there to make the whole thing work? So many turns and in and outs it just boggles the mind.

[/B]Well still needing help with this problem. Many thanks to all.

See the attached image - this is the screen you should be looking at.
Grub is the name of the bootoader, so they are synonymous. "**Device for boot loader installation**" at the bottom is where to install grub. Choose **sda** for this.

The following from memory - I do not have the installer running to look at it, but your display at the top will be different, since you already have some partitions!

The OS will be installed on the partition you select in the display. After selecting, click the "change" button - it brings up a little dialog asking how to use the partition you selected. So you select "use as ext4 journaling filesystem" here. It also asks if you want to format it. Check that. There is another question in the dialog which asks for "mount point". Choose root (symbolized as /). 

Then you are ready to click on "Install"!

---

### Post by loybanks on 2021-10-05
I am attaching some photos to give you an idea what I am dealing with trying to get this installed in the old HP Laptop. As mentioned with a legacy BIOS. Well I just thought I would be providing some photos. But looks like they want URL's to the Photos.  I should be able to just post the photo. Actually just trying to sign in to Ubuntu is a  real challenge. Every time I go around and around just getting signed in. I am sure the approach does discourage many people from joining in. Just too challenges to go thru. OH Well! What do I know!  Well I am out of ideas. Absolutely discouraged  with this install.

---

### Post by QIII on 2021-10-05
I am able to sign in and out dozens of times a day.  That is done, by the way, using Ubuntu One and we do not control that.

To post images, use the attachment facility via the "paperclip" button above the text entry box.  If you are trying to edit an existing post to do so, use the "Go Advanced" button at the bottom right to pull up more of the top buttons.

---

### Post by loybanks on 2021-10-05
Thanks for your input. It is appreciated. One aggravating issue for this old man. I am 81, it is my lack of patience at times. I try, but sometimes things just hit me wrong or...? Not to mention all the disgusting things going on in the world today. I have just about stopped watching news channels. OH well! What do I know! Thanks so much. Your input is appreciated. :)

---

### Post by loybanks on 2021-10-05
Thanks for your input. It is appreciated. One aggravating issue for this old man. I am 81, it is my lack of patience at times. I try, but sometimes things just hit me wrong or...? Not to mention all the disgusting things going on in the world today. I have just about stopped watching news channels. OH well! What do I know! Thanks so much. Your input is appreciated. :)

---

