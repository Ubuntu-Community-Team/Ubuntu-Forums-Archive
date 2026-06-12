---
title: "Ready to install dual boot ubuntu, but want to backup MBR. How/When?"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by Peter Parkorr on 2011-10-12
Hi,

I'm going to install Ubuntu 11.04 (alternate, 64bit) for dual boot with win7 on my laptop, and I want to make a backup of my MBR before going ahead. I dont have a windows disc or I would remove it completely.

I've read a few threads and HowTo's but none of them are clear enough for me and my HD seems to already have one more partition than I expected?

I've tried Ubuntu with the Live CD and everything works great. GParted showed;
/dev/sda1   PQSERVICE              15GB         label 'diag'
/dev/sda2   SYSTEM RESERVED   100MB       label 'boot'
/dev/sda3   Acer                         581.07GB  no label
unallocated                                 1.34MB

I am going to shrink my windows partition (using windows), and then define a partition for Ubuntu and have a final partition for storing files that I want both OS to be able to access (but mainly ubuntu).

So should I shrink windows, create the extra partitions and then backup my MBR to the Storage partition?
I'm not sure how to do it yet (or where the MBR is on my HD), and not very comfortable using dd commands as I have read the warnings!

Why does my system have the PQSERVICE partition? I have recovery DVDs, so is it still required?

Any help appreciated!
Shane

---

### Post by matt_symes on 2011-10-12
Hi

Before you do anything, i would highly recommend you clone your entire hard drive using Clonezilla (or something else) from a LiveCD/USB. Back it up to an external hard drive. 

That way if you have any problems you can roll back. It also comes in useful if you want to sell the computer at a later date.

Also, make a windows recovery disc.

Kind regards

---

### Post by Mark Phelps on 2011-10-12
While Clonezilla will certainly work, you might find it easier to restore later if you use a Windows app to backup Win7. Strongly recommend Macrium Reflect -- the FREE version.  Download and install that on Win7, then use the option to create and burn a Linux Boot CD.

While in Win7, use the Backup feature to create and burn a Win7 Repair CD.  With this CD, you can later restore your original Win7 MBR.

Also, when you do the partitioning in Win7 Disk Management, be careful to ensure that you do not end up with more than 4 Primary partitions. Doing so will automatically convert your existing partitions to Dynamic Disks -- something you do NOT want to do.

Once you have shrunk the Win7 OS partition to make room, use MR to do an Image backup to an external drive.  That will also back up the Win7 MBR.

---

### Post by matt_symes on 2011-10-12
Hi

> Macrium Reflect

Thanks Mark :p. I have never used this and i will check this program out myself.

Kind regards

---

### Post by dFlyer on 2011-10-12
Don't do anything without first making a clone of your hard drive. Problems have been known to arise and if you don't have a windows install disk, you will be up the creek. There are several free cloning programs available on the web, just do a google search search.

---

### Post by Peter Parkorr on 2011-10-12
Thanks for the quick responses (especially with the info on max 4 primary partitions).

I have created a Win7 repair disc and just looking at Macrium Reflect to make a backup image of my HD. I did search cloning software and [this review]("http://downloadsquad.switched.com/2008/09/05/5-free-apps-to-clone-your-hard-drive/") was helpful so I went with MR. Going to make a couple of clones and then proceed.

MR shows that 2 of my partitions are 'NTFS Primary' and the 3rd 100MB partition is 'NTFS Active'. So I hope I will be able to create 2 new partitions (one for Ubuntu, one for files/docs) without going over 4 Primary partitions?

I'm still not sure what my 1st primary partition (15GB) is there for...  other HowTo's on dual booting win7 and Ubuntu ([here]("http://www.lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") and [here]("http://members.iinet.net.au/%7Eherman546/index.html")) indicate there should only be 2 including the 100MB (which I assume is the windows boot loader). But it is 76% in use so I will leave it be.

Thanks,
Shane

---

### Post by anewguy on 2011-10-12
+1 on Macrium Reflect.  My friends and I have been using it for a few years for all of our Windows-based backups - even across a network.  Works great.  It will remind you, but be sure to do what Mark Phelps said:  Make the boot disk and test it to be sure you can boot from it prior to moving on.

