---
title: "Super Nas"
date: 2007-06-02
forum: Programming Talk
---

### Post by Pontifex on 2007-06-02
I'm not exactly sure where to put this, so I posted copies of it in the 'Servers & Security' [1] forum as well as 'Programming Talk' [2].  I'll hope you forgive the imposition, but I wanted to maximize my returns.  Feel free to merge / close threads as you see fit, though I will repost useful comments as needed to continue the discussion.

I've been messing around with storage for most of my adult life (15 or so on to 25 this year).  I've accrued  a massive amount of data and I've been looking for better ways to manage it.  In the past I've just bought big hard drives and shared them via a Linux box.  I usually hover around 300GB-500GB of live data at a time.  In the past I've messed around with LVM, which I was delighted to see incorporated into Ubuntu in a fairly painless fashion; Nothing like my long hours of diagnosing and  lost data.

I've since broken down and bought myself a NAS [3].  I love the thing to death.  But now I have a great deal of left over IDE and (old) SATA drives, that I used to use for storage.  I was seriously considering putting something like 12 drives in one computer off several Promise controllers, but that didn't turn out to be viable (Promise doesn't support more than _one_ controller per computer, I can get two working but three requires some hacking).  So I'm left with a lot of hardware sitting around that I can't turn into a single storage option.  If I could put them all together and RAID them, I'm pretty sure I could get something like 700GB out of them.

Ever since I encountered the &#8220;Promise Problem&#8221;, I've been toying around with the idea of putting together several computers that could share data (via SMB or something similar).  This would be just like what I've been doing for years.  So I thought to myself why not have a series of computers all sharing data and presenting themselves as one large logical drive.  The back end would have some serious RAID of course, but it sounds feasible.

I'm almost sure someone must have thought of something like this before.  But for the life of me I don't know what they would have called it.  I checked SAN [4], but that seems a bit overkill.  At least in it's current Enterprise form.  The closest thing I can find seems to be a &#8220;NAS Head&#8221; [5] which would mediate between my network and a SAN.  But a quickly google search doesn't show anyone with that sort of project going.  Nor a simple SAN program I could drop into my theoretical network of computers.

The problem doesn't sound too hard.  Start with something simple, like a boot CD.  Knoppix or something similar.  Boot up a terminal and a file sharing daemon and you have a simple NAS.  Step two: Slave them together.  Create a &#8220;controller&#8221; program and integrated it into your CD, the thing seeks out NAS's on the network and adds the storage advertised by our little NAS's to the controllers table of available storage.  The controller indexes where it can put things - you could use a database for this, which would necessitate a hard disk, but still it wouldn't kill the project &#8211; and downloads digests of where things are on its children.  Whoops, we're getting some network chatter here, let's make the protocol event driven and incremental; That way we minimize network usage except for file transfers.  You could do one better for security and create use accounts on the slaves to only be accessible to the controller; Random strings for Usernames and Passwords or something similar.  Then just point everyone to the controller and have them use it like a regular NAS.  No one's the wiser  You could then integrate RAID into the slaves and some fancy logic to figure out what the best redundant configuration for each slave would be and shuffle around data until everything is stable.  You'd then have a scalable network of computers that emulate a highly redundant and theoretically infinite NAS.

That doesn't sound too bad.  Tell me someone's done something like this before so I don't have to spend a couple months coding it myself. ^_^

[1] - [http://ubuntuforums.org/showthread.php?p=2765540](http://ubuntuforums.org/showthread.php?p=2765540)
[2] - [http://ubuntuforums.org/showthread.php?p=2765536](http://ubuntuforums.org/showthread.php?p=2765536)
[3] - [http://www.newegg.com/Product/Product.aspx?Item=N82E16822329031](http://www.newegg.com/Product/Product.aspx?Item=N82E16822329031)
[4] - [http://en.wikipedia.org/wiki/Storage_Area_Network](http://en.wikipedia.org/wiki/Storage_Area_Network)
[5] - [http://en.wikipedia.org/wiki/Network-attached_storage#NAS_heads](http://en.wikipedia.org/wiki/Network-attached_storage#NAS_heads)

---

### Post by FuriousLettuce on 2007-06-02
I've never looked into anything like this, but the first thing to check is wikipedia's [NFS]("http://en.wikipedia.org/wiki/Network_File_System")  (network file system) page. This leads immediately to a list of [distributed file systems]("http://en.wikipedia.org/wiki/Network_File_System#Distributed_file_systems"). From there I randomly checked on [Coda]("http://en.wikipedia.org/wiki/Coda_%28file_system%29"), and a [corresponding review]("http://linuxplanet.com/linuxplanet/tutorials/4481/1/"). 

I'm afraid I don't have enough time to spend actually appraising the different options, but they ought to be a good starting point.

---

### Post by Pontifex on 2007-06-02
Joining this this thread.

[http://ubuntuforums.org/showthread.php?p=2770339#post2770339](http://ubuntuforums.org/showthread.php?p=2770339#post2770339)

THanks for your help.

---

