---
title: "Vista to Kubuntu issues"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by TOMM_1230 on 2008-11-04
I have a few issues that I am not sure how to fix since I am new to Linux.

1) I can not get Vista to see my linux drive as a HDD it sees it as a FDD.


2) I can not get my .AVI, .MP3, and .WMP files to play. I think that mostly this is due to the fact that the media files are on my Vista drive. My Kubuntu drive can see my Vista drive but does not access the data properly.  

3) and finally, I installed Kubuntu on a third drive and it did not go well, so I used a new drive and now would like to format this third drive to be used by both for media storage and can not get Vista to see it nor can Linux access it.

Like I said I am new to Linux, I found a walk-through to set-up Kubuntu to work as a windows replacement but in all honesty I feel that there are to many apps installed so what apps are the most useful for replacing windows apps?

I am not interested in a "small" footprint, just FYI.  I have a 2.7 Ghz quad-core AMD Phenom 9850, with 4 Gb RAM, and a ATI HD4850 graphics card. And a 120 Gb or a 40 Gb HD for Linux and Vista is on a 500 Gb HD.  I want windows replacement apps, not small footprint apps. So any suggestions?

---

### Post by Peter09 on 2008-11-04
Most of the default apps you can leave, you can remove them from the menu if you want.

Microsoft only sees FAT and NTFS formatted drives. Linux sees them all. Your Linux drive will most probably be formatted as EXT2. 

Linux is most probably seeing the partition that is not formatted, but will not mount it as there is no filesystem on it.

---

### Post by TOMM_1230 on 2008-11-04
so how do I force Linux to use one of these formats?
Linux is so much more complicated but I think learning it will be worth the time in the long run.  But there is one heck of a learning curve.:confused:

Edit:
I am amazed and impressed at the quick reply. Thanks.

---

### Post by tarps87 on 2008-11-04
1) Windows will not see your Kubuntu drive unless you install third party software, if your Kubuntu install is a default install it will be using ext3 format. There are several programs about that will let you access your Kubuntu drive but I can not recommend any as I have not used them.

2) Have you installed the restricted extras?```
sudo apt-get install kubuntu-restricted-extras
```
This will install support for things like .mp3 formats

3) For formatting your extra drive can you post the output of ```
sudo fdisk -l
```
(lower case L not a one)

As for which apps are best that depends on what you want to replace, Vista has notepad, email, media player and ie by default (fresh install). Kubuntu has KMail for email, Amarok for media player, kate for notepad and firefox for ie. To add new programs open the start menu and look for add programs, click install and then apply changes and it will install it for you.
If you post a list of the programs you use people can post alternatives.

Remember that Linux is not windows and will be different.

---

### Post by tarps87 on 2008-11-04
> **TOMM_1230 said:**
> so how do I force Linux to use one of these formats?
Linux is so much more complicated but I think learning it will be worth the time in the long run.  But there is one heck of a learning curve.:confused:

Edit:
I am amazed and impressed at the quick reply. Thanks.

I wouldn't recommend forcing it to use NTFS, this will be complicated to set up. An alternative to the third party software is with the third drive format it to fat32, this can be read by both and can be done by installing gparted.
Linux can use (read/write) ntfs partitions but windows can not used anything other that fat or ntfs partitions.
Linux can be more complicated but there will always be people here to help.

---

### Post by Peter09 on 2008-11-04
Hi everyone,
just a thought, Linux is not more complicated - just that you can do a lot more with it :p

Take this thread - its Linux which is capable of working around windows, windows is pretty dead to all of this.

---

### Post by TOMM_1230 on 2008-11-04
As for which apps are best that depends on what you want to replace, Vista has notepad, email, media player and ie by default (fresh install). Kubuntu has KMail for email, Amarok for media player, kate for notepad and firefox for ie. To add new programs open the start menu and look for add programs, click install and then apply changes and it will install it for you.
If you post a list of the programs you use people can post alternatives.

Remember that Linux is not windows and will be different.[/QUOTE]

----------------------------------------------------------------

The main Apps I am worried about replacing are WMP as a all around Media Player, Office, and the codecs to play ".avi, .mp3, and .wmp" files. I am not sure with media player is best but I have found Amorok limited to Music and I want a all in one stop.  Also is the new OO.o an acceptable replacement for Office '03. I know it will lack some of the cutting edge stuff in '07 but for my wife and MIL (mother-in-law) who are not power Excel users like myself the extra power is uneccisary.  For me leaving MS completely is not an option, but for the other computers I maintain I don't see any reason if I can learn Linux to set it up that they will need to have Windows. and I believe you answered the third part already.

---

### Post by TOMM_1230 on 2008-11-04
[QUOTE=Peter09;6102911]Hi everyone,
just a thought, Linux is not more complicated - just that you can do a lot more with it :p
QUOTE]

