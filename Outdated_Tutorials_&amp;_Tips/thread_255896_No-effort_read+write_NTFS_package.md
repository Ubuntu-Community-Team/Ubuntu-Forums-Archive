---
title: "No-effort read+write NTFS package"
date: 2006-09-12
forum: Outdated Tutorials &amp; Tips
---

### Post by dyssident on 2006-09-12
As part of a larger project called [AfterBirth]("http://www.ubuntuforums.org/showthread.php?t=257116"), Ive created a package that sets up read+write access to your NTFS partitions. All the various and sundry command line work is done for you.

Just copy this into the terminal:

```

sudo apt-get update && sudo apt-get upgrade
echo 'deb http://www.voxpopulimedia.com/debian dapper main' | sudo tee -a /etc/apt/sources.list
echo 'deb http://flomertens.keo.in/ubuntu/ dapper main' | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install afterbirth-ntfs-3g

```

Because some very low level services are updated, once its done you will need to reboot. After restart, you should see an icon on your desktop for each NTFS partition.

The process used came from [this thread](http://ubuntuforums.org/showthread.php?t=217009). You can [find AfterBirth here]("http://www.ubuntuforums.org/showthread.php?t=257116").

edit 2006/09/17: updated instructions

---

### Post by thelocust on 2006-09-14
It did work for me. Nothing showed up on my desk top. I have my XP HDD mounted and i still dont have any write privliges (even as root). couldn't tell you what went wrong im still new to all of this. good luck.

---

### Post by DCM36 on 2006-09-17
Worked for me, although I had to replace the ntfs-3g repos

Changed:
```
echo 'deb http://givre.cabspace.com/ubuntu/ dapper main' | sudo tee -a /etc/apt/sources.list
echo 'deb-src http://givre.cabspace.com/ubuntu/ dapper main' | sudo tee -a /etc/apt/sources.list
```

To:
```
echo 'deb http://ntfs-3g.sitesweetsite.info/ubuntu/ dapper main' | sudo tee -a /etc/apt/sources.list
echo 'deb-src http://ntfs-3g.sitesweetsite.info/ubuntu/ dapper main' | sudo tee -a /etc/apt/sources.list
```

and it worked.

Thanks for the howto

---

### Post by dyssident on 2006-09-17
> **thelocust said:**
> It did work for me. Nothing showed up on my desk top. I have my XP HDD mounted and i still dont have any write privliges (even as root). couldn't tell you what went wrong im still new to all of this. good luck.

most likely you just need to reboot. because some quite low level packages are updated, you will need to reboot after installing for the icon to show up automagically and to have read+write access. 

if rebooting doesnt work, try upgrading to the newest version released last night. you can force apt to upgrade just the one package with 

```

sudo apt-get install afterbirth-ntfs-3g

```

---

### Post by dyssident on 2006-09-17
> **DCM36 said:**
> Worked for me, although I had to replace the ntfs-3g repos


Ive changed the instructions to use the mirror that seems most reliable. If you are setting up a new system, you may want to try AfterBirth ([find it here]("http://www.ubuntuforums.org/showthread.php?t=257116")). Its basically an Automatix clone; the full app is able to make a better effort at managing repository mirrors.

---

### Post by prince_niceguy on 2006-09-18
with this mount my ntfs usb drives too in read write mode?

I have manually installed ntfs-3g on 64 bit ubuntu. I am able to make usb read/write but have to do unmount and remount all drives which is little painful.

also will this work with 64 bit?

---

### Post by blackened on 2006-09-18
Great work dyssident. This is a very needed project, so kudos.

---

### Post by subiet on 2006-09-18
i already have ntfs-fuse installed, but i want to switch to 3g, so will this work for me?

---

### Post by dyssident on 2006-09-18
> **prince_niceguy said:**
> with this mount my ntfs usb drives too in read write mode? also will this work with 64 bit?

although ntfs formatted usb devices should be automagically mounted as ntfs-3g, my test show they are still mounted as just ntfs. this means that they will be mounted, but read only. there are definiately patches that support this correctly, but they apparently havent made it into the official release yet.

until i can find out something further, the recommended way is to use ntfs-3g-nautilus-tools. 

```

sudo apt-get install ntfs-3g-nautilus-tools

```

whenever the icon usb drive pops up on your desktop, right click on it and click Scripts > mount_with_ntfs_3g. it will be remounted as read+write.

as for 64 bit systems, people in the thread that this package is based on report that it works fine on 64 bit AMD hardware. i can tell you that some pretty critical libraries get replaced, so i wouldnt be too quick to install this on a critical 64 bit system. if you have an ubuntu install that you dont mind loosing, give it a shot and let me know how it works.

> **subiet said:**
> 
i already have ntfs-fuse installed, but i want to switch to 3g, so will this work for me?


it should work fine; at least it does on my test systems. basically, the package comments out the old ntfs entries in /etc/fstab and replaces them with ntfs-3g entries. so the old ntfs module never even gets called.

> **blackened said:**
> Great work dyssident.

thanks. i try.

---

### Post by subiet on 2006-09-18
> **subiet said:**
> i already have ntfs-fuse installed, but i want to switch to 3g, so will this work for me?
Yes, it worked, and it worked like a breeze, it also recognized my pen drive without any additional settings. Good program, also, i use initng to boot, and it worked with the ntfs-fuse tweak that i had already done (mentioned in initng wiki) , for my existing ntfs-fuse access method.

//tip: unmount the ntfs partions, if they are already mounted via ntfs-fuse (not 3g), like me, it will be safer.

---

### Post by dyssident on 2006-09-18
> **subiet said:**
> Yes, it worked, and it worked like a breeze, it also recognized my pen drive without any additional settings. 
//tip: unmount the ntfs partions

good to hear. did it mount your pen drive as read+write ntfs-3g, or the old ntfs? in my experience, removable drives still appear to be a bit hit and miss.

fyi: this package calles 'sudo umount -a; sudo mount -a', at the very end of installation, so you shouldnt need to umount by hand.

---

### Post by Toxicity999 on 2006-09-18
If you don't mind post the deb script for us? It would be interesting to know what you actually did here. It's a good idea and seems to work for a very broad range.

---

### Post by subiet on 2006-09-18
> **dyssident said:**
> good to hear. did it mount your pen drive as read+write ntfs-3g, or the old ntfs? in my experience, removable drives still appear to be a bit hit and miss.

fyi: this package calles 'sudo umount -a; sudo mount -a', at the very end of installation, so you shouldnt need to umount by hand.
my pen drive got recognized automatically, 5 seconds after i inserted it, without any additional work for me, and it was read+write.

btw, the package does called umount, but that returned with an error code, saying that the device is busy. Therefore i advised to unmount them before.

---

### Post by dyssident on 2006-09-19
> **Toxicity999 said:**
> 
If you don't mind post the deb script for us?


all the work is done in two standard deb scripts: postinst and postrm. they are executed after installation and removal respectively. you will find them both attached.

their basic content was taken from [this thread]("http://www.ubuntuforums.org/showthread.php?t=217009").

> **subiet said:**
> 
btw, the package does called umount, but that returned with an error code, saying that the device is busy.


that error is confirmed to be a throwaway; umount errors for /, /dev and /var/run no matter what. i should probably just send it to /dev/null.

---

### Post by rlynch on 2006-09-19
very nice, thanks for the how-to, worked flawlessly in under 30 seconds

---

### Post by subiet on 2006-09-19
One question, say i have 3 users, x (has sudo permissions), y and z.
now i want x to read+write my ntfs partions, whereas y should only be able to read them and z should not see them at all (neither should be able to read nor write).

how do i do that, please explain.

---

### Post by wilberfan on 2006-10-14
Man, I just can't get anything "AfterBirthy" to work!

When I tried to install this I got the following:

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  afterbirth-ntfs-3g: Depends: hal (>= 0.5.7-1ubuntu19givre1) but 0.5.7-1ubuntu18 is to be installed
                      Depends: hal-device-manager (>= 0.5.7-1ubuntu19givre1) but 0.5.7-1ubuntu18 is to be installed
                      Depends: pmount (>= 0.9.11-1ubuntu2givre5) but 0.9.11-1ubuntu1 is to be installed
                      Depends: libhal1 (>= 0.5.7-1ubuntu19givre1) but 0.5.7-1ubuntu18 is to be installed
                      Depends: libhal-storage1 (>= 0.5.7-1ubuntu19givre1) but 0.5.7-1ubuntu18 is to be installed
E: Broken packages


:confused:

---

### Post by givré on 2006-10-15
You should follow that : [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

dyssident : there were a little change in the repo, you should update your post in consequence. Thanks

---

### Post by wilberfan on 2006-10-15
> **givré said:**
> You should follow that : [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)


Yeah, I ended up doing that--and it seems to work fine! :KS

---

### Post by TreeFinger on 2006-11-27
> **dyssident said:**
> As part of a larger project called [AfterBirth]("http://www.ubuntuforums.org/showthread.php?t=257116"), Ive created a package that sets up read+write access to your NTFS partitions. All the various and sundry command line work is done for you.

Just copy this into the terminal:

```

sudo apt-get update && sudo apt-get upgrade
echo 'deb http://www.voxpopulimedia.com/debian dapper main' | sudo tee -a /etc/apt/sources.list
echo 'deb http://flomertens.keo.in/ubuntu/ dapper main' | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install afterbirth-ntfs-3g

```

Because some very low level services are updated, once its done you will need to reboot. After restart, you should see an icon on your desktop for each NTFS partition.

The process used came from [this thread](http://ubuntuforums.org/showthread.php?t=217009). You can [find AfterBirth here]("http://www.ubuntuforums.org/showthread.php?t=257116").

edit 2006/09/17: updated instructions


This worked just fine for me :) Thank you

--edit

I just noticed whenever I am installing new software I get this error: "E: afterbirth-ntfs-3g: subprocess post-installation script returned error exit status 4"

It doesn't seem to be affecting anything but I would like it to stop. Anyone know what to do here?

---

### Post by alpacaman72 on 2006-11-28
```
/dev/hdc3       /media/windows  ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
You can find your NTFS partition at /media/windows
/dev/sda1       /media/windows1 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
You can find your NTFS partition at /media/windows1
/dev/sda5       /media/windows2 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
You can find your NTFS partition at /media/windows2
fuse
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy
Failed to mount '/dev/hdc3': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.
dpkg: error processing afterbirth-ntfs-3g (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 afterbirth-ntfs-3g
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

what went wrong?

---

### Post by one_stinky_bum on 2006-11-29
Don't just unplug your drive from Windows. Make sure you shutdown and then unplug, or click on the icon with a green arrow in windows and select "safely remove hardware".

---

### Post by williamgjames on 2006-12-01
I noticed that after I have installed afterbirth-ntfs-3g that the afterbirth package is reconfigured after I install **any** new package which reprocesses my fstab.  How do I stop this????

---

