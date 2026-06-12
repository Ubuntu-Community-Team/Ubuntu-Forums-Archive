---
title: "Complete Newbie: How do I install Ubuntu on Win 8 for Dual boot?"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by mrgoodfox on 2011-10-11
Complete Newbie: How do I install Ubuntu on Win 8 for Dual boot?

Or is it better (how about more secure/private) to just use VMWare and create an image?

Thanks

---

### Post by mikewhatever on 2011-10-11
Ubuntu is an operating system (sort of like Windows itself) and not a Windows program, which means you can't install it on Windows.
The download page at [http://ubuntu.com](http://ubuntu.com) has step by step instruction on setting up a dual boot.

---

### Post by lincoln32 on 2011-10-11
I might recommend finding a local Ubuntu loco Team or Linux User Group (LUG)
while it is very easy to setup there a lot tricks/tips the will make it faster/better/pain free first Linux install and by the second you might be a expert;)

---

### Post by Mark Phelps on 2011-10-11
Windows 8 is still in Alpha stage, and unlike with Ubuntu where prerelease stages are only weeks apart, with Windows, it could easily be MONTHS before Win8 reaches Beta.

If you have any questions on it, you should post those in the Win8 forum -- eightforums.com.

---

### Post by Mark Phelps on 2011-10-11
Windows 8 is still in Alpha stage, and unlike with Ubuntu where prerelease stages are only weeks apart, with Windows, it could easily be MONTHS before Win8 reaches Beta.

If you have any questions on it, you should post those in the Win8 forum -- eightforums.com.

---

### Post by 11jmb on 2011-10-11
Personally, I think that computing power has advanced to the point where VMs give you the best of both worlds for the average user. If you are doing some big-time number crunching or you have an older, slower computer with less memory, running it natively as a dual boot would be probably be better. 

Also, you have to worry about stability with an alpha release. A win8 crash would probably lead to a loss of your work on the VM, so if you are just monkeying around go for the VM, if you are doing something critical, dual boot.

---

### Post by 11jmb on 2011-10-11
to answer your first question:

If you go the VM route, its pretty easy, just install virtualbox or vmware, download the ubuntu .iso, and create the vm.


If you want to dual boot, you will have to free up some space on your hd for a linux partition. 
I recommend doing it through Windows to make sure that nothing is lost during reformatting (hopefully the below process will work for windows 8 as well)

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

then you need to download an Ubuntu .iso and burn it to a disk. restart your computer and boot to that disk. the ubuntu installer should take you through the rest.


report back if you need help!

---

### Post by mrgoodfox on 2011-10-12
Thank you guys.

