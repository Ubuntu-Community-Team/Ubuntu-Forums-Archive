---
title: "I want to buy a new computer for Ubuntu (Beginner)"
date: 2020-03-10
forum: New to Ubuntu
---

### Post by polar-bear-8 on 2020-03-10
Hello everyone, I am a long-time Windows user who wants to get started with Ubuntu. I actually quite like Windows 10 but privacy concerns and an interest in Ubuntu lead me to want to learn this system. I would like some recommendations on which computer would be best to buy. I want to install the new Ubuntu release in April. Pretty much every computer I look at comes pre-installed with Windows 10 which is unfortunate. I had a bad experience trying to set up a dual-boot with Windows 10, so this time, I want to start with a new machine dedicated to Ubuntu but I don't like having to mess about with Windows to do it (shutting off boot protection and all that nonsense). I watched a video wherein the advice was given to avoid AMD processors for Linux. Is this true? Are there any specific recommendations for which processors are ideal for Ubuntu? I will be doing simple internet browsing, email, YouTube videos, watching movies, and maybe some photo editing. No games. Nothing very high-level, but still I want a snappy performance.

---

### Post by coley9225 on 2020-03-10
First of all, I'm a noob as well, welcome to the world away from windows. I have a lenovo ideapad 320, and played hell installing dual boot with lubuntu 18.04. I have seen people with issues with other models of lenovo as well, so I would recommend not using one. I have seen adds and references to manufacturers selling fully set up and running computers with linux based os installed. Pick your distro and they will install and get everything running, then it's like the out-of-the-box windows, just set your preferences and do a little fine tuning....and enjoy. Good luck on your search, I wish you luck. And, by the way, I installed lubuntu 18.04 and lubuntu 19.10 about 5 weeks ago, and I have'nt booted into windows in over a week now. It's a bit of learning but I feel it's worth it.

---

### Post by CelticWarrior on 2020-03-10
Welcome.

A lot to unpack for a first post...

