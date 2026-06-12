---
title: "First time dualbooting, can't create partition"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by matanc1 on 2012-11-17
Hey guys,
So I wanted to dual boot my laptop with Ubuntu. I created a 50GB partition for Windows 8 (which I've already got installed),  a 350GB one for Data to be shared between the 2 OSs, and I left 40GB or so for ubuntu. 
I've tried creating the partition upon installation (using an image on my USB) but it says that those 40GB are unusable. What can I do? 
SS attached
Thanks :)

[http://postimage.org/image/4hk7cfbyb/full/](http://postimage.org/image/4hk7cfbyb/full/)

---

### Post by centaurusa on 2012-11-17
> **matanc1 said:**
> I've tried creating the partition upon installation (using an image on my USB) but it says that those 40GB are unusable. What can I do? 

You need to delete the 40 GB NTFS partition (presumably this is the one that you intend to use for Ubuntu) and then use the unallocated space to install Ubuntu.  There are various ways of doing this.  It is fairly easy to use manual partitioning in the installation process to delete the existing partition, and create both a root partition and a swap area in the 40 GB of available space now to be used as an extended (ext4) partition.  See:
[URL="http://linuxnorth.wordpress.com/manual-partitioning/"]
http://linuxnorth.wordpress.com/manual-partitioning/ [/URL]

This blog posting has links to other related web sites, including video tutorials.

p.s. Note that you are only allowed to have four active partitions - which is why some of your disk space shows up as unusable.

---

### Post by Vaphell on 2012-11-17
> p.s. Note that you are only allowed to have four active **primary** partitions - which is why some of your disk space shows up as unusable.

you can have more than 4 partitions, but they will need to be logical ones, living inside one of primary partitions, eg
-sda1 ntfs (win)
-sda2 ntfs (win)
-sda3 ntfs (win)
-sda4 extended
---sda5 ntfs (win)
---sda6 swap (linux)
---sda7 ext4 (linux)
---sda8 ext4 (linux)

if your data partition is empty, kill it, create a new extended partition spanning the whole free space and inside it create target partitions (data and whatever linux you want)

---

### Post by matanc1 on 2012-11-17
> **Vaphell said:**
> you can have more than 4 partitions, but they will need to be logical ones, living inside one of primary partitions, eg
-sda1 ntfs (win)
-sda2 ntfs (win)
-sda3 ntfs (win)
-sda4 extended
---sda5 ntfs (win)
---sda6 swap (linux)
---sda7 ext4 (linux)
---sda8 ext4 (linux)

if your data partition is empty, kill it, create a new extended partition spanning the whole free space and inside it create target partitions (data and whatever linux you want)

Mind explaining this a bit more into depth?
From what I'm understanding from you I can take the data partition (which is roughly 350gb or so) and the 50gb I set aside to create another partition, and I can partition that one into a data partition for Windows+Linux and another one for the ubuntu installation?

---

### Post by Vaphell on 2012-11-17
random screenshot of gparted from the internet
[img]http://www.fell.it/wp-content/uploads/2008/12/gparted.jpg[/img]
as you can see here there are 6 partitions total, but to go around of the max 4 primary partitions limitation, 3 of them are created under extended partition (see that blue frame grouping 3 green frames?).
This is the same situation you want to achieve because your total count of partitions will be 5 or 6. In your case extended partition would be made of DATA, linux ext4 and most likely linux swap. Obviously that 'envelope' should occupy as much space as possible (current DATA plus current free space)

---

### Post by audiomick on 2012-11-17
You've pretty much got it. There is this restriction, unless you are using the newer type of partition table (EFI or GPT or both. I'm still learning), that you can only have 4 primary partitions. Your screenshot shows four, which is likely to be the reason why the remaining space is coming up as unusable, as has already been posted.

What you can do, also mentioned already, is to set up one of four the allowed primary partitions as an extended partition. Inside of that you can then create a large number of extended partitions. There is a limit. I forget how many, but it is something like 64, I think.

Windows must be installed on a primary partition. Linux systems can happily be installed in an extended partition.

