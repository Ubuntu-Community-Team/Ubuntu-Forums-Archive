---
title: "Ubuntu doesn't boot after upgrade 12.04 -&gt; 12.10"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by diniz-cpm on 2014-02-20
Hi everyone,
A few days ago I tried to upgrade Ubuntu from 12.04 to 12.10 (I'm trying to get to 13.04) following [these instructions]("http://www.maketecheasier.com/upgrade-ubuntu-12-04-lts-to-13-04/"). However, when [this window]("http://mcdn.maketecheasier.com/wp-content/uploads/2013/07/upgrade_linux_7.png") popped out I couldn't find the Start Upgrade" button and I couldn't resize the window either. So, I don't remember exactly how, I aborted everything and tried to do the upgrade again. It worked, apparently, but now Ubuntu doesn't boot anymore. I tried to boot with the recovery mode using clean, fsck (I guess that's how you spell it) and dpkg. [This is what happens with dpkg]("https://drive.google.com/file/d/0B-L9IXHAic8qYVpPVnJfb01GbWc/edit?usp=sharing") (I had to photograph the screen with my cellphone).
I thought that maybe the computer wasn't connected to the internet, so that's why dpkg wouldn't work. However I don't know how to allow the computer to connect to the internet. I tried to run "ifconfig wlan0" from the terminal (the "root" option at the recovery boot mode) but it said that wlan0 wasn't found.

Anyways, how can I make Ubuntu boot again?
Thank you very much!

---

### Post by monkeybrain20122 on 2014-02-20
Do a clean install of 13.10 (13.04 has reached end of life) I won't even try to trouble shoot a bad upgrade. "Upgrade" is easily the most problematic "feature" in Ubuntu if you look at all the threads here. I would avoid it totally. Even if you get it to boot this time, god knows how many hidden problems there are and they only manifest later on as weird, hard to diagnosed problems. A clean install takes you ~ 20 minutes plus the time to reinstall the software which normally will be still well under an hour combined. "Upgrade" takes hours during which many things can go wrong.

Edited: People probably choose to "upgrade" because they want to keep their customizations. But the truth is upgrade works best (or only works) if you have a very pristine system with minimal customization. All proprietary drivers have to be removed, ppa purged and third party software uninstalled before an upgrade for it to work. But if you have minimal customization why not just spend 20 minutes to do a clean install? (you can keep your settings and data if you have a separate /home partition which makes clean install even easier) I am surprised that your link doesn't even say a word about proprietary drivers and ppas.

---

### Post by Bucky Ball on 2014-02-20
You were in the right place to start with and 'if it ain't broke, don't fix it!'. 12.04 LTS is directly upgradeable to 14.04 LTS when it is released in April. Clean install of 12.04 LTS or 13.10 is probably your best option. 

You say Ubuntu doesn't boot anymore but give no clue what happens when you switch the machine on and the error messages you get when it stalls, or any information about when it stalls. You switch on, and the computer does what exactly? When it stops, what are you looking at? What are the error messages, if any?

12.10 is no person's land as it no longer upgrades to anything (13.04 EOL, as mentioned). You have chosen to go the longest, and most problematic, route possible to get to 13.10 or 14.04. ;)

---

### Post by diniz-cpm on 2014-02-21
Wow, it's great to find out that a tool provided by my own OS actually makes it unusable. Really great...
> **monkeybrain20122 said:**
> Do a clean install of 13.10 (13.04 has reached end of life) I won't even try to trouble shoot a bad upgrade. "Upgrade" is easily the most problematic "feature" in Ubuntu if you look at all the threads here. I would avoid it totally. Even if you get it to boot this time, god knows how many hidden problems there are and they only manifest later on as weird, hard to diagnosed problems. A clean install takes you ~ 20 minutes plus the time to reinstall the software which normally will be still well under an hour combined. "Upgrade" takes hours during which many things can go wrong.

Edited: People probably choose to "upgrade" because they want to keep their customizations. But the truth is upgrade works best (or only works) if you have a very pristine system with minimal customization. All proprietary drivers have to be removed, ppa purged and third party software uninstalled before an upgrade for it to work. But if you have minimal customization why not just spend 20 minutes to do a clean install? (you can keep your settings and data if you have a separate /home partition which makes clean install even easier) I am surprised that your link doesn't even say a word about proprietary drivers and ppas.
Hm, pardon my ignorance, but "clean install" means that everything on the Ubuntu partition of the hard drive will be erased, right? My personal files and the system files are at the same partition. Is here any way to acess my files before I do this clean install? I mean, I have backups but that would help me a lot.
 
> **Bucky Ball said:**
> You were in the right place to start with and 'if it ain't broke, don't fix it!'. 12.04 LTS is directly upgradeable to 14.04 LTS when it is released in April. Clean install of 12.04 LTS or 13.10 is probably your best option. 

You say Ubuntu doesn't boot anymore but give no clue what happens when you switch the machine on and the error messages you get when it stalls, or any information about when it stalls. You switch on, and the computer does what exactly? When it stops, what are you looking at? What are the error messages, if any?

12.10 is no person's land as it no longer upgrades to anything (13.04 EOL, as mentioned). You have chosen to go the longest, and most problematic, route possible to get to 13.10 or 14.04. ;)
When I press the button to turn on the computer the logo of its manufacturer appears, and then Grub. If I choose "Ubuntu", the screen flashes once or twice and then a terminal in a gray screen appears. It looks like the Ubuntu terminal. I'm asked to enter m login and password. And that's it.

---

### Post by monkeybrain20122 on 2014-02-21
> **diniz-cpm said:**
> Wow, it's great to find out that a tool provided by my own OS actually makes it unusable. Really great...

Hm, pardon my ignorance, but "clean install" means that everything on the Ubuntu partition of the hard drive will be erased, right? My personal files and the system files are at the same partition. Is here any way to acess my files before I do this clean install? I mean, I have backups but that would help me a lot.
 

Yes, everything will be erased. The way to access them now would be through a live usb since your OS is no longer working. For future reference you can keep your data and settings (say Firefox tabs and history) in a clean install if you make a separate /home partition.

So instead of installing Ubuntu in a single partition you create three: a root partition (mount point /) and a home partition (mount point /home) and a swap partition. You can do this if you choose advanced or manual during installation. You can create the partitions then but I usually do it in gparted ahead of installation just because I can (I have multiple linux installations on same and different drives so I can easily modify one from the other without booting from a live usb)

Then in future clean installs you also choose "advanced" or "manual" from the installer and only reformat the / partition (leave /home unreformatted) then the new Ubuntu system will be installed only in / and will use the same /home unmodified.

Normally 20G for the / partition would be more than enough (15G would be plenty but just to be on the safe side) and /home can be as big as your hard drive allows as it is where your data live. Both should be formatted to ext4. The swap partition should be about the size of your ram (they used to say 1.5 or 2 times but I think same size is ok)

---

### Post by diniz-cpm on 2014-02-21
> **monkeybrain20122 said:**
> Yes, everything will be erased. The way to access them now would be through a live usb since your OS is no longer working. For future reference you can keep your data and settings (say Firefox tabs and history) in a clean install if you make a separate /home partition.

So instead of installing Ubuntu in a single partition you create three: a root partition (mount point /) and a home partition (mount point /home) and a swap partition. You can do this if you choose advanced or manual during installation. You can create the partitions then but I usually do it in gparted ahead of installation just because I can (I have multiple linux installations on same and different drives so I can easily modify one from the other without booting from a live usb)

Then in future clean installs you also choose "advanced" or "manual" from the installer and only reformat the / partition (leave /home unreformatted) then the new Ubuntu system will be installed only in / and will use the same /home unmodified.

Normally 20G for the / partition would be more than enough (15G would be plenty but just to be on the safe side) and /home can be as big as your hard drive allows as it is where your data live. Both should be formatted to ext4. The swap partition should be about the size of your ram (they used to say 1.5 or 2 times but I think same size is ok)
Well, I run Windows 8 alongside Ubuntu so I guess it's easier to create the partitions with Windows before I try to reinstall Ubuntu. I know very little about partitions so I'd need help to do this. [That's how my hard drive is currently partitioned]("https://drive.google.com/file/d/0B-L9IXHAic8qeWZpX2NuZk1NSTg/edit?usp=sharing").
I guess I can keep the swap partition as it is and split the F: one into 2: one for system files (/) and one for /home. Is that correct? Should they be ext2?

And by "live usb" you mean downloading Ubuntu into a flash drive and then choosing the "try Ubuntu" option instead of "install Ubuntu" so that I can acess my files? But then would I able to copy files to somewhere else (I'm thinking about asking my roomate if he can allow me to temporarily save some files on his computer...)?

---

### Post by monkeybrain20122 on 2014-02-21
Well if you dual boot with Win8 then it is a completely different story as MicroSoft screws you with uefi and restricted boot and what not, the picture is now more complicated. I don't worry about working around Windows because I just get rid of it :) and it is a bliss to install any Linux and multiboot. You may want to wait for oldfred for advise about things to watch out if you use the advanced mode to install.

But one thing is for sure. If you intend your partitions for Linux then create them with a Linux tool, not Windows partition software.

---

### Post by Bucky Ball on 2014-02-21
> **diniz-cpm said:**
> 

When I press the button to turn on the computer the logo of its manufacturer appears, and then Grub. If I choose "Ubuntu", the screen flashes once or twice and then a terminal in a gray screen appears. It looks like the Ubuntu terminal. I'm asked to enter m login and password. And that's it.

Ok, that makes sense. When you get to the cursor, login and then issue this:

```
sudo service lightdm start
```

---

### Post by diniz-cpm on 2014-02-22
it looks like something has changed, the gray terminal doesn't appear anymore. instead there's a gray screen with a white underscore "_", but I can't type anything! What should I do?

---

### Post by diniz-cpm on 2014-02-23
Ok, so I guess things worked out pretty fine. I believe I managed to do a clean install. The OS looks much more clean and fast now, because when I first installed Ubuntu I think I messed up with a lot of stuff without knowing what I was doing...

So, just to make sure, even now that / and /home are at different partitions, I shouldn't use the upgrade thing? Or can I use it but only if it's an upgrade to another LTS version?

---

### Post by Bucky Ball on 2014-02-23
Huh? No. You want to update/upgrade regularly. 

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

These commands will not upgrade you to another release, LTS or otherwise. They will update/upgrade only what you have running currently and whatever apps you have instaled. 12.10 WILL NOT upgrade to 14.04 LTS, which, from memory, I think is the point I was making earlier. ;)

You'd need to go from 12.10>13.04>13.10>14.04 LTS to get there; impossible because 13.04 is no longer supported. You were in a good place with 12.04 LTS as LTS releases can always upgrade directly to the next LTS, leapfrogging the interims. The other issue is that 12.10 is only supported for a few more months, then you have NO upgrade path 'in machine' as 13.04 is dead.

A note: the newer releases are now supported for nine months rather than eighteen. LTS for five years rather than three (for Ubuntu at least).

---

### Post by diniz-cpm on 2014-02-24
Yes, I'm aware of sudo apt-get update, upgrade, etc., but I mean: when a new LTS edition is released, will I have to do a clean install to use it or can I just somehow upgrade from my 12.04 version? I mean, it was said that a new LTS will be released soon, so how will I be able to use it?

---

### Post by Vladlenin5000 on 2014-02-24
The long term support is 5 years know. You can wait as long as you need to feel comfortable about the upgrade and let the glitches be ironed out. A LTS is usually stable but no version is perfect, especially in the beginning and until it has been tested "in the wild". *REALLY NOT RECOMMENDED* You can install even install 14.04 right now and by the time of its official release the usual system updates will take care of making your alpha/beta version into the same as the "definitive" one. *REALLY NOT RECOMMENDED*

---

### Post by monkeybrain20122 on 2014-02-24
> **Vladlenin5000 said:**
> The long term support is 5 years know. You can wait as long as you need to feel comfortable about the upgrade and let the glitches be ironed out. A LTS is usually stable but no version is perfect, especially in the beginning and until it has been tested "in the wild". *REALLY NOT RECOMMENDED* You can install even install 14.04 right now and by the time of its official release the usual system updates will take care of making your alpha/beta version into the same as the "definitive" one. *REALLY NOT RECOMMENDED*

+1 to not installing the latest right after release. I suggest wait at least a month. I have an external hard drive, I would install the newly release there, do all the customization and tweaking, get all the post release fixes etc. When I make sure everything works and setting things up just right, I would delete the current Ubuntu just restore this over the vacated space. So I don't 'upgrade' and not really a 'clean install' either.

---

### Post by Bucky Ball on 2014-02-24
LTS upgrades directly to the next LTS. When the upgrade to 14.04 LTS is available in 12.04 LTS the option to upgrade will appear in your Software Updater. It is up to you to manually click and choose that option, but that's all you have to do.

I'd wait two or three months after release.

---

### Post by diniz-cpm on 2014-02-27
Hm, I see... Thanks very much for your help!

---

