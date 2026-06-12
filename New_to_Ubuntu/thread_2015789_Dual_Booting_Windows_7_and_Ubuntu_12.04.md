---
title: "Dual Booting Windows 7 and Ubuntu 12.04"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by nickelbox on 2012-07-03
So I currently am running Windows 7 and would like to be able to have the option of selecting either Windows 7 or Ubuntu 12.04 when I boot up my PC. My hard drive came partitioned with C: as my "OS" drive and also D: as "data" which I have nothing on (240 GB wasted). I would like to take my D: drive and use that for the Ubuntu 12.04 install. I have looked at WUBI but I understand that it is generally not advisable to use long term so I am settling on going with two separate physical partitions, each dedicated to an OS. 

There is some confusion on my part as to the best way to accomplish this. I know WUBI is quick and easy but it installs inside of Windows and is virtual. Not what I want. Can someone give me some simple instructions on how to proceed?

---

### Post by anewguy on 2012-07-03
Do the normal install from the LiveCD, with the following exceptions:

(1) Select the manual mode for defining partitions so that you can put the partitions on your 2nd drive

(2) When you are done selecting partitions there is another box on the screen that says where the boot loader will install.  By default, it will install to the same device as your ubuntu install.  Instead, point this to your main windows drive.  In this way the MBR will point to grub on your ubuntu drive and have the typical menu entries for ubuntu plus and entry for the windows loader.

---

### Post by nickelbox on 2012-07-03
> **anewguy said:**
> 
Select the manual mode for defining partitions so that you can put the partitions on your 2nd drive


Technically, I only have 1 hard drive with 2 partitions. If I understand you correctly, it will take my D: drive and then partition that further (as Ubuntu uses two separate partitions)?

---

### Post by chief grand teriki on 2012-07-03
boot from live cd, then select the unused partition to install ubuntu on!

---

### Post by wilee-nilee on 2012-07-03
The confusion here is calling D a drive when it is a partition and called something different in linux, such as a sda1 or sda2 etc.

Boot the live ubuntu cd open gparted take a screenshot of it and post it using the paperclip in the reply panel. We then can see exactly what is there and not just kick out answers, and give you solid advice.

The post above this one is wrong, you have to remove the data partition and make new ones for a Linux set up.

---

### Post by kansasnoob on 2012-07-03
Have you created an Ubuntu live CD/USB yet?

If so boot to the live desktop, open the terminal, and run this command:

```
sudo parted -l
```

Then post the full output of that command here so we can see what your actual partitioning layout is.

I'll bet you have at least one more partition than you think you do :)

---

### Post by kansasnoob on 2012-07-03
> **wilee-nilee said:**
> The confusion here is calling D a drive when it is a partition and called something different in linux, such as a sda1 or sda2 etc.

Boot the live ubuntu cd open gparted take a screenshot of it and post it using the paperclip in the reply panel. We then can see exactly what is there and not just kick out answers, and give you solid advice.

The post above this one is wrong, you have to remove the data partition and make new ones for a Linux set up.

+1!

Step #1 is always, show me what you got :D

---

### Post by CharlesA on 2012-07-03
> **chief grand teriki said:**
> boot from live cd, then select the unused partition to install ubuntu on!

Every setup is different and you should know how to proceed before jumping headlong into something such as installing an OS.

Backups help tremendously.

@OP: Gparted output would help wonders.

---

### Post by chief grand teriki on 2012-07-03
> **wilee-nilee said:**
> The confusion here is calling D a drive when it is a partition and called something different in linux, such as a sda1 or sda2 etc.

Boot the live ubuntu cd open gparted take a screenshot of it and post it using the paperclip in the reply panel. We then can see exactly what is there and not just kick out answers, and give you solid advice.

The post above this one is wrong, you have to remove the data partition and make new ones for a Linux set up.

When I installed ubuntu, I just selected the unused partition, and it formatted it automatically for me

---

### Post by mastablasta on 2012-07-04
> **nickelbox said:**
> I would like to take my D: drive and use that for the Ubuntu 12.04 install. 

if you want to access the data you download in ubuntu from windows then it might be a good idea to have a data partition formated to NTFS (which both OS can read and write to) and then use a smaller part of disk for Ubuntu 20-30 GB should be more than enough for the OS (i have it on 8GB virtual drive and it uses little over half of it).
 > 
