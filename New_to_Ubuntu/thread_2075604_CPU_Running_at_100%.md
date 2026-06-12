---
title: "CPU Running at 100%"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by ctdave on 2012-10-24
Hi,

I'm new to linux.  I have an old Sony Vaio PCV RX550 desktop that had been running Windows XP (Pentium 4, 1.5 GHz, 512 MB RAM).  It was running slow and was no longer usable as my work computer.  However, my kids wanted a computer for surfing the internet (mostly for watching videos).  I replaced Windows XP with the latest Lubuntu operating system.  It works better, but it is still slow.  Videos on the internet are stilted--audio is fine, but the video image starts and stops and does not keep pace with the audio. I checked task manager and was surprised to see that, whenever I am on the internet, the CPU usage is frequently at 100%.  Even more surprising, the list of applications does not explain what's causing the high usage--all the applications added together do not total anywhere near 100%.  What could be going on?  Did I mess up the installation somehow?  Could this actually be a hardware problem? Any help would be greatly appreciated.  Thanks.

Dave

---

### Post by 2F4U on 2012-10-24
What is your graphics card? What version of Lubuntu are you using? 512 MB RAM is pretty low, given that most modern web browser use a huge amount of RAM, so the reason may be that the system is swapping to hdd. What browser do you use?

---

