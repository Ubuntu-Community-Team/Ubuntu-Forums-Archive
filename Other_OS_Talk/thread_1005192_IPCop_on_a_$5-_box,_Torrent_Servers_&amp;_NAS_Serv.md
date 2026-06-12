---
title: "IPCop on a $5- box, Torrent Servers &amp; NAS: Server hardware is cheap now!"
date: 2008-12-08
forum: Other OS Talk
---

### Post by handy on 2008-12-08
I think this thread is appropriate here as [***_IPCop_***]("http://www.ipcop.org/") (Linux distro) & [***_FreeNAS_***]("http://www.freenas.org/") (FreeBSD OS) are not Ubuntu.

I've recently discovered how cheap PII & PIII's have become from the local recycler's (the rubbish dump), this opens up a whole world of server possibilities for the home user at negligible cost.  $5-/server here!  

There are great applications that have been built on stripped down distro's & OS's that are perfect for our cheap home servers, I'll share what I have been upto for the last week, perhaps some of you have used some of these purpose built distro/OS's & could tell us about your setup & experiences?

I started what is now a long thread [***_here_***]("http://ubuntuforums.org/showthread.php?t=998490"), on setting up IPCop, (which is a dedicated firewall & caching web proxy that has quite a few add-ons available for it), on a $5- box (Dell Optiplex GX150 - PIII 731Mhz/256Mb RAM/10Gb HDD CD & floppy drives/3Com NIC on board).

The $5- box is going great, the CPU rarely does more than idle & 256Mb RAM is more than needed (in my small network anyway).  Because our internet speeds are quite slow when compared to HDD data read/write speeds, the vast majority of home users could connect to their modem with a 10Mbit NIC & never get anywhere near maxing out the NIC's bandwidth.  So you can see that a PII (low power usage) is a brilliant piece of gear for a server, particularly one that deals with web traffic.

Installing & setting up IPCop is really not hard, there is excellent documentation on the IPCop site, it is separated; there is the [***_Quick Start Guide_***]("http://www.ipcop.org/1.4.0/en/quickstart/html/"), the [***_Installation Manual_***]("http://www.ipcop.org/1.4.0/en/install/html/index.html") (which includes instructions for using flash media), & there is the [***_Administration Manual_***]("http://www.ipcop.org/1.4.0/en/admin/html/") plus other documentation as well. There is also an active [***_forum_***]("http://www.ipcops.com/phpbb3/index.php?sid=8c57db5a7e7a7abb0b58cacfb82aacba"), as many businesses use this software.  If you know what you are doing you will be up & running inside of 30 minutes. 

The knowing how to get to the point where it is working great took about 6 days of on & off, style work, web research & waiting on 2 very helpful supporters in the Ubuntu/Server forum & one key helper in the IPCop forum for me. 

This was mainly due to my very limited knowledge of how this kind of server works.  Having only had experience with very simple, p2p, small office networking, which only used a file server. Only one of my customers ever ended up needing to move to serving applications from the file server.

All of this was windows based, & the only firewall was ZoneAlarm & when they went to broadband we also used what was available in the modem/router - NAT & some firewall settings.  So I new all but nothing on the subject of using a standalone computer as a configurable firewall.

So with IPCop I am learning some new stuff; I have never needed Bridge Mode in any, let alone my own nasty little modem/router, & putting the protected system (my home LAN) on a different subnet than the modem/router, to get it to work properly, (which is so easy to do once you know but) cost me some time (before I did know about it). :-)  Which my setting up IPCop thread shows.

*I highly recommend the use of IPCop, it is a tiny cut down distro' weighing in at about 35k, it is very mature & powerful, & really quite easy to install & set up, you don't need to know what you are doing, I've proved that, & if you do have a go at it, post questions in my thread & you will get help.  It really should not take you the kind of time it took me, far from it.  Knowing what I know now, I can install it & set it up easily inside of 30 minutes.*  

There is fantastic web based administration software that you use a client to log into, so your firewall/proxy server just sits somewhere headless & without keyboard (never needs a mouse). 

Because IPCop is a Linux distro, & Linux handles data packets much better than windows & windows based modems/routers, there is an improvement in data throughput when on the net, plus the use of a caching web proxy will also speed things for all but the most unusual uses of the internet.  

Using the proxy will cause a reduction in data throughput, which translates into less latency & a more efficient use of your monthly download limit, if you have that kind of account.

There are a lot of add-ons for IPCop, though at this early stage, I am thinking I will only need to use [***_Advanced Proxy_***]("http://www.advproxy.net/"), (once I work out how to get it on there using SSH & scp) as it enhances the IPCop squid web proxy capabilities, though the number of add-ons I end up using could change as my familiarity with IPCop & the size of my network grows. 

[I]**[Edit:]**  As of writing this "edit", I have been using IPCop for 10 months, during which time I have found that our small home network does not have anywhere near the amount of traffic to even be able to use the proxy capabilities already built into IPCop.  So unless you have a network that's load is registering on the inbuilt IPCop Proxy Graphs, don't waste your time with the Advanced Proxy add-on. 

