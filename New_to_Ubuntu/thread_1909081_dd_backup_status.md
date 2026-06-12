---
title: "dd backup status"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by chris1216 on 2012-01-14
All,

I have used the dd command to back up a lap top successfully, and am currently using it to back up a netbook to an external hard drive.  After I initiate the command the cursor drops one line and just blinks until the operation is done and then the prompt comes back.

Is there a way to show a status while the backup is taking place?

I am new to Linux and wanted a complete bit by bit copy of the drive, so if there is a simpler way to do this let me know.  I am backing up a windows 7 starter and Ubuntu 10.04 OS. I am using a System Rescue CD and after identifying the drives, and partitions I mount the external drive and run the dd command.  Below is the script I am using which was complied from tutorials here and via Google searches.

dd if=dev/sda of=/mnt/disk/netbook/jan142012.dd bs1024 

Finally, if this is the wrong place for this, would a moderator please move it and let me know where it ends up so I can check back

---

### Post by oldfred on 2012-01-14
I try to avoid using dd as it can be dangerous. Any typo and you have major issues. dd is intended for exact copy to exact copy & even copies empty space.

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

discussion of backup alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by chris1216 on 2012-01-14
Oldfred

In the second link you provided, I found the following entry from a forum member:

[I]Hi Ernest, I just wanted to mention that if you use gparted to copy the  Windows partition to another drive, you will just get a copy of the  partition without copying the MBR or any unused disk space on the  original drive. If you want to use dd to clone the entire drive, I would  recommend using "dcfldd", which is basically dd with more features; it  has the really useful feature of showing the copying progress, unlike dd  where you have no idea how much data has been copied while it runs. You  could do the following:
[/I]  	*Code:*
 	[I]sudo apt-get install dcfldd
sudo dcfldd if=/dev/[COLOR=Blue]<source drive>[/COLOR] of=/dev/[COLOR=Blue]<destination drive>[/COLOR] statusinterval=10 bs=10M conv=notrunc[/I] 
*The "statusinterval" times the "bs" or blocksize is how many bytes  dcfldd copies before it updates its progress, so in the above example  the progress will be updated for every 10M X 10 = 100 MB of data copied.  Using a blocksize of 10 MB works well, because that means dd copies 10  MB chunks at one time, rather than the default which is only 32 kB. That  means the copying goes alot faster. Also, to try and answer your  questions, I don't know of any way to set your source drive as  read-only, but if you are careful with the above command you should be  fine. In addition, you don't have to format the destination drive since  you will cloning the source drive byte-for-byte. Good luck and let us  know how it goes. :smile:*

I will try this and see how it works.  Thank you.

---

### Post by Cheesemill on 2012-01-14
From "man dd" -

```
dd if=/dev/whatever of=/dev/whatever & pid=$!
```To check progress -
```
kill -USR1 $pid; sleep 1; kill $pid
```

---

### Post by chris1216 on 2012-01-14
Cheesemill,

I am afraid I dont totally understand the "pid" part of each line

---

### Post by Cheesemill on 2012-01-14
You dont have to understand it, but basically when you call dd with 

& pid=$!

at the end it runs dd in the background and stores the process ID number as a variable.

Then the command

kill -USR1 $pid; sleep 1; kill $pid

pauses dd, prints the status, waits 1 second, then resumes dd.


To try it out just do 
```
dd if=/dev/zero of=/dev/null& pid=$!
```
to start a dd process then do:
```
kill -USR1 $pid; sleep 1; kill $pid
```
and see what happens.


The 'man dd' command is your friend :)

---

### Post by chris1216 on 2012-01-14
Thank you Cheesemill

the dd process I started earlier is still going.  I am trying to copy a 150GB hard drive, so when that finishes i will play with these commands

---

### Post by Cheesemill on 2012-01-14
No problem.