### Post by mittwit on 2012-10-24
The following may no be much help as I didn't read your post properly to see that you are using Lubuntu.
My original post:
[I]I'm not too surprised. Unfortunately I think you will struggle to get the standard Ubuntu working well on your P4. Here is a link to the PassMark for your cpu: [http://www.cpubenchmark.net/cpu_lookup.php?cpu=Intel+Pentium+4+1.50GHz&id=1053](http://www.cpubenchmark.net/cpu_lookup.php?cpu=Intel+Pentium+4+1.50GHz&id=1053)
I'm using a laptop with Intel® Core&#8482; Duo CPU T2350 @ 1.86GHz × 2
[http://www.cpubenchmark.net/cpu_lookup.php?cpu=Intel+Core+Duo+T2350+%40+1.86GHz&id=729](http://www.cpubenchmark.net/cpu_lookup.php?cpu=Intel+Core+Duo+T2350+%40+1.86GHz&id=729)

Now I'm not sure how accurate these scores are but 174 for the P4 compared to 852 for the T2350 is quite a difference.

If I have the chrome browser open and a youtube clip playing and then I open System Monitor my load average goes above 1 actually 1.5 at the moment. Chrome is using around 30% cpu and interestingly gnome-system-monitor is using around 30%.

If I use the top command in a terminal instead my load average is below 1.5 and the cpu usage of chrome varies totalling between 30% and 60%. I have a few tabs open, this one included.

My other laptop a Dell D420 has an Intel Core Duo U2500 @ 1.20GHz and it can be sluggish at times.
[/I]

So I have used Lubuntu and it is better on older systems but still not great. I would think the cpu demands of a browser running video would be much the same on all versions of Ubuntu.

---

### Post by ctdave on 2012-10-24
Thanks for your prompt replies.  The spec sheet on my computer describes the graphic card as follows: "4X AGP 3D Graphics Hardware Acceleration (nVIDIA TNT2 M64)."  I am running Lubuntu 12.10.  To me, RAM does not seem to be the problem.  While the CPU is reading 100%, only about half my RAM is being used.  (Perhaps I'm missing something in reading these numbers; I am a novice for sure.)  As for modern web browsers, I am using Chromium, which came with Lubuntu and, I thought, was supposed to be less demanding on the system.  Maybe my expectations were simply too great.  It does seem that this has been a recent phenomenon, even when it was operating Windows.  I do not recall having such issues a year or two ago.  Could it be a symptom of a failing CPU or motherboard?

---

### Post by mittwit on 2012-10-24
To check your memory usage open up a terminal window,
Menu -> Accessories -> LXTerminal
and enter,
***free***
This will display your memory usage. Look at the values in the "used" column. If the swap value (bottom row) is greater than zero then the computer is using part of the hard drive as ram which will slow things down.

Try this without the browser running and then with it running to see the difference.

---

### Post by ctdave on 2012-10-24
I checked my memory usage in LXTerminal, as you suggested.  The swap row shows 33,000 in the used column when the browser is not running and 32,876 (less) when it is.  I even tried it while playing a youtube video and it stayed at 32,876.

I also checked the task manager.  While playing the video, it showed the CPU usage was hovering around 98 to 99%.  The Chromium browser was using 75%, lxtask was using about 2%, and everything else was at 0%.  Meanwhile, the memory showed about 268 of 496 MB was in use, so only about half.

Any ideas or additional insight?

---

### Post by monkeybrain2012 on 2012-10-24
Try to use Firefox instead of Chromium. It appears to hog a lot of memory and use a lot of cpu in some Linux installations.

---

### Post by mardybear on 2012-10-24
> **ctdave said:**
> Any ideas or additional insight?
Hi ctdave...

I believe you have more than adequate hardware to run Lubuntu. Not sure if i understood the conversation correct...you only notice the very high processor usage when running a flash application?

If you have chromium open but no flash running, then processor usage drops low, <10% ?

If yes, then it's a chromium or flash issue.

If you're trying to troubleshoot chromium and flash, you could close chromium, install firefox and run the same flash video via firefox to see if there's difference in processor usage.

I know with firefox there's a program that runs during flash called plugin-container or something similar, which can be disabled and makes a big difference on flash performance.

mardybear

---

### Post by ctdave on 2012-10-25
I notice the high CPU usage whenever I am on the internet, regardless of whether Flash is running.  For instance, with the computer sitting idle, it is at 1 to 2%.  Oddly, the mere act of dragging the Task Manager window across the monitor causes CPU usage to jump to about 20%.  When I start Chromium up, CPU usage is at 100% even though the browser is only using 12 to 15% based on the list in Task Manager.  I let the computer sit idle on the Google.com webpage, and CPU usage remained at 100%.  The most demanding application was something called apport-gtk at only 9%.  Eventually, the CPU settled down to about 50%, but as soon as I did anything, like run a Google search, it jumped up to 100% again.

I'll try Firefox.  I'm new to Linux, so installing things is a little challenging for me.  I'll have to look into how to do it.  Again, thanks so much to everyone for taking the time to give me hand.

---

### Post by mastablasta on 2012-10-25
> **ctdave said:**
>  Oddly, the mere act of dragging the Task Manager window across the monitor causes CPU usage to jump to about 20%. .
 
that's because the graphics chip probably doesn't have or use it's own processor to handle graphics. as mentioned before oyu need to give full specs of your maschine.
 
easiest way to do it is to open terminal and insert (type or copy&paste) this command:
```
 
lshw

``` 
 
then copy all output in terminal and post it here. this command will list hardware (ls for list and hw for hardware :-) )

---

### Post by mardybear on 2012-10-25
Hi ctdave...

I'm not familiar with apport but here's what i found. You might want to check if there's a crash dump log file: apport automatically collects data from crashed processes and compiles a problem report in /var/crash/. This utilizes the crashdump helper hook provided by the Ubuntu kernel.

Is this a similar problem to yours:
[http://ubuntuforums.org/showthread.php?t=1838819](http://ubuntuforums.org/showthread.php?t=1838819)

It's probably okay if your cpu usage spikes during tasks, but 50% idle seems quite high. I always read about chromium using low resources but my experience was quite the opposite. My old hardware much prefers firefox (700MHz cpu, 512MB ram).

If you're not sure about firefox being installed, enter 'firefox' into the terminal and see if it opens, if not it will tell you otherwise.

I use Ubuntu 10.04 but hopefully your version still uses synaptic. It's very good for software install/management. You can run synaptic via terminal by typing sudo synaptic. If it's not installed, you should also be able to install it via terminal by typing sudo apt-get install synaptic.

If you don't have/want synaptic, you should also be able to install firefox by entering the following into terminal: sudo apt-get install firefox.

Hope this gets you started...i'm curious to see if your cpu usage changes.

mardybear

---

### Post by mittwit on 2012-10-25
> **ctdave said:**
> I checked my memory usage in LXTerminal, as you suggested.  The swap row shows 33,000 in the used column when the browser is not running and 32,876 (less) when it is.  I even tried it while playing a youtube video and it stayed at 32,876.

I also checked the task manager.  While playing the video, it showed the CPU usage was hovering around 98 to 99%.  The Chromium browser was using 75%, lxtask was using about 2%, and everything else was at 0%.  Meanwhile, the memory showed about 268 of 496 MB was in use, so only about half.

Any ideas or additional insight?

I have to admit I'm no expert regarding memory use so I'm happy to be corrected but it seems that swap memory does start getting used before the system runs out of ram. Also from experimenting on my machine the swap value doesn't immediately drop back to zero when less processes are running.
If your machine has a hard drive activity led look to see if it is busy flickering when the cpu load is high. This could indicate the memory swapping.
Also I remember I had Lubuntu on a server with 2 core 2 processors and 4G ram. The desktop was sluggish on that machine which I put down to it having just basic graphics support so I think the comments about your graphics card may be on the right track.

If all else fails try puppy linux, [http://puppylinux.org/](http://puppylinux.org/)

---

### Post by ctdave on 2012-10-25
Here are the full specs of my machine as requested/recommended.  It's really long (which I assume is no surprise to any of you):

david@Sony:~$ lshw
WARNING: you should run this program as super-user.
PCI (sysfs)  
sony                      
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 496MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 1500MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.0.10
          size: 1500MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-fbffffff
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:f4000000-f5efffff memory:f5f00000-f7ffffff
           *-display
                description: VGA compatible controller
                product: NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 15
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
                resources: irq:16 memory:f4000000-f4ffffff memory:f6000000-f7ffffff memory:f5ff0000-f5ffffff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:b000(size=12288) memory:f1800000-f3ffffff
           *-usb:0
                description: USB controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: a
                bus info: pci@0000:02:0a.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: uhci bus_master cap_list
                configuration: driver=uhci_hcd latency=32
                resources: irq:9 ioport:d800(size=32)
           *-usb:1
                description: USB controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: a.1
                bus info: pci@0000:02:0a.1
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: uhci bus_master cap_list
                configuration: driver=uhci_hcd latency=32
                resources: irq:23 ioport:d400(size=32)
           *-usb:2
                description: USB controller
                product: USB 2.0
                vendor: VIA Technologies, Inc.
                physical id: a.2
                bus info: pci@0000:02:0a.2
                version: 63
                width: 32 bits
                clock: 33MHz
                capabilities: ehci bus_master cap_list
                configuration: driver=ehci_hcd latency=32
                resources: irq:20 memory:f3800000-f38000ff
           *-communication UNCLAIMED
                description: Communication controller
                product: LT WinModem
                vendor: LSI Corporation
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32 maxlatency=14 mingnt=252
                resources: memory:f3000000-f30000ff ioport:d000(size=8) ioport:b800(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: d
                bus info: pci@0000:02:0d.0
                logical name: eth0
                version: 10
                serial: 00:e0:18:3d:9d:65
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:21 ioport:b400(size=256) memory:f2800000-f28000ff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB12LV26 IEEE-1394 Controller (Link)
                vendor: Texas Instruments
                physical id: e
                bus info: pci@0000:02:0e.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=3
                resources: irq:18 memory:f2000000-f20007ff memory:f1800000-f1803fff
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:a800(size=16)
        *-usb:0
             description: USB controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:a400(size=32)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 12
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:e800(size=16)
        *-usb:1
             description: USB controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:a000(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:e000(size=256) ioport:e100(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: 00:14:d1:ab:d6:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.1.105 multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
david@Sony:~$

---

### Post by ctdave on 2012-10-25
Hi,

I also installed Firefox.  I discovered it in the Lubuntu Software Center, which is a nice feature for those of us new to Linux.  The computer is running a little faster now.  I also disabled plugin-container in Firefox as suggested.  That helped as well, but only slighty.  Depending upon what I am doing on the internet, CPU usage can drop to as low as 12%, but still jumps to 100% quite often.  It seems that Firefox frequently consumes most of the CPU usage, often up to 80 or more percent, which Task Manager did not show Chromium doing, but overall CPU usage is down slightly but significantly.  The viewing of videos is still a problem--it's stilted and the video image frequently falls behind the audio.

I also checked the front of my computer for the light showing HD activity.  It does seem to go on and off quite frequently.  

Since nobody mentioned a potential hardware failure/problem lurking in my system, I am assuming that that is not the issue.  Does anyone think there are any configuration tweaks or changes that can be made to improve the computer's internet performance further or are/were my expectations about Lubuntu simply unreasonably high?

---

### Post by mardybear on 2012-10-25
Hi ctdave...

Glad to hear you've made some performance progress.

Disclaimer: i don't use Lubuntu but much of this should apply.

Ubuntu tweaks to consider (note this isn't 'your' version of Ubuntu):

[http://kmandla.wordpress.com/projects/set-up-ubuntu-for-speed/](http://kmandla.wordpress.com/projects/set-up-ubuntu-for-speed/)

Best advice is to disable all unnecessary graphic eyecandy and background services and run lightweight programs. Linux is infinitely tweakable. To maximize ram usage and minimize hard drive thrashing, reconfigure your swappiness and cache_pressure via /etc/sysctl.conf (need to run as root, back up files before tinkering). Here are my swappiness settings:
vm.swappiness=10
vm.vfs_cache_pressure=50

Hope this helps,

mardybear

---

### Post by monkeybrain2012 on 2012-10-25
Seems that the machine is really old and you shouldn't expect high video performance. If you watch videos on the internet chances are you are using flash and that is another horrible resource hog. I suggest you use minitube or smplayer for youtube instead of watching videos from the browser, that may help a bit. I have an old Dell ispiron with similar specs. Put Lubuntu 11.10 there (the video card is too old, doesn't work with 12.04) and can watch videos up to 480p and that's it. Use ViewTube so it doesn't require flash to watch videos on Youtube and a few supported sites ([http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011))  

Also if you watch videos locally it eases things up a lot.

Can't ask for too much from specs like that. :)  

The default vm.swappiness is 60 and it is about right. If you lower it to 10 then you may have some performance gain but your system may freeze (too much ram usage before dropping into swap) and if you increase it too much (say to 100) then it may ease the ram usage but it may slow things down too much.

Also don't open multiple tabs on your browser (especially Chromium! In Firefox there is an option to load tab on demand under Edit > Preference > General and it is enabled automatically and no longer optional for FF16, Chrome/Chromium doesn't have this feature so all the tabs are loaded and it can kill your machine if you have 10 tabs open)

---

### Post by monkeybrain2012 on 2012-10-25
Checkout this thread here  [http://ubuntuforums.org/showthread.php?p=12311853#post12311853](http://ubuntuforums.org/showthread.php?p=12311853#post12311853)

Some guys talking about their experience with Lubuntu on "old machines" (that depends on how you define "old"), you may get a better idea of what to expect.

---

### Post by ctdave on 2012-10-25
Thanks everyone. It will take me about a day to absorb all the information you gave me.  I'll give it all a try and post back later.

---