The only add-on I use is [**_Copfilter_**]("http://www.copfilter.org/") which integrates perfectly with the IPCop browser interface, & provides many more possibilities, most of which I don't need, but I do use Privoxy & ClamAV, both of which come with great configuration scripts & DO NOT slow down browsing on our LAN (though I don't know why they don't?). [/I]

For anyone who has got interested since the first link back there in the 3rd paragraph, ;-) below is a link to the IPCop thread, which educated me past a few problems on how to get it up & running, it could save you some time if you choose to go down the IPCop path, it will also hopefully cover the installation of add-ons soon. :-):

***_[http://ubuntuforums.org/showthread.php?t=998490](http://ubuntuforums.org/showthread.php?t=998490)_***
____________

Next I want to make a dedicated $5- torrent box, probably something along the lines of K.Mandla's how-to: 

***_[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)_***
___________

Then I'm going to make a NAS or two out of $5- boxes from the recyclers.

The NAS will be based on [**_FreeNAS_**]("http://www.freenas.org/") which looks to be a great little 35K FreeBSD installation.

***[Edit:]**  I have now had a FreeNAS system for many months; it installed easily, is easy to configure via its client side browser based configuration/observation system (similar to IPCop), it is reliable as can be.  I'm using a 2GB drive to boot FreeNAS & a 1TB drive for storage.  I can play a movie over the 10/100 speed LAN from the FreeNAS box no trouble at all.*

Our tip (recyclers) is closed one day a week, on Monday, so every Tuesday morning I will be off to the tip, 15 minutes round trip driving, to see what has come in on the weekend, I suspect that xmas time could be a time for good pickings.  

***[Edit:]** It wasn't, it has taken 10 months to find a box worth looking at from our local tip, which is a PII with no RAM, that I haven't seriously looked at yet!?*

At $5- each, I think I may build up a supply of about half a dozen, & have backups pre-setup to take the place of a failed box. :-)

K.Mandla has a story or two to tell, as he is big time into encouraging people to get the most out of what many consider to be redundant hardware if you haven't been there yet you should check out his blog:

[B][I][U][http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/](http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/)

[http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/](http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/)[/U][/I][/B]
________________

So tell us what you have got going on a cheap box? 

It will help broaden some of our imaginations, at least mine anyway & offer inspiration for us to go & save some computers from becoming landfill, & as far as PII & III's are concerned, now is the time to get them, because if they are worth next to nothing, it won't be long before it is a rare one that hasn't already been put in its grave. ;-)

---

### Post by handy on 2008-12-09
I picked up a Celeron 466Mhz/64Mb RAM/8.6Gb HDD/52xCD/floppy box for $5- at the tip this morning. :-)

I stuck another 64Mb of PC100 RAM in it, a CR2032 battery for the BIOS & a PCI NIC, (all of which I had laying around the place) so now its ready to have windows ME overwritten with some FOSS goodness & to be transformed into either a NAS box or a torrent server. I'm not sure yet, though I think the torrent path will probably suit this box well.

I've been doing more research on NAS, & have found that apart from FreeNAS, there is another very good looking product which I've been looking at called [***_OpenFiler_***]("http://www.openfiler.com/"), it is further developed than FreeNAS is at this stage.

OpenFiler is also available for free, though the company charges for support contracts & such.  It is a Linux kernel based distro, which is quite a bit larger than FreeNAS.  From what I have read it is also faster than FreeNAS at the moment.

---

### Post by Grant A. on 2008-12-09
8.6GB HDD? I would recommend you buy a larger disk, as due to Christmas, hardware has gotten very cheap.

---

### Post by smartboyathome on 2008-12-10
> **Grant A. said:**
> 8.6GB HDD? I would recommend you buy a larger disk, as due to Christmas, hardware has gotten very cheap.

That actually depends on the Motherboard. Some older motherboards can't handle over a certain amount of GBs on a HDD.

---

### Post by handy on 2008-12-10
> **Grant A. said:**
> 8.6GB HDD? I would recommend you buy a larger disk, as due to Christmas, hardware has gotten very cheap.

:lolflag:  I have other drives. I don't want to store data on it, I want it to be an rtorrent server, which I'll drop torrents into over the network from my main box, after which rtorrent will control the torrents & save them onto a NAS that I will make as soon as I find the right bit of gear at the rubbish dump for the job. :-)

> **smartboyathome said:**
> That actually depends on the Motherboard. Some older motherboards can't handle over a certain amount of GBs on a HDD.

I tried Arch on it today on both the original drive & an 80Gb IBM Deskstar, & could not get it past a kernel panic when it attempted to format the partitions. :-(

So I downloaded Ubuntu Server 8.10 & it failed, I tested the CD & it failed the test. So I just downloaded & burned Ub Server 8.06, & it just froze up when checking the CD as well.

I don't really think that there is anything wrong with the CD's unfortunately.

Anyway, if I can't get past this problem, for $5- I will have picked up some useful parts for my growing PII & PIII collection.

It's funny really, a few years ago, when I closed my business, I gave away most all of the stuff that I'm now happily collecting again. 

You never know what the future will bring eh!?

[I]**[Edit:]** The motherboard in this old box accepts both the AT & the ATX PSU's, it also has both CPU slot & socket & an AT keyboard plug.

So I think I can safely say that it is a mongrel of a motherboard.[/I] :-)

