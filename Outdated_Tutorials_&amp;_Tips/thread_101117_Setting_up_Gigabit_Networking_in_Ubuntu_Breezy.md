---
title: "Setting up Gigabit Networking in Ubuntu Breezy"
date: 2005-12-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Mathboy on 2005-12-09
I've finally got gigabit networking working to my satisfaction in Ubuntu 5.10, and as it took me a while to figure some of these things out I thought I'd share my experience. 

*Disclaimer*: I'm a noob. :|  This stuff might be totally wrong. Please let me know if you see something that looks incorrect!

I'm only covering the gigabit-specific things, the wired ethernet troubleshooting post covers the basics. 


**_Cards:_**
Most cheap cards seem to be based on the Realtek 8169s chipset. While Breezy has a driver for these that seems to load without issue, I didn't have much luck getting good throughput with them. Their frame size choices in windows don't match up with other cards, and they have a max of 7000 instead of 9000.

The card currently in my server is a **D-Link DGE-530T**. These are readily available, cheap, and based on the seemingly good Marvell Yukon I chipset. The open source skge driver (a tidied up version of the sk98lin driver) in Breezy works with these cards. 


**_Jumbo Frames:_**
The frame size for standard 10/100 ethernet is limited to 1500. Using little frames on a gigabit network requires more CPU time and decreases throughput. Jumbo frames allow up to 9k byte frames to be used, *but only work if _every_ device on that network uses exactly the same size jumbo frame*! That means no mixing 10/100 cards and gigabit cards, and you'll need to either plug two machines together without a switch or use a switch capable of the jumbo frame size you wish to use. 

To give a rough idea of the goodness of jumbo frames, I've found that using standard 1500 byte frames gives about _double_ the real-world performance of 10/100 ("real-world" meaning in things like samba and scp, not in straight throughput tests like iperf). Switching to jumbo frames increases throughput to around _five times_ that of 10/100! Both do pretty well with tests like iperf, with only a minor difference between them. 

Note that if you do end up with a device that doesn't handle jumbo frames on your network, or two gigabit cards set to different jumbo frame sizes, then you can end up with packet fragmentation or loss. Your network will run *really* slowly. 


**_Ubuntu Settings:_**
The settings I made for good performance in Breezy were:
- Frame size to 9014 bytes ("ifconfig eth0 mtu 9000" - a frame size of 9014 corresponds to an MTU of 9000)
- Transmission Queue Length to 10000 ("ifconfig eth0 txqueuelen 10000")
- Window sizes to 1Mb (change the contents of the files rmem_max and wmem_max in /proc/sys/net/core/ to be 1048575)

To make these settings stick I made a S99customnetwork file in /etc/rc2.d which contained:
> 
ifconfig eth1 txqueuelen 10000
echo "1048575" >> /proc/sys/net/core/rmem_max
echo "1048575" >> /proc/sys/net/core/wmem_max

and changed permissions for it with chmod a+rx. Finally I added the following line to /etc/network/interfaces in the section for my gigabit nic to get the jumbo frames:
> 
mtu 9000



**_Windows XP Settings:_**
In Windows XP the main thing is to turn the jumbo frames on in the advanced driver properties, and set them to 9014 bytes. I also increased the number of transmit and receive buffers.


**_File transfer performance:_**
With those settings, file transfers through samba are a healthy 30 to 40 megabytes per second. :D 


**_Weirdness Encountered:_**
*Card not recognised:*
A couple times the skge driver failed to properly detect my card on bootup - it'd report a hardware mac address of 00:00:00:00 (etc), and claim it only had a FIBRE port, no twisted pair.  I haven't reliably reproduced this, but it happened both with standard kernel 2.6.12-9-386 and 2.6.12.10-686. :? I've added sk98lin to the hotplug blacklist just in case it's causing issues, and am still investigating.

