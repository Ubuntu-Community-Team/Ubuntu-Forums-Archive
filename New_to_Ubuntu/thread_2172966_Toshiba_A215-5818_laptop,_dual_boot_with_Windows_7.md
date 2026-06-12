---
title: "Toshiba A215-5818 laptop, dual boot with Windows 7"
date: 2013-09-07
forum: New to Ubuntu
---

### Post by aaron9 on 2013-09-07
I want to try Ubuntu or Linux on my Old Toshiba A215-5818 but I'm not sure if Ubuntu has drivers for the hardware. Also I was going to do a dual boot so I can debug and learn about the Linux family. I am no expert but I have loaded OS on a few comps and want to learn more and i'm not afraid of getting feet wet, but still green compaired to you guys. I have researched some and want to try loading Ubuntu from USB stick but i don't understand how to get it on the stick , is it the same as ISO cd ? I amgoing to expand the hard drive to make a partition for Ubuntu and it running Windows 7 now ( which i hate Windows and wish to never use Windows again ). Also, will my laptop run better with Ubuntu or another Linux ? Thank You and HELLO EVERYONE...

---

### Post by Bucky Ball on 2013-09-07
Lot of questions there that could perhaps be broken up and asked in threads in the appropriate sub-forums. I will have a go on some though.

As for drivers, yes, probably already in the kernel. It it 'Windows think' to expect to have to install drivers for all your hardware. Generally, hardware 'just works' unless it was released five minutes ago (very new hardware). Best to install and find out how things run.

You can get some clues by booting from the install disk/USB and 'Try Ubuntu'. This won't make any changes to your system but you can get to a desktop top and have a trial run, see what is working and what isn't. 

The most common faults are graphics cards and wireless. Most of these can be fixed with a full install (they may need third-party drivers which can't be included by default on the Ubuntu install medium). 

So, my advice is to burn a disk or make a USB, boot from it and give it a whirl. See what flies! Running from the install media is not as quick as running from an install on the hard drive. As to whether it is faster than Windows: no idea. Depends on a lot, not least of all which 'flavour' of Ubuntu/Linux you decide to run. Xubuntu and Lubuntu would almost certainly run faster, Ubuntu and Kubuntu, unsure. You'll need to try.

Good luck and welcome to the forums. Enjoy the learning curve, cos there will be one, but sounds like you are ready, willing and able for that. Good start. 

PS: 12.04 LTS is a good, stable place to start for a newcomer. LTS (long-term support) releases are now supported for five years, 12.04 until April 2017.

PPS: How much RAM and which processor in your machine, if you know, please (and any other hardware specs you know). This will determine which flavour it is possible to install (successfully). Detailed specs of the machine can be found once you've booted into a desktop from the install media. 

PPPS: Yes, the USB install is exactly the same as the disk, if you mean what you are installing. Just a different method of installing the same thing. You don't have a disk drive? Might be easier for starters so you can get into learning about the OS sooner. You may have to jump through some hoops just learning how to get the USB together, but there are plenty of resources out there to show you how to do it. 

[https://duckduckgo.com/?q=create+usb+installer+ubuntu+12.04](https://duckduckgo.com/?q=create+usb+installer+ubuntu+12.04)

... and for the ISO:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

PPPPS: DO NOT create any partitions for Ubuntu with Windows. You can't anyway as Linux uses EXT* partitions which Win can't create, deal with or recognise (but Ubuntu can recognise, read/write to NTFS, FAT and other filesystem partitions). Just shrink the Win partition and leave free space to install Ubuntu to. You can create partitions during the install on the free space.

The install and partitioning is another support thread in itself when you get a bootable install disk/USB so we'll deal with going there when you get to that point. ;)

---

### Post by oldfred on 2013-09-07
Welcome to the forums.

My Toshiba is Satellite A105 with dual Intel, Intel video and 1.5GB of RAM. I bought it a couple of weeks before Vista came out. I run the 64 bit version of Ubuntu although 1.5GB is a bit light on RAM for 64 bit and it works fine. Only if I try to load a couple of large apps at once will it turn grey for a couple seconds, so I know it is use swap and slows greatly. But my normal use of Firefox, Zim & terminal to browse forums works without issue. I do not use Unity as it needs good video but find Full Ubuntu 12.04  with fallback or gnome-panel works. 

Or you should be able to install Ubuntu. It looks like yours is or was Vista, so newer than my system?

---

### Post by aaron9 on 2013-09-07
Thank You ' Bucky Ball '  ...I have started backing up everything and now have Ubuntu on USB stick. I'm taking your advice  on Xubuntu and Lubuntu and do more research. Going to launch it tomorrow morning 9/8/13. Alot of steps to do, but I feel better knowing I have a shoulder to lean on... THANKS AGAIN !! I will update you tomorrow...:D

---

### Post by aaron9 on 2013-09-07
' oldfred ' ....Thank You for replying... My laptop is a Toshiba A215-s5818 , 2009 model , with AMD Turion 64x2 MT TL-60  2.0 GHz, 3 g memory , 64 bit OS Windows 7. ATI Radeon XL1200 video card, Anthreos AR5007EG Network Adapter, Realteck RTL810E PCI-E Fast Ethernet NIC (NDIS 6.20 ).  Going to run some MasterCam and CAD pgms and internet ect..need more recources , It ran ok with Vista but slow and disfunctional with Winows 7. Hoping Linux is going to help.

---

### Post by oldrocker99 on 2013-09-07
It's likely to run much better than Win7, especially if you install a lightweight desktop like xubuntu-desktop or lubuntu-desktop. MATE (a much-liked desktop, and the one I use) is avalable thus:
[http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html](http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html)

and there are a number of other desktop environments available in GNU/Linux. You can search in the Software Center or Synaptic until you find one you like.

And welcome to the community!

---

### Post by aaron9 on 2013-09-08
Thanks ' oldrocker99 '...I saved your link and after I get Ubuntu loaded and learn more about the Linux Family I will try your suggestion. Right now I'm having trouble cleaning the temp internet files...very slow...I may have a bad hdd...

---

### Post by aaron9 on 2013-09-09
THANK YOU EVERYONE !!! . :P .   I just loaded Ubuntu on a USB drive ISO, and had my first taste . Runs perfect !!! Now going to do a dual boot install and confirm divers are at 100 %. Then I will commit to a full install and leave Windows in the dust forever !

---

### Post by Bucky Ball on 2013-09-09
Great news! Good luck and look forward to a progress report. ;)

PS: Yea, I know: sweet OS, ay? That's why we're here and all in this together!

PPS: If it runs well from 'Try Ubuntu' that is a good sign and good start. Now just a matter of clicking that little install icon on the desktop. 

You might want to have a good think, and perhaps a little research, regarding how you're going to go about the dual-boot. You can let Ubuntu handle the whole install, but this may set up partitions not to your liking, or you can choose 'Something Else' when you get to the partitioning section and do it manually. Just avoid the Win NTFS install partition (clearly marked and labeled in there). And, of course, backup anything you don't want to lose before beginning just in case something goes pear-shaped.

---

### Post by aaron9 on 2013-09-09
Hi ' Bucky Ball ' and Thank You again for the help. I found this on setting up USB stick     [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)   that setup a Pendrive   [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)  , Very easy and Educational....Just insert Pendrive with a correctly bootable USB drive and F12 , set to boot to USB , enter....

Next Question is  .... Can Ubuntu partition my hard drive (  smaller to 60G  ) and move the MFT (Master File Table) without derstroying Windows , so I can do a dual boot ?

 I thinking about trying this    [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)     but I'm not sure i can be successful.. No Pain No Gain...LOL  Sadly I cannot install AutoCad or Mastercam on Linux because they don't want to get out of bed with MS. Still researching this issue. I really do not want to use MS anymore and we Will find a way.....Virtualbox will use too much RAM between Os's, I only have 3G, not going to work...

---

### Post by oldfred on 2013-09-09
Only with XP should you use gparted to shrink a Windows system partition. With Windows 7 use Windows disk tools to shrink the partition, but not create any new partitions for Linux as it cannot. Then boot Windows so it can run chkdsk and other fixes for its new size. Do not shrink too much as Windows really want 30% free space in the NTFS partition to run well. At 10% free Windows slows to a crawl. 
Then you can install to the unallocated either auto install for just / (root) and swap or manual install to create your own partitions. I usually suggest a separate shared NTFS data partition if dual booting, but you usually have to create that before or after your install with gparted.

 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)


       Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)

