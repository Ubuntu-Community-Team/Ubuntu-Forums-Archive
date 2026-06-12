---
title: "need to set up backup"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by mzimmers on 2012-06-07
and I'm having a few challenges.

1. the drive I want to back up to is owned by root, and I don't have access to it. How do I fix this? I know I can sudo in a terminal, but where do the disks "reside" in the file system?

2. When I partitioned my backup disk, somehow I gave the two partitions identical names. Can I rename one of them?

3. I was just going to use backup, but if anyone has a recommendation for something better, I'm all ears.

Thanks!

---

### Post by traditionalist on 2012-06-07
> **mzimmers said:**
> and I'm having a few challenges.

1. the drive I want to back up to is owned by root, and I don't have access to it. How do I fix this? I know I can sudo in a terminal, but where do the disks "reside" in the file system?

2. When I partitioned my backup disk, somehow I gave the two partitions identical names. Can I rename one of them?

3. I was just going to use backup, but if anyone has a recommendation for something better, I'm all ears.

Thanks!

[http://www.remastersys.com/](http://www.remastersys.com/)  the best backup system for the system  in my opinion, easy, reliable and fast.

For data; 
 [[IMG]http://img710.imageshack.us/img710/193/ubuntusoftwarecenter015.th.png[/IMG]]("http://img710.imageshack.us/i/ubuntusoftwarecenter015.png/")

Change the drive permissions;

[CODE]sudo nautilus[/CODE  [B][COLOR=Red]EDIT:  You should use gksu or  gksudo to run graphical programs as root.  See here;

http://ubuntuforums.org/showpost.php?p=12006778&postcount=3
[/COLOR][/B]
][[IMG]http://img802.imageshack.us/img802/8158/selection014.th.png[/IMG]]("http://img802.imageshack.us/i/selection014.png/")



Yes, you can rename a partition. Use Gparted;

[[IMG]http://img843.imageshack.us/img843/558/ubuntusoftwarecenter013.th.png[/IMG]]("http://img843.imageshack.us/i/ubuntusoftwarecenter013.png/")

Instructions for renaming;

[http://www.tricksfind.in/2011/05/how-to-rename-drive-in-ubuntu.html](http://www.tricksfind.in/2011/05/how-to-rename-drive-in-ubuntu.html)

More related info;

[https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)

---

### Post by mzimmers on 2012-06-07
Thanks for the answers. I think I might have screwed something up on my partition rename, though. My partition doesn't have a mount point. How do I go about adding one? I can re-format if necessary; the partition is empty now.

---

### Post by traditionalist on 2012-06-07
> **mzimmers said:**
> Thanks for the answers. I think I might have screwed something up on my partition rename, though. My partition doesn't have a mount point. How do I go about adding one? I can re-format if necessary; the partition is empty now.


To set it up, use gparted.  Click on the device and look at the information using "View"

[[IMG]http://img841.imageshack.us/img841/8726/devsdagparted022.th.png[/IMG]]("http://img841.imageshack.us/i/devsdagparted022.png/")

Choose what you want to do and Gparted will do it. 

[B][COLOR=Red]Gparted must be used with great care! If you make a mistake it can destroy your system.

[/COLOR][/B][COLOR=Red][COLOR=Black]Make sure you know what you are doing and are on the right device before you change things.  Before you can do anything to devices they must be unmounted.[/COLOR][/COLOR][B][COLOR=Red] 

[/COLOR][/B][COLOR=Red][COLOR=Black]If you want to change something on a /root partition you need to do it from a live disk as you can not unmount the running root partition.[/COLOR]
[/COLOR]**[COLOR=Red] [/COLOR]**

---

### Post by mzimmers on 2012-06-07
Sorry if I'm being dense -- I'm past the point indicated in your picture. I have my two partitions now, but...one of them doesn't have a mount point. I don't know what to do from here.

---

### Post by traditionalist on 2012-06-07
> **mzimmers said:**
> Sorry if I'm being dense -- I'm past the point indicated in your picture. I have my two partitions now, but...one of them doesn't have a mount point. I don't know what to do from here.

Choose the disk you wish to set up.  Delete any partitions now on it. Make a new partition, using the whole disk if desired, or whatever size you want.  Format that partition and give it a mount point. More or less standard for extra disks is;

/media/devicename

in the case shown below one of my extra disks is set up as shown;

[[IMG]http://img98.imageshack.us/img98/8365/devsdagparted024.th.png[/IMG]]("http://img98.imageshack.us/i/devsdagparted024.png/")

This is what you should use unless you want to do something else with that disk. Of course the device name must correspond to the device on your system.

---

### Post by mzimmers on 2012-06-07
OK, here's our misunderstanding: I can't delete all the partitions on this drive; one of them is used when I boot Windows. I have two partitions:

- /dev/sdb1 (for Windows)
- /dev/sdb2 (for Ubuntu, once I can set it up right)

/dev/sdb2 doesn't have a mount point, and (I believe) I need to give it one in order to use the drive/partition, right?

Or, am I mistaken in thinking that each partition can have its own mount point?

Thanks.

---

### Post by traditionalist on 2012-06-07
> **mzimmers said:**
> OK, here's our misunderstanding: I can't delete all the partitions on this drive; one of them is used when I boot Windows. I have two partitions:

- /dev/sdb1 (for Windows)
- /dev/sdb2 (for Ubuntu, once I can set it up right)

/dev/sdb2 doesn't have a mount point, and (I believe) I need to give it one in order to use the drive/partition, right?

Or, am I mistaken in thinking that each partition can have its own mount point?

Thanks.

That is not a misunderstanding. It is the result of incorrect information. You did not say you had other partitions on the disk.

In that case just delete whatever is on  /dev/sdb2  make a new partition in it, format it  and give it a mount point.  Without a mount point disks are not accessible to the system. Each partition can have its own mount point.

---

### Post by mzimmers on 2012-06-07
OK, I click on the unallocated portion of the drive and select Partition->New.

1. Should this be a primary partion, or extended?
2. What file system should I select?
3. How do I go about giving it a mount point? I can't find that option within gparted.

Thank you.

---

### Post by traditionalist on 2012-06-07
> **mzimmers said:**
> OK, I click on the unallocated portion of the drive and select Partition->New.

1. Should this be a primary partion, or extended?
2. What file system should I select?
3. How do I go about giving it a mount point? I can't find that option within gparted.

Thank you.

You have to find some things out for yourself. Using google, or searching this forum, or reading the manual for whatever you want to use. You don't need help, you need information. I am not an information service. If you don't know anything at all about something then you have to make an effort to find out before asking for help.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by mzimmers on 2012-06-07
My questions about the details of the partition were borne of the fact that nothing had worked for me so far, and were intended to ensure I hadn't overlooked something basic. Regarding the third question, it's still not clear to me how to use gparted to set a mount point (and I did look at the page you cited), but it doesn't matter anyway, as I used Storage Device Manager to accomplish that.

It may well be that I "don't know anything at all about something," but it was my impression that this particular forum was appropriate for beginners. Much about the Linux world is difficult to fathom for people getting started, and I've found forums more helpful than reference documentation for answering specific questions such as these. 

In any event, I appreciate your initial helpfulness.

Pursuant to the original question, where it stands now is that backup returns a permission error on an attempt to create a directory, despite the fact that I've set the permissions on the new partition to full access for everyone.

---

### Post by traditionalist on 2012-06-07
> **mzimmers said:**
> My questions about the details of the partition were borne of the fact that nothing had worked for me so far, and were intended to ensure I hadn't overlooked something basic. Regarding the third question, it's still not clear to me how to use gparted to set a mount point (and I did look at the page you cited), but it doesn't matter anyway, as I used Storage Device Manager to accomplish that.

It may well be that I "don't know anything at all about something," but it was my impression that this particular forum was appropriate for beginners. Much about the Linux world is difficult to fathom for people getting started, and I've found forums more helpful than reference documentation for answering specific questions such as these. 

In any event, I appreciate your initial helpfulness.

Pursuant to the original question, where it stands now is that backup returns a permission error on an attempt to create a directory, despite the fact that I've set the permissions on the new partition to full access for everyone.

The point is, that if you don't know what you are trying to do then it is very difficult to accomplish. You have to know what sort of partitions you want and what for. These are basic system requirements. If you don't know what they are then it is pointless and dangerous messing about with powerful system utilities.  I don't know what is in or on your system, and I can never be sure that you have given me the information required to carry out various operations. You already failed to tell me that you were running another boot partition on that disk. This could have resulted in a very serious "error" which would have destroyed that system.

This is very basic information, and without it you will quickly be in very serious trouble with any system. 

People here are doing their level best to help where at all possible, but it is not possible to lead people by the hand.

Although you take any advice you receive here at your own risk, people still strive to give you the best advice possible.  In my opinion you are already taking too many risks trying to do something you obviously know nothing about and have made no effort to find out about.

If anything goes wrong, which is highly likely, you will then say it was the result of bad advice, when in fact it was the result of your lack of knowledge on the matter.

I am always pleased to help people if I can, but I can not give you a course on the whys and wherefores of partitioning and file systems. You have to know why you want to do something as well as how to do it.

Carrying out complex tasks like partitioning with extremely powerful utilities is not something complete beginners should be doing anyway. It will only end in frustration. There are far too many things that can go wrong.

Furthermore, if you are using a help forum like this simply because you are too lazy to look for the information yourself, that is misuse of the resource.

[http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-mount-partition](http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-mount-partition)

---

### Post by mzimmers on 2012-06-07
Thank you for the link. At the risk of beating a dead horse, I'll reiterate that the "mount" option was not open to me before I used Storage Device Manager to add a mount point. 

But...no matter; that issue appears to be resolved. I still would appreciate some assistance in getting some kind of backup working. I have tried to install remastersys, and have run into an error with the GUI installation (probably something to ask in their forum).

So...I guess I'd like to try the simple "backup" program again. Here are my settings: 
Storage->Backup Location is set to "Ubuntu HD" (my newly-created partition)
Storage->Folder is set to /backups.
Folders are set to /home and /opt (for now)

When I click on "Back Up Now" I get a window saying "Backup Failed" Error creating directory: Permission denied.

Since it doesn't tell me what directory it's trying to create, I don't know where to go from here. I can say that the directory "/backups" is set to allow maximum user access.

Any suggestions here would be appreciated. Thanks.

---

### Post by traditionalist on 2012-06-07
The mount point set option is only available when you create a partition with gparted. Which I already posted;

[http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-mount-partition](http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-mount-partition)

QUOTE FROM THE FIRST LINE OF THAT PAGE

**Mounting a Partition**

         To mount a partition:           

[LIST=1]
[*]               Select an unmounted partition.               See [the section called &#8220;Selecting a Partition&#8221;]("http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-select-partition").
[*]               Choose:               Partition &#8594; Mount               and select a mount point from the list.               The application mounts the partition on the mount point and               refreshes the device partition layout in the               gparted window.
[/LIST]
UNQUOTE

Which you apparently did not read.

Did you use this ?;  [http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

You can try grsync to backup;

[[IMG]http://img225.imageshack.us/img225/5117/ubuntusoftwarecenter001.th.png[/IMG]]("http://img225.imageshack.us/i/ubuntusoftwarecenter001.png/")

I don't use any other backup systems so I can't give you any advice on them. There will be a setup for defaults on the system you are trying to use, but I don't know anything about it. Is the program name "Simple backup" ?

There is a lot of information on how to set up remastersys and various possible problems here;

[http://www.remastersys.com/forums/index.php?PHPSESSID=80eq96qsk35pe2rs8ckc1b34j4&board=38.0](http://www.remastersys.com/forums/index.php?PHPSESSID=80eq96qsk35pe2rs8ckc1b34j4&board=38.0)

You have to install the base system first ( which can be used fom the command line) and then the GUI. There are two GUI's, you need to choose the one you prefer or which works best for you. This is explained at length on the the introductory page I posted and which you obviously also did not read.

[http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html)

As I already pointed out, trying to set up systems by asking for simple "step by steps" on an absolute beginners forum wont get you very far. You need to know something about what you are doing, not least so that you can ask the right questions. With a modicum of knowledge you wont need to ask as many questions either.

---

### Post by traditionalist on 2012-06-07
Permissions are invariably confusing and difficult for beginners. Many graphical user interfaces ( GUI's) make things easier but you still have to get some idea of what you can do and what you can't as a user  or as root.  You can not even read some files unless you are root.

Some "simple" backup programs are extremely confusing.

---

### Post by traditionalist on 2012-06-07
For any beginners who are reading this and are totally confused by it, you don't need to do any of this to get started. Normally the Ubuntu setup disk will give you various choices after it has checked your system and give you various choices. You just need to choose what you want to do.

So don't get hung up with all this stuff.

---

### Post by mzimmers on 2012-06-08
> **traditionalist said:**
> The mount point set option is only available when you create a partition with gparted. Which I already posted;

[http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-mount-partition](http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-mount-partition)

QUOTE FROM THE FIRST LINE OF THAT PAGE

**Mounting a Partition**

         To mount a partition:           

[LIST=1]
[*]               Select an unmounted partition.               See [the section called “Selecting a Partition”]("http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-select-partition").
[*]               Choose:               Partition &#8594; Mount               and select a mount point from the list.               The application mounts the partition on the mount point and               refreshes the device partition layout in the               gparted window.
[/LIST]
UNQUOTE

Which you apparently did not read.

Actually, I read it more than once. The missing bit of knowledge was that one must label a new partition in order for gparted to create a mount point. At least, that's the conclusion I've come to after some experimentation.

> Did you use this ?;  [http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)


Yes.

> You can try grsync to backup;

[[IMG]http://img225.imageshack.us/img225/5117/ubuntusoftwarecenter001.th.png[/IMG]]("http://img225.imageshack.us/i/ubuntusoftwarecenter001.png/")

I don't use any other backup systems so I can't give you any advice on them. There will be a setup for defaults on the system you are trying to use, but I don't know anything about it. Is the program name "Simple backup" ?

No, it's just called "backup" and can be found in the "System" portion of "System Settings."

I will take a closer look at grsync. Thanks again.

---

### Post by traditionalist on 2012-06-08
The main thing is to get it  up and running smoothly. I still think you would have been better off using the Ubuntu default install options. When they work, which is the majority of the time as only a few people have problems with them, they save you all this initial trouble.

Even when you have it running, if you immediately dive into the system and start changing things you will have problems, although this is one way to learn a lot it is probably  not the best way if you want a smoothly functioning "production" machine.

You can not learn everything immediately no matter how you go about it, it is quite impossible. I am still only a beginner myself with a very great deal to learn. I have been using Linux for five weeks. Before that I was a Windows user. However, I have been using it and playing with it for upwards of twelve hours a day.  Not everybody can do this of course. Anyway, good luck with your machine.

---

### Post by traditionalist on 2012-06-08
It occurred to me that you might not know how to use Grsync.

For a full backup of the complete system ( make sure you have enough space on the destination).

Run;
```
gksu grsync
``` ( Although there is a setup option in "preferences"  to "Run as superuser", and you will then  be prompted for your password).

The setup is;

[[IMG]http://img40.imageshack.us/img40/2086/grsyncdefault1008458ela.th.png[/IMG]](http://img40.imageshack.us/i/grsyncdefault1008458ela.png/)

 
when you have set up as shown, go to "File"  and "Execute". You can also do a "Dry Run" which will show you what would have happened using the setup you have chosen.

This will also back up any mounted drives etc. If you don't want to backup mounted data disks then unmount them before you run.

This can take a while depending on your setup.  For individual directories, drives, partitions, etc,  " /Home"  for instance;

[[IMG]http://img443.imageshack.us/img443/2456/grsyncdefault002.th.png[/IMG]]("http://img443.imageshack.us/i/grsyncdefault002.png/")

If they are your directories you don't need to run as root, you can just use;

```
Grsync
```It is best not to play around with anything else while the backup is running.

It  is fairly simple to use and not much can really go wrong unless you  make a mistake on the setup.  To restore a backup, simply reverse the  synchronisation so that the destination becomes the source, and the  source becomes the destination.;

Go to "File",  "Switch Source with Destination";

[[IMG]http://img36.imageshack.us/img36/5662/workspace1003.th.png[/IMG]]("http://img36.imageshack.us/i/workspace1003.png/")

Future backups are very fast because only changed files will be sent to the destination.

---

