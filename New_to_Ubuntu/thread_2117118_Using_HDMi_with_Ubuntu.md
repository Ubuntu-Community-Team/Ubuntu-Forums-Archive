---
title: "Using HDMi with Ubuntu"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by newgnu on 2013-02-17
I was just wondering if anyone has been able to use an HDMI cord to watch movies on there TV. Thanks.

---

### Post by PIE09gbLmgG6 on 2013-02-17
I use mine...but the tv I have is set up for smart devices...I pill up pbs on the laptop...have the cord and plug in...the video and audio sync perfectly...tv does tell me it has an hdmi source...

What I want to do is use ubuntu on a thumb drive and run off of that for the tv experience...learning more about ubuntu tv options myself...

ego-

---

### Post by kc1di on 2013-02-17
> **newgnu said:**
> I was just wondering if anyone has been able to use an HDMI cord to watch movies on there TV. Thanks.

Hello newgnu and welcome to Ubuntu,

I can use hdmi here with no problem on my laptop.  
that being said it has a lot to do with your video and sound card how well it works. 

I have to go to the audio mixer and set it for hdmi output in order to get sound working. 
good luck

---

### Post by sanderj on 2013-02-17
> **newgnu said:**
> I was just wondering if anyone has been able to use an HDMI cord to watch movies on there TV. Thanks.

Yes, no problem. Oh, wait: only video, no audio via HDMI on the TV.

---

### Post by gordintoronto on 2013-02-18
Select the HDMI in Sound Settings.

Newgnu: some laptops require a key combination to activate the HDMI, often cycling among: built-in screen, external screen, both. It's a battery-usage issue.

On my HP G62 laptop, I just plug in the HDMI cable and it works.

---

### Post by wp.rauchholz on 2013-06-07
I do have an HO G62 laptop.
I connect HDMI to HDMI of my Samsing LED TH Series 7. On the TV I can see that is has recognized that something is plugged in, but I have no audio nor video.
Do i need to install proprietary drivers?
I cannot find HDMI in sound seeting either. Any help is welcomed.

Thanks you, Wolfgang

---

### Post by gordintoronto on 2013-06-07
The TV is set to the appropriate HDMI port?

What version of Ubuntu?

As soon as I plugged in the HDMI connection, the same things appeared on the laptop and the TV.

Bear in mind that HP G62 is actually a family of computers. What do you see in Sound Settings/Hardware?

---

### Post by zemega on 2013-06-07
Perhaps you need to go to the Display panel and manually select to have output on the monitor/tv.

---

### Post by wp.rauchholz on 2013-06-09
According to the manual of Samsing I am using the right connection.
Again, Samsing TV sees that &#347;omething'is connected, but no audio/video.
on the Ubuntu side I cannot see the Samsing TV set in ´Systems Settings > Displays' not can I fiund an additional output in ´Sound settings' 

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise

*-display               
       description: VGA compatible controller
       product: Manhattan [Mobility Radeon HD 5400 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:3000(size=256) memory:c4440000-c445ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:4050(size=8)

---

### Post by gordintoronto on 2013-06-09
You have one of those hybrid video systems, with both Intel and AMD video adapters. See this long thread:
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by SeijiSensei on 2013-06-10
Go into the BIOS and set the video card to "fixed mode."  That will force it to use the ATI adapter and should fix the problem.  I have an HP dv6t with a Mobile Radeon connected over HDMI to a Sony TV.  No audio, though.  I use a standard adapter wire with a mini-phono connector on one end and red/white "RCA" plugs on the other to pipe the audio into my receiver.

If your computer doesn't offer fixed mode, you'll need to [upgrade the BIOS]("http://ubuntuforums.org/showthread.php?t=1842893&p=11244073#post11244073").  The ability to set fixed mode was added to the firmware sometime in 2011.

---

### Post by merockstar on 2014-01-09
sensei that sounds promising! I'm going to take a crack at this soon! thank you!

post or pm a bitcoin address if you wanna claim that five dollar offer from earlier, in case this works.

---