---

### Post by Bucky Ball on 2013-09-10
Prior to the install, get into Windows and create some free space, NOT a partition to install Ubuntu to. 

When you are installing Ubuntu, choose 'Something Else' when you get to the partitioning section (don't let Ubuntu automagically partition for you). In there, you will see the existing partitions on the drive. Your Win install will be CLEARLY visible as an NTFS partition. Just don't go there. Leave it alone. 

Best is to create an extended partition in the freespace then logical partitions inside that. This will overcome any problems with the four primary partition limitation. You will need a partition for the install (/ = 20Gb fine) and a /swap partition (2Gb fine). Separate /home partition is up to your discretion. These mountpoint are defaults in there which you can choose, but essentially, if you wanted to create a 40Gb partition called /nosehair, or anything else you like, then that is just fine. It doesn't need to be one of the default mount point names. 

As for the MFT, do you mean MBR (master boot record) or partition table? You shouldn't need to worry about any of this (unless you have a specific reason to and if that's the case, what is?). Ubuntu uses Grub by default which will identify your Win install and add it to the grub menu list which appears when you boot the machine. It will rewrite MBR accordingly and all should be good. (If it's not on your first boot, then generally easily fixable with something like Boot Repair which will identify all OSs and rewrite MBR accordingly). 

So, I would just hit the install, choose 'Something Else' at the partitioning section, setup your extended and logical partitions inside it, finish the install, reboot, and you should then get a list with a selection of your installs. That easy (he said!).

* NOTE: Ninja-ed by oldfred. A good thing as he's the resident guru on this, anyhow. ;)

But to corroborate the first part of his post, manipulate Win partitions with Win software, Ubuntu partitions with Ubuntu software. Good luck.

---

### Post by aaron9 on 2013-09-15
Hi All....I have successfully installed a Dual boot from everyones advice on my old Toshiba A215 Laptop. Thanks Again...Now I can run Cad pgms on Win 7 when needed and spend time on Ubuntu for everything else. I dislike MS because they are so greedy and selfish. Just need to tweek Ubuntu now so looking fwd to the forum. I do have a problem with the pc freezing up and having to reboot to get it working again in Ubuntu, any suggestions ?

---

### Post by Bucky Ball on 2013-09-15
The freezing issue is for a new thread, probably in ***General Help***. Please mark this one as solved from **Thread Tools **at top right. 

Good luck. ;)

---

