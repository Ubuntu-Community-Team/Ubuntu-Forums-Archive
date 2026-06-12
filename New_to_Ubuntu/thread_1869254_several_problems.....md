---
title: "several problems...."
date: 2011-10-25
forum: New to Ubuntu
---

### Post by kalebka55 on 2011-10-25
first problem is that I am unable to enter my GUI -
    after rebooting I get the common message of 
     
      "INSTALL PROBLEM! 
      THE CONFIGURATION DEFAULTS FOR GNOME POWER
      MANAGER HAVE NOT BEEN INSTALLED CORRECTLY. PLEASE CONTACT
      YOUR COMPUTER ADMINISTRATOR"

      The login screen does not allow me to login despite correct credentials.
      
      So I googled the problem and found many helpful recommendations.
[http://www.geekdevs.com/2010/04/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.geekdevs.com/2010/04/solved-unable-to-boot-due-to-gnome-power-manager-error/)

      It seems that my problem is that my root partition is maxed out - 100% full.

      So I 'removed' the power manager to free up some space 
      (I also conducted apt-get  autoclean, get clean, and supposedly emptied files
      from my trash folder).

     However, root is still maxed out....  So here im stuck.

To add to this, when trying to reinstall power manager -or- apt-get update, fix-misssing
     i am unable to retrieve anything from the archives....

desperate for help!!!  (assume beginner)

---

### Post by jnorthr on 2011-10-25
when your root fills up, even ubuntu cannot figure out what to do, cos there is no room to 'remember', so you need to do some housecleaning and free up some space. How to do that ? try removing any old log files as these take a lot of room. If you can start a terminal session, you might be able to change directory to /var/logs then look for any log files with an old date that you can remove. IF you have been using your system for a long time, these old log files will eat a bunch of disk space. You may even need to remove some of your applications or copy off some music or videos to another place.

If you cannot get into the terminal, you may need to reboot from a live CD and start ubuntu from it. Then while running from the live CD, all the existing partitions can be mounted and you can cleanup at your leisure.

good luck.

---

### Post by kalebka55 on 2011-10-26
Thanks for your reply.... very nice explanation!

question:  how am I able to get the dates of the log files to show in terminal?
Ive 'cd' to the log directory and 'ls' the directory to show whats inside.  hard to see whats old/new.


i have considered the live cd... but I have only been able to download the live cd which works in terminal.  this proves dfficult to me as Im not very comfortable in the shell environment.  would prefer a GUI.  

I have a feeling that my inability to access the archives is because of a lack of a network connection... I am researching to solve this... (any help appreciated)

**Thanks again jnorthr**

---

### Post by WasMeHere on 2011-10-26
> **kalebka55 said:**
> ...
Ive 'cd' to the log directory and 'ls' the directory to show whats inside.  hard to see whats old/new.
...[/B] Try ```
ls -l
```
Have fun finding out about Ubuntu :-)
Olle

---

### Post by kalebka55 on 2011-10-26
Thanks for the tip **Olle Wiklund**

I have come to the conclusion that I may move a directory in the root to a different location (i.e. /home) in order to temporarily free up some space.  this should give me some room to fix things...
any suggestions which directory will be the 'safest'?  (any considerations)

Also... reinstalling ubuntu is another option i am considering 
but... I have NB documents on /home that I cannot lose!!  will reinstalling do anything to these files? (/home a seperate partition on its own)
and.... will reinstallation only affect the / partition?

Thanks in advance

---

### Post by WasMeHere on 2011-10-26
Reinstallation would be a good option, but I strongly recommend that you backup all your personal data (documents, media files etc) before, because something can go wrong, and you lose your data.

I suggest that you think about the following questions.

- What systems do you want, and how should you make partitions?

- Is your hard disk big enough?

- What backup media do you have? Consider an external hard disk (for example a USB drive).

Have fun with Ubuntu :-)
Olle

---

### Post by kalebka55 on 2011-10-26
> **Olle Wiklund said:**
> 

I suggest that you think about the following questions.

- What systems do you want, and how should you make partitions?

- Is your hard disk big enough?

- What backup media do you have? Consider an external hard disk (for example a USB drive).



