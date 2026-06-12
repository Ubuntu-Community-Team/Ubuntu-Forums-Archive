---
title: "How to: ReadyBoost with Ubuntu Linux"
date: 2007-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by max.durden on 2007-03-28
[COLOR="Red"]EDIT: This thread is closed, and pending Staff review[/COLOR]

Hi everybody,
by following this little tutorial you'll be able to use a USB pen prive as an additional swap. As a result, the pen drive will be used in the same way windows Vista does through the ReadyBoost functionality.

Instructions are very simple:

1) plug the pen drive in your usb connector;
2) if ubuntu automount the device (usually in /media/usbdisk), umount the device (ie., sudo umount /media/usbdisk);
3) sudo mkswap /dev/sda1 (assuming /dev/sda1 is the correct device for the connected usb device)
4) sudo swapon -p 32767 /dev/sda1

... and you are in!

do a "cat /proc/swaps" to check if everything is ok; on my laptop I get the following output: 

Filename                                Type            Size    Used    Priority
/dev/hda4                               partition       2353512 116     -1 (standard HD swap partition)
**/dev/sda1                               partition       1981928 123900  32767** ("ReadyBoost"-style pen drive)

Quite obviously, performances are not the same as with real additional ram; however, I feel REAL gain in speed while using eclipse+tomcat+mysql for development on my laptop (which is equipped with just 512MB ram). 

Possibly, a simple bash-script can be developed to automate the few steps...

Happy coding!

Max

---

### Post by rolando2424 on 2007-03-28
Nice! :D

Too bad my pen is just 256 mb :(

---

### Post by max.durden on 2007-03-28
even if you have a small pen drive, you can still take some advantage from usb swapping: whenever usb space finishes, the system will automatically activate the "secondary" standard hd swap declared in the fstab conf directive! 

Bye

Max

---

### Post by Treviño on 2007-03-28
I tried the same some time ago, the problem is that I've read somewhere around that the flash memories can be wasted by this rapid read-writing...
Is this true?

---

### Post by max.durden on 2007-03-28
Hi, Treviño
you are right. Specifically, the usb storage writing cycles are limited, not the reading ones. However, I'm still incline to consider usb mass storages as a cheap solution to strict memory requirements: in example, if you check the Ebay for usb storages you can get a 2 gb pendrives for less than 10 euros (plus delivery cost).

Quite obviously, I'm not saying that you can substitute ram for pen drives, but situation exist where they are really useful. In my case, I use my *standard* 512 MB Mb for normal laptop use, and exploit "readyboost" only when I'm working on web development at home, where I cannot exploit facilities offered by other networked pcs.

Happy coding

Max

---

### Post by berserker on 2007-03-28
> **max.durden said:**
> Possibly, a simple bash-script can be developed to automate the few steps...

Thanks for this tip.  I was wondering if this could be done in Linux.

Can't you just add this to /etc/fstab as the second swap entry?

---

### Post by max.durden on 2007-03-29
I think you could add the swap entry to fstab, but this implies that you should have your pen drive already connected at boot time. If you are working on a desktop, this is fine, but with a laptop I think it is better to write a bash script to be invoked "on-demand" whenever you need the extra usb swap partition.

Bye 

Max

---

### Post by hype on 2007-03-29
You could make use of your usb pen uuid:
sudo vol_id -u /dev/hdxy

Then configuring you fstab, your pen will always be mounted where you want.
I dont know how to "add" this command to fstab tho: sudo swapon -p 32767 /dev/sda1

---

### Post by miggols99 on 2007-03-29
How do I stop the readyboost? When I looked on my flash drive it had a file on it, and I had to format it to remove it in Ubuntu.

---

### Post by max.durden on 2007-03-29
"swapoff /dev/sda1", assuming /dev/sda1 is the correct device for your pen drive

Max

---

### Post by Treviño on 2007-03-29
I think that users of PCs/Notebooks with flash-readers included could have a better use of their (generally) few used ports ;)

I knew this fact, but unfortunately I can't apply... (and btw I've 1280mb of ram :P)

---

### Post by max.durden on 2007-03-29
May the ram be with you :cool:

---

### Post by blue_Sphere on 2007-04-04
> **max.durden said:**
> Hi everybody,
by following this little tutorial you'll be able to use a USB pen prive as an additional swap. As a result, the pen drive will be used in the same way windows Vista does through the ReadyBoost functionality.

Instructions are very simple:

1) plug the pen drive in your usb connector;
2) if ubuntu automount the device (usually in /media/usbdisk), umount the device (ie., sudo umount /media/usbdisk);
3) sudo mkswap /dev/sda1 (assuming /dev/sda1 is the correct device for the connected usb device)
4) sudo swapon -p 32767 /dev/sda1

... and you are in!

do a "cat /proc/swaps" to check if everything is ok; on my laptop I get the following output: 

Filename                                Type            Size    Used    Priority
/dev/hda4                               partition       2353512 116     -1 (standard HD swap partition)
**/dev/sda1                               partition       1981928 123900  32767** ("ReadyBoost"-style pen drive)

Quite obviously, performances are not the same as with real additional ram; however, I feel REAL gain in speed while using eclipse+tomcat+mysql for development on my laptop (which is equipped with just 512MB ram). 

Possibly, a simple bash-script can be developed to automate the few steps...

Happy coding!

Max

Hrm reading this and knowing a little about windows paging I have some questions. 

1. Data that is stored on swap is sometimes critical data, if the drive is removed the system will crash, corrupt files, etc. For this reason Vista makes a duplicate copy on the hard drive as well. Is this the same as linux? 

2. The number of times flash can be rewritten is limited, we all know this, BUT according to Vista the readyboost system allows flash to last for ten years or even more. Is this true with Linux?

3. I know that programs like "virtual drive" for xp allow you to actually put the swap onto your ram if you have enough. Now this might sound excessive since swap is *supposed* to be an extension of ram, but the speed increase is phenomenal. Is this possible in linux? (or if linux actually makes efficient use of my ram I will cry tears of joy)

(Info on readyboost taken from here [http://blogs.msdn.com/tomarcher/archive/2006/06/02/615199.aspx](http://blogs.msdn.com/tomarcher/archive/2006/06/02/615199.aspx)) 

I am currently running a turion 64 (2.4ghz) with 2gb of ram. 

Thanks
-Blue

---

### Post by max.durden on 2007-04-05
Well, I am absolutely not an expert of linux swap management, but I will try to give you some answers while hoping that   a "swap guru" will join the thread...

So

1) if you swapoff the usb drive, the system will start to use standard hd swap (assuming it is has been activated during the boot sequence). You can try this by monitoring "/proc/swaps" after having issued a swapoff /dev/sda1 command (I have not yet tried "brute force" unplug of  the usb drive, however...);

2)I suspect it to be marketing ****...

3) simply turn off all your swap partitions

Please, let me now if you manage to get more info on the matter... It turns out to be very interesting to me, thanks

Bye
Max

---

### Post by insane_alien on 2007-04-05
just to add to this(although its completely pointless in this day of flashdisks by the dozen) it also works for a floppydrive :D

long story short, i was bored, i was browsing and i wanted to find a use for this floppy drive.

not so great performance though.

---

### Post by shingalated on 2007-04-05
Why would you need this in linux??
I have 768 MB of ram, and my computer hardly touches the swap file.

---

### Post by insane_alien on 2007-04-05
you don't it just proves that we can do anything MS can and have been able to for a long time. its just that we don't even need to do it that makes us so awesome :D

---

### Post by shizeon on 2007-04-05
From what I read, Vista's readyboost isn't making use of the flash drive for swap.  It is using it as a disk cache for frequently accessed files.  There is a difference **if** I understand this all correctly.  A (slightly stretched) example would be if a program needs to open a specific image over and over again.  If I was running vista, the program would automatically make use of the disk cache provided by readyboost and load it directly from flash.  Placing the swap file on flash wouldn't provide any speed up here.

Am I wrong?

