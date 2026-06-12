---
title: "Recovering Data From A Non-booting HDD Laptop Hard Drive"
date: 2017-03-13
forum: New to Ubuntu
---

### Post by hayaletinizi on 2017-03-13
Hello, I am very new to this website, platform, and of course ubuntu. I  have been searching and looking around and tried every single solution i  can come up with based on my search online to recover my data off my  HDD 500 GB Seagate Momentus 7200.2 internal hard drive i use in my Dell  Studio XPS 1640 with Vista Home Premium.

Here are the things I have tried last 1 week.
**1-I tried rebooting and always hung on the page where Green Microsoft loading bar screen**  and goes back to rebooting again and kept repeating ina loop and never  load top the page where I log in. I tried booting with my original vista  reinstallation disk to repair my Hard drive errors but no luck.

**2-I did start-up repair, chkdsk c: /f /r**  (C is my active primary partition) , I did memory diagnostic test, I  ran all system diagnostic tests, sfc /scannow, etc etc. whatever i  searched and whateer suggested to try out there without formatting or  anything to recover the data. Everytime I run checkdisk command , it  turns out be taking extremely long like it will take days, so i end up  using this one chkdsk C: /f /r /x which made the process faster but not  sure any better. and always have ad sectors, and mostly unreadable  indexes that is being processed which supposedly repairing i guess.

**3-I decided to order a cable 2.5" SATA hard drive to USB 3.0 **,  In that case i figured i wont need any power cable, (12V) as this is  2.5" HDD needs 5V whic can be supplied through USB. I was hoping it wont  delete any data off my hard drive. I did all these based on searches  only. I am not tech guy at all.
I WAS ABLE TO get to my files in a  crap laptop which always freezes, i plugged it in there and even i was  worried permission to access thing as HDD had password on it, i was  surprisingly able to get to every single file in it. UNTIL i went to  library to move all files. It didnt let me get in that folder as i  forgot i was not admin in library  but just  a guest account with no  rights over any folder to move which can be controlled by admin, oddly  even it was my own hdd. I was looking to move them off my HDD to move  into a usb flash drive.
So I came home and borrowed one of the laptops of my friend to be safe and i end up seeing my hard drive showing up but NO SIZE or name indicated, and when i click on it, it sees like RAW disk and saying please format to start using it. I have data in it and didnt wanna format it of course. 
My machine is out of warranty, and sick of hearing DELL telling me to go to technician because i was able to see those files but i can't even with the cable, i only able to connect it but not get to the files. 
I searched my warranty on seagate but it is out of warranty too of course.

**4-I came across one of these threads sugestin to use ubuntu live cd **and  i immediately burnt ubuntu 16.2 into my 8GB usb flash drive with Rufus.  and I tried to see if my hard drive will show up but NO luck, my hard  drive doesnt show up in computer inside ubuntu at all. so I go ahead and  tried the codes below:
# sudo /bin/bash    > to be root i guess, or admin
# mkdir /media/disk
#  mount -t ntfs-3g /dev/sda3 /media/disk -o force  >  as i know my hdd  primary partition was NTFS (I put sda3 as i ran gparted in terminal in  root, all my Hard drives showed up, 1st one is fat16 file system not  sure what it is, second and third ones are NTFS as i recognize them my  original internal hard drives which iam trying to recover the data in  it.)
(After i ran the code above , i was expecting to see my internal  hard drive be mounted but again NO luck and folowing respond i get in  terminal,
[U][I]<The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.>)[/I][/U]
**#fdisk -l **(to see if my disk will show and it showed up)

at  that point not sure what else i am supposed to do, the only thing i had  hope for seeing a thread on this website that offers to type "**gparted**" in the terminal and i did and scanned the every hard drive in my syste and showed my internal hard drive.
 (Note: I connected my non-booting HDD hard drive internally as it didnt show up at all through USB to SATA connection)

I  am very curious how I am supposed to use gparted in terminal after i  typed it and after i see my hard drives. Can I get to my files in it and  mount the data into another USB flash drive to move my files off it. 

The  only prolem I have in the list that shows my hard drive after gparted  typed in terminal is, the actual hard drive that has my data in it HAS  Input/Output Erro (I/O Error) and it has a red exclamanation sign next  to it. And when I right click> Information, following shows up as Warning:
[U][B]Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfs-3g / ntfsprogs.[/B][/U]

Not sure i should Format to NTFS again but would it delete my data in it. 

ANY help would be greatly appreciated. Thank you so much (I typed long and in dtail so everythingi did so far is clearly shown.)

---

### Post by TheFu on 2017-03-13
The first thing that should have been done was to clone the disk contents to a new HDD of equal or larger size. Then all the repair attempts should be done on that new disk.  NEVER TOUCH THE ORIGINAL DISK AGAIN. If it is failing, each access is making it worse.

> <The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.

I doubt that fixed anything.  You'll want to use Windows to fix Windows problems. Do it on a cloned disk, not the original.  If you must, there is a data recovery how-to. [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I/O Errors are troubling. Could be anything in the chain - motherboard, controller, cable, disk. 

