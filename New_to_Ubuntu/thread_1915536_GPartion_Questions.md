---
title: "GPartion Questions"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by Naulkrinn on 2012-01-26
Alright, im new to the whole Ubuntu thing. My Windows 7 crashed a few weeks ago, and my friend told me Ubuntu is the way to go. (it was free) I did a clean install and completely wrote over all of windows. Now iam interested in dual booting. I looked up a fourm that explained that I had to partion part of my hard drive for it. I encounter 2 problems now.  I have no idea what file type XP is seen in and I am not allowed to partion my harddrive because it is mounted. Any help is much appreciated.


-Naulkrinn

---

### Post by ngubk on 2012-01-26
Not so sure. Hope you give me more details on it.
For the first problem. Xp filesystem is often FAT32 or NTFS.
For the second. Just choose unmount that partition first(G parted has that option).

---

### Post by ngubk on 2012-01-26
But, as i use 2 OS myself, i believe the safest way for beginners is to install XP/ Windows 7 first. Then use G parted in Ubuntu CD to create an unallocated partition at the end of the hard drive then install Ubuntu on it. Here is mine:

---

### Post by Naulkrinn on 2012-01-26
Thanks for the solving the first problem for me. 

For the second problem is tricky because, It tells me 

***Could not unmount /dev/sda1***
[I]
"The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.[/I]"

So then when I go to the 2nd portion which is known as in the file system (unallocated)
file size is 11.34 GiB.

For this one iam unable to unmount, im not given any options for it. If I try to resize or anything in that drive, even trying "Disk Utility" it wont do anything.

---

### Post by Naulkrinn on 2012-01-26
> **ngubk said:**
> But, as i use 2 OS myself, i believe the safest way for beginners is to install XP/ Windows 7 first. Then use G parted in Ubuntu CD to create an unallocated partition at the end of the hard drive then install Ubuntu on it. Here is mine:

Thats what I wanted to do, but for some reason Windows 7 crashed, so I had to download XP because I dont have anything for Windows 7. Now that im stuck with Ubuntu , i actually really like it but I want to play my PC games.

---

### Post by ngubk on 2012-01-26
> ***Could not unmount /dev/sda1***
[I]
"The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.[/I]"


Of course you can't. Mount point is a point(normally you can see it as a folder to access other partition(Windows partitions, for ex) ) from your linux partition ( / ). So it is not an error. The same thing will happen to me if i try to unmount my /dev/sda7

Could you give me more detail of what is inside your hard drive now? If you don't have any important data, i recommend the above solution.

---

### Post by Naulkrinn on 2012-01-26
Nothing really just some music I downloaded and that's it. Nothing important. How do I create a portion for XP?

---

### Post by ngubk on 2012-01-26
Then i suggest you follow these step:
1/ Put your Ubuntu CD/Boot CD in. Using Gparted or whatever partitioning program to delete(not format) your whole hard drive.
2/ Install Win Xp. When you do so, remember to leave at least 10gb unallocated(or create a 10gb partition) at the end to install Ubuntu later.
3/After finish XP installation, Put Ubuntu CD in. During the installation, you'll be asked where to install Ubuntu. Choose the largest free space. 
That's it. Don't worry. Since you have no data in your computer, you can't mess up. 
If anything happens, just post it here.

---

### Post by Naulkrinn on 2012-01-26
Alright cool I will keep you posted.

---

### Post by Naulkrinn on 2012-01-26
Alright I tried to delete the partition with both, GParted and Disk Utility and had no luck. I have the boot CD in drive, is there a step im missing?

---

### Post by Mark Phelps on 2012-01-27
Are you sure you're actually booting from the CD, not the hard drive?  

You can check by opening GParted, it should list two "drives" (CD and hard drive), and all the partitions on the hard drive should show as unmounted.  If there is a swap partition and it IS mounted, then select SWAPOFF and unmount it.

---

### Post by Bartender on 2012-01-27
Although this will seem like more of a hassle at first, it's not.  Using any PC that can create a bootable disc, (Any Linux PC with Braseros, etc. or a Windows PC with ImgBurn installed) go to [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") and download the LiveCD package.  Screenie attached.