----------------------------------------------------------------
You do realize that in computers there are three variables,
1)speed
2)complexity
3)options

9 out of 10 times if you increase one the other two are affected adversely.  

Example:

Window is Easy, but slow and limited to what MS allows you to have
Macs are Easier still, but slow and extremely limited to what Mac will let you have.
Linux is HARD, but (can be) much faster and virtually unlimited in its customization.

I am familiar with the first two and am now learning the third.  Trust me, I am not a computer newbie, but, Linux is very different, even then MSDOS see am old.

---

### Post by tarps87 on 2008-11-04
> **TOMM_1230 said:**
> 
The main Apps I am worried about replacing are WMP.
Also is the new OO.o an acceptable replacement for Office '03. I know it will lack some of the cutting edge stuff in '07 but for my wife and MIL (mother-in-law) who are not power Excel users like myself the extra power is uneccisary.

As for a all in one (video/music) I'm don't know of one. I use Amarok for music and VLC for DVD's. With Ubuntu it tends to be on application for one thing rather that compromising features by combining them, someone else maybe have a better answer to this.
Open office can do everything that office 07 can except vb macros, you can also open and save the .docx format from 07 as well as open source formats. An alternative office package is koffice, this is deigned for the KDE environment that Kubuntu uses. I would recommend open office though.
All the codecs you need should be installed with the restricted extras
Here is a link about the formats:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
(for the Kubuntu restricted extras replace Ubuntu with Kubuntu)

What do you mean by "My Kubuntu drive can see my Vista drive but does not access the data properly"?

---

### Post by TOMM_1230 on 2008-11-04
What do you mean by "My Kubuntu drive can see my Vista drive but does not access the data properly"?[/QUOTE]

For example: If I can get a media player to go to my vista drive (only a few of them have the capability to see anything other than my Linux drive) Rather than play the media, Kubuntu crashes and has me login and starts me desktop from scratch.

and the reason I am looking for an all in one stop is my MIL is wel virtually computer illiterate.  She know how to use the proprietary software she has been taught at work but not much else.  So whatever I put on here I will have to teach her to use.  Fewer programs = higher learning curve.

---

### Post by tarps87 on 2008-11-04
> **TOMM_1230 said:**
> For example: If I can get a media player to go to my vista drive (only a few of them have the capability to see anything other than my Linux drive)

This is probably due to the drive not being mounted automatically on boot, you should be able to navigate to it using the file explorer. This should mount it the 'easy way'. The way that I remember is by the command line, it is probably a good idea to auto mount it. This can be done by:
Making a directory called vista
```
sudo mkdir /media/vista
```
Looking for the vista hard disk, the ntfs formatted one. You will the to make a note of its name e.g /dev/hda1
```
sudo fdisk -l
```
then add this to the fstab file
```
sudo cp /etc/fstab /etc/fstab.bck
sudo kate /etc/fstab
```
then add the line:
/dev/hda1 /media/vista ntfs defaults 0 0
(replace /dev/hda1 with the drive name)
This will mount it on boot automatically now.
This should mount it for this session without needing to reboot
```
sudo mount -a 
```
You vista drive will be found in /media/vista and can be linked from your desktop for easier access

---

### Post by TOMM_1230 on 2008-11-04
I am not able to save the changes I made in kate, something about file owned by 1000 not 0 or some list of 1000's and 0's this is so confusing.

---

### Post by tarps87 on 2008-11-05
This maybe due to using kate. The GUI package I was talking about is pysdm
To install ```
apt-get install pysdm
```
The other way will be to use ```
sudo vim /etc/fstab
```
press i to write and then esc, :wq to save and exit.
If you look around you can usually find a GUI to do what you want, they will all be listed in the package manager.

---

### Post by lepar_m on 2008-11-05
For better functionality in Windows with the third drive I would suggest NTFS. However in Ubuntu you will have to mount the drive by clicking 
Places>Drive(Name of the Drive/Partition)
Either way it will not be visible from either operating system until it is properly formatted.

To format the drive you can use either your Ubuntu installation disk or your Windows recovery disk. Or download G-Parted Live and burn it to a disk and boot it.

Im not sure but Fat32 might work natively in both windows and Linux... no need to mount? Correct me if I'm wrong I don't use Fat32.