*Settings change requires unplugging cable:*
Changing settings like the frame size seemed to sometimes require unplugging one end of the ethernet cable, stopping and restarting the drivers, and plugging the cable back in. Windows seemed particularly prone to getting in a weird state (in fact it might be the only culprit!).

*eth2 instead of eth1*
Some of us have ended up with our gigabit card on eth2, even though in dmesg it's eth0 or eth1. It seems that iftab gets an entry forcing certain mac addresses to map to certain eth#'s. You can see which eth's you're really using by looking at proc/net/dev.

*Cabling*
Some old cat-5 only had two pairs (four wires in it). Gigabit needs all eight wires. Also, I think gigabit crossover cables might be wired differently than some old crossovers for 10/100. With the 530T card you don't need a crossover cable though - you can plug two of these cards together directly with a straight cable :)

---

### Post by ubuntu_demon on 2005-12-09
I moved this thread to the customization section. Thnx for the information!

---

### Post by theQmaster on 2006-01-19
When I try to set 
ifconfig ethN txqueuelen 1000
I get
SIOCSIFTXQLEN: No such device

Any idea what's happening ?

Thanks,
Q

---

### Post by kleeman on 2006-01-20
I have a practical observation and a question:

I have gigabit connectors on a cluster and I see little speedup over 100Mbs transfer speed (I max out around 170Mbs). Gigabit should give you THEORETICALLY 1000Mbs.  Well I did an ordinary cp on one of the node disks and noticed a write speed of 180Mbs. Some research then revealed that disk read writes were often the bottleneck stopping gigabit transfers. 

Question: What speeds are you getting and if you are doing better than what I quote above what kind of disks have you got and what kind of r/w speeds do you get?

---

### Post by cphuntington97 on 2006-04-21
Is it possible that **not a single gigabit card** works perfectly out of the box on ubuntu breezy?

What's that you said, yours does? Great! Please post its make/model so I can get one. =D>

---

### Post by Rizado on 2006-04-21
[QUOTE=cphuntington97]Is it possible that **not a single gigabit card** works perfectly out of the box on ubuntu breezy?

What's that you said, yours does? Great! Please post its make/model so I can get one. =D>[/QUOTE]I have a somewhat related question. I've been thinking of moving my two ide hardrives to my server which have a gigabit card in it and buy one or two new sata drives and a gigabit card to this computer. Then my storage drives will be accessible from both my computers and maybe a laptop some time in the future. Now my question is will the speed too the storage drives be acceptable. I'm just going to use it as storage for games, movies and such things so I don't need the absolute top speed, but i don't want to end up with really slow transfers. Are there any gigabit cards that I should stay away from? Recompiling the kernel isn't a problem because I do that anyway.

---

### Post by moonlightcheese on 2008-02-15
well i'm kinda glad i found this.

been searching for info on getting my marvell yukon onboard gigabit nic on this DFI lanparty nF4 UT Ultra-D to transfer at a satisfactory speed for quite some time.  this seems more like a quick fix than a solution but i'm gonna try this later when i get back to my toy room.  i've got about 850GB to transfer <YIKES>

i'm having awful 10/100 speeds on my gigabit network.  hopefully this will solve the problem.

edit: SUPPORTING DATA!

[http://www.hep.ucl.ac.uk/~ytl/tcpip/linux/txqueuelen/datatag-tcp/](http://www.hep.ucl.ac.uk/~ytl/tcpip/linux/txqueuelen/datatag-tcp/)

---

### Post by bsh on 2008-04-11
> **Mathboy said:**
> **_File transfer performance:_**
With those settings, file transfers through samba are a healthy 30 to 40 megabytes per second. :D 


you should try to tweak samba too.
i didn't tweak my network settings, don't use jumbo frames, etc. but i did tweak samba, and i get 35-40mb/s too.
or i guess, if you do the above plus the samba tweaks, you can get even better speeds too.

---

### Post by Mathboy on 2008-04-27
> **bsh said:**
> you should try to tweak samba too.

Care to share the changes to smb.conf that you made? :)

---