WUBI is quick and easy but it installs inside of Windows and is virtual. Not what I want. 
with wubi only the disk is virtual. it's like a large file where the OS goes to. it is very good to test it, try it out, learn a bit about the os. it can then be easy to uninstall and move the stuff from it to a real install.

---

### Post by Fernhill Linux Project on 2012-07-04
First boot the live cd and select 'try ubuntu'
When it has loaded open 'disk utility' and click on your hard disk, then click on the 250gb partition you want to install to and just below you should see 'device' followed by something like /dev/sda2 and so sda2 would be the partition to install to.

Next click the 'install ubuntu' icon on the desktop and select the bottom option 'something else'. You will then be able to select which partition to install to, which will be called sda2 (or whatever you saw in disc utility).

Click on that partition and select 'change' then select 'format as ext4' and give it a mount point of '/'. 

Finally click install at the bottom.

---

### Post by nickelbox on 2012-07-04
I've played with the live disc and have installed Ubuntu 12.04 on my secondary laptop so I've gotten a little taste of the OS.

I don't want to go through the steps of installing WUBI and then doing the dual boot since I know I want to keep it. Seems to be an extra step for me since I know my end game.

As far as my partitions, I know I have C: and D: and there's a 25 GB portion allocated to what I assume is the recovery. I'll get an actual report soon...

---

### Post by nickelbox on 2012-07-04
> **Fernhill Linux Project said:**
> First boot the live cd and select 'try ubuntu'
When it has loaded open 'disk utility' and click on your hard disk, then click on the 250gb partition you want to install to and just below you should see 'device' followed by something like /dev/sda2 and so sda2 would be the partition to install to.

Next click the 'install ubuntu' icon on the desktop and select the bottom option 'something else'. You will then be able to select which partition to install to, which will be called sda2 (or whatever you saw in disc utility).

Click on that partition and select 'change' then select 'format as ext4' and give it a mount point of '/'. 

Finally click install at the bottom.

I ran across this tutorial. What do you guys think?

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

---

### Post by centaurusa on 2012-07-04
> **nickelbox said:**
> I ran across this tutorial. What do you guys think?

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

For me, it's more complex than it needs to be.  My preference is to create just a root partition and a swap partition.  Take a look at:

