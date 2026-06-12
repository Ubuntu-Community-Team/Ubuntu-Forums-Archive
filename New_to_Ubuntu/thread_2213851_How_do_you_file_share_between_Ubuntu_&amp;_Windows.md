---
title: "How do you file share between Ubuntu &amp; Windows XP dual boot?"
date: 2014-03-29
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-03-29
I am presently dual booting Windows XP and Ubuntu 12.04 LTS. It is working well. But I would like to be able to access some files that are on one "side" (Windows or Ubuntu) of the PC with the other "side." I'd especially like to be able to create or download a file in Ubuntu and be able to use it in Windows. I am presently transferring such files from Ubuntu to Windows using a thumbdrive. But this is pretty inconvenient. 

I've been trying to read posts in this forum and online, but it is not clear to me what a good and reasonable course of action would be. It seems that some posts suggest making a shared NTFS partition that is read only for one operating system. Another solution is in this post ( [http://ubuntuforums.org/showthread.php?t=469666](http://ubuntuforums.org/showthread.php?t=469666) ) that suggests downloading and installing an application into each OS. These applications apparently allow one operating system to see the other.

QUESTION(S): Does anybody have good advice about how to file share between Ubuntu and Windows XP?

I've attached a screenshot from my disk utility that shows the status of the hard drive.

Thank you,

R.

---

### Post by 3rdalbum on 2014-03-29
Your Windows drive should appear toward the bottom of the Launcher on the left side of the screen. Click its icon and you will be able to copy files to the Windows drive and access anything that is already there.

---

### Post by mikewhatever on 2014-03-29
A thumbdrive solution is about as good as it gets. Fs-driver does not support ext4, which you are presently using. ;)

---

### Post by monkeybrain20122 on 2014-03-29
XP support ends next week. Time to get rid of the XP partition.

---

### Post by mastablasta on 2014-03-29
> **monkeybrain20122 said:**
> XP support ends next week. Time to get rid of the XP partition.
my games on it still work nicely so i think i will keep it for the forseable future. it's not like they supported it a lot lately anyway. most security updates were for malware removal tool. no serious patches.


ext2nfs or what is called now - the tool that allows you to read linux parittion from windows will do. another option is separate partition for data or for example external disk formated with ntfs so both can read it.

otherwise as suggested moving files form linux part of disk to windows part of disk is easy.

---

### Post by monkeybrain20122 on 2014-03-29
@OP,

Didn't you solve your problem by dualbooting with CENTOS 6.5? Why still keep XP?

---

### Post by centaurusa on 2014-03-29
> **RMcGinnis said:**
> It seems that some posts suggest making a shared NTFS partition that is read only for one operating system.

Creating a separate NTFS data partition under Windows is a viable solution, allowing the use of the same files under both Windows and Linux.  The trick is that Linux will use the NTFS partition, while Windows would deny all knowledge of files contained in an ext4 partition.  Thus, the NTFS partiton can be read by both operating systems.

The other advantage is that it makes backing up your volatile data files very easy.  You just back up the data disk.

---

### Post by LukeMorrison on 2014-03-29
How much information would you be accessing between the OSes?  Have you considered something like Ubuntu One, Dropbox, or Google Drive?

---

### Post by pqwoerituytrueiwoq on 2014-03-29
mount the xp partition with fstab (google it)
add this to your /etc/rc.local script before the exit line
adjust the file paths as necessary, i made some guesses based on your user name here
i also assumed you will be using fstab to put xp in /mnt/XP
```
mount --bind /mnt/XP/"Documents and Settings"/RMcGinnis/"My Documents" /home/rmcginnis/Documents
mount --bind /home/rmcginnis/Documents/"My Music" /home/rmcginnis/Music

```
you can add lines based on the second line in that code for your Videos folder and what ever else xp has, i forget all the stock folders
By doing this all your files are stored on your XP install, these are not copies, if you delete xp you delete all your files

+1 for moving away from XP, but that is not what OP wants

---