***[Edit2:]**  The mongrel motherboard is beyond redemption from its designed for windows hell.  So I'll see what the tip man has put aside for me next Tuesday. :-)*

---

### Post by handy on 2008-12-24
Finally a potentially useful box was available at the tip, unfortunately it's an evil Compaq Deskpro.  But hey, for $5- I'll buy & have a look at any PII & above box. :-)  

I remember when I used to fix computers that I had a true dislike for the big manufacturer's rigs; Compaq, HP, Packard Bell, Acer, IBM, DEC, Del, as they usually didn't comply with the otherwise universal standards for computer component design.  

You could find that an ATX PSU from any one of these companies would be a non-standard shape, &/or may have a non-standard directly connected power switch, though the ATX standard is to have the motherboard controlling the PSU; the Deskpro has this abnormal switching *feature*.  

You could also find the PSU's power to the motherboard plug to be on a particularly short set of cables which of course makes sure that the PSU will only work on a tiny number of other motherboards; this is also another *feature* of the Deskpro.  

You would also find that some manufacturers included a tiny non-standard partition at the beginning of the hard disk drive, that had tools installed without which the HDD is unable to boot; the Deskpro has this *feature* as well.  

Being able to access the BIOS on some machines needs a special boot floppy, which I'm sure you guessed already that this is also a *feature* of the Deskpro.

& last but not least, in the bad old days the BIOS batteries were very often soldered onto the motherboard, I bet you can guess how the Deskpro's battery was fixed?  No simple pop out, pop in, replacement of a CR2032 here.

So I stripped out the little that was of use in the Deskpro & will return the carcass to whence it came.

Hopefully some good suitable boxes will turn up after xmas / new year, for me to build a backup IPCop box & a combination FreeNAS torrent slave box, with a backup (apart from the drives) box for that job too.

If not I will have to spend money on the problem & build up the NAS/torrent box.

---

### Post by Francewhoa on 2008-12-24
Thanks for this useful Post Handy. I'll have a look at IPCop.

---

### Post by handy on 2008-12-25
> **Onopoc said:**
> Thanks for this useful Post Handy. I'll have a look at IPCop.

No worries, I think you will be suitably impressed, it is so well refined.

---

### Post by chachawpi on 2008-12-25
I use PFSense on a crappy old Dell laptop with a Celeron processor and 256MB of RAM.  That thing is a rock.

---

### Post by handy on 2008-12-25
Depending on the services running & the number of computers using the gateway, on these firewall/proxy servers the CPU barely & rarely goes above idle, even though they are using slow old PII's or even slower.

I'm finding this new area I'm playing in to be quite an education.

I setup FreeNAS on my test machine today just to play around with it, & it too has a beautifully polished web interface.  It is so much better than I thought it would be, I'm very impressed.

---

### Post by K.Mandla on 2008-12-25
Actually you've sparked my interest now too. I know I have a spare computer around here somewhere I can test with. ... :-k

---

### Post by handy on 2008-12-25
> **K.Mandla said:**
> Actually you've sparked my interest now too. I know I have a spare computer around here somewhere I can test with. ... :-k

Understatement again? :-)

If you & I keep promoting what some consider to be worthless hardware, we'll create a price rise & a shortage of the things. :)

Which surely would be better than scrapping still useful technology.

---

### Post by tad1073 on 2008-12-25
I am interested also. 

