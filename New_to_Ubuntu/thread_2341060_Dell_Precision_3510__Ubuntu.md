---
title: "Dell Precision 3510 / Ubuntu ?"
date: 2016-10-24
forum: New to Ubuntu
---

### Post by jackwhitaker3 on 2016-10-24
Hi there. I'm planning on ditching my macbook and converting from osX to  Ubuntu as I'm really not keen to stick with Apple any longer for a number of reasons. I'm new to Linux and I'm wondering if it will be possible to run Ubuntu on a Dell Precision 3510? If anybody has any ideas/advice etc they would be very gratefully recieved! The full specs are:


[LIST]
[*]Precision M3510
[*]Processor: Intel® Core™ i5-6300HQ Processor (6M Cache, up to 3.20 GHz)
[*]Windows 10 Pro (64bit)
[*]8 GB (2x4GB) 2133MHz DDR4 Memory Non ECC
[*]500 GB 2.5inch SATA Hard Drive (7200 RPM)
[*]No Optical Device
[*]Intel 8260 Dual band 2x2 802.11ac Wi-Fi + Bluetooth 4.1
[*]No WWAN Card Included
[*]Non Touch WWAN HD/FHD LCD Backcover
[*]Non-Touch with Camera and Microphone
[*]Primary 4-cell 62W/HR Battery
[*]15.6 Inch FHD (1920x1080) Non-Touch Anti-Glare LCD
[*]Internal English Keyboard
[/LIST]

---

### Post by Geoffrey_Arndt on 2016-10-24
Your system should work well with Ubuntu.   It's an all Intel machine so graphics and and wireless are compatible and should be auto-configured.   SO, the main question is . . . will this be an all Ubuntu PC or a dual-boot?

---

### Post by jackwhitaker3 on 2016-10-24
I don't have anything tying me to Windows at the moment so it'd probably be all Ubuntu. I figure if I need to in the future I can always reinstall Windows as a dualboot. Would that be possible?

---

### Post by oldfred on 2016-10-24
Often best to keep Windows. 
With my Dell SFF desktop, it wanted two backups, one Dell & one Windows. And then I added another full backup with Macrium.
But it was Haswell and newer Ubuntu had caught up with all the drivers.

Dell often has a sputnik set of added drivers to fix any issues. Back with 12.04 was first sputnik and by 14.04 all those fixes were in standard Ubuntu.
       Dell XPS 13 9343 Needs /EFI/Boot/Bootx64.efi to boot
[http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13](http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13)
[URL="https://bugs.launchpad.net/dell-sputnik/+bug/1499323"]https://bugs.launchpad.net/dell-sputnik/+bug/1499323
[/URL]
 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241) 

[URL="https://bugs.launchpad.net/dell-sputnik/+bug/1499323"]
[/URL]

---

### Post by Geoffrey_Arndt on 2016-10-24
Good info from OldFred if you want to try the dual-boot scenario.  If you're up for a bit of reading on UEFI Ubuntu installs (including a few youtube vids), then, that is one option.   Another is, your machine should be an easy install via letting the installer use the whole disk.   I believe you'd get a straight-forward install done in 30-45 minutes.   

But honestly, I'm no longer a fan of dual-boot as I was once-upon-a-time (days before Win10 & uefi).    Windows tends to want to control the machine and its partitions, and I've read too many folks on these forums (and others) write about Windows over writing boot loaders etc.

So, IF Windows is absolutely required (e.g., for job or other critical apps, etc.), then I would opt for a second PC (yes, extra $$) that runs only Win10 - - perhaps one of the less expensive AMD based laptops, etc.   In the end, it really depends on your needs, and your resources.    I have 3 PC's currently.   Two of those can run Windows (I choose not to) via a Virtual Machine (software such as Virtual Box, or VMWare Player).   That works very well unless one is a gamer or needs top end graphic support.   VM's are how the "big-boys" (Corporate IT Departments) do it, and for good reason.   So, just more "food for thought" . . . check out Youtube and search for "Windows on Ubuntu Host" or similar.

---

### Post by mörgæs on 2016-10-25
Have you considered installing Buntu on the Mac?

---

### Post by reegz on 2016-10-25
Hi,

I recently took ownership of a 3510 as well. The specs are similar; except that mine has more RAM and has the SSHD.

Initially, I installed 14.04 LTS due to it being [officially supported]("https://certification.ubuntu.com/certification/hardware/201508-18812/") on this model. The OS installed without issue and ran just fine. A minor peeve was that I constantly found myself having to grab the latest versions of applications from the ppa repos. I then opted to upgrade to 16.04 LTS.

16.04 has been running on my laptop for over a month now. There are no major issues to report. A minor irritation is that the screen flickers once in a while. It happens so infrequently that it's not enough to make me downgrade; or worry or anything of the sort.

Just a note that I needed to change some bios settings before Ubuntu could install. This is related to it not being able to detect the drive. I don't think you'll have such issues with a standard HD.

As per [this blog]("https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/"), there is planned support for 16.04 LTS running on the 3510's.

I'm very happy with Ubuntu on my Dell and do not regret it for a second.

---

### Post by jackwhitaker3 on 2016-10-26
Thanks for all the tips!

Yeah I think i will go full Ubuntu rather than dual boot. I use Ableton Live for music recording/production a lot at the moment, which doesnt support Linux, but I'm keen to try other options such as Audacity.

Thanks reegz, that's good to know. In the end I actually went for a 3510 with slightly different spec, including SSD instead of regular HD. Just waiting for Dell to deliver my shiny new laptop now...

oh and I would install ubuntu on  the mac but its ancient and the screens super dodgy -   it will just go to minimum brightness randomly or if it gets knocked and refuse to get brighter again for ages. So I'm often left using a really dark screen most of the time!

---

### Post by mörgæs on 2016-10-27
Last post here, because it's borderline off-topic: It could be interesting to see how the Mac performed using an external monitor. They are sold very cheap second-hand.

---

### Post by reegz on 2016-10-31
Nice one. Enjoy your new laptop :)

---

