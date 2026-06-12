---
title: "Windows gaming on Ubuntu"
date: 2014-09-23
forum: New to Ubuntu
---

### Post by Michael_McKenney on 2014-09-23
I was going to setup a retro gaming box for my older Windows 98 and XP games like Half-Life, Outpost, etc.  XP is no longer supported.  My new Tape workstation has the hardware for a killer gaming box.  How can I install my older 16 bit games into Ubuntu 14.04 x64?

---

### Post by kira-yamato-2008 on 2014-09-23
You'll want Wine with a front end like say: PlayOnLinux(Found in the Ubuntu Software Center). For some older games you'll want to run them in Windows 95/98 mode, and others in XP mode. You'll also want to make sure you're running the correct binary for your video card(s), so you can make effective use of your rendering capabilities.

[Here is the Wine HQ install guide for Ubuntu.]("https://www.winehq.org/download/ubuntu") 
and
[Here is the Wine HQ Application Database, so you can make sure you have your games run correctly.]("https://appdb.winehq.org/")

With Wine you might expect some slow down, with a good set up you might not even notice though, except for on newer more demanding games. But even then with a good enough setup you still might not notice. Just be aware that not all games and apps work correctly in Wine, but the compatibility is always improving.

---

### Post by Michael_McKenney on 2014-09-23
I used Wine 15+ years ago.  It was about 50% slower than Windows.  The CPUs are dual AMD Opterons.  So four 2.8 GHz Opteron cores.  The video adapter was a good gaming board before I replaced it with my 6970.   I was going to see if Half-life had a 64-bit version for Windows 7.  I just miss Outpost 2 and a few other older games.

---

### Post by kira-yamato-2008 on 2014-09-23
With older games like Half-Life, which works just fine on Steam on 64 Bit Windows by the way, you probably won't notice slowdowns on that set up. Valve is also working on Linux compatible versions of their games available on Steam. You probably won't really notice issues. I'm just not sure if they have Linux versions of the original Half-Life and it's addons, expansions and mods... 

That being said if you want to resort to Windows 7 for classic gaming, it has compatibility modes that work pretty well. If not there's generally a workaround, or additions, and mods that help  if you google the game and Windows 7.

Also; either way with older DOS games, DOSBox is available for both Windows (compatible with 64-bit 7 and I think 8), and Linux. DOSBox is a great DOS emulator, and works really, really well.

[I]Edit: I forgot to mention compatibility tools for older versions of DirectX and such if you're needing to run pre-Windows XP games that run incorrectly on current versions of windows. I had issues with games such as Fallout and Fallout 2, along with Heavy Gear, EarthSiege 2, and other Windows 95/98 games on Windows 7.

Edit 2: Ugh I really have to collect my thoughts. So long as you make sure to check the Wine HQ AppDB before you install the game it should run pretty well or even perfectly in Wine. Regarding most older games that is.
[/I]

---

### Post by Michael_McKenney on 2014-09-23
You are at least pointing me in the right direction.  I heard Valve was working on Linux versions since Windows 8 is not a great gaming environment.  My main workstation is Windows 7 x64.  64-bit killed getting my 16-bit games to install properly and run.  I switched most of my gaming to my Xbox 360 and WII.  WII has a killer pinball game and Mario Karts.  My 360 has Skyrim.   My second Ubuntu box has my three SCSI tape drives and SCSI controller.  I like the performance of the NIC and Opterons for 3 concurrent backups.  I can push the tape drives to almost their limits of backup performance.  I just miss Outpost 2.   I don't like emulating on my Windows 7 x64 workstation.  It causes issues.  It takes 3 weeks to reinstall Photoshop and all my CAD software and add-ons.   Photoshop is a 2 day install with all the camera bodies, lens, printers, monitor, etc.

---

### Post by EngieOP on 2014-09-23
> **kira-yamato-2008 said:**
> I'm just not sure if they have Linux versions of the original Half-Life and it's addons, expansions and mods... 


Half-Life is available on Linux. :)

---

### Post by kira-yamato-2008 on 2014-09-23
Like I said, Wine is a great environment, especially for older windows games, and if you need to emulate for DOS, DOSBox is great on Linux as well as Windows.

For Outpost 2: Divided Destiny: [Here is the Wine AppDB page for it.]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=6168") It has a gold rating, but there may be some tweaks listed in the comments to up it all the way to Platinum performance levels. Also PlayOnLinux(Wine compatibility front-end app), which you can find in the Ubuntu Software Center, might have some helpful settings to help with the install and game play.

Remeber that used Wine last 15+ years ago and a lot has changed since then, mostly for the better. There's lots more compatibility anymore, and when my friend got StarCraft 2 on a not so new business convertible Laptop/Tablet it ran very smoothly. So on your setup you really shouldn't have any major issues with a game as ancient Outpost 2.

---

### Post by kira-yamato-2008 on 2014-09-23
I hate to double post... But this deserves it's own post. You mention SCSI Tape Drives, does that mean you don't have any Hard Disk Drives, or Solid State Drives, or do you use the SCSI Tape Drives and tapes for redundant data storage? Regarding install times you mentioned I'm curious now...

---

### Post by Michael_McKenney on 2014-09-23
Windows 7 Workstation
Intel i7 2600K CPU
16GB RAM
LSI Logic 8708EM2 SAS RAID controller with 128 MB battery cache
pair of 15K SAS Seagate Cheetah drives in RAID 1
pair of 10K SAS Seagate drives in RAID 1
Firewire 800 controller
6970 graphics adapter
PC Power and Cooling custom wired 1000W power supply: Single rail, 100W @ 12V.  On its own 20A circuit with 20A cord and 2400W Tripp Lite Line Conditioner.   It can pull 870W doing 3D CAD.  