As far as partitions, again as Mark Phelps mentioned, be sure not to try to have more than 4 Primary partitions.  Ideally, you would add a single Primary partition, then within it add the ubuntu partitions as extended partitions.  Normally it is recommended to create 1 partition for swap, 1 partition for / and one partition for /home.  /home is where all users' folders reside so if you make a separate partition for it you won't loose things if you have to reinstall or upgrade.

Dave ;)

---

### Post by oldfred on 2011-10-12
Your first partition is the vendor recovery partition. Some can just use it to make a set of DVDs that is the system image as when you purchased it. Before any updates, new software and many reboot. But some seem to create just a smaller recovery DVD and still require the recovery partition to recreate system to 'as new' state. Best to leave it if you do not know, but full backup would be better to restore system anyway.

You use the last primary partition as an extended partition which can hold may logical partitions. Windows will also read data from a logical that is NTFS formated, but will not directly boot from a logical. Linux boots from a logical without any issues.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Mark Phelps on 2011-10-12
> **Peter Parkorr said:**
> MR shows that 2 of my partitions are 'NTFS Primary' and the 3rd 100MB partition is 'NTFS Active'. So I hope I will be able to create 2 new partitions (one for Ubuntu, one for files/docs) without going over 4 Primary partitions?.

The 100MB partition is the new BOOT partition that OEMs put on Win7 preinstalled systems. So, that means you already have three partitions.  If you create 2 more Primary partitions, that will put you over the limit of four -- and, unfortunately, the Win7 Disk Management tool will let you do just that.

Instead, what you really want is the following:
-- Three Primary partitions
-- A fourth, Extended, partition -- with all the Linux filesystem partitions contained inside it.

This basically is the arrangement that oldfred mentioned in his latest post.

---

### Post by Peter Parkorr on 2011-10-12
Thank you again.

I am just updating windows, and then will give it a defrag before shrinking its partition. Then I'll clone my HD after shrinking so the image is as up to date as possible.

I've got a working Macrium recovery CD for windows now as well. Slow but steady progress   :thumbs:

Edit: Do you always need the swap partition? I have 8GB of RAM.

Now I've defragged my virtually unused HD (533GB free of 581GB) but windows disk manager is reporting I can only shrink the win partition by 280GB. 
Not cool, that will leave my windows partition at ~300GB. Is there a Linux tool that can do it better?

Shane

---

### Post by oldfred on 2011-10-12
If you never hibernate you probably could get by without. I have heard that it boots a bit slower without any swap as it has to look for it and fail. I would just give a small swap of 2GB or create a swap file.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

While you can backup MBR with dd, I would not. You can easily reinstall all boot loaders if you have the repair CDs or liveCD/USB.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by anewguy on 2011-10-13
> **oldfred said:**
> Your first partition is the vendor recovery partition. Some can just use it to make a set of DVDs that is the system image as when you purchased it. Before any updates, new software and many reboot. But some seem to create just a smaller recovery DVD and still require the recovery partition to recreate system to 'as new' state. Best to leave it if you do not know, but full backup would be better to restore system anyway.

You use the last primary partition as an extended partition which can hold may logical partitions. Windows will also read data from a logical that is NTFS formated, but will not directly boot from a logical. Linux boots from a logical without any issues.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Thanks for the partitioning stuff - I was getting pretty tired yesterday and in checking my posts tonight to see if I screwed something up I noticed my post prior to yours, and I screwed up the terms on the partitioning.  Glad you were there to straighten that out!

Dave ;)

---

### Post by Peter Parkorr on 2011-10-13
Ahh, didn't spot your response in time oldfred as it had moved on to a 2nd page!

Anyway, currently posting from my working Natty install so all good  :)

I created an Extended partition on my remaining free space. Then I created a 224GB NTFS logical partition called Storage, and an unformatted logical partition from the remaining space (~55GB). At this point I was intending to create a swap file in my Storage partition but later read that it was not as effective and can be slower, or can cause disk I/O problems.

I installed Ubuntu from the install file while running the LiveCD, using the 'advanced partitioning' option to choose the right partition, putting '/' in the Mount field and ext4 journaling as the format, and declined to add a swap file.