I am not entirely new to ubuntu so I have some partitions already in place.  it is just this problem that i have run into that is forcing me to consider to reinstall.  I had created partitions in the easiest recommended way.... one for root, one for home.  My hard disk is sufficient for what i use my laptop for (i.e. sufficient room)

I am quite happy with ubuntu 10.04 and would like to continue using this.  I will need to backup to my external hard disk.

WIll reinstall only affect the root? (i.e. will it only replace the files there?)
if I back up, is the 'rsync' method sufficient?

---

### Post by jnorthr on 2011-10-26
your re-install would possibly affect all your partitions, though we do have the option as to whether we completely re-install, or partially re-partition our drives. If you choose the manual mode, you can have more control over how much/little to change. Using manual mode, you can avoid reformatting the partition holding your /home directory. I do this a lot as i'm always upgrading ubuntu for each release, and so i never blitz my /home partition. I've also made another partition for /usr/local where i store my own programs, software things that are more 'programmy' than documents,music,etc.

But i get the feeling that you are happy with your system as is, and just need to get over this one issue. If we can free up enough space, you might be able to avoid a re-install as that is a rather big job. 

Do you really want to do a full re-install or just fix the current issue ?

---

### Post by kalebka55 on 2011-10-26
I have a root (/) that is 100% full and I recently had a package disruption.  This disruption caused a login problem and I am now confined to operating solely in terminal.

To free up some space (and try regain access to my GUI), I tried to move ('mv' ) my /var directory to the /home directory (since /home is in a separate partition) - this managed to to free up some space.

now i am unable to install packages since it needs access to the contents of the /var.  How am I to undo what I have done?  I tried to move it back but unsuccessful.:confused:

---

### Post by jnorthr on 2011-10-26
going on the assumption that you just want to fix your system, open a terminal console session. Next :
cd /var/log
ls -al

you should see something like this: 

[FONT="Courier New"][COLOR="Red"]RedApple:jim /var/log $ ls -al
total 6560
drwxr-xr-x  45 root   wheel    1530 Oct 25 12:30 .
drwxr-xr-x  26 root   wheel     884 Oct  9  2010 ..
-rw-r--r--@  1 root   wheel      12 Oct  9  2010 CDIS.custom
drwxr-x---  37 root   admin    1258 Oct 26 12:15 DiagnosticMessages
-rw-r--r--   1 root   wheel       0 Oct  9  2010 alf.log
drwxr-xr-x   5 root   wheel     170 Oct 25 12:24 apache2
drwxr-xr-x  26 root   wheel     884 Oct 26 12:15 asl
drwxr-xr-x   5 root   wheel     170 Jul 29 13:27 cups
-rw-r--r--   1 root   wheel  589484 Oct 26 12:15 daily.out
-rw-r--r--   1 root   wheel    2416 Nov 28  2010 dpd.log
drwxr-xr-x   2 root   wheel      68 May 18  2009 fax
-rw-r--r--   1 root   wheel   65503 Oct 26 16:22 fsck_hfs.log
-rw-r--r--   1 root   wheel    3798 Oct 13 21:51 hdiejectd.log
-rw-r-----   1 root   admin    6568 Oct 26 16:23 install.log
-rw-r-----   1 root   admin   31074 Oct 25 12:30 install.log.0.bz2
-rw-r-----   1 root   admin   52817 Jul  1 10:02 install.log.1.bz2
-rw-r-----   1 root   admin       0 Jun 23  2009 ipfw.log
[/COLOR][/FONT]

You can see in the above list of log files which ones have old dates. 

Also note those log files ending with .bz2  as these are log files that are compressed as zip files to reduce storage space. These would be good candidates for removal. So my install.log.1.bz2 file is old and can be blitzed using the rm command. I often need to become administrator using the sudo command so if i am in /var/log  i can issue the command
sudo rm install.log.1.bz2

and supply password when asked. Do this with several of the big log files and you may have the space you need. Dont worry much if you erase a log file as most software will recreate log files as they need to.

---

### Post by sanderd17 on 2011-10-26
you're making a mess of it. Please shut down your computer, and proceed working from a live CD.

First thing to do (after you booted a live CD) is check if a new /var has been created. If so, you will probably have to merge the two.

