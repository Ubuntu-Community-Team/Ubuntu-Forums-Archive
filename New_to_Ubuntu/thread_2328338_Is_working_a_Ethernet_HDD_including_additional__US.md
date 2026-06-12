---
title: "Is working a Ethernet HDD including additional  USB HDD(WD My Cloud?) in Ubuntu?"
date: 2016-06-20
forum: New to Ubuntu
---

### Post by vladku on 2016-06-20
Current situation:
I have minimal installation of Ubuntu LTS currently 14.04, soon 16.04 too.
I have some external USB HDD (WD 2TB, Maxtor 0.5TB, ADATA 1TB). Now I thinking about central data storage accessible from Windows and Linux (in the best case in Android too).
I found WD MyCloud HDD I have not bought yer. It seems perfect, Ethernet interface pro connection to router and USB (with a USB hub) for connection of old USB HDDs. But official support for Linux is missing. 

I have already found:
[http://www.huffingtonpost.com/dulio-denis/wd-my-cloud-nas-on-ubuntu_b_5121961.html](http://www.huffingtonpost.com/dulio-denis/wd-my-cloud-nas-on-ubuntu_b_5121961.html) 
so I know that WD MyCloud could be accessible from lInux.

Questions:
1. Is it possible to access the old HDDs (any HDD, not specifically my ones) connected via USB to WD My Cloud in Ubuntu/Linux? Did you try anyone?
2. Is it possible to set up backup of WD My Cloud to external USB HDD connected to WD My Cloud automaticaly? At least to one of them?
[3. Is is possible set up and manage the HDD from linux (or should done only  from Windows). There is a web interface but I didnt find any  documentation for that. But it is optional, I can manage via Windows.]
4. Do you know any similar solution supported by Ubuntu like WD My Cloud (Ethernet drive with USB and automatic backup to them [for reasonable price])? 

I am newbie on this forum please consider if I made anything wrong (I appreciate any notes about that).
I am rather newbie in Linux, I like instruction for dummies.

---

### Post by TheFu on 2016-06-20
With a proper setup, any disks directly connected to a Linux system on your network can be made available both inside and outside your LAN.  On the LAN, it is fairly easy because you don't need to deal with DNS, routers, port forwarding and much security considerations.

**On the LAN:**
For Linux-to-Linux storage sharing, use NFS.
For Windows-to-Linux storage sharing, use Samba.
For Android-to-Linux storage sharing, use Samba or SFTP.

**Over the WAN (i.e. internet), **
It is simplest to use use sftp (or anything else that works over ssh (rsync, scp, sshfs) , but you can do other things provided a full VPN is configured like Samba or NFS.  

I would avoid the following setups:
* connecting any storage directly to any router with built-in storage features. Router firmwares tend to be buggy and making storage available is a "feature list" that is seldom properly secured.
* buying an internet-ready storage device - The companies making these devices don't have the best security history. They are just trying to sell stuff. Security is NOT the main goal for their products. Their setups require there systems (and people) to have access to all the files stored on your internal storage and probably provide access to your LAN.  They forget to mention these "other features" of their products.
* I don't use cloud storage for anything I'm not willing to have posted to the front-page of the New York Times. That is my rule.  Same goes for cloud backup services.  If you boil your backups down to just the essentials, a $40 500G HDD should be sufficient to hold the wedding photos and videos along with a *crapload* (technical term) of bank, broker, insurance paperwork.  Get 2 USB disks and make daily or weekly versioned backups to those disks, swapping out the 2 USB disk between home and work locations weekly. I use rdiff-back for versioned backups.

You can do all this yourself without THAT much effort, but I do understand the desire to pay someone $100/yr and use their program to backup stuff.  That isn't for me, but we're all different.

If you want something at automatically syncs files between some storage areas and your smartphone, there are a few different tools for this - owncloud gets most of the press, but there are 2-5 other mature projects too.  All of these tools should not be considered secure enough to make directly available over the internet. In short, use a vpn for them.  OpenVPN is the standard for this which is well supported by Linux, Windows, OSX, and Android.

BTW, you don't need a powerful system to run all these things.  On the low end, a Raspberry Pi can do it, provided the USB storage is externally powered.  I build a $120 system for storage, vpn, Calibre, Plex Server and a few other small tasks.  Reused some components to keep the price down, but the Intel Pentium G3258 CPU was $58. It is amazing.  Used a $50 motherboard, $20 in RAM .... some old case, disks, power supply, loaded up Ubuntu 14.04 (this was about 18 months ago) .... BAM - new storage server.  Since that build, I've added an eSATA 4 disk external array for $99 and dropped in some 4TB disks.  2 for main storage and 2 for local backups. This isn't important stuff, so if the house burns to the ground, I'm willing to lose my time-shifted TV recordings.  The G3258 has a peak power use of 54W, but usually only takes 30W or so.  It is WAY, WAY, WAY overpowered for my uses.  For a LAN storage server, wired gigabit ethernet is very important. I had an old Intel PRO/1000 NIC around, dropped that in. Seeing 920Mbps transfers until the disk buffers are full.  Then it drops to what the spinning disks support - about 100-120Mbps.  Different disks have different performance, so some old ones are more like 60Mbps.

If I were doing it today, I'd look for a 35W CPU with 3000+ passmarks for $60-ish and build the system around that. I'd avoid anything that needs DDR4 (too new to be cheap). I'd stay with Intel to avoid AMD on-board GPUs (that's just me).  My ubuntu 14.04 system is headless - no GUI, so that overhead is avoided.  I can understand if someone needed to run a lite GUI like LXDE or Mate.

Anyway, you have nearly unlimited options.  I'd stay away from "networked" storage which limits your connectivity. Using a normal Ubuntu system (or almost any popular distro) provides tremendous flexibility to provide whatever services you desire much cheaper than the NAS-specific devices. Plus your machine can be selected for the CPU and RAM **YOU want**, not what they tell you you need.  Just sayin'.

There is always a trade-off between time and money. It is your choice.

---

### Post by DuckHook on 2016-06-21
^^^ +1 to what TheFu says.

With inevitable differences in details, this is very similar to my setup too: using absurdly cheap salvage-ware and abandon-ware to build home-made servers that are 10 times more powerful and 100 times more versatile than commercial server "appliances" (like My Cloud). I too have assembled a motley collection of synced servers, dedicated backup boxes, a torrent server, etc for no more than $300 all in.

The only point that I differ from TheFu is that if you feel that home-spinning a server is presently beyond you, or is just too much trouble, a product like My Cloud is a workable solution, but with the following caveats:

[LIST=1]
[*]TheFu is dead accurate when he says that such appliances are security holes. They are built as appliances. Therefore, they don't auto-update by default. I have a My Book Live that was still running Debian Lenny! Updating it manually only brought it up to Squeeze. Both are EOL and no longer supported. There are no further updates for this appliance, and unless I am willing to HW hack it to install a serial port, then SW hack it to bring it up to Wheezy, I am basically resigned to running outdated OSes on this box with known security holes (eg Heartbleed).
[*]If you do set them up to auto-update, this introduces a whole new set of exposures, including the possibility that your appliance won't boot after one of these automatic updates.
[*]They come bundled with all sorts of bloatware that I just don't need: like a primitive web server to serve up that pretty but hobbled web page through which you administer the box, commercial media streaming services that are useless to me, an internal software RAID mirror for the OS, and lots of other junk that I haven't even bothered to look at. Aside from eating up already limited (and therefore valuable) resources, each service is another attack surface on an OS that is already EOL and therefore unsupported.
[*]These boxes are all, to varying degrees, underpowered and skimpy on resources. They are usually based on some underpowered ARM chip with maybe 250MB of RAM, which is absurdly chintzy and anemic by todays standards.
[/LIST]
For the same money, a knowledgeable tinkerer could build a box far more powerful, a lot more secure and infinitely more versatile. That's the beauty of Linux. But after having said all that, they do their simple jobs reasonably well, and there is a place for them, especially if home-spinning a server is just not your cup of tea.

---

### Post by TheFu on 2016-06-21
Came across a quote today that I liked:   
> Selling security vs doing security. The first one is a hell of a lot easier.
[https://www.reddit.com/r/privacy/comments/4ortwb/i_bought_and_returned_a_set_of_wifi_connected/](https://www.reddit.com/r/privacy/comments/4ortwb/i_bought_and_returned_a_set_of_wifi_connected/) is about webcams that have security issues because the vendor never expected anyone to resell/return them.  The comments by *interested parties* about how to hack into webcams everywhere provides a little idea about why you never want to use passwords to secure your storage/systems.

Security is hard.  Outsourcing it almost never works, IMHO.

---

### Post by DuckHook on 2016-06-21
*sigh*

Even for a guy long passed the point where any security hole could shock me, this one makes me shudder.

@OP

Moral of the story is that if you want to use a MyCloud, you are relying heavily on your router/firewall to protect your home network, and WD to have the security chops to properly implement a personal cloud appliance with appropriate sandboxing to protect your data and the rest of your network.

...and don't ever use a unit that seems to have been previously opened, repackaged and resold. I have no idea how one is supposed to ascertain this.

---

### Post by Habitual on 2016-06-21
Any WD product I buy gets wiped immediately with extreme vengeance.
I fire up gParted and nuke it to orbit.
Apply.
New
...
Then it's ready for work.

---

### Post by DuckHook on 2016-06-21
> **Habitual said:**
> Any WD product I buy gets wiped immediately with extreme vengeance.*chuckle*

If the OP tried that, s/he wouldn't have much of a NAS left. :lol:

---

### Post by Habitual on 2016-06-22
> **DuckHook said:**
> *chuckle*

If the OP tried that, s/he wouldn't have much of a NAS left. :lol:

I certainly don't suggest they do that.
It's designed for Windows. of course I'd format it. ;)

---