I would like to create a file/media server with [my old computer](http://ubuntuforums.org/album.php?albumid=796) but don't know where to start. It has xp on it now.

With the above computer, I also have a raid controller, scsi controller, 3 x 9.1 Gb hdd's, and a 15 Gb hdd.

---

### Post by handy on 2008-12-25
> **tad1073 said:**
> I am interested also. 

I would like to create a file/media server with [my old computer](http://ubuntuforums.org/album.php?albumid=796) but don't know where to start. It has xp on it now.

With the above computer, I also have a raid controller, scsi controller, 3 x 9.1 Gb hdd's, and a 15 Gb hdd.

I'm all but a total beginner in this stuff, so be warned.

You want to know as best you can all of the potential possibilities that you will want the server to meet.  e.g.

Building a FreeNAS/torrent slave/media streamer is possible, but if you want to add anything else you may very well find that if it can/can't be done, or it is not as good as building on something other than FreeNAS.

I will put some more time into my test install of FreeNAS & see how it goes serving video. I'll let you know how it goes after I have done that, should be within the next 24 hours some time. :-)

Go to [***_FreeNAS & download_***]("http://www.freenas.org/index.php?option=com_versions&Itemid=51") the LiveCD & have a look, you don't even have to install it to use it, I reckon you will be quite impressed by the quality.  It is only a 68Mb download too.

The [***_FreeNAS Documentation_***]("http://www.freenas.org/index.php?option=com_openwiki&Itemid=30&id=start#documentation") is excellent.

---

### Post by K.Mandla on 2008-12-26
> **handy said:**
> Understatement again? :-)
8-[ :-\"
> **handy said:**
> If you & I keep promoting what some consider to be worthless hardware, we'll create a price rise & a shortage of the things. :)
Ooh, I hadn't thought of it that way. I better keep my mouth shut, or suddenly all these old laptops will be in demand. :lol:

---

### Post by mips on 2008-12-26
> **K.Mandla said:**
> Actually you've sparked my interest now too. I know I have a spare computer around here somewhere I can test with. ... :-k

Same here. Problem is all these spare computers eat a lot of power and are pretty noisy.

I would love to have something that is fanless/noiseless and low in power usage. I would love to add router/firewall capability to it.

The VIA chipset seems ideal for this but it's hard to come by over here and pretty pricey.

---

### Post by handy on 2008-12-26
> **mips said:**
> Same here. Problem is all these spare computers eat a lot of power and are pretty noisy.

I would love to have something that is fanless/noiseless and low in power usage. I would love to add router/firewall capability to it.

The VIA chipset seems ideal for this but it's hard to come by over here and pretty pricey.

The Dell Optiplex GX 150 (PIII 733Mhz) that I'm using as my IPCop box is barely audible in my converted bedroom/office, a PII apparently is getting down around the VIA MiniITX range of power consumption (from what I've read).  From memory the GX 150 only had a 90 Watt PSU, its a little one anyway, with a small fan.  The CPU rarely does more than idle, & the drive barely ever spins, usually once in the early hours of the morning when it does an auto-update of the ClamAV's virus signatures.

---

### Post by K.Mandla on 2008-12-26
> **handy said:**
> The Dell Optiplex GX 150 (PIII 733Mhz) that I'm using as my IPCop box is barely audible in my converted bedroom/office, a PII apparently is getting down around the VIA MiniITX range of power consumption (from what I've read).  From memory the GX 150 only had a 90 Watt PSU, its a little one anyway, with a small fan.  The CPU rarely does more than idle, & the drive barely ever spins, usually once in the early hours of the morning when it does an auto-update of the ClamAV's virus signatures.
And they looked really good painted red and black.

