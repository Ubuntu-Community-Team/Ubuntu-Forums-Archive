---
title: "Ubuntu boot problem"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by iuventus on 2012-01-09
Ok first of all Ubuntu 11.10 is awesome!!!

Here is what I did (oops)

My PC originally came with WXP Pro
Last year I updated to W7 64bit (works well...adressed a few driver issues, but all good!
This year I found Unbuntu 11.10 (as mentioned above...Awesome!)
I installed 11.10 with wubi inside my windows OS (W7 Home)
I only had 10gb free space in hd but it worked fine
Followed through a few forum searches and got my drivers working.
Played with 11.10 for a day or so (Awesome!)

I took it a little further and stated downloading apps. All good for a little while. Early this AM i rebooted and got a purple screen (ubuntu default) with nothing else? (boot problem?)

back to windows right now :(:(:(

I can only assume there is a problem based on apps/packages I installed?? I had several packages installing at the same time (probably bad idea)

So in the interest of learning what went wrong??
how can i check why it doesn't boot into Ubuntu any more?

I can find,open,view all my Ub files (.cfg, etc.)
but I don't know what i looking for?

my other question is: Can i save my driver updates from my previous Ub install?

what is the "best" way to do a full install of Ub 11.10
I mean...clear hd space, partition drive, continue running in W7OS, etc.

I still have all my personal docs (stuff i want to keep) in windows (but i want to move them over later)

I know this is long winded but perhaps someone could suggest the best way to fix or reinstall Ub for permanent and best performance?

thx in advance

Below: are my PC specs (thought this might help)


Intel Pentium 4 processor 650* with HT Technology 
(3.4-GHz, 800-MHz FSB, 2-MB L2 cache)
 	Operating System	 Genuine Windows XP Professional
 	Cache	2048 KB L2 cache
 	2-GB 400-MHz DDR SDRAM (1-GB SODIMM in slots 1 and 2)
 	Hard Drive	100GB 5400 RPM
 	Display	17-inch color TFT WSXGA+ BrightView with 1680 x 1050 resolution (up to 16.7M colors internal)
 	Graphics	ATI Mobility Radeon X600
 	Video Memory	128MB
 	Audio	SoundMAX audio with Pure Audio noise reduction with headphone and microphone jacks
 	Fixed Optical Drive	DVD+/-RW
 	Communications	56K modem, integrated 10/100/1000 NIC
 	Integrated Wireless	Broadcom Wireless 802.11b/g WLAN

---

### Post by Mark Phelps on 2012-01-09
The best approach for long-term Ubuntu use is to install it using the Linux filesystem in its own partitions.  Not only does that free you from the dependency on Windows loader working (to get the OS selection screen), your're also NOT in a virtual file system -- which allows it to run a little faster.

Downside is that you have to mess around with partitioning, being careful to NOT use the Ubuntu installer, or GParted, to shrink the Win7 OS partition. This also overwrites the MBR, making restoring it a task to be dealt with later.\

But, most important, it risks overwriting the Win7 install -- if the wrong partition is selected during Ubuntu install for formatting.

If you're interested in doing dual-boot, then let us know -- and I'll post another, longer, post with some details.

---

### Post by wolfen69 on 2012-01-09
A wubi install is ok for trying ubuntu, but a "real" install is much preferred. First, backup your stuff to an external drive and defrag windows. Then boot directly to the ubuntu cd and select "try ubuntu" to make sure all of your hardware is compatible.
 
Then you can start the installation and choose "install ubuntu along side of windows". Then you will see a "slider" that you use to choose how much hard drive space you want ubuntu to use. I personally, would give it at least 40gb if you have the room. The rest is pretty much self-explanatory. Come back with any questions you may have.

---

### Post by bcbc on 2012-01-09
You could boot in recovery mode and try to fix package errors. If it's Wubi it probably boots straight to a root prompt, so run:
```
dpkg-reconfigure -a
```

If you get a recovery menu, then it's probably the 'read-only' recovery menu, remount read/write (option 3) and select 'fix packaging errors'. Something like that. 

It's okay to reinstall and remove Wubi but it doesn't really answer why you got the problem in the first place.

---

