---
title: "I don't own my own hard disk??!!"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by 2benglish on 2008-04-23
In preparation for the new release I am trying to set up my HD a partition for the OS and another for my data.

My thinking behind this is that it will make upgrades less risky to my data if it is stored separately to the system. 

First, is this an advisable thing to do?
If so, on a 160GB disk, how big should the partition for the OS be?

Today I backed up my data, shrunk the partition to 60GB and then tried to move my data to the newly made partition of 85GB.

I am now getting the message saying that I cannot write to the disk as I am not the owner.

How should I go about changing this setting? Ideally, I would like to have my documents, photos and videos and the 85GB partition and have easy access to them whenever I choose.

Thanks,

Paul

---

### Post by sdowney717 on 2008-04-23
I think if you are not copying as 'root', then you cant move system files around.
If you are in the gui, then do 
sudo nautilus

And you will be moving files as root.

What is the problem with not keeping personal data in the same partition with file system files? I always thought if the drive fails, it may as well all fail. I suppose some people might think it easier to keep home separate? Is this the idea?

---

### Post by phidia on 2008-04-23
Take a look at the thread [here]("http://ubuntuforums.org/showthread.php?t=762027&highlight=mounting+partitions") (and within that thread) for editing and adding to your /ect/fstab file.

---

### Post by aeiah on 2008-04-23
i have my data on a new partition so if ubuntu breaks, i can just reinstall it if i cant fix it. what is the format for your new partition, and how is it mounted in your fstab file?

---

### Post by martrn on 2008-04-23
> **2benglish said:**
> In preparation for the new release I am trying to set up my HD a partition for the OS and another for my data.  My thinking behind this is that it will make upgrades less risky to my data if it is stored separately to the system. First, is this an advisable thing to do?


I wouldn't personally advise anyone to do this.  Unless of course the person who wished to do this had particular reasons for doing it.

> **2benglish said:**
>  If so, on a 160GB disk, how big should the partition for the OS be?  Today I backed up my data, shrunk the partition to 60GB and then tried to move my data to the newly made partition of 85GB.

I dunno / Cool if that is what you wanted.

> **2benglish said:**
> 
I am now getting the message saying that I cannot write to the disk as I am not the owner.  How should I go about changing this setting? Ideally, I would like to have my documents, photos and videos and the 85GB partition and have easy access to them whenever I choose. Thanks, Paul 

I don't know how you got the permission of how you ended up with an error message saying you are not the owner.  Usually ownership are related to files not partitions or hard-drives.  However everthing on linux is a file included file systems you wish to mount, therefor i guess you could get error when mounting a file system.

```
chown
chown user filename
```
is a command to take control of files on your system.  Filesystems, and devices are owned by root, so therefore you should
```
sudo
```
everything rather than taking ownership of files needing root ownership.

---

### Post by phidia on 2008-04-23
> **sdowney717 said:**
> 
What is the problem with not keeping personal data in the same partition with file system files? I always thought if the drive fails, it may as well all fail. I suppose some people might think it easier to keep home separate? Is this the idea?

In the case of drive failure (severe physical breakdown) you're correct, but a lot of other things can happen that make a system unable to boot or perhaps even lose or delete the / partition. If /home is on another partition then your personal files and some settings will be saved.

---

### Post by Harpoon on 2008-04-23
OK, here's the short story.  Keeping your data (and /home) on separate partitions keeps those files safe in cases of reinstall and upgrade.  So, it does make sense.  But I agree, if the drive fails it won't matter.

Yes, you are correct - -  you don't own the drive -- yet.  You can do this:

go to /media and get the full name of what you want to change ownership of.  This could be the name you gave the partition or something more cryptic like sda2 . . . 

Once you know this, then try
sudo chown -R username:username /media/whatevername

this should change ownership (chown) recursively in all directories and files -R to your username and group.

If. for some reason. that fails create a directory like DATA as root (sudo), then change the ownership of that one directory.  You'd then put all your data there.