So if I want to do a dual boot (which is what I'm probably going to do after reading this thread), do I have to format my hard drive in order to divide it in partitions?

I have plenty of free space but everything (windows) is on one drive

---

### Post by mastablasta on 2011-10-12
> **mrgoodfox said:**
>  
So if I want to do a dual boot (which is what I'm probably going to do after reading this thread), do I have to format my hard drive in order to divide it in partitions?

 
no but it would be a good idead to defragment it (about 2 times, second time it iwll go much faster). Then use windows diskmanager to shrink windows partition and leave the new space as empty space. then start ubuntu install.
 
if you just want to try it out you could try using wubi which install is as dual boot but it install it inside windows in a large file and can later be removed as any other windows programme.
 
However if you are really using Windows8 this might not be the best idea as i am sure windows 8 is not stable yet.
 
also be sure to run it in live boot ("try it option") first to see if all components behave propperly and that it all works well.

---

### Post by mrgoodfox on 2011-10-12
I'll definitely do the dual boot. 

Will i just be able to use Diskmanager to divide the hard drive up into two partitions while windows is running? (interesting)

---

### Post by Lisiano on 2011-10-12
Yes you can, but for the sake of time and easiness, just shrink the disk and let the Ubuntu Installer handle all the rest, just pick Install into Unallocated/Free space.

---

### Post by mrgoodfox on 2011-10-12
Question, is it better to take an image of my hard drive, format my hard drive, partition it, and mount Win8 on one drive and use the other for Ubuntu?

Or am i thinking too much about this?

Also, I have a 500GB hard drive now. It's allowing me to shrink the hard drive a little over 200GB. How much is reasonable to shrink the drive by?

---

### Post by oldfred on 2011-10-12
If you have more than one drive I always suggest each operating system on each drive. Keep Windows on sda where it still thinks it is the first and only operating system. Then on the second drive install Ubuntu. But be sure to install the grub2 boot loader to sdb.

Are you booting BIOS or UEFI? Do you want gpt partitions on the Ubuntu drive if it will never have Windows.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

I also suggest a shared NTFS data partition and only mount a Windows system partition as read only if you mount it at all.

Windows NTFS partitions need about 30% free space to maintain performance. At 20% free it slows down (why many users complain) and at 10% check disk will take days if the partition is of any size at all..

---

### Post by 11jmb on 2011-10-12
I strongly recommend using the Windows shrink drive tool to free up space for your dual boot. then use whatever third party formatter to reformat

---

### Post by mrgoodfox on 2011-10-12
I only have one hard drive.

---

### Post by oldfred on 2011-10-12
You have to decide how to divide up drive. I still suggest smaller system partitions with shared NTFS data partition for most data. If most data is in a shared data partition, you may not need a separate partition for /home and just make / (root)  a little larger. Most of /home is made up of your data with less than half a gigabyte of user configuration files. Some data though like Filefox profile is in a hidden folder. But it should be in the shared so you can use the same Firefox info in both systems.

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by mrgoodfox on 2011-10-13
Ok. I installed Ubuntu (or something). I have a feeling I screwed up though.

When the dual boot options list comes up I have a bunch of options one of them being the Linux one. 

When I choose that, I am redirected to a dos based environment (nothing like the Ubuntu that I had seen on other people's computers before). 

I installed the Ubuntu server. Did i screw up?

---

### Post by oldfred on 2011-10-13
Server is command line only. 

But you can install a desktop environment. Most server users that are not totally comfortable with command line install one of the lightweight gui's so they do not overload server.

If you want (not sure about the newest Unity):

The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)

sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
sudo service gdm start

---

### Post by mrgoodfox on 2011-10-13
So (excuse my ignorance) do I have Ubuntu-base right now? 

and perhaps I need to install Ubuntu desktop?
Thanks

---

### Post by oldfred on 2011-10-13
I think all Ubuntu installs have the same base and then server adds the programs most suited for a server, desktop then has a gui and the programs for a desktop. Each can install all the other programs if you want.

---

### Post by mrgoodfox on 2011-10-13
I see. So how do i install the desktop now? Put the Ubuntu boot CD in again?

---

### Post by oldfred on 2011-10-13
Server install does not have a desktop. But this will install a lot of support files.

sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart

---

### Post by mrgoodfox on 2011-10-15
Thank you everyone for all the help.

I'm a member of a lot of forums and this is certainly the most helpful so far. 

Now I have Ubuntu dual boot with Windows 8 and Ubuntu desktop installed.

What is my next step in the learning curve?

---

### Post by Lisiano on 2011-10-15
Next step? Ugh. Hard one to answer. Probably getting used to Unity (If you went Gnome) or to whatever DE you picked. Then becoming a bit nerdish like us and remembering every Terminal command by heart.
In reality, just try to get used to the desktop you picked, leave the thinking about the terminal stuff to us for a while, then try to gradually start fixing or tweaking stuff.

---

### Post by bob53124 on 2011-10-15
dual boot using WUBI (when on windows 8 put the disc in and load up wubi via autorun)

---

### Post by jfbooth on 2011-10-15
> **mrgoodfox said:**
> Complete Newbie: How do I install Ubuntu on Win 8 for Dual boot?

Or is it better (how about more secure/private) to just use VMWare and create an image?

Thanks

Sounds like you have succeeded .. but thought I would mention this:

[http://www.zdnet.com/blog/microsoft/will-windows-8-block-users-from-dual-booting-linux-microsoft-wont-say/10772](http://www.zdnet.com/blog/microsoft/will-windows-8-block-users-from-dual-booting-linux-microsoft-wont-say/10772)

---

### Post by mrgoodfox on 2011-10-15
> **jfbooth said:**
> Sounds like you have succeeded .. but thought I would mention this:

[http://www.zdnet.com/blog/microsoft/will-windows-8-block-users-from-dual-booting-linux-microsoft-wont-say/10772](http://www.zdnet.com/blog/microsoft/will-windows-8-block-users-from-dual-booting-linux-microsoft-wont-say/10772)

Interesting article. I have dual boot with Win 8 and Ubuntu running now so I guess so far they havent released an update to do anything to stop it

---

### Post by mrgoodfox on 2011-10-15
> **Lisiano said:**
> Next step? Ugh. Hard one to answer. Probably getting used to Unity (If you went Gnome) or to whatever DE you picked. Then becoming a bit nerdish like us and remembering every Terminal command by heart.
In reality, just try to get used to the desktop you picked, leave the thinking about the terminal stuff to us for a while, then try to gradually start fixing or tweaking stuff.

Where is a good place (i never learn code from books) to start learning the commands?

---

### Post by oldfred on 2011-10-15
Just use it. Then if there is something you may want to change hang out in the forums. Lots of people doing different things.

Ubuntu Documentation:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[https://help.ubuntu.com/11.04/index.html](https://help.ubuntu.com/11.04/index.html)

Beginners guide:
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485) (Newbie 101) 
[http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338) (Newbie Terminal Intro)
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885) (Terminal for Beginners) 
[http://www.solutionbeacon.com/CommonLinuxCommandsPocketGuide07.pdf](http://www.solutionbeacon.com/CommonLinuxCommandsPocketGuide07.pdf)

---