If not, you can try to move /var back, but you will have serious problems with the user rights. A lot of files in /var need special user rights, and the mv command just overwrites the user rights.

I think the most simple thing to do will be to reinstall ubuntu (and use a bigger root partition).

---

### Post by audiomick on 2011-10-26
Seems like you didn't really pay attention to the advice given to you here
[http://ubuntuforums.org/showthread.php?t=1869254](http://ubuntuforums.org/showthread.php?t=1869254)

Although it is no doubt possible to repair what has been done, I would personally, at this point, consider a re-install. In the process of doing this, you could then re-size your partitions to give / a bit more space, i.e. shrink your /home a bit and expand your /. Then do a re-install and use the existing /home. You have to create users with exactly the same user names and in exactly the same order of creation to have the /home just slot in, but otherwise it is a simple process.

What size are your partitions now, anyway?

---

### Post by kalebka55 on 2011-10-26
> **jnorthr said:**
> 
  Do this with several of the big log files and you may have the space you need. Dont worry much if you erase a log file as most software will recreate log files as they need to.


Thanks **jnorthr**

You were quite right in that I would rather fix this problem....

It seems that I only have .gz and .log files in the /var/log directory (some with strange irrelevant names like 'popularity-contest.gz' -or- 'jockey.log.gz' )    
these will obviously be targeted first.  

having been at this all day..... I came across a blog that suggested I try move ('mv') the /var directory to the /home to free up some space...... this worked but the system needs my /var to install packages.... I now cannot install.....

when trying to 'mv' it back to the original location i get the message:

inter-device move failed: '/home/var' to '../var' ; unable to remove target: Is a directory

<I know this was a bad move and Im regretting it! >

---

### Post by nothingspecial on 2011-10-26
One thread per issue please.

As you can see, it only confuses things.

Merged.

---

### Post by kalebka55 on 2011-10-26
c

---

### Post by audiomick on 2011-10-26
OK, have you a way of backing up the stuff you need to keep at all costs? If you have an external drive or something, you can also do this whilst booted to a live CD or USB.

Don't panic about the re-install. I have re-installed whilst retaining my /home numerous times without a problem.

While we are on the subject of the live CD, this is also a very comfortable way to re-size your partitions using Gparted.

Do you have one handy?

---

### Post by kalebka55 on 2011-10-26
Thanks Michael.

Yes, I have an external hard drive with plenty of room (+- 100 gb)

I dont have a live CD.  I have downloaded the 'rescue remix' version which only runs in the terminal.  I have been unsuccessful in making a CD of a proper live CD.  am looking for one now

---

### Post by cariboo on 2011-10-26
Next time you run out of room in your / partition, have a look in /var/cache/apt/archives, this is where all the packages you have installed and updated are archived. I'm running a fairly new (approx 1 week) Precise Pangolin install, and so far I have accumulated about 14MiB of log files, with twice daily updates /var/cache/apt/achives contains 986Mib, by cleaning out that directory, I gain almost 1GiB of free space.

---

### Post by kalebka55 on 2011-10-26
> **cariboo907 said:**
> Next time you run out of room in your / partition, have a look in /var/cache/apt/archives, this is where all the packages you have installed and updated are archived. I'm running a fairly new (approx 1 week) Precise Pangolin install, and so far I have accumulated about 14MiB of log files, with twice daily updates /var/cache/apt/achives contains 986Mib, by cleaning out that directory, I gain almost 1GiB of free space.

Thanks **cariboo907**, will keep that in mind... (but this will never happen again :))

Is this the directory that 'apt-get clean' targets?

---

### Post by audiomick on 2011-10-26
> **kalebka55 said:**
> Thanks Michael.
... a proper live CD.  am looking for one now

Ok. I'll try and keep an eye on the thread. Otherwise, I am sure someone else will be able to help you further. 

@cariboo907: thanks for the tip. I've often wondered where that sort of things ends up. ;)

---

### Post by kalebka55 on 2011-10-26
Ok, so Ive managed to download the live cd.  I have reached the install menu with 'a try' option and an 'install' option...

---

### Post by kalebka55 on 2011-10-26
I managed to obtain the live Cd.  I am at the install menu with a 'try' option and an 'install option

