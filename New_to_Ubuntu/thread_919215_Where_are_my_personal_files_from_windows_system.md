---
title: "Where are my personal files from windows system?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by saif2004 on 2008-09-13
Hi,

I was having problem with my windows xp so I downloaded ubuntu on a cd using another computer and then installed it on my troubled pc.  Everything ran very nicely and I was really impressed but now I can't find any of my pictures or other personal files that I had in windows xp.  Does Ubuntu delete all the files that I had?   Is there any way to find the files?  It will be really terrible if I can't find the files again.  Please help.

---

### Post by ChanServ on 2008-09-13
it depends on if you formatted the whole drive when you installed ubuntu

---

### Post by saif2004 on 2008-09-13
I just put the installation cd and followed the commands.. It never asked me about formatting the drive..  I had one option of trying ubuntu before installing it but as I had issues with xp so I chose "install ubuntu".. Unless that option automatically formats the drive it has not been formatted..

---

### Post by akiratheoni on 2008-09-13
Go to Applications -> Accessories -> Terminal

And post the output of:

```
sudo fdisk -l
```

It will prompt you for your password so type it in. When you type your password, nothing will appear (no ***** or anything) but type it in anyway.

---

### Post by saif2004 on 2008-09-13
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

---

### Post by akiratheoni on 2008-09-13
> **saif2004 said:**
> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

It looks like Ubuntu erased Windows at the installation... if Windows was there, then there would be an NTFS partition but there isn't one.

Sorry. That's why you are advised to back up everything before installing. Linux LiveCDs can load and mount Windows partitions and if XP failed to boot you could have still copied your personal files.

---

### Post by saif2004 on 2008-09-13
Actually there should be more warning in the installation process regarding this..  There was absolutley no warning from the download page through the installation where it says that I can lose all my files..  I would be really hesitant to install ubuntu if that was the case.. as I was worried about my files..  I really feel like a fool now.
I would just suggest the ubuntu guys to put these warnings during the installation process or the download pages.. I would never suggest ubuntu to anyone without this warning..

---

### Post by gali98 on 2008-09-13
You can now go through the process of trying to recover files.
One is  Photorec.
It trys to recover pictures, documents and videos.

To install it, go to the terminal (like you already did)
and run this command.

sudo apt-get install testdisk

then make the terminal fullscreen and run

sudo photorec

go through the instructions.

When selecting the partition to recover, select the whole thing.

If you need more help post back here.



***** it is imperative that you do not do anything on the system while it tries to recover****

