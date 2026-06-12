---
title: "HOWTO: Encrypted and Hidden Drive using GUI TrueCrypt"
date: 2008-11-22
forum: Outdated Tutorials &amp; Tips
---

### Post by ryukent on 2008-11-22
**Introduction**
This is a guide explaining how to create a secret encrypted drive the easy way using a graphic user interface. It covers installing and using the TrueCrypt software (version 6.1) and Ubuntu 8.10 Intrepid.

** Before we start**
Why would you want to create a encrypted drive? Why not? Probably the main reason is that you have some security sensitive file that you don't want other people to have access to. An encrypted drive provides a safe place to put these kind of files so that people cannot see or access them without a password.

Why would you want to create a hidden drive? There are 2 main reasons. The first is because you have sensitive files as mentioned above. Perhaps you don't want people to know they exist. The second reason is more serious. Recently a number of governments have implemented laws where you can be forced to provide encryption keys to officers (for example at airports) so that they can decrypt your files. It can be a criminal offence not to provide or to claim you have forgotten these keys. Imagine if you could comply, give them a key that they can use, decrypt some files you don't care about and still not have access to your sensitive files. Imagine if they could never prove that you were hiding any additional documents and that you could therefore show that you have been completely complaint with the law and yet still keep your files safe. This is now possible! 

DISCLAIMER: I do not, and will not ever advocate breaking laws. If you fail to prove an encryption key when legally required to do so, you could breaking the law. Don't do it.

** How it works**
Basically, first a container encrypted drive is created. Some non sensitive files are put on this drive. The remaining space is made up of random data. Then within this random data, a second hidden drive is placed. This drive can only be accessed with a second encryption key. Without that key it should be mathematically impossible to identify whether the random data is in fact random data or a second hidden encrypted drive. It could just be free space within the first drive. 

When forced under coercion to provide an encryption key, you provide the first one. They can decrypt the first container drive. They see you not so sensitive hidden files. They cannot ascertain if there is anything in the free space remaining and you have complied with the law and provided the decryption key. Provided the dummy files you have provided are interesting enough they'll probably be kept busy trying to work out why you encrypted them or simply feel happy you didn't  have anything worth finding.

The TrueCrypt system is easy to use, uses very strong encryption (US government agencies are authorised to use this cipher for all levels up to top secret), and is also windows and mac compatible for those people who share external devices with windows / mac systems too.

** Installing TrueCrypt**
TrueCrypt is not currently available in the repositories for various reasons (possibly licensing). It is opensource though and free for you to use. You need to download it from:

[ http://www.truecrypt.org/downloads.php]("http://www.truecrypt.org/downloads.php")

Go to the linux section and select Ubuntu DEB. 86 and 64-bit versions are available. It will come in a compressed file, so you'll need to decompress it and then run the deb file. It should install itself from then. The gui will become available in the 'other' folder in your applications menu. While you're at it, make sure you have the 'gparted' package installed too. This is the gnome partition editor and is available in the normal repositories.

** Two Different Types of Drive**
There are two different types of drive. One is stored like a normal partition on a physical drive. The other is stored in a container file. The file can then be stored anywhere that a normal file can. It can be renamed, copied, emailed etc. For the first example, we will use a physical drive. Then I will cover creating a file too. 

The benefits of a drive is that you just have don't have a file lying about that could draw attention to itself. For onlookers it will appear you just have an empty unformatted drive. Maybe it's new, maybe you haven't formatted it yet (actually you are hiding stuff there). The benefit of a file is that you don't need to do formatting or partitioning etc. You can send, move, copy, rename the file etc. Both systems use the same technology and are essentially just as secure, except that the file option obviously suffers from all the usual security issues with having a file.

** Using the Physical Drive Method**
In this example, we will use a USB key. I'm using the whole drive, you can use a partition on the key if you want, but I'm going to use the whole drive for simplicity. Make sure there is nothing on the drive you need. Then open gparted. This can be found in the System / Administration / Partition Editor menu. Ubuntu should automatically detect the device. If it has mounted existing volumes, dismount (eject) them. In gparted, find the drive in the drop down list at the top right. In my example it is /dev/sdb (117.66). If you're no sure, use the size to determine which drive. Warning, don't follow the next few steps on your primary hard disk or you could delete everything on your PC!!!

[ATTACH]93729[/ATTACH]

As you can see in my example, there are no partitions. That's what you want. If there are some existing ones, delete them (right click on them). Once you are finished, click on the apply button at the toolbar. It should bring you to a screen that looks something like the example. Unallocated is what you want. A disk that looks completely empty, no partitions. Remember the name of the drive (/dev/sdb in my case)

** Setting up the Encrypted Drives**
Open TrueCrypt (Applications / Other / TrueCrypt). Select Volumes / Create New Volume... Then select "Create a volume within a partition / drive". Then select "Hidden TrueCrypt Volume". You will now be prompted to select your device. Click on the "Select Device..." button and select the drive that we cleared earlier (/dev/sdb in my case). Clicking on next will bring up a warning message. Provided you have selected the correct drive, there is no danger of clicking OK. Please check you have selected the correct drive before proceeding.

At this point it will ask you for the encryption type to use for the outer volume. In the example, I have used AES as it is the most common cipher. You can change it if you want.

[ATTACH]93730[/ATTACH]

It will now prompt you to enter the outer volume password. This is the password you might have to divulge under duress. It should not be a dictionary word and should include a combination of letters and numbers. You probably don't want to have "Display password" on as in my example. 

[ATTACH]93731[/ATTACH]

Now select your file system. I recommend FAT as it is readable by windows as well.

The next screen will allow you to format this drive. Moving the mouse around a bit will allow you to generate a completely random seed to format the disk with. This fills it will random data. Finally, you will be prompted to open the outer volume. This is where you have the opportunity to place a few 'dummy' files that someone would be able to see if you provided them with the dummy key.

When you have finished, close the browser for that drive and return to TrueCrypt. Click on "next" and you will be prompted to go through the processes again for the hidden drive. You can just use the same encryption as you did for the first drive. Make sure that the password you use this time is different from the first one!

You will need to choose a size. This is the size that the hidden drive will take up. It needs to be smaller than the container drive because it sits in its free space. You will need to leave a couple of megabytes to store the dummy files in. Select FAT as the file system again and format. You have now set up your hidden drives.

** How to Mount the Drive**
There are two ways to mount the drive - automatic and manual. Automatic is less hassle but takes longer, manual requires you to select the device.

In the main TrueCrypt dialogue, select "Auto-Mount Devices". You will be prompted for your password. Here enter the password for the hidden drive (the second one you used earlier. TrueCrypt will search and find your device automatically. It will mount it in /media/truecrypt1. This is your hidden drive. Feel free to use it as you wish. Files stored there are automatically encrypted. Make sure you unmount it when you've finished. This can be done easily by right hand clicking on the TrueCrypt icon in the system tray and selecting "Dismount All Mounted Volumes".

[ATTACH]93732[/ATTACH]

** Manually Mounting**
Lets manually mount a drive and also see what happens if we try to mount the outer drive. Make sure you've dismounted the hidden volume, then click on "Select Device" button in TrueCrypt. Select your drive, then click on "Mount". This time enter the first password you used.

[ATTACH]93733[/ATTACH]

It will mount the outer volume. Here you can see you dummy file that you used earlier. This is what other people would see you if were forced to divulge the fake key. Make sure you don't add any more data to this drive as it will write over your secret drive. In fact, after setting up the outer drive, better not to use it at all. You can open in in protected mode so that the hidden system is protected. This is done using options in the mount dialogue.

For quicker mounting, you can add mount points to your favourites so that you can quickly mount that volume by right clicking on the TrueCrypt icon in the system tray.

** Using a File**
Instead of using a drive, you can create an encrypted volume and a hidden volume within a file. This is done pretty much the same way as in the first example, but you select "Create an encrypted file container" in the "Create New Volume" dialogue. When mounting those volumes, you will need to select the file instead of device.

**Things to Remember**
Following the above instructions should allow you to set up your hidden encrypted drives. Remember, always use the second password and so the hidden volume. Only ever give away the first password. Don't write data in the container drive unless you've protected it. Make sure the dummy files look realistic or it will be harder to claim that it is you actual encrypted drive. Remember to dismount drives after you've finished using them. Operate a physical security regime. 

Though it will take a very long time to brute force crack this strong encryption system, no system is ever safe against a brute force (guess every possible key) attack. Better to prevent someone coming into contact with your physical disk! Use long passwords that are a mixture of words and numbers that you can remember, other people cannot guess and are preferably not in a dictionary. For keeping a list of passwords secure, I recommend using KeePass. It is also available for Linux and Windows and uses string encryption.

---

### Post by wieman01 on 2008-11-24
I am a great fan & supporter of Truecrypt myself. Good job, Mr Dragon! :-)

---

### Post by C. Wizard on 2008-11-25
Nicely Done. Thank you.
Question. Is it possible to change the mount directory?
Truecyrpt, by default, mounts in the Media directory off of root, but I would prefer to mount the Truecrypt files in my home directory.
Is that possible, and, if so, how?
Thank you.

---

### Post by doyouhas on 2008-11-25
Awesome tutorial (check for spelling mistakes next time =P ). I will definetly be using this program, I have been looking for a simple way to do this exact thing.

---

### Post by ryukent on 2008-11-26
C Wizard,

You can mount the volumes anywhere. When mounting, click on options, then you can select a mounting directory. Make sure this is a directory that already exists. Once you have added this to your favourites, it will mount there every time you mount using the favourites list.

---

### Post by C. Wizard on 2008-11-26
> **ryukent said:**
> C Wizard,

You can mount the volumes anywhere. When mounting, click on options, then you can select a mounting directory. Make sure this is a directory that already exists. Once you have added this to your favourites, it will mount there every time you mount using the favourites list.
Thanks for taking the time to reply, but, sorry, I don't understand.  The only "options" for mounting I see are under, "Settings, Preferences, Mounting Options."
When I enter a path in the box, click "ok" and then try and mount a file I get this error message, 
"mount: wrong fs type, bad option, bad superblock on /dev/mapper/truecrypt1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

For example, say I want to mount the truecrypt volume in, /home/name/shared/
so I assume the path would read, 

/home/name/shared/truecrypt1

What do I have to do to get the truecrypt volume mounted in /home/name/shared/ ?

Thank you very much.

---

### Post by ryukent on 2008-11-26
Ahh, yes, what you need to do is not use the options in the Settings / Preferences section, but use the options button that appears when you click on the 'Mount' button. It expands the mount dialogue and gives you a "Mount at directory" option. Once it's saved in your favourites, you won't have to do this every time.

---

### Post by C. Wizard on 2008-11-27
Ah, so!
Imagine, if you will, an image here of myself slapping my forehead with the palm of my hand.
Many Thanks. Greatly appreciated.
:)

---

### Post by LexLuthor08 on 2009-01-08
is it possible to install ubuntu on such a hidden drive?

I cannot believe that windows can be installed as hidden OS but linux not...

---