---

### Post by audiomick on 2011-10-26
go into the "try" option. That is the "live" environment.

---

### Post by kalebka55 on 2011-10-26
done...start up tune...and desktop loaded...just trying to get a network connection\

---

### Post by audiomick on 2011-10-26
Ok. Even if the network connection doesn't work, it's not so tragic for now. Just out of interest, which version is the live CD?

The next step is to connect up your external drive and establish that you can see it, so that you can copy stuff to it. You don't need to move stuff off your drive, just make a copy. We are assuming that your /home is going to survive intact and be re-used. The copies are just to be sure. ;)

---

### Post by kalebka55 on 2011-10-26
> **audiomick said:**
> Ok.  which version is the live CD?

The next step is to connect up your external drive and establish that you can see it, so that you can copy stuff to it. You don't need to move stuff off your drive, just make a copy. We are assuming that your /home is going to survive intact and be re-used. The copies are just to be sure. ;)

10.04 LTS (long term support)

drive connected and visible...... so I  copy the /home  (and root?) and paste into external drive.   Ive checked out the damage ive done to the root and /home (i.e. /var move) and all is there as done.   There is a folder /var in root directory but lacking the contets that should be there.  the is also a /home/var directory.

---

### Post by audiomick on 2011-10-26
If you feel like playing, you could try copying the /var stuff back. I would do this, because I am very GUI orientated, using the file manager in the live environment. I think it would be neccessary to start an instance using
```
gksu nautilus
```
because I think at least some of the files in /var belong to root. This is what would stop me from trying this. I have no idea what the permissions in that folder should be, and I could imagine it would give you ongoing grief if they are wrong.

Before this, copy your files. You can use cut and paste. I don't think you need to copy anything out of /. Either it will be overwritten and all new through a fresh install, or you will get it back by restoring your /var.

Do the backups, whichever way you go. You will want to re-size your /home and /, and you should alway backup before you mess around with your partitions.

I'm in the middle of cooking dinner now. I'll look back in later.

---

### Post by kalebka55 on 2011-10-26
> **audiomick said:**
> 


I'm in the middle of cooking dinner now. I'll look back in later.


No probs Michael. Thanks a million!  Il try all you have suggested.  see you later and ENJOY

---

### Post by audiomick on 2011-10-26
So, when you have got all your stuff copied across, go to system> administration> Gparted

That is the partitioning program. Since you have been doing stuff on your drive, the partitions on your drive are possibly mounted. You can't work on a partition that is mounted, you they will have to be un-mounted. I can't remember if this works with a right click in gparted, but I think so. Otherwise, try in the file manager, right click unmount, or, if the worst comes to the worst, just re-start the live CD.

If you haven't already, you might like to read this
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by kalebka55 on 2011-10-26
With respect to /var  ....I am unable to copy it back into its original location. seems like the permissions are doing their job

Copying /home is also causing me troubles....it denies me to copy several documents and files... any reason why they could be doing this?

---

### Post by kalebka55 on 2011-10-26
> **audiomick said:**
> So, when you have got all your stuff copied across, go to system> administration> Gparted

That is the partitioning program. Since you have been doing stuff on your drive, the partitions on your drive are possibly mounted. You can't work on a partition that is mounted, you they will have to be un-mounted. I can't remember if this works with a right click in gparted, but I think so. Otherwise, try in the file manager, right click unmount, or, if the worst comes to the worst, just re-start the live CD.

If you haven't already, you might like to read this
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Thanks... I am familiar with gparted but I havent used it before.  thanks for the literature.

---

### Post by audiomick on 2011-10-26
Permissions again, no doubt. What is it not copying?

You can usually "force" it with an instance of Nautilus with super user privileges.

---

### Post by kalebka55 on 2011-10-26
> **audiomick said:**
>  What is it not copying?

You can usually "force" it with an instance of Nautilus with super user privileges.

OK, So I have successfully copied everything in /home to my external disk.  (finally moving forward).....  Including the /var directory that I had moved.  Is it worth to copy my / as well to maintain my original settings etc?

Will I have to re-setup my email 'retriever' when I reinstall....?

---