I assume that there is little or no data in your current sda4, and that sda3 is the win8 install. If there is data on there, move it out. Also, you are going to be doing some more partitioning, so back up anything at all that is on the computer that you can't afford to lose. Partitioning is safe, but if it does go wrong, it is possible that absolutely everything is gone from the drive.

So, having done any necessary backups, delete  sda4, assuming this is really the partition you had intended as a storage partition. This will leave you with some 400GB of unallocated space at the end of the drive.

Make all of this space  into an extended partition.

I like to put my /home on a seperate partition. Doing this means that if I have to re-install, all my config files, and any data I have in there, can simply be re-mounted at /home during the new install. I would do

a partition for / of about 15GB. Up until recently, I though 10GB to be more than enough, but the other week I had to enlarge the / on a friends computer because the 8GB or so that it had had gotten full.

a partition for /home. If your weren't going to have that shared data partition, I would say the rest of the space for that. Since you are going to be using a data partition, you can make it whatever you think useful. I read claims of people only leaving 1GB for their home. I think that is overdoing things. If you are consistent with storing your data to the data partition, however, 20GB or so should be more than ample.

a swap partition that is a little larger than your RAM. The standby function will only work properly if this is the case. The function writes the contents of RAM onto the swap space, so there needs to be room for that. If you are sure you will never need standby, the 1GB or so should be enough for normal computing.

the remainder as an ntfs partition for data sharing.

If you boot into the live environment, the "try without changing" option on the CD or USB installer, you can do the partition work with gparted. If you want the separate /home, you need to choose the manual partitioning option during the install. That is the "something else" at the point where you can choose "install beside windows" or "use the whole drive".

The only thing I don't know is if Win8 will automagically find the data partition once all this is done.

---

### Post by matanc1 on 2012-11-17
> **audiomick said:**
> You've pretty much got it. There is this restriction, unless you are using the newer type of partition table (EFI or GPT or both. I'm still learning), that you can only have 4 primary partitions. Your screenshot shows four, which is likely to be the reason why the remaining space is coming up as unusable, as has already been posted.

What you can do, also mentioned already, is to set up one of four the allowed primary partitions as an extended partition. Inside of that you can then create a large number of extended partitions. There is a limit. I forget how many, but it is something like 64, I think.

Windows must be installed on a primary partition. Linux systems can happily be installed in an extended partition.

I assume that there is little or no data in your current sda4, and that sda3 is the win8 install. If there is data on there, move it out. Also, you are going to be doing some more partitioning, so back up anything at all that is on the computer that you can't afford to lose. Partitioning is safe, but if it does go wrong, it is possible that absolutely everything is gone from the drive.

So, having done any necessary backups, delete  sda4, assuming this is really the partition you had intended as a storage partition. This will leave you with some 400GB of unallocated space at the end of the drive.

Make all of this space  into an extended partition.

I like to put my /home on a seperate partition. Doing this means that if I have to re-install, all my config files, and any data I have in there, can simply be re-mounted at /home during the new install. I would do

a partition for / of about 15GB. Up until recently, I though 10GB to be more than enough, but the other week I had to enlarge the / on a friends computer because the 8GB or so that it had had gotten full.

a partition for /home. If your weren't going to have that shared data partition, I would say the rest of the space for that. Since you are going to be using a data partition, you can make it whatever you think useful. I read claims of people only leaving 1GB for their home. I think that is overdoing things. If you are consistent with storing your data to the data partition, however, 20GB or so should be more than ample.

a swap partition that is a little larger than your RAM. The standby function will only work properly if this is the case. The function writes the contents of RAM onto the swap space, so there needs to be room for that. If you are sure you will never need standby, the 1GB or so should be enough for normal computing.

the remainder as an ntfs partition for data sharing.

If you boot into the live environment, the "try without changing" option on the CD or USB installer, you can do the partition work with gparted. If you want the separate /home, you need to choose the manual partitioning option during the install. That is the "something else" at the point where you can choose "install beside windows" or "use the whole drive".

The only thing I don't know is if Win8 will automagically find the data partition once all this is done.