Why not just restore the data from a backup?  That would be much easier, right?

---

### Post by hayaletinizi on 2017-03-13
This hard drive is total 500 GB and as far as i remember there was 205 GB free in it. So this leaves me around 295GB but i dont have a new hard drive yet ready to go. But i do  have few empty 128GB flash drives to put my Users folder  which contains pretty much all my personal data, I am so not sure ho to proceed and see the next best possible solution to to copy it all with no harm to this data i have since 2009, the year i started using this hard drive and this laptop i purchased back then.

---

### Post by TheFu on 2017-03-13
If you have all your data, I would abandon this effort, buy a new HDD and move forward.

If you don't have all your data and aren't willing to give up now, I would buy 2 new 500G HDDs and clone it before doing anything else.  

Use the 2nd HDD for backups going forward.  Getting backup religion is something that most people only learn the hard way. I lost 80% of my data long ago because I didn't have backup religion. A few months after that loss, I had gotten it and have slept very well ever since.

You had vista. Perhaps now would be a good time to switch to a Linux desktop? There are lots of youtube videos showing off all the different GUIs that might be fun to watch.  I can recommend the Ubuntu-Mate version, since a machine from 2009 won't be the fastest and a lite-er desktop would be smart.  You'd want the 16.04 LTS release [https://ubuntu-mate.org/blog/ubuntu-mate-xenial-final-release/](https://ubuntu-mate.org/blog/ubuntu-mate-xenial-final-release/)  which comes with 5 yrs of support. Newer releases only have 9 months of support from the release date. The next release happens in April and it will only get 9 months of support too. Since you are running Vista, you'll want to stay LTS (which is what I do as well).

---

### Post by hayaletinizi on 2017-03-13
I really appreciate you addressing those in long run not to face this kind of situation again.

Just curious what brand HDD do you suggest me to use ? 

I am still thinking why i was able to see my files two days ago through sata to usb cable. Now I am not able to see my files the same way i try. Probably the laptop is not the issue but the HDD has problem reading it. which is indicated that NTFS is not proper as I shut down the desktop at library before safely removing it. as it was hard drive, i just didnt know where the button was to safely remove it sinc ei connected it through sata.. 

I know there are testdisk, photorec etc. in ubuntu live but none of these will recover my files with their original directory file names etc. it will be hell of a pain to rename every data i have since 2009 . all those works. iu am just having headache even thinking/remembering them and renaming them. 

would i be able to clone the hard drive in ubuntu with no need any software out there begging to upgrade to paid version such as Easeus. ?

---

### Post by TheFu on 2017-03-13
99.9999999% of software used in Linux is F/LOSS, but if there is advertising, then 95% of the time, they took some F/LOSS program and changed the name. It is unusual to pay for programs in the Linux world.

All HDDs suck. Every one of them is going to fail at some point. We just hope they fail AFTER we are done using them.  There are HDD reports available on the internet which spell out which models/brands are less likely to fail.  However, most brands have a 0.5%-1% failure rate even when new. In the past, some models of some brands had over 30% failures. Some of those bad models are still being sold online and in retail stores, so do your homework in advance.  I don't know of any for a laptop.  My personal selection of HDDs isn't really useful. Your needs are probably not the same as mine, so we'd choose different models. Plus my personal experience is NOT large enough for a statistical sample.

Review the entire link already provided carefully. Data recovery is painful. Learn from this.  Backups are much easier, but be certain to validate those and that you can actually restore from the backups you make. Nothing is worse than believing you have been doing good backups for 5 yrs, only to find on the day you need them that none of the programs/data can be restored. These forums are full of people with that situation too.  It took me about 5 recovery attempts before I learned exactly what I needed in a backup in order to restore a system to the level I want.

BTW, all my SATA-to-USB cables require external power for the HDD.

---

### Post by norafaithrainbow on 2017-03-15
I would suggest western digital for hard drives in general. If you have the data backed up and just want the hard drive useable again (this may not work) I would try wiping and formatting it using gparted.

---

### Post by hayaletinizi on 2017-03-15
> **norafaithrainbow said:**
> I would suggest western digital for hard drives in general. If you have the data backed up and just want the hard drive useable again (this may not work) I would try wiping and formatting it using gparted.

I tried macrium reflectfree edition which I was hopin to clone my disk in windows WITH filenames and everything since i know testdisk and photorec will give dozens of files with given mix numbers and names. I never used testdisk,photorec as i am afraid to. and never did before and outcome will be yes i will have the files and probably renaming them and figuring out what is what will take me a year as these are files i had in it since 2009. after I have my data off it, I will format everything in it in heartbeat. but I didnt accomplish to get the stuff out of it yet.. I didn't have backup when it was in working condition. Now all I see, is the name of the hard disk. when i run diagnostics, i see Input/Output (I/O) error and unable to read message and the error messages i had in my original post above. I am looking for a way to get the files out, format it, and eventually buy  a new hard drive.. all i need basicly Users file in it..

---

### Post by TheFu on 2017-03-15
Until you buy a new HDD and clone it, you are just causing more damage. How you clone it is up to you, but I'd use **ddrescue**.
That makes a bit-for-bit copy, which is what you want.

The I/O issues are terrible. Might be too late to get any data off the drive.  Backups are good.

---

### Post by hayaletinizi on 2017-03-15
> **TheFu said:**
> Until you buy a new HDD and clone it, you are just causing more damage. How you clone it is up to you, but I'd use **ddrescue**.
That makes a bit-for-bit copy, which is what you want.

The I/O issues are terrible. Might be too late to get any data off the drive.  Backups are good.

I have never used ddrescue. would it work in Non-persisten live ubuntu in usb i have ? 
and once start using ddrescue, is it gonna hurt anything i have in my hard disk such as changing the OS or the filesystem type by switching it into something related to linux. I just wanna make sure my HDD stays as is even i try to clone some data off it.

---

### Post by TheFu on 2017-03-16
Yes, it will work. You can install software into a non-persistent environment. It is just lost at reboot.
dd and ddrescue are dumb. They do bit-for-bit copies. That includes the file system, partitioning, every bit on the disk. That is brilliant and stupid, both.  Just don't get the source and target mixed up or you'll end up overwriting the old disk.
[https://linux.die.net/man/1/ddrescue](https://linux.die.net/man/1/ddrescue) - but be certain to check the specific manpage for the exact version installed onto your box. It will be very similar to that link, but there could be important changes.

I think the damage to your old disk is already done. I/O errors are bad. The more use it gets, the more likely it is to completely fail. That is why we said to clone it in our first response.

---

### Post by norafaithrainbow on 2017-03-16
@TheFu I agree, the disk is probably damaged. But if they don't touch it until they clone it, they should be able to get some data off of the disk. After that maybe formatting can fix the disk. That happened to me with a flash drive that was damaged. I didn't care about the data because all it had was an ISO and just wanted the drive back so I formated it. It had to be formatted twice before my computer could read it again.

---

### Post by hayaletinizi on 2017-03-17
> **TheFu said:**
> Yes, it will work. You can install software into a non-persistent environment. It is just lost at reboot.
dd and ddrescue are dumb. They do bit-for-bit copies. That includes the file system, partitioning, every bit on the disk. That is brilliant and stupid, both.  Just don't get the source and target mixed up or you'll end up overwriting the old disk.
[https://linux.die.net/man/1/ddrescue](https://linux.die.net/man/1/ddrescue) - but be certain to check the specific manpage for the exact version installed onto your box. It will be very similar to that link, but there could be important changes.

I think the damage to your old disk is already done. I/O errors are bad. The more use it gets, the more likely it is to completely fail. That is why we said to clone it in our first response.


I truly appreciate you taking time to reply and show me my options. Now I understand better as i search more and more and it comes to point where your solution is being proven. But as I am really noob when it comes ubuntu. My question and main concern is the part you said "Just don't get the source and target mixed up or you'll end up overwriting the old disk." . 
Question 0: did you say that "Just don't get the source and target mixed up or you'll end up overwriting the old disk." for the case where I shouldn't clone the image into the same HDD. I believe it formats the all flash drive where i clone the image. Just confirming.

I have 3 questions:
1-If I want to clone it to two separate USB flash drive, would it be possible once the first 128GB flash drive is full and it is interrupted, do it again and let it take from where it was left by creating a log file?
2-If I want to clone it, how do i do that ? am I just simply using ddrescue such as done here in reply #3> [https://ubuntuforums.org/newreply.php?do=newreply&p=13621207](https://ubuntuforums.org/newreply.php?do=newreply&p=13621207) 
3-And once i clone the image to another FLASH DRIVE (if possible to do cloning to another flash drive) , what is the next step to take to view the files and work around the image i created on external flash drive ?

I wanna connect this dying HDD one more last time just to clone it and done connecting it before i damage more, i agree. and format shi(p) out of it :)

Full of questions and apologies, and thank you so much for trying to help

---

### Post by TheFu on 2017-03-17
The target drive MUST be larger than the source drive. Data amount doesn't matter. If the source is 500G, then the **target must be at least 500G in size.**
I am confident you'll figure out the rest.

---

### Post by hayaletinizi on 2017-03-17
> **TheFu said:**
> The target drive MUST be larger than the source drive. Data amount doesn't matter. If the source is 500G, then the **target must be at least 500G in size.**
I am confident you'll figure out the rest.

Right now I am using ddrescue GUI i installed in terminal.

I run it to image my HDD and seems like it says 2500 days for the time remaining. this is just imaging it but obviously a lot of bad sectors avoids it. I am not sure what to do at this point even I try to image it it seems like it just shows those scary numbers. will it takw too long or ddrescue GUI is bluffing. i am not sure. should I let it run .?

---

### Post by TheFu on 2017-03-18
Don't know anything about any GUI. Letting it run for a day or 2 is normal.  Predicted times are just that - predictions. These are based on how old the past recovery took.  Often, bad sectors are grouped near the beginning of a disk, so pessimistic guesses are common for the total time.

If you don't clone it, guess the data isn't that important.

Backups would have been much easier.

---