Make the GParted CD.  Boot from it.  You can almost always just follow the 3 or 4 default prompts, but every once in a while you might have to start over and choose the "Safe Video" option if you don't get a usable screen.

Using this CD makes all the mount/unmount problems go away.  I never use an Ubuntu install CD for partitioning.  Always GParted CD.

BEFORE installing Windows, make a home for it.  Doing it this way is much better than installing Windows to the entire drive, then trying to shove it out of the way. 

With the GParted LiveCD, delete all partitions.  Notice that you have to click the "Apply" button to actually do anything.  You can tell GParted to do several tasks, and it will keep stacking those tasks in the "To Do' list until you Apply the task.  Don't let the tasks stack.  Tell it what you want to do, then Apply at each step.

Create a primary partition for Windows.  Half the disc, one third, whatever.  Format it as "Primary" and "ntfs".  Tell GParted LiveCD to Apply the task.  You now have a primary ntfs partition ready for Windows.  When you install Windows, it won't even see the rest of the disk because Windows ignores Linux partitions.

--------------------------------------------------------------------------

OK, we're still in GParted.  With the rest of the disk, the "simplest" thing to do is create one  primary ext4 partition. 

Then you get out of GParted, install Windows to the ntfs partition, then install Linux and make sure it installs to that primary ext4 partition.  You may have to use the manual partition option to point it to the ext4 partition.

But there's a much better alternative if you're willing.  Instead of the "simplest" thing, do this with the GParted LiveCD:

1) create one primary ext4 partition (this will be for / - about 20 to 25GB should be plenty)
2) create an extended partition out of the rest of the space
3) create a logical partition inside the extended and format that for linuxswap - make this partition a little bit bigger than your physical RAM if you want to hibernate
4) create a logical partition out of the rest of the extended partition.  This will be for /home.  

If you've got a big HDD, /home should end up being plenty big enuf for pictures, videos, etc.  For example, let's say you have a 1TB drive and 6GB of RAM.  You set aside 400GB for Windows.  600GB left.  25GB for /, 7GB for linuxswap, there'll be approx. 560 GB left for /home.

Although you create the linuxswap partition in GParted, the other partitions are not actually set as / and /home.  They're just two ext4 partitions, one primary and the other logical.

-------------------------------------------------------------------------

Then get out of GParted.

Install Windows to the ntfs partititon.  Pop out the Windows disc, restart the PC, make sure Windows works.

--------------------------------------------------------------------------

Now, pop in your Linux install CD.  When you get to the partitioning step choose manual partition (I think they call it "advanced" now) and manually tell Ubuntu to mount the primary ext4 partition as /.  Make sure to check the "format" checkbox.

When I was new to Linux, I'd see forum posts about /.  That always confused me.  Wait a minute, you mean that forward slash means the entire operating system??!!  It seems ridiculous that the OS is represented by one character, but that's the way it is!  When you're in the installer, and you click on the "Mount As" button, you'll see just that.  A forward slash.  That's the one you want.  

Then you go to the small linuxswap partition.  The Ubuntu installer will probably want to format that. I've always let it.  

Then you tell the Ubuntu installer to mount that logical ext4 partition as /home.  Let it format that, too.  Then proceed with the rest of the steps.

Does this seem like a little more work?  Well, it is, but none of it's really geeky stuff.  You're in a perfect position, what with a brand new install and no worries about wiping out photos or music.

And although it seems like more work, it avoids the "cart before the horse" aspect of what people typically do.  Setting up the ntfs partition first, then installing Windows, is a much safer and more elegant method than installing Windows to the entire drive, then trying to shove it over.

And setting up all the Linux partitions first makes it much easier to install Ubuntu when you're into the install procedure.  The installer will see the partitions, and all you have to do is tell it, "I want / here, linuxswap here, and /home over here".

You're probably aware that there are advantages to setting up a separate /home partition?

---

