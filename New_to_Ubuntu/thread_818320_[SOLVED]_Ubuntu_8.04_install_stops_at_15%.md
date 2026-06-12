---
title: "[SOLVED] Ubuntu 8.04 install stops at 15%"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by tysonh on 2008-06-04
I use ubuntu on my desktop and installed it with no problems.  I just bought a IBM thinkpad T30 laptop.  It has a 1.8 mobile intel cpu and a ati 7500 video card. 

Every time I try to install it the install stops at 15% during that time it says detecting file system but doesn't go any further.

I thought it might be because I bought a hard drive that is a enchanced IDE drive.  Could this be the problem?

I ordered the install cd and I have a copy that I downloaded, and a older ubuntu but all of them do the same thing.  Any advice would be great.  I really hate winblows and wanna get it of my laptop.  thx in advance  :)

---

### Post by NoFearDJB on 2008-06-04
> **tysonh said:**
> 
Every time I try to install it the install stops at 15% during that time it says detecting file system but doesn't go any further.

I thought it might be because I bought a hard drive that is a enchanced IDE drive.  Could this be the problem?

I'm guess IBM has some sort of special driver to access the hard drive and the boot cd doesn't have it on the disc. Does the installer ever give an error (might have to wait awhile) or does it just hang?

---

### Post by rraj.be on 2008-06-04
Could you just tell me whether its getting into creation of partition or not.

what is the partition type that you used to install after  the  error in installation.

---

### Post by tysonh on 2008-06-04
I picked the use the whole disk option for installation.  I went with the default partitioning.  It formats the partitions and then stops at 15% saying detecting file system.  I let it sit for about twenty minutes hoping that it would give a reason while it wasn't working, but nothing it just hangs.

I thought I might have been unlucky and gotten a bad hard drive but xp and freebsd both load onto the drive with no problems.  

thx for the help )

---

### Post by tysonh on 2008-06-05
Anyone have any ideas?

---

### Post by rraj.be on 2008-06-05
my doubt is that whether your hard disk is partitioned correctly by the ubuntu partitionar during installation or it failed during instalation.

Failure of partitioning during instalation is one of the major reasons for Error in instalation.

Just answer this.

what is the partition type after this error.
```

Is it ext3fs or unallocated.
```

---

### Post by yaztromo on 2008-06-05
You could also try the alternate (text mode) install CD.

---

### Post by talktoari on 2008-06-05
Did you do a manual partitioning while installation?

I would recommend having an empty partition (Unallocated) in the harddrive and then you can select the option of "Choose maximum Contiguous available space" during installation. Ubuntu will create automatically the partition in the unallocated space and this won't affect any other partition you have in your PC.

Hope this works out.

---

### Post by tysonh on 2008-06-08
My first install attempt my hard drive was brand new.  I took it out of the package put it in my laptop and tried to install.  No matter what I do it hangs.  Both Windows, SUSE, FreedBSD and Fedora install quickly with no problems.  Ubuntu is my favorite and its just annoying that I can't get it work.

I can't think of any reason why this is happening with ubuntu only.  Its not just the current version.  I've tried every release of ubuntu that I have on cd.

The only thing I can think of is that ubuntu hates my new hard drive or for some reason doesn't support it.

I hope someone out there has had a similar experience that can shed some light on this for me.

Thanks is advance  :)

---

### Post by bumanie on 2008-06-08
EIDE drive are not new they have been around for 8-10 years, so unless there has been a firmware update that causes issues with ubuntu, I can't see that being the problem. Having said that, I have read that most hard drive manufacturers don't specifically support open source and recently some linux users have had problems with some external drives - upon complaint they get the reply that "we don't support linux/open source." I would try the alternate cd that very often works when the live cd won't.

---