So after reading the SwapFaq and before exiting the LiveCD I used GParted again to shrink the Storage partition and add a logical Swap partition. I saw a few threads on what size was suitable, and in the end went for my RAM size plus ~1GB (= a farily large 9GB), in case i want to hibernate and because I plan on using lots of graphics and video editing applications. I didn't realise 'hibernate' meant specifically with no power or battery tho, so its unlikely I will do that, but no harm done.

Also glad to read that I can use space in my Win7 partition for storage and access it readily from Ubuntu, so the oversized windows partition doesnt matter too. 

It's all going swimmingly. Thanks for the invaluable advice.

Just having problems getting updates now, but I think thats the Ubuntu servers today. Are they based near Blackberrys servers? lol

**One other question**; I want to install a lot of applications bundled with Ubuntu Studio, and I have the install image (which I didnt use as I dont need the low latency kernel). Is there a way to get the apps I want from that instead of downloading them all?

AND - should I bother to change my swapiness from 60 to 30 or 20?

Shane

---

### Post by oldfred on 2011-10-13
Oneiric just came out, servers are going to be busy for a few days. You should change your server to the 'best' server. In update manager, tab Ubuntu Software, download from, click on other and choose best server. It pings everyone and gives you the best. You may want to check again in a few days as it may change based on how systems will be loaded.

You can also select CD as download source but I have never done that. 

I prefer smaller system partitions, just so heads on hard drive are now search large partition for most used files. Data not used so much then can be spread out in a large partition.Also slightly easier to backup as you know data is in data partition(s).

---

### Post by anewguy on 2011-10-13
Re: hibernation - personally, if you have a relatively new piece of hardware (and I don't mean only a year or 2 old - can be quite a bit older), the new OS's with as fast as they boot to me makes hibernation sort of a mute point.  It made sense quite a while ago with slower hardware and slower to load OS's, as indeed the time to reload from swap and be running was quicker then - not so much now.  So, and this is just me, hibernation really isn't needed with modern hardware and OS's.

Just my 2-cents worth!  ;)

Dave ;)

---

### Post by Blasphemist on 2011-10-13
> **Peter Parkorr said:**
> Thank you again.

I am just updating windows, and then will give it a defrag before shrinking its partition. Then I'll clone my HD after shrinking so the image is as up to date as possible.

I've got a working Macrium recovery CD for windows now as well. Slow but steady progress   :thumbs:

Edit: Do you always need the swap partition? I have 8GB of RAM.

Now I've defragged my virtually unused HD (533GB free of 581GB) but windows disk manager is reporting I can only shrink the win partition by 280GB. 
Not cool, that will leave my windows partition at ~300GB. Is there a Linux tool that can do it better?

Shane

Good stuff! You've prepared well and protected yourself. Everyone has answered with conservative recommendations which are appropriate.

No, you don't have to use a swap unless you want to be able to hibernate. I will tell you that in my experience with 3GB of memory, only when working with a large number of songs or pictures is my swap used much at all. Still, with your amount of disk space it seems reasonable to put a 8GB swap at the end of the disk in the extended partition. More on that later.

You've done all the conservative preparation. Now you need to do something you will see disagreement about in these forums and that does carry some risk. It is my opinion and experience that windows will never shrink itself to where you are not wasting a bunch of space unused in the windows partition. It makes sense. Windows has itself spread out, fat and happy, and while it is in use you are trying to squeeze it down to a disk space diet. 

You can keep doing the whole cycle (defrag, shrink, look at application error log, see what stopped the shrink, figure out a way to address that file, do it all over) and find yourself trying to out smart windows by turning off services or features temporarily. This will include changes that should not be permanent and entail some risk. All in the name of shrinking an OS while it is in use. Doesn't make sense to me.

And if you think about it, the default install of ubuntu or any distro you first install on a system that already has windows will use linux tools to shrink the windows partition. If you want to limit windows to a reasonable level of disk space, you too will use linux tools to do this. In the ubuntu world the tool is GParted. 

Here is what you'll need to do with it. This is after you've done what you have done. Ensure that no more than 3 primary partitions exist so you can create an extended partition with logical partitions in it. This means some people will have to delete an existing manufacturer tools partition or some other partition that you can do without.

1. Determine how much free space you should leave within your windows partition for future needs. If you want to leave 30GB free for example and you currently have 200GB free, you'll shrink enough to free up 170GB. Know how much windows is using and much you want to leave it free, shrink the partition by the remaining amount.