### Post by Naulkrinn on 2012-01-28
> **Mark Phelps said:**
> Are you sure you're actually booting from the CD, not the hard drive?  

You can check by opening GParted, it should list two "drives" (CD and hard drive), and all the partitions on the hard drive should show as unmounted.  If there is a swap partition and it IS mounted, then select SWAPOFF and unmount it.


I boot from the hard drive, let me show you how Gparted shows it to me.

---

### Post by Bartender on 2012-01-28
Hmmm, interesting, no linuxswap at all.

It would be no problem to wipe this out with a GParted LiveCD (GPLCD).  I wonder why there's 11GB of unallocated space?

Whether you use a GPLCD or a LinuxLiveCD, you have to boot from the CD, not your HDD.

---

### Post by Naulkrinn on 2012-01-29
> **Bartender said:**
> Hmmm, interesting, no linuxswap at all.

It would be no problem to wipe this out with a GParted LiveCD (GPLCD).  I wonder why there's 11GB of unallocated space?

Whether you use a GPLCD or a LinuxLiveCD, you have to boot from the CD, not your HDD.

Hey thank you for your help, later tonite im going to try and get windows 7 back on, along with linux, will post my results later. Thanks again for your help.  :)

-Naulkrinn

---

### Post by Bartender on 2012-01-29
OK, did you download and burn a GParted LiveCD?  If so, and you're gonna reinstall Windows, I'm hoping you'll try it the way I described - create the primary ntfs partition first.

Looks like you've got a - what, a 700GB HDD?  Kind of a weird size.  Anyways, unless you've got big plans for Windows, I'd only reserve 150Gb or so.

If you set up the Windows partition first using GPLCD, make sure to delete all partitions.  You want one big unallocated partition.  Apply the change to create one unalloacted partition.  Then right-click on the grayed out partition map and click "Create".  Or is it "New"?  Anyway, create a Primary partititon, formatted as ntfs, for Windows.  Make sure to create the partition at the "beginning", or left, side of the partition map.  To do that, you just grab the little arrow on the right edge of the partition and drag it to the left.  Or you can type a specific number underneath.

Once you've created the partition, make sure to Apply.  Then you can create the Linux partitions, or get out of GPLCD and install Windows to make sure it works.  Once Windows is working, you can then go back in with GPLCD and create the Linux partition(s) with the remaining space.

---

### Post by oscarivera9 on 2012-01-30
> **Naulkrinn said:**
> I boot from the hard drive, let me show you how Gparted shows it to me.

You are NOT supposed to boot from the hard drive!
You are supposed to be using the Live CD, that way NO partition is mounted.  As long as you keep using Gparted or fdisk or anything else for that matter while you boot from the hard drive, you are going to have the problem of your partition being mounted.

The solution is this:
   Put the Live CD in the computer, then restart and make sure that you can boot from the disc and NOT the hard drive.  Then open GParted and try again.  You should be able to do it exactly like Bartender told you.  If you are still experiencing problems let us know and we will try our best to help you. 
And when you finally get it fixed, also let us know.

---

### Post by Naulkrinn on 2012-02-12
Alright, sorry guys I haven't been back on to report my issue.  Well everything came out great and worked fantastically. The Gparted Live CD worked and was the main reason for everything being fixed including the hard drive file type.  Now the legal way to get Windows 7 back on my computer was simply to find and download a copy of the OS. (*Well the original OS that matches the CD key attacked somewhere on the TOWER or under your LAPTOP*.) Everything is working great and better than ever.  I think maybe having installed too many programs and then uninstalling them actually is what caused the OS to fail and some hard drive problems I was having prior to this. Thank you so much guys for your help and support. 

TCGB

Naulkrinn

---

### Post by NadirPoint on 2012-02-12
Virtualbox made dual boot and related partitioning issues go away for me.

---

### Post by Mark Phelps on 2012-02-13
> **Naulkrinn said:**
> ...  Well everything came out great and worked fantastically. 

Good to hear it's OK again.  So please use the Thread Tools as the top of the Thread to mark this as SOLVED.  thanks

---