You can try it with your current;ly running dd. Open another terminal and do
```
ps ax
```
to find the PID of your runnnig dd (it's the number in the first column) and then do
```
kill -USR1 12345; sleep 1; kill 12345
```
Where 12345 is the correct PID.

---

### Post by chris1216 on 2012-01-14
I did not know I could do it through a terminal.  I started it using system rescue booted from a USB.

---

### Post by chris1216 on 2012-01-15
Oldfred and Cheesemill,

Thank you.  I now have a bit for bit copy of the netbook.  It took longer than I would like but now I know how to increase the file size dd copies at one time.

---

### Post by Paqman on 2012-01-15
> **oldfred said:**
> dd is intended for exact copy to exact copy & **even copies empty space**.


For this reason I wouldn't recommend dd for copying whole drives or partitions. Unless they're really full dd is going to be much slower than most other tools.

---

### Post by chris1216 on 2012-01-15
Paqman,

I am open to any suggestions.  As I am new to this, I will try whatever a seasoned pro suggests.

---

### Post by Paqman on 2012-01-15
Depends on exactly what you want to achieve. If you're just doing a regular backup there's an excellent tool called rsync that has a GUI called grsync. It's very fast, because it only copies the changes between the target and the destination backup. So the first backup it runs might take a while, but then subsequent backups can be very fast.

Personally for backups I just have an anacron job run rsync on the folders I want to back up to my NAS and it all happens quickly and quietly behind the scenes. Then periodically I run rsync manually to dump my NAS onto an external drive. 

Exactly what you choose will depend on how much data you want to backup, how often, what hardware you have, and how paranoid you want to be.

---

### Post by CharlesA on 2012-01-15
> **Paqman said:**
> Depends on exactly what you want to achieve. If you're just doing a regular backup there's an excellent tool called rsync that has a GUI called grsync. It's very fast, because it only copies the changes between the target and the destination backup. So the first backup it runs might take a while, but then subsequent backups can be very fast.

Personally for backups I just have an anacron job run rsync on the folders I want to back up to my NAS and it all happens quickly and quietly behind the scenes. Then periodically I run rsync manually to dump my NAS onto an external drive. 


+1. I use rsync the same way, except I have it run to backup my NAS to external media and all the machines sync to the NAS.

---

### Post by chris1216 on 2012-01-15
In this case I just wanted exact copies of my drives so as I play around with dual booting windows 7 and a version of linux I can always restore the drive just as it was with just windows and essentially just go back to my starting point.  After this point I would be interested in just backing up what has changed.

Not sure if it matters, but I am doing this with a sony vaio lap top that has no option to boot from a USB drive, and a MSI netbook that has no CD drive.  It seemed easiest to use system rescue cd in either the cd version for the lap top and on a USB drive for the netbook to be able to run the dd command.  Until this thread, and Cheesemill's advice that I could do this through a terminal command I thought this was my only option.

In the spirit of trying to tell you exactly what I am doing so I can get the help I need, I want to dual boot but found Ubuntu 11.10 ran rather sluggish on the lap top.  Perhaps I did not have some setting right?  It is a Sony Vaio with 100MB of RAM and an Intel CPU T2300 @ 1.66GHz x2.  Right now I have Lubuntu on it, in a dual boot with Lubuntu,  but I am not sure that lubuntu is for me either.  This has a 100GB hard drive.  

The Netbook is an Intel Atom N455 processor with 100MB of Ram and a 150GB hard drive.  It was running Ubuntu 10.04 and I was very happy with it.  In fact 10.04 was my first experience with Linux and what sold me on starting to use it more.  I took it off and reinstalled Windows 7 starter on it and will now be either going back to Ubuntu 10.04 or perhaps one of the "lighter" versions like Peppermint, Chrunchbang etc.

So any advice is appreciated.

---

### Post by sudodus on 2012-01-15
I suggest that you go back to Ubuntu 10.04 as your installed OS. You like it and it will be supported until April 2013.

In the meantime you can play around booting live systems from a USB flash drive. If you want, maybe you want to try persistent live systems with a casper-rw file. But basically that is not necessary in order to test different OS versions and flavours.

Lubuntu is good because it has a small footprint. But maybe you would like to add some particular software, that you use a lot. This is where the persistence comes in handy.

Xubuntu is somewhere between Ubuntu and Lubuntu 'foot-print-wise'. You might like it. Kubuntu's footprint is probably about as big as that of 'vanilla' Ubuntu, and it uses KDE instead of Unity.

Linux Mint is based on Ubuntu and uses the same repositories. There are several flavours with gnome, XFCE, LXDE desktop environments, and many people think it is easy to install and run.

Knoppix is made to run as live sessions from a CD or USB drive. It is also a nice experience.

Clonezilla is a live system for cloning or imaging partitions or whole (hard disk) drives. It is safer and much faster than dd. I use Clonezilla to make complete backup images to an external HDD.

---

### Post by chris1216 on 2012-01-15
Sudodus,

Can you recommend a tutorial on clonezilla?  I tired using it, but found it difficult to navigate the menu options.  And I think you are right about 10.04 on the netbook.  I am not familiar with persistent live systems.  Can you suggest some reading material?

---

### Post by CharlesA on 2012-01-15
> **chris1216 said:**
> Sudodus,

Can you recommend a tutorial on clonezilla?  I tired using it, but found it difficult to navigate the menu options.  And I think you are right about 10.04 on the netbook.  I am not familiar with persistent live systems.  Can you suggest some reading material?
Have you read the [manual]("http://clonezilla.org/clonezilla-live-doc.php")? The one I found had screenshots:
[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image)

---

### Post by chris1216 on 2012-01-15
Thank you CharlesA, I will go over that.

---

### Post by CharlesA on 2012-01-15
> **chris1216 said:**
> Thank you CharlesA, I will go over that.
No problem at all. I know the docs are pretty well written and help quite a bit. :)

---

