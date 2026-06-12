---
title: "Howto: Move /home and secure your files and configuration"
date: 2005-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Lunde on 2005-07-06
[SIZE=4]**Howto: Move /home and secure your files and configuration**[/SIZE]

I see many people here in this forum which have problems with their system after they  install software, drivers or patches. It's hard to tell what causes these problems and hard to solve them. Sometimes some of us loose our beloved configuration which we have spent a long time to tweak and perfectionize. ...Frustrating!
So lets put an end to this:

**Note:** It's a while since I did this, so please let some of the gurus in here read it first if you are not sure what you are doing. Then if there are any mistakes, I'll correct them and remove this note.

Be careful, do this at your own risk, if you do something wrong you can end up losing files or configuration. Again, if you do this correct, you hopefully never end up losing anything again.


[B]
[SIZE=3]MOVING THE HOME DIRECTORY[/SIZE][/B] 

If we have a free disk or a partition to play around with a good choice is to make a separate /home partition. By having a separate /home partition we don't have to worry that much about our files and folders anymore If everything breaks down and we get to the point of an upgrade or a reinstall, we can do so and just leave our files where they are.

This is what we do:

[B]1.) Creating the filesystem
[/B]
Use fdisk or any partitioner you feel comfortable with (Preferably not Windows fdisk), and create a partition or format your drive to a Linux filesystem. **Ext3** is good, some prefer **ReiserFS** or other, but this is your own choice. If you don't know the difference, choose **Ext3**.
Note: More information about mounting and partitioning disks in linux: 
[http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive](http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive)


**2.) Moving the /home**

First we need to log out of gnome. At the GDM (Gnome Login Screen) press:
**Ctrl+Alt+F1**