Thanks for the help, so a few more questions:
1. How do I make an extended partition? I'm currently on my win8 and I don't have the option in the disc management.
2. What's the difference between logic and primary? should my saw partition be logic or primary? should I install ubuntu on a swap or primary partition?
3. if I create the data partition inside the extended partition, will windows still be able to recognize it? 

Thanks for the help! :)

---

### Post by Vaphell on 2012-11-17
> 1. How do I make an extended partition? I'm currently on my win8 and I don't have the option in the disc management.

leave the space free and make use of it during ubuntu install. Remove the 4th partition (data) so the total count of primary partitions < 4 which is necessary to have a wiggle room.

> 2. What's the difference between logic and primary?
primary = 'true' partition, up to 4
extended = primary partition that acts as a wrapper for logical partitions
logical = 'fake' partition that lives inside extended.
> 3. if I create the data partition inside the extended partition, will windows still be able to recognize it? 
yes

---

### Post by Bartender on 2012-11-17
> **audiomick said:**
> So, having done any necessary backups, delete  sda4, assuming this is really the partition you had intended as a storage partition. This will leave you with some 400GB of unallocated space at the end of the drive.

Make all of this space  into an extended partition.

+1

audiomick's post was detailed, so I wanted to highlight the most important part.

You've already got 4 primary partitions right now so you're stuck.  That's why the last 40GB is showing up as unusable.

EDIT: I prefer to create/resize/delete partitions from a GParted LiveCD rather than the Ubuntu install disc.  I think the task is more understandable from the GPLiveCD.

---

### Post by matanc1 on 2012-11-17
So I've deleted the D partition and it's now free space. I have no option to create an extended partition in the ubuntu installation options I posted above (After highlighting the free space and clicking +). 
What can I do?

---

### Post by Vaphell on 2012-11-17
check if you can create more than 1 partition. i think the installer will create extended for you automatically

---

### Post by matanc1 on 2012-11-17
If I click the "+" button and choose, for instance, 40GB out of the 400GB ext4 for the ubuntu, than it won't let me create another one. It changes back to unusable .

---

### Post by audiomick on 2012-11-17
> **matanc1 said:**
> If I click the "+" button and choose, for instance, 40GB out of the 400GB ext4 for the ubuntu, than it won't let me create another one. It changes back to unusable .
Ok, so the extended partition hasn't happened. I am assuming you mean "choose, for instance, 40GB out of the 400GB and make a partition out of it". 

I think this should be possible with the installer, but I can't remember exactly what it looks like. I prefer, like a couple of other posters, to do the partition setup in gparted from the live environment. That is the "try without changing" option on the installer CD or USB. You might want to have a look at that. I find it a bit easier to keep track of what I am doing from there.

When that is done, it is more or less just a matter of choosing the partition and assigning a mount point to it in the installer.

Having said that, I reckon when you click that + button, there must be a dropdown or something to choose what sort of partition it should be.

---

### Post by matanc1 on 2012-11-17
I've done as you said and managed to create the extended partition using the live CD feature. However, it doesn't let me choose which OS I want at boot. It just starts windows. What can I do?

---

### Post by newb85 on 2012-11-17
When you're running the installer from the CD/DVD/USB, set up all the space for your Ubuntu install and your shared data partition as an Extended partition.  Then, inside the Extended partition, create your NTFS shared data partition, your EXT4 / partition, and (if you want it on a separate partition) your EXT4 /home partition.

---

