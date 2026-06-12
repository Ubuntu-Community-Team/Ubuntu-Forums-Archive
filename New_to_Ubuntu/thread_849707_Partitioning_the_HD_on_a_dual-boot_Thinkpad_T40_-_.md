---
title: "Partitioning the HD on a dual-boot Thinkpad T40 - what would you do?"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by majabl on 2008-07-04
I've recently bought a second-hand IBM Thinkpad T40 to use as a 'sofa' laptop, primarily for web browsing.  To do this, I want to have it dual booting XP and Ubuntu.

In terms of partitioning, how would you divide the laptop's 40GB hard drive?  I was thinking along the lines of a 10GB Windows partition (I already have 7.8GB used), a 5GB Ubuntu partition, 1GB /home partition, 1GB partition for the swapfile, and then the rest as a FAT32 partition for storing documents, mp3s, and whatever else, but I'm open to other suggestions and advice!

Also, it doesn't have an inbuilt wi-fi adaptor so I was thinking about one of [these Linksys Wireless-G Notebook adaptors]("http://www.dabs.com/productview.aspx?Quicklinx=2CM9").  Any idea whether this will work smoothly with Ubuntu with no/minimal fiddling?

---

### Post by benerivo on 2008-07-04
If your going to have an os agnostic partition for data (the fat32 one), then i wouldn't bother having a seaparate /home partition. You would never use the advantages it offers as being a separate partition other than when it stores program settings and prefs during a full upgrade or reinstallation. 

I don't know about the wireless card, but is it the one widely discussed [here]("http://ubuntuforums.org/showthread.php?t=5645")?

---

### Post by louieb on 2008-07-04
> **majabl said:**
>  I was thinking along the lines of a 10GB Windows partition (I already have 7.8GB used), a 5GB Ubuntu partition, 1GB /home partition, 1GB partition for the swapfile, and then the rest as a FAT32 partition for storing documents, mp3s, and whatever else, but I'm open to other suggestions and advice!

Pretty much describes how I did my T30's 40 GB drive.   only  my data partition is formated ext3. I'd use ext3 or NTFS.  

> **majabl said:**
> Also, it doesn't have an inbuilt wi-fi adaptor so I was thinking about one of [these Linksys Wireless-G Notebook adaptors]("http://www.dabs.com/productview.aspx?Quicklinx=2CM9").  Any idea whether this will work smoothly with Ubuntu with no/minimal fiddling?

Haven't tried the netgear but the airlink 101 awlc5025 or 4030 will work out of the box. Now I have an intel internal card I got on EBAY. One thing about the internal is I was getting an 1802 on boot. IBM will only take certain cards.  There is a fix  to disable the card check at boot on the net. 
a couple of good places to go.   [ThinkWiki - Linux on ThinkPad]("http://thinkwiki.org/wiki/ThinkWiki") and  [ThinkPad Forum ]("http://forum.thinkpads.com/")

---

### Post by bobpur on 2008-07-04
You might want to max out the memory in that Thinkpad. I had an old Thinkpad 390E that had 64 mb RAM when I got it and I maxed it out at 256 mb RAM. It dualbooted Win2k / Xubuntu real well. 
I never did get the wireless to work with Xubuntu, though. That was about 3 or 4 versions(of Xubuntu) ago and I didn't know a lot then either. So I wiped the linux partition reformatted the drive and made it a Win2k machine for my daughter and bought myself a new Acer. :)

Good Luck.

---

### Post by majabl on 2008-07-05
> **benerivo said:**
> If your going to have an os agnostic partition for data (the fat32 one), then i wouldn't bother having a seaparate /home partition. You would never use the advantages it offers as being a separate partition other than when it stores program settings and prefs during a full upgrade or reinstallation. 

I don't know about the wireless card, but is it the one widely discussed [here]("http://ubuntuforums.org/showthread.php?t=5645")?

What advantages might I be able to get from having a home partition separate from the data partition, and what would I need to do to get these advantages?

And that is indeed the wireless card - thanks!

---

### Post by majabl on 2008-07-05
> **louieb said:**
> Pretty much describes how I did my T30's 40 GB drive.   only  my data partition is formated ext3. I'd use ext3 or NTFS.

Doesn't having the data partition formatted as ext3 mean that XP can't read it?

And thanks for the tip on the wireless card!

---

### Post by majabl on 2008-07-05
> **bobpur said:**
> You might want to max out the memory in that Thinkpad. I had an old Thinkpad 390E that had 64 mb RAM when I got it and I maxed it out at 256 mb RAM. It dualbooted Win2k / Xubuntu real well.

Yeah - this one came with 256MB which seemed OK, but I bought another 512MB to supplement the RAM that came with the laptop.  For what I want to use this laptop for, 768MB should be plenty.

---

### Post by louieb on 2008-07-05
> Doesn't having the data partition formatted as ext3 mean that XP can't read it?My though - use XP more format the data partition NTFS - use Linux more format the partition ext3. A couple of ways to get at ext3 from XP [Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs") and [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html"). 

> benerivo -  /home ... other than when it stores program settings and prefs during a full upgrade or reinstallation. Having a separate /home when you have data partition is a Ginger or Mary Jane kind of thing.  :biggrin:

Since /home is a part of the OS I want it separated from my data.  And since it contains user setting its nice to have it in a separate partition  for the reasons ]benerivo pointed out.  I know when I first started using Linux I screwed it up to point of reinstall. Having my settings preserved make the reinstall easier.

---