[http://kmandla.wordpress.com/2008/12/26/the-red-hot-ubuntu-love-machine-revisited/](http://kmandla.wordpress.com/2008/12/26/the-red-hot-ubuntu-love-machine-revisited/)
> **mips said:**
> Same here. Problem is all these spare computers eat a lot of power and are pretty noisy.

I would love to have something that is fanless/noiseless and low in power usage. I would love to add router/firewall capability to it.
This is completely esoteric, but I once found a 400Mhz Celeron that was shockingly quiet, particularly for a desktop machine. For a heat vane it had this bizarre fork-shaped metal fin that rode alongside the processor, and the power supply had no audible fan in it (it was a very low power PS). If it wasn't for the occasional grunt from the hard drive, I couldn't tell if it was on or not. 

I think I gave it away as a free machine. I should've taken pictures.

---

### Post by handy on 2008-12-26
> **K.Mandla said:**
> And they looked really good painted red and black.

[http://kmandla.wordpress.com/2008/12/26/the-red-hot-ubuntu-love-machine-revisited/](http://kmandla.wordpress.com/2008/12/26/the-red-hot-ubuntu-love-machine-revisited/) 

Wow, it looks so much faster than mine.  Though it also looks hotter. :lolflag:

---

### Post by handy on 2008-12-26
***@tad1073:*** I have a problem with my NFS networking, that I haven't been able to sort from reading the doc's on the web.  I'm sure it is a simple thing, (probably in the /etc/exports file) so I contacted windependence (who is a master of FreeNAS in his professional life) who had offered me help in the past.  He is busy in post xmas stuff atmo, but is happy to sort it out with me over the weekend, he'll go through the FreeNAS browser interface settings & check the NFS setup out, so this will give me & anyone else who is moving into new territory some very valuable info' for now & future reference.

Don't you just love community? :KS

---

### Post by smartboyathome on 2008-12-26
I might have tried this, if I didn't get the parts for my media center for christmas and ReLectronics was open so I could get a second SMC Ez PCMCIA card. Only problem: my internet is already so dang slow with all the stuff I had to put on it, this would make it even slower so it was near unusable. :(

---

### Post by handy on 2008-12-26
> **smartboyathome said:**
> I might have tried this, if I didn't get the parts for my media center for christmas and ReLectronics was open so I could get a second SMC Ez PCMCIA card. Only problem: my internet is already so dang slow with all the stuff I had to put on it, this would make it even slower so it was near unusable. :(

IPCop didn't make my internet slower, if anything it is faster, as Linux handles packets of data better than windows & windows based modem/routers.

I have ClamAV & Privoxy running & there is NO slowdown.  I think it is incredible.  

I wouldn't have ClamAV running at all if it was slowing things down, as I don't need anti-virus software.

Also, if you have enough machines on using the internet on your LAN you will benefit from the web proxy service that is available in IPCop.  I run it, though it never gets used on my tiny LAN, though it is necessary for another service that I'm running (the name of which slips my mind atmo?).

The FreeNAS box won't have any more to do with the internet than being a torrent slave, it comes with Transmission installed so it is not hard to setup.

---

### Post by smartboyathome on 2008-12-26
> **handy said:**
> IPCop didn't make my internet slower, if anything it is faster, as Linux handles packets of data better than windows & windows based modem/routers.

I have ClamAV & Privoxy running & there is NO slowdown.  I think it is incredible.  

I wouldn't have ClamAV running at all if it was slowing things down, as I don't need anti-virus software.

Also, if you have enough machines on using the internet on your LAN you will benefit from the web proxy service that is available in IPCop.  I run it, though it never gets used on my tiny LAN, though it is necessary for another service that I'm running (the name of which slips my mind atmo?).

The FreeNAS box won't have any more to do with the internet than being a torrent slave, it comes with Transmission installed so it is not hard to setup.

Ok, thanks for the info. I have 3 comps running on the internet (which has to go through a set of powerline ethernet adapters, a wireless router, a wireless router, and a wireless extender). If I had another machine (this one's already commited to being a media center front end), then I would do this.

---

### Post by handy on 2008-12-26
> **smartboyathome said:**
> Ok, thanks for the info. I have 3 comps running on the internet (which has to go through a set of powerline ethernet adapters, a wireless router, a wireless router, and a wireless extender). If I had another machine (this one's already commited to being a media center front end), then I would do this.

IPCop has really simplified the process of setting up & organising your network through it.  See if you can find an old box at the tip for near nothing, (as you may have already read a dozen times in the forum) that is what I did. :lolflag:

An 8Gb drive on a PII with 256Mb of RAM should be more than enough.  If you add Copfilter & depending on the services that you run, you could possibly need more RAM.  I'm fine with 256, but when I find another 256 in a box at the tip I'll add it for good measure, which will have the motherboard at its max of 512Mb.

---

### Post by jflaker on 2008-12-26
$5 is not bad, but you can probably find computers for free ([http://freecycle.org]("http://freecycle.org"))

Many people just "junk" their old systems because they got a new one or because they became unbootable........Likely that there is nothing wrong with them except that windows lost its mind.

---

### Post by smartboyathome on 2008-12-26
> **jflaker said:**
> $5 is not bad, but you can probably find computers for free ([http://freecycle.org]("http://freecycle.org"))

Many people just "junk" their old systems because they got a new one or because they became unbootable........Likely that there is nothing wrong with them except that windows lost its mind.

There are also many local recycling stores which you can get free or cheap refurbished computers from. ReLectronics here is what I use, its great for spare parts and such (I haven't gotten a refurbished computer from it... *yet* ;)).

---

### Post by tad1073 on 2008-12-26
> **handy said:**
> ***@tad1073:*** I have a problem with my NFS networking, that I haven't been able to sort from reading the doc's on the web.  I'm sure it is a simple thing, (probably in the /etc/exports file) so I contacted windependence (who is a master of FreeNAS in his professional life) who had offered me help in the past.  He is busy in post xmas stuff atmo, but is happy to sort it out with me over the weekend, he'll go through the FreeNAS browser interface settings & check the NFS setup out, so this will give me & anyone else who is moving into new territory some very valuable info' for now & future reference.

Don't you just love community? :KS

I just installed Ubuntu 8.10 Server Edition on that old computer but it will be a while before I have it up and running. I am on wireless at my mom's house, where I live also, and she doesn't like me messing with her stuff. I have a dedicated dsl line in my room but the moden will not be here until Monday. Maybe that is a good thing, it will give me some time to read up on the server.

---

### Post by handy on 2008-12-26
***@jflaker** & **smartboyathome:*** I live out in the sticks, there is only 2500 people in the wider area, so my only real choice of supply of dirt cheap computers is at our local tip where they recycle things, which is great. Most people don't have any idea of the valuable uses that old computers can be put to, apart from the people who know to head to the tip & buy a $5- computer when they need to replace a power spiked PSU in their home machine.

---

### Post by handy on 2008-12-27
When windependence gets back to me & we go through the setup of FreeNAS I'll post a pointer to the thread in this one too.

I'll probably write a how-to or two on IPCop/Copfilter & FreeNAS & put them on my website.  I'll have a go at larch as well. 

If I can get larch to make a liveDVD copy of my installed Arch I'll do a how-to on that to.  Though my very limited bash scripting knowledge may end up stopping me on that one.

---

### Post by handy on 2008-12-31
I've been battling with my FreeNAS installation on & off for some days.
I did need a little assistance due to my ignorance of NFS, but know now that NFS really is a very simple networking system.

I had been waiting for a member here to find some time in his very busy schedule to help out as he has been flat out since xmas.

Anyway I got good help from others & from him today, but I still could not get my client connection to work reliably.  

In the end I used the BIOS to turn off the on-board NIC that I had been using & turned the 2nd on-board NIC on (yes, this motherboard has 2 network interface cards).  Rebooted FreeNAS, quickly configured it to use the new NIC & then rebooted Arch.

Now it is working properly.  Or at least it has been copying an 11.3Gb directory with over 1600 files in it from the client over to the FreeNAS box.

I must admit that I was feeling pretty dumb, not being able to understand why I couldn't get things to work properly. :-)

I'll set up the Transmission torrent slave & test it out after this file copy is finished & let you know how well it works.

I will also get around to writing how-to's for this stuff, as my threads on the subject are a bit painful to go through if you are trying to get something done. ;-)

---

### Post by K.Mandla on 2008-12-31
I tried out the FreeNAS CD for an hour or so the other night, and it was very impressive. Thanks for mentioning these; I don't think I would have spotted them otherwise. Cheers!

---

### Post by handy on 2009-01-01
***@K.Mandla:*** Glad to hear you are enjoying these great tools.

I am learning a lot about networking since I started playing with IPCop & FreeNAS, which is great.

I'll end up writing how-to's on this stuff for the dual purpose of making it easier for someone else who wants to have a go, & easier for me sometime in the future when I have to set it all up again & I've forgotten the lot!

Today I've been learning what I can to optimise NFS, which doesn't have a lot you can do with it, though I eventually stumbled on some help in the [***_FreeNAS online knowledge base_***]("http://www.freenaskb.info/kb/?View=entry&EntryID=129"), about someone having slow NFS.  

So using the web configuration interface, I set the *FreeNAS / Network / LAN / Advanced Configuration / Type / to _autoselect_*  

It had been set to 100baseTX which had caused confusion at each end of the cable.

I rebooted FreeNAS, & rebooted my client, then tested NFS's speed by copying a selection of large & small files (the identical group used for all my speed tests today), from the client, to /freenas, during which I found that the speed had gone up from around 2Mb/s to 11Mb/s.

This made me very happy. :-D

Here is a link to the thus far long & drawn out thread, that is still going, as I'm going to test out quite a few things with FreeNAS, like software RAID-5, iSCSI, bonding NICs & who knows what else...

***_[http://ubuntuforums.org/showthread.php?t=1025045](http://ubuntuforums.org/showthread.php?t=1025045)_***

---

### Post by ghindo on 2009-01-02
Just popping into this thread to thank the OP for it.  The subject of breathing life into older hardware and these niche operating systems are really really interesting and I look forward to more on your experiences with FreeNAS. :)

---

### Post by handy on 2009-01-02
> **ghindo said:**
> Just popping into this thread to thank the OP for it.  The subject of breathing life into older hardware and these niche operating systems are really really interesting and I look forward to more on your experiences with FreeNAS. :)

Thanks it's nice to know that you are enjoying my rant, or is it a rave? :-)

Today I've been reading up on RAID & other things associated with FreeNAS & hardware.

One thing I found very interesting was that with IDE drives & RAID, it is dangerous to your data to put more than one drive on a cable.  So a master IDE drive is it!

I think(?) that SATA gets past this problem, I haven't found confirmation on that yet.  I have a board here that has two separate SATA-1 controllers on it, each supporting two separate drives. Hopefully if one drive goes down, it does not take the controller & therefore the other drive, as is the case with IDE & software RAID.

Here is a link to some FreeNAS knowledge base information on software RAID:

***_[http://www.freenaskb.info/kb/?View=entry&EntryID=259](http://www.freenaskb.info/kb/?View=entry&EntryID=259) _***

---

### Post by mips on 2009-01-02
> **handy said:**
> 
One thing I found very interesting was that with IDE drives & RAID, it is dangerous to your data to put more than one drive on a cable.  So a master IDE drive is it!

I think(?) that SATA gets past this problem, I haven't found confirmation on that yet.  I have a board here that has two separate SATA-1 controllers on it, each supporting two separate drives. Hopefully if one drive goes down, it does not take the controller & therefore the other drive, as is the case with IDE & software RAID.

Sata controllers also do master & slave. Usually S0&S1 are on the same controller but I don't know if the effects are the same as for normal ATA.

---

### Post by handy on 2009-01-02
> **mips said:**
> Sata controllers also do master & slave. Usually S0&S1 are on the same controller but I don't know if the effects are the same as for normal ATA.

If I stumble upon info' about the reliability of the SATA controllers in the case of a disk failing I'll post it.

I've been playing around with both the SATA controllers on the GA-K8NS Ultra-939 motherboard, with no luck.  The Silicon Image Sil3512 controller would not work in RAID either way - soft or hard.

The nForce3 almost gets there but won't mount. I may be able to get this one to work with a little more study.

---

### Post by mips on 2009-01-02
> **handy said:**
> 
I've been playing around with both the SATA controllers on the GA-K8NS Ultra-939 motherboard, with no luck.  The Silicon Image Sil3512 controller would not work in RAID either way - soft or hard.


My old MB was very close to that one, GA-K8NXP-9, with he same chipset but I never tried RAID on it, only ever used LVM. i would not know what to do if raid failed thats why I simply backup to a second external drive.

---

### Post by handy on 2009-01-02
> **mips said:**
> My old MB was very close to that one, GA-K8NXP-9, with he same chipset but I never tried RAID on it, only ever used LVM. i would not know what to do if raid failed thats why I simply backup to a second external drive.

I have used the sil3512 controller's RAID-1 years ago, prior to my dumping windows.

From what I read, you are safer using the soft RAID in FreeNAS than the chips on motherboard routine.  Though the expensive RAID PCI-e cards seem to be the best solution of all for those that need it & can afford it.

I was thinking if I could get two SATA drives running in soft RAID on this Gigabyte board I'd use it as my FreeNAS server.  

I'd shut down everything I can in the BIOS, I have already put the lowest speck graphics card I could find laying around here in it, in an attempt to save on electricity. 

If it works out ok, maybe I'd water cool it in an attempt to shut it up. :lolflag:

---

### Post by mips on 2009-01-02
> **handy said:**
> 
I'd shut down everything I can in the BIOS, I have already put the lowest speck graphics card I could find laying around here in it, in an attempt to save on electricity. 

If it works out ok, maybe I'd water cool it in an attempt to shut it up. :lolflag:
That MB is serious overkill for a NAS box if you ask me, makes an excellent desktop though :)

Just submerse it in linseed oil :)

---

### Post by handy on 2009-01-02
> **mips said:**
> That MB is serious overkill for a NAS box if you ask me, makes an excellent desktop though :)

Just submerse it in linseed oil :)

I agree. 

I'm trying not to buy another motherboard. 

The computer supply at the tip  has dried up lately.  Though it may just be the holiday season, time will tell?

I used diesel oil once years ago, it had an interesting effect on the way dust stuck to the rotor, it certainly quietened down the fan though. :lolflag:

---

### Post by mips on 2009-01-03
> **handy said:**
> 
The computer supply at the tip  has dried up lately.  Though it may just be the holiday season, time will tell?

Maybe wait a week or so and then people will probably throw out the old stuf if they upgraded over xmas. People are probably still in holiday mode.



> **handy said:**
> 
I used diesel oil once years ago, it had an interesting effect on the way dust stuck to the rotor, it certainly quietened down the fan though. :lolflag:

Lol. I hope you used bio-diesel :)

---

### Post by handy on 2009-01-03
> **mips said:**
> 
Maybe wait a week or so and then people will probably throw out the old stuf if they upgraded over xmas. People are probably still in holiday mode.


That is what I'm hoping. :-)

> **mips said:**
> 
Lol. I hope you used bio-diesel :)

:lolflag:

At that stage of the game, I didn't even know such a thing existed!

The gradual dissolution of ignorance really is quite phenomenon, don't you think?

---

### Post by handy on 2009-01-03
> **mips said:**
> That MB is serious overkill for a NAS box if you ask me, makes an excellent desktop though :) 

Whether I do have to buy a motherboard to suit the FreeNAS job (or not), the problem I do have, is that I find myself a bit over 3 years out of the computer hardware game.

I don't know what is going on in the hardware side of things any more? (I happily don't seriously study it any more)

So I'm open to (actually I'm requesting) suggestions on what hardware would suit my needs.