### Post by sotiris2 on 2014-03-29
Using a cloud service to transfer files between two OS in the same physical system , is like going to London from Paris via Tokyo. It's slower , could be expensive if OP has a connection with bandwidth limits and totally unneeded and complicated. Linux can read/write to ntfs perfectly (to my experience) and ntfs is Window's native fs. So to share a file from Linux to Windows just put it directly on the ntfs partition , on the exact folder you 'll want it to be. To 'transfer' a file from Windows to Linux simply do ...*nothing. *Just access it directly from the Windows partition. 

You can make a new ntfs partition if you want to have shared files separately for easier find but it's not necessary. If you do you can event mount it to a folder on your home folder (I like it that way).

EDIT: pqwoerituytrueiwoq's (god bless copy-paste!) example above will make your Documents and Music folders in Ubuntu be the actual respective Windows' folders. Just keep in mind in that setup that if you want to add for example 1 GB of data in Music folder you 'll have to consider the Window's partition free space not Ubuntu's (thought right click on the folder will so the correct free space always)

---

### Post by monkeybrain20122 on 2014-03-29
If you have to dual boot with XP which I disagree, it is very easy to access the windows partition from Ubuntu, mount the partition from nautilus and cut/paste/copy that's it. Windows can't read Linux file system so you will do everything on Ubuntu. You can retrieve files from the Win partition or put files to it. You don't need bidirectional access, in any case XP should be quarantined like a pariah. I wouldn't let it have access to Ubuntu even if it can be done (with third party software)

---

### Post by GigabyteProduction on 2014-03-29
The best way in my opinion is to have a shared partition, this is the way i do my stuff, you might even want your home folder to be on that shared partition.

The best filesystem to use for the shared partition is ext3, because fat has size limitations, ntfs has a very very poor speed in windows, and all the ext files systems are supported in windows with ext2fsd, but ext4 can only work read only, but ext3 works perfectly in ext2fsd.

So for the actual setup, you would *not* be accessing your windows drive, it's too much risk for corruption and even mounting your windows drive as anything but read-only will erase the hibernation file for windows if you use hibernaton.

So to set this up (do all of this in a live-boot):
[LIST]
[*]make some space for the partition using gparted and shrinking your partitions
you shouldn't need too much space on the actual linux partiton since your home files will be on the other one, so make it like 30 gigs or something, just enough room for programs. 
[*]Create the ext3 partition of whatever size you want/can 
[*]keep gparted open to get the partition ids 
[*]Create a folder in /media called linux and a folder called shared 
[*]mount your linux installation to /media/linux (i.e. type "sudo mount /dev/sXX /media/linux" but without quotes and with XX replaced with what you see in gparted) 
[*]mount your shared partition to /media/shared (using the same method to mount as above) 
[*]move the entire /media/linux/home folder to /media/shared 
[*]create a symbolic link for the home folders with "sudo ln -s /media/shared/home /media/linux" but without quoes 
[*]create folders in /media/linux/media called shared and windows 
[*]add entires to the end of /media/linux/etc/fstab that look like this:
```
/dev/sXX /media/shared ext3 defaults 0 0 #<-- this is your shared partition
/dev/sXX /media/windows ntfs-3g ro,norecover,noatime 0 0 #<-- this is your windows drive with the options to not corrupt it
``` 
[/LIST]