[http://linuxnorth.wordpress.com/manual-partitioning/](http://linuxnorth.wordpress.com/manual-partitioning/)

This posting has basic information about manual partitioning, plus links to other sources of information and video tutorials.

---

### Post by SirWhy on 2012-07-04
> **nickelbox said:**
> I ran across this tutorial. What do you guys think?

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

That's a nicely laid out tutorial. Wish I had that my first attempt at dual-booting, all those years ago before I knew about partitions properly. Even has a bit of a tutorial on EasyBCD (which in fairness is pretty straightforward but I digress)

---

### Post by kansasnoob on 2012-07-04
> **nickelbox said:**
> I ran across this tutorial. What do you guys think?

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

I don't think any of us should be giving advice until we at least see the output of this command:

```
sudo parted -l
```

A screenshot of Gparted would be even better :D

---

### Post by Elfy on 2012-07-04
> **kansasnoob said:**
> I don't think any of us should be giving advice until we at least see the output of this command:

```
sudo parted -l
```

A screenshot of Gparted would be even better :D

Absolutely agree.

---

### Post by nickelbox on 2012-07-04
Ok, here's the screenshot.

So my objective is a dual boot with a separate partition that both OS's can access for anything that I download, save, etc...

---

### Post by kansasnoob on 2012-07-04
OK, you see you actually have three partitions rather than just the two you'd spoken of. That's just fine, this should be very easy and very safe if you're patient ;)

First of all you'll notice that Linux/Ubuntu does NOT use drive C, Drive D, etc but rather /dev/sda1, /dev/sda2, and /dev/sda3. **Under no circumstances should you remove, move, or resize either /dev/sda1 or /dev/sda2!**

In fact since you have only three primary partitions the safest way to proceed is to keep all three partitions and use Windows own partitioner to resize the 240GB partition. Here's a guide giving a basic description of the Win 7 partitioner:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

You will be able to share the data on both Windows partitions with Ubuntu!

Since Ubuntu and Windows identify partitions somewhat differently remember the sizes:

25GB is Windows recovery - leave it alone

200GB is the Windows OS - leave it alone

240GB is Windows data and can be read by both Windows and Ubuntu - that's the one you want to resize!

Now it's time to consider how much room you want to give Ubuntu and whether or not you want to use a separate /home. IMHO using a separate /home is not the life-saver I used to think it was, but that's arguable.

Data that's not backed up to an external device is always subject to loss due to hardware failure, and data that's not backed up off-site is always subject to loss through fire, flood, or theft :(

Another thing we should consider is swap size. I can't adequately address that issue w/o seeing the output of this command:

```
free -m
```

Believe me, this is all important. Why not get it right the first time instead of having to muck around for days fixing things ;)

So post that output and consider whether you want a separate /home or not.

---

### Post by nickelbox on 2012-07-04
So what is the purpose of a separate /home?

---

### Post by kansasnoob on 2012-07-04
> **nickelbox said:**
> So what is the purpose of a separate /home?

If you create a separate /home partition and choose to reinstall using advanced partitioning (now called "something else") you can then select to use but NOT format the existing /home partition. The /home partition houses all of your settings and also the default Document, Downloads, Pictures folders.

But just consider that you said:

> my objective is a dual boot with a separate partition that both OS's can access for anything that I download, save, etc... 

So it's reasonable to assume that most of your data will be on either the Windows OS partition (200GB) or the Win data partition that you're going to resize. Windows can't natively read Linux partitions but Linux can read and write to NTFS.

Another thing to take into consideration is that if you ever run the Windows recovery all Ubuntu will be gone, including any data in any Linux partition!

---

### Post by nickelbox on 2012-07-04
I don't think I need a /home partition for what my purpose is going to be.

Here's the screenshot you requested

---

### Post by nickelbox on 2012-07-04
Just bumping this so it stays on the first page...

---

### Post by mastablasta on 2012-07-05
/home is kind of like my documents folder. so since you don't need it lets not complicate things here. 
 
use windows disk manager to create empty disk space (don't format the partition). as i said before you might want to have an NTFS partition for data. and OS doesn't take so much.
if you already did this start the install and select to install it to largest free disk space check if it's the right partition and then just continue with install.

---

### Post by Elfy on 2012-07-05
> **nickelbox said:**
> Just bumping this so it stays on the first page...

Please only do this once a day. 

Not to keep it on the first page - people are answering and likely have subscribed.

---

### Post by nickelbox on 2012-07-05
So then how much space to allocate for Ubuntu?

I also assume that my D: that is labeled Data would already meet the specs to use for both OS's since it's already NTFS?

---

### Post by mastablasta on 2012-07-05
carve a 25GB of unformatted disk space out of your D drive. 
 
Ubutnu will use ext4 (at least that is recommended file system)
 
you will need about 6GB disk space for sytsem (maybe less then you will install some favourite programmes) and maybe some updates (older kernel) will also occupy some space. so let's say less than 10 GB. the rest you can use to store some data you download, or maybe load a game in wine (they take up plenty space) etc. point is it should be plenty of space.
 
if however, you would later find out you need more you can add more from D. only you would need to defrag the D partition first. or rather the computer will do the defraging :-)

---

### Post by kansasnoob on 2012-07-05
I'll try and get back to this ASAP. The neighbors were having a 4th of July celebration and nearly burned my garage down.

All is well but I inhaled a butt-load of smoke and combined with my emphysema I had to spend the night in the hospital.

It's just that my mind is even less sharp than usual ATM ;)

OTOH this is why the forums are truly great, it's not like dominos. Even if one falls the rest stay standing strong :D

---

### Post by nickelbox on 2012-07-05
Hope you're doing better. Sounds like a rough day for you...

---

### Post by kansasnoob on 2012-07-06
Thanks for your patience :)

I see from the last screenshot that you appear to have about 3GB of RAM. Does that sound right? If so I'd expect the "automated" installation process to create a swap partition ranging in size from about 3GB to 6GB. 

I'm not quite sure what parameters the installer uses to determine actual swap size. Certainly the amount of RAM is one of the parameters used but available disc/partition space appears to play a smaller role.

I just wanted to know because some of the newer computers I've worked on have had as much as 16GB of RAM so the automated installer will gobble up a fairly large amount of disc space.