By default Windows cannot see Linux partitions (Ext2,Ext3 etc...) but their are tools that can allow you to mount Linux partitions as well as mac partitions. Try [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

In regard to the simplicity, functionality argument in this thread... id like to throw in my two cents....
I think Ubuntu has made a great effort to make the simple tasks simple to perform out of the box. And I feel that it is also very efficient as most any Linux distro. The good part is if you want to get complicated your options are endless. Its far from dummy proof but its not any more complicated than windows. Accessing file systems from other operating systems is a bit tricky but its no less tricky in windows, but rather people never need to do so unless they are dual booting or migrating from windows.

---

### Post by TOMM_1230 on 2008-11-05
could it be that I was not in root, I don't know how to get to the root so I doubt I was there.  If I was in Window I would say that the /ect/ folder was protected and I did not have access rights. But I am just guessing.

---

### Post by TOMM_1230 on 2008-11-05
That may be and since I chose Kubuntu over so many other linux distros I have to agree that it is as simple as any other linux distro.

In regards to it being simpler than Windows, I have to disagree, conditionally.  Windows is high limited to MS's choices, but in those limits, it generally runs well. It is also extreemly simple to install and run out of the box.  I know this praise of Windows especially of Vista will seem odd in a ubuntu/Kubuntu forum, but I have not had a single crash (knocks on wood while throwing salt over shoulder) in Vista.  Last night I crashed Kubuntu three times.  Now this may be due to my high level of understanding and experience with Vista and Windows and my low level of understanding and experience with Kubuntu and Linux.  But from my current experience I would be turned off from the switch but, I know the devil is in the details.  Which is something most of the closed minded people who are dissing Vista specifically and Windows in general from the Linux side and Linux as a whole from the Windows side are not looking at.  

Window is simple.  Put in the DVD and leave it alone, and it will "just work".
Linux is Hard.  (If one wants it to be a Windows replacement not just a different OS.)  And my goal is to set Linux up to replace Windows for two people who want their computers to "just work".  And that is not easy in Linux.

Now mind you my problem here is not a simple "just work" question and is a little bit more advanced but if I can not get to all of my files I can not learn Linux to set it up for them.  For me I need to be on my second cup of Linux and right now I am just learning to appriciate the flavor of the first cup.

---

### Post by tarps87 on 2008-11-05
The command sudo and then you password gives you root/administrative privileges, this is one place where kate (the text editor) is not as 'user friendly'. If you were using gedit on Ubuntu it would say something along the lines of you do not have access

---

### Post by TOMM_1230 on 2008-11-05
I will try this way again later thanks.

---

### Post by angelsguitar on 2008-11-05
> **TOMM_1230 said:**
> I have a few issues that I am not sure how to fix since I am new to Linux.

1) I can not get Vista to see my linux drive as a HDD it sees it as a FDD.

There's a package called ntfs-config which you can install from synaptic package manager.  After you run that tool it will enable automounting of any NTFS volumes, external or internal, that you have connected or connect to your system.  I believe you have to run in as root to make the initial configuration, so after you install it just type in a terminal

```
sudo ntfs-config
```

and, after writing your password, enable all check marks you see on the window that opens, and press OK.

By the way, in Ubuntu the root account is disabled by default, but you can run administrator (as root) commands by using the command "sudo" before any command (like the command above)


> 2) I can not get my .AVI, .MP3, and .WMP files to play. I think that mostly this is due to the fact that the media files are on my Vista drive. My Kubuntu drive can see my Vista drive but does not access the data properly. 

That's because Ubuntu doesn't come with codecs that are propietary or copyrighted by default, for legal reasons (they are not allowed to include them in the install media).  Just follow this multimedia how-to and your machine will be setup to handle almost any media format, including DVD's:

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

> 3) and finally, I installed Kubuntu on a third drive and it did not go well, so I used a new drive and now would like to format this third drive to be used by both for media storage and can not get Vista to see it nor can Linux access it.

Windows can not see Linux partitions by default.  I use a third-party free driver for that purpose, called Ext2fsd, which you can find at this address:

[http://ext2fsd.sourceforge.net/]("http://ext2fsd.sourceforge.net/")

> Like I said I am new to Linux, I found a walk-through to set-up Kubuntu to work as a windows replacement but in all honesty I feel that there are to many apps installed so what apps are the most useful for replacing windows apps?

I am not interested in a "small" footprint, just FYI.  I have a 2.7 Ghz quad-core AMD Phenom 9850, with 4 Gb RAM, and a ATI HD4850 graphics card. And a 120 Gb or a 40 Gb HD for Linux and Vista is on a 500 Gb HD.  I want windows replacement apps, not small footprint apps. So any suggestions?


That depends on your needs, and what programs you usually use.  Most agree that OpenOffice is a very good replacement for Microsoft Office.  For graphics, there's Gimp and Inkscape.  For desktop publishing, Scribus.  You may already be using Firefox, an IE alternative.  Check out this address, which has suggestions on software replacements in Linux:

[http://www.linuxalt.com]("http://www.linuxalt.com")

Hope this helps.  It is true that in Linux you have to learn a bit more of your computer, and spend a little more time in it, but the knowledge and freedom you'll have in the long run is worth it.  Welcome to Linux! ;)

---