Benchmarks: 1.097 GB/s cached reads and 850 MB/s cached writes on 15K SAS RAID.  Windows 7 x64 installs in 7 minutes from the USB thumbdrive.  Photoshop can do 75 RAW to Jpg conversions a minute with 3 auto processes.  SAS RAID was my best investment ever.  I might convert my other workstations to it.   The i7 2600K can do 300,000 MIPs.  It is faster than my previous pair of Intel E5430 Xeons on a Supermicro board.   I looked at a i7 3900K CPU but can't justify the cost.  I really don't need it.  I can do everything at one time and not notice a lag with SAS RAID.  SSD drives degrade after two months of use.   SATA drives die after 1-2 months of use.  Only SAS drives can handle my IOs.  I stripped out the Cooler Master Stacker chassis of all its fans and installed Panflo 30 dB fans in it.  It is very quiet while running. The 6970 dual fans are the quietest that were even placed on a video adapter.  I added the 20A dual pole circuit for my workstation and toys.  I wanted clean power and larger grounds on it.  It has a 20A double pole wall switch to kill the power to it.   32 years of experience building highend workstations and servers.  

Tape workstation
Ubuntu 14.04 and XP Pro x64
Tyan Thunder K8WE server board
pair of AMD 280 Opterons
4GB RAM: I gave my friend my old Tyan Thunder K8W board with my 240 Opterons and strip this down from 16GB.
Adaptec 39320 dual channel 64/133 SCSI controller in a 64/133 slot
HP LTO 3 tape drive
Two Exabyte VXA-2 tape drives
The video card was the model before the 6970. I forget which one.
PC Power and Cooling 750 power supply

The three tape drives get 2800 MB/min backup performance concurrently.  I thought about getting an LTO 4 for it.  Not sure about spending $3200 on a tape drive.   This was my workstation 3 upgrades ago.  280 Opterons can do 230,000 MIPs and 60 GB/s memory bandwidth.  The board is pure 64 bit server hardware.  No 32-bit adapters on it.  

Web Site workstation
Intel DG33TL
Intel 775 dual core 1.8 Ghz
2 GB RAM
onboard video
500GB SATA drive

96W total usage.  It was designed for web site.  [www.michaelmckenney.com]("http://www.michaelmckenney.com").   I made it to run 24x7 at minimal power.  The DG33TL is 1/3 the size of the Tyan board.   I need to get Panflo fans for it to quiet down.  My workstation has 25,000 vacation pictures on it from all over the world.

---

### Post by whitesmith on 2014-09-23
First of all, a suggestion: when you have tons of data in your post the mass of detail really belongs between code tags. That way it will```
stand out like this
``` from the rest of your post, making everything easier to read and comprehend. Few will slog through that much information without some means of visual separation.

Second, I would suggest  considering virtual machines for playing games. A VM is not emulated Windows or application layer Windows (like Wine); rather, it is the real deal--Windows running as a guest under Linux as a host. It's normally faster than other approaches. And there are (to my knowledge) no situations in which apps fail to run in the same version of Windows that's in your VM. I would look into something like VirtualBox right away before encountering endless disappointments from apps that won't work under Wine.

---

### Post by kira-yamato-2008 on 2014-09-23
whitesmith I've used both VirtualBox and VMWare Player. Of the two VMWare player is a much smoother experience for some odd reason. But when it comes to older games. Plus on a Virtual Machine you need an actual copy of Windows. Since he's apparently been having compatibility issues with XP he'll still have those on a VM... Unless he does happen to have a copy of Windows 98 kicking around.

---

### Post by Michael_McKenney on 2014-09-24
I used VMware 5.5 U2 at work on our HP C7000 Blade Center and SAN.  I was trying to stay away from VMware.  It can have issues with workstation OS running on it.  I did consider Windows 98 but don't want to build another workstation or dual boot.

---

### Post by kira-yamato-2008 on 2014-09-24
> **Michael_McKenney said:**
> I used VMware 5.5 U2 at work on our HP C7000 Blade Center and SAN.  I was trying to stay away from VMware.  It can have issues with workstation OS running on it.  I did consider Windows 98 but don't want to build another workstation or dual boot.

VMWare Player and Virtual Box both work well enough, so long as you have the correct binary running in Linux, and the correct driver in the VM it self for the OS... That being said, you don't have to build a new workstation, or rig of any sort if you install Windows 98 on a Virtual Machine. Also keep Wine in mind as an option. If you have Ubuntu already running either/or (Wine/VMWare or Virtual Box) should fulfil your needs. With out the need to dual boot. Of course the best way to work these sort of things is from a home machine, not a business workstation. Since you can setup specifically sized virtual drives, memory allotments, and how many cores the VM actually uses... It makes VMs an ideal solution. VMWare Player, or Virtual Box both work effortlessly with my machine, they shouldn't cause you any issues, at least I wouldn't expect them to.

This is one of those situations where if you want to do something you can't throw the baby out with the bath water. Give one method a shot, if you're dissatisfied with the result it's easy enough to undo either way.

---

### Post by Michael_McKenney on 2014-09-24
Thanks for your help.  I will check into them.  I am working on Bacula and my tape backups first.  When I get time, I will consider my gaming rig on it.   VMware works great on our blade center and SAN.  It required the SAN to be configured with VMware VMFS first.

---