So, my personal recommendation would be to use Windows own partitioner to free up about 40GB of space for Ubuntu. The reason I recommend using Windows own tool is because it should never "eat it's own" ;)

The reason I recommend about 40GB is that since you're a bit new to Ubuntu you may want to try any number of things, like fiddling with different desktop environments, or even playing with virtual machines, etc.

So, once Windows is done freeing up that space I'd reboot Windows at least twice just to be sure all is well. Then it's time to boot the Ubuntu live CD. I'd personally boot to the live desktop rather than just choosing install because you can then take screenshots or use the command line to gather info in case something doesn't appear right or if anything is even slightly confusing.

Note: The **quit** button is there for a reason!

Now I need to pause and explain something, it might seem boring but it's important! Prior to Maverick (aka: 10.10) the live installer specifically included an option to "Use largest continuous free space" but the devs then combined it with "Install alongside".

In Precise the only way you can tell if you're actually going to be offered the choice of resizing a partition or installing to the largest continuous free space is whether the button in the lower right hand corner of the "Installation type" screen says "Continue" or "Install now". Examples:

[ATTACH]220758[/ATTACH]

[ATTACH]220759[/ATTACH]

If it says "Install now" then it has selected the largest continuous free space and the automated installer will create the partitions for you. One mistake many users make is having an external device connected with a larger free space than the one intended for installation, that includes external USB drives and flash cards.

Once that is complete you'll just need to answer some very simple questions, enter your user ID info, etc.

What the installer will do is create an extended partition that will contain two logical partitions and then you should be in business :D

Please let me know if any of this is even slightly confusing.

---

### Post by kansasnoob on 2012-07-06
> **nickelbox said:**
> Hope you're doing better. Sounds like a rough day for you...

The smoke from the fire was easier to deal with than the insurance adjusters and the fire marshals. It's getting to the point that everyone needs a lawyer on speed-dial :)

---

### Post by nickelbox on 2012-07-06
Thanks everyone for the info. I plan on possibly doing this on Sunday if all works out. Will let you know how it all turns out.

---

### Post by nickelbox on 2012-07-08
Ok, so I setup the dual boot and everything worked flawlessly except for one hitch. When I boot up, it appears I am getting the Grub boot menu which looks similar to this: (Obviously couldn't get a screenshot of what I actually have but this is close enough to give you an idea)

[IMG]http://www.dedoimedo.com/images/computers_new_2/dual-ubuntu-grub.png[/IMG]

When I select Windows 7, I get my options that I wanted when using EasyBCD which look like this:

[IMG]http://www.linuxbsdos.com/wp-content/uploads/2012/05/EasyBSDUbuntu-600x450.png[/IMG]


So how do I remove having Grub initialize first when I want Windows Boot Manager to start first?

---

### Post by oldfred on 2012-07-08
A few here that are primarily Windows users do use EasyBCD, but most of us use and like grub2 as it works to multi-boot.

Understand with EasyBCD you have to install grub2 to a partition which is not recommended. You may have to reinstall on major updates as it has to use hard coded addresses which may change on updates. So have liveCD ready and know how to reinstall grub2.

You may do better on the EasyBCD site.

[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by nickelbox on 2012-07-08
So then how can I edit Grub to only show the two options I want and default boot to Windows 7?

---

### Post by kansasnoob on 2012-07-08
> **nickelbox said:**
> So then how can I edit Grub to only show the two options I want and default boot to Windows 7?

I am very rusty at boot issues because I've focused mostly on desktop environment and installer issues over the past couple of dev cycles, but I have in the past used Grub Customizer:

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

You may be wise to add a comment to that thread before jumping headlong into it though :)

---

### Post by oldfred on 2012-07-08
+1 on kansasnoob's suggestion for grub customizer.

Many users have posted that it works well for them.

---

### Post by Shadius on 2012-07-08
> **nickelbox said:**
> So then how can I edit Grub to only show the two options I want and default boot to Windows 7?

I've used the guide from [Psychocats]("http://www.psychocats.net/ubuntu/bootmenu") to get my computer to default to Windows instead of Ubuntu. Also, Psychocats, in general, has great tutorials that you might want to check out.

---

### Post by nickelbox on 2012-07-08
I ended up using EasyBCD to fix the problem. Works beautiful now!

Thanks everyone for the help!

---