Then Login as your user and type (Without the #): 
**# sudo -s**
To permanently become root.
[B]

# mkdir /mnt/home
# mount -t ext3 /dev/hda5 /mnt/home [/B]
**Note:** In this case I use **hda5**, which is my second aprtition on my first hard drive, this needs to be changed to your correct partition number. Also when I mount the partition I tell the command which type of filesystem I'm mounting (**Ext3**). this also needs to be changed to the correct file system of your choice. 

Then we need to copy all the files from your **/home** directory, this may take a while since you probably have a lot of documents to move

**NOTE:** [dradul]("http://ubuntuforums.org/member.php?u=17939") suggest to use **rsync -aS** instead of **cp -a** 
[http://ubuntuforums.org/showpost.php?p=385415&postcount=25](http://ubuntuforums.org/showpost.php?p=385415&postcount=25)

**# cp -a /home/* /mnt/home**

now we have to edit the **/etc/fstab** to point the direction to the new home drive


[B]Understanding the fstab
[/B]
**/etc/fstab** is the configuration document that tells Ubuntu where to find your disks. 
Next you need to understand the disk structure. If you have one hard drive, that will most likely be named **hda**, if you have a slave hard drive to, that will most likely be named **hdb**. Your cd-rom will be **hdc**. If you partition your disk, **hda** will turn into **hda1, hda2, hda5** and so on, the number is individual depending how your disk is partitioned.
Ex.: /dev/hda1 ...means: dev = the devise directory. Your devise information is stored in the"/dev

**# pico /etc/fstab** 
Will bring up something like this in the Pico Text Editor: 

#-------------------------------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc                   /proc                  proc      defaults       0             0
/dev/hda1          /                         ext3      defaults,errors=remount-ro 0 1
/dev/hda6          none                  swap     sw 0 0
/dev/hda5          /home                ext3       defaults,errors=remount-ro 0 1
/dev/hdb1          /mnt/sys2          ext3       defaults,errors=remount-ro 0 1
/dev/hdc             /media/cdrom0  udf,iso9660 ro,user,noauto   0     0
/dev/fd0              /media/floppy0 auto        rw,user,noauto   0     0
/.iso/ubuntu-5.04-install-i386.iso /mnt/iso iso9660 ro,loop,auto 0 0
#---------------------------------------------------------------------------------------------------------
[B]
Note: [/B]We need to ad a line like this, again changing the (**ext3**) filesystem of your choice and the (**hda5**) the disk / partition you have moved your **/home **to.

/dev/hda5          /home                ext3       defaults,errors=remount-ro 0 1

**Note: **I like to add this line in accordance to your disk structure like shown above

when you are done press:
**Ctrl+o** to overwrite your old fstab. Press **Enter** to confirm the overwrite and **Ctrl+x** to exit 

Then rename the old **/home**, remove the mounted home dir and mount the new **/home** by:
[B]
# mv /home /homeOLD
# mkdir /home
# umount /mnt/home 
# mount -a [/B]



[B]3.) Check that all your files and configuration is correct in your new /home. 
[/B]
Log in and see that everything is as it should, and if it is we are now ready to delete your old home directory.

Open a terminal window and type (Without the $):
[B]$ sudo rm -rf /homeOLD
[/B]


[B][SIZE=3]CREATE BACKUPS OF YOUR SYSTEM[/SIZE]
[/B]

**NOTE:** [AgenT](http://ubuntuforums.org/member.php?userid=10526) suggest to us an alternative backup system **rsnapshot**. 
[http://www.rsnapshot.org](http://www.rsnapshot.org)

No need to reinvent the wheel, [Heliode](http://www.ubuntuforums.org/member.php?userid=10871) has written an excellent howto for creating backups of your system located here:
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

I will just add a coupple of thoughts of how to create different backups for different parts of your system.


[B]1.) System backup.
[/B]
As Heliode describes, do a system backup, but exclude also the **/home**. For the /home we will create a separate backup. Save this backup under your new /home


[B]2.) User configuration backup
[/B]
I prefer not storing my personal files directly under my **/home/username**, but instead create a subfolder: **Documents**.
Then do a backup as Heliode describes of your **/home** directory, but exclude the **/home/username/documents** Save this backup under your new /home. 

**Note:** Remember to also exclude this backup and the system backup which is now located under /home. 


**3.) Personal files backup**

Last you can also do a backup of your personal files if you like, these should preferably be backed up to a CD or a DVD.



**[SIZE=3]SUMMARY[/SIZE]**

Now if you mess up your system, you can restore this from the command line. If you mess up your personal configuration, you can also restore this easy from the command line.

---

### Post by r0jaws on 2005-07-08
just want to ask what may be a silly question, does the format have to be ext2/ext3? can it be fat32? I'd like to move my /home to a shared partition, accesed by numerous oS's and want them all to have rw access, this does include windows so therefore must have a MS format (unfortunately). Will this still work? or are there problems associated with having your home directory in a non-*nix format?

---

### Post by Lunde on 2005-07-08
[QUOTE=r0jaws]just want to ask what may be a silly question, does the format have to be ext2/ext3? can it be fat32? I'd like to move my /home to a shared partition, accesed by numerous oS's and want them all to have rw access, this does include windows so therefore must have a MS format (unfortunately). Will this still work? or are there problems associated with having your home directory in a non-*nix format?[/QUOTE]
 I would'nt recomend it. Some earlier comments about that subject:
[QUOTE=davahmet]I don't think there is anything that prevents you from putting /home on a FAT32 partition, it's just an extremely bad idea.  I believe you may not like the results that come from doing this.

The problem is with ownerships and permissions.  Linux uses filesystem ACLs to assign ownership and permissions to files, directories and symlinks.  Unfortunate, this concept isn't really applicable in the Windows world, so putting files on a FAT32 partition should give it root ownership with wide-open permissions.  You might say, "so what.  I like having a Windows security model" but the problem then becomes that your .profile, .bash_profile and or .bashrc is no longer owned by you.  Without these important files, you may face instability or complete failure to log on.  I've never tried it so I'm not sure how bad the results would be.

Putting /home on FAT32 may seem like a convenient idea, but certainly it is an experiment only for the adventurous.[/QUOTE]

[QUOTE=desdinova]I'd second the "disaster" .... as FAT32 has no concepts of permissions its very likely things like X and the like are just not going to work.[/QUOTE] 
However.. what you can do is to mount the Fat32 partition as a subdirectory under /home/username (**~/**). then you can just save the files you want to share and your backups to that directory and exclude it in the tar backups.

---

### Post by trash on 2005-07-18
just gave the howto a try, but I think there is a step missing, we moved the /home to /homeOLD so /home no longer exists as a mount point.
so we need to create a new /home directory i think.

EDIT:
btw, THANKS!
I never thought it wouuld be so simple:)

---

### Post by Lunde on 2005-07-18
[QUOTE=trash]just gave the howto a try, but I think there is a step missing, we moved the /home to /homeOLD so /home no longer exists as a mount point.
so we need to create a new /home directory i think.[/QUOTE]
 Thank you, correct! The howto is now updated.

---

### Post by kultex on 2005-07-26
"However.. what you can do is to mount the Fat32 partition as a subdirectory under /home/username (~/). then you can just save the files you want to share and your backups to that directory and exclude it in the tar backups."

I would like to do this - but as newbe I have no idea how it works - could you give me a short description

---

### Post by Lunde on 2005-07-26
[QUOTE=kultex]"However.. what you can do is to mount the Fat32 partition as a subdirectory under /home/username (~/). then you can just save the files you want to share and your backups to that directory and exclude it in the tar backups."

I would like to do this - but as newbe I have no idea how it works - could you give me a short description[/QUOTE]
 Sure...

In terminal as your user type:
**$ mkdir ~/shared_fat32**
I use the name **"shared_fat32"** as an example, you may name it to what ever you want. but remember to do so also in fstab.

**$ sudo gedit /etc/fstab**

Add this line just above the /dev/hdc /media/cdrom... line:

**/dev/hdXX    /home/username/shared_fat32    vfat user,rw,exec 0 0**
[B]
Note:[/B] Change the **"username"** to your user name and change the **"hdXX"** to your partition / disk number. Ex: hdb5

Save and Exit

Again in terminal type:
**$ sudo mount -a**

And that's it..

---

### Post by kultex on 2005-07-28
tank you - but is it not solving my problem. I need to have a link of directories (I hope it is the right word in english) I am actually working on the desktop and the problem is, that in Ubuntu I can not create a link on the vfat partitions (i hope it is clear, what I mean).

Do you know any solution - the only thing I see in the moment is [http://www.fs-driver.org/](http://www.fs-driver.org/) , but writing to ext3 from windows could be dangerous (searching the net)

---

### Post by Lunde on 2005-07-28
[QUOTE=kultex]tank you - but is it not solving my problem. I need to have a link of directories (I hope it is the right word in english) I am actually working on the desktop and the problem is, that in Ubuntu I can not create a link on the vfat partitions (i hope it is clear, what I mean).

Do you know any solution - the only thing I see in the moment is [http://www.fs-driver.org/](http://www.fs-driver.org/) , but writing to ext3 from windows could be dangerous (searching the net)[/QUOTE]
 I'm not sure if I understand what you meen. You can create what ever you like on the fat32 partition form both Linux and Windows. Maybe there are some file pernission problems, if that's the issue it can be fixed.

If you have a fat32 partition, I don't see why you would want to write to the ext3

---

### Post by kultex on 2005-07-29
I could transfer all my files and mails to /home, rename the partition in Windows - and it would be perfect. It works fine - I tried it, but I find it still to dangerous.

Yes it is a qustion of permission.

The owner of the shared partition is root - to make a link it is necessary that the owner is the user. After I changed the permission, it worked fine.

I know to change the permission for one file, but not for all the files eg. the whole partition.

---

### Post by Sam on 2005-07-29
[QUOTE=kultex]I could transfer all my files and mails to /home, rename the partition in Windows - and it would be perfect. It works fine - I tried it, but I find it still to dangerous.

Yes it is a qustion of permission.

The owner of the shared partition is root - to make a link it is necessary that the owner is the user. After I changed the permission, it worked fine.

I know to change the permission for one file, but not for all the files eg. the whole partition.[/QUOTE]
```
$ cd <dir>
$ find . -type f -exec sudo chown <username>:<group> {} \;
```
Replace <dir> by the base directory.
Replace <username> and <group> with your username (the group you belong has the same name as the username).

---

### Post by foxy123 on 2005-07-29
It is a very good idea to have /home on a separate partition. I have it on m desktop PC and am going to do it on my laptop. i've got a 40Gb HD and want to split in in 2: a system partition and a home partition. I wonder how much space should I left for system? Would 4.5 gig be enough?

---

### Post by Sam on 2005-07-29
[QUOTE=foxy123]It is a very good idea to have /home on a separate partition. I have it on m desktop PC and am going to do it on my laptop. i've got a 40Gb HD and want to split in in 2: a system partition and a home partition. I wonder how much space should I left for system? Would 4.5 gig be enough?[/QUOTE]
Yes, I have personally 3.5 Go on my root partition, with a lot of applications installed and a 32bit chroot environnement.

---

### Post by AgenT on 2005-07-29
>  I recommend not storing your personal files directly in your **/home/username**, but to create a subfolder: **Documents**.
Then do a backup as Heliode describes of your **/home** directory, but exclude the **/home/username/documents** Save this backup under your new /home. 

**Note:** Remember to also exclude this backup and the system backup which is now located under /home.

Can someone explain to me what the point of doing this is? Why everything in Documents? Are you saying that /home/xyz/ should be empty except for the dotted "invisible" files (configs)? Why? What are the advantages of this?

Curious. Right now I have a much better backup plan than what is explained in the backup how-to using **rsnapshot** (search for it, it's well worth it!). It's much better because of a lot of reasons, but one is: acts like rsync and uses hard links (meaning one can have 16 backups of home that has an average of 5GB and have all that be around 5GB!).

---

### Post by Lunde on 2005-07-30
I guess I just prefere collecting the documents in a sepereate folder. 

I find it a great benefit running emulators like VMware, then share the documents dir and use the same dir as My documents in Windows. 

Also be able to share the documents between users without giving write access to configuration files. 

And be able to do an extreemly quick and easy backup and restore of the user configuration

I can't find anything negative about seperating configuration and documents, if there is please let me know.

I'm definitly going to look into rsnapshot. Thanks

---

### Post by AgenT on 2005-07-30
> I find it a great benefit running emulators like VMware, then share the documents dir and use the same dir as My documents in Windows.  But could'nt you do the same with your home dir? If you are willing to share all your personal info, your personal configs won't really be more of a security risk. Especially since this is an emulator so you are going to be accessing these files from the same computer.

 > Also be able to share the documents between users without giving write access to configuration files.  Agreed. But why would you share *all* your documents with other users? If I were to share I would make a "share" folder and share that. This way I control what files are shared and what files are not.

 >  And be able to do an extreemly quick and easy backup and restore of the user configuration This I do not understand. How is changing the folder make a difference in how easy it is to backup and restore? Because you only want to backup your regular files? First, all you have to do is exclude all dotted files which is easy to do. Second, if you are backing up your home files, why would you not backup your configs as well? Maybe it has to do with how limited you are with your current backup solution (see rsnapshot).

 >  I can't find anything negative about seperating configuration and documents, if there is please let me know. First, it's more annoying to backup and restore (twice the work - granted, it's still not much more). Also, it's more cumbersome. And it makes browsing your home dir more annoying because now you have to go up/down one extra folder (instead of it being /home/something it is /home/something/somethingelse). More work. There are a lot of other specific reasons but my guess is they don't apply to you. To me it's like a waste of a folder. Sort of like having your config files in /etc/documents/ instead of /etc/.

Personally, I use multiple folders inside my home folder. Have a nice layout with different folders for different type of files. I backup the whole /home/ folder, plus others (/usr/local/bin/, /etc/, etc.). And up to this point I only needed to use my backup twice. Once because I deleted a file accidently (ha!) and the other time because I migrated from one distro to another. Both ran rsnapshot. And I backup "daily" and "monthly".
 
> I'm definitly going to look into rsnapshot.  Good idea! [http://www.rsnapshot.org/]("http://www.rsnapshot.org/") - the author is also a very nice person.

---

### Post by Lunde on 2005-07-30
I guess it's just preference to what you find most beneficial.

Sharing and user authentication is easy done on several levels anyway, no difference there accept the possibuility to share all without the configuration files.

I have 60gig of files, don't want to backup all of that, can exlude what ever you want anyway form the backup, but I guess I just find it more easy collecting the files in one place. If I want to restore my configuration, I just do so in 5min. And to be honest, I only backup about 5% of my documents, I'm not so scared of loosing the rest. 

I've made a menu based shell script / program that does the backup and restore for me. As soon as I'm done testing it, I'll post it here

I agree a bit on the extra folder regarding downloaded programs / tar files etc. This is mostly the only thing I navigate to by terminal. I like using symlinks placed on the desktop and/or directly under ~/

But I guess you're right, I might be a bit direct when I use the word recommend, I should maybe change it to I prefere.

---

### Post by AgenT on 2005-07-30
Nah, it's just your preference. No need to change anything. ;)

You seem to have your files and backup setup one way while I have it setup a totally different way. Mine works for me. Just so you know, rsnapshot allows you to exclude and include files and folders based on a lot of specifications (whole file names or regular expressions, etc.).

---

### Post by Lunde on 2005-07-30
[QUOTE=AgenT] 
 Good idea! [http://www.rsnapshot.org/]("http://www.rsnapshot.org/") - the author is also a very nice person.[/QUOTE]

Rsnapshot is added in the howto as an alternative backup solution. 

And... Recommend is changed to prefere :-)

---

### Post by kultex on 2005-07-31
I found something:

I changed my fstab entry to:

/dev/hdxx /home/"username"/windows_e vfat user,rw,exec,uid="username",gid="username" 0 0

now, the whole partition belongs to the user, but still it is not possible to make a link - when I try this in Nautilus, I get all the time: Error "Operation not permitted" while creating a link to "/home/tom/windows_e/Bilder"

But with the filemanager gentoo or emelfm it is possible - so this is just a problem of Ubuntu, Gnome or Nautilus.

---

### Post by Lunde on 2005-07-31
[QUOTE=kultex]I found something:

I changed my fstab entry to:

/dev/hdxx /home/"username"/windows_e vfat user,rw,exec,uid="username",gid="username" 0 0

now, the whole partition belongs to the user, but still it is not possible to make a link - when I try this in Nautilus, I get all the time: Error "Operation not permitted" while creating a link to "/home/tom/windows_e/Bilder"

But with the filemanager gentoo or emelfm it is possible - so this is just a problem of Ubuntu, Gnome or Nautilus.[/QUOTE]
 I don't think you have to set the owner in fstab. But try to **chown username mount_directory**

---

### Post by NZ-Wanderer on 2005-10-03
I have another partition at the end of /home and was wondering if I used a partitioner in windows and merged the end partition with the /home partition making one big /home partition, would I have to edit anything in Ubuntu or would Ubuntu pick up that the /home partition is bigger than it used to be??

---

### Post by Lunde on 2005-10-03
I would'nt suggest using a windows partitioner don't even know if it supports Ext3 or the partition type your home is located on. You should do a backup or just move the files first then recreate / expand your /home partition with fdisk or some other partitioning tool for linux. Be careful so you don't screw up your system.

---

### Post by NZ-Wanderer on 2005-10-03
Thanks for the reply..
I have partition Magic and Acronis Disk Director. - I Know Partition Magic doesn't support EXT3, but the Disk Director suite does, so I was planning on using that to do it..
Hehehe I already made 3 backups of my /home partition and have them safely stored away on both my main computer and my networked computer, (I like being better safe than sorry)
I guess I was just a little worried that by increasing the size of /home that Ubuntu wouldn't like it without me doing a fresh install...

---

### Post by GTvulse on 2005-10-03
[quote=Lunde]Then we need to copy all the files from your /home directory, this may take a while since you probably have a lot of documents to move
```
# cp -a /home/* /mnt/home
```
[/quote]

Please don't. cp is not safe nor designed for mirroring tasks.

You should use a proper tool such as ```
rsync -aS /origin/. /target/. 
```or a simple ```
cd /origin && tar cf - . | ( cd /target ; tar xf - )
``` Personally I prefer rsync because it can do md5 checksums on all files to decide if they need copying or not, by adding the "-c" flag.

---

### Post by Lunde on 2005-10-04
No problem increasing the size of /home.

---

### Post by John.Michael.Kane on 2005-10-04
Lunde can this be done when installing ubuntu for the frist time, when it ask the user to set up partitions. also what size do you all use for your home dir. i was thinking of setting up partitions like this.. just wanted to know if anyone else has set up their system like this, and how did it work out. Thanks for any, and all help.

/boot
/ 
/usr/
/home/

---

### Post by foxy123 on 2005-10-04
[QUOTE=SD-Plissken]Lunde can this be done when installing ubuntu for the frist time, when it ask the user to set up partitions. also what size do you all use for your home dir. i was thinking of setting up partitions like this.. just wanted to know if anyone else has set up their system like this, and how did it work out. Thanks for any, and all help.
/boot
/ 
/usr/
/home/[/QUOTE]

Though I did not have a separate /boot partition, I have other three separately on my desktop and it works fine. I guess you should allow 3-4 gigs for /usr and 2-3 for /, leaving the rest for /home.

---

### Post by Lunde on 2005-10-04
I guess you can have as meny partitions you like, just be aware that you lose some space because you need to allocate the partitions larger then the content that it will contain, if you have one big partition you need less free space. 

There are benefits to have a seperate boot partition and a seperate /home partition, but for the rest, I guess for a small system running on 1 disk it's more beneficial to keep it in one partition. If you run out of space later, you can mount a new partition or disk as your /usr.

As for the size of the /home.. this is up to you, as large as you need, it depends only on how much personal stuff and programs are you going to store on your disk. 

It all comes down to how and what you use your system for, if it's a webserver, personal computer, network server etc and what programs your running. 

There are some benefits of which filesystem your running on the different partitions / disks, depending if your handling many small files or some very large files and how frequent files are moved etc..

---

### Post by Lunde on 2005-10-04
Thanks **dradul**, I'll make a note in the howto above

---

### Post by mrmcctt on 2005-10-16
[QUOTE=foxy123]Though I did not have a separate /boot partition, I have other three separately on my desktop and it works fine. I guess you should allow 3-4 gigs for /usr and 2-3 for /, leaving the rest for /home.[/QUOTE]

When doing this at setup, do you have to do anything different?  This is what I did with a new install on a dual boot XP/Ubuntu system.

[Link to my original post on this subject.]("http://www.ubuntuforums.org/showthread.php?t=76826&highlight=%2Fhome+issues")

What I need to know is, will Ubuntu pick up the home partition and use it for my home directory or do I have to do something after setup to point my home directory to this partition.

Thank you.

---

### Post by foxy123 on 2005-10-17
[QUOTE=mrmcctt]When doing this at setup, do you have to do anything different?  This is what I did with a new install on a dual boot XP/Ubuntu system.

[Link to my original post on this subject.]("http://www.ubuntuforums.org/showthread.php?t=76826&highlight=%2Fhome+issues")

What I need to know is, will Ubuntu pick up the home partition and use it for my home directory or do I have to do something after setup to point my home directory to this partition.

Thank you.[/QUOTE]
No you have to do it manually. I do not remember the exact sequence but it should be quite straight forward. You should assign your hda4 to /home and hda2 to /.

---

### Post by bradroger on 2005-10-18
With regards to those discussing having a fat32 home directory...is there any issues beyond permissions?  I was planning on mounting a music and movies directory in home, that would be a separate fat32 partition.  Is there any disadvantages to having large files in a fat32 partition?  Does linux deal better with its own format efficiency-wise?  I've heard of something like journalling file systems...does that come into play?

Thanks

---

### Post by foolosophy on 2006-04-13
[QUOTE=r0jaws]just want to ask what may be a silly question, does the format have to be ext2/ext3? can it be fat32? I'd like to move my /home to a shared partition, accesed by numerous oS's and want them all to have rw access, this does include windows so therefore must have a MS format (unfortunately). Will this still work? or are there problems associated with having your home directory in a non-*nix format?[/QUOTE]

you can add ext2 or ext3 support to windows... i've done it.. look up in google.

---

### Post by disabled_20220313 on 2006-12-09
Hi,

Just used your guide to get my home directory set up on a separate hard drive.

It worked brilliantly! Though I used the rsync command and not cp. Could you change it to the rsync command, as a lot of other guides I read dismiss cp as it is not thorough enough.

Still thanks again. 

Ciaran

---

### Post by ~LoKe on 2006-12-14
Worked flawlessly.  Had it done in under 2 minutes.

Oh, and does anyone know why my 250GB SATAHD shows up as 232GB?  I assume this is normal?

---

### Post by disabled_20220313 on 2006-12-16
> Oh, and does anyone know why my 250GB SATAHD shows up as 232GB? I assume this is normal?

Yes that is perfectly normal, it happens because the definition of a gigabyte being used is different to different people.

Some people (software programmers) consider 1 gigabyte to equal 1024 megabytes. Hard drive manufacturers consider 1 gigabyte to equal 1000 megabytes. 

When you have a large drive the 24mb difference can add up, hence when the software of your computer figures out how much space you have it uses a different order of magnitude.

Nothing to worry about at all.

---

### Post by ~LoKe on 2006-12-16
Oh, I thought that only applied to DVD's.  Thanks. :)

---

### Post by Pedro84 on 2007-02-09
Hmm. I Got problem. 
I has HTFS partitions mounted using ntfs-3g and my Ubuntu doesn't mount my new /home directory partition. When I use

mount -a

I got

[mntent]: line 23 in /etc/fstab is bad
WARNING: Deficient FUSE kernel module detected. Some driver features are
         not available (swap file on NTFS, boot from NTFS by LILO), and
         unmount is not safe unless it's made sure the ntfs-3g process
         naturally terminates after calling 'umount'. The safe FUSE kernel
         driver is included in the official Linux kernels since version
         2.6.20-rc1, or in the FUSE 2.6.0 or later software packages,
         except the faulty FUSE version 2.6.2. For more help, please
         have a look at /usr/share/doc/ntfs-3g/README.Debian. Thanks


1. Any tips?
2. Maybe someone knows how to convert ntfs to xfs without formatting partitions? I can't lose my data and I cannot make backup [540 GB:), mostly my band's concerts;)]

Best wishes
Pedro84

---

### Post by rei on 2007-03-17
Hi, I followed this guide to the T and it worked like a charm. However, I get the following message everytime I boot now:

```

kernel: [17179600.604000] sda: assuming drive cache: write through
kernel: [17179600.604000] sda: assuming drive cache: write through

```

I looked at my syslog and found the following snippet:

```

kernel: [17179600.604000] sda: Write Project is off
kernel: [17179600.604000] sda: Mode Sense: 03 00 00 00
kernel: [17179600.604000] sda: assuming drive cache: write through

```

Is this something I should be concerned about? I tried looking around 'net about "assuming drive cache: write through" but it seemed like it was never an error.

---

### Post by Jack Jebedee on 2007-03-28
I plan on doing a clean install when Ubuntu distributes Feisty Fawn 7.04.  During the install, would it be easiest to use gparted to mount hdb at /home to get a separate home directory that won't be disturbed during future updates?

... JJ

---

### Post by satellite360 on 2007-04-17
Great guide, was wondering how to shift my /home to a partition and your guide gave me the answer.

Thanks

---

### Post by Ajc on 2007-04-25
> **trash said:**
> just gave the howto a try, but I think there is a step missing, we moved the /home to /homeOLD so /home no longer exists as a mount point.
so we need to create a new /home directory i think.

EDIT:
btw, THANKS!
I never thought it wouuld be so simple:)


=> so has this been included in some new documentation somewhere ?

... I have the problems of having followed the steps, I now have no home directory

can someone point me to the new / updated version of this ... many thx

Ajc

---

### Post by diss on 2007-05-10
thanks, worked for me 100% :) 

nice guide

---

### Post by HumbleGod on 2007-05-14
I'm in the process of following this guide for one of my computers, but when I got to the step on editing the fstab I was confronted by virtually unreadable strings of numbers. Apparently fstab relies on UUID for device identification now. (Forgive me if this isn't news, but I'm still a relative newbie and I didn't see this mentioned here, so it might be relevant to somebody.)

So to figure out your partition's UUID, type this:
```
$ sudo vol_id -u device
```

Then I suppose you can just add that info into your fstab accordingly, following the format of the other devices. (I'm still in the middle of this, so I can only assume it works!)

Source: [this thread]("http://ubuntuforums.org/showthread.php?t=427612").

---

### Post by jerrydrussell on 2007-07-22
Ack!

Ijust followed this guide step-by step on ubuntu feisty fawn 7.04, and now I can't boot at all. All seemed perfecly fine until I went to the final step-deleting /home/old on the original partition.  At that pint the system errored and locked.  I rebooted, and the system will not boot into gnome or KDE, nor can I get to a terminal window to restore the old /home folder!

Any help would be immensly appreciated, I'm down to no computer right now, which is going to cost me countless amounts of money in lost work!!!!

---

### Post by ChadMC on 2007-07-24
> **jerrydrussell said:**
> Ack!

Ijust followed this guide step-by step on ubuntu feisty fawn 7.04, and now I can't boot at all. All seemed perfecly fine until I went to the final step-deleting /home/old on the original partition.  At that pint the system errored and locked.  I rebooted, and the system will not boot into gnome or KDE, nor can I get to a terminal window to restore the old /home folder!

Any help would be immensly appreciated, I'm down to no computer right now, which is going to cost me countless amounts of money in lost work!!!!

I'm in the process of doing this now. I'm doing everything from the LiveCD, because I had to create and resize some partitions (i used gparted).

So in your case, I would suggest booting up the Live CD, and then trying to sort things out from there. I'm about to restart to see if I can boot up successfully. I believe I did everything right.

---

### Post by margaf77 on 2007-07-29
Is there any reason this cant be done without logging out of GNOME/KDE? Im using kubuntu and did everything from within KDE using a terminal window and all seemed to work.

---

### Post by L8erG8er on 2007-07-31
Lunde,
Thank you for taking the time to post this how-to.  It worked great for me - used rsync to move the files.  Made new home directory on an entire new disk!

Question (sorry to be stupid) - After finishing and looking at my new home directory, I noticed that I am left with an empty /mnt/home directory.

Can I remove it?  As it is empty, I can't see any further use for it...

---

### Post by beyboo on 2007-09-09
This just works  !!  

I now have a shiny 55G humble new  /home dedicated  in between the 520G of ntfs, ext3 is slowly eating in to my NTFS - and I am loving it ;) 

The only additional step I had to  perform was to find out the  UUID of my new part using vol_id /dev/sda2 command as as I am fesity !!

I additionally ran "rync -aSv" as I like to see all that is going on. Its feels raw power to see the blinding scroll of the path names being sucked in by the top of the terminal window !

I understand the thread is old, however since it is so relevant and simple to use, I would recommend upgrading the original post with a note for this change to the feisty users, so no one has to hunt around or read the entire thread to find this out  ;)

