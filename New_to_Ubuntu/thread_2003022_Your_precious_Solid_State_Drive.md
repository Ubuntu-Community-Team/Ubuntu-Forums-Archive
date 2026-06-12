---
title: "Your precious Solid State Drive"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by yeehi on 2012-06-13
It is great to have a Solid State Hard drive, SSD. They are very quick and meant to be more reliable, as they have no moving parts. (From what I have read, Intel SSDs are meant to be by far and away the most reliable SSDs at the moment. I wonder whether you agree with that.) Unfortunately, they are more expensive than tradittional hard disks and smaller, too. That makes real-estate space on a SSD at a premium. 

Some things really ought to go on the SSD. Others could go onto a tradditional Hard Disk, if both are in the machine.

What I would like to know is what things really should get put onto the SSD? If you are partitioning the SSD, what folders shouls definitely be on the SSD? Could the /home go onto the Hard Disk? I believe that games should go onto the Hard Disk,as modern games can be very large installations and it doesn't matter how fast the drive is for them, as the game is loaded into memory when it runs anyway.

I look forward to hearing what you have to say!

Thank you. :)

---

### Post by AlanR8 on 2012-06-13
The only thing I really use my HD in my laptops is for the OS. Everything else is in the cloud....

---

### Post by Sylos on 2012-06-13
I dont know a vast amount about SSDs but I have looked into the possibilities of having one alongside my HDD to increases speeds. From what I read it seemed the sensible move was to have your root on the SSD and your /home on the HDD as /home is where most of your files are going to be and therefore take up most space. Also it may reduce your writes to the SSD thus helping prolong the life of the drive. 

I did wonder when I looked into it whether the hidden configs in your /home directory might reduce your operating speed by being on the slower drive. Would be interested to hear peoples opinions on that.

Just the thoughts of the layman....

---

### Post by Cheesemill on 2012-06-13
I have / and /home on my 64GB SSD, swap and /data on my 1TB HD (with swappiness set to 0 as I have 8GB RAM).

Videos, Music, Pictures etc are symlinks to folders on my /data partition.

This way I still get the speed advantage of an SSD for all of my configuration files that live in /home.
If /home was on my HD then applications would have to read files from the HD when starting up, so I wouldn't get the same performance boost that I do with my setup.

To decrease writes to my SSD I enable the noatime option in fstab as  well as turning off the ext4 journaling (I use a UPS). Also make sure  you use the discard option to enable TRIM support.

Also /tmp is mounted as a RAM disk.

---

### Post by Bobhuber on 2012-06-13
In short everything that you write to frequently > tmp, var, cache files, download  etc should be placed on the rotating drive with symlinks (easiest way) to the drive. All of your system files, home etc should be left on the SSD. Otherwise you defeat the purpose of the SSD drive. And it makes a huge difference in performance even on a high end system.

---

### Post by Cheesemill on 2012-06-13
Deleted

---

### Post by ratcheer on 2012-06-13
IMHO, you should move things that are updated frequently off of the SSD to a hard drive. Things such as /var/log. And the place where your web browser cache is. Stuff like that.

It is my understanding that frequent updates somehow "wear out" the memory locations.

Tim

---

### Post by Jagoly on 2012-06-14
My setup is almost identical to Cheesemill's. Having /home on the ssd is a good idea because a lot of frequently read files reside there, and it's easy to symlink things to subdirectories on the big drive, in my case, /storage. I also have a few games (HIB) installed to /storage.

Another change you can make (if you want everything perfect) is to change the scheduler for the SSD to noop or deadline, but I forget how to do that :-)

---

### Post by Homeroast on 2012-06-14
Total newbie question here ... do solid state drives run cooler than hard disk drives?

---

### Post by ivanox1972 on 2012-06-14
> **Bobhuber said:**
> In short everything that you write to frequently > tmp, var, cache files, download  etc should be placed on the rotating drive with symlinks (easiest way) to the drive. All of your system files, home etc should be left on the SSD. Otherwise you defeat the purpose of the SSD drive. And it makes a huge difference in performance even on a high end system.