For help on this program (I've never really used it before)
use the link in the post below this one (Thanks starcannon!!)

Kory

---

### Post by starcannon on 2008-09-13
Nevermind gali98 pretty much beat me to it, feel free to go to testdisk's website and poke around though, I left the link in my post.

> 
Actually there should be more warning in the installation process regarding this.. There was absolutley no warning from the download page through the installation where it says that I can lose all my files.. I would be really hesitant to install ubuntu if that was the case.. as I was worried about my files.. I really feel like a fool now.
I would just suggest the ubuntu guys to put these warnings during the installation process or the download pages.. I would never suggest ubuntu to anyone without this warning..
One should always back up ALL important data before ever doing something as major as installing an operating system, regardless of what operating system one may be installing. Further one should always read all dialog boxes when installing an operating system, or any software, the dialog boxes contain valuable information. First rule to my computer sanity is in my signature.

Don't Panic,

You can get many of your lost files back using recovery software that is free and available for Ubuntu.

You can find it here:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

There are guides on that website as well, however, if you read the dialog boxes(you should ALWAYS read dialog boxes), its actually fairly intuitive.

GL

---

### Post by houbysoft.xf.cz on 2008-09-13
AFAIK, there is a warning on the last screen you see before installing. There is a complete overview of which actions will be taken during installation, and there is info about formating your drive(s) too... And when you install Ubuntu, it asks you if you want to use all your drive (it formats it obviously) etc...

---

### Post by ThrobbingBrain66 on 2008-09-13
I believe there's a warning in the partitioning section and there's definitely one on the summary page right before you click 'install'.

Also, if Ubuntu detects another operating system, it will always default to shrinking that partition and installing Ubuntu on a seperate partition.  This has always been my experience anyway.

I suggest you be more careful in the future, read *everything* on the screen and always have a backup handy.  I've never used a linux file recovery tool, but good luck saif2004.

---

### Post by gali98 on 2008-09-13
Now just seeing your post....

First of all, where did you download it from?

Second, when installing another operating system, or doing any major changes to your computer, you should always research what you are doing first.
There are many resoures on the net on how to install ubuntu that include telling you to back up you windows files. Also when installing, it gives you the option of resizing your windows partion, or installing the whole disk.

I'm not getting on to you or anything like that. I understand that you probably didn't quite understand everything you were doing, and that is normal. It happens to many people, especially new users.

You just should have researched a little more before you made the move...

Kory

try the instructions above to see if we can help you recover those files.

It is important that you do not do anything other than try to recover right now, so the files are recoverable.

---

### Post by OutOfReach on 2008-09-13
> 
Actually there should be more warning in the installation process regarding this.. There was absolutley no warning from the download page through the installation where it says that I can lose all my files.. I would be really hesitant to install ubuntu if that was the case.. as I was worried about my files.. I really feel like a fool now.
I would just suggest the ubuntu guys to put these warnings during the installation process or the download pages.. I would never suggest ubuntu to anyone without this warning..

Sorry that you lost all your files. But when you select what partition to use I think there is a warning that goes something like: (Erase entire drive) or something like that.

On a second note: you should read wiki's before trying anything big to your computer, and on the wiki it clearly says to backup all your data before trying to install Ubuntu.
Installing Linux on your computer is not like installing a normal program on Windows. It's a whole process. If done right, it will be a good experience, if done with carelessness the results will be disappointing.

---

### Post by mdsmedia on 2008-09-13
> **saif2004 said:**
> Actually there should be more warning in the installation process regarding this..  There was absolutley no warning from the download page through the installation where it says that I can lose all my files..  I would be really hesitant to install ubuntu if that was the case.. as I was worried about my files..  I really feel like a fool now.
I would just suggest the ubuntu guys to put these warnings during the installation process or the download pages.. I would never suggest ubuntu to anyone without this warning..It is disappointing that you appear to have lost your files, but if you install a new operating system, think about it, wouldn't it seem reasonable to backup your files before doing so? If you installed Windows it would wipe your system without warning. Ubuntu gives the option to install in free space. Windows gives no such option, so don't blame Ubuntu because you didn't take reasonable precautions.

---

### Post by mikewhatever on 2008-09-13
I am truly sorry for your loss, however, the partitions on the hdd clearly indicate that you've chosen to use the entire disk for the installation.
Anyway, it may still be possible to recover some of the date. If interested, read this [http://ubuntuforums.org/showthread.php?t=918050](http://ubuntuforums.org/showthread.php?t=918050).

---

### Post by saif2004 on 2008-09-13
Yeah I know I was not really thinking rationally.  I will try the insturctions and let you guys know what happens. I am really glad that I stopped by the forum because it really helped.

---

### Post by akiratheoni on 2008-09-13
> **ThrobbingBrain66 said:**
> Also, if Ubuntu detects another operating system, it will always default to shrinking that partition and installing Ubuntu on a seperate partition.  This has always been my experience anyway.


That's what I thought too... it should have detected Windows, but I guess not.

---

### Post by saif2004 on 2008-09-13
@gali98 
I followed your steps and it recovered tons of files and created recup_dirs but I can't access any of the recup-dirs. It says I don't have permission to view the folders.  Is there any remedy for that?  
I really appreciate you and everyone else's help here.

---

### Post by starcannon on 2008-09-13
You will need to change the permissions on those files.

The easiest method is probably to run a command:

```
sudo chmod -R 777 ~/path/to/file
```

Or you could:

```
gksu nautilus
```

browse to the directory containing the sub-directories, Rclick the directory, click on permissions, set them to allow your_user_name to the access options you prefer, then click "Apply Permissions to Enclosed Folders" and close out the Nautilus browser. 

Either way you should end up being able to view, delete, modify, and execute anything in there.

GL

---

### Post by saif2004 on 2008-09-13
Thanks starcannon...
Now there are so many folders and so many .txt files that I can't find the pictures I was looking for.  Is there a quick way to find the .jpg files? What would be the command?

---

### Post by gali98 on 2008-09-13
ahhh... okay starcannon beat me too it this time..
to search for jpg files you can do
gksu nautilus and there is a search buttton at the top, or 

do 

ls -lR |grep .jpg

in the terminal and that will also work...

Kory

---

### Post by starcannon on 2008-09-14
> **saif2004 said:**
> Thanks starcannon...
Now there are so many folders and so many .txt files that I can't find the pictures I was looking for.  Is there a quick way to find the .jpg files? What would be the command?

The fastest way to get the jpg's or other extensions with a slight modification is to use this command:

```
cp -r ~/path/to/backup/files/*.jpg ~/path/to/preferred/location
```

cp copies, the -r flags cp to copy recursively down into the folders and subfolders, the * is a wildcard, and in this case says "all files with the extension of .jpg should be copied", the tilde(~) is a shortcut to /home/your_user_name. 

Now lets say after you copy all the .jpg's you realize, oh man! some of my pictures where .jpeg's just rerun the command chane the .jpg to .jpeg, run again perhaps as .png or other formats that you used, .doc, .zip, .what-ever. There may be a way to do this in one command but I don't know how yet.

GL and have fun.

---