now every user file (downloads, documents, and so on) will be on the shared partition and all that will be on the original linux partition will be the linux operating system and the program files (stuff that you don't need to access in windows)

inside windows, you'll have to install ext2fsd and mount your shared partition with it, and inside that shared partition will be a home folder that will have all the user files availabe to you

if this is what you decide to do, let me know if any of these instructions confuses you.

---

### Post by monkeybrain20122 on 2014-03-29
> **GigabyteProduction said:**
> The best way in my opinion is to have a shared partition, this is the way i do my stuff, you might even want your home folder to be on that shared partition.

The best filesystem to use for the shared partition is ext3, because fat has size limitations, ntfs has a very very poor speed in windows, and all the ext files systems are supported in windows with ext2fsd, but ext4 can only work read only, but ext3 works perfectly in ext2fsd.
.

Sorry man I think this is a really bad idea. Why would you integtate the two OS more than it needs to and in this case you have XP which even when supported, is a security nightmare and its support ends next week?  I wouldn't choose my  linux file system based on what is supported in Windows, that shouldn't be part of the consideration. I certainly would not share my /home with XP. My philosophy is to keep them as far apart as possible so I can get rid of Windows as easily as possible. Afterall XP should be killed.

---

### Post by mikewhatever on 2014-03-29
> **monkeybrain20122 said:**
> I wouldn't choose my  linux file system based on what is supported in Windows and I certainly would not share my /home with XP. My philosophy is to keep them as far apart as possible so I can get rid of Windows as easily as possible. Afterall XP should be killed.

No offence, but can you please stop derailing the thread with your own opinions, philosophy and Windows bashing. While it may be interesting for a cafe discussion, here is a help & support section, and one's opinions are best kept private. The OP seems to know what he/she wants to use, and if you can help, do stick to the point, which is clearly expressed in the thread title..

---

### Post by GigabyteProduction on 2014-03-29
> **monkeybrain20122 said:**
> Sorry man I think this is a really bad idea. Why would you integtate the two OS more than it needs to and in this case you have XP which even when supported, is a security nightmare and its support ends next week?  I wouldn't choose my  linux file system based on what is supported in Windows, that shouldn't be part of the consideration. I certainly would not share my /home with XP. My philosophy is to keep them as far apart as possible so I can get rid of Windows as easily as possible. Afterall XP should be killed.

I'm not saying to change your entire linux partititon, it's a second partition that user's keeping their own files on, it's not the os files, it's not the security configuration files, it's the user's personal downloads and documents. The user wants to access them in windows, that's what this allows, it allows nothing more than access to the user's personal files. There's not security risk here.

---

### Post by AbleTassie on 2014-03-29
> **3rdalbum said:**
> Your Windows drive should appear toward the bottom of the Launcher on the left side of the screen. Click its icon and you will be able to copy files to the Windows drive and access anything that is already there.

**Mikewhatever** wrote: A thumbdrive solution is about as good as it gets.


**Monkeybrain wrote:** Didn't you solve your problem by dualbooting with CENTOS 6.5? Why still keep XP? 

If you have to dual boot with XP which I disagree, it is very easy to  access the windows partition from Ubuntu, mount the partition from  nautilus and cut/paste/copy that's it.

             [**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458") wrote:                     mount the xp partition with fstab (google it)...

[**[COLOR=#000000]sotiris2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1845661") wrote: Using a cloud service to transfer files between two OS in the same  physical system , is like going to London from Paris via Tokyo.

             [**[COLOR=#000000]GigabyteProduction[/COLOR]**]("http://ubuntuforums.org/member.php?u=1901165") wrote: The best way in my opinion is to have a shared partition, this is  the way i do my stuff, you might even want your home folder to be on  that shared partition.





[B]
OK, thanks for your replies everybody. I have put some of your quotes above. And have responded to them below. [/B]

I have been playing around with this and have come up with this solution so far: (1) create an "Ubuntu-WindowsXP shared folder" within the Windows partition by mounting the Windows partition while in Ubuntu (2) create a desktop shortcut link to the shared folder in Ubuntu and (3) create a desktop shortcut link to the shared folder in Windows. This allows me to share files between the Ubuntu and Windows sides. In order to use shortcut in Ubuntu, the Windows partition must be mounted, however. 

My fear is that I may accidently delete a file or add harmful files to the Windows system while using Ubuntu. I suppose changing the folder and file permissions of most of the Windows files in the Windows partition might minimize the chances of this. But I am no sure how to do this -- it looks complicated with various complex Terminal commands. I am also concerned that it might somehow affect the Windows operation. 

While in Ubuntu I tried segregating the files in the Windows partition to a "DoNotTouch" folder and the "Ubuntu-WindowsXP shared folder." But this caused WindowsXP to be unable to boot. So I just went back making the "Ubuntu-WindowsXP shared folder" just another folder in the Windows partition.

**QUESTION(S):** Are there any simple ways to change the folder & file permissions for the folders & files in the Windows partition so I don't accidentally alter them while using the "Ubuntu-WindowsXP shared folder" ?

**REPLIES TO SPECIFIC POSTERS, thanks to all of you and the others:**

**3rdalbum,** yes, the windows drive partition will appear in the Launcher, **_IF_** it is mounted by using the File Manager.  

**Mikewhatever**, a 4GB thumbdrive does work. But Ubuntu has had trouble mounting my thumbdrive and my 160GB external drive. I get an error message telling me to run chksk /f. So I've had to run chkdsk /f on these drives to allow them to be usable. Running chkdsk /f in Windows is one reason for keeping WindowsXP.

**Monkeybrain**, yes I thought I was going to use CentOS 6.5: the initial dry run simulation with WebEx tech support worked. But when I double-checked it failed, requiring me to use the old archived JAVA 1.6 plug-in, which I do not know how to install. I am concerned about Windows XP security vulnerability and will use it only for WebEx at the LGO (Large Govt Organization).

I think your suggestion as to what to do (despite your disagreement with the dual boot)  is similar to what I am presently doing. 

BTW, I have become a kind of Ubuntu missionary here. And many others are interested. But they are too insecure to give up Windows altogether--at least at first. So my knowledge of how to dual boot will be helpful in getting them to try Ubuntu.

[**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458") this looks too complicated for me right now. Thanks for your suggestion though. Maybe I'll use it eventually.

[**[COLOR=#000000]GigabyteProduction[/COLOR]**]("http://ubuntuforums.org/member.php?u=1901165") thanks, I might eventually go to something like this. This looks more complicated than my present solution, but less complicated than [**[COLOR=#000000]pqwoerituytrueiwoq's[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458") suggestion.

[**[COLOR=#000000]sotiris2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1845661") yes, I agree. Using the cloud for this is slow.

**Again, my QUESTION(S):** Are there any simple ways to change the  folder & file permissions for the folders & files in the Windows  partition so I don't accidentally alter them while using the  "Ubuntu-WindowsXP shared folder" ?


THANKS AGAIN TO EVERYBODY, I APPRECIATE YOUR INTEREST AND RESPONSES.

R.

---

### Post by GigabyteProduction on 2014-03-29
> **RMcGinnis said:**
> 
**Again, my QUESTION(S):** Are there any simple ways to change the  folder & file permissions for the folders & files in the Windows  partition so I don't accidentally alter them while using the  "Ubuntu-WindowsXP shared folder" ?

part of my solution/guide covered this, if you mount it with the options of ro,noatime,norecover then absolutely nothing is changable in your windows drive. You're going to want this to set itself at boot so you can't accidentally mount it with the default options by clicking the icon, to have this automount you need to do: ```
sudo mkdir /media/windows
sudo nano /etc/fstab

```
and add this to the end: ```
/dev/sdXX /media/windows ntfs-3g ro,noatime,norecover 0 0
```
but replace XX with the windows partition's thing from gparted (it should be /dev/sda1 or /dev/sda2)

doing this will make it so it's always safe to be in your windows drive because you can't change ANYTHING, ubuntu can't even accidentally do anything. And you don't have to remember to do this because it makes itself automatic

---

### Post by The Cog on 2014-03-29
Answer: No.

Linux doesn't obey (or even understand) the windows users permissions. The only attribute that Linux will respect on an NTFS filesystem is the readonly attribute. But setting everything in windows to readonly will thoroughly mess it all up. So you can't really keep Linux from damaging the windows files if the user makes a silly mistake.

I think a shared partition is probably best but I guess you will need to shrink your windows partition to make room for a new shared partition. Most folk would format the shared partition with NTFS, which both OSs can use easily.

---

### Post by GigabyteProduction on 2014-03-29
ntfs-3g is actually configurable to allow windows permissions to correspond to linux permissions with the permissions option and then a usermaaping file, by doing this, i was able to make an ntfs drive have all the abilities and permissions of my linux folders and my linux usernames correspond to windows usernames, so if i own a file here, i own a file on windows, too.

Since your windows drive isn't supposed to be the shared partition itself, you do not want to even write a single bit to it, so you need to mount it as readonly, mounting it as readonly is like flipping that little lever on an sd card, you don't have to physically set all files to have the readonly flag, but now it's protected from accidents.

---

### Post by monkeybrain20122 on 2014-03-29
I still don't get it. If you are using xp only for one application why do you need any file access, let alone bidirectional file acess?  GigabyteProduction'sn solution is not simple at all. I don't know of any way to change /home's setup and  convert your already installed Ubuntu to ext3 without reinstalling. I think to go through so much troubles to accomodate xp for one application is letting the tail wag the dog.

P.s. Just beware that your xp installation  is doubly insecure. Not only is xp not getting security update, you are also running an out of date java which is even a bigger security risk. As I said that partition  should be kept isolated as much as possible.

---

### Post by GigabyteProduction on 2014-03-29
> **monkeybrain20122 said:**
> I still don't get it. If you are using xp only for one application why do you need any file access, let alone bidirectional file acess?  GigabyteProduction'sn solution is not simple at all. I don't know of any way to change /home's setup and  convert your already installed Ubuntu to ext3 without reinstalling. I think to go through so much troubles to accomodate xp for one application is letting the tail wag the dog.

P.s. Just beware that your xp installation  is doubly insecure. Not only is xp not getting security update, you are also running an out of date java which is even a bigger security risk. As I said that partition  should be kept isolated as much as possible.

I don't see what's wrong with my setup, you aren't required to reinstall to access /home whether it's a symbolic link or not, ubuntu actually gives you the option at install time to make the folder a mountpoint of another partititon, as long as the folder isn't being used, you can just move it and create a link to where you moved it to replace it. You're not converting home to ext3, either, a file is a file. That's why i made the instructions say to do this from a live-boot, so 1) the home folder isn't in use and 2) so the asker can resize anything that needs to be resized

His linux partition also is isolated, ext2fsd doesn't mount ext4, so that's already inaccessable. All that can be accessed are the files he wants accessable. Even if there were some virus that got onto windows and was designed to expect a linux home directory somewhere and somehow put a script on it to attack linux, what's that script going to do withot root permissions? Linux has a very good defense against virusses. So it's near impossible for an attack to succeed, let alone getting an attack from a windows virus in the first place. It's not any safer than moving things back and forth with a flash drive, which isn't that unsafe when dealing with an os like linux.

---

### Post by monkeybrain20122 on 2014-03-29
> **GigabyteProduction said:**
> 
His linux partition also is isolated, ext2fsd doesn't mount ext4, so that's already inaccessable. All that can be accessed are the files he wants accessable. Even if there were some virus that got onto windows and was designed to expect a linux home directory somewhere and somehow put a script on it to attack linux, what's that script going to do withot root permissions? Linux has a very good defense against virusses. So it's near impossible for an attack to succeed, let alone getting an attack from a windows virus in the first place. It's not any safer than moving things back and forth with a flash drive, which isn't that unsafe when dealing with an os like linux.

If access becomes too automatic there will be temptation to send files to others. I don't usually recommend av on linux but in this instance op may consider installing one. So the point is, for just one application that needs unmaintained java you have to go through all this length to integrate the two oses. I fail to see the wisdom in it. OP can use his xp as an isolated box and when needed dumps a file into the xp partition and that is it.

---

### Post by GigabyteProduction on 2014-03-29
> **monkeybrain20122 said:**
> If access becomes too automatic there  will be temptation to send files to others.

What do you mean by this?

> **monkeybrain20122 said:**
> I don't usually recommend av  on linux but in this instance op may consider installing one.

what is an av?

> **monkeybrain20122 said:**
> So the  point is, for just one application that needs unmaintained java you have  to go through all this length to integrate the two oses. I fail to see  the wisdom in it. OP can use his xp as an isolated box and when needed  dumps a file into the xp partition and that is it.

Where in > **RMcGinnis said:**
> I am presently dual booting Windows XP and  Ubuntu 12.04 LTS. It is working well. But I would like to be able to  access some files that are on one "side" (Windows or Ubuntu) of the PC  with the other "side." I'd especially like to be able to create or  download a file in Ubuntu and be able to use it in Windows. I am  presently transferring such files from Ubuntu to Windows using a  thumbdrive. But this is pretty inconvenient. 

I've been trying to read posts in this forum and online, but it is not  clear to me what a good and reasonable course of action would be. It  seems that some posts suggest making a shared NTFS partition that is  read only for one operating system. Another solution is in this post ( [http://ubuntuforums.org/showthread.php?t=469666](http://ubuntuforums.org/showthread.php?t=469666)  ) that suggests downloading and installing an application into each OS.  These applications apparently allow one operating system to see the  other.

QUESTION(S): Does anybody have good advice about how to file share between Ubuntu and Windows XP?

I've attached a screenshot from my disk utility that shows the status of the hard drive.

Thank you,

R. does it say that all they needs it for is unmaintained java? They said they want to access files that may be on the other side, well now they can access any file they want aside from linux O.S. files.

---

### Post by monkeybrain20122 on 2014-03-29
An av is an antivirus. 

Op has posted numerous threads on the topic. To make a long story short he needs to run one software for desktop sharing. It doesn't really require Windows xp because e.g centos would work and a dual boot with centos is much easier to set up (or just install it in a flash drive). But it turns out he also needs an old version of java which for good reason is no longer available in centos, so back to xp (and he doesn't have the specs to run vm)

---

### Post by westie457 on 2014-03-29
Adding my 2 cents FWIW.

Ext2fsd installed to Windows can read from and write to Ext4 partitions.

A separate NTFS-formatted partition is better if HDD space allows.

If the Windows partition is put into hibernation and files are then copied to the partition Windows will not know about them the next time it is restarted and they will not show in Windows Explorer (not exist). The technical explanation is while the Windows partition is in hibernation the MFT is locked and therefore not updated when files are written. When Windows is cleanly shutdown and files copied the MFT is updated and Windows will sometimes force a chkdsk on the partition if there is a large enough difference in the before and after states.

When using Linux to work within a Windows partition you can see all of the files and if you so wish, you could delete any and all files.

So be aware at all times of what you are doing.

---

### Post by AbleTassie on 2014-03-29
> **monkeybrain20122 said:**
> I still don't get it. If you are using xp only for one application why do you need any file access, let alone bidirectional file acess?  GigabyteProduction'sn solution is not simple at all. I don't know of any way to change /home's setup and  convert your already installed Ubuntu to ext3 without reinstalling. I think to go through so much troubles to accomodate xp for one application is letting the tail wag the dog.

P.s. Just beware that your xp installation  is doubly insecure. Not only is xp not getting security update, you are also running an out of date java which is even a bigger security risk. As I said that partition  should be kept isolated as much as possible.

Again, I appreciate everybody's comments. BTW For Windows XP I am running the latest version of JAVA; Webex/Large Govt Organization (LGO) support this combination. For Linux it is the old archived version of JAVA (1.6) with older Linux versions (e.g. Ubuntu 10 &11) or Redhat 5 & 6 that Webex/LGO supports. I tried CentOS 6.5 with JAVA 1.7 and it seemed to work at first, but it did not work in the end with the most realistic simulation.

Again, running chkdsk /f on my USB drives in Windows is another reason to keep Windows XP. I've read that chkdsk f/ in Linux is not as good as chkdsk f/ in Windows.

Thanks,

R.

---

### Post by monkeybrain20122 on 2014-03-29
> **RMcGinnis said:**
> Again, I appreciate everybody's comments. BTW For Windows XP I am running the latest version of JAVA; Webex/Large Govt Organization (LGO) support this combination. For Linux it is the old archived version of JAVA (1.6) with older Linux versions (e.g. Ubuntu 10 &11) or Redhat 5 & 6 that Webex/LGO supports. I tried CentOS 6.5 with JAVA 1.7 and it seemed to work at first, but it did not work in the end with the most realistic simulation.
.

You may want to take a look at [https://bugzilla.redhat.com/show_bug.cgi?id=829817](https://bugzilla.redhat.com/show_bug.cgi?id=829817) and [http://www.emsperformance.net/2013/03/25/making-webex-work-on-64bit-fedora-core-18/](http://www.emsperformance.net/2013/03/25/making-webex-work-on-64bit-fedora-core-18/)

Apparently JAVA 1.7 would work on Redhat therefore Centos if you install the package pangox-compat
Alternatively you can get the developmental verson of webex

> Again, running chkdsk /f on my USB drives in Windows is another reason  to keep Windows XP. I've read that chkdsk f/ in Linux is not as good as  chkdsk f/ in Windows.


In Linux you run fsck, why is it 'not as good'?

---

### Post by AbleTassie on 2014-03-30
> **monkeybrain20122 said:**
>  Apparently JAVA 1.7 would work on Redhat therefore Centos if you install the package pangox-compat Alternatively you can get the developmental verson of webex.

In Linux you run fsck, why is it 'not as good'?

Thanks for your replies Monkeybrain,

**Regarding JAVA 1.7 working with Redhat,** I think that is incorrect. I think only JAVA 1.6 with Redhat 5 & 6 is officially supported by WebEx, even though JAVA 1.6 is old. 

See [https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm#OSSUpport](https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm#OSSUpport) and see [https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm](https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm) . Regarding my getting a development version of WebEx, this will not work, as the WebEx version that is relevant is the version that is being used by WebEx & the LGO to host the meeting. The crossplatform features and issues of the version used by WebEx & the LGO are described at the links above. 

**Regarding the superiority of Windows chkdsk**, see this post [http://ubuntuforums.org/showthread.php?t=2187063&highlight=chkdsk](http://ubuntuforums.org/showthread.php?t=2187063&highlight=chkdsk) which seems to be by knowledgeable posters. 

The actual error message in Ubuntu reads: [I]"**Unable to mount FreeAgent Drive:**
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0). Failed to mount '/dev/sdb1': Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. **In the first case run chkdsk /f on Windows then reboot into Windows twice.** The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details."[/I]

Thanks,

R.

---

### Post by monkeybrain20122 on 2014-03-30
> **RMcGinnis said:**
> Thanks for your replies Monkeybrain,

**Regarding JAVA 1.7 working with Redhat,** I think that is incorrect. I think only JAVA 1.6 with Redhat 5 & 6 is officially supported by WebEx, even though JAVA 1.6 is old. 

See [https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm#OSSUpport](https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm#OSSUpport) and see [https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm](https://uspto.webex.com/docs/T28L/mc0806l/en_US/support/xplatform.htm) . Regarding my getting a development version of WebEx, this will not work, as the WebEx version that is relevant is the version that is being used by WebEx & the LGO to host the meeting. The crossplatform features and issues of the version used by WebEx & the LGO are described at the links above. 

Did you read the redhat bug report? They say it is a bug and 1.7 will work with the extra package, also webEx developers are informed about it. As I said earlier, not supported doesn't mean it won't work, just that they don't guarantee that it will. XP will not be supported and you still plan to use it.


```
**Regarding the superiority of Windows chkdsk**, see this post [http://ubuntuforums.org/showthread.php?t=2187063&highlight=chkdsk](http://ubuntuforums.org/showthread.php?t=2187063&highlight=chkdsk) which seems to be by knowledgeable posters. 

```


Well that person  said chkdsk is superior is **for ntfs **and ntfs is a Microsoft file system. If you don't use Windows there is no reason to use ntfs in the first place. so chkdsk is superior for ntfsis not a reason to use xp.

---

### Post by AbleTassie on 2014-03-30
> **monkeybrain20122 said:**
> Did you read the redhat bug report? They say it is a bug and 1.7 will work with the extra package, also webEx developers are informed about it. As I said earlier, not supported doesn't mean it won't work, just that they don't guarantee that it will. XP will not be supported and you still plan to use it.


```
**Regarding the superiority of Windows chkdsk**, see this post [http://ubuntuforums.org/showthread.php?t=2187063&highlight=chkdsk](http://ubuntuforums.org/showthread.php?t=2187063&highlight=chkdsk) which seems to be by knowledgeable posters. 

```


Well that person  said chkdsk is superior is **for ntfs **and ntfs is a Microsoft file system. If you don't use Windows there is no reason to use ntfs in the first place. so chkdsk is superior for ntfsis not a reason to use xp.

Monkeybrain,

I appreciate your replies. 

**Regarding Windows & NTFS** 

QUESTION: Do you think I could easily reformat my USB drives (4GB thumbdrive & 160GB external drive) to a file system other than NTFS without corrupting the files?

**Regarding trying to get the Webex/LGO working desktop sharing with Linux operating systems**, I've spent hours and hours trying. WebEx tech support is only so helpful. They do not encourage various permutations of solutions, like using Centos 6.5, downloading archived JAVA plug-ins, etc. and I only have so much time as well. Though Microsoft will no longer be supporting Windows XP soon, that does not mean that Winodws XP & the latest JAVA plugin will not work with Webex/LGO into the near future.

Thanks,

R.

---

### Post by monkeybrain20122 on 2014-03-30
> **RMcGinnis said:**
> Monkeybrain,

I appreciate your replies. 

**Regarding Windows & NTFS** 

QUESTION: Do you think I could easily reformat my USB drives (4GB thumbdrive & 160GB external drive) to a file system other than NTFS without corrupting the files?

**Regarding trying to get the Webex/LGO working desktop sharing with Linux operating systems**, I've spent hours and hours trying. WebEx tech support is only so helpful. They do not encourage various permutations of solutions, like using Centos 6.5, downloading archived JAVA plug-ins, etc. and I only have so much time as well. Though Microsoft will no longer be supporting Windows XP soon, that does not mean that Winodws XP & the latest JAVA plugin will not work with Webex/LGO into the near future.

Thanks,

R.
Do what you have to. As for WebEx tech supports, I won't take too them seriously if I were you, I would rather listen to the redhat guys (Redhat is a major enterprise player, it is impossible that Redhat clients would have to use old java without any workaround, it is just impossible, makes no sense)

The thing is, tech support guys want to minimize their work so they prefer to give you 'by the book' answers. When  I started Ubuntu I installed 10.04 on a Samsung laptop. Everything worked beautifully out of the box, as a newbie that was very important to me. But I had put off installing Ubuntu for almost a year because the Samsung tech support guys told me Linux was not a supported platform and Ubuntu would never work on that machine, and that I should stick with Windows7 (and I didn't know about live usb then)

---

### Post by AbleTassie on 2014-04-01
> **monkeybrain20122 said:**
> Do what you have to. As for WebEx tech supports, I won't take too them seriously if I were you, I would rather listen to the redhat guys (Redhat is a major enterprise player, it is impossible that Redhat clients would have to use old java without any workaround, it is just impossible, makes no sense)

The thing is, tech support guys want to minimize their work so they prefer to give you 'by the book' answers. When  I started Ubuntu I installed 10.04 on a Samsung laptop. Everything worked beautifully out of the box, as a newbie that was very important to me. But I had put off installing Ubuntu for almost a year because the Samsung tech support guys told me Linux was not a supported platform and Ubuntu would never work on that machine, and that I should stick with Windows7 (and I didn't know about live usb then)

Thank you Monkeybrain,

I don't have a great deal of faith in WebEx tech support. Since I don't own Redhat, I cannot access Redhat tech support. What I do know is that I could not access the WebEx/LGO meeting using Ubuntu 12.04 LTS & JAVA 1.7, even though I could do a WebEx desktop sharing interview using my OWN basic WebEx account. And I could also access secure pages on the LGO's website with a digital signature using Ubuntu 12.04 LTS & JAVA 1.7.

You only get so many chances with LGO bureaucrats. If you miss meetings, that's your tough luck. So I have to try to go with what seems to work given the time and resources I have for experimentation. Windows XP & JAVA 1.7 work according to the best simulations I can get WebEx tech support to do.

Thanks again,

R.

---