### Post by matanc1 on 2012-11-17
It still won't let me boot: 
Here is the screen shot of the partitions after I've done the extended partition:
[http://i.imgur.com/c11l6.jpg?1](http://i.imgur.com/c11l6.jpg?1)

---

### Post by audiomick on 2012-11-17
Going by what you say, that you don't see the option for Ubuntu at boot, and going by the screen shot, I think you haven't finished the installation. In the screen shot, there is the button "install now". Had you clicked on that?

---

### Post by Vaphell on 2012-11-17
you haven't created ntfs DATA yet
10G for swap is excessive. 1-2G, maybe 4G.

i must say that imho the partitioning screen of the installation process is less useful than *gparted* if you want to do stuff by hand. Try cancelling installation process and run *gparted*, either by
- ubuntu icon/WIN key, *gparted*
- opening terminal (ctrl+alt+t), *gksu gparted*

gparted is more informative visually and more powerful. You can create ntfs here, but you can't during installation, at least that's what my test in virtualbox tells me.
Then start installation again, go into manual config in partitioning step, point to swap and / and continue.

as for boot menu with systems - you have to actually install ubuntu to its partition and in the process boot menu will be created. Until you do that boot sector will still be the default one with windows specific setup.

---

### Post by Bartender on 2012-11-18
matanc -
I think there may be a possibility that we're talking right past you.  Assuming certain things that aren't clear to you yet.

I've said it a thousand times, but I really prefer to set up partitions before installing Ubuntu using [GParted LiveCD]("http://gparted.sourceforge.net/download.php").

Download the package that I highlited in the attachment.  You can use a Windows PC and ImgBurn to create a bootable CD from the .iso.

Boot from the .iso, follow the prompts.  It'll ask about keyboard, language, and video driver.  The default video driver usually works, but you *may* have to try the fail-safe version.

The GParted environment you'll boot into is similar to the one on the Ubuntu installer disc, but the extended partition work is _vastly easier to understand_ in the GPLiveCD than it is in the Ubuntu install CD.

Two hints.  Don't forget to click "Apply" after each thing you do.  Otherwise GPLCD will just keep stacking up tasks.  If you click on the "extended" partition in the GPLCD map on the top part of the page and it doesn't respond, right-click on the text *describing* the extended partition on the lower half of the page.

So, right-click on sda6.  Remove it.  Apply.

Right-click on sda5.  Remove.  Apply. 

You should now have a huge chunk of space that will be called "unallocated".  If I understand your goal correctly, right-click on that space, click "Create", or "New" (I don't remember exactly) then choose to create an "Extended" partition out of the entire space.  Apply.

If you want a space for data that will be accessible from both OS'es, create a logical partition inside that partition.  Format it as ntfs.  Whatever size you want, but I'd leave at least 50 GB for Ubuntu if it were me.  

When you're in the "Create" window it's easier to drag one edge of the partition towards the center than it is to change the numbers below.  I don't think it matters one bit whether you shove the logical data partition to the left of the extended partition or to the right.  Apply.

Let's review.  You're still booted into the GParted LiveCD.  
You've deleted sda6 and sda5, creating a big chunk of "free" or "unallocated" space.  
You've created an extended partition out of that space.  
You made a data partition, *formatted as ntfs*, inside the extended partition.  Don't worry about "logical" or "primary"; if it's inside the extended partition it's logical.  

You have NOT installed Ubuntu.  All you've done is leave some space inside the extended partition for Ubuntu.  I prefer to create partitions for /, swap, and /home while I'm using the GPLiveCD, then install manually, but at this point you may have had enough fun.

If you just want to install Ubuntu: 

Double-click on the red icon upper left hand corner of GPLiveCD to close it.  You get a choice to reboot if you want.  It'll open the tray.  You can put the Ubuntu install CD in, then click Enter.

When you get to the partitioning part of Ubuntu, where it asks whether you want to wipe the drive, install next to Windows, etc.  I think the safest thing to do is choose "Something Else".  Then aim Ubuntu at the free space inside the extended partition.

I wish I could tell you for sure, but just letting it install next to Windows might work too.  But I don't know if it would erase your data partition.

---

### Post by Vaphell on 2012-11-18
gparted is available on ubuntu livecd too.

---

### Post by Bartender on 2012-11-18
> **Vaphell said:**
> gparted is available on ubuntu livecd too.

Yeah, I know, but then you've got the hassles of unmounting swap, etc.  Have you ever tried a GParted LiveCD?  I can't imagine anyone going back to the partitioner on the install CD after they've run a stand-alone GParted disc.  

Just my two cents...

---

### Post by matanc1 on 2012-11-18
So I've got it to work and have been using Ubuntu for 24 hours. 
I don't know if this is important, but I've been getting some errors with the Libre suit for some reason. Is this common? I'll try to post a picture later on.

---