Good news is that if you avoid the very cheap very entry-level Intel BayTrail and CherryTail class (if they're still around) and go just one tier higher, Intel or AMD, you find everything you need and some more for *simple internet browsing, email, YouTube videos, watching movies, and maybe some photo editing.* And some not very demanding games, why not?

Preinstalled Windows, not a problem. But if you want preinstalled Ubuntu you have options but not as many. Most laptops are very easy, trivial I dare say, to install a dual-boot, especially in the entry-level no mucking about with Nvidia or AMD dGPUs that is more than enough for the needs you expressed in the post. Any Intel Celeron or AMD APU based cheap laptop with a 256GB can run a Windows + Ubuntu dual-boot comfortably.

---

### Post by crip720 on 2020-03-10
Can get a computer with pre-installed Linux or a computer without a OS installed.  Intel does seem to play nicer with Linux.  I would go with hardware that is at least a year old, instead of brand new hardware that just came out.  I have had good luck with Acer(2) and a refurb Dell(needed bios adjustments for install).  Check the software that you use/need on Windows can be used/have alternatives on Linux.  Photoshop does not work well on Linux, but there are good alternatives like Gimp and others.  Should also check prices of refurb computers, can usually get more bang for your dollar.

---

### Post by DuckHook on 2020-03-10
Welcome to the forums, polar-bear-8,

My usual recommendation for people new to Ubuntu and who ask your question is: install Ubuntu into a VM and run it from within your Windows machine. Yes, I realize that you are willing to make the jump into Ubuntu with both feet, but I've seen so many people become disillusioned by the newness of the OS and then fall back to Windows over the years, that I've formulated the above recommendation instead.

From within a VM, you will be able to comfortably familiarize yourself with Ubuntu without pressure. More importantly, you will not have to give up functionality that you have grown used to—and perhaps even take for granted—while still educating yourself in something that can seem very different. Just as importantly, breaking your Ubuntu installation within a VM is a non-issue because you can undo your mistake by simply rolling back to a working snapshot. Last but not least, this allows you to purchase a Windows machine and not have to convert it to Linux until you are good and ready. It should be you who sets the pace, not have the pace set by external circumstances.

There are a number of free VMs that will run on Windows. Since Ubuntu is a free download, it shouldn't cost you a penny to implement the above.

---

### Post by TheFu on 2020-03-10
Any Intel or AMD CPU over $50 will be fine.  Whoever said to avoid AMD had a different agenda.  I would suggest staying away from newly released hardware, say anything first released in the last 6-12 months.  Since HW vendors don't often test with any Linux, it takes some time for volunteers to get new hardware working in the kernel.  An AMD Ryzen costing about $80-$140 would be crazy fast and not break most budgets.

But why get new hardware at all?  You can learn Ubuntu by running it inside a VM.  I think that is the best way to start, since running in a VM removes almost all hardware compatibility problems.  Virtual HW is almost always to most compatible there is with excellent drivers. Plus, you won't need to struggle to get wifi or bluetooth or GPU drivers to work just by choosing bad hardware or not knowing how to tweak motherboard settings to get the best/fastest RAM support possible. 

Running inside a VM to learn only costs the disk storage - so 15G - 25G is usually all someone new would need.  If you only want to run Ubuntu server, you can start with much less storage since there isn't any GUI or GUI-bloat.  A VM host doesn't need to be any great power. I've used carefully selected chromebooks, so chances are that your current machine can easily work as the VM host.

Wasting over $60 total just to watch movies/youtube isn't something I'd do.  I have a few raspberry pis and a $50 tablet for those distractions.

Snappy performance is easily achievable from a VM, using most of the non-Gnome3 based Ubuntu versions.  The GUI isn't the OS. Never forget that. There are 50+ different GUIs.  Each work fine, just a personal preference.

Spend a few months using a VM, see how it goes. See if you like it.   Just for reference, I've run 15 virtual machines concurrently on a Core2 Duo with a $40 nVidia GPU.  Worked great!  Upgraded that machine to a 1st generation Core i5, ran over 20 VMs concurrently on it for almost a decade.  Migrated most of those VMs to an AMD Ryzen 2600 about a year ago.

Don't expect your Windows knowledge to transfer more than about 20% to Linux.  That will be the hardest change. Usually, the way to accomplish something on Windows is not the most efficient method, so thinkingi a little different will take some time to get the hang of Linux.  That isn't to say that you can't just point-n-click most of the time, but that does you and your computer a disservice.  80% of the power in computing comes from NOT using a mouse and my having the computer do what you want before you need it.

---

### Post by QIII on 2020-03-10
> **polar-bear-8 said:**
> I watched a video wherein the advice was given to avoid AMD processors for Linux. Is this true? 

No. Not true.  Nonsense from a fanboy.  

AMD brought the first 64 bit processors and instruction set to the ***consumer ***market.  That's why you'll still often see references to AMD64.

I have both Intel and AMD CPUs as well as a variety of GPUs.  As said, stay away from the very latest cutting edge hardware, as it takes OEMs/the Linux community a while to get Linux drivers out.  The OEMs aren't stupid and they know that 97% of the market is something other than Linux.  They'll spend their time first where the money is.

---

### Post by mörgæs on 2020-03-11
The 'buy new hardware' approach is part of the Windows tradition but using Buntu you can begin with any kind of old gear you have around. 12 years age is no problem.
[https://ubuntuforums.org/showthread.php?t=1543006](https://ubuntuforums.org/showthread.php?t=1543006)

---

### Post by Impavidus on 2020-03-11
The "avoid AMD" may have been said in relation to GPUs, not CPUs, and there used to be some truth to this. But things have changed recently and AMD graphics seem to work quite well these days.

Having Windows preinstalled doesn't have to be a problem. You can always wipe it. True, you paid for the license so that money is wasted if you go that route, but if you won't use Windows, there's no reason to keep it, even if you spent money on it. You can buy a computer without an OS or with Linux preinstalled, but it may not be much cheaper.

If you only want your computer for "simple internet browsing, email, YouTube videos, watching movies, and maybe some photo editing," there's no need for a brand new computer. Any ten-year-old laptop will do (assuming you increase RAM to the max).

---

### Post by pantazi on 2020-03-11
Hello OP, 
I was in your situation two years ago with similar requirements. I began by buying a six year old HP Elitebook 8460p (no OS) with an early i5 plus 8gb Ram and 240gb ssd. I installed Ubuntu 16.04 LTS ( since updated to 18.04.04). As Ubuntu is lightweight this runs very fast and apart from the screen resolution it covers all my needs.
I read a lot beforehand, but as with most things, working with it is the best teacher.
Such was the success my wife bought an eight year old Lenovo 230i for £150 (no OS) with 8gb ram and 240gb SSD, and I fitted an IPS screen (£35- for better Flickr visuals) and taught her the basics. Success all round and we are both in our seventies!
Sure, go ahead a buy a posh computer but our way proved cheap to get started and learn.

---

### Post by poorguy on 2020-03-11
> **mörgæs said:**
> The 'buy new hardware' approach is part of the Windows tradition but using Buntu you can begin with any kind of old gear you have around. 12 years age is no problem.
[https://ubuntuforums.org/showthread.php?t=1543006](https://ubuntuforums.org/showthread.php?t=1543006)

Yep find a used computer you can find good deals everywhere for cheap cost if your willing to search a little bit.

Here's one of my **13 year old curb finds **upgraded from spare parts and then installed** Ubuntu 18.04 **and working well.

```


thomas@HP-Pavilion-PC:~$ inxi -Fxz
System:    Host: HP-Pavilion-PC Kernel: 4.15.0-88-generic x86_64 bits: 64 gcc: 7.4.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4) Distro: Ubuntu 18.04.4 LTS
Machine:   Device: desktop System: HP-Pavilion product: GN556AA-ABA a6200n serial: N/A
           Mobo: ECS model: Nettle2 v: 1.0 serial: N/A BIOS: Phoenix v: 5.12 date: 06/11/2007
CPU:       Dual core AMD Athlon 64 X2 5600+ (-MCP-) arch: K8 rev.F+ cache: 2048 KB
           flags: (lm nx sse sse2 sse3 svm) bmips: 9643
           clock speeds: max: 2800 MHz 1: 2400 MHz 2: 2400 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 8400 GS Rev. 3] bus-ID: 02:00.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1152x720@60.00hz
           OpenGL: renderer: GeForce 8400GS/PCIe/SSE2 version: 3.3.0 NVIDIA 340.107 Direct Render: Yes
Audio:     Card-1 NVIDIA MCP61 High Definition Audio driver: snd_hda_intel bus-ID: 00:05.0
           Card-2 NVIDIA High Definition Audio Controller driver: snd_hda_intel bus-ID: 02:00.1
           Sound: Advanced Linux Sound Architecture v: k4.15.0-88-generic
Network:   Card: NVIDIA MCP61 Ethernet driver: forcedeth port: ec00 bus-ID: 00:07.0
           IF: enp0s7 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 82.3GB (11.4% used)
           ID-1: /dev/sda model: Hitachi_HDS72168 size: 82.3GB
Partition: ID-1: / size: 75G used: 8.8G (13%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 40.0C mobo: N/A gpu: 0.0:50C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 200 Uptime: 10:03 Memory: 1365.1/5960.4MB Init: systemd runlevel: 5 Gcc sys: 7.5.0
           Client: Shell (bash 4.4.201) inxi: 2.3.56 
thomas@HP-Pavilion-PC:~$ 


```

---

### Post by TheFu on 2020-03-11
Using really old hardware has 1 liability.  

GPU drivers that support decoding modern videos using the hardware-drivers, not the CPU.  Around 2013 is when GPUs HW all started getting h.264 and mpeg2 video capabilities.  Cheap computers older than that struggle to playback nominal youtube hidef video today.  OTOH, since then, any intel CPU with built-in iGPU can easily handle playback for any mpeg2 or h.264 videos today.  Cheap chromebooks often have terrible CPUs, but the built-in iGPU can and does handle any youtube videos.

What is your current Windows hardware?  We can look at it to know how well it can handle virtual machines fairly quickly.

---

### Post by SeijiSensei on 2020-03-11
I'm agnostic in the AMD vs Intel wars, but this might make you pause: [https://www.engadget.com/2020/03/08/amd-cpu-take-a-way-data-leak-security-flaw/](https://www.engadget.com/2020/03/08/amd-cpu-take-a-way-data-leak-security-flaw/)

On the other hand, I don't often get too concerned about reports like these. I don't expect the computer I'm using now is going to start leaking data from its AMD processor.

I can't tell if you're looking for a laptop or a desktop. If you can go with a desktop and already have a monitor, how about
this one at $75: [https://www.newegg.com/p/1VK-001E-3WJ85?Item=9SIA596AYE5027](https://www.newegg.com/p/1VK-001E-3WJ85?Item=9SIA596AYE5027)

---

### Post by mastablasta on 2020-03-12
if you want to save money you can get business class dekstops or laptops form outlet. they are usually ubuntu certified and often come with no OS preloaded. for example HP Pavilions, Lenovo's think centers, Dells...

same goes for laptops.

---

### Post by Mark Phelps on 2020-03-14
I've done dual-booting with various Linux distros and Windows versions for well over ten years -- so let me provide some observations.

First, Linux is not a "free version of Windows".  OK, you probably know that -- but lots of folks don't.  And many of them come here asking how to run MS Office and other Windows apps they've grown dependent on using, and the simple answer is -- you don't!  So, that in mind, the main challenge in using Linux is going to be learning how to do the same old stuff with new apps.

Second, folks will say you can do EVERYTHING in Linux that you can in Windows.  This simply is not true!  But for most people, the few things that Windows does do not really matter.  So, if you're using e-mail, browsing the web, watching videos -- you can do ALL of that in Linux equally well, and you won't miss Windows.

Third, in Windows, folks can become OBSESSED with keeping up, almost daily, with driver updates and BIOS updates.  You won't be doing those in Linux, especially the latter -- as companies that provide BIOS updates do those using specialized apps that run only in Windows.  So, if you run into hardware issues in Linux, and folks say (as they all to often do) to do a BIOS update (as if it was some kind of miracle cure), then you can forget about that.

Fourth, the long-standing view is that, given ANY hardware, Linux distros perform much better than MS Windows.  Once again, this simply is not true.  I maintain a number of systems that are dual-booted and they display NO performance difference, whether they are running the Linux distros or Windows.  In addition, some of the new equipment, especially laptops, in order to keep the processor heat down run real-time utilities to reduce CPU usage -- and these utilities are generally NOT available for Linux.  

Fifth, the suggestion to use a VM is a good one because it prevents you from having to spend money on hardware that you might end up not using for the long run.  This will allow you to become accustomed to WHAT Linux does and HOW it does it -- but there is going to be some performance cost of using a VM. So, if it runs slower than the native Windows install, don't be surprised.  That is not a factor of running Linux; instead, it is a factor of using a VM.

Last, but not least, I do NOT share in the apparent common opinion that any laptop is going to work well in Linux, as I have seen the OPPOSITE to be the case.  I have three laptops I bought over the years and at one time, ALL of them were running Linux distros.  Now, NONE of them are, Why? Because  kernel upgrades over the years broke the working drivers and no new drivers were ever produced to fix that.  Laptop manufactures are INFAMOUS for using specialized hardware to keep down both the cost and the weight of their laptops.  One example, that is no so prevalent today, is switchable graphics -- which required using specialized video drivers which were mostly provided by the manufacturers.  If you had such a laptop and switched to Linux, you really suffered in the video performance area.  If you know of a specific laptop model you want, then search here for experience with that model as you will then see if there are major driver issues. The unfortunate fact is that everyone provides Windows drivers; very few provide Linux drivers.  So, if you buy the wrong laptop and discover no Linux drivers for some of the hardware, then you are stuck.

Sorry if this sounds overly negative, and I don't mean to discourage you, but thought it appropriate to mention some problems you're likely to encounter -- that you need to consider before spending money on a PC.

---

### Post by SeijiSensei on 2020-03-14
I have an HP laptop that's nine years old running Kubuntu 20.04. I added memory and swapped the hard drive for an SSD, but otherwise it's the same hardware.  I also have a Lenovo laptop that's eight years old and running Kubuntu 19.10.  I swapped the hard drive on this one as well, but that's it.  Neither computer has ever had a problem with any version of Ubuntu over their lifespans.

My experience with Dell servers has been pretty much the same. I do use CentOS on servers since companies like Dell pay more attention to enterprise users who prefer RedHat, but again, Linux on Dell servers has been rock-solid.

---

### Post by kurt18947 on 2020-03-14
I've one caution re AMD and it's related to theFUs caution above. If I were a beginner I'd think twice about Ryzen with integrated video at this point. I have a homebuilt Ryzen3 2200G - the G means it has integrated graphics. That has been problematic though newer Ubuntu releases, 19.10 and 20.04 seem better. Disabling the integrated graphics and installing a few years old discrete graphics card works much better. You can find pre Ryzen AMD processors for pretty low $. SWMBO had an AMD A6 machine and it worked very reliably for her including integrated graphics.  Her power supply died and took the motherboard and/or processor with it. I replaced her machine with a B450 chipset motherboard and AMD Ryzen 2600 processor no integrated graphics. It has been very reliable.

Short version re AMD Ryzen processors are getting excellent press these days but for Linux the graphics subsystem seems somewhat immature.  I don't know how reliable new discrete AMD video cards would be, I buy a few years old cards off Ebay, pay about $12. I don't game or use graphically demand apps so don't need the latest and greatest video.

---

### Post by mrdc76 on 2020-03-15
> **Mark Phelps said:**
> Third, in Windows, folks can become OBSESSED with keeping up, almost daily, with driver updates and BIOS updates.  You won't be doing those in Linux, especially the latter -- as companies that provide BIOS updates do those using specialized apps that run only in Windows.  So, if you run into hardware issues in Linux, and folks say (as they all to often do) to do a BIOS update (as if it was some kind of miracle cure), then you can forget about that

BIOS updates are available as bootable ISOs. Some brands support BIOS updates directly from Linux for certain devices. If you are buying a new computer to run Linux, check if it is supported: [https://fwupd.org/lvfs/docs/users]("https://fwupd.org/lvfs/docs/users")

---

### Post by pantazi on 2020-03-16
All good advice and would be good to know the OP's thoughts.

---