2. Get some familiarity with GParted. You can boot the live cd/usb and run GParted to do that. It isn't hard to use but use it's help to understand how to do what you plan to do.

3. Understand your partition layout. After shrinking will your free space all be contiguous? Shrinking the windows partition will leave free unused space at the end of the location it is using now on the drive. If you had to delete a partition, does it leave free space at the beginning of the disk or will it be contiguous with what you get from the shrink? The extended partition will need to use contiguous space on the disk. 

4. Think about how you plan to use the space for linux. You don't have to be able to see the future with clairvoyance but if you have desires and plans, plot that use out on the drive. You can make changes later but you should think about this and make partition changes as seldom as you can. If you want to share a partition for documents, pictures, music, etc., how big does it need to be and will it be shared just among linux distros or with windows too? A partition shared with windows needs to be formatted as NTFS but if it is only a linux share it should be EXT4 or another journaling file system. Know what partitions you'll be creating, what they will be used for and how big they'll be. One swap partition can be used for multiple linux distributions if you'll be installing multiple distros. Put the swap at the end. 

5. Start out with one change at a time. If you shrink windows, do only that, reboot and windows will want at least one chkdsk to run. There may be two reboots with a chkdsk each time. Make sure windows functions as expected before proceeding. Then if there is an existing extended partition (you don't have one now in this case) expand it and then reboot and retest existing functionality. 

6. I recommend that you create partitions prior to ubuntu/linux installation and then during installation direct the installer to use your planned partitions. During the disk allocation section of installation you can choose a partition for the / (root) mount point. You need that and you don't need to set anything for the swap if a swap type of partition already exists from your preparation. If you want a shared home partition for that distro to use, you need to choose the partition for that and set its mount point as /Home. The other mount point choices are seldom used.

I think that is a long enough post (sorry for the length) for now. If this brings up questions, please ask.

---

### Post by Peter Parkorr on 2011-10-13
> **Blasphemist said:**
> Good stuff...

No, you don't have to use a swap...  with your amount of disk space it seems reasonable to put a 8GB swap at the end of the disk in the extended partition. [COLOR=Blue]Did that (9GB)[/COLOR]

Now you need to do something you will see disagreement about... windows will never shrink itself...
You can keep doing the whole cycle... trying to out smart windows... If you want to limit windows to a reasonable level of disk space, you too will use GParted. [COLOR=Blue]Controversial! Go on...[/COLOR] 

create an extended partition with logical partitions in it. [COLOR=Blue]Did that[/COLOR]

1. Determine how much free space you should leave within your windows partition. [COLOR=Blue]It is using 51GB of 302GB, I would love to reclaim 200-225GB[/COLOR].

3. After shrinking will your free space all be contiguous? [COLOR=Blue]Jah. It won't be next to my current storage partition but the free space will be next to the extended partition;[/COLOR]

4. A partition shared with windows needs to be formatted as NTFS [COLOR=Blue]- It is.[/COLOR] 
Put the swap at the end. [COLOR=Blue]I did (fluke). Any reason?[/COLOR]

5. one change at a time. If you shrink windows, do only that, reboot and windows will want at least one chkdsk to run.[COLOR=Blue] kk[/COLOR]

6. I recommend that you create partitions prior to ubuntu/linux installation and then during installation direct the installer to use your planned partitions. [COLOR=Blue]Affirmative, this was carried out earlier, Sir[/COLOR]
During the disk allocation you can choose a partition for the / (root) mount point. [COLOR=Blue]Aye Captain.[/COLOR]  
You don't need to set anything for the swap.[COLOR=Blue] Completed in retrospect, commander.[/COLOR] 
If you want a shared home partition for that distro to use, you need to choose the partition for that and set its mount point as /Home. [COLOR=Blue]This I still need to do, as well as the win7 equivalent with libraries.[/COLOR]

Cool, thanks for the post, I think I scored 8 out of 10, with room for improvement in the 'get some balls and trim windows back boy!' area. I will not be doing it immediately, maybe after creating another disk backup image first. 
Plenty of room for now and as I mentioned earlier I can still use my win partition space from linux anyway. I'm mostly amazed that from a jumble of FAQs, a random assortment of threads, and a few differing opinions I came out with almost exactly what you recommend. Pat on my own back  :)

Thanks Jim,
Shane

---

### Post by Blasphemist on 2011-10-14
I think you're figuring this stuff out just like I did Shane. That would explain us coming to the same ideas. I'll include a shot of my partitions here so you can see how mine is set up. It sounds like you'll need to do just as I had to and expand your extended partition to the left after the shrink. 

Notice a few MB unallocated in a few places, don't worry about that. Also notice how much is used in each partition. The distros don't really need much space unless you install a lot, such as server stuff and development apps, and if aren't careful you can end up with a lot of unused space spread all over when using a bunch of partitions. I put the swap at the end just for organization and to keep it from being involved if I change partition sizes or use.

As I convert over to using my Oneiric parts as my main environment I think my now main partition is going to become a /Home partition for all distros. My data partition will hold a lot of the same stuff but is accessible to windows too. That /Home will be what gets backed up daily to the external usb drive and this will keep me pretty safe especially with the cloud now. I'm planning to play with Fedora 16 on the oneiric part that gets retired and then put precise pangolin on it after that.

---

### Post by Peter Parkorr on 2011-10-14
Mine looks similar but with a lot less partitions (pic attached). I was going to ask why you had so many! but I can see you are involved with the development like some other posters on this thread. I would love to get involved at some point, what is best to learn with that in mind? Scripting or a programming language?

I am not going to update to Oneiric (which I cannot even pretend to be able to pronounce) until I am happier with 11.04, but is there a benefit to updating over a new install of each version i.e. keeping installed programmes etc?

Cheers,
Shane

---

### Post by oldfred on 2011-10-14
After updating in place many times, had to do a clean install to convert to 64bit. Really liked how it ended up cleaner. But you have to plan ahead. If data or /home is in separate partition that helps. You can export list of installed apps and reinstall the latest version. Best is just to install to another 20GB partition and then if you forgot something you can go back. That is why I have all installs since 9.10 still installed. I originally was just going to use 2 partitions and alternate but I had room and kept adding.
My backup plan is a clean install as I do not have much that I have to have as a home system. So I backup what I would need anyway for each new install.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by Peter Parkorr on 2011-10-16
Thanks for that link oldfred, will make reference to it shortly. You said that having no swap may increase boot time as there is a delay while swap is being looked for - how can I check my installation is using swap properly?

I added my swap partition after installing so not sure it is being used. And I tend to get a 15 second black screen between my grub screen and ubuntu being loaded, doubling my start up time.

In Network Monitor my swap always shows 0% use but that may be expected as I am using <1GB of RAM from 8GB capacity. I did run a command from terminal (cant rmbr it now) to check my swappiness, which returned the default value of 60, but I thought that may come back regardless of swap being present.

> **anewguy said:**
> Re: hibernation - the new OS's with as fast as they boot to me makes hibernation sort of a mute point.
Dave ;)