### Post by tysonh on 2008-06-08
Yeah I've tried every cd I have including the Ubuntu cd I ordered through the mail.  Its not a live cd it's solely a install cd.  My hard drive is a western digital.  Here is the model number WD600BEVE.  Here is a link to product page: [http://www.westerndigital.com/en/products/Products.asp?DriveID=103]("http://www.westerndigital.com/en/products/Products.asp?DriveID=103")

---

### Post by tysonh on 2008-06-09
Just replying to myself in a attempt to bring some much needed attention to my issue.  I haven't tried to install Debian yet maybe that distro will let me dual boot xp and ubuntu.   Please help!

---

### Post by lisati on 2008-06-09
> **tysonh said:**
> Yeah I've tried every cd I have including the Ubuntu cd I ordered through the mail.  Its not a live cd it's solely a install cd.  My hard drive is a western digital.  Here is the model number WD600BEVE.  Here is a link to product page: [http://www.westerndigital.com/en/products/Products.asp?DriveID=103](http://www.westerndigital.com/en/products/Products.asp?DriveID=103)

What appears on the screen when you are using the CD? Is it a GUI (graphical user interface)?

---

### Post by starcannon on 2008-06-09
I'd scrub the hdd with this:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

and then try running 7.10 or 8.04 livecd again.

---

### Post by tysonh on 2008-06-09
lisati: Yes I did get a gui to install from.  I boot from the cd and then go through several set up options then I get to where and how I want to install it and it won't go past 15%.

As I have said earlier other distro's of linux seem to install just fine.  It seems to be limited to ubuntu. 

And I have used gparted to start over to take everything back to unallocated space and try to install from there.  Nothing I do seems to make a difference.

I've tried to install on the largest space after the windows partition and that didn't work either.  I haven't added any partitions manually.  I just tell it where to install and let it apply the default partition set up.

---

### Post by tysonh on 2008-06-09
Maybe this has something to do with my problems with the install.  While installing Fedora a message popped up during the installation.  It said it detected that I only had 256 memory and Fedora needed to creat a swap file to continue the installation.

Could I manually create a swap to do this in ubuntu?  I'm fairly new to linux in general and my partition knowledge is pretty limited.  

I have followed many how to's and search the forums here before posting in a hope to solve my own problem.  Could anyone give me a break down of what partitions I should create?  I have a 60g drive and I want 30g of it for windows xp and 30 for ubuntu.

I can get as far as making the hard drive allow 30g for windows and making 30g available for the install.  After that should I create my own partition scheme or should I just let ubuntu install a default set up.  Will the default set up create a swap file for me if I need it because of my low memory?

Any help would be great,  thx in advance :)

---

### Post by yaztromo on 2008-06-09
So to clarify you have tried both the live CD (GUI Install) and the Alternate CD (text install)? They both have different methods of installing and it's surprising they would get stuck in the same place.

A few suggestions:

- You could try manually partioning the drive instead of using guided mode. Just remove all existing partitions and then create a large / filesystem and a gigabyte of swap to fill the disk. Maybe the partioner is hitting a bug.

- Have you tried leaving the install running to see if it unsticks? Maybe it is just busy and you are stopping it prematurely.

- With the Live CD have you tried opening a terminal after it gets stuck? Run the top command to see if a process is eating all the CPU and run dmesg to see if the kernel has reported any errors.

- Try starcannons suggestion.

If all else fails and nobody here can help you. You should open a bug on launchpad.net

> Maybe this has something to do with my problems with the install. While installing Fedora a message popped up during the installation. It said it detected that I only had 256 memory and Fedora needed to creat a swap file to continue the installation.

(Edit: completely rewritten)
I read others on the forum recommend the same. If you really want to use the Live CD then you should run gparted live cd first and create the partitions you need yourself. As I said just one large ext3 partition and then a gigabyte of swap will do.

With only 256meg of RAM you should definitely use the alternate text mode CD to install from. Get this iso, burn it and see what happens [http://mirrors.gigenet.com/ubuntu/hardy/ubuntu-8.04-alternate-i386.iso](http://mirrors.gigenet.com/ubuntu/hardy/ubuntu-8.04-alternate-i386.iso)

---

### Post by tysonh on 2008-06-09
I downloaded the alternate cd and did the text install.  No problems what so ever.  8.04 runs pretty smooth on only 256, but i'll be buying some more memory as soon as possible.  Thanks to all those that helped me along.

Side note to whom it may concern:  If you have 256 memory on your system go with the alternate cd and save yourself some headaches.  :)

---

