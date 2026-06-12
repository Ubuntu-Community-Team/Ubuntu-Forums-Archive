---
title: "Leaving windows, clean install on ssd, partitioning"
date: 2015-11-11
forum: New to Ubuntu
---

### Post by petri6 on 2015-11-11
Hi!

As the title states I would like to leave Windows forever (have given this a good thought) and only use Ubuntu. I've googled a lot but can't really find a solid tutorial that explains how I should do.

I have of course found a lot of bits and pieces. I've already created a bootable USB with Ubuntu on it and I have also used the LiveUSB function to try out Ubuntu. What I haven't figured out is how I should do regarding my main SSD where I want Ubuntu to be installed. 
It is a 250gb SSD Samsung evo 840 with windows 10 installed on it.
I want to format the thing and partition it in the best possible way to have a clean and solid Ubuntu installation to function as my daily driver.

1. How do I partition it in the best way to give it some space for applications and other stuff?

2. Do I format and partition it in the install menu or thru Gparted when I have "logged in" via the liveUSB?

Best regards, Petri

---

### Post by ajgreeny on 2015-11-11
Hello petri6, and welcome to the forums.

Whilst it is great that you are wanting to throw yourself fully into Ubuntu and get rid of Windows why not dual boot the two for at least a while?  You bought and paid for Win10, and you may find it comforting for a start to have it available, just in case you come completely unstuck with Ubuntu for some of the activities you need to carry out.

There some applications and programs that will not run in Ubuntu (or any other Linux distro) no matter how hard you try and how much fiddling you do.
I do not know how you use your computer, but if you are a gamer, for example, Windows will be almost unbeatable as the OS to use; Ubuntu is getting better with steam now available, but not being a gamer, I am the wrong person to speak about that with any real authority.  If you use iTunes you will definitely be out of luck.

You will undoubtedly need to consider UEFI system potential problems so have a good look at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) whether or not you choose to dual boot as it may save you a lot of heartache when installation doesn't do what it should.

Keep in touch here whatever you choose, and if problems arise we are here to help, though remember we are all volunteers and it may take a while for answers to appear to problems you post.

---

### Post by grahammechanical on 2015-11-11
The Ubuntu installer gives an option to Erase disk and install Ubuntu. It will do what it says. Everything on the hard disk will be lost. If you do decide to dual boot Ubuntu & Windows 10 and that is advisable until you know from experience that you no longer need Windows, then remember,

1) Use Windows utilities to defrag the hard disk. Do it more than once and restart every time.
2) Use Windows utilities to create unallocated space on the hard disk and confirm that Windows still loads.
3) Have a method of restoring Windows just  in case.
4) backup any data that you simply cannot afford to loose.

Regards.

---

### Post by Bucky Ball on 2015-11-11
As ajgreeny says, make sure Ubuntu is going to be able to do everything you need it to do before you leap in wholly. It is not a drop in replacement for Windows. 

If you are going to dual-boot, grahammechanical's advice is the way to go.

As for installing Ubuntu and its partitions, you have options and good idea to research them as it sounds you're good at that. For instance, two basic installs below:

> / = your root partition. 
You will have a default folder in there called /home and other folders in that for your personal stuff:  /Documents, /Music, etc. 
This is created 'automagically' during the install;

/swap = 2Gb is fine or the size of your installed RAM if you intend to hibernate often (and with a heap running in RAM).

You may want to have your personal data and Ubuntu personal settings on a separate partition. This is handy for a lot of reasons, backing up being one, having to reinstall the OS another:

> / = 20Gb
/home = large as you can
/swap = 2Gb

If you are intending to have mulitple installs and you want all installs to show the same personal data folders a method I and others use is a separate /data partition rather than a /home partition and to use symlinks. Without going into a full explanation (yet), you would set up something like this:

> / = 20Gb
/data = large as you can
/swap = 2Gb

Anyhow, some basic info and hope that helps you along a bit more ... :)

---

### Post by oldfred on 2015-11-11
We get a lot of users who make the leap to Ubuntu only, but find one application that they just cannot live without and want Windows back. That is why we suggest dual boot. But if you want to erase fully at least do a full backup of Windows so you can easily reinstall it. Otherwise you may have to purchase a new copy of Windows. It took me several years to wean myself from XP as I had on app. But when I got my first SSD, I had to change to AHCI for trim and XP does not work with AHCI, so I finally was forced to shutdown Windows.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Is system UEFI or BIOS? If Windows boots with UEFI then you have gpt partitioning, but a total reinstall may convert to MBR(msdos). Better to partition in advance and keep gpt. Even if system is BIOS, may be better to use gpt partitioning, but then not required.

Post this from live installer's terminal:
sudo parted -l

---

### Post by leunam12 on 2015-11-11
The first thing that you need to do is get a removable hard drive and use clonezilla to make a copy of your entire drive before doing anything. That way if you make a mistake or if something goes wrong during the install you can always go back to square 1 and start all over again.

The advice to keep Windows as a dual-boot is a good one but if you decide to make the jump to Ubuntu only, the best course of action is to boot from the live USB stick (try Ubuntu), then use GParted and create a new partition table (MBR is fine) and partition your hard drive as advised above: 20 to 25 GB for root (/); 2GB for swap and leave the rest for your /Home folder.

The next step after you are done partitioning is to double click "Install Ubuntu" on the Desktop and choose "something else" and manually assign each partition to root, home and swap respectively. The reason I do it that way is because it is better to have a separate, smaller partition for your system files; it makes it easy to back up and recover should a problem arise.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by petri6 on 2015-11-14
Hi again!

First of all I'd like to thank you all for the thorough replies and the warming welcome. :-)

I answered you guys/girls a couple of days ago but my answer was strangely never posted, propably my bad.

With that said I am now a happy fulltime Ubuntu only user. :-)

Have installed a couple of apps that I need, have even downloaded a torrent app and used it successfully. :-)

First I had problems creating the partition. I made root 28gb, swap 2gb and rest for home but then I got this error message but after searching the internet I came to realise that I also had to create a EFI boot section which I did. So after that everything went well.

Should I use/create Trim on my SSD also?

Best regards, Petri

---

### Post by flocculant on 2015-11-14
> **petri6 said:**
> ...

Should I use/create Trim on my SSD also?

Best regards, Petri

Should be running weekly. 

Check in /etc/cron.weekly/ for fstrim

---