---

### Post by stchman on 2008-04-23
> **2benglish said:**
> In preparation for the new release I am trying to set up my HD a partition for the OS and another for my data.

My thinking behind this is that it will make upgrades less risky to my data if it is stored separately to the system. 

First, is this an advisable thing to do?
If so, on a 160GB disk, how big should the partition for the OS be?

Today I backed up my data, shrunk the partition to 60GB and then tried to move my data to the newly made partition of 85GB.

I am now getting the message saying that I cannot write to the disk as I am not the owner.

How should I go about changing this setting? Ideally, I would like to have my documents, photos and videos and the 85GB partition and have easy access to them whenever I choose.

Thanks,

Paul

By having the hdd owned by root Linux is far more secure than most OSes.  This keeps critical areas from being inadvertently modified and then the system becoming unstable.

For your / partition you should only be the owner of your home folder ~/.  I urge you to NOT make changes to any other areas.

If you need more storage space then create a separate partition e.g.

/media/yourstuff  replacing yourstuff with a better name.

and mount it in fstab using the EXT3 file system.

You can then take ownership:

```

sudo chown -R $USER:$USER /media/yourstuff
chmod -R 755 /media/yourstuff

```

This will give you read/write capability.

This will also give you the flexibility to install upgraded Ubuntu and not touch your data.  I personally don't use my home folder for my personal data.

---

### Post by Jay Car on 2008-04-23
I apologize if I am intruding on this thread of comments, it just caught my eye because I was sorting through the forum to find the answer to this very same problem.  

martrn's comment in particular made me decide to enter the discussion.  He wrote: "therefor i guess you could get error when mounting a file system."  

I can affirm that such an error is indeed possible.  The original Ubuntu install that came on my new computer developed a problem after an update (lost sound).  I reinstalled Ubuntu, and during the installation was a choice to partition the drive.  I decided to allow the partition, not realizing that it was just Ubuntu's way of being polite and keeping the old system safe.  As a result, I found that I am not able to access that 150GB partition at all.  Any attempt to move files to it, or to mount it are met with the message that it can't be done because I don't own the drive.

I haven't had time (until this morning) to really look into it, but I'm searching for ways to get rid of that old, unused installation and to permanently free up that partition. 

Mostly I just wanted to assure martrn that getting the "you don't own me" message for an entire partition is not only possible, but apparently not all that rare.

---

### Post by Jay Car on 2008-04-23
stchman, I was apparently writing my comment as you were posting yours. I just found the information I was looking for, both from your comment and from your website. Very helpful!

Thanks!!
JC

---