### Post by sudodus on 2012-01-16
> **chris1216 said:**
> Sudodus,

Can you recommend a tutorial on clonezilla?  I tired using it, but found it difficult to navigate the menu options.  And I think you are right about 10.04 on the netbook.  I am not familiar with persistent live systems.  Can you suggest some reading material?
I'm glad CharlesA helped you after I logged out last night.

You run a live system when you boot your computer from a CD or USB drive instead of booting from your internal hard disk drive. Such a system is very good for testing new operating systems and new software, since it does not mess with your hard drive. You can mount your hard drives and read/write files, but you need not do it. And it is also good for repairing a broken system on the internal hard drive.

A persistent live system has a particular file, often called **[FONT=Courier New]casper-rw[/FONT]**, to store modifications of the live operating system or simply store data files (documents, pictures, video clips). Such a system can be used not only for testing but also for porting a personal system on a USB flash drive. It can run on (almost) any computer that you can borrow when you are travelling.

I think you can find a lot of information browsing the internet for 'persistent live'. New versions of Unetbootin can install a persistent live system from an iso image of Ubuntu. With older versions you have to make the casper-rw file yourself and edit a couple of lines in a text file to make it persistent.

---

### Post by sudodus on 2012-01-16
Hi again, chris1216

Here is a link to my own solution for a persistent live system. It is good to use Lubuntu, because its desktop environment has a small footprint, which makes it fast also from a USB drive.

[http://ubuntuforums.org/showpost.php?p=11546560&postcount=5](http://ubuntuforums.org/showpost.php?p=11546560&postcount=5)

---

### Post by Paqman on 2012-01-16
> **chris1216 said:**
> I want to dual boot but found Ubuntu 11.10 ran rather sluggish on the lap top.

Have you tried switching to Unity-2D instead of the normal 3D version? That should have it run smoothly on even very modest hardware. Works fine on my netbook.

---

### Post by chris1216 on 2012-01-16
> **sudodus said:**
> I'm glad CharlesA helped you after I logged out last night.

You run a live system when you boot your computer from a CD or USB drive instead of booting from your internal hard disk drive. Such a system is very good for testing new operating systems and new software, since it does not mess with your hard drive. You can mount your hard drives and read/write files, but you need not do it. And it is also good for repairing a broken system on the internal hard drive.

A persistent live system has a particular file, often called **[FONT=Courier New]casper-rw[/FONT]**, to store modifications of the live operating system or simply store data files (documents, pictures, video clips). Such a system can be used not only for testing but also for porting a personal system on a USB flash drive. It can run on (almost) any computer that you can borrow when you are travelling.

I think you can find a lot of information browsing the internet for 'persistent live'. New versions of Unetbootin can install a persistent live system from an iso image of Ubuntu. With older versions you have to make the casper-rw file yourself and edit a couple of lines in a text file to make it persistent.

Thank you.  I like the idea of having my OS in my pocket on a USB drive, as I do have to travel for work every now and then.  As for testing it on my system, I am sure there are many who will call me foolish, but I would prefer to have my stuff backed-up, that was why I was trying dd commands, and install Lubuntu on the lap top and just use it for a few weeks to see how I like it.

---

### Post by chris1216 on 2012-01-16
> **Paqman said:**
> Have you tried switching to Unity-2D instead of the normal 3D version? That should have it run smoothly on even very modest hardware. Works fine on my netbook.

Paqman,

Since I am new and want to make sure I am following you, would that be the DE I log into, when I log and and log back in?  Right now I am just using the Ubuntu default setting I believe.  I also just downloaded Cinnamon DE and will be trying it.  I am having trouble getting used to the icons on the side, and the way files are accessed.  This is new DE, (with the icons on the side) is what is called Unity, correct??? 

On my net book I use Ubuntu 10.04LTS, and as I mentioned earlier that was what got me hooked on Linux.  As someone who is not a "computer" guy, I jumped in and did a full install of 10.04 on the netbook and loved it.  It was noticeable smoother and snappier than the windows 7 starter that came with it.  I just wanted to try Lubuntu on the lap top because so many people have had wonderful experiences with it on limited resource systems.  Plus thanks to this forum and people like you guys its easy to get help, like I have over the past day or so.

Now, I just need to keep working on my Conky as thanks to all  of you I am now addicted to that.  lol.  But that will be another topic for another thread.

---

### Post by CharlesA on 2012-01-16
> **chris1216 said:**
> 
Since I am new and want to make sure I am following you, would that be the DE I log into, when I log and and log back in?  Right now I am just using the Ubuntu default setting I believe.  I also just downloaded Cinnamon DE and will be trying it.  I am having trouble getting used to the icons on the side, and the way files are accessed.  This is new DE, (with the icons on the side) is what is called Unity, correct??? 

That's right.

---

### Post by Paqman on 2012-01-17
Indeed. To switch from 3D to 2D Unity log out and click the little cog by your user name.

---