Found some details on how it is implemented at: [http://blogs.msdn.com/tomarcher/archive/2006/06/02/615199.aspx](http://blogs.msdn.com/tomarcher/archive/2006/06/02/615199.aspx)

Question is, can we do something similar on Linux to transparently cache disk access?

Nice tip though, still going to give this how-to a try on my low ram systems that swap frequently!

Thanks!
- Sean

---

### Post by blue_Sphere on 2007-04-05
> **shizeon said:**
> From what I read, Vista's readyboost isn't making use of the flash drive for swap.  It is using it as a disk cache for frequently accessed files.  There is a difference **if** I understand this all correctly.  A (slightly stretched) example would be if a program needs to open a specific image over and over again.  If I was running vista, the program would automatically make use of the disk cache provided by readyboost and load it directly from flash.  Placing the swap file on flash wouldn't provide any speed up here.

Am I wrong?

Found some details on how it is implemented at: [http://blogs.msdn.com/tomarcher/archive/2006/06/02/615199.aspx](http://blogs.msdn.com/tomarcher/archive/2006/06/02/615199.aspx)

Question is, can we do something similar on Linux to transparently cache disk access?

Nice tip though, still going to give this how-to a try on my low ram systems that swap frequently!

Thanks!
- Sean
Hrm I am interested in this as well...

---

### Post by andb on 2007-04-06
Ive got a wonderfully functional Edgy machine with 512MB memory. My Vista work laptop has 3GB, and its almost as fast. 

Question - Concidering that memory management is done right in Linux, who needs such an problem-ridden solution?

MS has put a lot of work into their solution. If Linux kernel swap management could recognize what is not written to often then it might work. But why add unneeded functionality to the kernel? The more stuff, the more likely you are to have bugs. And this would really have to be a kernel level solution.

I have a 4 GB USB key on my vista machine now, and yes, it runs geat. But its still not faster than my 512MB P4 2.6ghz Edgy machine. 

ReadyBoost is a great marketing ploy. But not appropriate in Linux. But if you think so, maybe you can also work on a way to seamlessly integrate the great [_MS Agents_]("http://www.microsoft.com/msagent/default.asp") into your Linux desktop, too! :)

---

### Post by shizeon on 2007-04-06
See that is the confusion I think.   Readyboost has little do with memory management or swap (please correct if wrong), it is a disk cache.  Granted it 'might' do some cacheing of your swap file, but it is more general purpose.  File system access is going to be more or less the same in linux as it is in VIsta (without readyboost).  The bottleneck is the seek time on your HD.   So the question , is there a way to cache disk access (with RAM, Flash, anything) in Linux to speed up disk access to frequently used files transparently?  Does linux's memory management already do this for us?  Seeing as a 4 gb stick of flash is less than < 100 bucks but 4gb of RAM is around 400, I still think this is a great idea wither it came from MS or not..  Wouldn't any system  benefit from this, especially a laptop with an older high latency seek.   I've just gleamed some of this info from google searches so I may be way off base :)

MS Agents would be great, doesn't everyone want that !!!  (major sarcasm here) :)

---

### Post by alexandrul on 2007-04-06
AFAIK, in certain conditions, a portion of the video card RAM can be used as a swap space, and it is VERY FAST, even on low cost models.

---

### Post by blue_Sphere on 2007-04-08
> **shizeon said:**
> See that is the confusion I think.   Readyboost has little do with memory management or swap (please correct if wrong), it is a disk cache.  Granted it 'might' do some cacheing of your swap file, but it is more general purpose.  File system access is going to be more or less the same in linux as it is in VIsta (without readyboost).  The bottleneck is the seek time on your HD.   So the question , is there a way to cache disk access (with RAM, Flash, anything) in Linux to speed up disk access to frequently used files transparently?  Does linux's memory management already do this for us?  Seeing as a 4 gb stick of flash is less than < 100 bucks but 4gb of RAM is around 400, I still think this is a great idea wither it came from MS or not..  Wouldn't any system  benefit from this, especially a laptop with an older high latency seek.   I've just gleamed some of this info from google searches so I may be way off base :)

MS Agents would be great, doesn't everyone want that !!!  (major sarcasm here) :)

I was under the impression that cache and swap space were the same? Am I missing something? If you are right I would also like to know if caching is possible in linux...

---

### Post by blue_Sphere on 2007-04-09
bump

---

### Post by shizeon on 2007-04-09
Not an expert, but here is how I understand it.  SWAP is an extension of your RAM on to disk.  Disk Cache would be a copy of some of your Disk in to memory (RAM, FLASH, etc).  So say you are running 50 firefox windows that consume 512MB of Ram and only have 128MB ram.   The system would use swap to allow it to work, but it's going to be slow.   

I think putting swap on flash (this thread) might help performance for this scenario, since the swap wouldn't be going to slow disk anymore.

Now in my situation, I have a slow hard drive, but decent amount of RAM.  I rarely swap out on day to day activities.  Linux memory management does have some kind of file cache (buffers) built in to use RAM, but it dynamically shrinks and only will use main memory, not swap. Just googling around, I haven't found much in the way of configuring the built in disk buffers to act any differently.  

An idea I was tossing around was to put some of the file system mounts on flash, like /lib, /usr/lib , /usr/bin maybe.   These are mostly read-only and small files so would benefit from a faster seek than a faster transfer rate (I think?).  Since most linux programs are dynamically linked the hope would be that applications startup faster.  System would die horribly if the flash was removed though and would not be as dynamic as a general purpose flash based disk cache would be.  

Looks like some HD manufacturers are jumping on the band wagon too of flash assisted disk, so maybe this will gain more traction/support soon. 

[http://www.reghardware.co.uk/2007/03/07/samsung_ships_hybrid_hdd/](http://www.reghardware.co.uk/2007/03/07/samsung_ships_hybrid_hdd/)
[http://www.tfot.info/content/view/83/59/](http://www.tfot.info/content/view/83/59/)

---

### Post by Jach on 2007-04-14
Before you start adding swap, try running the "free -m" command to see if you even need it.

I read a related topic on this subject, but it was more on how to make a FILE on your hard drive itself become swap, rather than a flash drive. (Much more useful in my opinion.) The full thread can be found here:

[http://ubuntuforums.org/showthread.php?t=89782](http://ubuntuforums.org/showthread.php?t=89782) (See the third post down.)

---

### Post by talcite on 2007-04-14
This question was asked earlier in the thread so I might as well answer it now. 

"Will the readyboost/swap end up shortening the lifespan of your flash drive?" and also "readyboost claims ... 10 years life span" 

I guess there aren't too many hardware guys on the forum =P

Firstly, technically yes the lifespan of the flash drive will decrease. But... it will only decrease about as much as overclocking will shorten the lifespan of your CPU =P. In other words, no it will not shorten it to any meaningful extent. 

Although flash memory can only be written a few thousand times in a sector before it dies, all modern flash memory now uses algorithms to "spread" the writes over different sectors. The end result is a very long lifespan for the flash memory. 

This "spreading" is done through HARDWARE... i.e. Vista can do nothing to increase/decrease the lifespan. The only thing it can do is prevent things from being written to the drive... but then why have a drive in the first place?

Plus, on top of all this... most flash drives have a lifetime warranty, and they're dirt cheap =D.

---

### Post by blue_Sphere on 2007-04-19
Well thats good to hear about flash memory life! I will definitely use it then. 

Does anyone know the best way to cache the hard drive onto flash? I know some people were mentioning that certain folders would help. 

> 
From what I read, Vista's readyboost isn't making use of the flash drive for swap. It is using it as a disk cache for frequently accessed files. There is a difference if I understand this all correctly. A (slightly stretched) example would be if a program needs to open a specific image over and over again. If I was running vista, the program would automatically make use of the disk cache provided by readyboost and load it directly from flash. Placing the swap file on flash wouldn't provide any speed up here.

An idea I was tossing around was to put some of the file system mounts on flash, like /lib, /usr/lib , /usr/bin maybe. These are mostly read-only and small files so would benefit from a faster seek than a faster transfer rate (I think?). Since most linux programs are dynamically linked the hope would be that applications startup faster. System would die horribly if the flash was removed though and would not be as dynamic as a general purpose flash based disk cache would be. 

Question is, can we do something similar on Linux to transparently cache disk access?

---

### Post by PingunZ on 2007-04-19
Can I do that with my 20gb iPod, I'm not using it currently .. xD

---

### Post by blue_Sphere on 2007-04-20
Why would you want to put cache on your ipod? I imagine your harddrive would be faster. This idea should speed up the system if a faster read card is used. An Ipod would be a bad idea IMHO.

---

### Post by julian67 on 2007-04-20
This doesn't seem like a worthwhile way to use USB flash and is unlikely to do anything except degrade system performance.  Cheap USB drives have been suggested several times but usually their read and especially write performance is awful. Really good quality ones with fast read/write are not cheap and it would be better to spend the money on some more DDR RAM which *is* cheap and much much faster than any HDD or USB flash memory.

---

### Post by zsouthboy on 2007-04-20
It would be interesting to use this SD slot on my laptop for say, a 4gig card. Leave it in all the time.

Some way to profile the 4 most accessed gigs by the system, and then automatically copy that information to the card/drive, then simultaneously reading data from your hdd and flash at the same time, ala RAID.

Is it possible to log hdd accesses (with specifics, too)?
Then someone would have to write a kernel driver to manage this..

large sticks of system memory are still too damn expensive - in my case, it's $100 for 2 x 1gb, OR $400 for 2 x 2gb sticks. Dammit. :(

I will probably break down and grab them anyway. 

I'd still like to augment my (especially laptop drives are slow) slow HDD with faster seek flash, even with the additional mem.

---

### Post by blue_Sphere on 2007-04-22
Yeah I have to say it does work. When I was running vista it substantially increased the speed of the OS, with just a 512mb card. I have 2gb of ram anyway and just wanted to try it. 

It was the only "Wow" in vista that I ever saw :(. I would really like to see a linux version.

---

### Post by celticbhoy on 2007-06-05
Can this be used with a no longer want flash mp3 player ?

when it automounts, it shows as a music player, but when unmounted it shows as a USB flassh disk, and if this is possible how will it work with the how-to above. I already gave it a quick go, but I dont know how to find the device setting for it.

---

### Post by celticbhoy on 2007-06-05
Forgot to say, in /media I have

cdrom  cdrom0  General  sda1  sda2  usbdisk

The General refers to an SD card.

---

### Post by julian67 on 2007-06-05
> **blue_Sphere said:**
> Yeah I have to say it does work. 


You have to measure it and demonstrate your measurements are accurate or your statement evidences nothing but placebo effect.

---

### Post by sguart on 2007-06-05
> **julian67 said:**
> You have to measure it and demonstrate your measurements are accurate or your statement evidences nothing but placebo effect.

i think there was some performance measurement that website has already conducted on this. I think it's ExtremeTech but I don't remember the link to the article. 

Pretty much their conclusion is that, adding 1gig additional ram does way more performance-wise then any amount of readyboost memory(max 4gb)

Also, the effect of readyboost greatly diminishes when you have above 1.5gb of ram.  It's surprising for the previous poster with 2gb of ram and 512mb of readyboost to have a wow moment. Maybe that 512mb has super low seek time and very fast write time.

Personally, with 2gb of ram and 2gb of sandisk ultra 2 for readyboost, the gain is barely noticable. With 4gb of readyboost, it is little more pronouced.

I think the OP's idea will only benefit people that has low amount of RAM. If you are hardly swapping already because you have sufficient amount of RAM, extending your swap space onto the flash drive will not benefit in any way.

linux memory management is already sorta doing this readyboost all the time, provided you have extra ram. the kernel will occupy unused ram and use it as buffer/cache to speed things up. that's why u need to account for the memory used up by buffers and cache when you try to determine free memory under linux.

---

### Post by julian67 on 2007-06-05
Anyone who has  a low amount of RAM and enough money to buy a flash stick has enough money to buy real RAM. A couple of weeks ago I bought 1 GB of Kingston DDR2 667 for 1500 Thai Baht. A 1 GB USB flash USB Kingston (probably fake, usually is in fact locally made Samsung) costs  around 1000 Baht.  

500.00 THB = 15.2010 USD
500.00 THB = 7.61943 GBP
500.00 THB = 11.2379 EUR

I didn't check the price of 512MB DDR2 but it's plain that it won't be too far from  the price of 1GB flash memory. It will make a massive difference to the typical budget PC that was sold with 256 or even 128 on board whereas the USB flash memory will make only a small difference and anyway might die prematurely from being constantly written to. 

It's really hard to see how it makes sense to use USB flash memory in this way except under very odd circumstances i.e. someone who already posesses a PC with low memory but strangely has a very high speed USB flash drive but doesn't have $20.

---

### Post by adampyre on 2007-06-06
This is cool. I don't know why I didn't think of it before! It really helps with my laptop that only has 256 MB of ram (the ram for it is hard to find and expensive but I would love to upgrade it.) In the meantime using my pendrive helps! 

I DO HAVE A QUESTION THOUGH!!!!!!!

Is there a way to cascade the systems memory usage? Please read the following oh intelligent ones and tell me if I am going about this the right way:

I followed the tutorial about mounting my pendrive as swap space and then I turned of the HD swap space hoping it would speed things up. I have, 256 MB RAM, 512 MB pendrive all dedicated as swap, and 500 MB HD Partition that was dedicated as swap, but I turned it off to force the system to use my pendrive as a swap.

Would it be worth it, to turn the HD swap back on and possibly even make my system "cascade" it's memory usage? What I mean is, use the ram, once ram is full, go to pendrive. Once ram and pendrive are both full, then go to HD. Once all three are full, oh well...

Anyway, is there a way to do this? I have been plaing around with swappiness, should I set this to a certain number? What else do I do to figure this out? Thanks!

---

### Post by t4thfavor on 2007-06-08
I was looking into swap on flash for linux due to the rediculous prices on rdram. I have an ipcop fw that is running content filter and squid proxy cache. The system only has 128mb of ram, which is getting slightly over used from what the graphs tell me.  

I decided to add a flash drive to it for swap. This thread helped me do that. What I was wondering is on a usb 1.1 interface, will it actually help?

Also I tried it out on my feisty laptop, and it seems to not help (I have 1.5GB ram:). I opened everything I could and still could not even come close to filling the ram to force the system to swap.

chance@nc6220:/media$ free -m
             total       used       free     shared    buffers     cached
Mem:  1511       1254        257    0              231           480
-/+ buffers/cache:             542    969
Swap:   746          0            746
hmmm:(

---

### Post by max.durden on 2007-06-20
I adampyre, 
if i've well understood your problem, you can get what you want by simply setting a pertinent "swap priority" ['-p' parameter] on the used swap devices. In example, to get the usb pen-drive to be consumed before the hd swap space, you should simply set the priority for usb swap to be higher than the priority for hd-swap.

Please let me know if the solution works!

---

### Post by maestrobwh1 on 2007-08-03
I have a very old laptop, fujitsu 770 with PI 200 MMX with maxed out ram.  It also has 1 usb 1.1 port.

I formatted a 512 usb as a swap drive using gparted (the whole thing and I probably only need to use half of this but at the current prices, who cares).  I added pri=1 to this device in fstab, and then pri=0 to my hd swap.  I don't know if I notice a performance boost in speed, but I do notice that the HD can take a rest.

Considering that the HD is ATA 33 (gasp), and the usb port is 1.1, they probably even out in speed, although I guess technically usb 1.1 is 12 MBPS and ata 33 can be anywhere from 20 something MBPS down to around that...

The performance boost seems to come from the fact that now the HD is only seeking data for apps and is not being used for memory.

Does my speed for ATA 33 seem correct?

---

### Post by MTZeon on 2007-08-16
> **t4thfavor said:**
> I was looking into swap on flash for linux due to the rediculous prices on rdram. I have an ipcop fw that is running content filter and squid proxy cache. The system only has 128mb of ram, which is getting slightly over used from what the graphs tell me.  

I decided to add a flash drive to it for swap. This thread helped me do that. What I was wondering is on a usb 1.1 interface, will it actually help?

Also I tried it out on my feisty laptop, and it seems to not help (I have 1.5GB ram:). I opened everything I could and still could not even come close to filling the ram to force the system to swap.

chance@nc6220:/media$ free -m
             total       used       free     shared    buffers     cached
Mem:  1511       1254        257    0              231           480
-/+ buffers/cache:             542    969
Swap:   746          0            746
hmmm:(
That only demonstrates that linux is way more efficient on memory managment than Windows is!

Hurra!

---

### Post by maestrobwh1 on 2007-08-16
Its true.  Even running compiz-fusion on my desktop computer, I don't even need the swap.  I accidentally deactivated it when I moved it to the end of my disk, changing the uuid and I forgot to go back into fstab and fix it.  Noticed at some point way later that it was not automatically turned on.  I do have 2 GB ram, but I know that XP still uses its own swapfile b/d of the HD action during use.

I did notice on my old Fujitsu PII 200mmx with 96 MB ram that after I made a pen drive at sda1 be my priority swap over the hd swap, that the battery lasted longer and there seemed to be a marginal performance gain and a lot less HD action once programs loaded.  That is only with usb 1.1.

---

### Post by dj chainz on 2007-08-21
In response to this I have created a shell script which allows you to quickly swapon/swapoff a swap partition; perhaps in future it will also allow you to create the swap partition, which must for now be done with [FONT="Courier New"]gparted[/FONT].  It runs with a (gnome) GUI and so can be used outside of the terminal; run it once to select and **swapon** a partition, run it again to **swapoff** the partition you used before.

It uses the UUID of the partition and so should survive hibernate on laptops.  It needs to be run with superuser privileges so I recommend your menu entry/panel link should use the command [FONT="Courier New"]gksudo /pathtoscript/flashswap.sh[/FONT]  (of course replacing /pathtoscript/ with the path to the script).

Find attached :wink:

EDIT: It doesn't survive hibernation or standby; the disk gets unmounted/de-activated so that when it recovers ubuntu labels the drive as a new one, e.g. /dev/sdc instead of /dev/sda beforehand.  Despite mounting it via /dev/disk/by-uuid/..

---

### Post by DJRumpy on 2007-10-22
The mis-information in this thread is astounding. 

ReadyBoost has absolutely no relation to the amount of memory in your PC. Adding a 1 gig MicroSD card to a PC with 256 megs of ram will not make it run like a PC with a gig of ram. The amount of ram you have also doesn't affect how well ReadyBoost works, as the boost cache holds only data read off the hard drive, not data that's in memory.

It has no relation to the swap file as swap file data isn't typically the type of often read data that is cached. Windows (and Linux) both swap data to the swap file for inactive programs/threads and low priority/older threads when memory is low. That type of data wouldn't be useful in a disk cache.

ReadyBoost serves only one purpose. It is used as a secondary cache to your hard drives internal cache. Most hard drives have an internal 8 MB or 16 MB cache. ReadyBoost essentially helps to speed up your system by acting as a secondary cache so that your hard drive doesn't have to keep re-reading the same, often used files and data. Since memory seek times are MUCH faster than the physical seek time of your hard drive (typcially < 1 Millisecond where a physical hard drives range seek times range in the 4 - 20 MS range), you can see a nice performance perk from it.

If the data it needs from the hard drive exists on the thumb drive/SD card/etc, it will pull it from there, rather than from the hard drive. Just like your Internet Browser's cache is must faster than re-downloading content from the internet. Same principal.

You should not put a swap file on a USB or a thumb drive. Although the seek time is usually great (varies greatly according to the quality of the card you have) for a MicroSD, Compaq flash or other decent quality memory cards, the max throughput and random write times tend to leave MUCH to be desired (read, it's probably FAR slower than your internal hard drive). That is why it works well as a read only disk cache but not as a swap file. ReadyBoost is strictly read only. It is not used to write pages in memory back to disk.

Folks with older (slower) hard drives would see the greatest benefit, as well as those who's hard drives end up accessing a lot of the same data over and over again (common system files for instance). Apps like browsers and e-mail tend to launch faster and general GUI tasks tend to be snappier.

It works on the same principal as the internal cache in your CPU. Nothing more nothing less.

I'm rather surprised no one else though of it. M$ is typically the last one to think up a good idea. They usually just buy everyone else's idea's and claim it was theirs ;)

---

### Post by marstein on 2007-10-22
> **DJRumpy said:**
> The mis-information in this thread is astounding. 


Correct. To clarify - only files that are non-contiguous on the hard drive read faster from flash memory. Harddisks today have upto 60 MB/s thoughput while flash drives have only around 20MB/s. The flash drive shines when the drive head has to move a lot.

---

### Post by DJRumpy on 2007-10-22
Actually that's not quite true. Even a small contiguous file on the HD would be read faster from the ReadyBoost cache.  It's all about seek times. Solid state memory that is ReadyBoost compatible has excellent seek times (typically less than a millisecond) while hard drives are far worse in that area because of the time it takes to move the heads around on the platters.

Even the fastest server scsi drives rarely approach 4 milliseconds. Typical sata/ata drives on desktops and laptops are far slower. ReadyBoost is optimized for 4K blocks. Very small files. It probably doesn't even bother to cache large files that are read from the drive as it's max throughput would make that a poor performance choice. It's a very nice piece of code in it's simplicity.

For instance the one I use that is readyboost compatible only has about 4 MB/s throughput. Not anywhere near to a hard drives performance, but it's seek time is .8 milliseconds, compared to my laptop's 7200 RPM hard drive which has an average seek time of about 14 milliseconds.

---

### Post by maestrobwh1 on 2007-10-23
On a 200 MMX PII laptop machine with an ata 33 drive, making an additonal swapfile on a pen drive, and setting the priority to 0 in fstab, and making the hard disk swap as 1, there was a noticible improvement in speed, and a drastic improvement in battery life and hard drive activity.

That old machine usually runs Puppy Linux, but the Xubuntu does run okay if one is just doing internet stuff.

I understand it is not the same concept as ready boost, but for anyone who finds this, they might want to wonder.  I would say that for anyone with more advanced hardware, the gain would be marginal, or detrimental.

---

### Post by julian67 on 2007-10-23
> **DJRumpy said:**
> The mis-information in this thread is astounding. 

.................blah blah blah.........

Folks with older (slower) hard drives would see the greatest benefit, as well as those who's hard drives end up accessing a lot of the same data over and over again (common system files for instance).

And where are these PCs which simultaneously have old drives with tiny caches but nonetheless are capable of running  Vista???? Even if they do exist wtf are people doing running Vista on them???? The solution to the appalling performance is not to spend more money or sacrifice an otherwise useful piece of hardware, the solution is to roll back to XP or 2000 or use a Free OS. Seriously if I was a Win XP user with an older PC would I be better off spending $200 on Vista or $200 on RAM? That question makes things a little clearer I think. 

The wholesale swallowing of MS marketing nonsense in this thread is astounding.

---

### Post by DJRumpy on 2007-10-23
That kinda of Linux fanboy hype isn't very useful. This is a discussion. Not a linux commercial. I think we all appreciate Linux since we're all in the thread here asking for a Linux version of it, no? Your preaching to the choir. M$ does come up with a good idea every few years. Give credit where credit is due and ease up of the fanaticism.

---

### Post by julian67 on 2007-10-24
> **DJRumpy said:**
> That kinda of Linux fanboy hype isn't very useful. This is a discussion. Not a linux commercial. I think we all appreciate Linux since we're all in the thread here asking for a Linux version of it, no? Your preaching to the choir. M$ does come up with a good idea every few years. Give credit where credit is due and ease up of the fanaticism.

If you come in with an attitude you might be receiving some isn't it? ;-)

Call me a fanboy  or fanatic if you like but  what I said was actually > the solution is to *roll back to XP or 2000* or use a Free OS. not "everybody must use Linux"! or "MS sucks" or similar.

Maybe MS do come up with good ideas but the point stands that ReadyBoost, working as described, is mostly useful on PCs that aren't suited to the OS anyway and the money spent on Vista and a USB flash drive would be better off spent on RAM, a new HDD or even a cheap PC  like this one [http://store.madtux.org/product_info.php?cPath=57&products_id=311]("http://store.madtux.org/product_info.php?cPath=57&products_id=311"). I would hope that any PC supplied with Vista pre-installed would not be fitted out with such old hardware that ReadyBoost would be needed. It seems ReadyBoost can only really benefit people who *buy* the OS and try to use it on older/cheaper hardware and that's why I think the money is better spent elsewhere. So I'm not questioning the inventiveness or talent of MS people but am really struggling to see ReadyBoost as useful feature. It seems to be mostly marketing, and it certainly featured very heavily in the launch publicity and marketing of Vista. Here's what MS say about ReadyBoost: > Adding system memory (typically referred to as RAM) is often the best way to improve a PC's performance, since more memory means more applications are ready to run without accessing the hard drive. However, upgrading memory can be difficult and costly, and some machines have limited memory expansion capabilities, making it impossible to add RAM.   Windows Vista introduces Windows ReadyBoost, a new concept in adding memory to a system. You can use non-volatile flash memory, such as that on a universal serial bus (USB) flash drive, to improve performance without having to add additional memory "under the hood."

The clear implication is that you're better of buying more RAM but if your computer sucks use ReadyBoost, whereas most people outside of MS will say if your computer sucks don't even think about using Vista.

---

### Post by DJRumpy on 2007-10-24
Actually, that's not true either. These memory cards are far faster with seek times than any hard drive current on the market (except for a solid state hard drive and those are still prohibitively expensive). Even a cutting edge PC will benefit. Again, it has nothing to do with how fast a pc is due to ram, video, or cpu. It's all about hard drive cache, and even current hard drives are slow in comparison to solid state seek times.

Hard drives have historically always had a small cache (4, 8, or in the latest ones, only 16 MB). Only hybrid drives come with the kind of memory you get with an SD card and hybrid drives are a brand new invention.

The vast majority of IDE and SATA drives out there have a sad 8 MB of memory cache and they would benefit from ReadyBoost as a result.

The fact is you can buy 2 gigs of SD for 20-30 bucks, while the same ram for your PC costs many times more. It's a very cheap and easy boost to a PC's performance. As i said, give credit where credit is due. They do sometimes get things right ;)

---

### Post by maestrobwh1 on 2007-10-24
Or spend nothing on kubuntu with compiz fusion...

---

### Post by cdean on 2007-10-24
On a side note, BIOSLEVEL did a fun thing using two flash drives in RAID. This could be extended to use the RAIDed drives as a swap for even more speed gains.

[http://www.bioslevel.com/index.php/reviews/aid/1190315496](http://www.bioslevel.com/index.php/reviews/aid/1190315496)

---

### Post by julian67 on 2007-10-24
> **DJRumpy said:**
> Actually, that's not true either. These memory cards are far faster with seek times than any hard drive current on the market (except for a solid state hard drive and those are still prohibitively expensive). Even a cutting edge PC will benefit. Again, it has nothing to do with how fast a pc is due to ram, video, or cpu. It's all about hard drive cache, and even current hard drives are slow in comparison to solid state seek times.

Hard drives have historically always had a small cache (4, 8, or in the latest ones, only 16 MB). Only hybrid drives come with the kind of memory you get with an SD card and hybrid drives are a brand new invention.

The vast majority of IDE and SATA drives out there have a sad 8 MB of memory cache and they would benefit from ReadyBoost as a result.

The fact is you can buy 2 gigs of SD for 20-30 bucks, while the same ram for your PC costs many times more. It's a very cheap and easy boost to a PC's performance. As i said, give credit where credit is due. They do sometimes get things right ;)

Here it is again from Microsoft > Adding system memory (typically referred to as RAM) is often the best way to improve a PC's performance, since more memory means more applications are ready to run without accessing the hard drive

You differ from MS in that *they recommend more RAM* as the preferred method to upgrade, with ReadyBoost being suggested as an alternative if this is not possible. It's right there in b+w. 

There are no figures to suggest that a drive with 8MB cache will necessarily benefit. Until recently (this year?!) 8MB cache was not considered "sad" but the peak of performance. I have plenty of drives with smaller caches. and only the one I bought this year has 16MB cache. Calling drives with 8MB cache "sad" is pretty desperate.  The hardware shouldn't be blamed if the OS can't extract the same performance from it as previous or different OS manage. 

Who is the fanboy and a fanatic? 

It's still plain that $100 or $200 spent on moving a PC from 2000 or XP to Vista would be better spent on RAM.  I'm with Microsoft on this one ;-)

---

### Post by DJRumpy on 2007-10-24
I never said more ram is a bad thing. That is true for any platform, including Linux. I said that ReadyBoost is a very cheap way to increase performance.

8MB is sad considering how cheap memory is these days, as is 16. Hard drives are easily one of the biggest bottlenecks on today's PC. I've always wondered why they don't use a bigger cache. I would hardly call that 'desperate'. It's actually called an opinion.

You obviously have me confused as a fanboy because I refuse to scream fowl at anything that is non-linux. I happen to be replying on Kubuntu. I can see how so many folks are turned off from Linux just from this exact kind of response. You imply that people who even deign to use an M$ product are fools. You are trying your damnedest to turn this into yet another pointless OS debate.

That is the one thing I hate about Linux. The people who will slam anything that is non-Linux without a valid reason. THAT is fanaticism.  I said ReadyBoost was a good technology (admittedly so by many other Linux enthusiasts as well. Just Google how many are looking for this tech in Linux). If someone can get a decent performance increase for 20 or 30 bucks, then I would say that's a great deal. If they can get this idea into Linux, even better!

---

### Post by Peacez on 2007-10-24
workss!!:rolleyes:
Filename                                Type            Size    Used    Priority
/dev/hda6                               partition       971892  31320   -1
/dev/sda1                               partition       1006568 0       32767

my RAM already 1GB..my pendrive 1GB..result..1.89GB total

---

### Post by ydrol on 2007-10-27
DJRumpy is right as far as I can tell, 

swap = running out of RAM and storing ***infrequently*** used ***memory*** to a slower larger device. (READ&WRITE)

readyboost = READ-ONLY cache of small ***frequently*** used ***files*** from HD to avoid seeking.

They are two completely different things.

Ideally with RAM so cheap a normal desktop should be swapping much anyway.

I dont use ubuntu,but I just had to register because I'm surprised the discussion has gone on for this long..

---

### Post by scorp123 on 2007-10-27
> **max.durden said:**
>  As a result, the pen drive will be used in the same way windows Vista does through the ReadyBoost functionality. Sorry to say so ... but this is silly. Vista needs this functionality because it is so horribly bloated. With Ubuntu you probably will not even use your swap ever, so this "readyboost on Linux" thing doesn't really make much sense in my humble opinion.

There are better ways to tune your Linux system, e.g. by adjusting the "swappiness" parameter, giving the system enough RAM, proper partitioning, and so on.

Reproducing workarounds Microsoft had to come up with for their horribly bloated "Vista" OS on other operating systems that don't even have the same problems in the first place -- and in any case function in a fundamentally different way -- doesn't make much sense.

That's like living in Hawaii and putting snow-chains on your car's wheels because you heard somewhere they do that in Alaska, Canada, and in cold European countries too. .... But you live in Hawaii. You don't have snow. So why bother with snow-chains?? :)

Same here. Why worry about "readyboost" on Linux?? :biggrin:

---

### Post by DJRumpy on 2007-10-27
Again this has nothing to do with 'bloat'. It simply makes more cache available to your hard drive, which if you must be reminded, was not built or sold by Microsoft.

---

### Post by julian67 on 2007-10-27
> **DJRumpy said:**
> Again this has nothing to do with 'bloat'. It simply makes more cache available to your hard drive, which if you must be reminded, was not built or sold by Microsoft.

There *has* been a lot of confusion here over what exactly ReadyBoost does.  I got more interested and have been reading. Here's something from the Windows Vista Blog. It's written by Jim Allchin, Microsoft's Co-President, Platform and Services Division so I'm going to take his word over everyone else's in this thread > I should be clear that while flash drives do contain memory, Windows ReadyBoost isn’t really using that memory to increase the main system RAM in your computer.  Instead, ReadyBoost uses the flash drive to store information that is being used by the memory manager.  If you are running a lot of applications on a system that has limited memory, *Windows ReadyBoost will use the flash drive to create a copy of virtual memory that is not quite as fast as RAM, but a whole lot faster than going to the hard disk.*   source: [http://windowsvistablog.com/blogs/windowsvista/archive/2006/11/20/windows-readyboost.aspx]("http://windowsvistablog.com/blogs/windowsvista/archive/2006/11/20/windows-readyboost.aspx")

(my italics)

So ReadyBoost is essentially a method to speed up swapping on those systems with inadequate RAM by caching the vm to a faster medium. Inadequate RAM in Vista seems to be 512MB. 

This *is* to do with bloat *and* to do with RAM because if you have plenty of free RAM you have a system that doesn't need to swap and hence does not require the sacrifice of a USB port and your flash memory to gain a remedial speed boost. And the best way to have plenty of free RAM with an "inadequate" 512MB installed is to avoid any OS that can use a GB RAM just to sit idle.

---

### Post by scorp123 on 2007-10-27
> **DJRumpy said:**
> Again this has nothing to do with 'bloat'. It simply makes more cache available to your hard drive, which if you must be reminded, was not built or sold by Microsoft. Linux already does all the caching you'd ever want with unused RAM. That's why I said that giving more RAM to the system can help a great deal. This "readyboost" thing is needed on Vista because Microsoft OS's always did and always do an extremely poor job at this. "readyboost" is nothing but just a marketing gag ... they hide the fact that they had to come up with this because their silly OS can't handle RAM reasonably.

Example from my system right now: ```
:~> free
             total       used       free     shared    buffers     cached
Mem:       1026004    1007220      18784          0      14936     594240
-/+ buffers/cache:     398044     627960
Swap:      1855468      33908    1821560
``` Total RAM on this laptop is 1 GB ... but as you can see only 390 or so MB are really used by the OS and its applications (and I am running Compiz-Fusion here + Azureus is downloading some stuff for me ...), the remaining ~620 MB (from 1024 MB total) are used for disk caching. And I tell you the system feels very very snappy and responsive :)

Linux doesn't need this "readyboost" crap ... all the caching you'd ever might want is already there and happens automagically for you. :D

---

### Post by DJRumpy on 2007-10-27
Marketing Gimick? Do you seriously think anyone is going to drop 200 bucks for an OS based on something as simple as this? Most people, including the author of this utility have virtually no idea as to how it even works. If your thinking MS can actually pull off a marketing coup, you should look at their past marketing performance. They suck ;)

The idea is sound however, otherwise we wouldn't be seeing Hybrid drives making their debut. I don't care how good your memory management is (Vista also fills the system memory with cached data), you can always benefit from dedicated cache. How much do you want to bet that Linux on a hybrid drive runs better than Linux on a standard SATA drive?

---

### Post by julian67 on 2007-10-28
> **DJRumpy said:**
>  Most people, including the author of this utility have virtually no idea as to how it even works.  

You know more about it than the engineers at MS who built it? I don't think so. They have explained very clearly what it is for and how it works. You came into this thread saying > **DJRumpy]The mis-information in this thread is astounding[/quote] and then piled it on high.  

[QUOTE=DJRumpy said:**
> 
 If your thinking MS can actually pull off a marketing coup, you should look at their past marketing performance. They suck ;) 

If there is one area where MS are expert it's marketing and getting their products onto people's hardware.  They sold ME and now they sold Vista. 
 
> **DJRumpy said:**
>  
The idea is sound however, otherwise we wouldn't be seeing Hybrid drives making their debut. I don't care how good your memory management is (Vista also fills the system memory with cached data), you can always benefit from dedicated cache. How much do you want to bet that Linux on a hybrid drive runs better than Linux on a standard SATA drive?

Yes the idea of a bigger faster cache on the HDD is great, I'd like some of those hybrid drives too. But ReadyBoost is not that, it's a way to cache the virtual memory to flash for faster access and it has no useful purpose on an OS that has enough RAM and manages it well.

---

### Post by DJRumpy on 2007-10-28
I don't believe I said at any time that I know more than the engineers at Microsoft. Please point out the relevant thread?

ME was a sad excuse for an operating system, and hardly a blip on the radar. Most people either reverted to 98 or went on to 2000. Even hardcore MS fanboys will tell you that. It was a total failure and a sad hack of an OS.

Do you think the OS just makes up the data it stores in ReadyBoost? Does it just POOF it into existence? Hardly. It reads it from the hard drive and if it fits the profile for ReadyBoost (read: small, often used data), it's kept in memory so that the disk doesn't have to be accessed again.

SWAP is a totally different animal. This type of memory isn't even good at swap specific tasks. It's max throughput is far slower than even the oldest hard drives.  I own a 2 gig 'extreme' SanDisk that is supposed to be a good performer that will barely push out 4MB a second. Even an old ATA 33 drive (which I doubt there are any left alive at this point) would far outperform this type of memory as a swap drive). SWAP stores old, unused data to disk to free up system ram for active threads. Most Linux systems never even use SWAP at this point unless your running some ancient piece of shite that deserves to run like shite.

This utility has nothing to do with ReadyBoost or how it works.

---

### Post by julian67 on 2007-10-28
> **DJRumpy said:**
> I don't believe I said at any time that I know more than the engineers at Microsoft. Please point out the relevant thread?

this thread here 

[quote=you]Most people, including the author of this utility have virtually no idea as to how it even works.[/quote]

Your description of how ReadyBoost works, its purpose, and the circumstances when it might be useful is at odds with the descriptions from Microsoft.  I happen to think their descriptions of their own tool and intention are more reliable.  I won't repeat myself on the usefulness or otherwise of ReadyBoost.

---

### Post by DJRumpy on 2007-10-28
I don't see me mentioning Microsoft in the above thread. Had you actually read it, I was speaking about the author of this utility and the various other folks in here thinking this was a Linux verison of ReadyBoost when it's not even similar. 

lol..have you even USED vista? It hardly crawls. The network stack far outperforms Linux Kubuntu 7.10. It transfers at almost twice the speed of my Linux box. The graphics are also faster due to DirectX.

I just wish they had something similar so that Linux could perform so well as it does so well in other areas. I'm not sure why the wireless transfers are so slow in 7.10. I'm assuming that will come along with a little tweaking.

---

### Post by julian67 on 2007-10-28
> **DJRumpy said:**
> I was speaking about the author of this utility and the various other folks in here thinking this was a Linux verison of ReadyBoost when it's not even similar. 

OK, but that wasn't clear.  But still your assertions about ReadyBoost are not Microsoft's. They have given a very clear description of ReadyBoost. Your opinion/understanding of it obviously is different to theirs. 

> **DJRumpy said:**
> lol..have you even USED vista? It hardly crawls.  

I heard it's pretty fast with Core 2 Duo and 4GB RAM, possibly even approaching the performance level of Xubuntu on Core Duo with 1 GB RAM ;-)  Seriously, you have to specify the hardware and make objective, verifiable,  repeatable tests and measurements for statements like "hardly crawls" to have any meaning.

MS themselves use a PC with 512 MB RAM as an example of a computer with inadequate resources that needs more RAM. They suggest ReadyBoost as a viable but less good alternative to increasing the amount of RAM. That seems clear enough to me.  I'm not making this up, if you follow the links in my earlier posts you can read it on Microsoft's own pages. 


> **DJRumpy said:**
> The network stack far outperforms Linux Kubuntu 7.10. It transfers at almost twice the speed of my Linux box. The graphics are also faster due to DirectX.

Another assertion with no supporting figures or examples. That means it isn't credible. 

> **DJRumpy said:**
> 
I just wish they had something similar so that Linux could perform so well as it does so well in other areas. I'm not sure why the wireless transfers are so slow in 7.10. I'm assuming that will come along with a little tweaking.

It's not good reasoning to think that an apparent problem with your individual install of Kubuntu equates to a universal truth about the merits of Linux networking. 

Your understanding of how ReadyBoost works, its purpose, and the circumstances when it might be useful is at almost completely at odds with the descriptions from Microsoft, and nothing you've said so far persuades me that they are mistaken in anything other than their belief that an OS needing this is worth using. 

That's the nicest way I can think of phrasing it.

---

### Post by DJRumpy on 2007-10-28
Man, the hate for MS must just be tearing you up. Are you so sad that Linux has only a fraction of the market that your fanboyism knows no bounds? No wonder the Windows folks don't want to even go there. I happen to like both OS's as they both have different strengths and weaknesses.

I run Vista and Kubuntu on an older 1 GB non-core duo 32 bit P4. They run very similar except for the fact that Vista actuall loads to the login screen faster than Kubuntu, and the apps open faster. Once you log in, Vista tends to thrash the hard drive with pointless services and such. Once they are both fully loaded, they pretty much feel the same. You should actually try using something before dissing it. 

If you want exact numbers, when I transfer a ripped DVD via wireless connection in Kubuntu to my Media PC from my spankin new Viao using the new 4965 Intel chipset I get 1.2 to 1.5 Mb/s in Linux. Transferring the same file in Vista on a dual-boot machine I get 2.2 to 2.5 Mb/s. Obviously your hate for anything MS will lead you to doubt my word. Why waste my time?

[http://ubuntuforums.org/showthread.php?t=581055](http://ubuntuforums.org/showthread.php?t=581055)

They are obviously having problems with the network stack on the latest release kernels. That above link took all of 5 seconds to find. I don't need to search to see if anyone else is having an issue. This laptop is store bought with standard hardware. If I'm having a problem using a stock install, then undoubtedly someone else is to.

Please enlighten me. Show me where my statements that ReadyBoost is essentially a secondary cache for a hard drive. Show me a statement from Microsoft's site that contradicts my statements.

[http://www.microsoft.com/windows/products/windowsvista/features/details/readyboost.mspx](http://www.microsoft.com/windows/products/windowsvista/features/details/readyboost.mspx)

The above link is directly from the Vista ReadyBoost description, no some blog on the net.

---

### Post by julian67 on 2007-10-28
> **DJRumpy said:**
> Man, the hate for MS must just be tearing you up. Are you so sad that Linux has only a fraction of the market that your fanboyism knows no bounds? No wonder the Windows folks don't want to even go there. I happen to like both OS's as they both have different strengths and weaknesses.

I just thought a post where you present *verifiable* facts, without feeling the need to resort to personal attacks on this forum's users in general and a couple of us in particular would be a refreshing change. . 
> **DJRumpy said:**
> 
I run Vista and Kubuntu on an older 1 GB non-core duo 32 bit P4. They run very similar except for the fact that Vista actuall loads to the login screen faster than Kubuntu, and the apps open faster. Once you log in, Vista tends to thrash the hard drive with pointless services and such. Once they are both fully loaded, they pretty much feel the same. You should actually try using something before dissing it. 

If you want exact numbers, when I transfer a ripped DVD via wireless connection in Kubuntu to my Media PC from my spankin new Viao using the new 4965 Intel chipset I get 1.2 to 1.5 Mb/s in Linux. Transferring the same file in Vista on a dual-boot machine I get 2.2 to 2.5 Mb/s. Obviously your hate for anything MS will lead you to doubt my word. Why waste my time?


An individual experience doesn't equate to a universal truth. I don't hate everything MS, I used to have a great MS keyboard and mouse.   I don't know why you waste your time.

> **DJRumpy said:**
> 
[http://ubuntuforums.org/showthread.php?t=581055](http://ubuntuforums.org/showthread.php?t=581055)

They are obviously having problems with the network stack on the latest release kernels. That above link took all of 5 seconds to find. I don't need to search to see if anyone else is having an issue. This laptop is store bought with standard hardware. If I'm having a problem using a stock install, then undoubtedly someone else is to.

That thread describes a bug in Gutsy. Gutsy does not equal all Linux, it's one version of one distro. Again, a bug in one place does not make a universal truth or rule and there are millions of Linux users who do not have this problem. I tried Gutsy and rolled back to Feisty for other reasons but I had no problem with the wireless performance (using Intel and Zydas adapters). 


> **DJRumpy said:**
> 
Please enlighten me. Show me where my statements that ReadyBoost is essentially a secondary cache for a hard drive. Show me a statement from Microsoft's site that contradicts my statements.

The links are there in my earlier posts if you care to follow them. I still find Microsoft's Co-President, Platform and Services Division to be more credible in this matter than you. I expect he also has better manners. 

> **DJRumpy said:**
> 
[http://www.microsoft.com/windows/products/windowsvista/features/details/readyboost.mspx](http://www.microsoft.com/windows/products/windowsvista/features/details/readyboost.mspx)

The above link is directly from the Vista ReadyBoost description, no some blog on the net.

Yes I posted the exact same link earlier. It mentions that > The flash memory device serves as an additional memory cache—that is, memory that the computer can access much more quickly than it can access data on the hard drive. though it fails to mention that the memory they are talking about caching is a copy of virtual memory. That's explained elsewhere by the gentleman whose department created the tool.  You can read all about it if you follow the links from my previous posts.

I don't see how Microsoft's Co-President, Platform and Services Division's  credibility is lessened by his writing on his official MS blog on windowsvistablog.com. He doesn't contradict anything stated on the MS product info, but offers some more detail.

---

### Post by DJRumpy on 2007-10-28
Again you didn't point out where the MS post discredits anything I have said or in the links you posted for that matter..I also didn't state that I speak for every Linux distribution out there (although Ubuntu is the most popular distribution out there right now, so a good representative). I haven't seen anything you have posted that states fact that anything I have said about ReadyBoost is not true. Actually the personal attack was at you personally, not this forums users. I find your blind faith in Linux and your distrust anything MS rather confusing. I'm not so close minded. I actually like both. I will also question both when the need arises.

Obviously the data read into the SD card is from system memory. Unless they hard wired the SD card's into the hard drive then it would obviously have to go through system memory to get to the card. It certainly won't get there by osmosis. 

I'm done with this discussion. By all means, place your swap on your SD card. Enjoy your blazing performance  (and your MS Keyboard and mouse..lol). You obviously have no experience with Vista and therefore, no room to speak as to it's merits and faults.

I'll continue to wait for the real ReadyBoost in Linux if and when it appears, as I have no plans to go out and buy a new hybrid drive..

---

### Post by scorp123 on 2007-10-28
> **DJRumpy said:**
>  lol..have you even USED vista? It hardly crawls.  Oh yes it does. :lolflag:  Seen it in "action". And funny bugs too, e.g. copying of small files that takes bloody ages, or when the Internet Explorer all of a sudden decides that "drag & drop" between two windows (one being a local folder, the other a network share ...) should no longer be possible (but copying files via command line still works), and so on.

> **DJRumpy said:**
>  The network stack far outperforms Linux Kubuntu 7.10.  You're free to use whatever OS you prefer. But please spare us the M$ propaganda, OK? :)

> **DJRumpy said:**
>  It transfers at almost twice the speed of my Linux box. The graphics are also faster due to DirectX.  Yeah right. Whatever. :)

This entire thread is kinda silly ... Sorry to say so. :roll:

---

### Post by scorp123 on 2007-10-28
> **julian67 said:**
>  Your understanding of how ReadyBoost works, its purpose, and the circumstances when it might be useful is at almost completely at odds with the descriptions from Microsoft, and nothing you've said so far persuades me that they are mistaken in anything other than their belief that an OS needing this is worth using. 

That's the nicest way I can think of phrasing it. Well said =D>

---

### Post by DJRumpy on 2007-10-28
scorp123, those were brilliant debate points... (if you can't tell, I'm being sarcastic here).

 "Yeah right. Whatever."

lol...

I didn't ask if you've **seen** Vista. I asked if you had actually USED Vista. I have to use both OS's as part of my job. The simple truth is it doesn't crawl. It's also the most popular OS on the planet. It obviously has things going for it that Linux does not. If it sucked as bad as you would have it, we wouldn't be having this discussion, no?

I have asked you repeatedly to show me where anything I have posted is contradicted by the Microsoft site or the blog you posted for that matter. Every time you point out some other irrelevant or vague reference to bloat and don't respond with the specific text that contradicts what I've said.

This time around I get from you, an interesting diatribe on bugs in the OS. As if either OS has never experienced them. As to the network speed, I speak from personal experience with Vista, of which you obviously have none. Just because you happen to turn your nose at something without even using it, and then expect me to take your empty arguments with any credibility is just asking too much. Perhaps if or when you ever decide to actually use the OS, we can have a proper debate as to it's merits.

Until then, please continue to spout the typical fanboy Linux propaganda. I'll continue to use both OS's as it suites me.

---

### Post by kerry_s on 2007-10-28
lol, my setups to efficient i can't even get it to dip into swap, my ram just go's up and down. :lolflag:

450mhz
256ram 
20gig hd 4200rpm

---

### Post by DJRumpy on 2007-10-28
On that I agree entirely. Vista (and XP) sucks when it comes to memory management. I don't even use a swap partition on my Linux boot. It's entirely unnecessary. I think MS has just gotten into the lazy habit of throwing more system ram at everything rather than coding tightly.

---

### Post by cjpetrie on 2007-10-28
Hi, could you please help this noobi with the actual invocation?

petrie@symantha:~$ sudo mkswap /dev/sda1 
Password:
Setting up swapspace version 1, size = 2062528 kB
no label, UUID=eccca030-02f7-4abd-96b2-5f105005a3a5
petrie@symantha:~$ sudo swapon -p 32767 /dev/sda1
swapon: /dev/sda1: Invalid argument

If it is that the device is not really /dev/sda1, could you please
point me to how to learn what it really is?

Thanks, Charles

---

### Post by kerry_s on 2007-10-28
> **cjpetrie said:**
> Hi, could you please help this noobi with the actual invocation?

petrie@symantha:~$ sudo mkswap /dev/sda1 
Password:
Setting up swapspace version 1, size = 2062528 kB
no label, UUID=eccca030-02f7-4abd-96b2-5f105005a3a5
petrie@symantha:~$ sudo swapon -p 32767 /dev/sda1
swapon: /dev/sda1: Invalid argument

If it is that the device is not really /dev/sda1, could you please
point me to how to learn what it really is?

Thanks, Charles

**sudo fdisk -l**
should tell you

---

### Post by scorp123 on 2007-10-28
> **DJRumpy said:**
>  I didn't ask if you've **seen** Vista. I asked if you had actually USED Vista.  We're a very very UNIX-centric place and Microsoft is outright banned in most of our subnets anyway :)

The only time we see Vista is on new laptops or desktops (from e.g. HP) when we BS around with it ... before we kill Vista and replace it with something "UNIX-like". 

Have I used Vista??? Why would I even want or need to? It's an inferior crap OS I don't care about the least little bit. :lolflag:

> **DJRumpy said:**
>   I have to use both OS's as part of my job.  You have my sympathy then.

> **DJRumpy said:**
>   The simple truth is it doesn't crawl.  The simple truth is: None of us here cares :lolflag: ... And it *does* crawl compared to the others if you look at the hardware specs that are needed to have Vista run with a decent speed, especially if you turn on all the "Aero" effects (or whatever they are called). But if you feel like using Vista because you perceive it to be "better": Please do so. Just leave us alone then, OK? :)

> **DJRumpy said:**
>   It's also the most popular OS on the planet.  And cow dung is the most popular food amongst certain types of flies. But I am not a fly, so I don't really care how popular cow dung as a food source is. Not the least bit. Same goes for Vista. I don't care how "popular" or unpopular it is. I don't need it. I don't use it. I have Linux and that's all I want. And Solaris on many of my servers.

> **DJRumpy said:**
>  It obviously has things going for it that Linux does not.  For you maybe. For me it offers nothing of value and I will not use it.

> **DJRumpy said:**
>  If it sucked as bad as you would have it, we wouldn't be having this discussion, no?  We wouldn't have this discussion if you just packed up and left this forum and spread your Pro-Microsoft propaganda somewhere else.

> **DJRumpy said:**
>  I have asked you repeatedly to show me where anything I have posted is contradicted by the Microsoft site or the blog you posted for that matter.  We don't need those stupid workarounds Microsoft had to come up with on their bloated crappy OS. Get that into your head. :grin:

> **DJRumpy said:**
>  This time around I get from you, an interesting diatribe on bugs in the OS.  Seen those bugs in action when we fired up a brand-new HP laptop. One of the guys asked  to copy the HP-branded wallpapers those laptops ship with to a network share. There is a whole sub-directory full with those, and I agree, they really look nice. Kudos to HP for shipping such great wallpapers :) So we booted into Vista (because we were curious) and we wanted to copy those files to a network share. That's when we ran into those symptoms. Copying even small files took bloody ages (and if you Google around you will find many stories confirming this as being one of the most annoying bugs Vista has); and drag & drop was all of a sudden no longer possible, no idea why. Not that we really care. We tried the command line and there copying stuff worked without problems. After the files were copied all the Vista crap was deleted and replaced with a Debian-based corporate desktop installation our users receive around here. End of the story.

> **DJRumpy said:**
>  As to the network speed, I speak from personal experience with Vista, of which you obviously have none.  Whatever works best for you. But as I sad above: Please spare us the Microsoft propaganda. If you think Vista is great and you want to use it ... fine. Go ahead and use it.

> **DJRumpy said:**
>  Perhaps if or when you ever decide to actually use the OS, we can have a proper debate as to it's merits.  Merits???? ROFL.

> **DJRumpy said:**
>  Until then, please continue to spout the typical fanboy Linux propaganda. Ah, and that from a Microsoft fanboy ... :lolflag:  But at least I actually am on a Linux forum. I don't go to Microsoft forums and get on people's nerves with "propaganda" as you do around here. Food for thought .... :-)

---

### Post by julian67 on 2007-10-28
...was just on the tip of my tongue....

---

### Post by ydrol on 2007-10-29
Looks like, based on earlier descriptions, I was giving ReadyBoost way too much credit.. 

It does seem to be an 'intelligent' cache of some of the page file, and necessitated in part by more demand on the page file (bloat)..

[http://blogs.msdn.com/tomarcher/archive/2006/06/02/615199.aspx](http://blogs.msdn.com/tomarcher/archive/2006/06/02/615199.aspx)

"Overall, as many posters have pointed out, the feature is designed to improve small random I/O for people who lack the expansion slots, money, and or technical expertise to add additional RAM. As y&#8217;all know, adding RAM is still the best way to relieve memory pressure."

It is NOT as I first was lead to believe, an intelligent cache for the Hard Drive. 

Apologies.

---

### Post by DJRumpy on 2007-10-29
Vista pre-fills sytem ram with data it sees that you use most often or it thinks you may need. Linux uses a similar system with preload daemon/caching techniques. If you have sufficient system ram, then it's unlikely it would utilize the ReadyBoost device. With 2 gigs, it pre-fills about a gig of that on my PC. 

If you run low on system memory, it writes often used data to the ReadyBoost device so that it doesn't have to re-read it from the hard drive.

It doesn't involve the swap file.

---

### Post by cyberfella on 2007-12-18
a moderator should go back through this thread and clear out the peeing contest between these two, and remove my posting here too - it's equally pointless.  

whilst technically its possible to use flash memory for swap space etc on linux, you're really not going to need to do it.   minimal benefits if any, and hammering reads and writes to flash mem is just gonna kill it in time.  

what you gonna do when it dies?  replace it at more expense?  nah, i dont think so.  see how much swapping you've got going on if you're using 512Mb, and decide whether a 1Gb upgrade is necessary or not, and go with your decision.

i've just seen a 1.7Ghz dual core laptop with 1Gb ram and 2Gb readyboost running like a three legged dog.  My 1.5GHz centrino with 1Gb ram whoops it hands down, every day of the week, no argument.  This isn't fanboyism - it's purely an observation.  All OSes are a work in progress at all times.  No OS is or will ever be perfect.  pay your money and take your choice.

---

### Post by scorp123 on 2007-12-18
> **cyberfella said:**
>  whilst technically its possible to use flash memory for swap space etc on linux, you're really not going to need to do it.   minimal benefits if any, and hammering reads and writes to flash mem is just gonna kill it in time.  Amen.

---

### Post by lespaul_rentals on 2008-01-09
Thank you!  :D

I have a 4 GB flash drive, so this will be fun to try out.  :popcorn:

EDIT: Oh, and to all those people out there who says this is a bad idea because of limited number of writes, don't worry about that.  I think the average flash drive has 1 million writes, and they are so cheap these days it doesn't matter.

---

### Post by scorp123 on 2008-01-09
> **lespaul_rentals said:**
>  I have a 4 GB flash drive, so this will be fun to try out.  You realise that this is a totally pointless exercise? 

Similar threads + postings:

"I can't imagine that the performance benefit is really that great. I'm not sure that the effort required to implement it would be worth it" -- RAOF (Ubuntu Developer) ... posted here:
[http://ubuntuforums.org/showthread.php?p=1236270&#post1236270](http://ubuntuforums.org/showthread.php?p=1236270&#post1236270)

"It doesn't work"
[http://ubuntuforums.org/showpost.php?p=3182697&postcount=4](http://ubuntuforums.org/showpost.php?p=3182697&postcount=4)

"hardly any speed difference"
[http://ubuntuforums.org/showpost.php?p=2930319&postcount=10](http://ubuntuforums.org/showpost.php?p=2930319&postcount=10)


So you can save yourself the hassles, it won't make any noticeable difference.

A Linux system with a reasonable amount of RAM won't even use the swap at all.

---

### Post by lespaul_rentals on 2008-01-09
I want to try it out for fun, and for the sake of learning how Ubuntu associates devices with swap.  God forbid I try something new!

---

### Post by PinkFloyd102489 on 2008-01-09
Ive got a 16GB flash drive on my Zen. I might use it. :-p

---

### Post by scorp123 on 2008-01-09
> **lespaul_rentals said:**
> I want to try it out for fun, and for the sake of learning how Ubuntu associates devices with swap.  God forbid I try something new! You got me wrong there. This "ReadyBoost" thing is a workaround that Microsoft had to come up with to address a few serious flaws in Vista. Only that even on Vista it doesn't really help that much (see the links that I posted above).

To reproduce "ReadyBoost" on Ubuntu is kinda totally useless. First of all Ubuntu doesn't have the same problems there, so why implement this workaround if your OS isn't even suffering from the same problems?

And if you really want to learn about swapping in Linux I'd suggest you try this:
[http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/](http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/)

I myself settled for **vm.swappiness=10** (default is 60!! ... see the link above, it explains what this value does or doesn't) and my system's responsiveness has improved dramatically. At least I perceive it like that :)

Yes, it doesn't harm to learn new stuff .... but trying to reproduce workarounds for one OS on another OS that functions entirely differently is kinda pointless and won't produce the results and "speed miracles" people who believe Microsoft's marketing blah blah blah seem to expect here.

But hey, it's your system, and your time. All I'm saying is that this is a pointless exercise and has nothing to do with how Linux does swapping. That's all. :)

---

### Post by lespaul_rentals on 2008-01-10
> **scorp123 said:**
> You got me wrong there. This "ReadyBoost" thing is a workaround that Microsoft had to come up with to address a few serious flaws in Vista. Only that even on Vista it doesn't really help that much (see the links that I posted above).

To reproduce "ReadyBoost" on Ubuntu is kinda totally useless. First of all Ubuntu doesn't have the same problems there, so why implement this workaround if your OS isn't even suffering from the same problems?

And if you really want to learn about swapping in Linux I'd suggest you try this:
[http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/](http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/)

I myself settled for **vm.swappiness=10** (default is 60!! ... see the link above, it explains what this value does or doesn't) and my system's responsiveness has improved dramatically. At least I perceive it like that :)

Yes, it doesn't harm to learn new stuff .... but trying to reproduce workarounds for one OS on another OS that functions entirely differently is kinda pointless and won't produce the results and "speed miracles" people who believe Microsoft's marketing blah blah blah seem to expect here.

But hey, it's your system, and your time. All I'm saying is that this is a pointless exercise and has nothing to do with how Linux does swapping. That's all. :)

I tried it, and it actually increased my performance by about 10% or so.  Not amazing by any means but fun to try.

But, yeah, Microsoft is only trying to mask Vista's horrible coding and process management with an amazing "feature."  Last year, when I was life-guarding at the YMCA, we learned a lot about first aid, CPR, AED's, etc. because we had to be ready to help people out.  I remember we heard about a girl who was sick and the doctors gave her a lot of DXM because she was coughing so much (DXM works as a cough supressent in drugs like Robutussin, Nyquil, etc.).  She went down the water slide, and naturally she got some water in her mouth.  Well, as she kept going down, more and more collected in her lungs, and since her body didn't feel the urge to cough, she eventually passed out and almost died.  Point is, Microsoft is treating Vista the same way.  If it's sick and it coughs, just give it more drugs!

---

### Post by scorp123 on 2008-01-10
> **lespaul_rentals said:**
>  DXM works as a cough supressent in drugs like Robutussin, Nyquil, etc. .... If it's sick and it coughs, just give it more drugs! Oh dear. Talk about a "workaround" totally gone wrong .... I'd kick her doctors in the ..... Oh well. Where it really hurts. You get the idea. But you are right, it's the same thing with Microsoft. Instead of curing what's really wrong they come up with a workaround so you hopefully won't notice the "coughing" and all the rest that's wrong.

---

### Post by rosegarden78 on 2008-02-01
Thank you very much for this informative thread. :KS

---

### Post by clonne4crw on 2008-03-08
this is awesome, but every time I reboot, the swap settings are rest. I know I can add it to my list of startup programs, but 1)then it won't make my system boot faster, and 2) I'm using SUDO, so won't it prompt me for a password every time I log in, will it? I don't want that.:?

---

### Post by ChameleonDave on 2008-03-11
> **adampyre said:**
> 
Is there a way to cascade the systems memory usage? Please read the following oh intelligent ones and tell me if I am going about this the right way:

I followed the tutorial about mounting my pendrive as swap space and then I turned of the HD swap space hoping it would speed things up. I have, 256 MB RAM, 512 MB pendrive all dedicated as swap, and 500 MB HD Partition that was dedicated as swap, but I turned it off to force the system to use my pendrive as a swap.

Would it be worth it, to turn the HD swap back on and possibly even make my system "cascade" it's memory usage? What I mean is, use the ram, once ram is full, go to pendrive. Once ram and pendrive are both full, then go to HD. Once all three are full, oh well...
!

I'm not sure if anyone replied to this.

Open your /proc/swaps file as root.  Here's mine:

```
cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/sda1                               partition       1020088 0       -1
/dev/sdb1                               partition       2048248 0       -2
```

You'll notice that each swap partition has a priority number.  I'm sure that editing that number will do what you want.

I don't think I'll bother with adding swap at all though:

```

free -m
             total       used       free     shared    buffers     cached
Mem:          2027       1710        316          0        234        930
-/+ buffers/cache:        545       1481
Swap:         2996          0       2996
```

---

### Post by brucewestfall on 2008-03-21
Whew!  Quite a flame war back a couple pages ago...

Here is my situation and why I looked into this:

Not enough money for a newer computer right now, so I have to deal with my hp pavilion 526.  Memory maxes out at 1 gig, which is what I have.  I've got 2 HD with about 180gig total, with around 80 or so still free.

I do graphics all day using either Gimp, Inkscape ( which can run my vinyl cutter as of yesterday! ) and Blender.  I always have the system monitor running in the upper task bar, and it OFTEN runs at maximum.

Processor at 100% and memory scraping the top line also.  About once every other week, I get busy and don't pay attention - have WAY too many programs running, try to do a bucket fill on a 2000 x 3000 pixel image and - - - - - - - - - - - ( to simulate this, pretend like you're trying to move the mouse and nothing happens for about 5 or 10 minutes until either the system recovers, or you reboot, then go make more coffee) - - - - - - - 

Moral of the story:
No money for a new computer right now.
No use buying more memory since the motherboard is maxed out.
No patience to do things one at a time.
No desire to keep doing this.

But I do have money for a $20 4 gig high speed card from meritline.com

Will it help in this case?

(BTW, I'm a 44 yr old Ubuntu fanboy.):guitar:

---

### Post by scorp123 on 2008-03-21
> **brucewestfall said:**
>  But I do have money for a $20 4 gig high speed card  You can try. You could add that as swap space, but you'd clearly benefit from having more RAM. What I'd also suggest is to tune your swappiness parameters, e.g. my posting #90 here in this thread:
[http://ubuntuforums.org/showpost.php?p=4106572&postcount=90](http://ubuntuforums.org/showpost.php?p=4106572&postcount=90)

---

### Post by Recruit0 on 2008-05-16
It would be interesting to use flash drives to speed up load times though (booting, program launching). Read from the flash drive as the HD seeks, then use a type of RAID 0 (although technically it'd be more like a RAID... 1+0...) and read from both (and only write data to flash that is unlikely going to be changed/erased [often], e.g. executables, DLLs, boot, drivers ). I'm not sure if you can increase throughput by reading from both though. While the HD seeks you can read up to 1/4 ~ 1/2 MB of data from flash. Basically use the flash drive like a cache for the HD.

I think some Memory Sticks have faster data transfer rates than USB 2.0 sticks so would be preferable (good option for laptop users until they need to use the slot reader for something else, in which case, using the flash drive as a cache will simply be dropped out of the equation [since the data is on disk] )

Can also be used with swap to decrease load time. Yeah I know swap is practically never used (have a laptop with 4 GB RAM, never touches swap) but still if it ever gets used then it'd help. Although it'd still need the same restriction of only writing data that doesn't change often (swap probably changes too much though so it's unlikely to be eligible for the flash cache, unless some parts of swap are "static" enough)

---

### Post by lavinog on 2008-05-29
Regardless of how readyboost works on vista, I think linux could benefit using a flash drive as a hd cache. The Linux kernel will cache files in memory currently, but the user memory will take the place of the cache as needed. So say your commonly used files are in cache and you open a bunch of images in the gimp. Your cache will be purged, and after you close the gimp you lost your performance gain.
As mentioned before: flash reads are many times faster than its writes. This is ideal for a cache since the user wouldn't need to wait for a write operation only read. (Flash media would be a poor choice for a swap partition for this reason)

Here is what I think should be the chain of events for the 'flashboost':
IO read from HD into memory.
Kernel checks file size if < some threshold (lets say 40k) store onto flashdrive.
Kernel then keeps a record in memory of what files are on the flash.
All subsequent reads of that file are read from the flash drive
If the file is modified...it is modified on the hd and the cache entry is removed until modification time is older than some threshold (we don't want to cache files that are modified too many times.)

The system should allow for some form of encryption, but unlike readyboost it should be up to the user since encryption would require more cpu cycles.

If the flash drive is removed or some other hardware failure (such as overloading the usb bus) and the data can't be read within a reasonable time then the kernel should automatically retrieve the data from the hd and notify the user of what happened.

I think this setup should not be over looked. I agree that linux is much more efficient with shared memory which reduces the bloat, but the issue is that storage media needs all of the improvements it can get. Also some motherboards are coming with the readyboost flash drives soldered onto the boards...why not take advantage of them.

One more thing: Flash memory is more energy efficient than adding more ram...I like having a home server, but I like having lower electric bills too.

---

### Post by markomanka on 2008-07-22
Hi everyone :)

my attention got so caught by the discussion here that I've decided to register to talk...

I wanted to share with you the following article

[http://apcmag.com/readyboost_for_linux.htm](http://apcmag.com/readyboost_for_linux.htm)

It describes how swap and readyboost are different (being the first quite more "specialized" than the second)... and how linux is far better than Windows in managing memories, thus not really sure it would require readyboost nowadays...

Nevertheless, let me say I'm a vintage-computing addicted(I'm trying to revive an old 386 25MHz and just 1Mb RAM... and I'm currently using a PIII 550MHz and 512Mb RAM) and I would really value a full capable linuz-readyboost to be added to my weaponry...


I'm looking forward to your replies. Thank you in advance for any answer!

Marco.

---

### Post by tobie.de.beer on 2008-11-05
Hi,

I've used linux back in '95 in those days we always tried to have two disks, one for swap and the other for the filsesystem. Using the flash as swap is basically the same - it saves your HD to move between your filesystem and your swap.(seek times !)

Something I can mention, there is a program call readahead and readahead-watch as discribed in the ' Make Ubuntu Extremely Fast ' thread.
From that you can determine which files are being read by your computer (from some time onwards ) create your filesystem to have those on flash...

One way to make your computer very fast would be to build a new filesystem on the flash that get mounted as root with the HD at some mount point and all the big files and files being written frequently on the HD with links to them from the file system ( on the flash) - Adding a second hard drive for swap (you don't want reliability issues there)

Or if you really have a lot of flash create boot-time scripts to copy /bin, /usb/bin and /usr/lib to three flash drives, mount them on those places ( as far as I remember the original files will then be hidden) and use a second HD for swap.

With these methods you basically have a static cashe (e.a. it does not chance with your system dynamics or use.

T

---

### Post by Gilgamech on 2008-12-02
hey dude i tried the ready boost in ubuntu and it worked perfectly fine with my usb and then i thought: lets try it with my 8gb SD card using my psp as usb since this laptop is too old and doesnt have an sd slot XD, anyways it worked perfectly fine but when i removed it using "swapoff /dev/sdb1" it completly deleted everything on my sd card :cry:](*,) plus now i cant insert the sd using the psp as and usb it tells me "mount:/dev/sdb1: can't read superblock". is there anyway u can help me???

---

### Post by scorp123 on 2008-12-02
> **Gilgamech said:**
> hey dude i tried the ready boost in ubuntu This is total nonsense and not needed for Linux! That "ReadyBoost" BS was something Microsoft had to come up with because of the many shortcomings of Vista! Chances are you're not even using swap on your Linux installation, so please everyone: stop following this "guide" here ... it's nonsense and will only cripple your SD cards!

---

### Post by bapoumba on 2008-12-02
Thread closed.

---