How to do this exactly as you said?
thanks

---

### Post by steve7777777 on 2012-06-14
What's wrong with leaving the OS on the SSD and data on a mechanical hard drive? 

Also, how does SSD work with Clonezilla? If you have to restore an image made from SSD only to another SSD (as opposed to mechanical drive) that's a deal breaker for me.

---

### Post by Jagoly on 2012-06-14
> **Homeroast said:**
> Total newbie question here ... do solid state drives run cooler than hard disk drives?

> **steve7777777 said:**
> What's wrong with leaving the OS on the SSD and data on a mechanical hard drive? 

Also, how does SSD work with Clonezilla? If you have to restore an image made from SSD only to another SSD (as opposed to mechanical drive) that's a deal breaker for me.

@Homeroast: Yes, SSD's run very cool. Think of them as very fast internal thumb drives, consisting of flash memory. They consist of no moving parts, so they can resist large amounts of shock as well. And, they use almost no power.

@steve7777777: We are saying to do that, were just being a bit more technical about it. As for clonezilla, remember that to an operating system the data on an SSD is no different to the data on a mechanical drive. Same files, same filesystems. So clonezilla will happily work in that situation.

---

### Post by yeehi on 2012-06-15
> **Cheesemill said:**
> I have / and /home on my 64GB SSD, swap and /data on my 1TB HD (with swappiness set to 0 as I have 8GB RAM).

Videos, Music, Pictures etc are symlinks to folders on my /data partition.

This way I still get the speed advantage of an SSD for all of my configuration files that live in /home.
If /home was on my HD then applications would have to read files from the HD when starting up, so I wouldn't get the same performance boost that I do with my setup.

To decrease writes to my SSD I enable the noatime option in fstab as  well as turning off the ext4 journaling (I use a UPS). Also make sure  you use the discard option to enable TRIM support.

Also /tmp is mounted as a RAM disk.
 
When you installed Ubuntu, what size did you allocate to the swap partition? Or did you not create a swap partition, since you have so much RAM?

You have a 1TB HDD. That is nice :) During installation, you configured a partition /Data, is that right? I have tried something like that before, but I wasn't able to write to it, (or even read it!) as far as I can remember. What settings did you need to set? What file system did you use for /Data, by the way? And what sort of things would you store on /Data rather than in /home?

---

### Post by pablolie on 2012-06-15
i think a good guide is 
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)