I too (as a few other readers of this thread, I'm sure) would like to know just how much money/in the end, do we have to spend on hardware, to get no less horsepower than we require to download some torrents whilst simultaneously watching a movie on at least one other computer in the house over a 100/Mbit LAN?

Me, I just need to know whether a nice quiet, low energy Mini-ITX motherboard will do it for me, & if so, what the CPU/RAM combination would be.  I'm also open to intel's Atom, as they make Mini-ITX motherboards that are suitable also.

---

### Post by mips on 2009-01-03
I think most new hardware would be overkill for a home NAS box doing whaty you want it to do, download torrents & stream a movie.

I'm pretty sure the VIA stuff will be up to the job but it is best to do some research and poke around the hobbyist forums for clarity.

Edit:

Just found this, [http://www.pcadvisor.co.uk/reviews/index.cfm?reviewid=103539&pn=1](http://www.pcadvisor.co.uk/reviews/index.cfm?reviewid=103539&pn=1)
Runs on a VIA Artico Pico

I dont think cpu power is that important, I mean how much cpu is used downloading torrents and copying a file over ethernet? My 1.4GHz laptop can do way more than that and it's 4yrs old. I think the ticket here is to look at power consumption.

[http://www.pcadvisor.co.uk/reviews/index.cfm?reviewid=103539&pn=1](http://www.pcadvisor.co.uk/reviews/index.cfm?reviewid=103539&pn=1)
[http://www.mini-itx.com/](http://www.mini-itx.com/) Front page article looks like it is custom designed for you except it would be better with the lower power Via Nano CPU instead of the C7.

---

### Post by handy on 2009-01-03
Thanks mips, you surely are a great resource of information; if you don't know it, you get it off the web consistently quicker than anyone I have ever come across.

Well done. :KS

---

### Post by mips on 2009-01-03
> **handy said:**
> Thanks mips, you surely are a great resource of information; if you don't know it, you get it off the web consistently quicker than anyone I have ever come across.

Well done. :KS

Thanks but it was pure fluke, I just went to the mini-itx site and there it was :)

---

### Post by handy on 2009-01-18
Surprisingly to both the guy who runs the local tip & myself, there have been NO computers come in since the xmas new year period?

I asked a friend who still does a bit of professional computer work to give me a quote on the parts I need to build a new MiniITX FreeNAS server, but his supplier was really expensive.

The other person on these forums who I asked for a quote a couple of weeks ago has never got back to me, so he mustn't be interested.

So, I'm thinking of just buying the 2 x 1Tb SATA-2 drives & an IDE to SATA adapter card, & using my testing box as the FreeNAS box when required until I feel like coughing up for the new stuff.  In that time a suitable old machine might turn up at the tip for $5- which would be very convenient.

I don't remember whether I mentioned earlier in this thread, the problems associated with a drive failing on an IDE bus (either the Primary or Secondary bus, as was standard on motherboards before SATA); this apparently often causes the 2nd drive (if it exists) sharing the same bus, to become inaccessible.  

Which can be ok if you are using 2 disks on the same bus in RAID-1 config', but really no good if you have a RAID-5 or similar setup, as they can not tolerate loosing 2 drives simultaneously.

I still don't know whether SATA controllers suffer from the same results when a drive fails on a SATA bus?

I have a question on this topic in the Server section of these forums & another in the FreeNAS forums (which are unfortunately very slow).

My intention is to set up 2 x 1Tb drives on the same IDE bus using the aforementioned adapter, in a software RAID-1 array.  If one of these new drives fails, & I can't access the 2nd drive, it won't be a big problem, as the machine is just for personal use & I can easily pull out the bad drive & leave the good one in, turn off the RAID-1 until I get a replacement drive.

That's where my thoughts are at at the moment anyway. :-)

[I]**[Edit:]**  What I have learned in the months following this post, is that RAID is a very poor choice for use as a backup system.  There are some varieties of RAID that are better than others, but we are talking lots of money for the controller cards & for the drives.  Some forms of RAID are offer the inherent ability to be the quickest form of replicating corruption from one drive to another, known to man. :-|

For people in the professional world the right type of RAID, in combination with the existence of at least one other backup, that is on a separate machine & ideally at another physical (different building) location, may be required, for both speed & to meet the storage space requirements.

So basically, for backup, avoid RAID unless you absolutely have to use it, & then have another separate machine to hold a backup.[/I]

---

### Post by handy on 2009-01-20
Still no computers at the tip, so I went to see a friend of mine that spends a lot of time at the auctions, one of the things he does is buy old computers, monitors & whatever else that he can salvage the scrap metal out of & sell.  

He had just taken a large van full of PII/PIII's to the scrap metal merchants.  So I missed out on them, but he had a PIII 1Ghz box which he gave me, as well as a Digital BA356-RA external SCSI drive box.  It has 7 drive slots - draws - that plug straight into the backplane.  This is a pretty flash bit of gear, it would have been worth a fortune 10 years or so ago when it was new.

It has some 4.3Gb drives & an 18Gb Seagate Cheetah in it.  From what I have read on the web, it handles a variety of types of SCSI drives, it has 3 different coloured draws, each colour represents the type/version of SCSI that it will max out at.  You can put a faster type of SCSI drive in a slower type of SCSI draw, & it will work at the draws top speed, not the drives. The Cheetah is an Ultra2 SCSI Wide, which is the fastest SCSI that the box can handle, I think.

I have an old PCI SCSI 1 or 2 (I'm not sure yet) card & 50 pin cable, which I will have to buy an adapter for so I can play with this contraption.  Even though there are drives using various types of SCSI in the box you can run them all on SCSI-1, 2 or 3 if you choose.

I had a look at the price of SCSI drives & boy they are still really expensive.  I really could not afford to populate this thing with the couple of terabytes that I need.  I also know that I don't need the SCSI speed that the new drives would provide for my FreeNAS setup, as it would be wasted by my LAN speed bottleneck.

It is a real shame this thing isn't built for SATA drives.

Anyway, I'll get an adapter & see if I can get it working for the hell of it. :-)

Now that I have the PIII, I can get on with setting it up as the FreeNAS box.  I will have to order a couple of 1Tb drives & something to connect their SATA cables to.  I heard on the FreeNAS forums today that the VIA PCI SATA cards work, & with 1Tb drives.  I'll certainly have my fingers crossed if I buy one of those cards, which would be the best solution as I wouldn't have to have the two SATA drives running on an adapter on one of the IDE buses if I had a SATA card.  

It should be a faster & hopefully more reliable setup if the SATA drives are attached to a SATA controller & not an IDE controller.

---

### Post by mips on 2009-01-27
Hey Handy, look what WD made just for you,
[http://www.theinquirer.net/inquirer/news/653/1050653/biggest-hard-drive-world-arrives](http://www.theinquirer.net/inquirer/news/653/1050653/biggest-hard-drive-world-arrives)

Two of those puppies and you can backup the Internet :)

---