Yeah, agreed Dave!

If I change my thread to [SOLVED] will I no longer get replies? My original query is solved, but I have more   :P

Shane

---

### Post by oldfred on 2011-10-16
A lot of people stop looking once its is solved. But if different issues best to start a new thread with better title anyway.

You really do not want to use swap as it is at least 10 times slower than RAM. With lots of RAM Linux caches recent activity in RAM so RAM may look more full than it really is and it will only start using swp when current running program(s) fill all of RAM. Video editing can use a lot of RAM otherwise you just about have to load every program you have all at once.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

Memory use including swap
free -m

---

### Post by Peter Parkorr on 2011-10-17
Thanks again oldfred.

As suspected, I have zero swap coming up so I will go to the swapfaq and work it out.

Cheers,
Shane

---

### Post by Peter Parkorr on 2011-10-17
I checked if swap was enabled with the 'cat /etc/fstab' command in terminal (as per Enabling Swap in swapfaq), and there was no line present for my swap. Also noticed my swap use showed as 0% _of 0.0GB_ in the monitoring software (duhhh...).

I thought I would try remedying this by auto-mounting my swap partition using Storage Device Management ('pysmd') and when I clicked Yes to 'do you want to enable this partition' it detected it was swap itself. Reboot, and I am showing 7.7GB Ram and 8.8GB swap. Too easy...    ha. Hasn't fixed the 16 seconds of dead time before booting up tho.

I will mark this thread solved anyway, thanks all for the help.
Shane

---