in general, i don't think one needs to worry too much about writing to SSD these days. sure it "wears the drive out", but it'll take much longer then the time an even high wear computer user will keep the drive. 
[http://www.storagesearch.com/ssdmyths-endurance.html](http://www.storagesearch.com/ssdmyths-endurance.html)
I have a first generation Intel 80GB SSD that is still going very strong in  my mother's laptop without ever having undergone much optimization. if and when it fails it will be the first one of a dozen or so SSDs i have had running in a number of machines.

in summary, the basic rule seems to be:
* include noatime in your fstab (12.04 does this all by itself with SSDs, at least it did so in my system) (I think nodiratime is enabled automatically if you set noatime, but some do both) to avoid the silly UNIX design idea to constantly update file access times...
* enable trim (discard in fstab)

the other considerations are for additional drive space. if you collect movies and pictures, you'll prolly want to move your videos and picture folders there. :)

---

### Post by Paqman on 2012-06-15
> **steve7777777 said:**
> What's wrong with leaving the OS on the SSD and data on a mechanical hard drive? 


Nothing, it's a good way to do it.

If you've got enough RAM I'd suggest instead of putting /var and /tmp on a hard drive, stick it into a ramdisk. You'll lower writes to your SSD and it'll be even quicker.

I don't bother with noatime for SSDs, relatime is good enough and is the default these days. TRIM is important, definitely enable that. I wouldn't advise using a non-journaling filesystem unless you have a rock-solid system for protecting your data. Just use EXT4 and don't worry about it.

The new hybrid drives are also interesting, as they give some of the benefits of SSD technology at a price per GB that is useful for storage.

---

### Post by steve7777777 on 2012-06-15
> **Paqman said:**
> Nothing, it's a good way to do it.

If you've got enough RAM I'd suggest instead of putting /var and /tmp on a hard drive, stick it into a ramdisk. You'll lower writes to your SSD and it'll be even quicker.

I don't bother with noatime for SSDs, relatime is good enough and is the default these days. TRIM is important, definitely enable that. I wouldn't advise using a non-journaling filesystem unless you have a rock-solid system for protecting your data. Just use EXT4 and don't worry about it.

The new hybrid drives are also interesting, as they give some of the benefits of SSD technology at a price per GB that is useful for storage.

Thanks Jagoly and Paqman. Great information!

---

### Post by 3Miro on 2012-06-15
I followed some recommendation by the Gentoo howto and got the following:

/ -> goes on the SSD
/var, /tmp -> go on RAM disk
/home -> mechanical 1
/media/Storage -> mechanical 2

---

### Post by yeehi on 2012-06-15
Thank you for the great suggestions, people!

There is some nice information about configuring your SSD [here]("http://forums.linuxmint.com/viewtopic.php?f=90&t=101810&start=0") and [here]("http://www.void.gr/kargig/blog/2012/01/11/linux-ssd-partition-alignment-tips/"). It seems to be quite up to date, too.

---

### Post by yeehi on 2012-06-15
> **Paqman said:**
> 

If you've got enough RAM I'd suggest instead of putting /var and /tmp on a hard drive, stick it into a ramdisk. You'll lower writes to your SSD and it'll be even quicker.

I don't bother with noatime for SSDs, relatime is good enough and is the default these days. TRIM is important, definitely enable that. I wouldn't advise using a non-journaling filesystem unless you have a rock-solid system for protecting your data. Just use EXT4 and don't worry about it.

The new hybrid drives are also interesting, as they give some of the benefits of SSD technology at a price per GB that is useful for storage.


How do we put /var and /tmp into a ramdisk? Do we do that during installation? On a system with 16 GB of RAM, how large should the /var and /tmp ramdisks be?

BTW, during installation, should any of the partitions be ext 2? Why use that instead of ext4? 

Thank you!

---

### Post by Paqman on 2012-06-15
> **yeehi said:**
> How do we put /var and /tmp into a ramdisk? Do we do that during installation? On a system with 16 GB of RAM, how large should the /var and /tmp ramdisks be?

To mount a part of the filesystem to a ramdisk add a line to /etc/fstab by hitting Alt-F2 and typing:
```
gksudo gedit /etc/fstab
```
Add a line such as:
```
none    /tmp    tmpfs    defaults    0    0
```
You can specify a size if you want by adding an option such as "size=512m" instead of "defaults".

Reboot and in a terminal do:
```
df -h
```

You should see your ramdisk(s) listed.

> 
BTW, during installation, should any of the partitions be ext 2? Why use that instead of ext4? 


There's no good reason to use EXT2 IMO. People used to use it on early SSDs that lacked good wear levelling, as it would reduce disk writes, but it's superfluous these days. EXT4 has better features than EXT2, so use that.

---

### Post by yeehi on 2012-06-15
Thank you, Paqman!

What size should you give to /var and /tmp in a ramdisk, if you are an average user?

For example, browsing the web with a lot of tabs open, maybe using a virtual machine, watching a movie, streaming youtube, that sort of stuff?

Are there any sorts of applications in particular that would require larger ramdisks?

---

### Post by Jagoly on 2012-06-15
whoa whoa whoa, you definitely don't want /var on a ram disk. The locations you want on a ramdisk would be:
/tmp
/var/tmp
/var/spool
You put /var on a ram disk and you'll be in a bit of trouble :-)

add these to the end of your /etc/fstab file:
tmpfs   /tmp       tmpfs   defaults,noatime,mode=1777   0  0
tmpfs   /var/spool tmpfs   defaults,noatime,mode=1777   0  0
tmpfs   /var/tmp   tmpfs   defaults,noatime,mode=1777   0  0

---

### Post by pablolie on 2012-06-15
I think in reading the diverging recommendations it is obvious that there is no universal agreeement that going beyond the noatime thing is worth it. If you do the temporary files, you may have to separately tune some programs -most notably Firefox- to change their behavior, and may ghet erratic performance.

See [http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/](http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/)
Here's how I roll in /etc/fstab

#begin fstab info
UUID=5da37f97-c506-4e7e-8c0d-1b6cde7fc2fe	/	ext4	discard,noatime,nodiratime,errors=remount-ro	0	1
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
#end fstab info

*And* I did the Firefox browser.cache.disk.parent_directory value to /tmp thing. Which is a must if you dio the tmp move, imho, I did notice odd Firefox dithering and decreased browsing perfromance before I did.

The rest I didn't bother with. But that's just me. SSDs *are* write resistant in consumer system environments these days, we're just optimizing some further with noatime and such, and for heavy net browsing folk there just possibly *may* be some benefit to doing what I did, even though I am not sure I'd claim it's worth the bother.

---

### Post by Paqman on 2012-06-16
> **Jagoly said:**
> whoa whoa whoa, you definitely don't want /var on a ram disk. The locations you want on a ramdisk would be:
/tmp
/var/tmp
/var/spool
You put /var on a ram disk and you'll be in a bit of trouble :-)

add these to the end of your /etc/fstab file:
tmpfs   /tmp       tmpfs   defaults,noatime,mode=1777   0  0
tmpfs   /var/spool tmpfs   defaults,noatime,mode=1777   0  0
tmpfs   /var/tmp   tmpfs   defaults,noatime,mode=1777   0  0

Sorry, that's true. Personally I do /var/log and /var/log/apt. Could probably do /var/spool too, that's a good shout. I also mount with the noexec and nosuid options.

Is there any benefit to doing noatime in a ramdisk?

**Yeehi**: you don't need to specify a size, but you can if you want.

---

### Post by Jagoly on 2012-06-16
> **Paqman said:**
> Sorry, that's true. Personally I do /var/log and /var/log/apt. Could probably do /var/spool too, that's a good shout. I also mount with the noexec and nosuid options.

Is there any benefit to doing noatime in a ramdisk?

**Yeehi**: you don't need to specify a size, but you can if you want.
In reality mounting /var/spool on the ramdisk is pointless, but it doesn't hurt :-)
But I'd never put the logs on the ramdisk, I use them anyway.
It depends on your own preferences really.

Also no there probably isn't any real benefit putting noatime on a ramdisk, but you're never going to need access times on a volatile file system, so if it's useless remove it is what I reckon :-)

---

### Post by Paqman on 2012-06-16
> **Jagoly said:**
> 
But I'd never put the logs on the ramdisk, I use them anyway.
It depends on your own preferences really.


Meh, I can't remember the last time I needed to look at logs on a desktop, and even then it'd only be the most recent stuff I was interested in. I guess it depends how often you reboot too.

---

### Post by yeehi on 2012-06-16
You are all so knowledgeable! While you are all here, I would like you to chime in on aligning the SSD, too. There is an article about it [here]("http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance").

I have in mind a clean installation of Vista and then putting on GNU/Linux as a dual boot. I worry that the dual booting will mis-align the partitions. It is a bit complicated. Do the partitions have to be at particular sizes to work optimally on the SSD?

Don't all these sorts of things happen automatically in Ubuntu now? From which release did Ubuntu start doing automatic, nice SSD configuration?

---

### Post by pablolie on 2012-06-16
> **yeehi said:**
> ...
Don't all these sorts of things happen automatically in Ubuntu now? From which release did Ubuntu start doing automatic, nice SSD configuration?

I am not sure when it started, but I have been using SSDs since 10.04, and even then gparted and ext4 (in regular install) resulted in optimized alignment.

Now 12.04 (probably somewhere in the 11.x tracks, bui I prefer to stick with LTS) added trim and automaticalled does the noatime etc during the install.

---

### Post by Cheesemill on 2012-06-16
> **pablolie said:**
> I am not sure when it started, but I have been using SSDs since 10.04, and even then gparted and ext4 (in regular install) resulted in optimized alignment.

Now 12.04 (probably somewhere in the 11.x tracks, bui I prefer to stick with LTS) added trim and automaticalled does the noatime etc during the install.
Odd.

I'm using a fresh install of 12.04 (actually 12.10 now) and I had to manually add the discard and noatime flags myself.

---

### Post by meathdeath on 2012-06-16
SSD HDDs are only useful if youre on windows. to be honest the only place they are useful for is loading games quickly.

---

### Post by Cheesemill on 2012-06-16
> **meathdeath said:**
> SSD HDDs are only useful if youre on windows. to be honest the only place they are useful for is loading games quickly.
I would love to hear your reasoning for this.

Like any hardware you need to weigh up the pros (increased speed) and cons (lower capacity, higher price per GB) before making a choice.
Having an SSD with my / and /home partitions on has halved my boot time as well as allowing me to launch applications near instantaneously. I would love to hear why this isn't useful.

---

### Post by ivanox1972 on 2012-06-17
I plan to install both win 7 and ubuntu on one ssd. This means first make 2 partitions with win 7 installer and then, after win7 installed, instal ubuntu on second of them. Will be, in this case, ssd alligned propertly?

---

### Post by audiomick on 2012-06-17
> **Cheesemill said:**
> I would love to hear your reasoning for this.

Like any hardware you need to weigh up the pros (increased speed) and cons (lower capacity, higher price per GB) before making a choice.
Having an SSD with my / and /home partitions on has halved my boot time as well as allowing me to launch applications near instantaneously. I would love to hear why this isn't useful.

My thoughts exactly. I don't want to claim a halving of boot time, but the install that I have on my SSD definitely boots faster and runs more briskly than the install that is on the HDD in the same machine.

---

### Post by HeroOfCanton on 2012-06-17
If someone thinks all they will do is make games open faster, that's because all they do is play games. ;)

Pretty much every program will open faster. As a programmer compiling and running software all day I find my SSDs invaluable.

ivanox, your Ubuntu install should detect the partition as usual. You'll still want to follow the tips posted earlier though (enable trim and set noatime).

Tip for Windows: Turning of the hibernate option will save 4-6 gigs of wasted disk space. [Instructions]("http://www.howtogeek.com/howto/15140/what-is-hiberfil.sys-and-how-do-i-delete-it/")

---

### Post by adad on 2012-08-04
After having burnt an SSD within three weeks, I decided I had to tweak my settings if I wanted to run Linux on it.

This article helped a lot.

[http://brizoma.com/2012/08/04/running-ubuntu-and-other-linux-flavors-on-an-ssd/](http://brizoma.com/2012/08/04/running-ubuntu-and-other-linux-flavors-on-an-ssd/)

---

### Post by Scott Harrison on 2012-08-04
I have / on my 120GB SSD, which makes boot time incredibly quick (<20 seconds). I have /home on a 1TB SATA, which leaves me with plenty of space and easy upgrades in the future.

I also backup /home to another 1TB drive on a daily basis.

---

### Post by yeehi on 2012-09-05
Firmware updates to SSDs can be quite important to their performance and even to their life expectancy.

Will the Ubuntu update centre be able to detect download and install newer versions of firmware for a SSD?

Thank you!

---

### Post by lolpenguin on 2012-09-06
> **Scott Harrison said:**
> I have / on my 120GB SSD, which makes boot time incredibly quick (<20 seconds). I have /home on a 1TB SATA, which leaves me with plenty of space and easy upgrades in the future.

I also backup /home to another 1TB drive on a daily basis.

Ermm...the normal boot time of most GNU/Linux distros, including Ubuntu, on a HDD, is around 10 seconds. With my SSD, my computer boots in 5.

If you want to maximise the life of your SSD, move any frequently read and written places to RAM or a HDD, like /tmp, /home, /var/log, /var/tmp, /var/spool and swap. It is a good idea to keep /home on the SSD if you want applications to load faster.

---

### Post by PaulDoc on 2012-09-09
I reckon they do, the fact that they have no moving parts they would be cooler and quieter.

---