Thanks for the gr8 guide buddy !!:guitar:

---

### Post by diskotek on 2007-09-20
my ext3 partition is getting bigger day by day. i'm now moving my /home driectory on desktop feisty fawn. well everything seem pretty well, execpt my monitor. when i log out from gnome, my screen is blinking and  glitching time to time. but it blinks contuiniously. it's the first time i ever see my monitor like that. it's not very relevant but anybody knows anything about it?

---

### Post by sasquatch74 on 2007-09-29
Just a quick thank you for this howto.  I had tried other guides to move my /home directory, but they did not work.  This did the trick!!!

---

### Post by pinkpanther_bc on 2007-10-02
well what would be the correct info to put in my fstab?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bf54a21f-39af-4eca-8787-1d1d04c003d9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=689fa8ae-41af-4c35-b1e4-caf365ba269e /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=c96a4ca6-41ec-4f2c-91cd-54076eb2aca2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

My partition is sda3

---

### Post by Tristan85 on 2010-07-22
um thanks {although i didnt use this tutorial}
i used [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

is it possible to also move other dirs like /opt {and there was another one but i forgot now {P.S. im a newbie aswell}
to another dir {if needed i read in one of the howtos that /opt is a good dir to move incase of upgrade or use of another distro because of user installed progs like adobe are installed there mine only has my google chrome ATM.
becuase i run my linux distro from a usb hdd {WD 320Gb} on my laptop i hopefully will delete my windows partitions as i dont really like windows.
just learning some new stuff and wondered if it was possiblt to do in a similar/same maner to the /home partition 

{my / and /home are on the same hdd but different partitions

thanks in advance..

---

### Post by AlexanderDGreat on 2010-08-18
Is it just me or has anyone overlooked the fact that,

On my new mounted Home Partition. Try to delete a file in that New Home Folder, and it doesn't go to the trash can, just in case you might need to Restore the file later.

So how do you solve this problem?

Pls. help.

---

### Post by AlexanderDGreat on 2010-08-18
Oh I got it. But this is gonna be ridiculous.

I have:
1 80gb /dev/sda1 - /boot /swap /
1 80gb /dev/sdb1 - /home

I introduced:
1 120gb as my NEW HOME
-to look at its /dev location type sudo fdisk -l
-in my case it's in /dev/sdc1


I just commented out this line in /etc/fstab

#/dev/sdb1       /home           ext4    defaults        0       2 

Replaced with:

/dev/sdc1       /home           ext4    defaults        0       2

Now from: [https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

Copied files from OLD home to NEW home via this command

sudo rsync -axS --exclude='/*/.gvfs' /home/. /media/home/.

And everything worked!

Bottomline

1. just copy your /home to New Hard Disk/Partition properly using rsync
2. edit your fstab

There! I don't know why there are a lot of complicated instructions out there! Or am I missing something?

---

### Post by xeddog on 2010-10-21
Question - the rsync command copies all of the files from the existing home directory to the new one.  What if I already have a home directory on another disk that I want to use.  Can I just skip the rsync step?

Here is what I am going to try to do.  I have an existing Lucid installation on a single partition 1TB disk drive (sda for now), and I have a second 300GB drive (sdb for now) in the machine that has an older karmic installation on it.  I want to take the 300GB disk, make it sda, partition it into two partitions sda1 and sda2, install maverick on sda1, and then use the home directory on the 1TB drive which should now be sdb1.  Then later on I might install something else on sda2 such as natty narwhal or Xubuntu, and still use the 1TB disk sdb1 for /home. 

Is this doable and will I run into any problems with existing config files or ??? 

Wayne

---

### Post by Marionumber1 on 2011-04-20
Hi UbuntuForums! I'm very new to these forums, and just recently set up a Windows 7 and Ubuntu 9.10 dual boot. Anyway, I followed the guide on a FAT32 drive. Now, when I try to run Nautilus, it says it can't create the folder .nautilus. I really need a fix or I can't use the file manager anymore.

EDIT: Never mind. I removed the entry from /etc/fstab and rebooted. Works now. :)

---