### Post by 2benglish on 2008-04-23
This is the reason I am trying to separate my data [http://ubuntuforums.org/showthread.php?t=732783]("http://ubuntuforums.org/showthread.php?t=732783")
I had a bit of a scare when GRUB wasn't allowing me to boot and now am looking to meep my data separate from the nuts and bolts.

To answer some questions:
The new partition is ext3.
How is it mounted in fstab? I don't know. I can't figure out how to find out.

The location of the partition is /media/disk
Does this sound right?

I get the idea of putting a directory into this partition and setting it up to be mounted automatically at boot (by adding the location to fstab). 

Also, if I use the chown command I can permamently change the ownership of a directory, and it is advisable to do this over changing the ownership of the whole file system.

Please correct me if I am misunderstanding!

So what I should do now is craete a directory in /media/disk and then add /home to that location.

However, I still cannot get access to write to /media/disk.

What should I put into the terminal to allow me to write here?

Thanks for all your help.

Paul

---

### Post by starcannon on 2008-04-24
I've always found that putting /home on another partition has been sufficient; that is after all where all the important not replaceable stuff exists, ie... email, documents, bookmarks, pictures, music, etc...

If you have already done an install and would like to resize your drive then try the gParted LiveCD [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
Do be careful, if you mess up you could lose all your files.

If you have another drive where you would like to put /home, then simply format the drive to whatever file system you like ext3 is a good solid choice (again gparted is a good tool), then copy your /home folder over to it, then either hand edit or reinstall and choose the manual partitioning option during the install wizard, its fairly intuitive, be sure to set the labels in the drop down boxes, i.e. / for root, /home for home, and don't forget to designate a /swap partition >= the amount of ram you have.

Have fun, and keep asking questions, and be sure to back up any mission critical data before messing with partitions.

---

### Post by 2benglish on 2008-04-24
I have already used GParted from the live CD to resize the partition and to make the new partition.

Now I am trying to get permission to write to the new partition.

That is where I am stuck.

---

### Post by starcannon on 2008-04-24
gksudo nautilus

R-click on the drive or folders you want to change permissions on.

L-click on Properties (at bottom of menu)

L-click on Permissions tab.

Make any changes you require.

Decide whether those changes should be recursive and click the button at bottom of Permissions tab if you decide they should.

Click Close

Close that rooted nautilus window

You should now be able to read, write, execute at what ever permission level you set for yourself

Hope that helps, keep asking, theres more than one way to skin this cat, just thought I'd give you a mostly gui option first.

---

### Post by 2benglish on 2008-04-24
gksudo nautilus - OK

R-click on the drive or folders you want to change permissions on. 

L-click on Permissions tab. - in order to do this I had to go to properties first. 

Make any changes you require. - am not allowed to do this (all the fields are in light grey and the message at the bottom tells me that I am not the owner so I cannot change these permissions)


I appreciate your help, but maybe one of the other ways to skin this cat is called for?

Paul

---

### Post by 2benglish on 2008-04-24
I'm sorry. I have been doing this wrong.

I was trying to access the partition in a browser that was not the nautilus one.

On retying as you said it wss perfect.

Thanks.

I now have to go to work. Will get on to the fstab bit later on.

---

### Post by starcannon on 2008-04-24
The possibly quick fix, with the caveat that it should be set correctly by following information from [http://catcode.com/teachmod/]("http://catcode.com/teachmod/") as well as [http://www.ss64.com/bash/chmod.html]("http://www.ss64.com/bash/chmod.html") here.
Would be to chmod 777 /location/of/your/hard/drive

Warning chmod 777 makes things wide open, meaning anyone has permission to read, write, delete, execute, look at pictures of your significant other, copy, paste, play paddy cake, you name it on the file, drive, or directory that you set to 777.

However, it can be handy for a quicky, but do read those man pages I linked, and set permissions correctly.

I gotta go to sleep now, will check back tomorrow to see how your doing, theres a lot of people here, and I am still an egg, so hang in there, your problem is really not that complex.

Me thinking out loud, you could also ```
sudo apt-get install gparted
``` then go into System-->Administration-->Partition Editor and try reformatting it using gparted from within Ubuntu (be careful you choose the correct device and or partition :) and that may fix things in a satisfactory way as well. Never had permission issues using the gparted livecd before, but theres always a first for everything.

Good Luck my friend, and hang in there, you'll get the hang of this in no time.

---

### Post by DJiNN on 2008-04-24
> **sdowney717 said:**
> I think if you are not copying as 'root', then you cant move system files around.
If you are in the gui, then do 
sudo nautilus

And you will be moving files as root.

What is the problem with not keeping personal data in the same partition with file system files? I always thought if the drive fails, it may as well all fail. I suppose some people might think it easier to keep home separate? Is this the idea?

Copying files as root is not such a good idea (Although it works well and i do it often) :) ....... one of the reasons being that when you copy/move a file as root, often the attributes will change. Then that file (From a Linux POV) becomes the property of root, and can only be changed/altered/moved etc by root again. It's like locking yourself into something unknowingly, and later wondering why you can't access that file/folder etc. 

Much better to change the ownership of the file/drive to whatever username you use most often (if it's a desktop setup) and then you should be able to do whatever you want with your data, without coming across endless restrictions.

---

