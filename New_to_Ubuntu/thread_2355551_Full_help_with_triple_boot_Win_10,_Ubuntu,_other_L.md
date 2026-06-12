---
title: "Full help with triple boot: Win 10, Ubuntu, other Linux - separate data partition"
date: 2017-03-13
forum: New to Ubuntu
---

### Post by Mike Krall on 2017-03-13
I'm on my way to a dual boot... set up specifically to move to triple or quadruple boot (multiple Linux distros)... Windows 10/Ubuntu 16.04, then ???  It's a very slow process for me... I understand lttle about computers...  many quite simple things written about in this sub-forum and other computer-help sites go by me at the function level.  

I've got a new ASUS notebook. 8 GB Ram, 256 GB SSD (GPT/UEFI).  My computer world is extrememly simple.  I use the Internet... I save links. I've got pictures. I've got documents... no music, no videos, no games.  By example, my 2010 ASUS Laptop (4 GB Ram, 320 GB HDD (BIOS/MBR) started with Win. 7 / Ubuntu 10.04, upgraded to 12.04 (well), upgraded to 14.04 (not perfect), and now a fresh install of 16.04.02_amd64 with Win. 7 gone.  That computer's total space-used is just under 15 GB ( / + /home + 5 GB swap) after 7 years of "collecting".   

I've shrunk Win 10 C:  through it's 'disk management' tool (along with 3 other, simple, internal manipulations) from 237.5 GiB to 49.32GiB (just under 40% free).  
I've got a USB .iso of 16.04.2 LTS made with Rufus (GPT/UEFI setting)... the download (Ubuntu.org) and md5sum check.  Booted it and ran 'check disk'... it's OK.  Booted into 'Try'.  Checked wireless and wired connections, sound, videos, music, etc.  Stayed on it for the evening.  It appears fine. 

Some givens:

*  I'm not going to use Windows unless pushed to it (by a printer or scanner or ???)... I've got no reason to go there.  I'll keep it because I always seem to get pushed to it, sooner or later, and I surely don't need the space. 

*  There is no need to share data.  

There are some things I'm aware of in dual/triple booting... and things in GPT/UEFI machine installs (OldFred, Rod Smith, How-to Geek, Every day Linux User, etc.).  Awareness is not function.  I've read about dual Linux distros...  / + /home (part of home) for each with /mnt/data partition (after install) and symlinks for separation where needed, but a common data section.  I'm confused.  

So... start...

The disk has 4 existing partitions... /dev/sda 1-4.  sda3 is C: and the shrinking put 188+ GiB 'unallocated' between it and sda4 (Basic Data - NTFS - Recovery - 499 MiB  - 'hidden, diag').  Does sda4 need to be moved up next to sda3?  If yes, how?  I have a bootable Recovery Drive and a bootable System Repair Disk.  Should sda4 be deleted with GPartEd through a "Try" session?  Should it just be left alone and go on?

"Fast Start ", "Quick/Fast Boot", "Secure Boot",  "Intel SRT"...  "Fast Start" and "Fast Boot" are already off.  My firmware has no "Intel SRT".  When asked, ASUS pointed me to 'Intel Anti-Theft Technology'.  A look today didn't find that and it didn't find "Secure Boot" either.  I asked ASUS if I needed to have firmware paswords set to access some functions.  Haven't heard back.  I'm unclear what condition these settings need to be in as of this date with 16.04.2 LTS.  Would you say? 

In firmware...  there is a grayed-out "CSM Support / disabled" and I can't find a switch or combination of switches bringing it out of non-function.  "USB Legacy Support" has 3 toggles... disable (only EFI applications), enable,  and auto (disabled unless USB connected).  I don't know if the condition has any effect on anything, but if  it does, what condition do I need it in? 

This is already too long.  I'll leave it here for now instead of going into partition stuff.  

One last question...  does anyone have links to information on multiple Linux distros with separate /home's and symlink /mnt/data?  I have no idea how a person would need to work with a set up like that and I'd read up about it if I could...  searching is not finding.

Mike

[COLOR="#FF0000"]Edit:  May 28, 2017...[/COLOR] There is a lot of information in this thread and in links in this thread about multiple Linux distro setup... creating and  using separate data partition  ( /mnt/data )

---

### Post by Geoffrey_Arndt on 2017-03-14
Just a quick suggestion about a dual-boot install given the info you're provided so far.   I would opt for the simplest setup possible . . . no separate data partition(s) and even no separate /home.    Not required especially with your low data collection habits.   System will be very stable with just the standard / root and home within root tree.   I would also avoid moving partitions at this time.   Use the custom install option (something else) and use the unallocated for Ubuntu.   The partition labels may change anyway after the install (ubuntu likely to be sda5).   Remember to setup swap also.

---

### Post by oldfred on 2017-03-14
What model Asus?
Does this have the newer NVMe SSD?

       ASUS VivoMini UN45 UEFI update required to see NVMe drive
[https://ubuntuforums.org/showthread.php?t=2355295](https://ubuntuforums.org/showthread.php?t=2355295)
Asus/Samsung problem with every NVME SSD and G752! 
[https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551](https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551)
[http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04](http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04)
Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/)
Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)
Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273) 

i915.preliminary_hw_support=1 should not be required if newer version of Ubuntu, many Asus have needed pci=nomsi or other boot parameters.

Shared /mnt/data, I shared data with multiple Ubuntu versions and flavors
 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

### Post by Mike Krall on 2017-03-14
Thank you, Geoffrey...  Thank you, 'oldfred'...  I've got reading to do and it will take a while.

The ASUS Notebook Mdl. # is F556UA-AB54

The SSD is shown in Win 10 Device Manger as Micron_1100_MTFDDAK256TBN.  A net search doesn't answer the NVMe SSD question.  I've asked ASUS.

Mike

Edit:  I think not a NVMe type SSD... I think firmware lists Serial ATA in a couple of places.  I'll go check to be sure ...

Edit again: Start+F2 = Firmware... > Advanced > Sata Mode Selection (= ACHI)...  Lists Serial Port 0 & 1, with 0 as Micron_1100_MTFDDAK256TBN.  And for the record... both old ASUS and this new one have a boot choice selection via Start + esc... which I've needed to use to get a live USB to boot... scroll to select > Enter.

---

### Post by oldfred on 2017-03-14
It still is the newest Kabylake CPU.
So you need the newest Ubuntu version installed in UEFI boot mode.
You may still need boot options like nomodeset and/or pci=nomsi. You often just have to experiment to see if it boots, if not try one or the other boot option and then both, or perhaps others.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

My Skylake system with 16.04 did not need to install,  but works with the newest Intel video driver. When I installed it, it also now gives me a warning on another driver may be required, but that is really the Kabylake one. Not sure if newest 16.04.2 includes that driver automatically or not.
 
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See also link in my signature.

---

### Post by Mike Krall on 2017-03-14
Thanks for the links and comments, 'oldfred'.

I haven't gotten to the reading but will tonight.

If I get things sorted out, I'll start structuring a partition diagram.  Should I be partitioning specifically for triple/quadruple boot, or rearrange after successful dual boot? 

I'm thinking to sandwich 'swap' between first '/' and first '/home' as opposed to front or back... comments?   

When I subtract my old ASUS's personal folders (pics, music, documents, videos) GB's from '/home' total GB's I get about 3.5 GB's.  How large a '/home' for a particular distribution would be recommended if there is a data partition?

Mike

---

### Post by oldfred on 2017-03-15
I prefer just to put swap at end of drive so it is out of the way.

With a separate large data partition, /home is so small that I just keep it inside my / (root) partition.
I also have moved some hidden folders in /home like Thunderbird & Firefox. I do not link those but edit profile.ini to find them.

---

### Post by norafaithrainbow on 2017-03-15
Well if you want to quad boot, you would have to do away with your swap partition, which I do not recommend if you have less than 16gbs of ram. Because of this, I am going to address the tri-boot.

1. Install windows 10 FIRST if you do not already have it installed (This is mandatory, due to the fact that windows will not let you access the grub menu if you install it last)
2. Then install ubuntu, or any linux distro you want, I suggest installing any ubuntu based distro last because they tend to be easier to install, though this will not always be the case.
3. After that, you will not be given the option to keep your current OSes unless you click the "something else" button.
4. Make sure you know which partitions ubuntu and windows are on, it will not always let you see the partition labels.
5. Click the partition you want to use, format it, and continue the install.

---

### Post by sp40140 on 2017-03-15
May I suggest something bit different?
have dual boot with one windows and one linux (whichever distro you prefer).
And run vmware (VMWare Player is free, but you can create virtual machines in it) or virtualbox (I prefer vmware though) under primary linux and mess with any distro / os you like. 
This set-up gives you flexibility in many ways. You can use virtual machines as disposables, few days with one then discard and get new one. Also, backing up vmx files are very easy, so if you mess up something and want to go back, you can go back to your last back up (provided you do back up).
And boot into windows when you are pushed (as you mentioned). 
This way you don't need to worry too much about different partitions and grub settings and such.

I do have this set-up (for about 4 years now). Very happy with it.

Cheers,

---

### Post by Mike Krall on 2017-03-16
I'm still here.  I got lost in the links... which have links... which have other links.  I'm trying to catch up to 'oldfred's' links on /mnt/data, etc. right now because I ran right by them a number of posts ago.   I appreciate the other input.  It may be I'd be best off with VMWare Player system.  Right now I can't even think about it without getting lost wussah in what I'm trying to get some sort of grasp on.

Mike

---

### Post by oldfred on 2017-03-16
Linux is about choices, but in beginning until you know or develop your own preferences it can be a bit much.
But it is easy to experiment. And the more you try different things the better idea you have of what you really like.

---

### Post by norafaithrainbow on 2017-03-16
> **Mike Krall said:**
> I'm still here. I got lost in the links... which have links... which have other links. I'm trying to catch up to 'oldfred's' links on /mnt/data, etc. right now because I ran right by them a number of posts ago. I appreciate the other input. It may be I'd be best off with VMWare Player system. Right now I can't even think about it without getting lost wussah in what I'm trying to get some sort of grasp on.

Mike
I don't know about VMware but I do know that loading your own os onto VirtualBox can be relatively complex if you don't know how to do it. I know how to do it and can show you how if you wish.

---

### Post by Mike Krall on 2017-03-17
I've about run my limit on separate data partition link-reading.  I understand, in theory (which everyone knows means 'not really').  I need to get a dual boot done and working, I think.  

Would you partition swap through GParted choice "add at end of space"?  

I will follow advice... /home in /.  My old machine has a 10 GB / and I'm using 53%.  If I use 20 GB for / (with /home) it would be 5 GB above recommended minimum / of 15 GB... or use 15 GB minimum Or? 

I don't know how to deal with the rest of the space regarding other distros and /mnt/data... found nothing specific.  I read somewhere (probably an "oldfred" thing) to do /mnt/data partition later.  Should I set up for 3 or 4 / (with /home)? Leave space to right unallocated with swap at end?  Or? 

Oh, nearly forgot... found this...  [https://community.linuxmint.com/tutorial/view/1609]("https://community.linuxmint.com/tutorial/view/1609").  It helped me get a better picture, though I need to cross check the code with the code from other links of 'oldfred's' and others (I think). 

Mike

---

### Post by sp40140 on 2017-03-17
There is lots of documentation which goes into LOTS of details, which could be overwhelming for beginners. (I have been there).
So, my ELI5 / TLDR version for dual boot:
From Blank HD: install windows, during install steps, create a partition of around 60GB to install windows. and second one of X (where X is rest of the remaining space - 40 GB (to be used for linux)). So, if you have 300 gig HD: you will have 1]60 GB NTFS for windows install, 2] 40 GB unallocated space, 3] ~200 (300 - 60 - 40) GB NTFS (call it data partition).
If you have windows already installed: You can do same, just shrink the boot partition for windows. And create other partition from windows.
Once you have this settled. You can install Ubuntu on the 40 gig partition. Boot into installer and select something else for drive selection* (this is important). And select the 40 gig partition. And install Ubuntu on it.
Your linux will automatically read the data partition and this partition will be available to both windows and linux automatically.
Swap space. If you absolutely want to have it, just create one of 8 GIG (size of ram) from the 40 gig and use remaining 32 for Ubuntu. or create a swap file instead of the dedicated partition.
Now, recent years use/purpose/creation has been up for debate, and from experience I am of the opinion that it is not needed if you have RAM of 8GB or more. I have q6600 (core2Quad) and 8 gig of ram and my server never uses swap space even with heavy workload. At a Financial institution I consult at, their cloud servers don't have provision for swap partition. And even Ubuntu 17.04 is doing away with swap partition and going to suggest swap files if needed from what I read. swap partitions were needed when ram was limited in the past, it is not the case any more. However, this is my suggestion. I am sure you can find people who can make valid points for the partition as well.

So that's it: for absolute simple set-up, you need three partitions: 1 for windows, 1 for linux and 1 for data (to be shared between os).

---

### Post by Geoffrey_Arndt on 2017-03-17
Mike Krall wrote:

"[COLOR=#000000]I'm on my way to a dual boot... set up specifically to move to triple or quadruple boot (multiple Linux distros)... Windows 10/Ubuntu 16.04, then ??? It's a very slow process for me... I understand lttle about computers... many quite simple things written about in this sub-forum and other computer-help sites go by me at the function level. "

Given the above . . . for a person knowing "little" about computers . . . above plan not a good idea.   Like not knowing how to swim and jumping into the deep end of a pool without a life preserver.

Best scenario is to have separate hardware for Windows & Linux.   This could include installing Linux (not Windows) on an external usbv3 SSD such as the SanDisk Extreme 500:  (smallest learning curve) [http://omahatechconnect.org/2016/07/04/sandisk-extreme-500-portable-ssd/](http://omahatechconnect.org/2016/07/04/sandisk-extreme-500-portable-ssd/)

Next best scenario is to install & run windows via Virtual Techology (Cubes OS (Xen), Virtual Box, VMware (moderate learning curve)

Worst scenario . . . traditional multi-boots sharing EFI partitions and Win Bootloaders (no company would go for that in a standard IT Dept or Data Center).

About "Data Sharing" . . .

Easiest & most  flexible solution . . . (imho) are Cloud related (dropbox, spideroak,etc.)   Another is just a 128gb or larger USBv3 flash-drive or even flash-stick.

Just my two cents for what it's worth . . . [/COLOR]

---

### Post by norafaithrainbow on 2017-03-17
I would give at least 30gb, but 20gb is fine if the minimum is 5gb.

---

### Post by Mike Krall on 2017-03-17
I think part of my idea about setting up for multiple Linux distributions has to do with your, "And the more you try different things the better idea you have of what you really like.", Fred.  I would find, if I can, what I like about different Linuxes.

Mike

---

### Post by Mike Krall on 2017-03-17
norafaithrainbow... I've just run into the idea of 15 GB minimum as a recommended amount a number of times.  My historical use of / is a little over 5 GB, which is more than original install, I believe, but I don't appear to grow it much. I'm just trying not to argue with folks going out of their way to help (the whole of the Linux/Ubuntu community).

---

### Post by Mike Krall on 2017-03-18
Geoffrey...

People's "two cents" always tends to being worth more than the estimate.  I may get down the road with my idea and find I need to change.  It seems doable and liveable-with, but I'm not at all unwilling to erase the machine, put in a 16.04.2 LTS single boot and go on to tomorrow.

---

### Post by Geoffrey_Arndt on 2017-03-18
Mike,

After more than 15 years of running Linux and another 5 running Unix, I've seen a LOT of changes.   It used to be "relatively" simple to setup dual-boots, and "very" easy to install Linux as the sole OS on a machine PROVIDED that machine had Linux friendly architecture (meaning essentially ALL Intel (cpu, gpu, wireless & sound) - - but also nVidia).  In other words, will the machine boot up without need for bootloader changes (e.g., nomodeset, etc.)? 

So, in our local PC computer club, when I introduced Linux as a realistic option other than a tightly controlled rented OS, I explained that BY FAR the best way to run a Linux machine is just to buy it pre-loaded (see my sig link).   If people can somehow manage to do that for their current PC's,  why not for a Linux PC?    For example, it takes all of 5 to 10 minutes for complete setup.   Initially, a barrier was a price disparity not favoring a pre-installed Linux PC.   That's getting to be less and less of a factor anymore.

   But I digress  . . . my point boils down to this . . . with all the OEM variation in implementing UEFI, today's machines can be very problematic (e.g., damn diffficult) to set up multi-boots.   I've seen **_hundreds and hundreds_** of newbie posters that tried to casually do it and they basically "crashed and burned" . . . . gave up and said "this is just not worth it" (they couldn't boot Linux, they couldn't boot Windows, the Linux Live Rescue tools/media didn't work for them, etc.   So, time for a trip to "Geeks R Us" or whatever to do a low-level reformat and reload of the latest (and not greatest Windows OS).   From what I've seen, DELL systems are most perhaps the mose UEFI specs compliant and best for other OS multibooting.

That's why I suggested to take the simplest and most stable method to run Linux . . . via it's own dedicated machine "designed"  for Linux, OR, on an external SSD such as the SanDisk I referred to, or lastly, via Containerization & VM's.   Note that if you plan to run any high-end games, VM's are not a great option.

Even with the methods I described, there is a learning curve that can be steep.   For example, just a couple days ago, I spent about 3 hours with a friend at the local Paneras to research running Linux off read-only live USB sticks (v3) or via the SanDisk Extreme 500.    After much fooling around with the firmware on his Lenovo Yoga notebook, we found we had to set a bios supervisor password to just allow the usb live flash-sticks to be recognized in the one-time boot menu (via F12).  But we couldn't (so far) figure out how to get the SSD to be recognized via one-time boot menu thus not allowing a fully installed OS to run on that machine.    Next step is to try and setup a supervisor password in the bios/firmware for the Disk System and hope that allows us further options - -  including disabling UEFI altogether and enabling "Legacy Mode" . . . . which is a good solution for modern UEFI machines as the disk system will still be running GPT (imho).

So, give multi-booting a try but do your homework first as you appear to be doing.   But don't be totally shocked if things go south.    Especially important to know what your "graphics" system is and what that may entail for the install.

---

### Post by Mike Krall on 2017-03-19
I'm back in 'oldfred's' signature link and I'm wondering a thing.  I've maybe knee-jerked myself into my long time standard dual-boot with Windows (since early 6.04).  Is a multiple Linux-distro boot with /mnt/data partition easier to set up than same with Windows in the boot also?  I mean, I don't mind jumping through hoops...  I'll either get it done or I won't... but being able to see the ground on the other side of the hoops has a certain level of comfort.

Mike

---

### Post by oldfred on 2017-03-19
Oldfred started using a NTFS shared data partition with Windows XP back in 2006 or 2007. That was when I realized I could have the Thunderbird & Firefox profiles in the NTFS partition and not have to reboot back into Windows just for email & standard list of bookmarks. I later added a Linux formated data partition for most new data as I was planning on getting rid of Windows. But one application kept me in Windows for several years.

Then when I finally shut XP down for good I had all my /home type data including the hidden profile folders for Thunderbird & Firefox in my /mnt/data partition. I regularly copy partition from home computer in Ill. to home computer in Fla. I used to copy to laptop an take to Fla, but hated ergonomics on laptop and now in Fla more so built new desktop for Fla. I found my backups of /home & /mnt/data  to flash drives easier to carry than laptop. :)

---

### Post by Mike Krall on 2017-03-19
In post #21 I didn't ask what I thought I asked.  I've got an excuse... it was a little late.  

Specific to "fast start", "fast boot", "secure boot", UEFI/GPT, no-Ubuntu-boot with attendant, necessary, try-this-try-that work around's, nomodeset, acpi_osi=Linux,etc.  Is booting only with Linux distros potentially less problematic? 

Mike

---

### Post by oldfred on 2017-03-19
windows has its own issues, you may have to run chkdsk to repair it occassionly and as with any system have to keep track of amount of free space inside the NTFS partitions. Windows really likes 30% free. Linux also needs free space but not quite as much.

Windows has all its default settings which make booting more complex. I do not think that is by accident.

But UEFI or BIOS boot is just a new choice with all new hardware now. That does make it a bit more complex as you start off with two (actually 3) boot choices before doing anything. UEFI with Secure Boot, UEFI or BIOS. Windows is just pre-configured for UEFI with Secure Boot, but will work with Secure boot off. LInux can install in any mode.

Fast Boot is a new UEFI/BIOS setting. My motherboard lets me set a delay, so I use 3 sec, just to have a bit of time to press a key to get into UEFI. Windows assumes that Windows boots and you only need to get into UEFI from Windows or alternative assumes you should never have to get into UEFI.

If you attempt to install Windows from scratch you have all the settings issues and if not the OEM/vendor version the issues of finding correct drivers for your system.

---

### Post by Geoffrey_Arndt on 2017-03-20
Yes . . . booting and managing multiple distros is FAR easier on a non-windows machine.   

No need then for uefi at all.   No need for secure boot.   But still have the more practical advantages of gpt disk operating system (many partitions).

This is being input on an Acer Travelmate B (Amazon $294.00 with Pingus Linux originally installed (which I_ quickly replaced_ with Solus on internal SSD (LiteOn 128gb SSD) and Ubuntu 16.10 on an  external usbv3 SanDisk 500 Extreme SSD)) _after enabling Legacy mode and disabling UEFI_.   Very easy, very flexible, very nice 10 hour laptop.

On a straight Linux (aka non-Windows machine), the install procedure after enabling Legacy mode is "slam-dunk" easy . . just let the OS install to the whole disk (and then do your multi booting on external SSD's such as the SanDisk) . . . . there is a 450 GB model now for about $150.00 that you can install, and reinstall a ton of Linux distros and just keep the ones you like best (like Ubuntu, Solus and Antergos in my case).

---

### Post by Mike Krall on 2017-03-20
Geoffrey,

I've run into similar-seeming approaches.  I'll have to get this done on the one 256 GB SSD.  

You did cause me to mess around in the American Megatrends ver. 302 firmware again.  Found "Secure Boot" hidden at bottom of scrolling "Advanced Mode" > "Security" page.  Disabling "Secure Boot" brings "CSM Support" out of grayed-out... could "Enable" / "Disable" if "Secure Boot" "Disabled".  "Secure Boot_Disable" causes subsection "Key Management" to be unavailable... for whatever that is worth.
------------------------------------------------------------------------------  

Right now I'm trying to reeducate to partitioning with sectors in mind (maybe not technically correct descriptor)...  the idea a disk is set up in units and having partitions start/stop at unit boundaries.  That along with references found about leaving little dead spaces between partitions... a thing in which I am a "person unclear on the concept".  Almost seems like a person ought to be defining partitions by units 'X', then start/stopping partition by +1 MiB / -1 MiB... would leave 2 Mib between... in theory.  

Mike

---

### Post by oldfred on 2017-03-21
All the current partitioning tools automatically use correct 4K boundaries. Just do not use an old copy of gparted.

Windows requires gpt partitioning for UEFI boot and only boots in UEFI mode from gpt. Should work with Secure boot on or off. 
Windows requires MBR(msdos) partitioning for BIOS/CSM boot.

In UEFI mode Windows has/needs lots of extra partitions, best to install it with its defaults.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)

---

### Post by Mike Krall on 2017-03-21
> **oldfred said:**
> All the current partitioning tools automatically use correct 4K boundaries. Just do not use an old copy of gparted.

Thank you.  I was getting to think that might be true just as I started into the GParted website last night.  Fell asleep in the chair prior to continuing.  

I did check the disk in Win. 10 under a 'Start' search for msinfo32 > System Information... under System Summary > Components > Storage > Disks.  First listed 'Partition Starting Offset' = 1,048,576... divided by 4096 = 256... a whole number... = correct alignment.  Probably an unnecessary exercise... 

Under the heading of:  I learn slowly, but I do...  Finding information needs date/last-update checking, or a person might find themselves back in the dark ages of UEFI/GPT, Partition Alignment, etc.  Preferably no earlier than 1/2 of 2016...  But then...  a person might find themselves missing the information from prior times on how to easily create a live, UEFI/GPT only, USB drive.  To read everything, or not to read everything?  That is a question...  =]

I'll do some reading...

Mike

---

### Post by sp40140 on 2017-03-22
One more piece of general information.
Ext2FSD is a windows program which will enable you to read EXT file systems (name says ext2 but it can read most of the linux filesystems). From my experience it works reliably.

---

### Post by Mike Krall on 2017-03-22
I'm about settled on not keeping Win. 10... still... I don't at all mind having more view of keeping and using it as it is what I've historically done.   

The links 'oldfred' put up in Post #27 (and links from those pages) caused me to feel, *if keeping Win. 10*, I would be best advised to move 'RECOVERY' (/dev/sda4) tight up against /dev/sda3, so MS sees what it expects to see (where it expects to see it), and can work between the two as designed.  I don't know if a large chunk of EXT4 (with or without 'unallocated') between end-sector /dev/sda3 and start-sector /dev/sda4 would be seen by MS, or not, on the basis of "working between"???  

The GParted Manual is amazing. I feel like I could simply create same-size /dev/sda4 at front of 'unallocated', copy/paste /dev/sda4 into it, delete source-/dev/sda4 and be done... that file system Label and UUID would be correct.  But, really, I'm guessing... or wishful thinking (a road I've been on many times) and I do know "everyone" says don't mess with MS partitions from anywhere but within Win. OS. 

I'm still tending to dumping Win. 10, though.  A GPartEd view of the disk shows /dev/sda1 first sector as 2048 (512bytes / sector)... or 1 MiB.  If partitioning for Linux-only, it seems I should start first partition (would be ESP-boot-whatever-it's-called) at that same point.  GPartEd looks like it wants MiB's, not sectors, so a start at 1 MiB, not 0 MiB.  The existing /dev/sda1 (ESP) is 260 MiB.  (fits Fat32 and 4K though the disk appears to be 512)...  so start /dev/sda1 at 1 MiB and end at 261 MiB looks right to me.  Have I become lost in unnecessary-ness?

Also noticed in GPartEd view of existing SSD disk that "the next" partition starts at one more (sector-unit) than "preceding partition" ends with.  I keep looking at that and thinking there must be one sector-unit (512 Bytes) between the end and start of the two consecutive partitions. Am I imagining things (misconstruing), or is that the little blank space between-all I thought I ran into in the Arch Linux partition manual?

Oh, there's more... but not now...

Mike

---

### Post by oldfred on 2017-03-22
Before the "new" 4K drives and larger gaps, gparted and other tools did not show any space between partitions as they rounded down.
Now with slightly more space between partitions, gparted may show a gap. But the few users that attempted to minimize the gap created huge issues and often had to re-partition and re-install. More details:
 [https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666) 

Whether keeping Windows or not, make a backup. You paid for it. And later if selling system, that buyer will probably want Windows.
One user who must regularly buy a newer system, said he would buy a laptop with a HDD, and before even booting it, remove HDD and install SSD and then UBuntu. Then later sells laptop with "new", unused and no user data copy of Windows.

I got a system for recording TV, planning on using Ubuntu. But then Xfinity/Comcast allowed watching shows, but only Windows worked. I had only shrunk Windows when I installed Ubuntu, so I was able to re-expand it and have to use it. Now I remember why I shutdown XP. :)

      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by Mike Krall on 2017-03-22
I wouldn't know enough to even think about thinking about out thinking GParted...  =]

I've got reading to do.  Maybe I'll make it back tonight, but maybe not.  I need to get some view of partition structure, but more so, view of process phases for multiple Linux and /mnt/data.  I've got some pieces but not a picture.

Oh, I believe I have all the backup I need... both a Recovery DVD and a System USB.  I've not added anything to this system besides Chrome and X-Marks and have dumped some of the foofah.  If I have to put Win 10 back in it will only be a minor pain. And I've got my link-notes, by date, on "What-to-do-if-it-don't-boot".  Another couple of weeks, I'll have this done... maybe...  =]

Mike

---

### Post by oldfred on 2017-03-23
Some recovery drives are not much, and rely on the recovery partition on the hard drive. You want to be sure it is a full recovery.

When I posted this I had two installs on SSD, another install & /mnt/data on HDD.  You can adjust sizes to be on one drive.
I now have Zesty & Yakkety on sdb. I show server in label currently, but forget that I installed that. (old in oldfred?)
       Oldfred's current partitions Dec 2015
[URL="http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413"]http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413


[/URL]

---

### Post by Mike Krall on 2017-03-23
Thank you... 

Spent a very little time in Post#33 link... I'm having to "not computer" from nearly now through maybe Saturday.  I think I've got a working grasp on partition alignment... convert partition 'start' to sectors, if result of division by 8 is whole number, the partition is aligned (Rod Smith links).  My "sudo parted /dev/sda unit s print" (run off 'Try' on live-usb)  looks like (for 'Sector size' and Partition Table) your linked:
 
fred@trusy-ar:~$ sudo parted -l
[sudo] password for fred: 
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

I noticed a couple of things, but I don't know if I read well.  Are the tables truely in KB/MB/GB or is it actually KiB, etc.?  Still in the linked /dev/sda disk...  There is an emptiness between sda6 and sda5... approx. 68GB.  Is that equivalent to my Win. 10 shrink creating "Unallocated" space (a size but no file system, label, UUID, etc.)?

I've got to go...

Mike

---

### Post by oldfred on 2017-03-23
See this entry for unit.
man parted

       sudo parted /dev/sda unit s print
sudo parted /dev/sda align-check opt 

Unallocated is just that, you have not created a partition in that space.

---

### Post by Geoffrey_Arndt on 2017-03-23
Sometimes a video is worth a ten thousand words (or more):

Intro to Partitioning:   [https://www.youtube.com/watch?v=BtSQIxDPnLc](https://www.youtube.com/watch?v=BtSQIxDPnLc)

Partitioning Part 2:   [https://www.youtube.com/watch?v=O5kh_-6e4kk&t=9s](https://www.youtube.com/watch?v=O5kh_-6e4kk&t=9s)

And finally, Joe Collins on Ubuntu Partitioning-Trending Practices:   [https://www.youtube.com/watch?v=1OEidskpcC0](https://www.youtube.com/watch?v=1OEidskpcC0)

---

### Post by Mike Krall on 2017-03-26
I caught myself up in a volume-variable Mobius strip... 
--------------------------------------------------

Geoffrey,

Thank you for the video links... it's helpful.
--------------------------------------------------------- 

'oldfred',

I understand the necessity of full disk image now.

I'm going to see what the Post #35 code for both the new and old ASUS show... partly on a curiosity about what GParted did for alignment and at ends-of-disk when I simply specified " / ", "swap", "/home", "apply" installing 16.04 in the old ASUS.

Mike

---

### Post by Mike Krall on 2017-03-26
GParted shows my "dumped in partition size" install of 16.04.2 LTS (old ASUS) the same as it sees the Win. 10 ASUS... sector view of both with 1st partition start at 2048 sectors (1 MiB)  with 'end' 1 sector prior to aligned 'start' of 2nd partition. I assume any size partition gets auto-corrected in that manner by GParted.  Another thing I checked (who knows why) was the total sectors of both disks less the 'end-sector' of the last partition.  Both partition structures fill their disks... no specified space left at disk end.  Both have 689 sectors after the last partitions end-sector.  There is a reason.  Maybe I'll have to know what/why sometime.

I'll start EFI/ESP /boot/efi, /dev/sda1 at 1 MiB (2048 sectors), though I feel sure GParted would auto-number to that.  I've run into various thoughts on UEFI/GPT /sda1 boot partition sizes:
   *  Use what MS gives (in my case 260 MiB).  Reasons being... it will work... don't even think to mess with MS boot partiton... the easy/logical route in Win./Linux dual boot.
   *  Rod Smith recommend 550 MiB (from "RodsBooks" partition pages).
   *  Various and sundry 100 MiB thru 1 GiB from anywhere a person wants to look
   *  'oldfred' has a recommended MiB number, but I've lost it in the hen scratch of notes I've accumulated in this project... if he would say again, please.

I'm wondering what drives one size over another for a UEFI/GPT boot partition?  

I read the MS links 'oldfred' posted again and roughly understand the constraints FAT 32 puts on a UEFI/GPT boot partition.  Do Linux-only UEFI/GPT disks not have /sda1 w/ FAT32, or ???  

Mike

---

### Post by oldfred on 2017-03-26
Windows used to use 100MB for ESP, and most systems did not have an issue.
I use 50 to 100 on a smaller flash drive like 64 or 32GB.
But I normally suggest 300 to 500MB for ESP.

I think Rod Smith wants extra room for potential other boot loaders like his rEFInd or other ways to boot than current configurations use. Best to allocate a bit too much. But if smaller drive the new(?) Windows default of 260GB should be fine.

I only have multiple copies of Ubuntu. I do put an ESP and bios_grub on just about every drive even drives that may currently only be data drives, so later I could add an operating system in either UEFI or BIOS boot mode.

---

### Post by Mike Krall on 2017-03-27
Thank you...

In partitioning it seems I should use the large end of rational sizes... there is So much room on this 256 GB SSD relative to how much room I use on a computer.  

I've made a Win. 10 disk image with 'oldfred's' Macrium Reflect link... Post #31.  Set it up to auto verify, which it did. The 'unallocated' space was not copied, as it would have been if I had cloned the disk.  I tossed a coin on that decision.  It seems a restore would create a disk with the 'unallocated' space at disk end and /sda4 moved next to /sda3 (C:\) instead of between /sda3 and /sda4, as it is now.  What difference that would make, I don't know.  Anyhow, Windows is going away, soon... no matter. 

It seems I should be able to GPartEd an install of three partitions: 500 MiB - EFI/ES, /boot/efi...  approx. 25 GB (23.28 GiB) " / "...  with "swap" at disk end, and do it all at once unless there are reasons not to???  From the Ubuntu Swap FAQ... for my 8 GB RAM the recommend is 3 GB with no hibernation and 11 GB with hibernation.  I don't hibernate and understand a multiple Linux distro machine using a /mnt/data partition *can't* use hibernation.  Still, I've run across references to having more 'swap' (either partition or file) for other reasons... a little more than RAM is a common feeling.  I can't make any of that come straight and I could use some help with it. 

I got figured out a partition's "Start" number in MiB correlates to alignment *if* it is a whole number.  A person has to run it into numbers of sectors and divide them by 8 to see it (a whole number), but it's true.  As mentioned, it seems GPartEd auto-adjusts partition "End" to one sector short of following partition "Start".  I don't suppose this makes much difference as GPartEd seems to make things "right" automatically... I don't know if PartEd through command line does... maybe it's more literal. 

Mike

---

### Post by oldfred on 2017-03-27
If you have 4GB RAM or more, you may not even need swap. I suggest and use 2 or 3GB just to have some. Old rule of 2X RAM was when you only had 256 or 512MB of RAM. And you only need swap equal to RAM if hibernating, but then have to have a separate swap for every Linux install. Windows is the one that cannot be hibernated if you dual boot as it keeps all NTFS partitions mounted. 
Starting with 17.04 they are planning on no swap partition, but using a swap file.
If planning on editing videos or very few other applications that want/use an unlimited amount of RAM, may having larger swap make sense.

       17.04 Ubuntu To Begin Making Use Of Swapfiles In Place Of SWAP Partitions
[http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html](http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html)
no more than 5% of free disk space or 2GiB, whichever is lower.
[https://wiki.archlinux.org/index.php/swap#Swap_file_creation](https://wiki.archlinux.org/index.php/swap#Swap_file_creation)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
[https://help.ubuntu.com/community/SwapFaq#What](https://help.ubuntu.com/community/SwapFaq#What) is swappiness and how do I change it?

---

### Post by Geoffrey_Arndt on 2017-03-27
Also, I've read hibernation (deep slumber) is disabled by default in Ubuntu since about 9.xx.   It can be reactivated but most don't.     So, in place, there is suspend short, and suspend wake only on power depress (based on time duration from suspend start).

As OldFred indicates, swap not especially needed any more with sufficient ram - my machines are 4 gig, 6 gig, 8 gig and 16 gig ram.    Have never had these machines hibernate.

Really now, the question is:

>  do you keep a Win/Linux dual boot on permanent drives (single drive, two drives)?,
>  do you keep a Win single boot with option to boot into an "installed" external drive?  (e.g.,  a USBv3 SSD) (note, I don't consider a usbv2/3 flash-stick with "persistence" enabled to be the same as an "installed" system as above),
>  do you overwrite Win with a full-disk Linux install and keep system UEFI?
>  do you overwrite Win with a full-disk Linux install and disable UEFI (and enable Legacy/CSM mode)?  <this is the most user friendly, easiest method to run Linux exclusive of buying a pre-loaded Linux PC . . . IMHO).

I've done all the above, but now have only Linux on my 3 laptops and 1 System76 Sable AIO - - and run several distros via two portable usbv3 SanDisk Exteme 500 SSD's . . . works very well with no possibility of a Win10 update overwriting EFI partition or any other similar scenarios.

---

### Post by Wadim_Korneev on 2017-03-28
[COLOR=#000000]My Skylake system with 16.04 did not need to install, but works with the newest Intel video driver. When I installed it, it also now gives me a warning on another driver may be required, but that is really the Kabylake one. Not sure if newest 16.04.2 includes that driver automatically or not.[/COLOR]

---

### Post by Mike Krall on 2017-03-28
I've been rereading... ASUS problem links from Post #3 & #7... plus links from the links.  And I've been reading about 'secure boot'... mostly from first 3/4's of 2016... none found from 2017.  It seems as if with late-2016 Ubuntu updates and move to 16.04.2 many feel 'secure boot' is not an obstacle.  Still, Rod Smith encourages disabling secure boot (might be "too old" writing, though).  What do you feel the state of installing with 'secure boot' enabled is today?  In a Linux system, is 'secure boot' a valuable tool? 

The question of 'swap' (partition or file... not size)... There is a lot written (I've got links on top of the links 'oldfred' provided)... Roughly, it seems easier to provide 'swap' by partition.  

Some folks make partitions first, then install, and some make and install in one swipe (what I did with my old ASUS and 16.04.2).  I'm not finding process description of making partitions first, then installing.  Are partitions created while in "Try Ubuntu" then filled during "Install Ubuntu"?   Do you have preferences? 

My install looks like this:  /sda1, 499 MiB, ESP boot, FAT32...  /sda2, 23,842 MiB (25+GB), " / " with home, EXT4...  /sda3, 2862 MiB (3+GB) "swap" (I can't remember if it gets a file system, or not).  I know what whole MiB needs to start each partition.  Figuring the MiB 'swap' would start on took a while.  I got leery of the 689 sectors of ??? at disk end and decided not to have GPartEd put the 'swap' MiB's at end of space... probably ill founded leery-ness, though.  

The space between /sda2 and /sda3 is +/- 228 GB (not GiB).  I've assumed the space will be 'unallocated', or rather, *should be* 'unallocated', is right?  

Do you see anything I'm missing or misunderstanding?  

One last... I made the 16.04.2 Live-USB nearly a month ago.  Are there reasons I should make it again?
-------------------------------------------------------------------

I'm intending to go on to /mnt/data partition.  If I don't, for some reason, I'll be close to your third listed option, Geoffrey... could easily turn 'unallocated' into '/home'... or not... don't need the room.  I am really looking forward to the idea of running my simple little computer world on other Linuxes...  =]

Mike

---

### Post by oldfred on 2017-03-28
If you have 16.04.2 it will just update after/during install to add changes since. Download of a version does not ever get updates as once released as ISO, it is frozen.

I just find partitioning with gparted a bit easier. But if you do not know or do not like gparted then you can partition during install. You still have to use the Something Else install option and choose (change) partitions for /, /home, but swap is auto found if it already exists. Installer actually uses swap during install.

I still think UEFI Secure Boot is just a Microsoft marketing program. If you have a product that always has security issues with virus and hacks, what better to market a system that says Secure Boot. Even though secure boot has essentially nothing to do with most virus. The main MBR boot sector virus was Sony with its DRM software to prevent you from playing music without paying.

Older post
 Torvalds clarifies Linux's Windows 8 Secure Boot position
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security 

Also some Linux drivers were not secured with the key, so entire Secure Boot chain was a work around. Some of that has been fixed. Even Windows had issues with some of that as vendors had to make sure all drivers were enabled with security key.

---

### Post by Mike Krall on 2017-03-28
Late lunch...

I'm hoping 16.04.2 has Kaby Lake facility...

I've turned 'Secure Boot' off.

I'll use GPartEd through Live-Install.  I'll do this as I've done before... *all in one shot*...  by chosing "Something Else", build the partitions, etc.  

I've gotten help and clearing-up from this, also: [https://ubuntu-mate.community/t/install-ubuntu-mate-using-something-else-method/651]("https://ubuntu-mate.community/t/install-ubuntu-mate-using-something-else-method/651")

Comments?

Mike

---

### Post by oldfred on 2017-03-28
Looks like a typical Something Else install.

---

### Post by Mike Krall on 2017-03-29
I started into "Install Ubuntu", got to the partition builder, thought, "This isn't GPartEd.", went ahead and built the EFI, " / ", and "swap" (start, stop, backup, redo...)  Stopped to look at it... make sure before clicking "Install", then thought, "I'm not going to get to 'Name' or 'Label File System' for partitions in this." 

I thought about that for a while.  I don't know anything about working with multiple Linuxes with /mnt/data as far as keeping things (me and them) straight.  It doesn't seem viable to me to just sda1, 2, 3, 4 the different " / " 's and have an evolving crib sheet stuck to the table.  What organising things have been found to work well?  

Things I'm wondering:  
*  Does each " / " need to be a different "User" and/or "Host"?  
*  Does having different "Host"'s in the same machine cause problems interfacing with the world? 
*  Can "My Name" be the same everywhere, or ???  
*  Same or different passwords for each " / " ?   

I can't think of any others, but I feel there are...

Mike

---

### Post by oldfred on 2017-03-29
I have only installed Ubuntu and its various flavors.
I always use same name & password. (something about "old" in oldfred)

My old "large" 650GB drive eventually had 5 or 6 Ubuntu versions, some obsolete. 
But when first using it, I created 25GB for /  & 100GB for data. 
And of course installed new system into data partition. Fortunately I had not saved any data. And showed me why backup important.

I run Boot-Repair occasionally. Part of Boot-Repair is bootinfoscript and I run that as part of my regular rsync backup, so I have latest configuration stored.
 Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript) 

I also label all partitions, but installer does not show labels. When I forget to include label when using gparted, I often just use disks. Gpt drives now have two labels. To see labels:
      
 lsblk -o NAME,LABEL,SIZE,UUID,MOUNTPOINT 

 sudo blkid -c /dev/null -o list
ls -l /dev/disk/by-id

Partial list:
```
fred@Z170N:~$ ls -l /dev/disk/by-label/
total 0
lrwxrwxrwx 1 root root 10 Mar 28 08:56 backup_b -> ../../sdb4
lrwxrwxrwx 1 root root 10 Mar 28 08:56 data -> ../../sdb6
lrwxrwxrwx 1 root root 10 Mar 28 08:56 ESP -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar 28 08:56 ESP_B -> ../../sdb1
lrwxrwxrwx 1 root root 10 Mar 28 08:56 ISO -> ../../sda3
lrwxrwxrwx 1 root root 10 Mar 28 08:56 ISO_b -> ../../sdb3
lrwxrwxrwx 1 root root 10 Mar 28 08:56 zesty -> ../../sdb2

```
Noticed I am missing a couple of labels, back to correcting that. Every time you format a partition label is erased.
Someone did comment that with a data partition you do have to be careful of user number. Fedora used to be 500, but changed to 1000 as default first user. Debian based use 1000. Not sure about others.

>  One problem I encountered with all those distros is the default user is 500 on some 1000 on some. To share data easily you need to always be the same user number, not just the same name. The control is UID_MIN in /etc/login.defs 



---

### Post by Mike Krall on 2017-03-29
Using same 'My Name', 'User Name', 'Host' ('Computer'), and password  is going to help me...  it's the way my "logic" system runs...  =]

Ah, details on details and implication on all.  I may find I'm in well over my head... but I won't know until I get there. 

Back to GPartEd...

Mike

---

### Post by oldfred on 2017-03-29
The nice thing about Linux is that it is relatively easy to install, experiment with and then if you mess up, just reinstall.

But back up procedures are important for your data. And if you modify configurations you need to kept track of those. I copy any files I manually edit in /etc into /home to have a copy when I run my backups of /home. And with separate /mnt/data, I separately back that up.

After I converted to new installs only and many test installs just to see what new versions were like, I found I was spending time resetting system & re-adding links. So I tried to do as much as I could with command line. Then copied commands from history (first time needed lots of cleanup of errors) into a file and made a script to semi-automate configuration. I am up to about 75% configured with two scripts and if just a test install, that often is all I need. 

But you have to walk before you run, so install, install again and find out what you like or want.

My scripts which would not apply to you as I have embedded UUIDs, specific paths, and other unique configuration.
But gives an idea of what you can do.
 Oldfred's install scripts
[https://ubuntuforums.org/showthread.php?t=2347811&p=13588662#post13588662](https://ubuntuforums.org/showthread.php?t=2347811&p=13588662#post13588662)

---

### Post by Geoffrey_Arndt on 2017-03-29
> **Mike Krall said:**
> I started into "Install Ubuntu", got to the partition builder, thought, "This isn't GPartEd.", went ahead and built the EFI, " / ", and "swap" (start, stop, backup, redo...)  Stopped to look at it... make sure before clicking "Install", then thought, "I'm not going to get to 'Name' or 'Label File System' for partitions in this." 

[COLOR=#0000ff]That's OK . . because later after install, you can use (open) the gparted program to access your partition table and add, change, delete labels etc.[/COLOR]

I thought about that for a while.  I don't know anything about working with multiple Linuxes with /mnt/data as far as keeping things (me and them) straight.  It doesn't seem viable to me to just sda1, 2, 3, 4 the different " / " 's and have an evolving crib sheet stuck to the table.  What organising things have been found to work well? 
[COLOR=#0000ff]
You're cornfusing "/ root" with partitions . . . . not the same thing.   Root is normally a subsection of a partition.  It's like a Parent/Child relationship.[/COLOR]

Things I'm wondering:  
*  Does each " / " need to be a different "User" and/or "Host"? 

[COLOR=#0000ff]No, . . . there can be many 2 - 200?? different users under (within) root.   for a home PC, more like 2 to 5 is about average.   Each user will have their own distinct /home/user1, user2, user3 set of directories (which include the standard 7 or 8 directories that each /home has (such as documents, pictures, etc.).[/COLOR]

*  Does having different "Host"'s in the same machine cause problems interfacing with the world?

[COLOR=#0000ff]It is basically inaccurate to have more than one "Host" because the "Host" means the "Computer Name" . . . I usually use the Model name - my host is "Sys76-Galago" on this laptop, and it applies to all users and all partitions.[/COLOR]

*  Can "My Name" be the same everywhere, or ??? 

[COLOR=#0000ff]No - you want each user to be distinct, meaning both user name and user ID (which the system assigns- like user 1 is typically user 1000).   
[/COLOR] 
*  Same or different passwords for each " / " ? 
[COLOR=#0000ff]
Again - - passwords are unique to users, . . . . users and partitions are totally different things (so, I don't know if it's even possible to associate passwords to a partition - although technically it could be).   Important thing to remember is one unique name and one unique password for each user.   Note, you don't have to create a second or third user right away - - it's often done later after the first user (also known as the sudo'er or admin) sets up his profile and user customizations).[/COLOR]

I can't think of any others, but I feel there are...

Mike

Hope the above info in blue helps.   One bad thing about learning Windows is . . . you learn Windows, but you don't learn "basic" computing.

EDIT:   note . . . if you install multiple distros, each of course, in their own partition and set of directories, then, you can use a different "Host Name', different "User Names" etc. because each install is it's own Domain (like a little Kingdom).   But I'd still use the same host name, because all the installs are basically done on the same machine (or same Host).   Like the country "America" hosts all "States"- - - America applies to them all.

---

### Post by Mike Krall on 2017-03-29
You-all are trying to help a dumb-ass...  

In 'Try Ubuntu'... in GParted... 'Device'... 'Create Partition Table'... and now past the warning and having set for 'gpt' partition table.  Filling in the numbers I'm fine. Making sure 'Align to:' is MiB... 'Create as:' is 'Primary Partition'...

Now... my understanding is 'Partition name:' is at my personal convenience... call it what you will, or don't.  

Under 'File system:'...  The first partition, what will be sda1 (efi, boot, esp, GUID Partition Table, and more)... is it supposed to be (needs to be) fat32?  The partition with " / " in it... this case sda2...  is ext4 file system.  'linux-swap' has no file system.

Under 'Label:'  (File System Lable, also Volume Label)  It seems there needs to be very specific things put into this for a boot partition or a partion with " / " in it, or for a 'swap' partition (I'm guessing 'linux-swap' for this one).  Would you say what the correct labels are, please?

Never mind I get past that point to 'Add', past that point to all partitions correct and added, then towards "Apply" and...  Wait a minute, where's the flags... when do they go in?  I hesitate strongly at clicking "Apply" on "fear of the unknown"... Windows gone away (not that that is not fine), but without an Ubuntu to replace it... as in "Sorry, dude, you forgot the boot flag". 

I'm going to do something else for a bit...  

Mike

---

### Post by oldfred on 2017-03-29
Lots of links:
 It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

I have posted this many times, and most of it is in the link in my signature. Did you review that or search forum?
If multi-booting I do not suggest separate /home as that is more for beginners, but not first time installers with only one system. Use a data partition like /mt/data. details also in my signature on UEFI boot.

---

### Post by Geoffrey_Arndt on 2017-03-29
You absolutely don't need to be a "Power User" to run Ubuntu (or most any Linux distro).     Don't need to know "Jack" about partitions or gparted.

. . . . [https://system76.com/desktops/meerkat](https://system76.com/desktops/meerkat)

---

### Post by Mike Krall on 2017-03-29
'oldfred',

I've read every link in your signature, many more than once, and read links where your links took me, as well as all the links to links to other links in this thread... plus my own searches.  I've been exposed to a tremendous amount and was happy to be. I think about it like this... It's tough to read between the lines when you don't know what the lines mean.   I do have GParted figured out, it's was a matter of not knowing all the steps... and not finding them in searches, mostly because I'm a terrible search-phrase writer.  I feel like I know the step-by-step now (got lucky in a search that linked me to others).  I'll find out in a bit.

Mike

Edit:  This is the link I found... would be different for every user, but...  [https://docs.google.com/presentation/d/1HEBkP-nAPAaouS-DzLsFldL7vH6PMmUIt_wtBQXUeag/edit#slide=id.g13375c473d_0_19]("https://docs.google.com/presentation/d/1HEBkP-nAPAaouS-DzLsFldL7vH6PMmUIt_wtBQXUeag/edit#slide=id.g13375c473d_0_19")
-----------------------------------------------

Geoffrey,

I really appreciate your making time for your post (#52).  It made pieces fall together... gave me other ways to look at the same thing.  Thank you.

I did try to buy an Ubuntu machine both last laptop and this one.  Various things got in the way.  Actually, for me, all this I'm doing here and did before is more fun. 

Mike

---

### Post by Geoffrey_Arndt on 2017-03-30
Sometimes a person can only stand so "much fun" . . . . (it's no fun at all if you're working with PC's you actually need to run to do your work or other essentials).   Test or extra machines are a "horse of a different color" . . .

---

### Post by Mike Krall on 2017-03-30
> **Geoffrey_Arndt said:**
> Sometimes a person can only stand so "much fun" . . . .

"There are lots of things that I have done, but I ain't never had too much fun..."  =]

---

### Post by Mike Krall on 2017-03-30
16.04.2 LTS went in.  There were internal problems (reported) and 4 restarts didn't change that.  I intended to follow into the problem last night but it was late.  This morning there has been no "problem" popup through a few restarts...  magic. The disk looks like....

sda1 ESP System Partition fat32 /boot/efi 499 MiB boot, esp
sda2 16.04 LTS  ext4 " / " 23.28 GiB
Unallocated 211.91 GiB
sda3  Swap  linux-swap  2.79 GiB

All the (unnecessary) fussing I did with GB to GiB to sectors for partition size and alignment worked out... started 'unallocated' at a given MiB for a 2862 MiB Swap to finish at 'no more room' and not have GParted have to shrink swap size or note free-space at end of Swap.  GParted left all my other numbers alone, too.  There's one thing I roughly get.

I'm going to have to do some thinking about /mnt/data and it's implications.  I've got link references to Separate Data Partitions (what I've scooped out of 'oldfred's' links here and through his 'signature link', plus my searches) to read again to see more than the partially built puzzle I have now.  Right now /mnt/data looks to have a lot of pieces, but that is likely not functionally so.

Mike

---

### Post by Geoffrey_Arndt on 2017-03-30
Well done Mike . . . so no more Windows/dual-boot?   No loss, you have the better OS.    Might want to mark this thread as solved (see "thread tools" in header), so you can start with fresh threads on using/managing Ubuntu if needed.


GG

---

### Post by Mike Krall on 2017-03-31
I'd thought to go on from the original intent of Windows with multiple Linux versions... now just multiple Linux versions.  If you-all feel I should do otherwise, please say.

I'll say it may be a bit before I need help (don't know that for sure... messing with the 16.04 set up).  I've actually got a few questions now, but I'll first start rereading the /mnt/data and 'separate data partition' links... see if I can grasp it well enough to not ask questions and get answers to which I have to reply, "Really? Well, I thought..."   

Mike

---

### Post by leopoldgt on 2017-03-31
use linux dual boot and prepare a usb for live windows? just for the times when nothing else seems to be working? you can try it via vmware route too.

---

### Post by oldfred on 2017-03-31
We are here to answer questions & to help.
But appreciate those who at least have tried to find solutions on their own.

Most of my instructions do assume some level of understanding.
I started a shared NTFS data partition soon after  started dual booting XP & 6.04. I am trying to understand/learn Linux and my wife wanted to read email or do Internet with standard bookmarks in Firefox.  So I moved some data into the NTFS partition and just mounted it in /home. And used Firefox & Thunderbird's profiles to find new location for them.

But then I saw linking.
I have over time had data partition(s) mounted in /home, but got duplicate mounts in Naulitus, in / which some pointed out was not very standard and in /media. But finalized on /mnt/data. I first test was just one folder called of all things test and one folder temp. Then if I messed things up, I did not lose my actual data. And only later learned to do better backups, but managed not to lose my data.

another set of instructions.
 howto shared data - by  captain_chaos2
[http://ubuntuforums.org/showthread.php?t=2213485&p=12979581#post12979581](http://ubuntuforums.org/showthread.php?t=2213485&p=12979581#post12979581) 

      
 Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by Mike Krall on 2017-03-31
Thank you for the links, 'oldfred'.  

I started here...  [http://www.linfo.org/mnt.html]("http://www.linfo.org/mnt.html")

Mike

---

### Post by Mike Krall on 2017-04-01
> **leopoldgt said:**
> use linux dual boot and prepare a usb for live windows? just for the times when nothing else seems to be working? you can try it via vmware route too.

I've got a Win. 10 image on an external HDD.  I don't know if that is a bootable thing or not, but believe so.  If I've guessed correctly, I hadn't thought about that as useful... that I could use the Win. 10 image in ways I use a Linux .iso image.  Thank you for making the point

Mike

---

### Post by Mike Krall on 2017-04-06
I've got a better understanding of /mnt/data separate data partition.  This link from 'oldfred' (post #63)helped me a lot:

"How-to shared data - by captain_chaos2"
[http://ubuntuforums.org/showthread.php?t=2213485&p=12979581#post12979581]("http://ubuntuforums.org/showthread.php?t=2213485&p=12979581#post12979581")

I've read the whole thing a few times... the evolution of problems and solutions.  There were a lot of side-notes I chased that helped me have a whole picture as opposed to just a list of "do this, do that".  For me, if I don't have some idea about *why*, *definitions*, and *details* I'll have a very difficult time doing a thing.  Much of that listed is here, or linked from here, or easy to find through searches from here.  I've also cross referenced on other /mnt/data separate data partition links from this and other threads.  I'm an expert now, right?  How would you bet that?  

I've got questions (and you are one nickle richer)...  

A thing I can't get settled:  Some of the commands are "outdated"...  "gksudo /etc/fstab' for editing 'fstab' to mount /mnt/data. And some of the indication on command-use ('oldfred's' "Don't 'sudo' graphical/GUI') I'll avoid because I asked for advice.  I've looked into what the alternatives are... installing 'gksudo',  installing 'pkexec' for Nautilus and Gedit, installing 'nautilus-admin', and probably others I haven't found.  What is 'best practice', this date, 16.04.2 LTS editing 'fstab' (and similar) as " / " or 'admin'? 

Mike

---

### Post by oldfred on 2017-04-06
I occasionally still use gksudo gedit, but now suggest sudo nano.

Nano will run when you have gui issues if you can still boot to terminal so worthwhile to know nano. It is part of every standard install as far as I know.

To manually mount.
 sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod after mounting either manually or via fstab
sudo chown $USER:$USER /mnt/data
#sudo chmod 775 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
#Edit fstab with your UUID:
sudo blkid -o list
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab 

Be sure to unmount if manually mounted first, and run this to be sure edit is valid. If it just returns with no errors then the edit of fstab is ok & it remounted everything.

typical entry with my UUID:
      
 UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext4         auto,users,rw,relatime               0  2 

#Verify entry is ok, if no errors it is:
sudo mount -a

---

### Post by Mike Krall on 2017-04-07
Thank you. 

Messed with 'sudo nano' then ran into this (which helped):  [https://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/]("https://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/")

Another thing I ran into that helps me make a picture:  *"Mounting simply means that you mount/insert/attach a disk partition onto the filesystem hierarchy. It's a folder you make and you attach the partition to that folder so that the file/folders on that partition will be accessible by the user/operating system."*  Yeah, I know, 'oldfred' has been saying that for years!

Mike

---

### Post by Mike Krall on 2017-04-07
From 'oldfred':

I[I] occasionally still use gksudo gedit, but now suggest sudo nano.

Nano will run when you have gui issues if you can still boot to terminal so worthwhile to know nano. It is part of every standard install as far as I know.

To manually mount.
sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod after mounting either manually or via fstab
sudo chown $USER:$USER /mnt/data
[COLOR="#0000FF"]#sudo chmod 775 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data[/COLOR]
#Edit fstab with your UUID:
sudo blkid -o list
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab 

Be sure to unmount if manually mounted first, and run this to be sure edit is valid. If it just returns with no errors then the edit of fstab is ok & it remounted everything.

typical entry with my UUID:

UUID=a55e6335-616f-4b10-9923-e963559f2b05 /mnt/data ext4 auto,users,rw,relatime 0 2 

#Verify entry is ok, if no errors it is:
sudo mount -a[/I]
-------------------------------------------------------------------------------

I need to make sure I understand the blued section...  It looks to me like a choice.  Use either 'sudo chmod 775 /mnt/data'  or use  'sudo chmod -R a+rwX /mnt/data.  If so, I don't know what the choice is... why one or why the other.  

Could you say this...  *The big "X" will also not make files executable unless they were executable to begin with*... another way, please.  I'm simply clueless. 

Mike

---

### Post by oldfred on 2017-04-07
I commented out (#) the chmod 775.
One of the users who knows and understands all that pointed out that 775 is not the correct way.

 From user Morbius1
[http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259) 

See this thread & post #8 on why not to use octal notation:
[https://ubuntuforums.org/showthread.php?t=1795369](https://ubuntuforums.org/showthread.php?t=1795369)

---

### Post by Mike Krall on 2017-04-07
Thank you...  I've got more reading to do...  =]   

Mike

---

### Post by Mike Krall on 2017-04-08
I've been wondering about the basics of how to deal with multiple Linuxes from the disk and partition point of view.  I've got /efi/boot at the front with " / " next to it and 'swap' at the end with 212 GiB of 'unallocated' between.  I'm guessing here...  it seems like a person puts the /mnt/data partition at the end with 'swap' and adds other distribution partitions at the front... leaving whatever amount of space between left as 'unallocated'.  As I mentioned in the early pages of this, I *really* don't use much space in a computer... old ASUS /home is about 6 GiB.  Anyhow, how would you organize the partitions and space?

Mike

---

### Post by Dennis N on 2017-04-08
It won't matter at all where on the disk the data partition is. It can be on the same disk as the OS or on another disk, for that matter. The same is true for the / partition.

The EFI system partition can theoretically be anywhere - you can even have two or more of these. But Ubuntu will only install to the one on sda; most people locate it as the first partition, but it may work elsewhere on sda with Ubuntu - but never tried it to see what happens.

My sdb with two EFI partitions (only other distros will use these on sdb; any Ubuntu-based systems on sdb will only use the ESP system partition on the sda disk):

```
Model: ATA WDC WD10EZEX-22B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  211MB   210MB   fat32           EFI System Partition  boot, esp
 2      211MB   33.8GB  33.6GB  ext4
 3      33.8GB  38.0GB  4194MB  linux-swap(v1)
 4      38.0GB  58.9GB  21.0GB  ext4
 5      58.9GB  86.2GB  27.3GB  ext4
 6      86.2GB  113GB   27.3GB  ext4
 7      113GB   141GB   27.3GB  ext4
 8      141GB   168GB   27.3GB  ext4
 9      168GB   195GB   27.3GB  ext4
10      195GB   195GB   83.9MB  fat32           EFI System Partition  boot, esp
11      195GB   223GB   27.3GB  ext4
12      223GB   250GB   27.3GB  ext4

```

---

### Post by oldfred on 2017-04-08
I usually put ESP & bios_grub as first two partitions and swap as last partition. Those are partitions I probably will never change.
In middle I have large /mnt/data and multiple 25GB / (root) partitions, a some what larger /mnt/backup that is not a real backup but copy of some more important files from other drive, and partition on every drive for ISO, so I can directly install from one drive to the other drive or from SSD to flash drive.
Real backup is versioned, or if file is changed you still can find older version. My real backups are to DVDs, flash drives and other computers.

 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by Mike Krall on 2017-04-11
Life is getting in the way of life.  

The only progress I've made on this part of life is to find out the external HDD needs work (or replacement).  Found I've lost my Win. 10 image (still have lower level recovery DVD and Windows USB stuff that could be used to replace if needed).  Tried to figure and am still dithering on how easiest to back up the existing Ubuntu disk.  I'm thinking imaging /boot/efi partition and / partition would be simplest (no personal data in this machine yet, and only minor changes... all documented...  to / partition)... could easily do a total disk rebuild (yes, time, but... ).  

The only thing I can do now is ask questions.  I'll reach a point where /mnt/data exists and has permissions, is in fstab, is mounted.  Then to symbolic links...  All my personal data is in a folder called "Everything".  I've been carrying it since before my start with Ubuntu  at 6.04.  It came out of an old-at-the-time Win. 98 machine that was dying due to age and Windows OS evolution.  Was created and backed-up due to fears of hardware failure and/or OS failure.  Anyhow, it seems like I ought to unwind the "Everything" folder into its constituent parts... Pictures, Documents, etc., for the /mnt/data machine format... that that is what I will find in every Linux distribution and should not argue the system.  I feel like I wouldn't really need to... just put "Everything" into 16.04 /mnt/data and symlink it to "Everything" in 16.04 /home, then the same for the next distribution.  That sounds simple, but I don't have view on what kinds of complications might arise from that approach, nor do I have a view of what complications might arise from the next, then next. Linux distributions.  If I could borrow your view for some gentle use, I'd appreciate having it.  

Mike

---

### Post by Mike Krall on 2017-04-11
> **oldfred said:**
> I occasionally still use gksudo gedit, but now suggest sudo nano.

Nano will run when you have gui issues if you can still boot to terminal so worthwhile to know nano. It is part of every standard install as far as I know.

To manually mount.
 sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod [COLOR="#0000FF"]after mounting either manually [/COLOR]or via fstab
sudo chown $USER:$USER /mnt/data
#sudo chmod 775 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
#Edit fstab with your UUID:
sudo blkid -o list
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab 

Be sure to unmount if manually mounted first, and run this to be sure edit is valid. If it just returns with no errors then the edit of fstab is ok & it remounted everything.

typical entry with my UUID:
      
 UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext4         auto,users,rw,relatime               0  2 

#Verify entry is ok, if no errors it is:
sudo mount -a


Does this constitute 'mounting manually'...  "sudo mount /dev/sda4 /mnt/data" ?  (my /mnt/data is /dev/sda4)...

Mike

---

### Post by yancek on 2017-04-11
> Does this constitute 'mounting manually'...  "sudo mount /dev/sda4 /mnt/data" ?  (my /mnt/data is /dev/sda4)...

Yes, that should work if you've created the data directory in /mnt and it is on a standard filesystem type which is recognized.  You could add the filesystem type to be certain, if it is an ext4 filessytem, just add: -t ext4 anter mount but that should not be needed.

---

### Post by oldfred on 2017-04-11
I am constantly reorganizing data. 
Under Windows I did have different folders. Then a shared data partition with just photos, Firefox profile & Thunderbird profile & some misc. That NTFS partition was then just mounted in /home.
Then I learned about linking and created a Linux data partition. I moved what little data I had in the default folders into /mnt/data. (It originally was in a lot of different places before I settled on /mnt/data which seems more common).

I rarely manually mount data partition as one of the first things I do is add it into /etc/fstab, so auto mounted.

With Linux, I prefer to only backup my data, settings & list of installed apps. No need to backup system as that is on install disk or then I can do a new version install and just restore my data, settings & apps. I use rsync and DVDs for backup. Some prefer rdiff which for several years I thought about using.
       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]https://help.ubuntu.com/community/CategoryBackupRecovery
[/URL]
 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) 

[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]
[/URL]

---

### Post by Mike Krall on 2017-04-11
> **yancek said:**
> Yes, that should work if you've created the data directory in /mnt and it is on a standard filesystem type which is recognized.  You could add the filesystem type to be certain, if it is an ext4 filessytem, just add: [COLOR="#0000FF"]-t ext4 anter mount[/COLOR] but that should not be needed.

Thank you, yancek...

Is the blued the code to add?  With space after,  "sudo mount /dev/sda4 /mnt/data"  ? 

Mike

Edit:  Oh, I see it now. You said, "just add: -t ext4 *after* mount...  Like this:  "sudo mount -t ext4 /dev/sda4 /mnt/data" ???

---

### Post by Mike Krall on 2017-04-12
> **Mike Krall said:**
> ...All my personal data is in a folder called "Everything" in /home.  I've been carrying it since before my start with Ubuntu  at 6.04.  It came out of an old-at-the-time Win. 98 machine that was dying due to age and Windows OS evolution.  Was created and backed-up due to fears of hardware failure and/or OS failure.  Anyhow, it seems like I ought to unwind the "Everything" folder into its constituent parts... Pictures, Documents, etc., for the /mnt/data machine format... that that is what I will find in every Linux distribution and should not argue the system.  Though I feel like I wouldn't really need to.  That I could just put "Everything" into 16.04 /mnt/data and symlink it to "Everything" in 16.04 /home, then the same for the next distribution.  That sounds simple, but I don't have view on what kinds of complications might arise from that approach, nor do I have a view of what complications might arise from the next, then next. Linux distributions.  If I could borrow your view for some gentle use, I'd appreciate having it.

I'm wondering if I can get some input on the above section of a previous post (#75).  

Another thought on using "Everything" was I should re-name folders inside to Ubuntu standard... like Documents, not MyDocuments... which I did originally so there were not two folders with the same name.  It seems, if I were to use "Everything", with deleting Documents, etc. from /home, recreating them inside "Everything" (same name as deleted) might somehow satisfy any Ubuntu "need" to find Documents somewhere.  

In the end, it's probably better for me to simply follow convention... as in, if I do a thing that isn't just right, I could show what I had done and those using the convention would most likely see differences readily... not have to figure out my methods and then figure what's wrong... right? 

Anyhow, it's gone late... and I think I caught my tail...

Mike

---

### Post by Mike Krall on 2017-04-12
Well, maybe not *that* late...

In this command for creating permissions on /mnt/data... "sudo chown $USER:$USER /mnt/data"  I had thought $USER was the 'user name' I installed with (the name in terminal prior to the @ sign)... so my instinct was to use that name twice and without the $ sign.  Looking at a folder and it's permissions, there is Owner - Group - Others.  Now I'm wondering if the first $USER is Owner (name) and the second $USER is Group (my user name)? 

Mike

---

### Post by Dennis N on 2017-04-12
$USER is a variable set to the current user's user name. You can find the value of $USER in the terminal:

for me:
```
[05:32 dmn ~]$ echo $USER
dmn

```

replace $USER by the result in both instances in the command in question. For me, the owner of the folder will become dmn, and the group owning the folder will also become dmn.

Note: Ubuntu creates a group with the user's name for each user when the user is first created.

---

### Post by Mike Krall on 2017-04-12
Dennis N,

Thank you... that helps with both the coding and understanding a little more how the system thinks/links.

Mike

---

### Post by Mike Krall on 2017-04-13
I was able to make time for this tonight.  Used GPartEd to create a 50GB ext4 partition at end of "unallocated", directly in front of swap (swap off).  Messed with sectors to align.  Named and Labeled it (/mnt/data and Data).  After applying, the new /sda4 partition shows 
928.99 MiB used.  I deleted and tried again... same thing. Deleted and tried again moving the 50GB away from swap by over the amount of "used"... yeah I know, GParted wouldn't let me overlap if I tried.  Same thing.  Deleted.

I know I should have done this via a Live USB, but didn't.  I then ran on the Live USB and tried again.  Swap off.  No Label or name.  Same 928.99 MiB in the "used column. Deleted. (All along here I "refreshed device" in GPartEd at every change).  Tried moving the partition to the front of the unallocated space... same thing. Deleted.  Refreshed.  Tried again at end of unallocated space, formatted it to ext4 (had not done that in any prior try's)... same thing. Deleted it. 

I was going to assume a couple of things here and then thought, "Based on what experiential data base and understanding?", and figured I best let it go. I don't understand how a partition can be created out of nothing and have something in it... maybe you will.

Mike

---

### Post by Dennis N on 2017-04-13
> I don't understand how a partition can be created out of nothing and have something in it... maybe you will.

ext4 is a format that uses journaling. The journal is kept on the file system, and _the initial used space you see is created for the journal_. The amount reserved depends on the size of the partition. 

See:

[http://www.linfo.org/journaling_filesystem.html](http://www.linfo.org/journaling_filesystem.html)

---

### Post by oldfred on 2017-04-13
Do not mess with the default sector alignment. All new  partitioning tools will do it correctly. 
A few that have tried to change those settings have gotten into major issues with partitions.

With newer gpt partitions and if not editing mounted partitions you may be able to use gparted from your install. But much better safer to use gparted from live installer. I always use flash drive or my other drive. Every drive has an install, and I can boot that to edit main working drive. But /mnt/data is on my second drive, so I usually use live installer.

In addition to journal, is the issue of MiB vs MB. Not all tools are consistent with how they report sizes.

---

### Post by Mike Krall on 2017-04-13
Thank you 'Dennis N'...

Thank you 'oldfred'...

I have no idea why I did not use install USB initially... I know it is sounder.  

I don't believe I messed with default sector alignment.  I made sure the partition started at an MiB that was divisible by 8 = whole number.  GPartEd arranged both the exact size and end point in sectors in relation to the existing swap partition. 

I looked into journaling file systems and have a rough understanding... 
[https://en.wikipedia.org/wiki/Journaling_file_system]("https://en.wikipedia.org/wiki/Journaling_file_system")
[http://www.linfo.org/journaling_filesystem.html]("http://www.linfo.org/journaling_filesystem.html")  

I am unable to make a connection between GParted GUI running in MiB in all instances (it appears to run in sectors behind the GUI) and MiB / MB discrepancies... don't need to, do I...  

Mike

---

### Post by Mike Krall on 2017-04-13
> **oldfred said:**
> I occasionally still use gksudo gedit, but now suggest sudo nano.

Nano will run when you have gui issues if you can still boot to terminal so worthwhile to know nano. It is part of every standard install as far as I know.

To manually mount.
 sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
[COLOR="#0000FF"]# so chown & chmod after mounting either manually or via fstab[/COLOR]
sudo chown $USER:$USER /mnt/data
#sudo chmod 775 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
[COLOR="#FF0000"]#Edit fstab with your UUID:[/COLOR]
sudo blkid -o list
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab 

Be sure to unmount if manually mounted first, and run this to be sure edit is valid. If it just returns with no errors then the edit of fstab is ok & it remounted everything.

typical entry with my UUID:
      [COLOR="#008000"]
 UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext4         auto,users,rw,relatime               0  2 [/COLOR]

#Verify entry is ok, if no errors it is:
sudo mount -a

I have to make sure I understand this. 

(Considering I need to check -thru GPartEd- to see if partition for /mnt/data is mounted or not (make unmounted), in a couple of places.)

The way I read the blued line is as two choices... 1. mount manually (code in posts #76, #77, #79), then on to permissions (chown & chmod)... *Or*... 2. process mount thru /etc/fstab.  To follow #2... It looks to me that I go to the red line and follow on from there... Three code lines:  Get UUID: of /mnt/data partition... Backup existing /etc/fstab... Edit /etc/fstab (I would use existing wording for comment line with my /sda, and add my /sda UUID: to green line and place it below comment line), then save, then close.  Would then goto /etc/fstab and verify.  If correct, run command "sudo mount -a. 

Finding 'no errors' on "sudo mount -a"... then go on to chown-code line (Enter), then on to chmod-code line (Enter).

Am I a person clear, or unclear on the concept?

Oh, are there needed 'reboot' points in the above process?

Mike

PS...  I can't help but ask...  *if* I were to follow step #1. in blue line... I would edit /etc/fstab (identically) after running permissions-codes?  Edit as 'oldfred' shows (red line on) , making sure to unmount prior to "sudo mount -a" ?

---

### Post by oldfred on 2017-04-13
It has to be mounted one way or the other, manual or fstab, but not both as that creates conflicts. 
No reboot required. But if fstab edited without error, then on a reboot it should auto mount.

I find I accidentally used sudo or downloaded something into /home (really /mnt/data) and ownership or permissions are not correct.
So I to re-run my settings for chown and chmod. Easier than trying to reset several files.

---

### Post by Mike Krall on 2017-04-14
Now looks like:

Number     Size     File system                Name                           Flags
 sda1      523MB     fat32                  ESP System Partition    boot, esp
 sda2      25.0GB    ext4                   16.04 LTS
 .........177GB                               Unallocated
 sda4      50.0GB     ext4                  Data Partition
 sda3      3.0GB    linux-swap(v1) Swap

You did it 'oldfred'... and Dennis N... and... and... and...  =]

I did 'oldfred's' "via fstab"... check, check, double check, check... and don't touch *anything* that doesn't *need* to be touched...  =]  

What specific code do you prefer for creating symbolic links (I've seen ...I think... a couple, maybe three, slightly different ones).  I know I have links to process and some on theory... I would take more if a person had them...  and/or other advice's.  

Mike

---

### Post by Mike Krall on 2017-04-14
> **oldfred said:**
> It has to be mounted one way or the other, manual or fstab, but not both as that creates conflicts. 
No reboot required. But if fstab edited without error, then on a reboot it should auto mount.

I find I accidentally used sudo or downloaded something into /home (really /mnt/data) and ownership or permissions are not correct.
So I to re-run my settings for chown and chmod. Easier than trying to reset several files.

Thank you for this post, 'oldfred'...  I've got copies stashed in several places (hard copy, even) of 'all', but especially the second paragraph.  

And it did auto mount on reboot... 

And I found the fstab backup, too... right there next to fstab in /etc. 

Mike

---

### Post by Mike Krall on 2017-04-16
> **Mike Krall said:**
> I'll reach a point where /mnt/data exists and has permissions, is in fstab, is mounted.  Then to symbolic links...  All my personal data is in a folder called "Everything".  I've been carrying it since before my start with Ubuntu  at 6.04.  It came out of an old-at-the-time Win. 98 machine that was dying due to age and Windows OS evolution.  Was created and backed-up due to fears of hardware failure and/or OS failure.  Anyhow, it seems like I ought to unwind the "Everything" folder into its constituent parts... Pictures, Documents, etc., for the /mnt/data machine format... that that is what I will find in every Linux distribution and should not argue the system.  I feel like I wouldn't really need to... just put "Everything" into 16.04 /mnt/data and symlink it to "Everything" in 16.04 /home, then the same for the next distribution.  That sounds simple, but I don't have view on what kinds of complications might arise from that approach, nor do I have a view of what complications might arise from the next, then next. Linux distributions.  If I could borrow your view for some gentle use, I'd appreciate having it.

The quote is part of a post I made a few pages back.  I've been thinking about this again... either of

* make /mnt/data look like un-hidden files typical of /home (Desktop, Documents, Downloads, etc.) with added hidden-types like .thunderbird, .mozilla., .googleearth, etc.  

OR...

* create "Everything" in /mnt/data and add necessary hidden-types (in /mnt/data, not in "Everything").  Some things that look positive about that (given I really don't know how Linux file systems work, etc.).  Less items in /data.  A differentiation between un-hidden and hidden parts of /home linked with /mnt/data.  Fewer steps creating links in /mnt/data for this and other Linux distributions.  I've been working with "Everything" for over ten years... not that dealing with the various places differently is any kind of a large change... it's not.  

I understand everyone has their "ways.  I'm looking for technical advice... are there problems you see with using "Everything"?  And, with "Everything, would a person be best off having folders within be named as they are typically named in Linux?

Mike

---

### Post by oldfred on 2017-04-16
I create all my links in one step, normally do this first thing with new install, so I know default folders are empty and I delete them in my script.
And I already have all my folders in /mnt/data. Do not remember how or when I copied all the data to that years ago.

Then I have a small script copied from my history that does several set up thing in a new install, one is linking.
 #Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

---

### Post by Mike Krall on 2017-04-17
Linux Mint How-to:  Create and Use a Separate Data Partition
[https://community.linuxmint.com/tutorial/view/1609]("https://community.linuxmint.com/tutorial/view/1609")

Seems they are making all folders at same time in /mnt/data via opening terminal in /mnt/data and entering... "mkdir Documents Downloads Music Pictures Videos", etc.  I don't know if I'm reading that right...  is correct?

If it is, I would add .thunderbird to the list as well as the other un-hidden /home folders, whether I ever use them or not... under the idea they won't take any room and will be there if wanted.    

Also wondering if I need to move .mozilla to /mnt/data and link.  I dumped FireFox out of this machine and put Chromium in.  I'm wondering if there is stuff in .mozilla that needs to be with .thunderbird?  I don't know how to tell.  And I expected to find a .chromium in /home hidden folders but do not.  Are there Chromium things in /home hidden folders that ought to be in /mnt/data like would be if I still had FireFox? 

I'd like to have the same Desktop on all distros... I use my desktop like a board for stickies, along with other current and old business that needs minded (remembered).  I thought I would "mkdir Desktop" in /mnt/data, but I don't know if I will get what I want that way... would you say, please?

Mike

Edit:  I should say... the two places in /home I find Chromium is  */home/user/.config* and  */home/user/.cache*

---

### Post by oldfred on 2017-04-17
I think the first time I created /mnt/data I already had lots of data in various folders. So I just copied all that data from /home into /mnt/data.

I do copy Firefox & Thunderbird but do not link. Or with my script remove link after the fact.
I have the edited profile in my /mnt/data/Thunderbird and copy that back into /home/.thunderbird/profiles.ini replacing the default one. I do have to start it once to create the .thunderbird.

I have never edited or used Desktop. And have not used Chromium enough to know or move it.

---

### Post by Mike Krall on 2017-04-19
> **oldfred said:**
> I think the first time I created /mnt/data I already had lots of data in various folders. So I just copied all that data from /home into /mnt/data.

[COLOR="#0000FF"]I do copy Firefox & Thunderbird but do not link. [/COLOR]Or with my script remove link after the fact.
I have the edited profile in my /mnt/data/Thunderbird and copy that back into /home/.thunderbird/profiles.ini replacing the default one. I do have to start it once to create the .thunderbird.

I have never edited or used Desktop. And have not used Chromium enough to know or move it.

Why?

Mike

---

### Post by oldfred on 2017-04-19
The profile.ini just has the correct path.
In my /mnt/data I created a /mozilla folder for both Firefox & Thunderbird.

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=[COLOR=#ff0000]/mnt/data[/COLOR]/mozilla/firefox/wojjex8t.default
```

---

### Post by Mike Krall on 2017-04-21
I got two balls in the air... then dropped one... but I got it picked back up again...  =]  

This is related to 'oldfred' last post... #97.  

I'm trying to understand the simple bits of this system (/mnt/data).  Looking at code is awareness, but it is not function unless I can at least sort of see what it says.  Searching, reading, cross-searching, cross-reading. I've got a little collection of various words connected to code that is related to some degree to /mnt/data.... Thunderbird, Chromium, and, of all things, Trash (trash)... and then 'trash' related to Desktop.  I know I can CLI a Desktop into /mnt/data... that the partition /mnt/data is in (or is it *'is'*?) /dev/sda4 and /dev/sda4 belongs to 'user'. And I know I can CLI a symbolic link in /home/user pointing to Desktop in /mnt/data.  

I messed with rt. clk. > 'copy to' tonight. Populated an empty Desktop with a file, a directory (with a file), a picture.  Then...  Nautilus > Desktop > 'copy to' > step, step, step > /data > select.  Goto /mnt/data > /data and there is Desktop.  Open and there is a file, a directory (and a file), a picture.  So, I "move to trash' the file in the directory, the directory, the other file, the picture, then the Desktop directory.  From the start... do it again.  Now there is a .Trash-1000 directory in /data along with Desktop (and the ever present 'lost+found' directory).  Desktop has all it's bits and so does .Trash-1000.  Hmm... that don't work.  Permission on .Trash-1000 is "Me" only... not user, etc.  Won't let goto 'trash' with .Trash-1000, but, a kindly thought by Ubuntu code-ers allows as how I can delete it directly. 

An epiphany...  I create new Desktop in /mnt/data...  .Trash-1000 pops back in.  Is 'owner and 'user' permissioned.  Mess with making and trashing in /mnt/data/Desktop, then looking-at, then emptying trash on /home/user/Desktop, filing it up again from /mnt/data Desktop, repeat.  Rename /mnt/data Desktop (Desktop-2)... rt. clk. > 'make link' > select. There's the Desktop-2 link in Desktop-2...   rt. clk. > 'move to' > /home > select...  clk. Desktop-2 link in /home and I'm in Desktop-2.  Add stuff to Desktop-2 > /home/user/, clk. Desktop and it's different than Desktop-2.  Clk. 'Desktop-2' link and I'm in 'Desktop-2'... property of /mnt/data and so are all it's pieces and pieces in pieces.  Is that recursive GUI? 

Anyhow... I'm working on Thunderbird (and Chromium) along the 'oldfred' "move to /mnt/data but don't link" line of thought.  I've got some links and some hints about how to do it like 'oldfred's' Thunderbird post above.  I want to do all this CLI and that's going to take me building a picture (an understanding) of the code (what it is saying) and that is going to take me a bit.  

Mike

---

### Post by oldfred on 2017-04-21
This is oldfred's scripts to configure a new install.
Most copied from bash history & edited/fixed over time.
The are unique to my configuration, but if trying to use command lines may show you some things.

 Oldfred's install scripts
[https://ubuntuforums.org/showthread.php?t=2347811&p=13588662#post13588662](https://ubuntuforums.org/showthread.php?t=2347811&p=13588662#post13588662)

---

### Post by Mike Krall on 2017-04-21
Glad to have 'oldfred's' install scripts.  

Because I've got "the old ASUS", I'm running the new one empty... a very few added things, no personal data, 16.04 with nothing in /mnt/data or in un-hidden /home.  I feel having close to zero complexity is a lot safer place for me to be.  

If I understand correctly ( ??? ), I could populate /mnt/data and create symbolic links and still have a "simple" world (deal with the Thunderbird, Chromium, etc. stuff later), but it seems to me having clear view on the possibly more problematic (at least confusing) things first, will help in the long run. 

Thanks for the help, 'oldfred'...

Mike

---

### Post by Mike Krall on 2017-04-25
Is this command correct (copy .thunderbird to /mnt/data)?

"cp /home/$USER/.thunderbird /mnt/data" 

Mike

---

### Post by oldfred on 2017-04-25
If you want to keep it hidden.

I do not keep it hidden in my /mnt/data. Since you edit profile, you can edit profile to be anyplace you want.

For backup purposes I copied both Firefox & Thunderbird to a Mozilla folder and the had Firefox & Thunderbird folders inside that.
From my backup script, so does not have sudo.
rsync -aruvlP --exclude-from=mybackup_excludes.lst /mnt/data/mozilla /mnt/backup

I have similar commands to my 32GB flash & 64GB flash data drives.
And I manually add to my DVD occasional backups.

---

### Post by Mike Krall on 2017-04-26
Is this command correct (would there be a better way)... to copy Thunderbird  to  /mnt/data?

"cd -R /home/$USER/.thunderbird /mnt/data"

Mike

---

### Post by Dennis N on 2017-04-26
> **Mike Krall said:**
> Is this command correct (would there be a better way)... to copy Thunderbird  to  /mnt/data?

"cd -R /home/$USER/.thunderbird /mnt/data"

Mike

The command **cd** should be **cp**.

---

### Post by oldfred on 2017-04-26
While rsync is intended primarily for network copies, I often use it locally also.

I have in my notes:
 Note: cp without -a means root takes ownership which would be a big issue 

You want to use similar command as any  copy of /home as here as you are copying folders from /home.

 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I am pretty sure I posted this before, but occasionally I have to re-run this on my data partition as I copied something incorrectly:

 sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod after mounting either manually or via fstab
sudo chown $USER:$USER /mnt/data
# The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data

---

### Post by Mike Krall on 2017-04-26
> **Dennis N said:**
> The command **cd** should be **cp**.

No excuses.  Thank you pointing out the error.

Mike

---

### Post by Mike Krall on 2017-04-26
> **oldfred said:**
> While rsync is intended primarily for network copies, I often use it locally also.

I have in my notes:
 Note: cp without -a means root takes ownership which would be a big issue 

You want to use similar command as any  copy of /home as here as you are copying folders from /home.

 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I am pretty sure I posted this before, but occasionally I have to re-run this on my data partition as I copied something incorrectly:

 sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod after mounting either manually or via fstab
sudo chown $USER:$USER /mnt/data
# The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data

You did post the permissions section before.  I was looking at it last night.  I woke up this morning with "No, 'cp -R, etc.' is not right... leaving stuff out".  I spent a while looking at permissions in original locations.  Using 'copy to' carries original permissions.  I haven't tested much, but creating folder in /mnt/data gives /mnt/data partitions to (in this case) .thunderbird... still 'copy to' of pieces passes original-location permissions. 

I know I need to read before I yap... but...   

To see if I understand first three paragraphs...  command would be "cp -R -a /home/$USER/.thunderbird /mnt/data/.thunderbird  to keep original-location permissions (not give permissions to root)? 

An after thought...  With .thunderbird, in this specific application... the permissions would ideally be the same in /mnt/data as they are in original-location?  

Mike

---

### Post by oldfred on 2017-04-26
Best to test.
Make good backups and experiment. 
That was essentially how I learned. And lots of searches for more info as I started to learn.

---

### Post by Mike Krall on 2017-04-30
> **oldfred said:**
> [COLOR="#0000FF"]I think the first time I created /mnt/data I already had lots of data in various folders. So I just copied all that data from /home into /mnt/data.[/COLOR]

I do copy Firefox & Thunderbird but do not link. Or with my script remove link after the fact.
I have the edited profile in my /mnt/data/Thunderbird and copy that back into /home/.thunderbird/profiles.ini replacing the default one. I do have to start it once to create the .thunderbird.

I have never edited or used Desktop. And have not used Chromium enough to know or move it.

I've come onto a number of different ways to have Documents, etc. in /mnt/data... Because mine in /home are all empty, I can rt.clk. > 'move to'... or 'copy to'... or "mkdir Documents" from terminal if I "cd /mnt/data" first... or... in /mnt/data, rt.clk. > 'new folder'... or I can use cp or mv code in terminal (various and sundry versions... many seemingly designed to accommodate data and permissions and executions and ???).  

The methods I've tested  (not any cp or mv  types) all create a Documents folder.  Depending on which method, permissions are different... either of:  Standard /home "Owner"_"Me"_ create & delete;  "Group"_user_access files, "Others"_access files... OR...  /mnt/data "Me" and "user"_create & delete, "Other"_access files.  

Does it make a difference?  

I noticed /data in /mnt/data has "Me", "user", "Others"  permissions as 'create & delete' for all.  Is that wrong? 

Mike

---

### Post by oldfred on 2017-04-30
```
-rw-rw-r--  1 fred fred   268190 Jun  8  2016 Screenshot from 2016-06-08 11-10-23.png
-rw-rw-r--  1 fred fred   259320 Jun  8  2016 Screenshot from 2016-06-08 11-10-55.png
-rw-rw-r--  1 fred fred   100246 Oct 27  2016 short_workout.jpg
drwxrwxr-x  2 fred fred     4096 Apr 28  2016 spreadsheets

```

Directories have the d as first parameter. If not executable then -rw-rw-r-- is correct.  If executeable the x is added.
-rwxrwxr-x 1 fred fred    125 Dec 18  2014 trimSSD.sh

---

### Post by Mike Krall on 2017-04-30
Thank you...

What command did you use to generate the Code: in Post #110?  I found "ls -l" but it doesn't return as 'oldfred' returns.

MIke

Edit:  Never mind the question... I found this:  [https://www.divms.uiowa.edu/clas_linux/help/start/permissions.html]("https://www.divms.uiowa.edu/clas_linux/help/start/permissions.html")

---

### Post by oldfred on 2017-04-30
I used ls -l

fred@Z170N:~$ cd /mnt/data
fred@Z170N:/mnt/data$ ls -l
Showed all my folders only 2 copied
drwxrwxr-x 21 fred fred  4096 Apr 27 12:44 Documents
drwxrwxr-x  7 fred fred  4096 Apr 29 15:24 Downloads
fred@Z170N:/mnt/data$ cd Documents
fred@Z170N:/mnt/data/Documents$ ls -l

All my files in Documents were shown.

---

### Post by Mike Krall on 2017-05-01
I cross posted...  see edit w/ link my last.  

After looking at 'oldfred' ls -l  I'm glad I didn't get him stopped.  

waldo@11:~$ cd /mnt/data
waldo@11:/mnt/data$ ls -l
total 20
drwxrwxr-x 4 waldo waldo  4096 Apr 20 23:18 Desktop-2
drwxrwxrwx 2 root  root  16384 Apr 13 20:28 lost+found

OR...

waldo@11:~$ cd /mnt/data 
waldo@11:~$ ls -al
total 36
drwxrwxrwx 6 waldo waldo  4096 Apr 30 12:14 .
drwxr-xr-x 3 root  root   4096 Apr 13 20:52 ..
drwxrwxr-x 4 waldo waldo  4096 Apr 20 23:18 Desktop-2
drwxrwxrwx 2 root  root  16384 Apr 13 20:28 lost+found
drwxrwxr-x 3 waldo waldo  4096 Apr 26 10:59 .thunderbird
drwxrwxr-x 5 waldo waldo  4096 Apr 20 22:05 .Trash-1000

And I'm intending to change from .form directories in final /mnt/data...

Mike

---

### Post by Mike Krall on 2017-05-06
I've been going around with Chromium.  Don't know if I understand yet but think so.  I've finally figured out I need to ask a little more about Thunderbird but I'm not at a point of asking well, so holding off.  And spring has hit, fixing 440 acres of fence, dealing with 20 head of horses, and other spring "emergencies".  I can't do more than this, right now.

Mike

---

### Post by Mike Krall on 2017-05-16
*A person doesn't get time and a person doesn't have time... a person makes time. *

Thunderbird... I think I understand and need to find out from someone who does if I'm right.

A person doesn't link .default and profiles.ini to /mnt/data from /home/.thunderbird because the edited profiles.ini is the link.  

I had to make a drawing of it... TB in 16.04, it's .default (profile 0) and profiles.ini... .default and profiles.ini in /mnt/data... then another TB and .default and profiles.ini in different Linux distribution.... with little lines and arrows...  =] 

So, the way I have it is TB starts, looks for profiles.ini, profiles.ini points to .default.  The profiles.ini in /home points to .default in /mnt/data (for any number of TB in other distros) and TB functions as setup.  The .default in /mnt/data is accessible to all distros.  The profiles.ini in /mnt/data is accessible to all distros... so a person can put in another distro and copy /mnt/data profiles.ini to the other distro's /home profiles.ini.

Why isn't the distro's /home .default deleted?  It doesn't seem to do anything.  The only thought I had was if a person needed/wanted to copy a distro ( / partition ) it would be there... as opposed to not.  A reason to not delete I guess... but...  Am I missing something?  

Mike

---

### Post by oldfred on 2017-05-17
I copy profile.ini from my copy in /mnt/data.
I always delete the default profile & profile.ini that gets created when first starting both Thunderbird & Firefox, once I know they are working with my profile.

---

### Post by Mike Krall on 2017-05-18
Ah,  I see it now.  Thank you oldfred.
--------------------------------------------------------------

Chromium...

I can't tell you how many search terms I've run looking for Chromium in /mnt/data... how it's dealt with. I would bet a nickle on no one using Chromium and /mnt/data ever having written about it, but then, as I have said, I'm a terrible searcher. 

I gave up after a while and started searching for information about Chromium... pointed mostly towards profiles, moving them, but also generally .  I've collected 13 links (*way* less than the links read) and I've got 4 Google searches for various and sundry pieces of Chromium... different view points, really. 

These were helpful for basic understanding:  
[https://www.chromium.org/user-experience/user-data-directory]("https://www.chromium.org/user-experience/user-data-directory")
[http://www.chromium.org/developers/creating-and-using-profiles]("http://www.chromium.org/developers/creating-and-using-profiles")
[http://www.chromium.org/user-experience/multi-profiles]("http://www.chromium.org/user-experience/multi-profiles")

There are a number of other links with bits and pieces of Chromium views that might pertain to Chromium and /mnt/data (I'm not asking anyone to look at any of these):
See last post... How to import Chromium-Browser data to Chrome...
[https://askubuntu.com/questions/89567/how-to-import-chromium-browser-data-to-chrome]("https://askubuntu.com/questions/89567/how-to-import-chromium-browser-data-to-chrome")
How do I modify Chromium's default data directory...
[https://superuser.com/questions/546743/how-do-i-modify-chromiums-default-data-directory]("https://superuser.com/questions/546743/how-do-i-modify-chromiums-default-data-directory")
4 ways to backup and restore Google Chrome's entire settings...
[http://www.wikihow.com/Backup-and-Restore-Google-Chrome%27s-Entire-Settings]("http://www.wikihow.com/Backup-and-Restore-Google-Chrome%27s-Entire-Settings")
How do I move/create Chrome profile elsewhere?...
[https://productforums.google.com/forum/#!msg/chrome/9bqidhQLwHg/8Sm4OJirwYEJ]("https://productforums.google.com/forum/#!msg/chrome/9bqidhQLwHg/8Sm4OJirwYEJ")
Change the Google Drive default folder...
[http://gappstips.com/google-drive/change-the-google-drive-default-folder/]("http://gappstips.com/google-drive/change-the-google-drive-default-folder/")
Easier way to move the location of Google Chrome cache & user files...
[https://www.neowin.net/forum/topic/1044311-easier-way-to-move-the-location-of-google-chrome-cache-user-profile/]("https://www.neowin.net/forum/topic/1044311-easier-way-to-move-the-location-of-google-chrome-cache-user-profile/")
Running Chromium in separate instances...
[http://www.gate2.net/TnT/ChrmSecure.html]("http://www.gate2.net/TnT/ChrmSecure.html")

And this...

*"Note: Some browsers such as Chrome/Chromium, Firefox (since v21) and Midori actually keep their cache directories separately from their profile directory. It is not within the scope of profile-sync-daemon to modify this behavior; users are encouraged to refer to the Chromium tweaks#Cache in tmpfs section for Chromium and to the Firefox on RAM article for several workarounds. An easy fix is to move the various browsers' cache directory from their default location (e.g. /home/$USER/.cache/<browser>/<profile>/) to the corresponding profile directory, e.g. /home/$USER/.mozilla/firefox/<profile>/cache, and then symlink the new cache folder back to its original location. This way, profile-sync-daemon will automatically take into account the cache folder too."*
From this link.. See second "Note:"
[https://wiki.archlinux.org/index.php/profile-sync-daemon]("https://wiki.archlinux.org/index.php/profile-sync-daemon")

And... From Chromium Projects: Common Problems and Solutions... which I just found tonight while writing this...
[https://www.chromium.org/administrators/common-problems-and-solutions]("https://www.chromium.org/administrators/common-problems-and-solutions") 

[I]"Can I store my users' Chrome profiles on a Roaming Profile?  Or sync it to a network drive?"

"Chrome user profiles are not backwards-compatible.  If you try to use mismatched profiles and Chrome versions, you may experience crashes or data loss.  This mismatch can often occur if a Chrome profile is synced to a roaming profile or network drive across multiple machines that have different versions of Chrome.  We strongly encourage admins & users to consider using Google Chrome Sync, which persists user settings across machines, instead of using roaming profiles for the time being.

That said, there are policies for controlling the location of the user profile and the cache:"
[http://dev.chromium.org/administrators/policy-list-3#UserDataDir]("http://dev.chromium.org/administrators/policy-list-3#UserDataDir")
[http://dev.chromium.org/administrators/policy-list-3#DiskCacheDir]("http://dev.chromium.org/administrators/policy-list-3#DiskCacheDir")[/I]

It seems like, from the lack of information on Chromium and /mnt/data, plus the Chromium Projects information above and the fact other Debian Linux distros *do* have different Chromium versions, don't update them, or do update them but on an 'as choose' basis, my best guess for Chromium with /mnt/data is try using Google Chrome (Chromium) Sync instead... and hope...  =]

I did look at the links in the Chromium Projects question/solution.  I don't understand well enough to do anything with it... maybe I will later... especially if I have to understand/do it later. 

Does any of the 'conclusion' part of this seem right-ish... or ???

Mike

---

### Post by oldfred on 2017-05-18
I have never moved Chromium folders. But I only recently started using Chromium.

With Firefox I think used same profile in XP & Ubuntu from 6.06 till now. Perhaps changed when I installed 9.10 as 64 bit.
I do know that between XP on desktop & laptop & Ubuntu on desktop and later Ubuntu on laptop were often different versions of Firefox. 
Only relatively recently did Ubuntu start updating to latest Firefox as standard procedure in updates.

---

### Post by Mike Krall on 2017-05-19
I've reread the Chromium Projects info from post #117 and looked around more along the lines of profiles mismatching versions.  I thought at first I confused the link/info with one actually for Chromium OS.  Now, I don't think so. Seems consistent at Chromium Projects that browser is called Chromium and OS called Chromium OS.  Any way, it would be very easy for me to be confused about things... that's a thing I Do know.  I didn't find anything corroborating profiles mismatching versions problems.

It seems the specific point of Google Chrome (Chromium) Sync is to have the same browser set up on different devices.  Yet, I don't see how the cache can be involved.  Then symlinking ~/.config/chromium/default and ~/.cache/chromium into /mnt/data so all distros have the same of both.  There are a couple of inferences in the links of post #117 that the folder should be moved or copied and not just the contents copied, but the discussion is not about separate data partitions. As near as I can tell, there is nothing in Chromium like TB's profiles.ini... a thing looked for and used specifically to point to profiles (default, or 1, or etc.), so standard symlinking should do.

One last... If there is a profile version mismatch problem, a person might use Chromium Sync with a symlinked /cache/chromium folder in /mnt/data.  I guess I'm going to be doing more reading...

Mike

---

### Post by Mike Krall on 2017-05-19
> **oldfred said:**
> I copy profile.ini from my copy in /mnt/data.
I always delete the default profile & profile.ini that gets created when first starting both Thunderbird & Firefox, once I know they are working with my profile.

Two things:

* Do you delete ~/.thunderbird/Crash Reports, or /mnt/data/Thunderbird/Crash Reports, or ???

* Is this correct for edited ~/.thunderbird/inu34g98.default? 

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/mnt/data/Thunderbird/inu34g98.default
Default=1

Mike

---

### Post by oldfred on 2017-05-19
this is mine, but I put both Thunderbird & Firefox in a mozilla folder since they were related. There was discussion by Firefox of separating Thunderbird, but for now still related.

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/mnt/data/mozilla/thunderbird/lyu25irb.default
Default=1
```

Off topic
I have not had to repair Fences for over 20 years. Normally our tenant took care of it. Dad nor I farmed the farm. When a kid grampa had steers and most neighbors did also, so everyone maintained fences. But then farms all became corn & soybeans and most fences came out. 
Neighbor had Belgians (big work horses like like Budweiser's Clydesdales). When in high school (1960s)I laughed at him as he still used horses. Grampa sold our horses when I was 3 and we only used tractors.
But right up to when we sold farm we had to maintain fences with that neighbor.
He also did demonstration plowing with the horses at the history farm nearby. But had converted to using a tractor for normal plowing as he said plowing was hard work for horses.

---

### Post by Mike Krall on 2017-05-20
Thank you...

I can't imagine reinstalling FireFox.  I've been 'other browser-ing' (Chromium mostly) for 10 years now.  

I've still got to look into Chromium more... the potential profile/version conflicts I mentioned/imagined... I'll make some time.

Off topic:
Every year we wander the fence line prior to the lease horses arriving.  It's patching mostly.  Age (some of it is older than you and me) and the beloved elk is what causes the work.  Elk get along with fences on an adversarial basis.  The snow moves them back and forth through here.  Sooner or later they knock some fence down.  Funny how they sometimes don't remember where a knocked down section is and do it again 50' or 100' up or down the line.  

I've been around work horses a little.  A little haying, and mostly logging... dragging logs, or bundles of them, out to access points.  Nice quiet work with the cutters somewhere else... trace chains clinking...  clip clopping... some gidupping, whoaing, geeing and hawing here and there.  Good logging horses know the job... hooking up and unhooking is what they need people for.  Oh, and for getting the end-of-day oats out, too...  =]

Mike

---

### Post by Mike Krall on 2017-05-23
I got all empty /home (un-hidden) removed (rm -rf ), got all into /mnt/data (cd /mnt/data... mkdir Documents/, etc.), got all symlinks made with 'oldfred' all-in-one-symlink-maker-script... all except Desktop which I was using (had stuff on).   

Well... it looks broke.  It was "rm -rf Desktop" that caused the problem... and "mkdir /mnt/data/Desktop".  I don't know how to explain it, really.  

I think (too late) Desktop is not a simple thing like Documents, or Pictures and a Desktop directory in /mnt/data (mkdir /mnt/data/Desktop) does not suffice for function.  The symlink looked right... Desktop icon with link arrow... but there was no function on the real desktop.  That is, created folder in /mnt/data/Desktop and put a couple of 'oldfred' CLI links in it. They are there, they open, they do not show up on the Desktop.  I can create things on the Desktop and they show up in /mnt/data/Desktop, just not the other way around, which is what I wanted.    

After the fact, I searched Computer for 'Desktop'... lots a stuff touching or being touched by lots of things... Unity, for one.  Whether there is a pointer for Desktop like .thunderbird/profiles.ini I don't know.  Looked at a lot of stuff and didn't see anything l thought might be a pointer or profile kind of thing.

Anyhow... it needs fixed... ran into this old thread:
[https://ubuntuforums.org/showthread.php?t=1716158]("https://ubuntuforums.org/showthread.php?t=1716158")

This is my ~/.config/user-dirs.dirs file:

[COLOR="#0000FF"]# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"[/COLOR]

I tried editing the ~/.config/user-dirs.dirs file. After backing it up I made it look like the example at the end of the linked thread.  Reverted to same after restart.  Depleted all mkdir /mnt/data directories and tried again (all the symlinks were gone prior to first try). Restart... didn't change anything.  Ran code: "*gconftool-2 /apps/nautilus/preferences/desktop_is_home_dir --type bool --set false*" (same post as shows copy of  ~/.config/user-dirs.dirs file and tried again. Restart... reverted to same as shown again.  

I could reinstall.  I'd have a little work to do to come back to where I am now but not like it can't be done.  The partitioning would be there.  I would likely need to edit fstab, maybe reset permissions but I'm guessing not. 

Other ideas?

Mike

---

### Post by oldfred on 2017-05-23
I normally only move my data to /mnt/data, not any configurations.
About the only hidden folders that I have move are the .thunderbird & .firefox.

---

### Post by Mike Krall on 2017-05-24
I could say I 'miscalculated', but that would be more than a little disingenuous.  It's not like I haven't spent a lot of time looking into all files/folders in .thunderbird and .chromium.  I might not have *"rm -rf Desktop"* if it had dawned on me to look at all of what/where Desktop is in 'Computer'. 

Now I've got more reading to do... starting with how come a relatively simple solution doesn't work (edit the file: Ubuntu Forums link from Post #123).  I do know I likely need the OS to make the directories, that it is,  making folders in /home for Documents, Downloads, etc., either "mkdir" or GUI may not work... certainly unlikely to work for Desktop. 

I'll be back... if the process don't kill me first...  

Mike 

PS...  It does look as if the *~/.config/user-dirs.dirs* file should allow Desktop to be in /mnt/data  (available to other distos).

---

### Post by Mike Krall on 2017-05-24
Fixed it.

The link from Post # 123
[https://ubuntuforums.org/showthread.php?t=1716158]("https://ubuntuforums.org/showthread.php?t=1716158")

And this from Ask Ubuntu... last post by Maythux
[https://askubuntu.com/questions/711126/recreate-desktop-directory]("https://askubuntu.com/questions/711126/recreate-desktop-directory")

Making the new Desktop CLI is part of the solution.  GUI making of Desktop in home, even with editing of ~/.config/user-dirs.dirs didn't, but I could have gotten carts in front of horses.  All non-config folders need to be gone in both /home and /mnt/data and not on Desktop either and then restart. The directories need to exist prior to editing... I did Desktop first, then edited for that only. A restart changes the made Desktop folder in /home to a Desktop icon. Made other non-config directories.  Editing can order directory position in /home... as made (mkdir xxx), the arrangement in /home was random-ish.  A restart lines them all out in original alphabetical order and all folders with their proper type symbols.   

It seems like there are two, maybe three ways to have Desktop in /mnt/data.  Second link and last poster says it should work as with standard /mnt/data non-config files. I tried copying Desktop to /mnt/data, editing ~/.config/user-dirs.dirs to absolute path.  It failed... went right back to non-hidden folders showing up on the desktop... I fixed it again.  It might be moving Desktop to /mnt/data, then editing to absolute path, then restarting would work. 

A question...  do you edit ~/.config/user-dirs.dirs?  What does your ~/.config/user-dirs.dirs look like?  

Mike

---

### Post by oldfred on 2017-05-24
Only once years ago I saw some info on editing ~/.config/user-dirs.dirs. As I remember it did not work or did not do anything for me.

I want all data in a data partition so I can share with my other installs.
But I do not want configuration as other install may be newer, older, or just a test where I want totally different configuration. So I do not include hidden user settings from /home in /mnt/data.
I typically have multiple 25GB / (root) partitions and do not want settings changes in a test to change my main working install.

---

### Post by Mike Krall on 2017-05-25
I asked for help and advice in this thread and I'll take it... thanks 'oldfred'.

I wanted to see your ~/.config/user-dirs.dirs to see what the system had done when you moved and symlinked Documents, etc. 

In the knocking around I did, if I did a restart, ~/.config/user-dirs.dirs self edited.  After all in /mnt/data were gone and all symlinks were gone off the desktop and in /home, I created a Desktop CLI.  It showed as a plain folder icon in /home.  I went to ~/.config/user-dirs.dirs and all the "yyy" were gone.  I edited in Desktop, saved, closed and restarted.  There was a normal Desktop icon in /home.  

Between the time I posted last night and saw 'oldfred' response today, I did try to have Desktop in /mnt/dat via edit to absolute path. That blew up... un-hidden directory on desktop again.  Fixed it again and copied my ~/.config/user-dirs.dirs.backup into original.... and there I will leave it (Desktop)... though I *do* have an ingrained attraction to puzzles. Anyhow, I'll work around the way I use Desktop when I've got other Linuxes and their Desktop's need to be the same. 

Now I have all but Desktop in /mnt/data with symlinks via 'oldfred's' all-in-one-link-making-script... who would have ever thought a thing that looked like that would do what it does...  =]  And a person can make all directories in /mnt/data as one whack with: 
"mkdir Documents Downloads Music Pictures Public Templates Videos"

And because I can't let the Desktop thing go I looked at Desktop with rt. clk.  Any other file/folder in /home has "make link" available... Desktop has "make link" grayed out... curious, huh? The Desktop god... thou shalt not move.

Mike

---

### Post by Mike Krall on 2017-05-25
I've questions;

* Does 'oldfred' have a .Trash-1000 folder in /mnt/data?

* Does 'oldfred' have a lost+found folder in /mnt/data?

* In /home/$USER/.thunderbird there is a Crash Reports folder.  Does it get moved to /mnt/data? If yes, does it get deleted in /home/$USER/.thunderbird. 


Mike

---

### Post by oldfred on 2017-05-25
Yes to both in /mnt/data.
And this is on my newer system created about a year and a half ago.
But /mnt/data was a copy of /mnt/data from flash drive which was a backup of /mnt/data on other system.

I used to use a laptop in FL and Desktop in IL. But found I was now in FL more and laptop's smaller screen and fixed keyboard not as functional. Plus laptop was from 2006 and new desktop in IL had SSD. Big improvement. So new desktop in FL. :)
And I was both copying /mnt/data from desktop to laptop & backing up to flash drives and some data to DVDs.
I realizes it would just be easier to cart flash drive back & forth. And am wanting to set up SSH, but have not gotten around to it as flash drive works for both backup & moving from state to state.

With effectively one /mnt/data on two systems and multiple flash drives I have issues with housekeeping. I need to change my procedures as I have been overwriting flash drive. But files deleted or moved then still are on flash drive and copied to other system, then return when copied back.  Or lots of duplicates get created when trying to reorganize. I need to delete all of a flash drive before copying data to it.

My Thunderbird is probably 10 years old. I have only housecleaned some known older files.

This thread shows files that you do not need to rsync to a backup.
[https://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](https://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

I change this from /home to my locations in /mnt/data.
       /home/lost+found
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/** 

While most of what we have discussed is related to original thread title of triple boot. Some are more detailed on only related issues. Each of those probably should have become a thread. 
You may be better served by asking a separate question on each issue. Since thread is now so long and they see oldfred, others are not contributing. Others also have good ideas, alternatives that can be useful and should be adding their info. So best to start new thread on each new topic.

---

### Post by Mike Krall on 2017-05-27
Thank you for the answers and for the other information, 'oldfred'.  I'm sorry to not have gotten back sooner.  A few days ago my computer started with an over large login and desktop... no mouse... no touchpad.  I've been trying to figure out how to even start a thread on it with my available time... an excuse, not a reason.

I understood (came to understand) a while ago that other folks had either of dropped out or not dropped in.  It's a by product of me and my ways, I feel.  As I started into /mnt/data (reading Lots of links to lots of threads and lots of other threads from lots of other links) I decided I could not learn-then-do all those different "ways"... could not make them mesh.  It was, simply, confusing. I evolved to having best luck understanding by staying with your view of /mnt/data and your methods, then relating all other views and ways to that.  I essentially forced others out of the discussion.  

I will try, as you suggest, to work with related topics through new threads.  My mind is to leave this thread open for now (I may have to come back), or you can close/"solved" it... as you choose, 'oldfred'.

I've cruised all of this thread's pages off and on.  There is a very large amount of /mnt/data info all here in this one place along with a lot of other, necessary, related issues... all most all from you and your links. Really, it's more your thread than mine, anyhow. I wish I had gotten "separate data partition" into the original title... really, that is what all of this is about... How to set up for multiple Linux distros. 

Mike

---

### Post by oldfred on 2017-05-27
You are the one that has to change to Solved if and when you think it is solved.

And I think you can change title while in editing first post. But  titles in every post since do not change. 

I use forum search to find threads with oldfred and it shows ones with new posts, so if a new post in any thread I have posted in, I usually see it.

---

### Post by Mike Krall on 2017-05-29
Off topic:

I found help with "too large graphics, no mouse/touchpad" in the forums here... It took a while.  Really ought to learn how to search more effectively.   
This bug (or similar):  
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623)
This thread: 
[https://ubuntuforums.org/showthread.php?t=2360292](https://ubuntuforums.org/showthread.php?t=2360292)
-------------------------------------------------------------------------------------- 

I may fuss with the title if only to help people find things easily.  I'll leave this open for a bit.  I want to mess with Chromium more and maybe a thread specific to "Chromium in multiple Linux distro separate data partition" would provide information that could be linked to from here.  Does 'oldfred' have any ideas about good place in Ubuntu Forums to run a thread like that?  My tendency is to always stay in "New to Ubuntu" but that may not be particularly productive for the question. 

I'll remember about the searching to find new posts... thank you again 'oldfred'.  I enjoyed the way you helped me by causing me to help myself... I don't know much, but I certainly know a lot more than I did...  =]

Mike

---

### Post by oldfred on 2017-05-29
The forum search is rather limited. One work like oldfred works but anything more complex does not.

 But using google is often better than the forums search function.
Just append **site:ubuntuforums.org** to your search term
or:
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by Mike Krall on 2017-05-30
I forgot I hadn't replied.  Got caught up in being able to search Ubuntu Forums and find things...  =]  Thanks, 'oldfred'... I've been struggling with Ubuntu Forum search coming 10 years now.  

The Ubuntu.com Google link isn't working.  I tried variations... https... googl[COLOR="#FF0000"]e[/COLOR]ubuntu.com... and recombinations.  Nothing worked. Well, appending **site:ubuntu.com** to a search phrase did, of course.

I did change the thread title and put a red-Edit at end of original post.  Maybe helps, maybe ??? 

Mike

---

### Post by oldfred on 2017-05-31
I guess my old link did not work. I found I have it in 4 places in my notes that I typically copy & paste into answers.

I may need to start reviewing old links to make sure they work before posting.
I mostly have used the site:ubuntu.com added to a google search.

---

### Post by Mike Krall on 2017-06-04
> **oldfred said:**
> Yes to both in /mnt/data.
And this is on my newer system created about a year and a half ago.
But /mnt/data was a copy of /mnt/data from flash drive which was a backup of /mnt/data on other system.

I used to use a laptop in FL and Desktop in IL. But found I was now in FL more and laptop's smaller screen and fixed keyboard not as functional. Plus laptop was from 2006 and new desktop in IL had SSD. Big improvement. So new desktop in FL. :)
And I was both copying /mnt/data from desktop to laptop & backing up to flash drives and some data to DVDs.
I realizes it would just be easier to cart flash drive back & forth. And am wanting to set up SSH, but have not gotten around to it as flash drive works for both backup & moving from state to state.

With effectively one /mnt/data on two systems and multiple flash drives I have issues with housekeeping. I need to change my procedures as I have been overwriting flash drive. But files deleted or moved then still are on flash drive and copied to other system, then return when copied back.  Or lots of duplicates get created when trying to reorganize. I need to delete all of a flash drive before copying data to it.

My Thunderbird is probably 10 years old. I have only housecleaned some known older files.

This thread shows files that you do not need to rsync to a backup.
[https://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](https://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

[COLOR="#0000FF"]I change this from /home to my locations in /mnt/data.
/home/lost+found
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/** [/COLOR]

While most of what we have discussed is related to original thread title of triple boot. Some are more detailed on only related issues. Each of those probably should have become a thread. 
You may be better served by asking a separate question on each issue. Since thread is now so long and they see oldfred, others are not contributing. Others also have good ideas, alternatives that can be useful and should be adding their info. So best to start new thread on each new topic.

I'm getting distracted... I did not see the blued section in this post.  Ran off into backups info and never came back.  The three things listed are copied/moved to /mnt/data and symlinked at original position?

Mike

---

### Post by Mike Krall on 2017-06-04
How much time can a person spend looking for Chromium and Google Earth in a multi-distro separate data partition system and not find anything before they admit to being irrationally hard-headed and quit?  Well, I've quit.  Chromium and Google Earth are just going to have to figure out how to live with a separate data partition on their own...  =]   

Mike

---

### Post by oldfred on 2017-06-04
The blue was folders I do not backup/copy to flash drive. I had to edit rsync to not copy those, but askubuntu showed them in /home. So I do not want to copy from my new location in /mnt/data. 
I find newer locations of caches & temporary files. So I occasionally run in test mode & watch what is copied. And then update excludes file to add additional paths to exclude.

Have not used Google Earth for years and use Chromium, but have not tried to move data.

---

### Post by Mike Krall on 2017-06-06
Well, all of everything is in /mnt/data and working for 16.04.  I've yet to put in another Linux... still deciding which first.  I was not able to do all CLI and that is too bad.  I am still a long way from figuring out how commands need structured to do what I want... copy/paste 'R Us... a little 'copy to', 'move to', 'drag-and-drop', and even that causes things to happen I don't understand.  I'm a lot better at finding answers, but still bad at remembering... does that get better with time, 'oldfred'... =]

Some how my 'Documents' symlink in ~/ was "/mnt/data"... instead of "/mnt/data/Documents".  I don't know for sure how it happened but am sure it was not paying attention to the non-CLI shuffling.  I did fix it with: 
"unlink /home/*/Documents" 

Apparently could have used 
"rm linkname" (with no / at end) 

and remade it correctly with: 
"cd"
"ln -s /mnt/data/Documents /home/*"

I'm still trying to understand the 'blued' part of 
[https://ubuntuforums.org/showthread.php?t=2355551&page=14&p=13652593#post13652593]("https://ubuntuforums.org/showthread.php?t=2355551&page=14&p=13652593#post13652593")
I believe I have part of it... will ask when can.

Ran into what to me is an oddment.  Noticed lots of files in a 'Computer' search: mnt...  100+ of them.  Looking at many, all permissioned 'root' / 'root' /..., One example... *"Could not open the file 'proc/2334/task/2339/ns/mnt.  Unexpected error. Error reading from file: Invalid argument"*  Are all of those files to be expected, or ???

Off to spray weeds (White top this time of season)... nice day, at least...  

Mike

---

### Post by oldfred on 2017-06-06
I once linked a folder over a real folder and destroyed data. I did not know then how to unlink or unlink did not return data.
It was the folder with all my notes from Forum (If you search enough in Forum you probably find all of my notes). I had backup, but it was a bit older. Ended up using Photorec which was a task.

The blue files/folders are temporary or cache files that appear in my folders in /mnt/data. So it just exclude most temp type files. A lot of tiny little useless files then do not get backed up. 

I have all my folder in a partition at lowest level.
I mount that partition in fstab.
Then I only from /home run this after deleting any default folders that are same name. Almost always new install, so no data in default folders anyway.
Since in script that already has  sudo to run script, sudo not need. But if run from command line to test then I add sudo.
for i in `echo /mnt/data/*`;do ln -s $i; done

The defaults put links in folder I am in or /home.

---

### Post by Mike Krall on 2017-06-07
Thank you...

I kept my machine as close to 'new install' as possible.  Got the idea from your typical (now) function adding new OS... makes life simple(r), it seemed.  I need 'simple(r)'

If you search your primary OS's "Files/Nautilus" in Computer for 'mnt', do you see a hundred or so mnt files, root/root/... permission, that can't be opened?  I assume yes.  What are they? A byproduct of symlinks connecting places differently? 

Mike

---

### Post by oldfred on 2017-06-07
In /mnt I have several folders. Of course /mnt/data where all my data is.
But I created several mounts, some were just tests of something.
Did you experiment with the /mnt/data folders? or manually make multiple mounts. Or copy some files?
```

fred@Z170N:/mnt$ ls -l
total 40
drwxrwxr-x  2 fred fred 4096 Feb 29  2016 backup
drwxrwxr-x  2 fred fred 4096 Nov 19  2016 backup_Dell
drwxr-xr-x 11 fred fred 4096 Feb 16 16:56 BootInfo
drwxr-xr-x 12 fred fred 4096 Feb 16 16:56 boot-sav
drwxrwxr-x 16 fred fred 4096 Jul  8  2016 data
drwxrwxr-x  2 fred fred 4096 Nov 19  2016 data_Dell
drwxr-xr-x  2 fred fred 4096 May  5 18:40 flash
drwxrwxr-x  2 fred fred 4096 Nov 19  2016 home_Dell
drwxrwxrwx  2 fred fred 4096 Jan 31 12:41 iPhone
drwxrwxr-x  2 fred fred 4096 Jan 24 08:27 tempefi
```

---

### Post by Mike Krall on 2017-06-08
Under /mnt I have only /data. Under /data there are only those folders put there plus 'lost+found' and .'Trash-1000'... both of which were internally created... that is, were in /mnt/data either first or second time I went there.

I have done "none of the above" that I know of, 'oldfred'.  I've been trying hard to follow prescribed procedure. I used GUI out of necessity loading /mnt/data. Idon't know what kinds of things can outfall from that. Could I have done something silly?  How would I know? Yeah, and that's lame, but it's a truth.  

There are two groups of 'mnt' files... Example of first-in-line of the two groups... Under properties window title 'mnt Properties': Location:  /proc/1427/ns  (68 +/- of them)...  and Location:  /proc/1427/task/1427/ns  (360 +/-... and growing). All of each group look identical name with a difference of number.  All sampled (10% of each) show Accessed and Modified as this date and this time.  

Also, att the end of the 'mnt' search-list in Nautilus > 'Computer', there are two sets of three-each named files:  
'/usr/src/linux-headers-4.8.0-54/include/linux/mnt//namespace.h' 
and 
'/lib/modules/4.8.0-54-generic/kernel/drivers/isdn/hardware/eicondiva_mnt.ko'

Both root/root/...  all of first shown identical on opening... all of second (open with ("edit as admin.") are red code-looking pages and no telling if identical...  header claim:  Problem opening,  and "The file you opened has some invalid characters. If you continue editing this file you could corrupt this document. You can also choose another character encoding and try again."  That is what I get every time I open a file of this type... has been true for months.

```
waldo@11:/mnt$ ls -l
total 4
drwxrwxr-x 12 waldo waldo 4096 Jun  5 23:25 data
```

---

### Post by oldfred on 2017-06-08
Are you doing a search on /mnt? And finding it in lots of other places thru out system? Those would all be defaults and do not mess with system files/folders.

Your ls -l from /mnt only shows the one folder or /mnt/data.

---

### Post by Mike Krall on 2017-06-08
I open Nautilus/Files... open 'Computer'... click search icon. Type in mnt... no slash as search won't take a slash.  I get /mnt folder inside of which is /data, etc., a few other folders/files and tons of the mnt files mentioned.  And I didn't say, for who knows why, all mentioned mnt files are links.  Don't know whether hard or soft... don't know how to tell. 

It has occured to me, all mnt files being root/root/ and distinctly unfathomable to me, it might be tons of files for root mounting tons of things?  Anyhow, you will know... then I will know...  =]

And sorry for the poor original description of this... it created a lot of unnecessary back 'n ferth...  =[

Mike

---

### Post by oldfred on 2017-06-09
I think all those other mounts are just your normal system files. You would have those with a brand new unmodified install.

---

### Post by Mike Krall on 2017-06-09
Thank you, 'oldfred'.  It's really difficult for me to tell what a thing is or isn't.  I mean, given time and diligence, I can find out about most anything.  No matter the time and diligence, I'm not going to be able to give someone else the answer you just gave me. 

I've figured out what other Linux distributions I'm going to install.  It's a process... lots of little bits of things to get them all done... install media > GPartEd partition creation > install > etc/fstab > Symlinks > Thunderbird moves and edits and deletes > Program deletes and installs (like out with FF and in with Chromium, etc.) > and all the checks at each step > then again for the next.  I'd almost thought I was sort of done... =]  The hard parts (me coming to understandings) is done.  I'll run through one distribution install and check, then call this thread good-to-go. 

I don't know forum policy.  When a thread is marked "Solved" by the starter, is that the end of any possible posts?  Had a thought I could maybe help someone by putting up bits and pieces of separate data partiton / multiple Linux distro experience... not like "Oh, I like this one" but more technical oriented (given I'm not going to have much to say with any depth to it)... in part, links to stuff that helped me understand possibilities and un-possibilities... the more links, the better... right 'oldfred'...  =]

Mike

---

### Post by oldfred on 2017-06-09
Normally once [Solved] those looking to help stop looking, but those looking for answers can tell thread has solutions.
But this thread is now so long, not sure how many  will review it.

I went thru manually configuring several installs and learned as I went. But then realized that I was doing the same stuff over & over. I thought that was what computers to supposed to save us from having to do.
I most was installing versions of Ubuntu.
So I tried to do as much as I could thru command line. Then listed history and copied commands into a bash file. I then had a script to redo a lot of another install.
Not sure script would be good for anything that was not an Ubuntu flavor.

---

### Post by Mike Krall on 2017-06-09
[I]"Normally once [Solved] those looking to help stop looking, but those looking for answers can tell thread has solutions.
But this thread is now so long, not sure how many will review it."[/I]

That last is odd to me.  Every time I've been looking for help or answers in this or other forums, I've always looked for the longest threads I could find...  more details and/or more views or ways.  

I appreciate that second paragraph... lots of information about "things".  I have no idea what happens after 5 or 6 Linux distributions.  I'll have to get there to find out.  Might be I finally get settled into Unity and am a single OS person again... no telling.  There's a question I've wondered about.  What desktop environment suits you most, 'oldfred'? 

Mike

---

### Post by oldfred on 2017-06-10
I started with Ubuntu 6.06 which was the old gnome2 menus with top & bottom menu bars.
And my monitor (in ILL, FL is wide but I still use same configuration) is an old 4:3 where menu on side like Unity took valuable space & menu bars on top & bottom did not.
And other issue with Unity I have/had was I often open browser or terminal more than one. With menu bar at bottom I can see each separately. With Unity you have to click twice or more.
So I installed fallback/flashback/gnome-panel. Name has changed and it was originally based on gnome2 like Mint (I gather, have not use Mint), but now is based on gnome3.
I hope with Unity being discontinued that gnome-panel stays as an option. They say 17.10 has already switched to gnome, but I have not rebooted the one flash drive install and have not installed to hard drive. I will when I get back to IL as that has a lot faster Internet, till Fall when I get Fiber in Fl. :)

       [https://wiki.archlinux.org/index.php/GNOME/Flashback](https://wiki.archlinux.org/index.php/GNOME/Flashback)
The differences to the MATE project is that GNOME Flashback uses GTK+ 3 and tries to follow the current GNOME development by integrating recent changes of the GNOME libraries.
[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

---

### Post by Mike Krall on 2017-06-11
I started with Ubuntu 6.06, too, and was sorry to see Unity come and Gnome go.  I do like the Unity launcher and it's left side position,  makes my screen taller (relatively) and that's marginally better for picture and documents viewing.  When using Gnome, I actually knew, or could find, where most things were.  Spent some time with Unity trying to relearn the places and never got far.  Still, I look at other desktop environments now and would rather not have top/bottom panels, close-minimize-maximize on right side.  If Dash worked for slow-learners and those of little knowledge, I'd find Unity to be fine enough. 

Thank you for the links, 'oldfred'.  I've spent time looking at different Linux's desktop types and more information helps.  I think I'll have to actually work with the distro's and their DE's to understand them, though.

Mike

---

### Post by Mike Krall on 2017-06-12
Post #148... this thread... the part about bits and pieces for other installs [https://ubuntuforums.org/showthread.php?t=2355551&page=15&p=13654849#post13654849]("https://ubuntuforums.org/showthread.php?t=2355551&page=15&p=13654849#post13654849")

I'm wondering what happens with Grub.  Original UEFI/GPT install has boot at front (/dev/sda1...EFI System...Fat32... /boot/efi mount).  What, if any thing, needs done boot/Grub wise as other Linux OS's are added?

Mike

---

### Post by oldfred on 2017-06-12
I have not installed in UEFI anything other than Ubuntu flavors. And everyone of them overwrites /EFI/ubuntu folder in the ESP. I quickly learned to backup ESP. But it turns out only real difference is the small 3 line /EFI/ubuntu/grub.cfg which is a configfile or chain to full grub.cfg in the install. I have just edited it manually in some cases.

I have seen the Boot-Repair summary reports and some others use /EFI/grub or /EFI/Fedora or similar folders. So they all shared ESP without issue.
And so I know other names/labels can be used by grub2.

 I have filed Ubuntu bug reports or seen bug reports on that, but they do not consider it important, but have to be modifying base grub2 to use "ubuntu". Or have a setting somewhere pretty deep in Ubuntu's grub somewhere. I have tried changing name of GRUB_DISTRIBUTOR in /etc/default/grub and that did create new /EFI/flavor folder, but grub only read the configfile data in /EFI/ubuntu/grub.cfg.

---

### Post by Dennis N on 2017-06-12
> I'm wondering what happens with Grub. Original UEFI/GPT install has boot at front (/dev/sda1...EFI System...Fat32... /boot/efi mount). What, if any thing, needs done boot/Grub wise as other Linux OS's are added?

It depends on the distro as you might expect. I have these installed now on my main UEFI computer: Manjaro, Korora (a self-described Fedora remix), and Linux Mint (XFCE), as well as several Ubuntu-flavor OSes.

First, you have the problem of keeping your primary grub menu up-to-date, as kernel changes in the secondary OSes are not automatically updated in the primary grub menu. With Ubuntu-flavors (and Linux Mint editions) as secondary OSes, there is an easy way to avoid this - see "Maintainance-Free Menu Entries" in the link below. 
 
For other distros, grub menu entries in Ubuntu may require special attention. For example, with UEFI, using Ubuntu to generate the grub menu will fail to generate a bootable entry for Fedora or Manjaro. You can create a custom entry for each of these in order to correctly boot from Ubuntu. I create custom menu entries for all OSes on the machine, based on the methods described at this link:
 
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

At present, I have managed to make this system "maintainance-free" for all OSes installed, meaning the primary grub menu automatically boots the latest kernels in everything and does not require editing.

Have fun with your multi-booting!

---

### Post by oldfred on 2017-06-12
I also do what Dennis N does as in link he posted.
I have a 40_custom with most of the entries i want to boot and turn off os-prober.

I think with Fedora it defaults to LVM and Ubuntu in standard partitions does not have the LVM driver installed.Either you can install lvm2 driver, but if multi-booting I have seen some suggest not using Fedora's default LVM  and just install in a standard partition. One of advantages of LVM is controlling entire drive which if installing to just a small part of drive eliminates that advantage.

---

### Post by Dennis N on 2017-06-12
> **oldfred said:**
> I also do what Dennis N does as in link he posted.
I have a 40_custom with most of the entries i want to boot and turn off os-prober.

I think with Fedora it defaults to LVM and Ubuntu in standard partitions does not have the LVM driver installed.Either you can install lvm2 driver, but if multi-booting I have seen some suggest not using Fedora's default LVM  and just install in a standard partition. One of advantages of LVM is controlling entire drive which if installing to just a small part of drive eliminates that advantage.

I concur with those who recommend a standard partitioning for Fedora (or Korora). That's the way I have done it - no LVM for the OS. 

With Fedora, if you choose when installing to "automatically configure" partitions, then you get LVM. To avoid LVM, you choose "I will create my own partitoning" and proceed to the manual partitioning screen where you specify LVM or standard partitioning and all the mount points, including specify the EFI system partition, which you can't do in Ubuntu's installer. You get the Ubuntu boot menu fail for Fedora with UEFI, but probably not BIOS install.

LVM is easily expandable if you need more room for your OS or data. I think this is the main advantage - especially for data. If I ever outgrew the size of my standard data partition with no simple way to enlarge it, I would change it to LVM and then expand into any available space, even space that is non-contiguous.

---

### Post by Mike Krall on 2017-06-12
Well I was just about to dump an OS in (Bodhi Linux... built on 16.04... Enlightenment 17 mod.).  I'm glad you both got me stopped.  It is going to take a bit for me to read/learn enough about this to see if I have questions (how many, more like).

Thank you 'oldfred'... Thank you 'Dennis N'... 

Mike

---

### Post by Mike Krall on 2017-06-15
Re: Posts #153 - #157 -  I've caught my tail... I'm trying to figure out how to let it go...

Trying to get somewhere...  A thing I've wondered about with a multiple-Linux machine.  Is a person best off having a separate Live-install USB for each OS available?  I've been using one spare USB for different distributions so far. Heading to town for the day tomorrow and could get more if advisable.  If you do this, do you put anything besides the .iso on the USB? Like ??? 

Mike

---

### Post by oldfred on 2017-06-16
I have two hard drives, one SSD and one HDD. 
And in each I create a ISO labeled partition and copy all my ISO into each. Then I can install from SSD to HDD or from HDD to SSD. Had issues trying to install to another partition on same drive, due to mount issues. But still have to often unmount a partition to get it to install. sudo umount -lrf /isodevice.

My problem is I have a MicroCenter about 2 miles away. I do not think I have been to that store and not bought another flash drive. Every time (not really too often) the capacity was doubled for price I am willing to pay. Then USB3 was only one $ more. Only buy USB3 even if current ports are all USB2.
Now all my flash drives 16GB or larger have a full install, many ISO and a lot of my data.

       [URL="https://help.ubuntu.com/community/Grub2/ISOBoot"]https://help.ubuntu.com/community/Grub2/ISOBoot
[/URL]
 Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive) 

[URL="https://help.ubuntu.com/community/Grub2/ISOBoot"]
[/URL]

---

### Post by Dennis N on 2017-06-16
> **Mike Krall said:**
> Re: Posts #153 - #157 -  I've caught my tail... I'm trying to figure out how to let it go...
Trying to get somewhere...  A thing I've wondered about with a multiple-Linux machine.  Is a person best off having a separate Live-install USB for each OS available?  I've been using one spare USB for different distributions so far. Heading to town for the day tomorrow and could get more if advisable.  If you do this, do you put anything besides the .iso on the USB? Like ??? 
Mike
I don't keep the install software for an OS after I do all the installs I plan to do, or even the downloaded ISO itself. I can download another copy of the ISO, and write another USB installer all within 15 minutes should that be necessary.

---

### Post by Mike Krall on 2017-06-20
> **Dennis N said:**
> I don't keep the install software for an OS after I do all the installs I plan to do, or even the downloaded ISO itself. I can download another copy of the ISO, and write another USB installer all within 15 minutes should that be necessary.

Being a slow learner is not so problematic as being a slow understander... 

'Dennis N' and 'oldfred' threw me a curve ball.  Maybe I've got a couple of parts to Grub2 and menu and 'cfg' files and etc.  understood... I'll know later.  I really don't want to ask questions that don't need asking if I can get enough pieces put together first to do otherwise.  I've been through Posts # 154 - #161, 'Dennis N' link, and 'oldfred's links again and again... and to links from those... then out onto the net... then back... then over it all again.  Out on the net I find what I call translations.  Many simply in depth looks at one aspect... like this:
[https://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/]("https://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/")

And then last last night, way down at the end of this:
[https://help.ubuntu.com/community/Grub2/ISOBoot]("https://help.ubuntu.com/community/Grub2/ISOBoot")

[I]**Alternatives to ISO Booting**
In addition to booting directly from an ISO menuentry or a bootable CD/DVD, there are also applications which can install the contents of an ISO onto the user's hard drive. These utilities copy the necessary system files into a folder on the partition designated by the user and can create a menuentry to access these files.

One such utility compatible with Ubuntu is UNetbootin. UNetbootin is available via the Ubuntu repositories and Launchpad. Once UNetbootin extracts/installs the ISO files of an operating system or utility it generates a new item in the GRUB 2 menu.[/I]

*  Is this me (the person just dumpling Linux's into a machine and floating around from one to another with a /mnt/data so my simple little computer world can function in each)? 

*  And the quote at the top... How does 'Dennis N' download .iso and make bootable USB stick in that short a time?  Me, the download (1.50 - 2.50 Mbps wireless radio) is an hour +/-.

Mike

---

### Post by Dennis N on 2017-06-21
> How does 'Dennis N' download .iso and make bootable USB stick in that short a time?

Download Speed = 6 mB/sec =360 mB/min = 1800 mB (1.8 gB) in 5 min.

I use the program called Imagewriter to make a USB installer from the iso - takes no more than 5 min. to do that.

Add a couple of minutes to verify the downloaded ISO, and I would say you have 15 min. or less total time.  

The howtogeek article has good information - adjusting grub menu settings like default menu entry, time out before default OS is booted, optional background image for grub menu, and so on. Important to be aware of these so you can make adjustments if needed. I set my timeout to 900 seconds, since I want to manually choose what to boot.
 
ISO booting: nice for a quick look, but you can't keep any updates, or new software you install - its gone with the next boot. A program that can do this is Gnome Boxes but I think it may require gnome shell to work - I have been trying it out recently - it does not need a grub menu entry. 

Installing in a virtual machine like Virtual Box is another approach that would allow you to do those things ISO boot can't, but getting Virtual Box going is a whole new topic. I haven't used it for a long time, preferring a real install on a small disk partition. 

Just wondering: Have you installed your second OS yet, or still researching?

---

### Post by Mike Krall on 2017-06-21
Thank you 'Dennis N'.  I believe your solution to picking which OS to boot is one that will work for me, too.

I haven't put another OS in yet.  I feel there are things to understand better before I do that.  I'm thinking right now putting one in will get me a 'menuentry'.  What I would do with that is "yet to be determined"...  =]

I decided to save .iso's.  I've downloaded 6 or 7 of them over the past months (some where re-do's), and they always take about an hour... and I've got room in /mnt/data/ISO for them... no problem.  I can do otherwise as I come to understand better, I think.

---

### Post by Mike Krall on 2017-06-28
I installed and ran Yannubuntu's Boot-Info.  I'm wondering if this is right for multi-Linux OS.  I'm intending to follow into '40_custom' for menu entries and maintenance-free.  

Mike
  

[I]Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]

============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        
[/I]

---

### Post by Dennis N on 2017-06-28
Looks correct to me. sda4 is for your next OS?

Comment on custom menus: Quoting from the linked article in post #155, this is the easiest way rather than write it out yourself:

> The surest way to build a custom menu is to copy one or more working menuentries from the grub.cfg file. Menuentries can be placed in any order.

You probably want the custom entries to show at the top of the grub menu, so after pasting the menu entry into 40_custom, save it* with a name beginning with any of 06,07,08,09 - like 06_file-name. They will appear alphabetically in grub menu. I use a different file for each OS (see display below) but others use just one file, and put all the OS menu entries in it. 

*To make it "maintainance free" you need to fix two lines in the menu entry as suggested in the article, before saving:

> Replace the normal linux and initrd references, which normally contain the complete kernel version, with the following:

    linux /vmlinuz root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff{

    initrd /initrd.img

My own /etc/grub.d. One file for each OS that's installed.

```
[dmn@Sydney /etc/grub.d]$ ls
00_header                   07_f-ubuntu-mate-1404  20_linux_xen
06_c-manjaro-xfce-kernel44  07_n-xubuntu-1504      30_os-prober
06_d-Xubuntu-1404           07_p-lubuntu-1404      40_custom
06_e-Xubuntu-1604           07_r-mint-mate-173     41_custom
06_f-korora23               07_s-mint-xfce-173     60_memtest86+
06_h-korora25-gnome         07_t-mint-18-xfce      README
06_k-lubuntu-1704           08_a-ubuntu-mate-1410
06_m-ubuntu-gnome-1704      10_linux

```

---

### Post by oldfred on 2017-06-28
I also back up my 40_custom & make sure to turn off os-prober, so you do not get double entries.

I run Boot-Repair's summary report just to know what is where. And as part of my back up I run bootinfoscript which is part of Boot-Repair's report, but can run without gui, so is part of my rsync file that does several things.

---

### Post by Mike Krall on 2017-06-28
Thank you, both.  I'm going to have to take your info, find other info, and run it against my info...  =]  I feel like I'm getting a rough working understanding for Grub2 and your posts show that... I'm not spun off into LaLa Land again.  I'll still have to double check with you-all, though...

*'Dennis N'*...  /sda4 is /mnt/data.  If, a long time ago now, I had been able to see this point in the process, you would see all the / *partitions-to-be* with everything numbered in order.  As is, disk order will be 1, 2 (16.04), 5, 6, 7, 8, 9, 10, 28 GB unallocated, 4 (/mnt/data), 3 (swap). Now, between /sda2 and /sda4 there is 178 GB 'unallocated'.   

*'oldfred'*...  Backups 'R Us, right?  I don't understand the concept well, so don't intuitively know 'what to' or 'what not to'.  I'd thought to backup parts of the Grub2 files before making changes (like I did with /etc/fstab).  Would you say what else besides '40_custom' a person ought to consider for back up in this 'menuentry' process? 

Mike

---

### Post by oldfred on 2017-06-28
Anything I manually edit in /etc, I copy to /home (really then in /mnt/data). Since it normally is only a few files it saves backing up all of /etc. Otherwise you should backup /home, /mnt/data,list of installed apps and if server or other software running from / folders somewhere will also need configurations & data backed up.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup

[/URL]
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) 

(Did I post this before?)
Maybe why separate thread on each issue is better rather than on mega-thread.

[URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]
[/URL]

---

### Post by Mike Krall on 2017-06-29
Thanks, 'oldfred'... this is going to help.  

*  A quick question from beginning of above post #169.  You save/backup "*a list of installed apps*".  Is there a command for generating that?

Mike

PS...  No... not posted before in this thread... or not all.  I found the first two links on my own after reading your many mentions of backing-up... a thing I'll have to learn and deal with... but not here... I promise!

I do understand much of this forum is "specifically, specific Q&A"... it's "the standard form" in a lot of other Linux/computer-in-general information sources, whether forum or Wiki or manufacturer or, etc., etc.  I see the importance and value of the form.  Still, my view, or rather, my way of coming to understanding/doing does not work well with it.

---

### Post by oldfred on 2017-06-29
If you go back to my post on things to backup (oldfred's list from 2011) is the dpkg command to create a list of installed apps. It is just a text file. If reinstalling apps to a newer version, you may want to edit out old kernels and perhaps some other info.

I still use same rsync command to copy files to another folder on another drive. I do not necessarily consider that backup as backup also has to be versioned. Or if you edit a file can you recover versions before edit but after you run a backup. Since only my personal data and not much changing, I copy most critical data to DVDs,flash drives & totally other systems. And more regularly run the rsync to another drive, but it is not versioned.

If running a business or have lots of critical data better to use versioned backups daily or even more often.

I have thought about changing to rdiff, but my rsync has been enough for me.
 [https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync](https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync)
Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)
[https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/)

---

### Post by Mike Krall on 2017-06-30
I did it again... didn't read before yapping...  =[   I'm sorry to have caused you extra time-use 'oldfred'.  

Mike

---

### Post by Mike Krall on 2017-06-30
'oldfred'...  Would you show me how your /etc/grub.d. lies?  And/or your 40_custom?  

'Dennis N'....  Do you turn off 30_os-prober?  If not, how does it not make extra menuentries?

Mike

---

### Post by Dennis N on 2017-06-30
> **Mike Krall said:**
> 'oldfred'...  Would you show me how your /etc/grub.d. lies?  And/or your 40_custom?  

'Dennis N'....  Do you turn off 30_os-prober?  If not, how does it not make extra menuentries?

Mike

Once I know the custom entries work, I turn off the os prober and run sudo update-grub again to remove the non-custom entries as a final step. The os prober will still run under certain circumstances - like if grub packages are re-installed in an upgrade.

Attached is a screen shot of grub menu's appearance.

---

### Post by oldfred on 2017-06-30
This is my 40_custom on this system. I use a configfile to chain to a text file with the boot stanzas for my ISO. I have ISO on both SSD to install to HDD and HDD to install to SSD. Or either to install to a flash drive. I changed to configfile as I regularly update some ISO with newer version and have to edit. But I almost always forget to run the sudo update-grub. With configfile no update required, just edit of text file with boot stanzas.

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


menuentry "Xenial on sdb3" {
    set root=(hd1,gpt3)
        linux /vmlinuz root=/dev/sdb3 ro quiet splash
        initrd /initrd.img
}

menuentry "Yakkety on sdb9" {
    set root=(hd1,gpt9)
        linux /vmlinuz root=/dev/sdb9 ro quiet splash
        initrd /initrd.img
}

menuentry "Mate 16.10 on sdb10" {
    set root=(hd1,gpt10)
        linux /vmlinuz root=/dev/sdb10 ro quiet splash
        initrd /initrd.img
}


menuentry "trusty 14.04.3 on sdb10" {
    set root=(hd1,gpt10)
        linux /vmlinuz root=/dev/sdb10 ro quiet splash
        initrd /initrd.img
}

# spacer line
menuentry " " {
set root= 
}

menuentry 'Live ISOs on SSD' {
configfile (hd0,5)/livecdimage.cfg
} 

menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,6)/livecdimage.cfg
} 

# spacer line
menuentry " " {
set root=
}

menuentry "System restart" {
echo "System rebooting..."
insmod reboot
reboot
} 

menuentry "System shutdown" {
      echo "System shutting down..."
      insmod halt
      halt
}
```

My script is outdated, I am about to install 17.10 over one of my old installs.

---

### Post by Mike Krall on 2017-06-30
Thank you, 'oldfred'.  I don't understand the description of your "ways" and "why's", but the picture is what I wanted... it helps, for sure. 

I don't know where I'll get to between now and the weekend after the 4th of July.  There are plans on plans, trips to and from, old, old friends by the bucket load. I'll try, but I wouldn't bet a nickle on much time here.

Mike 

PS...  Just noticed...  Mate 16.10 and Trusty 14.04 both on sdb10.  ???

---

### Post by oldfred on 2017-06-30
That is why I said it is outdated. I probably copied boot stanza with a new install, but did not delete the old one. Needs housecleaning. Not sure what I have where, but with new 17.10 install I will have to update.
With old BIOS system I had so much room that I filled my sdc drive with 25GB  / (root) partitions, some same version just to test something, but never deleted. Now I still have some space to add more 25GB partitions, but have no use for old installs, so will overwrite something.

---

### Post by Mike Krall on 2017-06-30
Ah, OK... I miss interpreted "My script is outdated..."   

Mike

---

### Post by Mike Krall on 2017-06-30
This is silly... I've been looking for answers for this off and on for a while and haven't gotten anywhere with it.

I'm going to create 6, 25GB, partitions for other Linuxes.  That will leave +/- 27.5 GB 'unallocated' in front of /mnt/data that is tight against 'swap' at end of disk.  One day I might use that empty space for another Linux distribution... OR... one day I might need the empty space in /mnt/data.  Neither of those are particularly likely.  Would you create an ext4 partition there now (along with those for other Linuxes), or would you leave it as 'unallocated'? 

Mike

---

### Post by oldfred on 2017-06-30
Totally up to you.

I leave mine unallocated. If an SSD probably better to leave unallocated as they suggest a small amount of unused space on SSD, so newer SSD can manage use/life.

---

### Post by Mike Krall on 2017-07-01
Thank you, 'oldfred.  Finding discussion/answers is a lot easier when a person knows (now) what to search for...  =]

Mike

---

### Post by Mike Krall on 2017-07-02
I got the partitions built tonight.  GPartEd through a live install USB... one at a time.  Now it's /sda 1,2,5,6,7,8,9,10,4,3... with 27.5 GB 'unallocated' between /sda10 and sda/4 (/mnt/data).  

I would liked to have installed an OS, but I couldn't make the time.  Who knows what I'll be thinking about which OS's next weekend and I've still got some blank spots in the whole 'menuentry' part... questions I haven't asked, but need to.  

Right now, OS's I intend to put in are:

*  elementaryOS

*  Bodhi Linux

*  Mint Xfce and Cinnamon

I'd like to work with a Gnome desktop... maybe Ubuntu or Kororaa or both.  I'd like to see Manjaro and MX and Debian.  I guess, in the end, it's a lot about desktop environments.  I've been trying to figure out which distributions have well suited desktops... distributions that aren't WAY over my head (Arch, Fedora, etc.)

Anyhow, I'll be back.  Have a nice time with the holiday.

Mike

---

### Post by Mike Krall on 2017-07-13
> **oldfred said:**
> I have not installed in UEFI anything other than Ubuntu flavors. And everyone of them overwrites /EFI/ubuntu folder in the ESP. I quickly learned to backup ESP. But it turns out only real difference is the small 3 line /EFI/ubuntu/grub.cfg which is a configfile or chain to full grub.cfg in the install.[COLOR="#FF0000"] I have just edited it manually in some cases.[/COLOR]

I have seen the Boot-Repair summary reports and some others use /EFI/grub or /EFI/Fedora or similar folders. So they all shared ESP without issue.
And so I know other names/labels can be used by grub2.

 I have filed Ubuntu bug reports or seen bug reports on that, but they do not consider it important, but have to be modifying base grub2 to use "ubuntu". Or have a setting somewhere pretty deep in Ubuntu's grub somewhere. I have tried changing name of GRUB_DISTRIBUTOR in /etc/default/grub and that did create new /EFI/flavor folder, but grub only read the configfile data in /EFI/ubuntu/grub.cfg.

Some times, the more I don't think about a thing, the better I understand it.  So, am I getting close yet? 

I've found and backed up /EFI/ubuntu/grub.cfg.  What do the three lines say, 'oldfred'?
---------------------------------------------------------------------------

The red line in the quote...  The only thought I've come to is, as a step to keeping a certain OS in a primary position... keeping boot and/or grub in that OS.  Like this...  my case of primary OS Ubuntu-Unity LTS with multiple other OS's coming and going... put in new OS, EFI/ubuntu/grub.cfg gets overwritten.  I reset it to primary OS via backup Ubuntu-Unity version. 

Is there a logic, or necessity, to have the three lines point to same-as GRUB_DEFAULT=  in /etc/default/grub ? 

Mike

---

### Post by Dennis N on 2017-07-13
/EFI/ubuntu/grub.cfg:

```
dmn@Sydney:/boot/efi/EFI/ubuntu$ cat grub.cfg
search.fs_uuid 76a3e43d-fc69-4907-ac71-79fdd0b77cd3 root hd1,gpt15 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```
The first line contains the OS location using its UUID and root partition designation (here, the OS is on sdb15). These can be manually edited to specify the previous Ubuntu OS location. 2nd and 3rd line specify where in the OS the grub.cfg file is that generates the grub menu, which is a different grub.cfg. These 2 lines don't change (at least not so far).
-------------
You can backup the entire ubuntu folder before installing another ubuntu os and copy it back after the new install is done, or just edit the file above and change the UUID and root location to the ones you want. Save it and reboot.

I used to edit this file, but my preference now is to use a non-ubuntu OS to control the booting. I am using Manjaro, because it's a rolling release and (theoretically) permanent. So far, this has met my expectations.

---

### Post by oldfred on 2017-07-13
I both backup ESP to another drive, include in my rsync backup and copy /EFI/Ubuntu to another folder in /EFI and copy each installs grub.cfg to its name like grub_artful.cfg. Then when next install overwrites it I can either edit back by copying or copy/rename file.

I have tried renaming grub distributor. Comment out standard with # and add my own.
        
 #GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
       GRUB_DISTRIBUTOR=`artful` 

Several versions ago it did create a folder in /boot/efi/EFI using the version's name. But it still used the /EFI/ubuntu/grub.cfg.

Have not tested with my latest version artful, yet as example shown above.
My main working install is now always the latest LTS version.

---

### Post by Dennis N on 2017-07-13
> I have filed Ubuntu bug reports or seen bug reports on that, but they do not consider it important, but have to be modifying base grub2 to use "ubuntu". Or have a setting somewhere pretty deep in Ubuntu's grub somewhere.

I think the folder for grub bootloader files is set in the installer's grub-install options, specifically 

```
--bootloader-id=ID
the ID of bootloader. This option is only available on EFI and Macs.

```

I think Ubiquity has set the option: 
**--bootloader-id=ubuntu**

It seems you should be able to manually install grub, and change this to something else, but I have not attempted that.

---

### Post by oldfred on 2017-07-13
Thanks Dennis N.
found more details & explanations why name issue may be there because of UEFI Secure Boot.
Booting multiple Ubuntu versions with EFI
[http://blog.lxgr.net/posts/2015/04/30/grub-efi-multiboot/](http://blog.lxgr.net/posts/2015/04/30/grub-efi-multiboot/)
And 
[https://www.kubuntuforums.net/showthread.php?t=43221&page=15](https://www.kubuntuforums.net/showthread.php?t=43221&page=15)

---

### Post by Dennis N on 2017-07-14
Thanks for the information. I need to study the blog post further to fully absorb. I have already been able to get two Ubuntu's on different EFI system partitions without resort to using grub-install. All I did was move ubuntu folder to new EFI partition, make a new EFI boot menu entry with efibootmgr and edit fstab location of EFI partiton to mount. That works. 

The reason was to have an installation immune to EFI folder being overwritten by additional ubuntu installs, thus eliminating the need to restore a backup folder or edit.

Later, I started using Manjaro to control the booting instead because it is a rolling release which won't (theoretically) need to be replaced. 16.04 will eventually reach EOL.


 Current output of efibootmgr -v | grep -i ubuntu

```
dmn@Sydney ~ $ sudo efibootmgr -v | grep -i ubuntu
Boot0000* ubuntu	HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0003* Xubuntu	HD(1,800,64000,8e6dba8f-5bdf-4b99-b7a4-2730717b1dba)File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0004* ubuntu	HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)File(\EFI\UBUNTU\GRUBX64.EFI)..BO
Boot0005* ubuntu	HD(1,800,64000,8e6dba8f-5bdf-4b99-b7a4-2730717b1dba)File(\EFI\UBUNTU\GRUBX64.EFI)..BO


```Boot0003 is Xubuntu 16.04 with its /EFI/ubuntu folder moved to sdb1. Once booted, it has custom grub menu entries to boot other OS on the computer.
Boot0000 is just the most recent ubuntu-type install. I believe it is Ubuntu GNOME 17.04

---

### Post by Mike Krall on 2017-07-27
Of the Engine Order Telegraph's typical dial positions, one is 'Dead Slow Ahead'...

There are a lot of bits and pieces between Post #153 where I asked, "*I'm wondering what happens with Grub. Original UEFI/GPT install has boot at front (/dev/sda1...EFI System...Fat32... /boot/efi mount). What, if any thing, needs done boot/Grub wise as other Linux OS's are added?*",   and present position... this post, #189. 

There is no way to reference them all short of WAY too much copy/paste with reference-to-references dialog... colored lines to specifics in each... inadequate/unknowledgeable questions about too many colored-lines.  Un-do-able.  The alternative would have been to ask questions along the way... not read a lot first, just ask.  Who knows how that would have worked... seemed another "un-do-able" to me.

I'm stuck... Like "All ahead, Stop" (a contradiction in Engine Order Telegraph directive... impossible to execute)... W&TF.

One thing at a time...

These links from 'oldfred' Post # 187....> Thanks Dennis N.
found more details & explanations why name issue may be there because of UEFI Secure Boot.
Booting multiple Ubuntu versions with EFI
[http://blog.lxgr.net/posts/2015/04/3...efi-multiboot/](http://blog.lxgr.net/posts/2015/04/3...efi-multiboot/)
And 
[https://www.kubuntuforums.net/showth...=43221&page=15](https://www.kubuntuforums.net/showth...=43221&page=15)


From Lxgr blog link, at ending, is this link... [https://www.kubuntuforums.net/archive/index.php/t-68588.html]("https://www.kubuntuforums.net/archive/index.php/t-68588.html")

At end 2015, the last date I find any reference to /boot/efi/EFI/ubuntu/grub.cfg... no boot of "other Ubuntu's" do to overwriting.  I thought the problem must be resolved but the last few 'oldfred' and 'Dennis N' posts cause me to think maybe not.  If resolved, I'd like to know about the solution.  If not, how do 'oldfred' and 'Dennis N' run multiple Ubuntu's and live?

Mike

---

### Post by Dennis N on 2017-07-27
I think you are concerned about too much. You have the disk all prepared - I suggest just installing one of your selected distros as a second OS and experience first hand what happens. You can create a custom menu later if you want that and you probably will when you get to 4 or more OS. 

Mint XFCE is an good one to start with - much like Ubuntu, except for the Mint updater, and the Mint Software "store" where you pick applications you want to install. They put a lot of effort into revising those to make them a bit nicer (my opinion, of course). 

I think your OS choices are all Ubuntu based, so they probably use the Ubuntu installer. We know how to work with that - such as how to edit the grub.cfg in the EFI system partition to have grub menu from your first OS restored to appear at startup if desired. And in the meantime, Mint will handle the dual boot just fine as well.

>  ...no boot of "other Ubuntu's" do to overwriting. I thought the problem must be resolved but the last few 'oldfred' and 'Dennis N' posts cause me to think maybe not. If resolved, I'd like to know about the solution. If not, how do 'oldfred' and 'Dennis N' run multiple Ubuntu's and live?


Just because the second Ubuntu-type OS will overwrite the folder of the first Ubuntu-type OS doesn't mean the first can't be booted. It will appear in the grub menu of the new OS. I have custom grub menu entries, but the adoption of those developed over time until I managed to get a no-maintenance UEFI setup  -  including some OS which are not Ubuntu based that I needed to learn something about.

---

### Post by oldfred on 2017-07-27
I backup my ESP, and found it really only is the three line grub.cfg in /EFI/ubuntu that is a configfile (chain) to the full grub.cfg in an install. So I have also edited it, or just backed it up. If I know the new install is just temporary, I edit the grub.cfg before rebooting as easier from live installer, see permissions below. Then edit my 40_custom in my main working install to include that new install's partition.

If not Ubuntu, I have seen Boot-Repair reports with that distribution's name in UEFI entries. All my installs are Ubuntu flavors.

New versions of Ubuntu set very limited permissions on the ESP, so from inside your install you cannot see it. Probably for security reasons. But I change permissions back so I can work with it from inside my install.

After you do a couple of installs, you can come back with more questions. But it should just keep working.

---

### Post by Mike Krall on 2017-07-28
Wrote this but forgot to post in the morning...  

Thank you both.  I've read each twice. Now out the door for a day of spraying leafy spurge.  I will do some processing during the time of 'hunt and squirt'.

Mike

---

### Post by Mike Krall on 2017-07-28
Now I've read 'Dennis N' and 'oldfred' last two posts 4 x's... =]  I've got questions generated by each but I'm not going to ask them... and I'm not going to go off "researching" them.

*This is what I want to do*... I'll likely go for some time using Ubuntu 16.04 LTS.  Ubuntu is the only Linux I know... it's home.  Having other Linuxes to work in may change that.  That would be down the road.  Set up as Ubuntu LTS first, everything else after that. I want to have this be "maintenance free".  I want to be able to incorporate *other-than-Ubuntu* Linuxes.  Those three things.  

I'm working on copies and backups.  I like terminal and I like man pages.  I don't know enough to use either out of my own head... and they make my brain ache.  I'll use terminal as I can, GUI to get things done without so much searching/reading.

I need to back up ESP.  I thought to rsync /boot/efi into /mnt/data or to a USB...  my best guess is:

```
sudo -i
rsync -azvh /boot/efi/  /mnt/data/16.04_efi.backup/

# Or

sudo -i
rsync -azvh /boot/efi/  /dev/sdb/16.04_efi.backup/
```
---------------------------------------------------------

Over time I've generated a list of Linuxes I'll spend time in.  Some that I've downloaded and "Tried" got deleted... some not.  I knew at the start this was not about work environment... it's about comfort, ease, personal aesthetic, simple curiosity, learning, and fun.

The list of Linuxes I'd like to look in... roughly ordered by interest: *elementaryOS... Linux Mint Cinnamon... KDE Neon... Linux Mint Xfce... Bodhi Linux Enlightenment..*. and in no particular order... *Peppermint 8... Zorin OS... Manjaro Xfce... MX OS Xfce... Debian Gnome... Kororaa 25 Gnome... Fedora 24 Gnome... Ubuntu Gnome... Linux Mint MATE... OpenSuse KDE and/or Gnome... Ubuntu 14.04.4 Unity *(Dedoimedo says it's a truly Great Ubuntu).

Mike

---

### Post by Dennis N on 2017-07-28
Happy to answer questions and discuss these issues, so don't hesitate to ask. 

At the risk of being too repetitive:

I would be easy to avoid the overwriting problem if you are able to choose a different EFI system partition for the second Ubuntu-type install. Ubuntu installer so far does not allow this. But, knowing what is going to happen we can take preventative measures and save the ubuntu folder before installing the 2nd Ubuntu-type OS, then copy it back. An alternative is to directly edit the grub.cfg file in the EFI folder to be as it was before. (There is still another way I touched on in post #188, but not as simple.)

Other distros can make life simpler in this respect, because their installers allow you to choose an EFI system partition to use, so the overwriting problem can be avoided. Create and choose a different EFI system partition if you know an installation will overwrite the EFI system folder of another install.

---

### Post by oldfred on 2017-07-28
I have two drives, so I just copy to ESP on sdb (HDD) as I have yet to get grub to directly install to sdb, except the one time I had SSD (sda) unplugged, and then HDD was sda. and then I have copies in /EFI/ that I have renamed.

I do not consider copies to same drive as backup, but often do that. 

Backup needs to be different drive, so when drive fails you still have it. And backups need to be versioned, or if you edit a file you have both the unedited & edited version, just in case you need old version. 

I do not have a lot of data I consider I need to fully back up regularly, so use flash drives & DVDs. I do have copies (not then really backups) on several drives.

After giving myself permissions to see EFI from inside my install, I just copy folder to version it is and copy grub.cfg back. Or I just edit my grub.cfg.
 sudo cp /boot/efi/EFI/ubuntu /boot/efi/EFI/mate
sudo cp -a /boot/efi/EFI/xenial/grub.cfg /boot/efi/EFI/ubuntu

I now more often, just edit grub.cfg in /EFI/ubuntu. Test install in sdb9, edited back to working install in sda6. UUID & drive info.

```
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
#search.fs_uuid fabeeda1-ad36-4300-a7f8-73afba118f37 root hd1,gpt9 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

---

### Post by Mike Krall on 2017-07-30
> **oldfred said:**
> I have two drives, so I just copy to ESP on sdb (HDD) as I have yet to get grub to directly install to sdb, except the one time I had SSD (sda) unplugged, and then HDD was sda. and then I have copies in /EFI/ that I have renamed.

I do not consider copies to same drive as backup, but often do that. 

Backup needs to be different drive, so when drive fails you still have it. And backups need to be versioned, or if you edit a file you have both the unedited & edited version, just in case you need old version. 

I do not have a lot of data I consider I need to fully back up regularly, so use flash drives & DVDs. I do have copies (not then really backups) on several drives.

[COLOR="#0000FF"]After giving myself permissions to see EFI from inside my install[/COLOR], I just copy folder to version it is and copy grub.cfg back. Or I just edit my grub.cfg.
 sudo cp /boot/efi/EFI/ubuntu /boot/efi/EFI/mate
sudo cp -a /boot/efi/EFI/xenial/grub.cfg /boot/efi/EFI/ubuntu

I now more often, just edit grub.cfg in /EFI/ubuntu. [COLOR="#008000"]Test install in sdb9, edited back to working install in sda6. UUID & drive info.[/COLOR]

```
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
#search.fs_uuid fabeeda1-ad36-4300-a7f8-73afba118f37 root hd1,gpt9 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```


*In blue*...  my /boot/efi/EFI are all root root.  Are you changing 'owner' and/or 'group' permissions to 'me' and/or 'user'? Where changed... like for /EFI? 

*In green*...  I don't understand what you are doing here.

Mike

---

### Post by Dennis N on 2017-07-30
The EFI system partition is FAT file system, so the permissions for access are set in /etc/fstab. Here is how I change the line in /etc/fstab that mounts the EFI system partition to make it accessible:

```
# /boot/efi was on /dev/sda1 during installation
UUID=3DE5-79D6  /boot/efi       vfat    [COLOR="#FF0000"]defaults[/COLOR]      0       1

```
I replace whatever they have as permissions (the section after 'vfat') to 'defaults'. Then you are able to copy the ubuntu folder and store it somewhere in your own space (home folder or external). Use sudo with **cp -R** to put it back after a new installation has replaced the previous folder. 

An alternative method to backing up the ubuntu folder is to edit the grub.cfg file inside it to restore root UUID and root setting. Even if you never back up the folder itself, you can find the correct UUID with the **blkid** command.

Good luck.

---

### Post by oldfred on 2017-07-30
Up thru about 14.04, Ubuntu used defaults to mount the ESP. But they changed, I do not know full reason but suspect for security. 
Boot-Repair also changes entry in fstab to defaults as it is also writing into ESP.

The edit of my 3 line grub.cfg, is either from blkid or my backup grub.cfg and I used # to comment out the install in sdb9 and use my main working install in sda6. I change UUID & drive & partition.


Windows formatted partition like FAT32 or NTFS always are shown as root. It then is permissions that let you use them. The Windows formats do not support Linux style ownership & permissions. Also part of why Linux is a bit more secure than Windows.

---

### Post by Mike Krall on 2017-07-30
I'll, hopefully, mess with ESP copy/backup tonight, and get one or more installs done.  I was thinking I'd need to copy (maybe edit first) /etc/fstab as I go along).  I already have one /etc/fstab copy from /mnt/data creation.  I understand each new copy needs to be different (like numbered) or 'cp' will overwrite (I assume having all versions of /etc/fstab is desirable).
----------------------------------------------------------------------------------

Right now, my /etc/fstab is this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=0f47f885-3e8b-475b-9082-2ea2c05ff732 /               ext4    errors=remount-ro 0       1
[COLOR="#0000FF"]# /boot/efi was on /dev/sda1 during installation
UUID=B70F-1399  /boot/efi       vfat    umask=0077      0       1[/COLOR]
# swap was on /dev/sda3 during installation
UUID=a64147fb-9025-46ee-b704-c6b7877d28c7 none            swap    sw              0       0
# /mnt/data was on /dev/sda4 during installation
UUID=a3c5362b-1fb9-44b9-8afb-050980ea65c2 /mnt/data ext4 auto,users,rw,relatime 0 2
```

Is there any security need of moving blue-line back to original after all copy/backup is done... like switch it back and forth as necessary?
-----------------------------------------------------------------------------------

Somewhere in here it seems like I need to make changes in /etc/default/grub.  I've got links (and discussion here) to ideas about that, and I understand it can be changed quite easily.  Is there an advisable "When"? 

Mike

---

### Post by Dennis N on 2017-07-30
> Is there any security need of moving blue-line back to original after all copy/backup is done... like switch it back and forth as necessary?
I consider it a permanent change. Never changed it back from "defaults".

/etc/default/grub is for grub settings for the grub menu, like GRUB_DEFAULT=0, GRUB_TIMEOUT=10 and so on. I change the timeout to 900, because I will be choosing myself which OS to boot, and that gives me plenty of time to act. I don't think I've changed any other settings in that file on Ubuntu.

Some grub menus (like Ubuntu MATE) have a theme or background, which is nice, but if it's not already there, I don't bother with such things.  

Good luck with your install(s).

---

### Post by oldfred on 2017-07-30
Each install has its own fstab, so you may want to back it up to have any manually edited additions like your data partition, but should not need and would not copy one fstab to another system as then you mount incorrect / (root).

---

### Post by Mike Krall on 2017-07-30
Thank you, 'oldfred'

A while back I had worked into my head the separation realities (only linked through /mnt/data).  I think dealing with Grub2/Boot drug me away from that... mostly separate, excepting fer...  =]

Mike

---

### Post by Mike Krall on 2017-07-31
> **Dennis N said:**
> The EFI system partition is FAT file system, so the permissions for access are set in /etc/fstab. Here is how I change the line in /etc/fstab that mounts the EFI system partition to make it accessible:

```
# /boot/efi was on /dev/sda1 during installation
UUID=3DE5-79D6  /boot/efi       vfat    [COLOR="#FF0000"]defaults[/COLOR]      0       1

```
I replace whatever they have as permissions (the section after 'vfat') to 'defaults'. Then you are able to copy the ubuntu folder and store it somewhere in your own space (home folder or external). Use sudo with **cp -R** to put it back after a new installation has replaced the previous folder. 

An alternative method to backing up the ubuntu folder is to edit the grub.cfg file inside it to restore root UUID and root setting. Even if you never back up the folder itself, you can find the correct UUID with the **blkid** command.

Good luck.

There is something I don't understand... edited /etc/fstab to 'defaults', saved, rebooted.  All of /boot, /efi, /EFI, /ubuntu, and on, show permissions root root 'you are not owner...'  
The /efi no longer has an 'x' on it (or maybe it was a lock)... is the only change I find. 
```
# /boot/efi was on /dev/sda1 during installation
UUID=B70F-1399  /boot/efi       vfat    [COLOR="#0000CD"]defaults[/COLOR]      0       1 
```
It's not possible to run:
```
waldo@11:~$ sudo cp /boot/efi/EFI/ubuntu /boot/efi/EFI/ubuntu-16-unity2
cp: omitting directory '/boot/efi/EFI/ubuntu'
waldo@11:~$
```

I did get all of /boot/efi/EFI/ubuntu into /boot/efi/EFI/ubuntu-16-unity via GUI... open all as administrator... rt. clk. > copy to > sort-to-folder > select > copy... for each item.  Not the easy way.  

Just thought and did... open /EFI as admin., rt.clk. /ubuntu > copy to > sort to /EFI > select.  Makes 'ubuntu(copy) in /EFI... rt. clk. > rename to /ubuntu-16-unity.  Worked... dumped all other similar folders. 

I did try the command in both cd terminal and cd /boot/efi/EFI terminal.  Putting in '-a' (with spaces) after 'sudo cp' did make /ubuntu inside of /ubuntu-16-unity.

So, what did I do (or not do) causing /etc/fstab to not change permissions... Or... wrong-ness in command-ing... Or... ??? 

Mike

---

### Post by Dennis N on 2017-07-31
Hello. 'defaults' changes the permissions, not the owner or group for the folder. did you restart after editing fstab so the new permissions can take effect? You are considered an 'other' user. 

With 'defaults' in fstab, I have these permissions:
```
dmn@Zotac:/boot/efi/EFI/ubuntu$ ls -l
total 4764
-rwxr-xr-x 1 root root   72144 Jul  9 14:16 fbx64.efi
drwxr-xr-x 2 root root    2048 Jul  9 14:16 fw
-rwxr-xr-x 1 root root   64352 Jul  9 14:16 fwupx64.efi
-rwxr-xr-x 1 root root     126 Jul  9 14:16 grub.cfg
-rwxr-xr-x 1 root root 1121144 Jul  9 14:16 grubx64.efi
-rwxr-xr-x 1 root root 1168464 Jul  9 14:16 mmx64.efi
-rwxr-xr-x 1 root root 1271672 Jul  9 14:16 MokManager.efi
-rwxr-xr-x 1 root root 1169992 Jul  9 14:16 shimx64.efi

```

To copy the folder and its contents, you need to use **cp -R**. You don't really need sudo if the destination is in your user space, since you have read permissions. To copy the folder back, you do need to use sudo, since your user has no write permissions.

for example,
```
dmn@Zotac:/boot/efi/EFI$ cp -R ubuntu ~/Desktop
```

---

### Post by Mike Krall on 2017-07-31
Bound to happen... =[

Trying to work with sudo cp from above post... in new terminal ('cd' > Enter) ran: 'sudo cp -a /boot/efi/EFI/ubuntu . /boot/efi/EFI/new-ubuntu.  It was a run away.  "x-ed" out... killed process.  Got a note on Desktop  of '0 bytes in /efi'.  Messing with folder names in /EFI, couldn't rename.  Deleted folder and created new one, or tried to... note: no room in /EFI.  I'm clueless.  

Had also tried sudo cp -a /boot/efi/EFI/ubuntu . /boot/efi/EFI/new-ubuntu from 'cd /boot/efi'.  Why?  Why does a person do anything? It's not like I don't know I can't get myself out of corners. 

Mike

---

### Post by Dennis N on 2017-07-31
man page for cp says -a option includes the -R option, so should work. If the destination folder exists before copying, copied folder should go inside it. If not, it duplicates the source folder with name changed to destination name. Not sure what your actual command was, as you have a period between the source and destination in what you wrote: > sudo cp -a /boot/efi/EFI/ubuntu . /boot/efi/EFI/new-ubuntu

I would recommend not backing up in the EFI folder since you lose original and copy if the EFI folder goes down.

---

### Post by Mike Krall on 2017-07-31
I got it fixed, 'Dennis N'...  disk usage analyzer was the "note" I mentioned.  Showed again after reboot (hoping it would maybe fix itself) with an 'Examine' option, so I did.  10228 items in 'new-ubuntu'.  efi contains EFI and .Trash-0, inside of which is 'new-ubuntu' and some other dumped folders.  It's a virtuous circle.  Can't send 'new-ubuntu' to Trash (not the Desktop trash).  Way out was opening efi as administrator, show hidden files, rt. clk. .Trash-0 > send-to-trash > note says, can't do that but can delete immediately.  I thought, whatever got copied into 'new-ubuntu' is a copy, deleting will be fine... right?  =]  Well it appears fine, is fine this time.  If efi needs a .Trash-0, it can make another one like it did the first time, right? 

"*sudo cp -a /boot/efi/EFI/ubuntu . /boot/efi/EFI/new-ubuntu*" is actual... 2011 "Ask Ubuntu" answer with explanation of why the dot was necessary.  

I can't do it now... gone late-ish... but I'll work with your command description tomorrow (likely night-ish).  I almost got to an install... 

I just noticed you posted twice.  Can't get to 'defaults' now, either... getting in my jammies... thank you and thank you, 'Dennis N'.

Mike

---

### Post by oldfred on 2017-07-31
I looked at my history, but do not remember now. (Something about old in oldfred.)
But I include a backup of history in my rsync backups script.

I found multiple commands where I tried to copy my ubuntu to mate, so not working. 
But last two commands I had to create the folder first. Not sure why, but have had a few cases where if multiple levels deep my rsync commands will not copy.

This tells my I installed mate, copied the ESP to a mate folder & restored my grub.cfg from xenial folder previous made (my main working install).
378  sudo mkdir /boot/efi/EFI/mate
  379  sudo cp -a /boot/efi/EFI/ubuntu/* /boot/efi/EFI/mate
  380  sudo cp -a /boot/efi/EFI/xenial/grub.cfg /boot/efi/EFI/ubuntu

---

### Post by Mike Krall on 2017-07-31
> **Dennis N said:**
> Hello. 'defaults' changes the permissions, not the owner or group for the folder. did you restart after editing fstab so the new permissions can take effect? You are considered an 'other' user. 

With 'defaults' in fstab, I have these permissions:
```
[COLOR="#0000CD"]dmn@Zotac:/boot/efi/EFI/ubuntu$ ls -l[/COLOR]
total 4764
-rwxr-xr-x 1 root root   72144 Jul  9 14:16 fbx64.efi
drwxr-xr-x 2 root root    2048 Jul  9 14:16 fw
-rwxr-xr-x 1 root root   64352 Jul  9 14:16 fwupx64.efi
-rwxr-xr-x 1 root root     126 Jul  9 14:16 grub.cfg
-rwxr-xr-x 1 root root 1121144 Jul  9 14:16 grubx64.efi
-rwxr-xr-x 1 root root 1168464 Jul  9 14:16 mmx64.efi
-rwxr-xr-x 1 root root 1271672 Jul  9 14:16 MokManager.efi
-rwxr-xr-x 1 root root 1169992 Jul  9 14:16 shimx64.efi

```

To copy the folder and its contents, you need to use **cp -R**. You don't really need sudo if the destination is in your user space, since you have read permissions. To copy the folder back, you do need to use sudo, since your user has no write permissions.

for example,
```
dmn@Zotac:/boot/efi/EFI$ cp -R ubuntu ~/Desktop
```

Ran this...
```
waldo@11:~$ ls -l /boot/efi/EFI/ubuntu
total 3468
[COLOR="#FF0000"]drwxr-xr-x 2 root root [/COLOR] 4096 Mar 29 23:49 fw
-rwxr-xr-x 1 root root   64352 Jul 21 18:37 fwupx64.efi
-rwxr-xr-x 1 root root     126 Jul 29 10:08 grub.cfg
-rwxr-xr-x 1 root root 1133432 Jul 29 10:08 grubx64.efi
-rwxr-xr-x 1 root root 1168464 Jul 29 10:08 mmx64.efi
-rwxr-xr-x 1 root root 1169992 Jul 29 10:08 shimx64.efi
waldo@11:~$ 
```

There is a difference... number 2 in red line. 

Blue line did not work here.  Had to fuss it into form seen, my reply.  

Mike

---

### Post by Mike Krall on 2017-07-31
> **oldfred said:**
> [COLOR="#FF0000"]I looked at my history[/COLOR], but do not remember now. (Something about old in oldfred.)
But I include a backup of history in my rsync backups script.

[COLOR="#006400"]I found multiple commands where I tried to copy my ubuntu to mate, so not working. [/COLOR]
But last two commands I had to create the folder first. Not sure why, but have had a few cases where if multiple levels deep my rsync commands will not copy.

This tells my I installed mate, copied the ESP to a mate folder & restored my grub.cfg from xenial folder previous made (my main working install).
378  sudo mkdir /boot/efi/EFI/mate
  [COLOR="#0000CD"]379  sudo cp -a /boot/efi/EFI/ubuntu/* /boot/efi/EFI/mate
  380  sudo cp -a /boot/efi/EFI/xenial/grub.cfg /boot/efi/EFI/ubuntu[/COLOR]

Red line... Is that .bash_history, or ??? 

Green line... At /EFI, I GUI 'open in terminal' (did not create folder prior to)... then ran
```
sudo cp -a /boot/efi/EFI/ubuntu /boot/efi/EFI/test-ubuntu
```
Created /test-ubuntu directory, poplulated with complete and correct.

Deleted 'test-ubuntu' from /EFI

In terminal: ```
cd /boot/efi/EFI
sudo cp -a /boot/efi/EFI/ubuntu /boot/efi/EFI/test-ubuntu
```
Created /test-ubuntu... populated complete and correct

Thanks for Blue Lines, 'old fred'.  What is '*' in there for?  How come not in following line?

The weeds are calling...  last day... until the Russian Knapweed later in the fall... "Weeds 'R Us' 

Mike

---

### Post by Dennis N on 2017-07-31
In:
```
dmn@Zotac:/boot/efi/EFI/ubuntu$ ls -l
```
Everything before $ is part of the command prompt, and the prompt includes the current working directory. The actual command is after the $. I changed directories to /boot/efi/EFI/ubuntu before issuing the command **ls -l**.

---

### Post by oldfred on 2017-07-31
History is bash history, but command is:
history
I have this in my rsync backup. Paths exist.
history > ~/Documents/LinuxDocs/CurrentSys/asus_ar/history_$(date '+%Y-%m-%d_%H:%M:%S')_$(hostname).txt

But finding about half of the backups are 0 length, so need to debug a bit.
I have several current systems, one in ILL and one in Fla, so have different paths for each system.

I think * is redundant. I usually do not use it in my rsync commands. But I still have issues understanding paths in commands (slash or no slash). I have to regularly reread this:
 man rsync has explanation of trailing /.  trailing / copies contents:

---

### Post by Mike Krall on 2017-07-31
> **Dennis N said:**
> In:
```
dmn@Zotac:/boot/efi/EFI/ubuntu$ ls -l
```
Everything before $ is part of the command prompt, and the prompt includes the current working directory. The actual command is after the $. I changed directories to /boot/efi/EFI/ubuntu before issuing the command **ls -l**.

Boy, I sometimes just can't see stuff.  It's as plain as day if a person doesn't let their thinking get in the way.  Thank you.

Mike

---

### Post by Mike Krall on 2017-08-01
> **Dennis N said:**
> I would recommend not backing up in the EFI folder since you lose original and copy if the EFI folder goes down.
Meant to get here quicker...

Thanks for pointing out, 'Dennis N'. I'll have /EFI_backup in /mnt/data prior to install(s)... then on to external.

---

### Post by Mike Krall on 2017-08-01
Got elementaryOS installed after minimal copy of /EFI, etc. I'm going to have to work on the copy-backup-directory organizing later.  Spent a while there, fussing around, doing downloads.  When boot menu came up, the first time it ran elementaryOS.  I remembered a thing from somewhere... hitting any letter/number key stop countdown to auto-boot.  Works.  If all distros show in boot menu, this will work for me... clk. 'on' button... press key to pause at boot menu.

I've not got anything like progress done... copies, backups, showing elementaryOS /mnt/data, and on. 

Mike

---

### Post by oldfred on 2017-08-01
When you get more than one system installed, I like to run Boot-Repair's Summary Report, just for my own information and documentation. It helps to know what is installed where.

Boot-Repair uses bootinfoscript as part of its report and I run that as part of my rsync backup (the one that is not a real backup but just a copy to another drive, not versioned). Boot-Repair requires a gui so I do not run it as part of my backup.

---

### Post by Mike Krall on 2017-08-01
> **oldfred said:**
> When you get more than one system installed, I like to run Boot-Repair's Summary Report, just for my own information and documentation. It helps to know what is installed where.

Boot-Repair uses bootinfoscript as part of its report and I run that as part of my rsync backup (the one that is not a real backup but just a copy to another drive, not versioned). Boot-Repair requires a gui so I do not run it as part of my backup.

Thanks, 'oldfred'.  

I've got Boot-Info installed.  I'll put in Boot-Repair, too (should have already).  Have run it twice.  I can't figure out if it stores and/or where (seems so... but).  Where does yours go if you opt. other-than-link choice for report? 

Mike

---

### Post by oldfred on 2017-08-01
I have seen Reports with the folders in the ESP. I think those are from flash drive installers, so there is a saved copy on system.
On my system I have a /var/log/boot-sav folder. And then log folder inside that. (I see I should house clean out some older copies). I normally regularly house clean some log files.

---

### Post by Mike Krall on 2017-08-02
> **oldfred said:**
> I have seen Reports with the folders in the ESP. I think those are from flash drive installers, so there is a saved copy on system.
[COLOR="#0000CD"]On my system I have a /var/log/boot-sav folder. And then log folder inside that. [/COLOR][COLOR="#B22222"](I see I should house clean out some older copies)[/COLOR]. I normally regularly house clean some log files.

Me too, blue then red.  A person just dumps older dates? 

Mike

---

### Post by oldfred on 2017-08-02
Sometimes I save some old info and newest, but generally as info gets old, it is not useful anymore.

---

### Post by Mike Krall on 2017-08-03
And if a person collected enough of them, could put them out at a yard sale later, right? 
-----------------------------------------------------------------------------------------

So, I've been knocking around in & with elementaryOS Loki... running 4.10.0.28 kernel after post-install update.  I've got stories to tell but not here/now.  It took me a while to get "first things first" in order.  Edited /fstab to mount /sda4 (/mnt/data).  Edited /fstab to 'defaults' permissions (/sda1... /boot/efi).  Got cd /mnt/data... mkdir /Documents... etc., and cd,  'rm -rf  Documents/... etc. done, then symlinks built via 'oldfred' all-in-one script. Ran BootInfo and saved it in 16.04 and 'cp' to /mnt/BootInfo (Boot Info made that directory and /boot-sav in /mnt). 

There's other stuff to do in elementaryOS... Thunderbird, etc.  Besides that, I'm going to have to figure out what their point is.  It's a lot different approach... or is to me... and I haven't got a clue why it is put together the way it is.  I hadn't realized how well I get around in Ubuntu (that's relative to me).  

Anyhow, there is menuentry stuff to do and I don't know where to start or how to go...

Mike

---

### Post by oldfred on 2017-08-03
Copy your history to a file & save it elsewhere, like in your /mnt/data partition.
You can then edit it, remove sudo, add she-bang/bash as first line and then be able to reinstall and reconfigure almost automatically. Script may work on other installs or need changes depending on differences.

---

### Post by Mike Krall on 2017-08-03
> **oldfred said:**
> Each install has its own fstab, so you may want to back it up to have any manually edited additions like your data partition, but should not need and would not copy one fstab to another system as then you mount incorrect / (root).

I see it (fstab).  I've got local copies of original, of /mnt/data and 'defaults' change.   

I saw somewhere a path of yours */mnt/backup*... also a */mnt/data/Documents/LINUX_DOCS* (or something like that).  I noticed I've generated looonng paths in /mnt/data... folders in folders in folders.  Spent some time today to simplify.  Would you say what kinds of things go in your /mnt/backup... and did you do a permission change on it like /fstab for /boot/efi?  What things in Documents/LINUX_DOCS... others ?  I'm just looking for ideas-with-experience. 

In /EFI I *"sudo cp -a..."* the 'ubuntu overwrite' into (first case) /EFI/elementary.  Makes it's own folder.  Then *"sudo cp -a..."* the whole folder to */mnt/data/Documents/LINUX_DOCS/EFI-backup*... then go in */EFI-backup* and 'cp...' out, and name, grub.cfg file (both outside and inside with # line at top of "three lines").  I'll edit Ubuntu 16.04 grub.cfg (in */EFI/ubuntu-16-unity*) back to */EFI/ubuntu* one of these days as I do want it at top of boot menu over the long haul. Right now, I'm happy to have boot menu pop up and hit Enter for elementaryOS or 'letter key'... arrow dn... Enter for 16.04. 

I'll get the .bash_history copied into somewhere in /mnt/data.  I ran a search on shebang/bash (got nearest as shebang/bin/bash along with other variations).  Read a half dozen links and I'm here to tell you, you have more faith in me than I do...  =]  
I roughly understand the value and maybe I'll get it figured out.  It will take help, though... not now... not here.

Search results...
[https://www.google.com/search?newwindow=1&client=ubuntu&hs=BqO&q=what+is+shebang/bash+in+Linux&spell=1&sa=X&ved=0ahUKEwibpIey7LvVAhUhh1QKHTVPBq8QBQgkKAA]("https://www.google.com/search?newwindow=1&client=ubuntu&hs=BqO&q=what+is+shebang/bash+in+Linux&spell=1&sa=X&ved=0ahUKEwibpIey7LvVAhUhh1QKHTVPBq8QBQgkKAA")

To do the shebang/bash thing... might be I should do another or two installs 'by hand'... I'd learn something... have to get better organized (tough work)... have a better *.bash_history* in the end, maybe.

Too long, with more to say/ask...

Mike

---

### Post by oldfred on 2017-08-03
I have ended up using sudo when I should not have and permissions or ownership of some files in my /mnt/data are not right.
I run this occasionally. These are the same as what /home has.
       sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data 

Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER 
      
 Seems like a better way as you have more control over what is executable. Isee post #8 & 10 by morbius1.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369) 
    
I have ended up with some longer paths. But it is how I have things organized for now.

I manually installed and configured multiple times. Since most were Ubuntu and flavors of Ubuntu, I realized I was doing the same thing over & over. Is not that what computers are for, saving us from having to do things over & over? But I learned by doing that.
I then tried to do as much as possible by command line, where before I was using gui, like to install apps I used synaptic before (still do on occasion).

[https://en.wikipedia.org/wiki/Shebang_%28Unix%29](https://en.wikipedia.org/wiki/Shebang_%28Unix%29)

 Lots of links on scripting in this thread
[http://ubuntuforums.org/showthread.php?t=1893106](http://ubuntuforums.org/showthread.php?t=1893106) 

Oldfred's install scripts, my bash files, but constantly changing after/during every install. Also have to be made executeable.
[https://ubuntuforums.org/showthread.php?t=2347811&p=13588662#post13588662](https://ubuntuforums.org/showthread.php?t=2347811&p=13588662#post13588662)

---

### Post by Dennis N on 2017-08-04
I find it useful to make bookmarks for various often-used locations on my data partition. See attached screenshot of Thunar file manager. In sidebar Places, are 'gnumeric' 'webpages' 'music' 'Common-Files' all of which are bookmarked locations on my data partition. 'Common-Files' is root of data partition. Having 'music' bookmark makes it simple to access my music collection from audacious. 'webpages' is the home page of my local web site.

Unlike you guys I don't use symbolic links from home folders to data partition, relying instead on my bookmarks. Also, I find in daily work I am often just saving and loading files from there, and user-friendly applications remember the most recent save/load path.

I did make a bind mount of Common-Files in my home folder partly for faster access to data with terminal, either on this computer or remotely from another computer. You can see the bind mount in main window in the screenshot.

Besides reading Dedoimedo's Loki review, I am not familiar with Elementary Loki Distro. Good luck with it. Loki was a Viking god (learned from watching 'Vikings').

---

### Post by Mike Krall on 2017-08-04
Read and noted.  Off to town until late.  

Thanks, 'oldfred'... thanks, 'Dennis N'

Mike

---

### Post by Mike Krall on 2017-08-05
> **oldfred said:**
> I occasionally still use gksudo gedit, but now suggest sudo nano.

Nano will run when you have gui issues if you can still boot to terminal so worthwhile to know nano. It is part of every standard install as far as I know.

To manually mount.
 sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod after mounting either manually or via fstab
sudo chown $USER:$USER /mnt/data
#sudo chmod 775 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
#Edit fstab with your UUID:
[COLOR="#FF0000"]sudo blkid -o list
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab [/COLOR]

Be sure to unmount if manually mounted first, and run this to be sure edit is valid. If it just returns with no errors then the edit of fstab is ok & it remounted everything.

typical entry with my UUID:
      
 UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext4         auto,users,rw,relatime               0  2 

[COLOR="#FF0000"]#Verify entry is ok, if no errors it is:
sudo mount -a[/COLOR]

Post # 67 link (is that above)
[https://ubuntuforums.org/showthread.php?t=2355551&page=7&p=13630043#post13630043]("https://ubuntuforums.org/showthread.php?t=2355551&page=7&p=13630043#post13630043")

Two things:

* I'm sorry... can't find the link (it's in there somewhere)... was looking into "cp".  Ran into a site saying if a config file was to be copied (specifically mentioned /etc/fstab) the form should be "cp -w /etc/fstab.  So there was no chance of "wrapping" (I think...).  Is that old, and is different now, 
or ???

*  First time running red lines (original mounting of /mnt/data (my sda4), all went as expected.  Doing "Edit /fstab" for both elementaryOS and KDE Neon... "sudo nano /etc/fstab" (for for both auto-mount of /mnt/data and /boot/efi permission change to "defaults") the return on "sudo mount -a" was like "there is no /mnt/data".  In both cases, a reboot, made /mnt/data an auto mount.  I'd like to know why... that is... what am I not doing or "seeing" correctly?

Mike

[COLOR="#FF0000"]Edit: 8-7-2017[/COLOR]... totally wrong on "cp" section in "Two things:" above.  Reference to "-w" is in this:  [https://wiki.gentoo.org/wiki/Nano/Basics_Guide]("https://wiki.gentoo.org/wiki/Nano/Basics_Guide")

---

### Post by oldfred on 2017-08-05
In each install you have to make the mount point before you can mount to the mount point.
Linux does not auto make mounts, whether manual or in fstab.
Windows auto makes mounts, but you can only use d:, e: f: etc which are not very descriptive of what you may have.

Do not off hand know cp -w, I use cp -a to preserve ownership, if that is what I want.
I only backup fstab to have entries, so I can copy if needed into a new install.
But my script auto creates mount & copies mount into fstab. I have run script more than once to fix something else and then had mount twice which system did not like.

---

### Post by Dennis N on 2017-08-05
> the return on "sudo mount -a" was like "there is no /mnt/data". In both cases, a reboot, made /mnt/data an auto mount. I'd like to know why... that is... what am I not doing or "seeing" correctly?

All this is normal. It's how Ubuntu behaves: 1) a **mount** command issued in terminal will not work unless the mount point is created first. But, 2) on mounting partitions in /etc/fstab on startup, Ubuntu creates the mount point if it does not exist. This is the only time it will automatically create one. The folder created is permanent.

_This behavior is definitely not universal in Linux_. Other Linux OSes (maybe all?) require you to have an existing mount point before mounting partitions in /etc/fstab at startup, or in terminal (with mount command), will succeed. 

----------------------------------
Experiment to test this auto-creation (I will use my computer and Lubuntu 17.04 as test subject). Try it yourself - takes just a minute.

I edit existing mount line in /etc/fstab for my data partition from:
[FONT=Courier New]UUID=c3121154-ee33-418b-8c43-10377841e3c2 /mnt/Common-Files ext4 defaults 0 2[/FONT]
to:
[FONT=Courier New]UUID=c3121154-ee33-418b-8c43-10377841e3c2 /mnt/MyData ext4 defaults 0 2[/FONT]
At this point, the folder /mnt/MyData does not exist. 
Save and reboot.
Result: system created the new mount point /mnt/MyData, and mounted this filesystem.
-----------------------------------

---

### Post by Mike Krall on 2017-08-06
> **oldfred said:**
> [COLOR="#800080"]In each install you have to make the mount point before you can mount to the mount point.
[/COLOR]Linux does not auto make mounts, whether manual or in fstab.
Windows auto makes mounts, but you can only use d:, e: f: etc which are not very descriptive of what you may have.

[COLOR="#B22222"][COLOR="#0000CD"]Do not off hand know cp -w, I use cp -a to preserve ownership, if that is what I want.[/COLOR][/COLOR]
I only backup fstab to have entries, so I can copy if needed into a new install.
But my script auto creates mount & copies mount into fstab. I have run script more than once to fix something else and then had mount twice which system did not like.

Purple: ...Is that, *"sudo mkdir /mnt/data"* alone, or needing *'chown'* and* 'chmod'*, too?  I didn't do any of that.  And when /mnt/data needs permissions rectified, all of* "mkdir"*, *"chown"*, and *"chmod"* are done?  Just now checked permissions on all 3-distros and are the same... /mnt = root:root, /data = owner:group. 

Blue: ...Found the *"sudo cp -w...."* reference, 'oldfred'... last modified Oct 2016... 
[https://wiki.gentoo.org/wiki/Nano/Basics_Guide]("https://wiki.gentoo.org/wiki/Nano/Basics_Guide")

Seems to me a person could "sudo cp -aw...", or either-of singly or none... depending.

Mike

Edit: 8-7-2017... "Blue" section above Does Not refer to "cp -w", but to editing with nano in some instances with "-w". See this:  [Edit: 8-7-2017... totally wrong on "cp" section in "Two things:" above. Reference to "-w" is in this:]("Edit: 8-7-2017... totally wrong on "cp" section in "Two things:" above. Reference to "-w" is in this:")

---

### Post by Mike Krall on 2017-08-06
I'm getting behind, and I've got both reasons and excuses...  

I've got to finish the KDE Neon put-in (copy-backup, etc.)  I spent time using both elementaryOS and Neon OS... bad idea.  I can do that anytime... as in, not now. I'm going to see what I need to ask from recent... do some reading from recent (maybe ask about that)... try to figure menuentry.  I did notice there are menuentries for all three OS's now.  I'll see if 30_prober looks the same from all three points of viewing... I believe it should, but ???  Anyhow... good night...

Mike

Edit:  Look at menuentries in the OS's  /boot/grub/grub.cfg... not 30_prober found in /etc/grub.d.

Edit:  In /boot/grub/grub.cfg, the menuentry for OS being run is in 10_Linux.  In that OS's /boot/grub/grub.cfg, all machine OS's, all of mine are in 30_prober section (all Ubuntu-based...3-at-present).

---

### Post by Dennis N on 2017-08-07
> Seems to me a person could "sudo cp -aw...", or either-of singly or none... depending.

cp with -w gives me an error. Also, man page for cp doesn't show -w as an option.

```
dmn@Sydney:~/work/test2$ cp -w file1 file2
cp: invalid option -- 'w'

```

same when combined with a valid option -  and no copy was made.

```
dmn@Sydney:~/work/test2$ cp -uw file1 file2
cp: invalid option -- 'w'
```

best regards.

---

### Post by Mike Krall on 2017-08-07
'Dennis N'...  I'm really sorry.  "-w" has *Nothing* to do with "cp"... it's a thing about editing with nano... as in "sudo nano -w..." This link:  [https://wiki.gentoo.org/wiki/Nano/Basics_Guide]("Edit: 8-7-2017... totally wrong on "cp" section in "Two things:" above. Reference to "-w" is in this:  [URL="https://wiki.gentoo.org/wiki/Nano/Basics_Guide")

I've gone back and edited with "Edit note" to other incorrect references and put above link there, too. Again... apologies...   

Mike

---

### Post by Mike Krall on 2017-08-15
Well, wrote and forgot to post again.  Is that like not *sudo update-grub*...ing?

'Dennis N'... would you show me some of your custom menuentries, please... like Linux Mint Xfce and Manjaro Xfce?  

In the OS's I've installed, I've looked at each in /boot/grub/grub.cfg... similar but (excluding title line) not all the same... and I recall the advice posted from Grub2/CustomMenus, * "The surest way to build a custom menu is to copy one or more working menuentries from the grub.cfg file."*  Yet, it seems like the 'menuentry examples' I've seen are much less complex. (I wonder if the "if, then, else, fi" lines are not necessary and/or shouldn't be in?)  

I'm wondering a thing:

*  Does installing an "other than Ubuntu OS" and putting it's boot files into /sda1 (my /boot/efi partition) cause problems with "maintenance-free menuentries"... Or rather,  unnecessary complications.   

Mike

---

### Post by oldfred on 2017-08-15
too much info on grub2.
 Grub2 wiki page - also see links to additional pages 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 

The entries in the ESP would be for booting directly from UEFI boot menu, f12 on my system, but varies by vendor.
Grub2's os-prober finds other boot files, but you are only using one default entry in UEFI to load grub and then that grub can boot other installs. Its just when you use specific copy of boot stanza it usually is for one kernel like what os-prober finds. But that one kernel may get updated and then you have to manually update entry in first grub like you would have to re-run os-prober in default boot grub menu.

Standard boot configuration stanza includes lots of details, paths, UUIDs and other info.
The simplified custom entry uses device (which can lead to issues if device varies) and uses a link in / to the boot most current kernel in grub in that install. That then has all the updated info.

I have skipped SATA port and then with a flash drive still plugged in, my sdb drive becomes sdc. That has then changed what works. I now realize that when it happens and manually edit entry when booting.

---

### Post by Dennis N on 2017-08-15
> 'Dennis N'... would you show me some of your custom menuentries, please... like Linux Mint Xfce and Manjaro Xfce? 
Hello again, glad to see you are back at it.

I create one file in **/etc/grub.d** for each OS I want in my grub menu, as shown in post #166. Also, see menu appearance on monitor in post #174.

To make files, I first copy **/boot/grub/grub.cfg** and **/etc/grub.d/40_custom** to a work folder in **~/home**.

Work here based on the directions at: [https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Assuming that's done, I look for Linux Mint in the grub.cfg copy. I copy the entry starting with the line beginning 'menuentry' down to and including the closing bracket in the last line. Then paste this into 40_custom. Then I edited the title in the first line in single quotes right after menuentry to 'Mint 17.3 MATE     (sdb8)'. Then, the lines starting with 'linux' and 'initrd' are edited to look like what you see here. This step is what makes it maintenance free. Then I saved this to a file '07_r-mint-mate-173' in /etc/grub.d, as you see in post #166. You then need to make the file executable. When done, run sudo update-grub to generate new grub menu with these custom entries.

Below: Copy of file for custom Mint menu entry:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Mint 17.2 MATE     (sdb8)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5b573f23-5e58-4cfd-9dfe-3babdb6c840b' {
	insmod part_gpt
	insmod ext2
	set root='hd1,gpt8'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt8 --hint-efi=hd1,gpt8 --hint-baremetal=ahci1,gpt8  5b573f23-5e58-4cfd-9dfe-3babdb6c840b
	else
	  search --no-floppy --fs-uuid --set=root 5b573f23-5e58-4cfd-9dfe-3babdb6c840b
	fi
	linux	/vmlinuz root=UUID=5b573f23-5e58-4cfd-9dfe-3babdb6c840b ro  quiet splash $vt_handoff
	initrd	/initrd.img
}

```
> Yet, it seems like the 'menuentry examples' I've seen are much less complex. (I wonder if the "if, then, else, fi" lines are not necessary and/or shouldn't be in?) 

I think more content is there for specific install situations which change over time. Even the example in the directions article is simpler than what we have now. Since I just copy and paste the whole menu entry as suggested in the help article, no reason not to include it all. I would not use a bare bones entry with no UUIDs, like:

```
menuentry "Ubuntu on sda3" {
set root=(hd0,gpt3)
linux /boot/vmlinuz-4.4.0-89-generic.efi.signed root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-4.4.0-89-generic
}

```

As written, I don't think this entry will work with LVM installations (since they are not on their own separate partitions). Also, without UUIDs, this would fail if your partition got renumbered. And it may work for an Ubuntu type OS but may fail for other Linux, like Fedora or Manjaro or Open SUSE. 

Are you installing Manjaro in UEFI and booting it from Ubuntu grub? Then you need to get Manjaro's menuentry from Manjaro's grub.cfg and make a custom menu file with that, same technique as above, except you must not change the linux and initrd lines.
 
Below: Copy of the file for custom entry in Ubuntu grub to boot Manjaro (with kernel 4.4). You cannot shorten the linux and initrd lines as done in the Ubuntu example.

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Manjaro XFCE       (sdb9)' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a5a5aab2-2f6e-4cfc-87d8-7e0ba62ebad6' {
	savedefault
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd1,gpt9'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt9 --hint-efi=hd1,gpt9 --hint-baremetal=ahci1,gpt9  a5a5aab2-2f6e-4cfc-87d8-7e0ba62ebad6
	else
	  search --no-floppy --fs-uuid --set=root a5a5aab2-2f6e-4cfc-87d8-7e0ba62ebad6
	fi
	echo	'Loading Linux 4.4.5-1-MANJARO x64 ...'
	linux	/boot/vmlinuz-4.4-x86_64 root=UUID=a5a5aab2-2f6e-4cfc-87d8-7e0ba62ebad6 rw  quiet splash resume=UUID=9b8e3bd1-e837-4bf0-b869-fac060d6ebf2
	echo	'Loading initial ramdisk ...'
	initrd	/boot/intel-ucode.img /boot/initramfs-4.4-x86_64.img
}

``` 

That should get you started for now on a custom menu. 

P.S. 
There is an optional technique valuable in some cases, learned from columnist J.A. Watson of ZDNet that I have started using, but will save that for another time.

---

### Post by oldfred on 2017-08-15
cavsfan posts his screen shots & menus from the Customized menu 
You can start at back & work forward. And see first post.

[https://ubuntuforums.org/showthread.php?t=2076205&page=44](https://ubuntuforums.org/showthread.php?t=2076205&page=44)

---

### Post by Mike Krall on 2017-08-17
And once again... wrote and didn't post... from two nights ago:

Took a quick look, but it's gone too late to do anything with this tonight. (I've been chasing the Solus Grub2 boot problem since before dinner.)  

Every once in a while I look at the help I've gotten here with a little wonderment.  Thank you 'oldfred'.  Thank you 'Dennis N'.  I mean really... thank you. 

Mike

---

### Post by oldfred on 2017-08-17
You are welcome.

I find using Boot-Repair's summary report critical for understanding what is where & details. Also good just to have current copy included in backup for documentation of system configuration.

---

### Post by Mike Krall on 2017-08-18
I've got Boot-Info reports in /mnt/data... first one, pre "other OS's", and present... and hard-copy "process" note, to run and edit-to-current Boot-Info.  

I've been reading/re-reading all Grub2 and "menuentry" pages since pages-back when first mentioned... over and over.  Right now I'm reading (back to front) 'oldfred's' forum link from post #237.  When that gets done, I'll likely re-read the associated Ubuntu Wiki on same.  Then some questions on differences in custom menu form (w/ maintenance-free).  

It's Friday.  I'm off to town for the day.  Tonight the "Eclipse-ers" start coming in (we are 50 miles from path). It's going to be busy here for a while.  We'll see if a person can make time in the middle of too many people in too small a place for too long a time, or not. 

Mike

---

### Post by Mike Krall on 2017-08-23
No time made... lots of people and fun instead... plus 1 minute and eight seconds of amazing...  

I shouldn't shotgun a bunch of questions... bad form... counter productive... but I do so want to.

This is the plan to build custom menuentry around.

Ubuntu-unity LTS (now and following versions GRUB_DEFAULT=0. I'll edit it back into /boot/efi/EFI/ubuntu at some point.
Other OS installed and set up now:  ElementaryOS... KDE Neon... LinuxMint-Cinnamon... LinuxMint-Xfce

I'm going to take out LinuxMint-Xfce and put in Manjaro-Xfce... Ubuntu Budgie (can't use Solus Linux because it doesn't seem to work now with multi-distro set ups)... CentOS 7-Gnome.  Yeah, I know, I've got no business messing with either of CentOS or Manjaro.

> [COLOR="#FF0000"]Are you installing Manjaro in UEFI and booting it from Ubuntu grub?[/COLOR] Then you need to get Manjaro's menuentry from Manjaro's grub.cfg and make a custom menu file with that, same technique as above, except you must not change the linux and initrd lines.

Below: Copy of the file for custom entry in Ubuntu grub to boot Manjaro (with kernel 4.4). You cannot shorten the linux and initrd lines as done in the Ubuntu example.

Code:
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Manjaro XFCE       (sdb9)' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a5a5aab2-2f6e-4cfc-87d8-7e0ba62ebad6' {
	savedefault
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd1,gpt9'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt9 --hint-efi=hd1,gpt9 --hint-baremetal=ahci1,gpt9  a5a5aab2-2f6e-4cfc-87d8-7e0ba62ebad6
	else
	  search --no-floppy --fs-uuid --set=root a5a5aab2-2f6e-4cfc-87d8-7e0ba62ebad6
	fi
	echo	'Loading Linux 4.4.5-1-MANJARO x64 ...'
	linux	/boot/vmlinuz-4.4-x86_64 root=UUID=a5a5aab2-2f6e-4cfc-87d8-7e0ba62ebad6 rw  quiet splash resume=UUID=9b8e3bd1-e837-4bf0-b869-fac060d6ebf2
	echo	'Loading initial ramdisk ...'
	initrd	/boot/intel-ucode.img /boot/initramfs-4.4-x86_64.img
} 

'Dennis N'... 

*  Red line - I am intending to put Grub into /sda1 - /efi/boot in all installs. (I've got no hard reasoning to do that.  It's what I assumed was a 'correct' method.) Is that what you mean? 

*  Is the Manjaro menuentry structured the way you've shown because it is a rolling release... an entry that doesn't/can't change... Or ? 

*  If you can point me to J.A. Watson 'alternative method', I'd appreciate it.  Not to do... to have in collected links.

Mike

---

### Post by oldfred on 2017-08-23
With UEFI you will have the entry in the ESP - efi system partition, but then to use that have to interrupt normal boot with f10 or f12 to get UEFI boot menu.

We normally then have os-prober find other installs and add then to the default grub menu. But have to reboot into default install and run sudo update-grub to get new kernels installed in other install(s).

But if using the Maintenance free method documented by cavsfan, you turn off os-prober and add your own entries to 40_custom in default boot install. That works for Debian based installs, but I do not know about other distributions. It works for Debian based installs as with every kernel update, they also update a link in / that we then use the link to boot from default install/grub, so we always are booting most recent kernel in our other installs.

If directly copying a boot stanza, you have to update grub in that install, normally part of kernel update, and then reboot into default grub's system and edit boot stanza with new kernel. If none of the other installs have the link in /, it then may be easier just to leave os-prober turned on. I have only installed flavors of Ubuntu and mostly just every 6 month release of Ubuntu.

---

### Post by Mike Krall on 2017-08-23
> **oldfred said:**
> [COLOR="#FF0000"]With UEFI you will have the entry in the ESP - efi system partition, but then to use that have to interrupt normal boot with f10 or f12 to get UEFI boot menu.[/COLOR]

We normally then have os-prober find other installs and add then to the default grub menu. But have to reboot into default install and run sudo update-grub to get new kernels installed in other install(s).

But if using the Maintenance free method documented by cavsfan, you turn off os-prober and add your own entries to 40_custom in default boot install. That works for Debian based installs, but I do not know about other distributions. It works for Debian based installs as with every kernel update, they also update a link in / that we then use the link to boot from default install/grub, so we always are booting most recent kernel in our other installs.

If directly copying a boot stanza, you have to update grub in that install, normally part of kernel update, and then reboot into default grub's system and edit boot stanza with new kernel. If none of the other installs have the link in /, it then may be easier just to leave os-prober turned on. I have only installed flavors of Ubuntu and mostly just every 6 month release of Ubuntu.

One thing at a time...

Red line:  Right now (all Ubuntu) I get list of OS + Advanced line right after ASUS firmware coming up. "Any letter/numeral" stops count-down to auto boot of last install (three line entry in /boot/efi/EFI/ubuntu/grub.cg).  As kernel updates have been available and accepted, I find them in /boot/grub/grub.cfg  (either /10_linux or /30_os-prober).  I typically remove any but two most recent (synaptic package manager) and note changes in /boot/grub/grub.cfg

Mike

---

### Post by oldfred on 2017-08-23
You have two boot managers, UEFI & grub.
Boot manager is the menu. 
Grub is both the menu & a boot loader.
UEFI has a default boot which then is your default grub install, usually last system installed.
You can see UEFI default:
sudo efibootmgr -v

You should never be editing grub.cfg as every kernel update or sudo update-grub replaces it. 
You do edit grub's configuration files and then run update-grub to include those changed in grub.cfg.
 sudo nano -B /etc/default/grub 

 sudo nano -B /etc/grub.d/40_custom 


Grub then has a default boot, generally first line in grub's menu, but can be set in /etc/default/grub to be any line, either by line number or exact description.

---

### Post by Dennis N on 2017-08-23
> Red line - I am intending to put Grub into /sda1 - /efi/boot in all installs. (I've got no hard reasoning to do that. It's what I assumed was a 'correct' method.) Is that what you mean? 

That will work. Your operating systems will end up getting booted from the grub menu of the OS that's first in the EFI boot order. 

> Is the Manjaro menu entry structured the way you've shown because it is a rolling release... an entry that doesn't/can't change...

Rolling release is not the reason. Linux distros will have differences in how the system is put together, hence some differences in grub menu entries. What I do know is that if you use Ubuntu's OS prober to make a grub menu entry for Manjaro, it will fail to boot on UEFI systems. Manjaro will boot Ubuntu, however. 

I use Manjaro XFCE as #1 in efi boot manager boot order and once booted, it subsequently can boot anything else. I've had it in use as such since Oct. 2015.

Manjaro custom menu entry will not need to be edited unless you switch kernel version, like from 4.4 series to 4.9. Any switch is a user choice. The example menu entry boots any 4.4 kernel.   

Re: J.A. Watson - don't have any specific link available to post. He wrote many columns on multi-booting you can peruse. Just Google to find his work. But, I would recommend sticking to the methods we are discussing here until they are down pat before experimenting further. Watson's goal is making his multi-boot setups maintenance free for a wider range of distros. Ubuntu-family custom grub menu entries can easily be made maintenance free by use the special modification to linux and initrd lines in their menu entry as described in post #236.

---

### Post by Mike Krall on 2017-08-24
Thank you both... every little bit helps.  

I'm going to lose the next 5 - 6 days here... no computer access in the mountains... and I'm sorry about that... =[

Mike

---

### Post by Mike Krall on 2017-09-28
"When you come to a fork in the road, take it."...* Yogi Berra*

The distance between Point A and Point B can get really long if a person wanders off the straight line...

If you get in way over your head... stop.  Take a good look around.  Move to the light.

I went to RHEL and lived!  I really wasn't there long, but I might have died...  =] 

Some stories... not questions... 

I put in CentOS 7 because of a (years long) series of posts by Dedoimedo.  It's an interesting idea (and I was looking for an OS with default Gnome DE)
[http://www.dedoimedo.com/computers/centos-6.html]("http://www.dedoimedo.com/computers/centos-6.html")
[http://www.dedoimedo.com/computers/centos-perfect-desktop.html]("http://www.dedoimedo.com/computers/centos-perfect-desktop.html")
[http://www.dedoimedo.com/computers/centos-pimpage.html]("http://www.dedoimedo.com/computers/centos-pimpage.html")
[http://www.dedoimedo.com/computers/centos-pimpage-more.html]("http://www.dedoimedo.com/computers/centos-pimpage-more.html")
[https://www.dedoimedo.com/computers/centos-6-2-ssd.html]("https://www.dedoimedo.com/computers/centos-6-2-ssd.html")
[http://www.dedoimedo.com/computers/centos-ssd-boot-time.html]("http://www.dedoimedo.com/computers/centos-ssd-boot-time.html")
[http://www.dedoimedo.com/computers/centos-7.html]("http://www.dedoimedo.com/computers/centos-7.html")
[http://www.dedoimedo.com/computers/centos-7-perfect-desktop.html]("http://www.dedoimedo.com/computers/centos-7-perfect-desktop.html")
[https://www.dedoimedo.com/computers/dual-boot-windows-7-centos-7.html]("https://www.dedoimedo.com/computers/dual-boot-windows-7-centos-7.html")
[http://www.dedoimedo.com/computers/centos-7-perfect-desktop-more.html]("http://www.dedoimedo.com/computers/centos-7-perfect-desktop-more.html")
[https://www.dedoimedo.com/computers/lenovo-g50-centos-kde.html]("https://www.dedoimedo.com/computers/lenovo-g50-centos-kde.html")
[https://www.dedoimedo.com/computers/lenovo-g50-centos-gnome.html]("https://www.dedoimedo.com/computers/lenovo-g50-centos-gnome.html")
[https://www.dedoimedo.com/computers/lenovo-g50-centos-xfce.html]("https://www.dedoimedo.com/computers/lenovo-g50-centos-xfce.html")
[https://www.dedoimedo.com/computers/centos-7-perfect-theme.html]("https://www.dedoimedo.com/computers/centos-7-perfect-theme.html")

So, down the road I go.  Put in CentOS one evening... mess with it a very little bit... get up the next day and it's "broke" (won't boot to other than giant screen)... won't boot other OS's... "can't find linux or initrd".  I got into it through F2 (my ASUS equivalent of F10 - F12)... boot anything into a boot menu then boot CentOS. Can also get into it via "Sub Menu" if I pick the last of 3 in the list (starts into a giant screen form then quits).  The primary menuentry and the first in "sub menu" have [COLOR="#FF0000"]rescue[/COLOR] in their linux lines... and there are some other oddments... things supposed to be there, but not.    

Whatever...  I'm leaving CentOS in it's little hole... not connected to separate data partition system.  I've dug around a bit... looked at some of the differences from Debian, a little of "The Server World", chased the "won't boot" question.  One of these days I'll pursue either of:
[https://www.dedoimedo.com/computers/grub2-fedora-command-not-found.html]("https://www.dedoimedo.com/computers/grub2-fedora-command-not-found.html")
Or...
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/installation_guide/chap-uninstall-rhel#sect-uninstall-rhel-dual-linux-x86]("https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/installation_guide/chap-uninstall-rhel#sect-uninstall-rhel-dual-linux-x86")... continue or not. 

More story...

I read all of 'Cavsfan''s custom grub menu thread... it's 46 pages now, 'oldfred'... back to front (as suggested) and Post #1 (once at the beginning... once at the end).  

From 'oldfred' mention of "*too much info on grub2.  Grub2 wiki page - also see links to additional pages*"  I went to all (again) and saw all (again).  

Saw 'Cavsfan' synopsis of  the above mentioned thread (again and again):
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")

Spent weeks with the last few pages of this thread and this 'Dennis N' provided link in my Chromium tabs...
[https://help.ubuntu.com/community/Grub2/CustomMenus]("https://help.ubuntu.com/community/Grub2/CustomMenus").... read them, too.

So, I've got a question... it's rhetorical, though.  When a person gets around cows, they get sh*t on them... and it sticks.  How come Linux don't work like cows?
   
-----------------------------------------------------------------------------------

I put Manjaro in (nice installer!) and got it hooked to /mnt/data... got copies/backups of the basic stuff.  It sits at the front of the boot menu and brought along it's own custom boot menu background and function.  Restarting has the last-used OS highlighted in the boot menu.  Nice... especially since I goto Ubuntu 16 LTS a lot. 'Dennis N' mentioned Manjaro will boot other Linux OS (hopefully CentOS, too, if fixed) and I figure having it run the boot (rolling release OS, too) is a sound base for a separate data partition system.       

Made a place in /home for 40_custom and /boot/grub/grub.cfg.  Copied Manjaro menuentry (all).  Then deleted because I had picked them up from Ubuntu 30_os-prober (learned from 'oldfred' inference and made it stick finding menuentry difference between CentOS viewed in Ubuntu 30_os-prober and CentOS 10_linux).   I'm going to Manjaro-world now to figure out what constitutes "sudo update-grub" there... then do it... then copy all 10_linux menuentry into /mnt/data... then see if I can find it after "save as"  06_custom.    

Mike

---

### Post by HermanAB on 2017-09-28
Note that multiboot is very 20th century and probably should not be encouraged.

The 21st century solution is to use a virtualizer (KVM, Virtualbox, Virtualbox...).  KVM is built into the Linux kernel and if your hardware supports it then that is best.  If not, then Virtualbox is probably the easiest.

---

### Post by Mike Krall on 2017-09-28
Early on in this thread, others mentioned virtualizer method.  I'd done a lot of looking around prior to starting the thread.  Simply, I understood the discussions surrounding separate data partitions better than I understood those surrounding virtual multi-boots.  Might be I'll learn more about virtual systems as I go along.  Maybe next time I'll see the advantage clearly.  

Mike

---

### Post by Dennis N on 2017-09-28
> I put Manjaro in (nice installer!) and got it hooked to /mnt/data... got copies/backups of the basic stuff. It sits at the front of the boot menu and brought along it's own custom boot menu background and function. Restarting has the last-used OS highlighted in the boot menu. Nice... especially since I goto Ubuntu 16 LTS a lot. 'Dennis N' mentioned Manjaro will boot other Linux OS (hopefully CentOS, too, if fixed) and I figure having it run the boot (rolling release OS, too) is a sound base for a separate data partition system.
Glad to learn you are making progress! Manjaro is excellent choice to control booting. I use the XFCE version myself. 

> Made a place in /home for 40_custom and /boot/grub/grub.cfg. Copied Manjaro menuentry (all). Then deleted because I had picked them up from Ubuntu 30_os-prober (learned from 'oldfred' inference and made it stick finding menuentry difference between CentOS viewed in Ubuntu 30_os-prober and CentOS 10_linux). I'm going to Manjaro-world now to figure out what constitutes "sudo update-grub" there... then do it... then copy all 10_linux menuentry into /mnt/data... then see if I can find it after "save as" 06_custom. 
Sorry, I don't understand what you did here, so can't comment. Manjaro has an excellent forum. I am a member there too.

> I'm going to Manjaro-world now to figure out what constitutes "sudo update-grub"
This command is also valid in Manjaro.

---

### Post by Mike Krall on 2017-09-30
Sorry 'Dennis N'...

This:
> *Made a place in /home for 40_custom and /boot/grub/grub.cfg. Copied Manjaro menuentry (all). Then deleted because I had picked them up from Ubuntu 30_os-prober (learned from 'oldfred' inference and made it stick finding menuentry difference between CentOS viewed in Ubuntu 30_os-prober and CentOS 10_linux). I'm going to Manjaro-world now to figure out what constitutes "sudo update-grub" there... then do it... then copy all 10_linux menuentry into /mnt/data... then see if I can find it after "save as" 06_custom.*

Sorry, I don't understand what you did here, so can't comment. Manjaro has an excellent forum. I am a member there too.

You mentioned in Post #236...  [http://https://ubuntuforums.org/showthread.php?t=2355551&page=24&p=13676662#post13676662]("http://https://ubuntuforums.org/showthread.php?t=2355551&page=24&p=13676662#post13676662")
> I create one file in /etc/grub.d for each OS I want in my grub menu, as shown in post #166. Also, see menu appearance on monitor in post #174.

To make files, I first copy /boot/grub/grub.cfg and /etc/grub.d/40_custom to a work folder in ~/home.

That is what I meant I had done.  

Part of the reason I've put in Manjaro Xfce Is your mention of it earlier in this thread...  a different Linux... a nice Xfce distro... would boot others...  would not have be messed with due to rolling release.  The reason I put it in last was so it would be first in the boot menu.  Don't know if that will help in making maintenance-free custom menu, or not. 

Mike

---

### Post by Mike Krall on 2017-09-30
I need to progress from having collected Manjaro menuentry (I collected all... pimary and sub menu).  Wherein 'Cavsfan' has never found an instance to use previous kernels, I've needed to run on them a half dozen or more times... very recently with CentOS 7.  Could be that's the only trick I know (that 'Cavsfan' has a million of them)... but still... if it can be done this way relatively easily, it's how I feel I should go.  

*  I haven't been able to put all the pieces together into understanding how a person makes a specific OS control booting.  It seems like having the chosen OS first in a custom menu might do that, but then, is that all needing done ???  I can't tell.  Seems like changing "GRUB_DEFAULT="  to Manjaro # might need to be done.  I assume =6 from this...
```
~$ efibootmgr -v
BootCurrent: 0006
Timeout: 2 seconds
BootOrder: 0006,0002,0000,0001,0003
Boot0000* ubuntu	HD(1,GPT,591246c8-678b-4b3a-a890-0a0db0402efc,0x800,0xf9800)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* bodhi	HD(1,GPT,591246c8-678b-4b3a-a890-0a0db0402efc,0x800,0xf9800)/File(\EFI\BODHI\SHIMX64.EFI)
Boot0002* CentOS Linux	HD(1,GPT,591246c8-678b-4b3a-a890-0a0db0402efc,0x800,0xf9800)/File(\EFI\CENTOS\SHIM.EFI)
Boot0003* neon	HD(1,GPT,591246c8-678b-4b3a-a890-0a0db0402efc,0x800,0xf9800)/File(\EFI\NEON\SHIMX64.EFI)
Boot0006* Manjaro	HD(1,GPT,591246c8-678b-4b3a-a890-0a0db0402efc,0x800,0xf9800)/File(\EFI\MANJARO\GRUBX64.EFI)
```

But reality in machine is this... 
```
~$ sudo parted -l
[sudo] password for waldo: 
Model: ATA Micron_1100_MTFD (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  524MB   523MB   fat32           EFI System Partition  boot, esp
 2      524MB   25.5GB  25.0GB  ext4            16.04 LTS
 5      25.5GB  50.5GB  25.0GB  ext4            elementaryOS
 6      50.5GB  75.5GB  25.0GB  ext4            KDE Neon
 7      75.5GB  101GB   25.0GB  ext4            LM-Cinnamon
 8      101GB   126GB   25.0GB  ext4            Manjaro-Xfce
 9      126GB   151GB   25.0GB  ext4            Ubuntu-Budgie16
10      151GB   176GB   25.0GB  ext4            CentOS-7
 4      203GB   253GB   50.0GB  ext4            Data Partition
 3      253GB   256GB   3001MB  linux-swap(v1)  Swap

```

In a 0 to 6 system, Manjaro is 4, but this is boot, right, so it should be 6... last of 7 put in.  I'm about to catch my tail...  =]

Mike

---

### Post by oldfred on 2017-09-30
With UEFI you set the master default in UEFI.
I just have my one Ubuntu, so that always is the default, and then in grub's 40_custom I have all my other installs. You then can set another default in the grub menu if UEFI is booting a grub.
I just use the grub of my main working system as default which is the first entry anyway.

You can use description in grub, this is an old example, but it still is the same whether Windows or any other install. Description in grub has to be the description grub uses, not UEFI.
 [https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub](https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub)
find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
sudo -H gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by Dennis N on 2017-09-30
> I need to progress from having collected Manjaro menuentry (I collected all... pimary and sub menu). Wherein 'Cavsfan' has never found an instance to use previous kernels, I've needed to run on them a half dozen or more times... very recently with CentOS 7.

You can use the kernel or kernel version that work best when you use a custom menu. That's one of the advantages.

Note: Manjaro easily lets you use a different kernel. See Settings Manager > Kernel. On one (older) computer, I choose to use 4.4 rather than the default 4.9. 
> I haven't been able to put all the pieces together into understanding how a person makes a specific OS control booting. It seems like having the chosen OS first in a custom menu might do that, but then, is that all needing done.


The OS you want to control booting in UEFI system is configured in the UEFI boot order (corrects previous statement which incorrectly said grub menu controlled this. Sorry for any confusion.) 

I bought a new 500 GB SSD for my best computer, so I am installing and slowly rebuilding my selection. Many were due for removal anyway. This time, I started all the files with 08, then use a secondary number to determine the order. This file order is automatically the order in the grub menu: 

```
[dmn@Sydney grub.d]$ ls -1
00_header
08_05-manjaro-mate
08_08-manjaro-xfce
08_12-mint-18-xfce-lvm
08_14-mint-18-mate-lvm
08_15-xubuntu-1404
08_20-xubuntu-1604
08_25-lubuntu-1704
```

The first four 08s are on the new SSD, the last 3 are on a second HDD. The second HDD also has my big data partition. When possible, I am also planning on using LVM on the new disk as you can see. Calamares installer won't do LVM right now, so the first two had to be on standard partitions! I understand the non-GUI Manjaro-Architect installer will do LVM, but since it is sort of experimental at this time, I decided to use Calamares.

---

### Post by Mike Krall on 2017-09-30
'oldfred'...  Went to the link in Post #253 (Grub2/Setup)...  [ password for waldo: /dev/sda2"]https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub$ sudo grub-probe -t device /boot/grub [sudo] password for waldo: /dev/sda2]("https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub$ sudo grub-probe -t device /boot/grub [sudo)

Ran this...```
$ sudo grub-probe -t device /boot/grub
[sudo] password for user: 
/dev/sda2

```
/dev/sda2 is my first root partition... first install... Ubuntu 16.04

Isn't it booting Manjaro (last install) and all others OS? 

Mike

PS... forgot to post again... from this morning...  =[

---

### Post by oldfred on 2017-09-30
First what is UEFI default?
Then what default do you have in grub?
And is grub up to date with sudo update-grub or if os-prober turned off, is 40_custom (or other XX_custom files up to date.

When you start to get more than one install, it starts to become difficult to keep track of which boot manager, UEFI, grub2, rEFInd, or other is presenting menu and then which have defaults.
I use Boot-Repair & bootinfoscript to generate reports so I know what is where.

---

### Post by Dennis N on 2017-10-01
> Part of the reason I've put in Manjaro Xfce Is your mention of it earlier in this thread... a different Linux... a nice Xfce distro... would boot others... would not have be messed with due to rolling release. The reason I put it in last was so it would be first in the boot menu. Don't know if that will help in making maintenance-free custom menu, or not.

Yes, each time you install a new OS, that OS adds an entry to the UEFI boot manager, and also places it first in the boot order. But that is a problem, since if you add another OS after installing your controlling OS, your chosen controlling OS loses control. So you need to do more: 
Each time you add something new, to give priority back to the OS you want to control the grub menu, you need to use the **efibootmgr -o** command to restore the correct boot order. 
All the custom menu entries you make go into the /etc/grub.d directory of the controlling distro (including one for the controlling OS itself) only. 
Also, once you have a working custom menu entry for any OS, I just keep that one working menu entry - no recovery options are in my custom menu as you can always regenerate those if necessary. As discussed in post #236 and probably others, I use the copy and paste method of the one main menu entry for each OS as it appears in the grub.cfg of my controlling distro. In rare occasions, that menu entry generated by os prober does not work. I think I explained how to fix that if you try to boot Manjaro from Ubuntu generated entry.  But you aren't, so that is moot. Again, most everything is done based on methods described at:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

If you ever put one in, Fedora based OS won't be maintenance free **by this method**, since the kernel is always specifically named in the boot line of it's grub menu entry. That means you have to edit its custom menu entry each time it upgrades its kernel to keep using the latest kernel. I think a virtual machine installation or Watson's method are ways to beat this problem. Watson is only good for UEFI installation, however. 

I hope that helps to clarify how it all works.

---

### Post by Mike Krall on 2017-10-01
> **Dennis N said:**
> Yes, each time you install a new OS, that OS adds an entry to the UEFI boot manager, and also places it first in the boot order. But that is a problem, since if you add another OS after installing your controlling OS, your chosen controlling OS loses control. So you need to do more: 
Each time you add something new, to give priority back to the OS you want to control the grub menu, you need to use the **efibootmgr -o** command to restore the correct boot order. 
All the custom menu entries you make go into the /etc/grub.cfg directory of the controlling distro (including one for the controlling OS itself) only. 
[COLOR="#FF0000"]Also, once you have a working custom menu entry for any OS, I just keep that one working menu entry - no recovery options are in my custom menu as you can always regenerate those if necessary[/COLOR]. As discussed in post #236 and probably others, I use the copy and paste method of the one main menu entry for each OS as it appears in the grub.cfg of my controlling distro. In rare occasions, that menu entry generated by os prober does not work. I think I explained how to fix that if you try to boot Manjaro from Ubuntu generated entry.  But you aren't, so that is moot. Again, most everything is done based on methods described at:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

If you ever put one in, Fedora based OS won't be maintenance free **by this method**, since the kernel is always specifically named in the boot line of it's grub menu entry. That means you have to edit its custom menu entry each time it upgrades its kernel to keep using the latest kernel. I think a virtual machine installation or Watson's method are ways to beat this problem. Watson is only good for UEFI installation, however. 

I hope that helps to clarify how it all works.

Thanks, 'Dennis N'...

Red line:  Specifically, *"... no recovery options are in my custom menu as you can always regenerate those if necessary." * As mentioned, I've always kept one extra kernel to fall back on (and have needed to).  It's my only trick.  How does a person "regenerate, if *necessary"*?

Mike

---

### Post by Dennis N on 2017-10-01
> **Mike Krall said:**
> Thanks, 'Dennis N'...Red line:  Specifically, *"... no recovery options are in my custom menu as you can always regenerate those if necessary." * As mentioned, I've always kept one extra kernel to fall back on (and have needed to).  It's my only trick.  How doe a person "regenerate, if *necessary"*?
Mike

Well, I figure I can boot into my default OS (Manjaro), then in /etc/grub.d change 30_os-prober to executable, and then run sudo update-grub to 'regenerate' the missing entries. Then all the boot entries for all the OS in the system will return to the menu.

In Manjaro, you could use the menu entry that works for the problematic OS, put it into a custom menu file, and then update-grub. When satisfied it works, you can turn off the os-prober, update-grub again, and you go back to just custom entries.

---

### Post by Mike Krall on 2017-10-03
Thank you for that, 'Dennis N'...  helps.

*  Do you build the custom menu in Manjaro... or doesn't OS it is built in make a difference? 

*  Do you build a menu file, then test it, build another and test, etc.?  If yes, it seems making and unmaking executable, plus switching 30_os-prober on and off is necessary...yes? 

*  When all the custom menu files are built, made executable, and functioning, does their existence reorder which OS is viewed as DEFAULT=0, 1, etc., or does the original OS installation-order still control that?

*  If the latter, does Manjaro need to be made GRUB_DEFAULT=Manjaro (or, in my case "6"... as in 0006)?  

Mike

---

### Post by Dennis N on 2017-10-03
> *  Do you build the custom menu in Manjaro... or doesn't OS it is built in make a difference? 
I would construct it the same way regardless of what OS is used. But, os-prober of different OSes might produce a few differences in grub menu entries. All Ubuntu-based OSes probably will give the same result.  
> *  Do you build a menu file, then test it, build another and test, etc.?  If yes, it seems making and unmaking executable, plus switching 30_os-prober on and off is necessary...yes? 

After installing a new OS, reboot into it, change boot order back to controlling OS with efibootmgr, reboot to controlling OS, run update-grub, make new custom entry for /etc/grub.d based on new  /boot/grub/grub.cfg, add it to /etc/grub.d, update-grub again to make new grub.cfg with new custom entry, reboot, test the new custom entry, and if ok you can at your convenience turn off os-prober until next time its needed. 
> *  When all the custom menu files are built, made executable, and functioning, does their existence reorder which OS is viewed as DEFAULT=0, 1, etc., or does the original OS installation-order still control that?
With custom entries included on grub menu, default=0 would still pre-select the first menu entry, which in my case is the first custom entry.
> *  If the latter, does Manjaro need to be made GRUB_DEFAULT=Manjaro (or, in my case "6")?  
No. The order in the grub menu doesn't change, only which grub entry would boot automatically if you let it. To boot to Manjaro grub menu when you boot computer, it needs to be first in UEFI boot order. Once you get to the grub menu, GRUB_DEFAULT=0 would normally pre-select first entry (which would be the first custom entry if you have them), BUT the default setting in Manjaro is **GRUB_DEFAULT=saved**. I have left it alone cause I want that. If you don't want to use save default feature, you could change this to 0 and also comment out the **GRUB_SAVEDEFAULT=true** line in /etc/default/grub. 



Hope that helps clear things up!

---

### Post by Mike Krall on 2017-10-03
From this (end page): [http://https://help.ubuntu.com/community/Grub2/CustomMenus]("https://help.ubuntu.com/community/Grub2/CustomMenus")
```
linux /vmlinuz root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff{

initrd /initrd.img
```
Every install I have has a *'linux'* and* 'initrd'* line continuing like this: * "/boot/vmlinuz, etc."* and either * "/boot/initrd, etc."*...Or... * "/boot/initramfs, etc."  *

Is necessary now for "Maintenence Free" menuentry to have */boot/* ?

Mike

---

### Post by deadflowr on 2017-10-03
> Is necessary now for "Maintenence Free" menuentry to have /boot/ ?
Depends on setup and how you want to have the custom entries work.
the /vmlinuz and /initrd.img are actually links from the top level of the file system to the latest (newest) kernels in /boot.
so if the latest kernel is 4.4.0-100-generic, then those files will link to the 4.4.0-100 entries in /boot.
That makes it easier to roll along.
Setting the entries for the /boot instead would require you constantly change the entries, since after every kernel update those old entries will keep pointing to the old kernels in /boot.
If that make sense.

---

### Post by Dennis N on 2017-10-03
see post #236:
> ...the lines starting with 'linux' and 'initrd' are edited to look like what you see here*. This step is what makes it maintenance free.
*referring to the display in that post.

This change is only for Ubuntu distros. Do not do this in other Linux. The system will probably fail to boot if you do.

---

### Post by Mike Krall on 2017-10-03
From Post #259...

> **Dennis N said:**
> Well, I figure I can boot into my default OS (Manjaro), then in /etc/grub.d change 30_os-prober to executable, and then run sudo update-grub to 'regenerate' the missing entries. Then all the boot entries for all the OS in the system will return to the menu.

[COLOR="#0000FF"]In Manjaro, you could use the menu entry that works for the problematic OS, put it into a custom menu file, and then update-grub. When satisfied it works, you can turn off the os-prober, update-grub again, and you go back to just custom entries.[/COLOR]

I just now got fully straight on blue line.  That's a good thing to know about and it causes a person to see some other things better, too.  Thanks, 'Dennis N'...

Mike

---

### Post by Mike Krall on 2017-10-04
> **deadflowr said:**
> Depends on setup and how you want to have the custom entries work.
the /vmlinuz and /initrd.img are actually links from the top level of the file system to the latest (newest) kernels in /boot.
so if the latest kernel is 4.4.0-100-generic, then those files will link to the 4.4.0-100 entries in /boot.
That makes it easier to roll along.
Setting the entries for the /boot instead would require you constantly change the entries, since after every kernel update those old entries will keep pointing to the old kernels in /boot.
If that make sense.

Thanks 'deadflowr'... that was helpful...  =]

And It gives me something else to try to understand the "why" of...  

Mike

---

### Post by Mike Krall on 2017-10-05
> **Dennis N said:**
> 
Post #254
```
[dmn@Sydney grub.d]$ ls -1
00_header
08_05-manjaro-mate
08_08-manjaro-xfce
08_12-mint-18-xfce-lvm
08_14-mint-18-mate-lvm
08_15-xubuntu-1404
08_20-xubuntu-1604
08_25-lubuntu-1704
```

Why did you switch to 08_custom from 06 and 07?  Why switched to numbers for delineators from letters?   

I noticed my LinuxMint-Cinnamon has a 06_themes in it's /boot/grub/grub.cfg and thought I'd start custom menu with 07.  Was wondering if there is a tactical advantage to leaving one empty number-space in front of number used for custom menu?

Mike

---

### Post by Mike Krall on 2017-10-05
Partial quote... Post #261
> **Dennis N said:**
> No. The order in the grub menu doesn't change, only which grub entry would boot automatically if you let it. To boot to Manjaro grub menu when you boot computer, it needs to be first in UEFI boot order. Once you get to the grub menu, GRUB_DEFAULT=0 would normally pre-select first entry (which would be the first custom entry if you have them), BUT the default setting in Manjaro is **GRUB_DEFAULT=saved**. I have left it alone cause I want that. If you don't want to use save default feature, you could change this to 0 and also comment out the **GRUB_SAVEDEFAULT=true** line in /etc/default/grub.

To Note:  
In my Manjaro-Xfce /etc/default/grub there is no  **GRUB_SAVEDEFAULT=true** line.  There is only a **GRUB_DEFAULT=saved**.  I noticed in Manjaro /boot/grub/grub.cfg **all** menuentry's (for Manjaro and for all other OS's) the first line after the title line is **savedefault**.  Looking at information on variables for /etc/default/grub I thought, to have boot menu come up with highlight on last used menuentry, a person needs to have both  **GRUB_DEFAULT=saved**... and...**GRUB_SAVEDEFAULT=true**?  Maybe I misunderstand.  Maybe the *savedefault* menuentry line does the same thing.  

Mike

---

### Post by Dennis N on 2017-10-05
> Why did you switch to 08_custom from 06 and 07?  Why switched to numbers for delineators from letters?   

Completely arbitrary on using 08_ followed by 2-digit number. Could be letters if you like, but 2-digit number has 100 possibilities. I numbered those by 5 so I could squeeze some in between, just like when programming in BASIC. As long as each filename starts with integer >05 and <10. 

> I noticed my LinuxMint-Cinnamon has a 06_themes in it's /boot/grub/grub.cfg and thought I'd start custom menu with 07.  Was wondering if there is a tactical advantage to leaving one empty number-space in front of number used for custom menu?

Anything is ok as long as it starts with 06_, 07_, 08_, or 09_

Red lines generate custom entries at top of grub menu in alphanumeric sorted order (ascending), Blue lines generate the standard grub menu. 
```
[dmn@Sydney grub.d]$ ls -1
00_header
[COLOR="#FF0000"]08_05-manjaro-mate
08_08-manjaro-xfce
08_12-mint-18-xfce-lvm
08_14-mint-18-mate-lvm
08_15-xubuntu-1404
08_20-xubuntu-1604
08_25-lubuntu-1704
08_30-manjaro-mate-sda
08_35-mint-18-mate-sda
08_40-korora-26-menu[/COLOR]
[COLOR="#0000FF"]10_linux
20_linux_xen
30_os-prober[/COLOR]
40_custom
41_custom
60_memtest86+
README

```

---

### Post by Dennis N on 2017-10-05
> **Mike Krall said:**
> Partial quote... Post #261
To Note:  
In my Manjaro-Xfce /etc/default/grub there is no  **GRUB_SAVEDEFAULT=true** line.  There is only a **GRUB_DEFAULT=saved**.  I noticed in Manjaro /boot/grub/grub.cfg **all** menuentry's (for Manjaro and for all other OS's) the first line after the title line is **savedefault**.  Looking at information on variables for /etc/default/grub I thought, to have boot menu come up with highlight on last used menuentry, a person needs to have both  **GRUB_DEFAULT=saved**... and...**GRUB_SAVEDEFAULT=true**?  Maybe I misunderstand.  Maybe the *savedefault* menuentry line does the same thing.  

Mike

It's there. Except for the 900, these are the default settings.

```
[dmn@Sydney default]$ head grub
GRUB_DEFAULT=saved
GRUB_TIMEOUT=900
GRUB_DISTRIBUTOR='Manjaro'
GRUB_CMDLINE_LINUX_DEFAULT="quiet resume=UUID=391dcd7b-ca92-4cfb-98e4-4619ea27aa96"
GRUB_CMDLINE_LINUX=""

# If you want to enable the save default function, uncomment the following
# line, and set GRUB_DEFAULT to saved.
GRUB_SAVEDEFAULT=true

```

The savedefault menuentry line probably results from having these two settings in /etc/default/grub.

---

### Post by Mike Krall on 2017-10-05
> **Dennis N said:**
> It's there. Except for the 900, these are the default settings.

```
[dmn@Sydney default]$ head grub
GRUB_DEFAULT=saved
GRUB_TIMEOUT=900
GRUB_DISTRIBUTOR='Manjaro'
GRUB_CMDLINE_LINUX_DEFAULT="quiet resume=UUID=391dcd7b-ca92-4cfb-98e4-4619ea27aa96"
GRUB_CMDLINE_LINUX=""

# If you want to enable the save default function, uncomment the following
# line, and set GRUB_DEFAULT to saved.
[COLOR="#0000FF"]GRUB_SAVEDEFAULT=true[/COLOR]

```

The savedefault menuentry line probably results from having these two settings in /etc/default/grub.

It is right there, isn't it...  I've got excuses, but no reasons.

Thanks for your patience, 'Dennis N'...

Mike

Edit: From 'Dennis N' quote above... 
 > The savedefault menuentry line probably results from having these two settings in /etc/default/grub.

Found this after posting.  See Post #5 -#6...  [https://www.linuxquestions.org/questions/slackware-14/grub_savedefault-option-not-working-4175595515/]("https://www.linuxquestions.org/questions/slackware-14/grub_savedefault-option-not-working-4175595515/")

---

### Post by Mike Krall on 2017-10-14
Where's the Smiley with the dunce cap?

So now I've got an /etc/grub.d/25_custom.  Put in Boot-Repair and didn't understand it was going to "fix" things for me.  Lost Manjaro as primary boot then got it back through "update-grub" then "grub-install" at Manjaro... which I found out later should have been done with "efibootmgr" (via older post from Rod Smith... see last post in:  [https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows/88432#88432]("https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows/88432#88432")).

Should I be trying to go back to original (pre Boot-Repair)... uninstall Boot-Repair... and or ???

Mike 

PS --  So you know, my small piece of the world got tipped over a little over a week ago... nothing that won't "fix"... but what I want and what I get are being very different things.

Edit: Maybe should show you... from /etc/grub.d/25_custom (Ubuntu 16)
```
#!/bin/sh
exec tail -n +3 $0

menuentry "EFI/BOOT/bkpbootx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/BOOT/bkpbootx64.efi
}

menuentry "EFI/BOOT/fbx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/BOOT/fbx64.efi
}

menuentry "EFI/centos/mmx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/centos/mmx64.efi
}

menuentry "EFI/elementary/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/elementary/fwupx64.efi
}

menuentry "EFI/elementary/mmx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/elementary/mmx64.efi
}

menuentry "EFI/mint-cinnamon/fbx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/mint-cinnamon/fbx64.efi
}

menuentry "EFI/mint-cinnamon/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/mint-cinnamon/fwupx64.efi
}

menuentry "EFI/mint-cinnamon/mmx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/mint-cinnamon/mmx64.efi
}

menuentry "EFI/neon/mmx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/neon/mmx64.efi
}

menuentry "EFI/ubuntu-16-unity/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/ubuntu-16-unity/fwupx64.efi
}

menuentry "EFI/ubuntu-16-unity/mmx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/ubuntu-16-unity/mmx64.efi
}

menuentry "EFI/ubuntu-budgie/fbx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/ubuntu-budgie/fbx64.efi
}

menuentry "EFI/ubuntu-budgie/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/ubuntu-budgie/fwupx64.efi
}

menuentry "EFI/ubuntu-budgie/mmx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/ubuntu-budgie/mmx64.efi
}

menuentry "EFI/ubuntu/fbx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/ubuntu/fbx64.efi
}

menuentry "EFI/ubuntu/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/ubuntu/fwupx64.efi
}

menuentry "EFI/ubuntu/mmx64.efi" {
search --fs-uuid --no-floppy --set=root B70F-1399
chainloader (${root})/EFI/ubuntu/mmx64.efi
}
```

[COLOR="#FF0000"]Edit again:[/COLOR] Never mind... I guess. 'oldfred' is everywhere... [https://ubuntuforums.org/showthread.php?t=2333289]("https://ubuntuforums.org/showthread.php?t=2333289").  I don't feel I need anything in 25_custom, so I'm going to 'mv' it to /etc/grub.d/bkp25_custom, then make it unexecutable.... then 'update-grub'.   

So, why does Boot-Repair think "right and proper" is a 25_custom file? Or maybe I should say, "What does having 25_custom do that isn't being done?"  

Mike

---

### Post by Dennis N on 2017-10-15
Yes, getting the boot priority changed at startup with efibootmgr was mentioned for sure in post #261:

> "To boot to Manjaro grub menu when you boot computer, it needs to be first in UEFI boot order...change boot order back to controlling OS with efibootmgr."

I've never use boot-repair to fix problems - I don't really trust it. These 25_custom entries use chainloader, which is what Watson's method uses, but not exactly the same construct. Do they actually work?? I ask because these boot-repair entries have different folders named for specific ubuntu or mint flavors, which would be a nice, but I had understood from my reading that such naming does not work.  Mint did this at one time, then abandoned it because of problems with updating, I think. All ubiquity installs create just "ubuntu" as their folder name, which means each overwrites the previous ubuntu folder when installed, leaving only the last one to get a UEFI boot menu entry.

Also, there appear to be different *.efi files for three different ubuntus in the same folder. Possibly boot repair can make a different custom one for each ubuntu, something us humans can't, but I've never read anything about this possibility, or seen anything on our forum threads. 

You can certainly get rid of the 25_custom. I hope boot repair didn't wipe out your other custom menu entries!

---

### Post by oldfred on 2017-10-15
Boot-Repair adds all the additional .efi files it finds in the ESP into 25_custom. I have not seen anyone else use 25_custom, so just from Boot-Repair. 
If grub did not add them, then probably not required. 

Some vendors like HP have all the vendor utility boot files in the ESP.
Other vendors have a hidden or another FAT32 partition with all the vendor utility boot files. Boot-Repair then does not see nor add those files.

Not sure if you would ever want to boot vendor utility files from grub. But do not know how those vendors like HP boot into those files.

Ubuntu renamed MokManager.efi to *mmx64*.*efi, *it looks like others did also. That is the key manager which unless you are using UEFI Secure Boot and want to enable your own keys is not required.
[https://askubuntu.com/questions/903207/refind-shows-multiple-ubuntu-choices](https://askubuntu.com/questions/903207/refind-shows-multiple-ubuntu-choices)

 bkpbootx64.efi is Boot-Repair's backup of bootx64.efi. Many systems do not have this file, it is a fallback or hard drive boot entry. This is the file/path used for all external drives, but can be used for internal drives. If it exists it usually is just a copy of Windows .efi boot file. 
I copy shimx64.efi to bootx64.efi, so boot repair them makes a backup of that. Some other installs may also create this file.

---

### Post by Dennis N on 2017-10-15
Very interesting. I looked at ubuntu's EFI files, and see fbx64.efi, fwupx64, mmx64.efi in there. Who would know what these do based on the grub menu entry titles that you would see? Our Manjaro's EFI folder doesn't have any of these - just grubx64.efi. 

Thought you had made your own custom entries? If I may ask, why using boot repair? Something not working? 

I see CentOS in your collection:

I suspect CentOS may fail to boot after awhile without periodic editing your custom entry as kernel version changes over time. If it's like Fedora, it is configured to remove all but 3 kernels. If you don't watch it, eventually the kernel version you are booting through your custom menu will be deleted.

---

### Post by Mike Krall on 2017-10-16
> **Dennis N said:**
> Very interesting. I looked at ubuntu's EFI files, and see fbx64.efi, fwupx64, mmx64.efi in there. Who would know what these do based on the grub menu entry titles that you would see? Our Manjaro's EFI folder doesn't have any of these - just grubx64.efi. 

Thought you had made your own custom entries? If I may ask, why using boot repair? Something not working? 

I see CentOS in your collection:

I suspect CentOS may fail to boot after awhile without periodic editing your custom entry as kernel version changes over time. If it's like Fedora, it is configured to remove all but 3 kernels. If you don't watch it, eventually the kernel version you are booting through your custom menu will be deleted.

*  I've spent a lot of time looking at OS's in /boot/efi/EFI... I stare at them, and they stare back.  Noticed Manjaro is the only one in list having but one piece ( grubx64.efi )... and no 'grub.cfg' either, like all the rest, including OS's I've put in and dumped out again...well... all the rest except CentOS 7, which does have a grub.cfg but it's like other's /boot/grub/grub.cfg.  

*  Using Boot-Repair by accident... the why of needing a Smiley w/ dunce cap.  And what's not working is me.  Seems like every time I get started messing with custom menuentries I get required to get off the computer.  By the time I get back, I've got to remember where I was and get back there.  One of these days... but not today... and tomorrow doesn't look good either (that's a little inside joke).

*  CentOS is in goat screw mode (besides need of updating 'Dennis N' mentioned).  Even when it was in charge of Grub it booted into rescue mode.  I'm not sure I'll get it to stop doing that but haven't made time for the effort, either.  CentOS '10_linux' shows a totally different script than what other OS's have in their '30_os-prober' for CentOS at the 'linux' and 'initrd' lines.  The other OS's are picking up the 'rescue' script somehow.  Even the clean CentOS 7 boot out of 'Esc' at ASUS screen > CentOS > the previous version boots 'rescue' and there is no 'rescue' scripting in it's menuentry anywhere.  

The problem was in a link in Post #247:  [https://ubuntuforums.org/showthread.php?t=2355551&page=25&p=13691190#post13691190]("https://ubuntuforums.org/showthread.php?t=2355551&page=25&p=13691190#post13691190")  from Dedoimedo:  [https://www.dedoimedo.com/computers/grub2-fedora-command-not-found.html]("https://www.dedoimedo.com/computers/grub2-fedora-command-not-found.html")  I fixed all the links in that post, by the way.  Anyhow, CentOS is a story for another place and time... though I'd love to run it by 'oldfred' and 'Dennis N'.  I'll probably put it in 08 and/or 09_custom by itself so I can mess with it separately from the other OS's.

Mike

---

### Post by oldfred on 2017-10-16
I was curious about grub and UEFI. Ubuntu's grub uses the grub.cfg in /EFI/ubuntu to configfile/chain to full grub.cfg in install. 
So other Linux obviously do not have a grub2 that has to have /EFI/ubuntu.
So I install Debian just to see how it does UEFI boot.

Debian does not have UEFI secure boot and also just has grubx64.efi. And the entries in Ubuntu's grub.cfg are inside the grubx64.efi in Debian.
Or Ubuntu's UEFI grub has lots of changes.

I have changed GRUB_DISTRIBUTOR= in /etc/default/grub and that does create a new separate UEFI entry. But even that entry boots from /EFI/ubuntu/grub.cfg
Inside grub code is also an efi_distributor and in Ubuntu that has been changed everywhere to be "ubuntu". I remember a bug report where someone wanted a separate entry for kubuntu and there is logic that if kubuntu allow that as a separate entry.

---

### Post by Mike Krall on 2017-10-16
> **oldfred said:**
> I was curious about grub and UEFI. Ubuntu's grub uses the grub.cfg in /EFI/ubuntu to configfile/chain to full grub.cfg in install. 
So other Linux obviously do not have a grub2 that has to have /EFI/ubuntu.
So I install Debian just to see how it does UEFI boot.

Debian does not have UEFI secure boot and also just has grubx64.efi. And the entries in Ubuntu's grub.cfg are inside the grubx64.efi in Debian.
Or Ubuntu's UEFI grub has lots of changes.

I have changed GRUB_DISTRIBUTOR= in /etc/default/grub and that does create a new separate UEFI entry. But even that entry boots from /EFI/ubuntu/grub.cfg
Inside grub code is also an efi_distributor and in Ubuntu that has been changed everywhere to be "ubuntu". I remember a bug report where someone wanted a separate entry for kubuntu and there is logic that if kubuntu allow that as a separate entry.

I was thinking maybe to change my forum name to NTIAUAOFT (= Not that I actually understand any of this )... =]

A small part of the reason I've not got a functioning 'XX _custom' are things like this...  [https://en.wikipedia.org/wiki/Initial_ramdisk]("https://en.wikipedia.org/wiki/Initial_ramdisk")   Had it with coffee this morning (prompted by 'intramfs' in CentOS 'initrd' line).  There are specific references to Debian and also to Ubuntu / Fedora as examples of specific forms in the link.  Also (towards end) a noting of most Linux's using initramfs...  NTIAUAOT... 

Mike

PS --  Maybe should just add NIAUAOT as a signature line... standard disclaimer...

---

### Post by Dennis N on 2017-10-16
_Concerning CentOS/Fedora/Korora in your custom menu_: probably the best solution to the grub menu problems (inspired by J.A. Watson of ZDNet) is to chainload. And with this you make the custom menu maintainance free.

Here is the custom grub menu entry I made for Korora 26 (Gnome):
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'KORORA 26 menu' {
insmod part_gpt 
insmod fat
set root='hd1,gpt4'
chainloader /EFI/fedora/shim.efi 
}

```
This is maintainance free, as all kernel updates in Korora are reflected in the Korora menu loaded by this menu entry. 
This technique works with UEFI only.
NOTE: 'set root=' is set to the EFI system partition for Korora. 

I chose Korora over Fedora (or CentOS) cause the guys who make it do the work with basic Fedora to get something that works out of the box as most users would want. Pure Fedora, being open source only, takes some fiddling with added repos and settings to do that.

You could make custom grub menu entries for other OSes this way, but each of these would need grub bootloader files in an EFI system partition.

---

### Post by Mike Krall on 2017-10-17
> **Dennis N said:**
> _Concerning CentOS/Fedora/Korora in your custom menu_: probably the best solution to the grub menu problems (inspired by J.A. Watson of ZDNet) is to chainload. And with this you make the custom menu maintainance free.

Here is the custom grub menu entry I made for Korora 26 (Gnome):
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'KORORA 26 menu' {
insmod part_gpt 
insmod fat
set root='hd1,gpt4'
chainloader /EFI/fedora/shim.efi 
}

```
This is maintainance free, as all kernel updates in Korora are reflected in the Korora menu loaded by this menu entry. 
This technique works with UEFI only.
NOTE: 'set root=' is set to the EFI system partition for Korora. 

I chose Korora over Fedora (or CentOS) cause the guys who make it do the work with basic Fedora to get something that works out of the box as most users would want. Pure Fedora, being open source only, takes some fiddling with added repos and settings to do that.

You could make custom grub menu entries for other OSes this way, but each of these would need grub bootloader files in an EFI system partition.

Thanks, 'Dennis N'... maybe this works with CentOS, too.  I mean CentOS is Red Hat Enterprise Linux (RHEL)... Fedora is RHEL (to a point)... Korora is Fedora... maybe CentOS is Korora...  =]

I'm wondering if the 'set root=' line could be 'set root=UUID=4d7429d0-2d26-4d49-806b-46629198f13b' (CentOS UUID, this machine)?

Also wondering if my CentOS '/etc/default/grub' is going to cause problems... like GRUB_DEFAULT=saved.  I got curious when 'Dennis N' pointed to Manjaro having same, but also having GRUB_SAVEDEFAULT=true... ran into this:  [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/sec-customizing_the_grub_2_configuration_file]("https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/sec-customizing_the_grub_2_configuration_file")  See 25.5.1  

CentOS 10_linux with exact copy of CentOS /etc/default/grub file:
```
menuentry 'CentOS Linux (3.10.0-693.2.2.el7.x86_64) 7 (Core)' --class centos --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-3.10.0-693.2.2.el7.x86_64-advanced-4d7429d0-2d26-4d49-806b-46629198f13b' {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  4d7429d0-2d26-4d49-806b-46629198f13b
	else
	  search --no-floppy --fs-uuid --set=root 4d7429d0-2d26-4d49-806b-46629198f13b
	fi
	linuxefi /boot/vmlinuz-3.10.0-693.2.2.el7.x86_64 root=UUID=4d7429d0-2d26-4d49-806b-46629198f13b ro rhgb quiet 
	initrdefi /boot/initramfs-3.10.0-693.2.2.el7.x86_64.img
}
menuentry 'CentOS Linux (3.10.0-514.el7.x86_64) 7 (Core)' --class centos --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-3.10.0-514.el7.x86_64-advanced-4d7429d0-2d26-4d49-806b-46629198f13b' {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  4d7429d0-2d26-4d49-806b-46629198f13b
	else
	  search --no-floppy --fs-uuid --set=root 4d7429d0-2d26-4d49-806b-46629198f13b
	fi
	linuxefi /boot/vmlinuz-3.10.0-514.el7.x86_64 root=UUID=4d7429d0-2d26-4d49-806b-46629198f13b ro rhgb quiet 
	initrdefi /boot/initramfs-3.10.0-514.el7.x86_64.img
}
menuentry 'CentOS Linux (0-rescue-939b2eb92531492091f67303efe567f2) 7 (Core)' --class centos --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-0-rescue-939b2eb92531492091f67303efe567f2-advanced-4d7429d0-2d26-4d49-806b-46629198f13b' {
	load_video
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  4d7429d0-2d26-4d49-806b-46629198f13b
	else
	  search --no-floppy --fs-uuid --set=root 4d7429d0-2d26-4d49-806b-46629198f13b
	fi
	linuxefi /boot/vmlinuz-0-rescue-939b2eb92531492091f67303efe567f2 root=UUID=4d7429d0-2d26-4d49-806b-46629198f13b ro rhgb quiet 
	initrdefi /boot/initramfs-0-rescue-939b2eb92531492091f67303efe567f2.img
}

-------------------------------------------------------------------------------------------

/etc/default/grub

GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
GRUB_DEFAULT=saved
GRUB_DISABLE_SUBMENU=true
GRUB_TERMINAL_OUTPUT="console"
GRUB_CMDLINE_LINUX="rhgb quiet"
GRUB_DISABLE_RECOVERY="true"
```

This is what Manjaro 30_os-prober makes of CentOS... note the 'rescue' in 'linux' and 'initrd' lines:
```
menuentry 'CentOS Linux 7 (Core) (on /dev/sda10)' --class centos --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-4d7429d0-2d26-4d49-806b-46629198f13b' {
	savedefault
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  4d7429d0-2d26-4d49-806b-46629198f13b
	else
	  search --no-floppy --fs-uuid --set=root 4d7429d0-2d26-4d49-806b-46629198f13b
	fi
	linux /boot/vmlinuz-0-rescue-939b2eb92531492091f67303efe567f2 root=/dev/sda10
	initrd /boot/initramfs-0-rescue-939b2eb92531492091f67303efe567f2.img
}
submenu 'Advanced options for CentOS Linux 7 (Core) (on /dev/sda10)' $menuentry_id_option 'osprober-gnulinux-advanced-4d7429d0-2d26-4d49-806b-46629198f13b' {
	menuentry 'CentOS Linux 7 (Core) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-0-rescue-939b2eb92531492091f67303efe567f2--4d7429d0-2d26-4d49-806b-46629198f13b' {
		savedefault
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  4d7429d0-2d26-4d49-806b-46629198f13b
		else
		  search --no-floppy --fs-uuid --set=root 4d7429d0-2d26-4d49-806b-46629198f13b
		fi
		linux /boot/vmlinuz-0-rescue-939b2eb92531492091f67303efe567f2 root=/dev/sda10
		initrd /boot/initramfs-0-rescue-939b2eb92531492091f67303efe567f2.img
	}
	menuentry 'CentOS Linux 7 (Core) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.10.0-514.el7.x86_64--4d7429d0-2d26-4d49-806b-46629198f13b' {
		savedefault
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  4d7429d0-2d26-4d49-806b-46629198f13b
		else
		  search --no-floppy --fs-uuid --set=root 4d7429d0-2d26-4d49-806b-46629198f13b
		fi
		linux /boot/vmlinuz-3.10.0-514.el7.x86_64 root=/dev/sda10
		initrd /boot/initramfs-3.10.0-514.el7.x86_64.img
	}
	menuentry 'CentOS Linux 7 (Core) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.10.0-693.2.2.el7.x86_64--4d7429d0-2d26-4d49-806b-46629198f13b' {
		savedefault
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  4d7429d0-2d26-4d49-806b-46629198f13b
		else
		  search --no-floppy --fs-uuid --set=root 4d7429d0-2d26-4d49-806b-46629198f13b
		fi
		linux /boot/vmlinuz-3.10.0-693.2.2.el7.x86_64 root=/dev/sda10
		initrd /boot/initramfs-3.10.0-693.2.2.el7.x86_64.img
	}
} 
```

Ubuntu '30_os-prober' sees CentOS same as Manjaro... without the 'savedefault' Manjaro puts in all of it's '30_os-prober menuentries... otherwise, identical

Anyhow... I'm thinking a custom menuentry as 'Dennis N' posted might run into problems with CentOS use of GRUB_DEFAULT=saved... but...  ???

Mike

---

### Post by Dennis N on 2017-10-17
> Thanks, 'Dennis N'... maybe this works with CentOS, too. I mean CentOS is Red Hat Enterprise Linux (RHEL)... Fedora is RHEL (to a point)... Korora is Fedora... maybe CentOS is Korora... =]

It would work with any UEFI installed OS that has grub boot loader files in some EFI system partition.

> I'm wondering if the 'set root=' line could be 'set root=UUID=4d7429d0-2d26-4d49-806b-46629198f13b' (CentOS UUID, this machine)?

Maybe. I was planning to try this, but never did. Let me know if it works if you do. Worth a try.

> Also wondering if my CentOS '/etc/default/grub' is going to cause problems... like GRUB_DEFAULT=saved. I got curious when 'Dennis N' pointed to Manjaro having same, but also having GRUB_SAVEDEFAULT=true... ran into this: [https://access.redhat.com/documentat...iguration_file](https://access.redhat.com/documentat...iguration_file) See 25.5.1 

Cause problems when you use Watson's method? No. Once Manjaro grub chainloads CentOS grub bootloader, CentOS settings would be used, and you see boot entries of the CentOS grub menu.   

> Ubuntu '30_os-prober' sees CentOS same as Manjaro... without the 'savedefault' Manjaro puts in all of it's '30_os-prober menuentries... otherwise, identical
Anyhow... I'm thinking a custom menuentry as 'Dennis N' posted might run into problems with CentOS use of GRUB_DEFAULT=saved... but... ???

Ubuntu just may not use this command in it's menu entries, so ignores it. I also recall there were also some commands used in certain grub menus that will throw a warning or even hang up when you use it with a 'foreign' OS. I think I just edited or removed those lines to (hopefully) make it work.

Note: When I use the menu entry of post #279 in Manjaro menu, and put in the line 'savedefault' line, it didn't work. What you see is what I use.

---

### Post by Dennis N on 2017-10-17
Just looked over you post again. From your display in post #280 showing result of 30_os-prober:

```
menuentry 'CentOS Linux 7 (Core) (on /dev/sda10)' --class centos --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-4d7429d0-2d26-4d49-806b-46629198f13b' {
	savedefault
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  4d7429d0-2d26-4d49-806b-46629198f13b
	else
	  search --no-floppy --fs-uuid --set=root 4d7429d0-2d26-4d49-806b-46629198f13b
	fi
	linux /boot/vmlinuz-0-rescue-939b2eb92531492091f67303efe567f2 root=/dev/sda10
	initrd /boot/initramfs-0-rescue-939b2eb92531492091f67303efe567f2.img
}

```
This looks peculiar. For one thing, I think you need **linuxefi** and **initrdefi** to make a UEFI Fedora boot proceed - this happened with Ubuntu too, but the rescue part? Don't know why that's there. Avoid these potential problems as I do by using the construct in post #279 modified for your system.

UPDATE: I get the same kind of menu entry lines for Korora with Manjaro as you do for CentOS. Using linuxefi and initrdefi didn't work, so scratch that suggestion. Booting "as is" ends up in "emergency mode". I think I went with Watson's method (post #279) from the git-go when I installed Korora on this machine, so never saw this problem with the Manjaro created entry. So, best solution I see for booting Korora/Fedora is to go with that.

---

### Post by Dennis N on 2017-10-17
Hello Mike Krall,

Gave this some more thought. I saw the same kind of linux and initrd lines as you show when I looked at my Manjaro grub menu's os-prober entry for Korora. These lines are not correct and fail to boot Korora.

Fix: For you, instead of looking at Manjaro's grub.cfg file, use CentOS grub.cfg file as the source of the Manjaro's custom menu entry for CentOS. After copying and pasting that menu entry into a 40_custom file, you need to change **linuxefi** to **linux**, and **initrdefi** to **initrd** as well. I won't repeat here the remaining steps to finish up generating a new Manjaro grub.cfg, as they should be familiar by now. The result should then work correctly. I tested this on my system, and it worked to direct boot Korora (no chainload) from Manjaro.  

Even though this works, to have a completely maintenance-free custom menu, as previously discussed, you must use Watson's method of post #279 like I do. Your choice, of course.

---

### Post by Mike Krall on 2017-10-18
That looks like a lot of brain work you did, 'Dennis N' (Posts #281 - #283).  I'm happy to have the outcome of it... thank you.

Yes... maintenance-free is better.  Functionally, I don't care what a CentOS custom menu looks like... I'll use the J.A. Watson custom menu-form 'cause it works. (I've read his 3-part article on multi-distro menuentry's a number of times... there are parts of it I can't get pieced.)   And it will be interesting to see if a Manjaro-controlled boot without 'savedefault' after the menuentry title will show up as 'last OS booted' in rebooted boot menu (Manjaro's green font for 'last booted").  Aesthetically and technically, I've got a heartache with "Fedora-like" not having something that works (that is... it won't boot other OS's and other OS's boot it to 'rescue'). That will probably cause me to dig and fuss with it.

I'll try using (CentOS UUID, this machine):
```
set root=UUID=4d7429d0-2d26-4d49-806b-46629198f13b
``` 
I wonder if putting quotes in would be better... like this:
```
set root='UUID=4d7429d0-2d26-4d49-806b-46629198f13b'
```

When Dedoimedo posted his article on the CentOS problem on Feb. 22, 2017 (this one... from Post # 276... [https://www.dedoimedo.com/computers/grub2-fedora-command-not-found.html]("https://www.dedoimedo.com/computers/grub2-fedora-command-not-found.html")), the "Fedora-like" OS's didn't have 'efi' in the 'linux' and 'initrd' lines. Now they do (see CentOS 10_linux in Post #280).  

To make sure some things are clear...

Dedoimedo was trying to have "Fedora-like" be in charge of boot.

I got same problems doing same thing... CentOS running boot when newest OS install. 

I got CentOS "rescue" trying to boot CentOS kernel with other OS in charge of boot (Manjaro, only)... regular, start-up boot menu. 

With Manjaro in charge of boot, going to ESP menu (Asus screen > 'Esc') and picking CentOS shows three CentOS entries at top (other OS below)... "new kernel", "previous kernel", and "rescue".  All listed same (no 'submenu' structure).  "new kernel" boots correctly... "previous kernel" boots to "rescue", as does "rescue" kernel. Choosing any other OS from this menu gets: 
```
error: can't find command 'linux'
error: can't find command 'initrd'
```

Mike

---

### Post by Dennis N on 2017-10-18
Reread the Dedoimedo article. Maybe best advice is at the bottom:

> Just set a different distro [other than Fedora] to be in charge of your boot plan.

Just as a test, from Manjaro custom menu, I did the chainload to Korora's grub menu, but rather than go with the top choice and continue to Korora as I always have done, tried the lower ones (all these use linuxefi and initrdefi). The Ubuntu and Mint entries booted, but trying to boot Manjaro from this gave me a kernel panic - not just error messages. That shouldn't happen.

Otherwise, once I apply a number of the Gnome extensions, Korora Gnome is nice to use.

Since I recalled seeing something like this in the past, I looked back at my log book, I noted the exact same problem 2 years ago in Nov 2015, after I had just installed Fedora 23 (my first try with Fedora). Should sound familiar:
> Nov 30, 2015: Fedora 23 won't boot Ubuntu from it's own generated grub entries. I get errors like &#8220;can't find command initrd&#8221;. Update-grub also does not exist as a command, so I couldn't generate a custom menu...

Shortly thereafter, a fix:
> One-time fix is to select the boot entry for Xubuntu, then 'e' to edit. Find the line beginning with 'linux' and change to 'linuxefi' and the line beginning with 'initrd' change to 'initrdefi' and then Ctrl+x to continue the boot. Permanent fix of course is to create a custom menu entry once I find the equivalent of update-grub in language Fedora will understand - it doesn't have this command.

My solution for the missing update-grub command was to construct an alias for it:
```
alias update-grub='sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg'
```

---

### Post by Mike Krall on 2017-10-19
A divergence from specific line of thought:  Long time ago meant to put the following links in this thread.  Mention of J.A. Watson, 'Dennis N' in Post #282 and me in Post #284 reminded...

3 Parts:  **Hands-On: Linux UEFI multi-boot, my way**... J.A. Watson... maintenance-free menuentry's  
[http://www.zdnet.com/article/hands-on-linux-uefi-multi-boot-my-way/]("http://www.zdnet.com/article/hands-on-linux-uefi-multi-boot-my-way/")
[http://www.zdnet.com/article/hands-on-linux-uefi-multi-boot-part-2/]("http://www.zdnet.com/article/hands-on-linux-uefi-multi-boot-part-2/")
[http://www.zdnet.com/article/hands-on-linux-uefi-multi-boot-part-three-problem-solving/]("http://www.zdnet.com/article/hands-on-linux-uefi-multi-boot-part-three-problem-solving/")

Mike

---

### Post by Mike Krall on 2017-10-19
> **oldfred said:**
> With UEFI you will have the entry in the ESP - efi system partition, but then to use that have to interrupt normal boot with f10 or f12 to get UEFI boot menu.

We normally then have os-prober find other installs and add then to the default grub menu. But have to reboot into default install and run sudo update-grub to get new kernels installed in other install(s).

But if using the Maintenance free method documented by cavsfan, you turn off os-prober and add your own entries to 40_custom in default boot install. That works for Debian based installs, but I do not know about other distributions. It works for Debian based installs as with every kernel update, they also update a link in / that we then use the link to boot from default install/grub, so we always are booting most recent kernel in our other installs.

[COLOR="#FF0000"]If directly copying a boot stanza, you have to update grub in that install, normally part of kernel update, and then reboot into default grub's system and edit boot stanza with new kernel.[/COLOR] If none of the other installs have the link in /, it then may be easier just to leave os-prober turned on. I have only installed flavors of Ubuntu and mostly just every 6 month release of Ubuntu.

Red:  I got myself confused.  I'm reading this as method to copy menuentry to use in custom menuentry.  I'm making separate files for each OS's_menuentry as 'Dennis N' has shown, using Manjaro as DEFAULT, and Manjaro '/etc/grub.d' to place custom menus. By red-line, I would 'update-grub' in an OS, copy 1st menu entry in that OS '10_linux' (store in /mnt/data for access)... edit as necessary (title)... 'save as'  (my case -example) '07_00-Manjaro-Xfce'. (Hopefully it shows up in '/ect/grub.d'... if not... I find and 'mv'.  Do I understand, or ??? 

Mike

---

### Post by oldfred on 2017-10-19
Yes, but you have to run in Ubuntu:
sudo update-grub
Changes then in the /etc/grub.d and /etc/default/grub     configuration file are updated into /boot/grub/grub.cfg file.

And if  you look to see what update-grub does:
fred@Z170N:~$ whereis update-grub
update-grub: /usr/sbin/update-grub /usr/share/man/man8/update-grub.8.gz

It is just grub-mkconfig:
fred@Z170N:~$ cat /usr/sbin/update-grub
#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

---

### Post by Mike Krall on 2017-10-19
> **oldfred said:**
> [COLOR="#FF0000"]Yes, but you have to run in Ubuntu:
sudo update-grub[/COLOR]
Changes then in the /etc/grub.d and /etc/default/grub     configuration file are updated into /boot/grub/grub.cfg file.

And if  you look to see what update-grub does:
fred@Z170N:~$ whereis update-grub
update-grub: /usr/sbin/update-grub /usr/share/man/man8/update-grub.8.gz

It is just grub-mkconfig:
fred@Z170N:~$ cat /usr/sbin/update-grub
#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

I've run the scripts.  My return is same-same.  Have scripts saved.

Red line:
To be sure I understand...  I posted (#287)... >  I'm making separate files for each OS's_menuentry as 'Dennis N' has shown, using Manjaro as DEFAULT, and Manjaro '/etc/grub.d' to place custom menus. By red-line, I would 'update-grub' in an OS, copy 1st menu entry in that OS '10_linux' (store in /mnt/data for access)... edit as necessary (title)... 'save as' (my case -example) '07_00-Manjaro-Xfce'. (Hopefully it shows up in '/ect/grub.d'... if not... I find and 'mv'.

At end of that process (in Manjaro), I need to "sudo update-grub".  

Also need to make each custom menu file executable.  Does it matter when custom menu file is made executable?   

It seems, to test, I reboot.  Grub comes to '07_XXX' before '10_linux', and following /etc/grub.d files.  Should boot.  If yes, make tested file unexecutable.  Go to working folder, make file for next OS in line (seems not to matter which order past Manjaro-file in 1st position).  Run through quoted process for next OS... "sudo update-grub"... make executable... test... make unexecutable...  and on through all OS.  

Mike

---

### Post by oldfred on 2017-10-19
Only files that start with two numbers & underscore and are executable will be updated with the grub-mkconfig.

You should be able to compare setting in /boot/grub/grub.cfg after update to confirm it did update.

---

### Post by Mike Krall on 2017-10-19
Thank you, 'oldfred'... 

Mike

---

### Post by Dennis N on 2017-10-20
> If directly copying a boot stanza, you have to update grub in that install, normally part of kernel update, and then reboot into default grub's system and edit boot stanza with new kernel. If none of the other installs have the link in /, it then may be easier just to leave os-prober turned on. I have only installed flavors of Ubuntu and mostly just every 6 month release of Ubuntu.

I have Manjaro control booting. Let's say Fedora is booted from Manjaro's custom grub menu. With Watson's method, if Fedora updates it's kernel then I don't need to do any editing - period. Once I chainload to Fedora's grub menu, Fedora's kernel update has also updated the Fedora grub menu, and the new kernel is now the top entry. That's the beauty of it. Maintenance free.

---

### Post by oldfred on 2017-10-20
I did not thoroughly read Watson's methods.
He had the copy & paste boot stanza, and since I do not boot other versions & all my versions of Ubuntu only have one UEFI entry (/EFI/ubuntu) I have to boot via grub.
But he also shows the chainloader back into the ESP, just like a Windows entry so you are restarting with that installs entry in ESP. That would work well for any version that correctly installs a unique entry into UEFI/ESP partition.
There was a bug report years ago to add Kubuntu as an entry, and Ubuntu did modify its grub to do that. But it is just some logic in grub that if version is Kubuntu use that rather than ubuntu. Otherwise ubuntu is hard coded into grub's UEFI entry. That is why some like Mint that use Ubuntu's grub still show ubuntu as UEFI entry.

---

### Post by gaodiangui on 2017-10-20
helpful

---

### Post by Dennis N on 2017-10-20
> **oldfred said:**
> I did not thoroughly read Watson's methods...
No criticism intended. Just reiterating for user Mike Krall what was discussed in the previous posts on this method versus the standard method with respect to Fedora in particular in order to include it in a multiboot setup that would be maintenance free. Limitations are 1) it only works for UEFI installs, and 2) an OS you want to boot this way must have boot files in an EFI system partition.

---

### Post by Dennis N on 2017-10-21
> **Mike Krall said:**
> A divergence from specific line of thought:  Long time ago meant to put the following links in this thread.  Mention of J.A. Watson, 'Dennis N' in Post #282 and me in Post #284 reminded...

3 Parts:  Hands-On: Linux UEFI multi-boot, my way... J.A. Watson... maintenance-free menuentry's ... 
Mike
Those, from March 2015, are the essentials. I can see related UEFI multibooting articles all the way back to Apr 2013 where I see "My experiments with multi-boot selection with UEFI boot manager", but those three linked articles contain the key concepts. Watson ideally wants to boot everything this way (this is my sense of his goal). Instead, I (and the majority of users, I think) boot to one controling grub, then boot the target OS directly (which can save a few seconds), and use Watson technique of starting another grub bootloader when that is needed to have a maintenance free setup. 

Added: Looking over those articles. He doesn't say much about the custom menus concept, except these sentences in the second article:
> "Once you have a the configuration for a specific Linux installation the way you want it, you can copy that part of the grub.cfg file and add it to the end of /etc/grub.d/40_custom. The contents of that file are automatically added to the end of grub.cfg whenever it is (re-)created, so your changes will survive intact. Hooray!"
Is there more somewhere? 

Good luck with your work.

---

### Post by Mike Krall on 2017-10-25
I've been fiddling with menuentry since my last Post #291 (top of this page)... up until last night.

It's hard to say what the title of this post should be.  Over the past 22 hours I've thought of a number of possibilities... 
-----------------------------------------------
"Oh, oh..."

"A Comedy of Errors"

"Persons Unclear on the Concept"

Maybe "All of the Above"...

In the end, I think "The Blind Leading the Blind" says it. [https://en.wikipedia.org/wiki/The_blind_leading_the_blind]("https://en.wikipedia.org/wiki/The_blind_leading_the_blind")   (See "Interpretations"... and PLEASE note, there is only this one person involved here.  OK, I talk to myself, sometimes out loud, and that's "all of us".  You-all are innocent bystanders.)  

From the above link is this follow-on link:  [https://en.wikipedia.org/wiki/The_Blind_Leading_the_Blind]("https://en.wikipedia.org/wiki/The_Blind_Leading_the_Blind")  It's a wonderful painting (pics can be blown up). I've been looking at it and reinterpreting it though my life for decades.  Re viewing it again in light of recent events caused me to think of a related parable: * It's one thing to talk to ones self (even out loud).  It's another thing to listen.*
------------------------------------------------------------------------------------------------------------------- 

It's hard to say what-all is going on.  Right now Manjaro ( /dev/sda8 ) is full... 16 MiB of 23,842 MiB "available"...  Manjaro seen through mounting it from Ubuntu 16.04 shows an empty /boot/efi, yet there is a Manjaro in startup boot menu (now only Manjaro and Manjaro-Advanced listed -and the Advanced doesn't have all it's pieces)... both fail boot... other 6 OS are gone from startup menu but exist and boot from UEFI menu. 

I'm going to put this down here, but if anyone thinks I should take it somewhere else, please just say.  

Seemingly, creating and installing custom-menu files went well in the beginning.  In Manjaro: Checked for updates... ran "sudo update-grub"... copied all of "10_linux"  to work folder in /mnt/data.  Have  'Copy_40_custom' as text file in 'Menuentry' work folder... added it there... no line spaces... click 'save as'... title it '07_00-Manjaro-xfce'... point it to /etc/grub.d... click 'save'.  Failed for permissions.  Opened file with Thunar Root... clked. 'save as' ... etc. and it saved.  Checked /etc/grub.d... file there... check permissions... not executable.  Ran "sudo update-grub".... clean.  Opened terminal... ran "sudo chmod a+x /etc/grub.d/07_00-Manjaro-xfce.  Checked file... executable. Rebooted.  Two Manjaro's in startup menu... original with custom_entry above.  Both boot. Looked at /boot/grub/grub.cfg and there it is... 07_00- etc.   

That was simple...  I'm an expert now, right?  

Do same for Ubuntu 16.04 with steps for my choice of title (in single quotes)... adding my sda/2 UUID in 'linux' line... in Thunar Root 'save as'. Check /etc/grub.d... run "sudo update-grub".... make executable... check that... reboot.  No extra Ubuntu 16.04.  It took two more times to actually get the 'linux' and 'initrd' lines right. Figured out a better step-by-step for the process in the effort. Last time copy/paste of first menuentry in Ubuntu 16.04 was missing the closing bracket... typed one in... facing the wrong direction and didn't catch it... 'save as'... check /etc/grub.d... make executable and check... run "sudo update-grub".  End of normal print out throwing errors.  Goto /boot/grub/grub.cfg (again).  Try to make line numbers show up... won't.  Finally figure out to copy /boot/grub/grub.cfg to a plain text file in 'Menuentry' work folder and get line numbers there.  #150 is a wrong facing ending-bracket.  Make unexecutable.  Delete Ubuntu 16.04 custom_menuentry.  Change bracket facing direction Thunar Root.  'save as', etc. check, check, check....  make executable... "sudo update-grub" throws errors and advice to look at /etc/default/grub and /etc/grub.d... with "error in line 776" (last line in /boot/grub/grub.cfg).  Compared with other OS is not wrong... looks like this:
```
### BEGIN /etc/grub.d/60_memtest86+ ###
if [ "${grub_platform}" == "pc" ]; then
    menuentry "Memory Tester (memtest86+)" --class memtest86 --class gnu --class tool {
        search --fs-uuid --no-floppy --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  988844a7-a4ec-40ac-b12f-05724ca4c899
        linux16 /boot/memtest86+/memtest.bin 
    }
fi
### END /etc/grub.d/60_memtest86+ ###
```

Enough, it's late... but one last look.  End of both custom-menuentrys looks like this:

```
}### END /etc/grub.d/... 
```

No single line space between un-tabbed closing bracket and ### END.  Too late, deal with tomorrow...  

Review... delete Ubuntu custom... "sudo update-grub"... throws errors... out of memory...syntax error... incorrect command... error at line number 776 (again).  Delete Manjaro_custom...  "sudo update-grub"... no errors.  OK start again... check, check, double check.  Spent some time wondering how come the closing bracket and ### END, etc. are on same line.  That's what happens when a person leaves a cusor at the end of a custom-menu... tight up against the closing bracket.  OK, I'll fix that... "Enter"... "Enter".  Now closing bracket  has a line space below it and cusor is where ### END, etc. are to go.  'Save as'... check /etc/grub.d.  now there are roughly 4 empty lines below "}"  Tried again (Thunar Root)... same... again and move cursor to line below "}"... same.  Try "sudo nano /etc/grub.d"... same... same... same.  OK, put it in and see what happens.  Bad Idea, but it wasn't me, it was the one who talks out loud. 

Messing with 'nano' (I'm a rank amateur, I promise) moving cursors I used 'Enter' key to line down... that creates extra lines, like TAB creates X number of horizontal spaces (how it's set, near as I can figure).  'Arrow' key  seems to do the same... extra empty lines.  Right at the end I messed with 'Space Bar' in nano but didn't use that version... it moves one space, then another, then pops down what looks like one line.

Anyhow, I haven't made time to dig into this much.  Ran some commands (like "efibootmgr" -v) but didn't see anything odd. Ran Boot-Info and I'm looking at it now (have my previous runs of it saved... comparing line by line is a tedious thing...).  Here is the Paste Bin link:  [http://paste.ubuntu.com/25814265/](http://paste.ubuntu.com/25814265/) And there is this: Modified /etc/default/grub ... added to both Ubuntu and Manjaro (red lines):
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

[COLOR="#FF0000"]# Uncomment to disable 30_os-prober
#GRUB_DISABLE_OS_PROBER=true[/COLOR]

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

If anyone can point me to some things I can check, I'd appreciate it.  If you want  to do that and need more info, just say.  In the end, I'll learn some things, though it might be a reinstall would be simpler.  Hard to say without starting into the alternative, though.

Mike

---

### Post by oldfred on 2017-10-25
Try meld
Synaptic says this:
> Meld  is  a  graphical  diff viewer and merge application for the GNOME
desktop.  It supports 2 and 3-file diffs,  recursive  directory  diffs,....

Arrow keys work for me in nano to move down and in a line. But when I paste it pastes where cursor is when moved by arrow keys not with mouse. So I often get paste into wrong spot as I have not moved cursor location with arrow keys.

Any typo or incorrect construction will prevent sudo update-grub from creating new file.
With early version of grub2, I had a 40_custom that seemed to work. Then newer version of grub and it said error and wrote grub.cfg.new. And at line was not the error but nearby was a missing }. And early version just did not write that boot stanza.
So look at line 776.

I just did something similar. I use a configfile to boot my  ISO and again in copying a boot stanza left off the ending }. But then it only showed the stanzas before the missing }. So configfile is not checked just used.

---

### Post by Mike Krall on 2017-10-25
Thanks for the "directionalization" and information, 'oldfred'.  

Learning more than the very minimal 'Nano' I know now might help. When I get back to custom 'menuentry' I'll experiment. 

*  Do you know what  "{" at the end of  a /boot/grub/grub.cfg menuentry would cause ( as opposed to the correct "}" )?

*  Or what this would cause?:  }### END /etc/grub.d/<file name>

*  Would extra blank lines after either "}" or "{" cause problems?  So far (and I've not made much time for it), I've not a clue to why the seemingly simple process(es) I've done would cause Manjaro / partition to write so much "stuff", and go from 5.7-ish GiB full to max-full (23.83 GiB), let alone how to find and get the "stuff" out.  

I do have a Manjaro Live-USB but need to learn more about using it... if it *can* be used here, the first thing to 'find out'.  It would help if I knew a lot more Linux than I do.  Any one finding a "magic wand" laying around, holler... I'll send you my mailing address. 

Mike 

Oh... From Ubuntu... 'Disk Usage Analyzer' shows Manjaro full... 18.3 GB in ~/... with an:  error opening directory /media/waldo/<UUID>/lvm/cache... 'permission denied'... *also*... top note:  Could not scan some of the folders in "/media/waldo/<UUID>"

---

### Post by Mike Krall on 2017-10-25
> **Dennis N said:**
> Those, from March 2015, are the essentials. I can see related UEFI multibooting articles all the way back to Apr 2013 where I see "My experiments with multi-boot selection with UEFI boot manager", but those three linked articles contain the key concepts. Watson ideally wants to boot everything this way (this is my sense of his goal). Instead, I (and the majority of users, I think) boot to one controling grub, then boot the target OS directly (which can save a few seconds), and use Watson technique of starting another grub bootloader when that is needed to have a maintenance free setup. 

Added: Looking over those articles. He doesn't say much about the custom menus concept, except these sentences in the second article:

[COLOR="#0000FF"]Is there more somewhere?[/COLOR] 

[COLOR="#FF0000"]Good luck with your work[/COLOR].

... "A person makes time"...  Blue Line:  Haven't dug here, 'Dennis N', and maybe search terms could be better (I typically run D+ at best in 'search terms'):

[https://www.google.com/search?q=J.A.+Watson%2C+multi-boot&oq=J.A.+Watson%2C+multi-boot&aqs=chrome..69i57j69i65l3j69i59.12007j0j7&client=ubuntu&sourceid=chrome&ie=UTF-8]("https://www.google.com/search?q=J.A.+Watson%2C+multi-boot&oq=J.A.+Watson%2C+multi-boot&aqs=chrome..69i57j69i65l3j69i59.12007j0j7&client=ubuntu&sourceid=chrome&ie=UTF-8")
[https://www.linuxtoday.com/author/J.A.+Watson/]("https://www.linuxtoday.com/author/J.A.+Watson/")
[http://www.zdnet.com/blog/jamies-mostly-linux-stuff/]("http://www.zdnet.com/blog/jamies-mostly-linux-stuff/")
[http://www.zdnet.com/meet-the-team/uk/j.a.watson1/]("http://www.zdnet.com/meet-the-team/uk/j.a.watson1/")

Red Line:  Thanks for the wishes, 'Dennis N'... I think I'm going to need them... 

Mike

---

### Post by Dennis N on 2017-10-25
Great links. Didn't know he wrote all those Linux Today articles. He's been at it for a long time.
I made a short list from his writings for reference. BTW, your third link needs fixing. I get "Page Not Found".

Looked through #297.
> Checked for updates... ran "sudo update-grub"... copied all of "10_linux" to work folder in /mnt/data. Have 'Copy_40_custom' as text file in 'Menuentry' work folder... added it there... no line spaces... click 'save as'... title it '07_00-Manjaro-xfce'... point it to /etc/grub.d... click 'save'. Failed for permissions.

You added all of 10_linux? That would be wrong. You should be copying only menu entries from /boot/grub/grub.cfg and paste each of the ones you want into a 40_custom from 'menuentry' line down to and including closing brace. If they don't work when you test them, try again with the menu entry from the target os and see if that works. 

```
menuentry 'title' and code stuff here {
lines of code
}
```
title between ' ' can be changed to whatever you want.

Copying a file to a location outside your home folder generally requires sudo since those locations belong to root.

In the boot info summary I wondered how this line in the boot files section with 'ubuntu-budgie' and the others like it would come about? 
```
/EFI/ubuntu-budgie/grubx64.efi
```
All ubuntu flavors using ubiquity installer only get 'ubuntu' for their folder when installed: 
```
/EFI/ubuntu/grubx64.efi
```

---

### Post by Mike Krall on 2017-10-26
> **Dennis N said:**
> Great links. Didn't know he wrote all those Linux Today articles. He's been at it for a long time.
I made a short list from his writings for reference. BTW, your third link needs fixing. I get "Page Not Found".

You added all of 10_linux? 

In the boot info summary I wondered how this line in the boot files section with 'ubuntu-budgie' and the others like it would come about? 
```
/EFI/ubuntu-budgie/grubx64.efi
```
All ubuntu flavors using ubiquity installer only get 'ubuntu' for their folder when installed: 
```
/EFI/ubuntu/grubx64.efi
```

*  Fixed the third link in previous post.  Looking at that home page again, seems it might be a different format of the fourth link... blog.  Like I said, I haven't dug. 

*  On the '10_linux' copying... Bad Editing... I'm taking all of '10_linux' to a named file... header to ender.  Coping ONLY first menuentry  -word menuentry through closing bracket-  to 'Copy_40_custom' file.  Run "save as" from there.  I've fixed the problem in original post.

*  On naming.  I was getting lost. Noticed one 'name' aspect put in GPartEd when original partitions were made showed up where I needed it.  Went to GPartEd and named them all.  I don't know how many places those names will show, but they show where it's helpful to me.  I thought to do same in GPartEd for 'label' (see where it showed up that might be helpful), but I got scared... want to run UUID only, and who knows what having partition labels laying around might cause to happen.  

*  Ubuntu flavors and about every other Ubuntu based OS I've run into... Bohdi Linux... Solus... elementaryOS... Puppy Linux... Linux Mint... KDE Neon.  I figure it's likely all Ubuntu-based OS's have the same affliction. Deep down and dark depths of Ubuntu where no one wants to go any more.  Odd thing... well, surprising at least.  When I put in CentOS-7, then Manjaro, one or the other caused /EFI/ubuntu/grubx64.efi to switch from last entered Ubuntu-type (Ubuntu 16.04 LTS - Budgie-remix - 'hd0,gpt9'... back to first Ubuntu entered (16.04.3 LTS - Unity - 'hdo,gpt2'  ... the original (and still is) GRUB_DEFAULT=0.  Magic 

Mike

---

### Post by Mike Krall on 2017-10-26
> **Mike Krall said:**
> Oh... From Ubuntu... 'Disk Usage Analyzer' shows Manjaro full... 18.3 GB in ~/... with an:  error opening directory [COLOR="#0000CD"]'/media/waldo/<UUID>/lvm/cache'[/COLOR]... 'permission denied'... *also*... top note:  Could not scan some of the folders in "/media/waldo/<UUID>"
I've gone around a number of different ways to look at the Blue-line file.  It doesn't seem to exist.  

In every way of going around (not live-USB yet... only from Ubuntu 16.04) I took a look into Manjaro's /boot/efi... it's empty.  And Manjaro's /boot/grub/grub.cfg is incomplete... no entries in '30_os-prober, but if empty, BEGIN and END lines should not have space between. 
```
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

[COLOR="#0000CD"]### BEGIN /etc/grub.d/30_os-prober ###


### END /etc/grub.d/30_os-prober ###[/COLOR]

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
```

The file 'oldfred' mentioned would likely be created, '/boot/grub/grub.cfg.new', is there, but empty.  Previous iterations of failed custom-menuentry had the same file, but it was not empty. 

Finding Manjaro and Arch Wiki/Tutorials on Live-USB use.  Ran some of the commands mentioned... just to see.  These in particular (Manjaro is /dev/sda8).  Ran the commands minutes apart and got different returns

"lsblk -f"... first time window too small but didn't rewrap on resizing..
```
waldo@11:~$ [COLOR="#FF0000"]lsblk -f[/COLOR]
NAME    FSTYPE LABEL    UUID                                 MOUNTPOINT
loop1                                                        
sr0                                                          
loop0                                                        
sda                                                          
&#9500;&#9472;sda4  ext4            a3c5362b-1fb9-44b9-8afb-050980ea65c2 /mnt/data
&#9500;&#9472;sda2  ext4            0f47f885-3e8b-475b-9082-2ea2c05ff732 /
&#9500;&#9472;sda9  ext4            435cd801-26a4-4fe6-a66f-15c66724df09 
&#9500;&#9472;sda7  ext4            1c957a29-a0ba-4453-83b9-3bdb67d50fc4 
&#9500;&#9472;sda10 ext4            4d7429d0-2d26-4d49-806b-46629198f13b 
&#9500;&#9472;sda5  ext4            b018ef16-2996-4e7a-9725-3ee3d4e91b28 
&#9500;&#9472;sda3  swap            a64147fb-9025-46ee-b704-c6b7877d28c7 [SWAP]
&#9500;&#9472;sda1  vfat   BOOT EFI B70F-1399                            /boot/efi
&#9500;&#9472;sda8  ext4            988844a7-a4ec-40ac-b12f-05724ca4c899 /media/waldo/988844
&#9492;&#9472;sda6  ext4            e12a55fa-51b8-46dd-b3ba-f8ce802df0dd 

waldo@11:~$ [COLOR="#FF0000"]lsblk -f[/COLOR]
NAME    FSTYPE LABEL    UUID                                 MOUNTPOINT
loop1                                                        
sr0                                                          
loop0                                                        
sda                                                          
&#9500;&#9472;sda4  ext4            a3c5362b-1fb9-44b9-8afb-050980ea65c2 /mnt/data
&#9500;&#9472;sda2  ext4            0f47f885-3e8b-475b-9082-2ea2c05ff732 /
&#9500;&#9472;sda9  ext4            435cd801-26a4-4fe6-a66f-15c66724df09 
&#9500;&#9472;sda7  ext4            1c957a29-a0ba-4453-83b9-3bdb67d50fc4 
&#9500;&#9472;sda10 ext4            4d7429d0-2d26-4d49-806b-46629198f13b 
&#9500;&#9472;sda5  ext4            b018ef16-2996-4e7a-9725-3ee3d4e91b28 
&#9500;&#9472;sda3  swap            a64147fb-9025-46ee-b704-c6b7877d28c7 [SWAP]
&#9500;&#9472;sda1  vfat   BOOT EFI B70F-1399                            /boot/efi
&#9500;&#9472;sda8  ext4            988844a7-a4ec-40ac-b12f-05724ca4c899 
&#9492;&#9472;sda6  ext4            e12a55fa-51b8-46dd-b3ba-f8ce802df0dd 

```

Then "lsblk":
```
waldo@11:~$ [COLOR="#FF0000"]lsblk[/COLOR]
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop1     7:1    0   1.2M  1 loop 
sr0      11:0    1  1024M  0 rom  
loop0     7:0    0   1.2M  1 loop 
sda       8:0    0 238.5G  0 disk 
&#9500;&#9472;sda4    8:4    0  46.6G  0 part /mnt/data
&#9500;&#9472;sda2    8:2    0  23.3G  0 part /
&#9500;&#9472;sda9    8:9    0  23.3G  0 part 
&#9500;&#9472;sda7    8:7    0  23.3G  0 part 
&#9500;&#9472;sda10   8:10   0  23.3G  0 part 
&#9500;&#9472;sda5    8:5    0  23.3G  0 part 
&#9500;&#9472;sda3    8:3    0   2.8G  0 part [SWAP]
&#9500;&#9472;sda1    8:1    0   499M  0 part /boot/efi
&#9500;&#9472;sda8    8:8    0  23.3G  0 part /media/waldo/988844a7-a4ec-40ac-b12f-05724ca4c899
&#9492;&#9472;sda6    8:6    0  23.3G  0 part 

waldo@11:~$ [COLOR="#FF0000"]lsblk[/COLOR]
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop1     7:1    0   1.2M  1 loop 
sr0      11:0    1  1024M  0 rom  
loop0     7:0    0   1.2M  1 loop 
sda       8:0    0 238.5G  0 disk 
&#9500;&#9472;sda4    8:4    0  46.6G  0 part /mnt/data
&#9500;&#9472;sda2    8:2    0  23.3G  0 part /
&#9500;&#9472;sda9    8:9    0  23.3G  0 part 
&#9500;&#9472;sda7    8:7    0  23.3G  0 part 
&#9500;&#9472;sda10   8:10   0  23.3G  0 part 
&#9500;&#9472;sda5    8:5    0  23.3G  0 part 
&#9500;&#9472;sda3    8:3    0   2.8G  0 part [SWAP]
&#9500;&#9472;sda1    8:1    0   499M  0 part /boot/efi
&#9500;&#9472;sda8    8:8    0  23.3G  0 part 
&#9492;&#9472;sda6    8:6    0  23.3G  0 part 

```

Then this:
```
waldo@11:~$ [COLOR="#FF0000"]sudo blkid -o list -c /dev/nul[/COLOR]
[sudo] password for waldo: 
device              fs_type   label      mount point             UUID
-----------------------------------------------------------------------------------------------------
/dev/sda1           vfat      BOOT EFI   /boot/efi               B70F-1399
/dev/sda2           ext4                 /                       0f47f885-3e8b-475b-9082-2ea2c05ff732
/dev/sda3           swap                 [SWAP]                  a64147fb-9025-46ee-b704-c6b7877d28c7
/dev/sda4           ext4                 /mnt/data               a3c5362b-1fb9-44b9-8afb-050980ea65c2
/dev/sda5           ext4                 (not mounted)           b018ef16-2996-4e7a-9725-3ee3d4e91b28
/dev/sda6           ext4                 (not mounted)           e12a55fa-51b8-46dd-b3ba-f8ce802df0dd
/dev/sda7           ext4                 (not mounted)           1c957a29-a0ba-4453-83b9-3bdb67d50fc4
/dev/sda8           ext4                 (in use)                988844a7-a4ec-40ac-b12f-05724ca4c899
/dev/sda9           ext4                 (not mounted)           435cd801-26a4-4fe6-a66f-15c66724df09
/dev/sda10          ext4                 (not mounted)           4d7429d0-2d26-4d49-806b-46629198f13b

```

Same command and different returns... some with odd Mount Points? Then /dev/sda8 "in use" ??? 

The first return on "lsblk" looks like the Blue-line at top of post without the '/lvm/cache', which is where Ubuntu's Disk Usage Analyzer says most of Manjaro's GB's are.  

Enough...

Mike

---

### Post by Dennis N on 2017-10-26
> *  Fixed the third link in previous post.  Looking at that home page again, seems it might be a different format of the fourth link... blog.  Like I said, I haven't dug. 

*  On the '10_linux' copying... Bad Editing... I'm taking all of '10_linux' to a named file... header to ender.  Coping ONLY first menuentry  -word menuentry through closing bracket-  to 'Copy_40_custom' file.  Run "save as" from there.  I've fixed the problem in original post.

Got it.

> *  On naming.  I was getting lost. Noticed one 'name' aspect put in GPartEd when original partitions were made showed up where I needed it.  Went to GPartEd and named them all.  I don't know how many places those names will show, but they show where it's helpful to me.  I thought to do same in GPartEd for 'label' (see where it showed up that might be helpful), but I got scared... want to run UUID only, and who knows what having partition labels laying around might cause to happen.

**Names** only exist in GPT partitioning, and are written into the partition table on your disk. If you replace that OS with another, the Name stays and doesn't change. **Labels** exist within partition's file system in both MBR and GPT partitioning. When you replace the OS with another and formatting is done, the Label is destroyed and you have to make a new one. 

> *  Ubuntu flavors and about every other Ubuntu based OS I've run into... Bohdi Linux... Solus... elementaryOS... Puppy Linux... Linux Mint... KDE Neon.  I figure it's likely all Ubuntu-based OS's have the same affliction. Deep down and dark depths of Ubuntu where no one wants to go any more.  Odd thing... well, surprising at least.  When I put in CentOS-7, then Manjaro, one or the other caused /EFI/ubuntu/grubx64.efi to switch from last entered Ubuntu-type (Ubuntu 16.04 LTS - Budgie-remix - 'hd0,gpt9'... back to first Ubuntu entered (16.04.3 LTS - Unity - 'hdo,gpt2'  ... the original (and still is) GRUB_DEFAULT=0.  Magic 

I wonder if Boot Repair changed these entries? Boot Repair could change the EFI folder names and then rewrite the UEFI boot manager entries. As I have said before, I've never used the boot repair function (only the boot info script), so don't know how it handles multiple Ubuntu OS installs on a computer when it does its repair thing. I'm pretty sure J.A. Watson wrote in one of his columns that this eventually failed when he tried the same thing manually.
-----------------------------------------------------------

You should also give regular Ubuntu 17.10 a try. I installed it and actually like it now that it's switched to Gnome desktop.

I wish you success.

---

### Post by oldfred on 2017-10-26
Boot-Repair would not change name.

Some of the Linux that use Ubuntu have UEFI folders that are /EFI/ubuntu.
Many other flavors use their own name for the folders & entry in UEFI.

Being curious on how grub works (where you may not want to go), I just installed Fedora to see how it handles grub.
They have this in their instructions:
 grub2-install shouldn't be used on EFI systems. The grub2-efi package installs a prebaked grubx64.efi on the EFI System partition, which looks for grub.cfg on the ESP in /EFI/fedora/ whereas the grub2-install command creates a custom grubx64.efi, deletes the original installed one, and looks for grub.cfg in /boot/grub2/.
efi_distributor = bootloader_id; 
Debian does this, so bootloader _id is based on grub_distributor from /etc/default/grub:

It also looks like Fedora has the entire grub.cfg in the ESP, not in /boot folder, but I used a partition install, not its default LVM install.

 bootloader_id="$(config_item GRUB_DISTRIBUTOR | tr A-Z a-z | \ 

Ubuntu hard codes efi_distributor to "ubuntu", so if using Ubuntu's UEFI grub then that is why other verions have "ubuntu" as UEFI entry. But if based on standard grub2 or Debian, may have its own name as UEFI boot name or efi_distributor variable.

I change this in Ubuntu:
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR='Ubuntu16.04_Zesty'
And that does create a new UEFI folder, but grub.cfg with Ubuntu is always the one in /EFI/ubuntu. Hard coded some where like the comment on Fedora.

I label & name all partitions. Particularly those I only mount occasionally or temporarily. I do that with my other installs, so I can rember which partition I have installed them into, although I have written it down (somewhere?).

What is Budgie's entry for this in /etc/default/grub?
GRUB_DISTRIBUTOR=

---

### Post by Dennis N on 2017-10-26
> Boot-Repair would not change name.

So the mystery remains. The official Ubuntu 'flavors' I've used in UEFI systems (Ubuntu, Xubuntu, Lubuntu, Ubuntu-MATE) all use 'ubuntu' as EFI folder name by default. Even the Linux Mint varieties which use Ubiquity installer have 'ubuntu' for their folder name.

I will be watching to see what the answer is to your question:
> What is Budgie's entry for this in /etc/default/grub?
GRUB_DISTRIBUTOR= 


---

### Post by Mike Krall on 2017-10-26
Ubuntu 16.04.3 LTS - Budgie-remix: GRUB_DISTRIBUTOR='lsb_release -i -s 2> /dev/null || echo Debian'

Side note:
With 'Manjaro-broke', my startup process is:  Start button... 'Esc at ASUS screen (brings UEFI menu, I believe... 'neon' at top)... 'Enter' takes to *list-of-all-OS*-menu ('Ubuntu' at top, with * at front)... press-'Enter'... get Ubuntu-unity.  This is with GRUB_DEFAULT=0... /boot/efi/EFI/ubuntu at 'hd0,gpt2' (first OS on disc... first install).  Done it a number of times since 'Manjaro-broke'.

Then...

Pick 'Budgie' out of menu list (last in line... right behind Manjaro at 'hd0,gpt8'... look at /etc/default/grub... get GRUB_DISTRIBUTOR= for 'oldfred' and 'Dennis N'.  While there download updates... didn't look closely... recent Chromium and UEFI firmware... plus ??? (Haven't been in 'Budgie' for weeks).

Reboot... 'Esc' at ASUS screen... 'Enter' at UEFI menu... 'Enter' at *list-all-OS* (with * 'Ubuntu' at top).. get 'Budgie' (not Ubuntu-unity).  Goto /etc/default/grub... no change.  Goto /boot/efi/EFI/ubuntu... now 'hd0,gpt9' 

Reboot... 'Esc' at ASUS screen... 'Enter' at UEFI menu... pick 'Ubuntu-unity' out of list... check /boot/efi/EFI/ubuntu, it's 'hdo,gpt9' (Budgie).  

Got to get to work (other)...

Mike

---

### Post by oldfred on 2017-10-26
Major grub updates or re-installs will rewrite the /boot/efi/EFI/ubuntu/grub.cfg entry to be that install.
I have multiple installs and with each new install it replaces the ubuntu folder & I restore my old grub.cfg configile to be my main working install.

fred@Z170N:~$ lsb_release -i -s
Ubuntu
Then what does Budgie show?

But when I changed name with grub, it gives me a new UEFI entry & /EFI/zesty, but my install of Fedora which actually installed to ESP on sdb seemed to erase some of my UEFI entries originally from ESP on sda.

---

### Post by Mike Krall on 2017-10-26
> **oldfred said:**
> Major grub updates or re-installs will rewrite the /boot/efi/EFI/ubuntu/grub.cfg entry to be that install.
I have multiple installs and with each new install it replaces the ubuntu folder & I restore my old grub.cfg configile to be my main working install.

fred@Z170N:~$ lsb_release -i -s
Ubuntu
Then what does Budgie show?

But when I changed name with grub, it gives me a new UEFI entry & /EFI/zesty, but my install of Fedora which actually installed to ESP on sdb seemed to erase some of my UEFI entries originally from ESP on sda.

About 5 minutes ago I copied /boot/efi/EFI/ubuntu-16-unity into /boot/efi/EFI/ubuntu. So, "lsb_release -i -s" now looks like this:
```
waldo@11:~$ lsb_release -i -s
Ubuntu
waldo@11:~$
```

Wish I hadn't of done that, but I figure running the command 6 min. ago would have returned the same... you?

Not like this is related, but I've got two CentOS in UEFI menu (startup > 'Esc' at ASUS screen).  I'm guessing it's because I ran RHEL equivalent of "sudo update grub" in BIOS-form (before knowing there was a difference) and then in UEFI-form.  On the 'to do' list is to see if I can find any kind of differences in the two.  There are two different /boot/efi/EFI/grub.cfg (equivalent of /boot/grub/grub.cfg in Ubuntu and Manjaro) now... one 'grub.cfg' and then came 'grub2.cfg'.  

Mike

---

### Post by oldfred on 2017-10-26
in # 305 I posted the comment on Fedora and reinstall grub.
It seems there are pre-configured grubx64.efi and the standard grub2 installs the create /boot/grub2/grub.cfg.
So it depends on what your specific distribution is using.

---

### Post by Dennis N on 2017-10-27
Manjaro and Ubuntu both use /boot/grub/grub.cfg for their grub configuration files. Fedora sticks theirs into the EFI system partition at /EFI/fedora/grub.cfg. I never need to update Fedora's grub.cfg as it is automatically updated by Fedora itself.  

Different command is used for Fedora:
[FONT=Courier New]**sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg**[/FONT]
You can make an alias of this by putting
[FONT=Courier New]**alias update-grub='sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg'**[/FONT]
into Fedora's **~/.bashrc** 
Then using command **update-grub** in terminal would update its grub configuration files.

Is Manjaro working now? You said somewhere above that it broke? I just installed 165 updates in Manjaro a few minutes ago. Did you localize the repos to the United States? Makes things faster.

---

### Post by Mike Krall on 2017-10-27
> **Dennis N said:**
> -----------------------------------------------------------

You should also give regular Ubuntu 17.10 a try. I installed it and actually like it now that it's switched to Gnome desktop.

I wish you success.

Off topic 
This is a funny thing.  I originally headed into looking for other Linux OS because I was more comfortable with Ubuntu 6.04, etc. Gnome than Ubuntu w/ Unity.  I found the idea of multi-boot and separate data partition from that interest.  Now that I've messed a little with Xfce, KDE, Cinnamon, Enlightenment, Lxde x ??? (of Peppermint Linux), Pantheon, and both Gnome Classic and Gnome 3 (CentOS-7 has a choice at login) I've come to see what the good of Unity is. Not that I work really well in it (quicker and more fluidly than either Gnome, for sure) but everything about Unity is sharp and clear and distinct (old eyes).  It could be tweaked into a really good general-use desktop. 

Mike

---

### Post by Mike Krall on 2017-10-27
> **Dennis N said:**
> Manjaro and Ubuntu both use /boot/grub/grub.cfg for their grub configuration files. Fedora sticks theirs into the EFI system partition at /EFI/fedora/grub.cfg. I never need to update Fedora's grub.cfg as it is automatically updated by Fedora itself.  

Different command is used for Fedora:
[FONT=Courier New]**sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg**[/FONT]
You can make an alias of this by putting
[FONT=Courier New]**alias update-grub='sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg'**[/FONT]
into Fedora's **~/.bashrc** 
Then using command **update-grub** in terminal would update its grub configuration files.

Is Manjaro working now? You said somewhere above that it broke? I just installed 165 updates in Manjaro a few minutes ago. Did you localize the repos to the United States? Makes things faster.

*  And I still get confused when in CentOS... figuring where grub.cfg is.

**  Thanks for the information and, especially, for 'alias' creation, 'Dennis N'. I've been doing copy/paste for that when in CentOS, and the location of the copy is never convenient.

***  'Manjaro-broke' is still the same.  'oldfred' mentioned maybe Grub.  I think that is right, but maybe it's not gone, gone.  With Disk Management Analyzer saying 18.3 GB of Manjaro's 24.4 GB is in /media/waldo/<UUID>/lvm/cache, I'm wondering if all the writing that was going on (filling up /) caused "root" to shove everything it could into a logical volume.  ???  I'm trying to understand live USB and chroot, etc., well enough to not make a bigger mess. Got to find, then make paper copies of directions, then understand it well enough to do it... what ever "it" turns out to be.

Mike

---

### Post by Dennis N on 2017-10-27
Many newer users aren't familiar with **alias**. Maybe **Jennifer Garner** comes to mind. Anyway, the way that's written, you just type update-grub without sudo and you will be prompted for password.

I must have missed reading how Manjaro is broken. That is bad news. Do you get as far as Manjaro grub, and then Manjaro won't boot from that point? Or does the system fail to boot to Manjaro grub at all? Hopefully fixable with more information or details. (If you already gave all details of the problem, please tell in what post - thanks).

On my somewhat-buggy Asus UEFI the other day, instead of booting to Manjaro on startup, it booted to Ubuntu. Uh-oh. I ran efibootmgr and the Manjaro entry was missing entirely from UEFI. Poof. Just gone. And sometimes, things get renamed. My Korora entry that was once there has been changed to 'other OS'. I almost never start something from the UEFI menu - usually after installing a new OS and get back into my main OS to do any menu entry creation needed and change the boot order back.

---

### Post by Mike Krall on 2017-10-27
*'Dennis N'*... It's not like I put up any information in recently past posts a person could easily work with.  'oldfred' made an educated 'guess'... Grub. 

I thought to try booting Manjaro again tonight.  Boots into Manjaro prior to this one got boot-up lines... one red indicator... and others... then a freeze with blinking ending counting down seconds, then resetting and counting them down again.  What I got tonight (in part):
```
Not syncing: VFS: Unable to mount rootfs on unknown-block (0,0)
CPU: 3 PID: 1 Comm: Swapper/0 Not tainted 4.9.51-1-Manjaro #1
Hardware name... blah, blah
[COLOR="#0000FF"]4-6[/COLOR] = number/letter codes
Call trace:
[COLOR="#0000FF"]8-17[/COLOR] = number/letter codes + dump_stack +0x63.0x81
                                             panic+0e4/0x22d
                                             blah, blah
[COLOR="#0000FF"]18[/COLOR] = Kernel offset: Disabled
_ _ _ [end Kernel panic_ etc.
```

Anyhow... when I figure out how to use Live-USB and chroot into Manjaro (real) and look around and see something looking like anything, if I have questions, I'll holler back.  

I figure I know how to reinstall Grub (have to cross check it a few places to make sure I get it).  I don't want to do that without understanding if recreating boot-abilty will dump me right back into the same Kernel-panic whirlpool... like maybe ought to find 'cause', then dump it, then reinstall Grub (on assumption 'oldfred' "guess" is not one... =]  )  Who knows, maybe I'll disagree...  

And thank you for the concern and offer... 

Mike

---

### Post by Dennis N on 2017-10-28
**Plan B:**

1. Switch default OS in UEFI boot order and use another one that is bootable (Ubuntu?). 
2. Copy any custom menus to it's /etc/grub.d. update grub, reboot and test custom menu entries to see which (if any) might need some fixing or even replacing. If you have Watson-type menu entries (see post #279), those are universal and work anywhere.
3. Creating and using Watson-type custom menu entries will avoid any grub problem with the OS being booted as you are using it's native grub and its own commands. Replace non-working entries with these. (Like Watson does, you could use mainly those - On my Zotac, a number of entries are Watson-type.)

---

### Post by Mike Krall on 2017-10-28
Would advise on updating software: A number of updates... all Grand Unified Bootloader.  Would move machine from 3.12 to 3.14.  I don't know if install would make differences in fixing Manjaro... either of good to bad or bad to good... or ???

Mike

---

### Post by Dennis N on 2017-10-28
> **Mike Krall said:**
> Would advise on updating software: A number of updates... all Grand Unified Bootloader.  Would move machine from 3.12 to 3.14.  I don't know if install would make differences in fixing Manjaro... either of good to bad or bad to good... or ???

Mike

Generally you should install all recommended updates. They have been tested. I should ask on what OS and version were these? I don't recall seeing them. Upgrade to a new grub version (which would reinstall grub) is rare.

---

### Post by Mike Krall on 2017-10-28
I don't have a multi-boot mind, do I?  On Ubuntu 16.04.3 LTS, 'Dennis N'... They came in yesterday sometime (24 hr. +/- of now)

Mike

---

### Post by Mike Krall on 2017-10-29
Figured out how to run Manjaro from Live-usb... [https://wiki.manjaro.org/index.php?title=Restore_the_GRUB_Bootloader#Use_mhwd-chroot]("https://wiki.manjaro.org/index.php?title=Restore_the_GRUB_Bootloader#Use_mhwd-chroot")  Used manual because there was no room to download mwhd-chroot... just as well... the more command line I do, the more sense it makes.

For a while I couldn't figure out where the excess was.  The light went on... hidden files... .xsession-errors to be exact... 17.7 GB all in one little file.

This:
```
xrdb:  "Xft.hinting" on line 19 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 22 overrides entry on line 7
gpg-agent[786]: WARNING: "--write-env-file" is an obsolete option - it has no effect
gpg-agent: a gpg-agent is already running - not starting a new one

(xfce4-session:778): xfce4-session-WARNING **: gpg-agent returned no PID in the variables

(xfce4-session:778): xfce4-session-WARNING **: xfsm_manager_load_session: Something wrong with /home/waldo/.cache/sessions/xfce4-session-11:0, Does it exist? Permissions issue?
Setting up watches.
Watches established.

** (xfce4-clipman:801): WARNING **: Unable to register GApplication: An object is already exported for the interface org.gtk.Application at /org/xfce/clipman

(xfce4-clipman:801): GLib-GIO-CRITICAL **: g_application_get_is_remote: assertion 'application->priv->is_registered' failed

(xfce4-clipman:801): GLib-WARNING **: g_set_application_name() called multiple times

** (xfce4-clipman:801): WARNING **: Clipboard manager is already running.

(blueman-applet:810): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates: assertion 'window->update_and_descendants_freeze_count > 0' failed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Thunar: Failed to initialize Xfconf: Using X11 for dbus-daemon autolaunch was disabled at compile time, set your DBUS_SESSION_BUS_ADDRESS instead


(thunar:1010): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(thunar:1010): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Thunar: Failed to initialize Xfconf: Using X11 for dbus-daemon autolaunch was disabled at compile time, set your DBUS_SESSION_BUS_ADDRESS instead


(mousepad:1082): dconf-WARNING **: failed to commit changes to dconf: Error spawning command line “dbus-launch --autolaunch=f8a7b0e9c0d04b38ada5c88996855ac5 --binary-syntax --close-stderr”: Child process exited with code 1

(mousepad:1082): dconf-WARNING **: failed to commit changes to dconf: Error spawning command line “dbus-launch --autolaunch=f8a7b0e9c0d04b38ada5c88996855ac5 --binary-syntax --close-stderr”: Child process exited with code 1

(mousepad:1082): dconf-WARNING **: failed to commit changes to dconf: Error spawning command line “dbus-launch --autolaunch=f8a7b0e9c0d04b38ada5c88996855ac5 --binary-syntax --close-stderr”: Child process exited with code 1

(mousepad:1082): dconf-WARNING **: failed to commit changes to dconf: Error spawning command line “dbus-launch --autolaunch=f8a7b0e9c0d04b38ada5c88996855ac5 --binary-syntax --close-stderr”: Child process exited with code 1

(mousepad:1082): dconf-WARNING **: failed to commit changes to dconf: Error spawning command line “dbus-launch --autolaunch=f8a7b0e9c0d04b38ada5c88996855ac5 --binary-syntax --close-stderr”: Child process exited with code 1

** [COLOR="#FF0000"]MILES AND MILES OF ABOVE... ENDING ABRUPTLY WITH[/COLOR] >

(mousepad:1082): dconf-WA
```

I mean, how many lines does there have to be to make 17.7 GB? 

Now I need to figure out what to do with it and if there are any related files having 'error' stuff in them I should have information from and/or empty.  

I'm wondering if deleting most of 'xsession-errors'... keep a little bit of it for posterity... if there is enough room to let /EFI back out of where ever it got cramed in?  Probably not.  Probably it's gone some how.   

Does "grub-install" and/or "update-grub" make files it needs if those don't exist?

Mike

---

### Post by Dennis N on 2017-10-29
> .xsession-errors to be exact... 17.7 GB all in one little file.

Are you sure you are reading the size correctly? Mine is 4.3 K.
```
[dmn@Sydney ~]$ ls -alh .xsession-errors
-rw------- 1 dmn dmn 4.3K Oct 29 07:21 .xsession-errors

```
and the contents are:
```
[dmn@Sydney ~]$ cat .xsession-errors
xrdb:  "Xft.hinting" on line 19 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 22 overrides entry on line 7

(xfce4-session:732): xfce4-session-WARNING **: xfsm_manager_load_session: Something wrong with /home/dmn/.cache/sessions/xfce4-session-Sydney:0, Does it exist? Permissions issue?
Setting up watches.
Watches established.

** (xfce4-clipman:753): WARNING **: Unable to register GApplication: An object is already exported for the interface org.gtk.Application at /org/xfce/clipman

(xfce4-clipman:753): GLib-GIO-CRITICAL **: g_application_get_is_remote: assertion 'application->priv->is_registered' failed

(xfce4-clipman:753): GLib-WARNING **: g_set_application_name() called multiple times

(xfsettingsd:752): xfsettingsd-WARNING **: Failed to get the _NET_NUMBER_OF_DESKTOPS property.
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `XfcePanelImage::force-gtk-icon-sizes' of type `gboolean' from rc file value "((GString*) 0x1c75780)" of type `GString'

(pamac-tray:761): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates: assertion 'window->update_and_descendants_freeze_count > 0' failed

(wrapper-2.0:880): Gtk-WARNING **: Negative content width -7 (allocation 1, extents 4x4) while allocating gadget (node button, owner GtkButton)

(wrapper-2.0:886): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 29
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `XfcePanelImage::force-gtk-icon-sizes' of type `gboolean' from rc file value "((GString*) 0x18546c0)" of type `GString'

(wrapper-2.0:893): Gtk-WARNING **: Negative content width -1 (allocation 1, extents 1x1) while allocating gadget (node button, owner PulseaudioButton)

```
It's just for the current session. _I would ignore all this scary stuff unless you experience a problem._
FWIW, If you should want another plan back to normalcy, **plan C** is to reinstall Manjaro after saving its custom menus to your data partition for reuse. My **plan B** is detailed in post  #316.

---

### Post by Mike Krall on 2017-10-29
> **Dennis N said:**
> Are you sure you are reading the size correctly? Mine is 4.3 K.
```
[dmn@Sydney ~]$ ls -alh .xsession-errors
-rw------- 1 dmn dmn 4.3K Oct 29 07:21 .xsession-errors

```
and the contents are:

It's just for the current session. _I would ignore all this scary stuff unless you experience a problem._
FWIW, If you should want another plan back to normalcy, **plan C** is to reinstall Manjaro after saving its custom menus to your data partition for reuse. My **plan B** is detailed in post  #316.

Yup... real sure... Live-USB  trip shows:

.xsession-errors... 17.7GB (17,692,565,504 bytes)... 4,497,352 lines

Or, it did... I dumped all of it excepting the lines looking like the lines in your 'xsession-errors'  Only regret is likely never to know what or how all those bytes got into that file. 

It seems I can go a number of ways from here... your mentioned "Plan B" (Post #316) and/or "Plan C" (besides the Manjaro 17.0.4 Live-usb, I've got an iso_image for Manjaro 17.0.6).  

Might also follow Manjaro "Restore Grub Bootloader" [https://wiki.manjaro.org/index.php?t...se_mhwd-chroot]("https://wiki.manjaro.org/index.php?t...se_mhwd-chroot")  

I'll have to do some figuring = planning.

Mike

---

### Post by Dennis N on 2017-10-29
> Yup... real sure... Live-USB trip shows:
.xsession-errors... 17.7GB (17,692,565,504 bytes)... 4,497,352 lines

There is an explanation and two solutions here (dates from April):
[https://forum.manjaro.org/t/xsession-errors-keeps-growing/22068](https://forum.manjaro.org/t/xsession-errors-keeps-growing/22068)
I would use the second one.
AFAIK, I'm not affected.

Also Google ".xsession-errors is huge "
for more reports to read (mostly Ubuntu, and from years ago).

---

### Post by Mike Krall on 2017-10-30
'oldfred'... Post #305:

> t also looks like Fedora has the entire grub.cfg in the ESP, not in /boot folder, but I used a partition install, not its default LVM install.

My CentOS-7 is the same... same partition install, too.

> I label & name all partitions. Particularly those I only mount occasionally or temporarily. I do that with my other installs, so I can rember which partition I have installed them into, although I have written it down (somewhere?).

Would you example me your 'name' and 'label' system, 'oldfred'?

Mike

---

### Post by Mike Krall on 2017-10-30
> **Dennis N said:**
> There is an explanation and two solutions here (dates from April):
[https://forum.manjaro.org/t/xsession-errors-keeps-growing/22068](https://forum.manjaro.org/t/xsession-errors-keeps-growing/22068)
I would use the second one.
AFAIK, I'm not affected.

Also Google ".xsession-errors is huge "
for more reports to read (mostly Ubuntu, and from years ago).

Thank you for that... 

I ran this search (there are more than first hit I haven't looked at):  [https://www.google.com/search?q=Arch+Linux%2C+.xsession-errors+growing&oq=Arch+Linux%2C+.xsession-errors+growing&aqs=chrome..69i57j69i64.31542j0j7&client=ubuntu&sourceid=chrome&ie=UTF-8]("https://www.google.com/search?q=Arch+Linux%2C+.xsession-errors+growing&oq=Arch+Linux%2C+.xsession-errors+growing&aqs=chrome..69i57j69i64.31542j0j7&client=ubuntu&sourceid=chrome&ie=UTF-8")
and found this:  [https://bbs.archlinux.org/viewtopic.php?id=227774]("https://bbs.archlinux.org/viewtopic.php?id=227774")

I'm dithering... trying to talk to CentOS folks about tweaking /etc/default/grub to maybe cause CentOS more comfort in a multi-boot world.  They really are server-folks and I'm pretty-odd-duck-ish there.  I'm going to follow the above Arch Linux link a little.  Make a run at "grub-install" on Manjaro... reinstall with 17.0.6 if problems with that (started with 17.0.4... added updates). 

Just found Manjaro '.xsession-errors.old' with a lot of generated lines in it (nothing like 17.7 GB, but big-ish)... last night was empty.  Dumped the repetition out.  At least I can deal with it though GPartEd... not have to "sudo mount... etc." my way around... or at least I think I'm dealing with it this way... ???  We'll see.  

Mike

---

### Post by oldfred on 2017-10-30
When I reformat a partition, I often forget to rename it, so I now see several partitions with out labels, one is Artful.
I normally edit both labels with Disks if not when I created it with gparted.

  Label is the labels that both gpt & MBR would show from formatting a partition. PARTLABEL is from gpt(GUID) partition label.
```
sudo blkid -c /dev/null -o list
[sudo] lsblk -o NAME,LABEL,PARTLABEL,SIZE,MOUNTPOINT,UUID
NAME   LABEL   PARTLABEL    SIZE MOUNTPOINT UUID
sda                       232.9G            
&#9500;&#9472;sda1 ESP     ESP         49.8G /boot/efi  D966-440A
&#9500;&#9472;sda2         System      30.3G /          5c1e1a3f-261f-4da5-a0c2-8f479b3039de
&#9500;&#9472;sda3 ISO     ISO         20.5G /media/fre ab916e15-8a74-4d6e-a0b1-32718a505dc7
&#9492;&#9472;sda4 root2   root2       25.4G            85a3d0a5-d4f8-473e-b89c-24c2cba6631a
sdb                       931.5G            
&#9500;&#9472;sdb1 ESP_B   EFI System Partition
&#9474;                          48.9G            F496-1330
&#9500;&#9472;sdb2 zesty   zesty       30.3G            a9bd9a65-bc8c-41b1-95b1-2dceb66b2652
&#9500;&#9472;sdb3 ISO_b   ISO_b       49.8G            c395f36d-5e02-4913-a904-e336054b2eff
&#9500;&#9472;sdb4 backup_b
&#9474;              backup_b    49.8G /media/fre dd4e4a2e-4785-4441-91b0-28234b98e625
&#9500;&#9472;sdb5         server      30.3G            b76dc590-99a3-4e34-af35-e0dd43507232
&#9500;&#9472;sdb6 data    data       205.1G /mnt/data  f9537995-8b44-4abb-b5fb-ec27023f57b2
&#9500;&#9472;sdb7                      2.1G [SWAP]     3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd
&#9500;&#9472;sdb8         yakkety     25.4G            6c042846-fc6c-4f5b-80fc-7aa678cf09b7
&#9492;&#9472;sdb9 Fedora  Fedora      25.4G            5326d262-26af-4b38-a523-b0f4d261f1a4
```

---

### Post by Mike Krall on 2017-10-30
'Dennis N'...

Since running Manjaro, every time using 'Thunar Root', a very short time later my laptop fan kicks up... then up again.  I'm guessing this is the endless writing going on.  Whether I can "fix" that or not, I don't know.  The number of times I need to go into "Thunar Root" is fairly high, compared to the Ubuntu's.  I'm wondering a thing... pages back you showed me to editing /etc/fstab to ease getting around... replaced "umask=0077" with "defaults".

My Ubuntu /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=0f47f885-3e8b-475b-9082-2ea2c05ff732 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
[COLOR="#0000CD"]UUID=B70F-1399  /boot/efi       vfat    defaults      0       1[/COLOR]
# swap was on /dev/sda3 during installation
UUID=a64147fb-9025-46ee-b704-c6b7877d28c7 none            swap    sw              0       0
# /mnt/data was on /dev/sda4 during installation
UUID=a3c5362b-1fb9-44b9-8afb-050980ea65c2 /mnt/data ext4 auto,users,rw,relatime 0 2

```

This is my Manjaro /etc/fstab (edited to get things labeled... uncommented lines identical to /fstab.backup - the original):
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
# /boot/efi was on /dev/sda1 during installation 
[COLOR="#0000CD"]UUID=B70F-1399                            /boot/efi      vfat    defaults,noatime 0 2[/COLOR]
# / was on /dev/sda8 during installation
UUID=988844a7-a4ec-40ac-b12f-05724ca4c899 /              ext4    defaults,noatime,discard 0 1
# swap was on /dev/sda3 during installation
UUID=a64147fb-9025-46ee-b704-c6b7877d28c7 swap           swap    defaults,noatime,discard 0 0
# /mnt/data was on /dev/sda4 during installation
UUID=a3c5362b-1fb9-44b9-8afb-050980ea65c2 /mnt/data ext4 auto,users,rw,relatime 0 2
tmpfs                                     /tmp           tmpfs   defaults,noatime,mode=1777 0 0
```

When I first saw the 'defaults' in the '/boot/efi' line, I thought it would act like switching the Ubuntu's 'umask=0077' to 'defaults' but it doesn't seem to.  Is there something else needing done?

Mike

[COLOR="#FF0000"]Edit:[/COLOR]  Forgot to post again...  from last night.  Looks like I'm about half-trained to it...  =[

---

### Post by Mike Krall on 2017-10-30
Thank you, 'oldfred'...

Mike

---

### Post by Dennis N on 2017-10-31
> I'm wondering a thing... pages back you showed me to editing /etc/fstab to ease getting around... replaced "umask=0077" with "defaults"...When I first saw the 'defaults' in the '/boot/efi' line, I thought it would act like switching the Ubuntu's 'umask=0077' to 'defaults' but it doesn't seem to. Is there something else needing done?
For me, 'defaults' in the /boot/efi line gives the same permissions for folders and files in the EFI system partition in both OSes: **rwxr-xr-x**

---

### Post by Mike Krall on 2017-10-31
> **Dennis N said:**
> For me, 'defaults' in the /boot/efi line gives the same permissions for folders and files in the EFI system partition in both OSes: **rwxr-xr-x**

Thank you, 'Dennis N'...

---

### Post by Mike Krall on 2017-10-31
Well, things are a lot better.  I used the manual section of 'Restore Grub Bootloader'... [https://wiki.manjaro.org/index.php?t...se_mhwd-chroot]("https://wiki.manjaro.org/index.php?t...se_mhwd-chroot").  Got same 'fails' as noted at end of link's directions.  Went through them  to the end... installed 'efivarfs' and then everything worked as supposed to.  Did all updates and now in Manjaro Linux 17.0.6 - stable. 

Then...

Went to mess with custom-menuentry and thought, "I ought to go look at ~/.xsession-errors.  There were a few more lines there than when I left, but only a handful. Looked like it had started writing, then stopped.  Tried to look at ~/.xsession-errors.old.  For some unknown reason, though the permissions are Owner - rw, it won't (and hasn't) open without opening ~/ with Thunar Root.  And then it still wouldn't open due to the root window not opening with 'hidden  files' checked.  I think checking 'show hidden files' in the root window disables the root aspect.  Anyhow had Thunar Root open for less than 2 minutes, likely way less, and ~/.xsession.errors had accumulated nearly 600,000 lines.  Deleted them all.  Now that file will no longer open.  Can get there with Nano, though.  I'm going to have to take this to Manjaro Forums... see about fixing it... or doing a clean install of Manjaro 17.0.6 - stable if that makes better sense.  Now I wish I had the errors to show them.     

I'll mess with making custom menuentry work-files while I work on that...

The old expression (one of my all time favorites), "I was looking for something to do, anyhow.", comes to mind...  =[  

Mike

---

### Post by Mike Krall on 2017-11-02
> **Mike Krall said:**
> Well, things are a lot better.  I used the manual section of 'Restore Grub Bootloader'... [https://wiki.manjaro.org/index.php?t...se_mhwd-chroot]("https://wiki.manjaro.org/index.php?t...se_mhwd-chroot").  Got same 'fails' as noted at end of link's directions.  Went through them  to the end... installed 'efivarfs' and then everything worked as supposed to.  Did all updates and now in Manjaro Linux 17.0.6 - stable. 

Then...

Went to mess with custom-menuentry and thought, "I ought to go look at ~/.xsession-errors.  There were a few more lines there than when I left, but only a handful. Looked like it had started writing, then stopped.  Tried to look at ~/.xsession-errors.old.  For some unknown reason, though the permissions are Owner - rw, it won't (and hasn't) open without opening ~/ with Thunar Root.  And then it still wouldn't open due to the root window not opening with 'hidden  files' checked.  I think checking 'show hidden files' in the root window disables the root aspect.  Anyhow had Thunar Root open for less than 2 minutes, likely way less, and ~/.xsession.errors had accumulated nearly 600,000 lines.  Deleted them all.  Now that file will no longer open.  Can get there with Nano, though.  I'm going to have to take this to Manjaro Forums... see about fixing it... or doing a clean install of Manjaro 17.0.6 - stable if that makes better sense.  Now I wish I had the errors to show them.     

I'll mess with making custom menuentry work-files while I work on that...

The old expression (one of my all time favorites), "I was looking for something to do, anyhow.", comes to mind...  =[  

Mike

Have I done something stupid?  Person about has to say, "Yes".  And it's "Off Topic", to boot. 

When I was reestablishing Grub in Manjaro 17.0.4, I was 'offered' the opportunity to 'update' to 17.0.6 along with.  Bad Idea.  I've got an excuse, but nobody (me either) wants to hear it.  So 17.0.6 generates tons of '.xsession-errors' but not as virulently as 17.0.4.  I did a lot of reading and some amateur testing & file copying.  Thunar really sets off the line-generation (like approx. 324,000 in a timed 10 seconds). Found later, if left to it's own devices, 'Mousepad' makes lots of lines in .'xsession-errors'... originally thought not... but may be missing a point somewhere.  Also found I'm missing a file and a lot of work on that produced " 0 ".  The complexity of the question I'd need to ask and answers I'd need to understand has kept me from stating it at Manjaro Forum.  Started in this morning to do it anyhow when I found Mousepad had crammed Manjaro " / " full and there was no longer a bootable Manjaro (both UEFI menu and Boot menu have listings, though).   

I can redo Grub and have an OS that needs fixing.  Or I can install 17.0.6 and hope it has gotten beyond the line-writing thing.  If it hasn't I would tend not to just shut '.xsession-errors' off (/dev/null dump), but look for a fix.  The problem is, it's not like Xfce-Thunar-Mousepad hasn't had iterations of this problem for a while and I've got limited ability to do anything about it.  

Anyhow... 

New Install:  I mistrust installing Manjaro 17.0.6 over the top of Manjaro 17.0.4.  I'm thinking going into Manjaro with Live-USB and dumping it's entries in /boot/efi... dump Manjaro /boot/grub/grub.cfg or just it's menuentry's or even all of it's /boot/grub, might be good to do.  Anyhow, I'm guessing - *and would like verification and/or ideas and/or thoughts and/or direction* -  simply deleting Manjaro partition ( /dev/sda8 ) is going to leave remnants and I don't know if the reality of Manjaro having an empty /boot/efi is going to account for that, or if a new install is going to rewrite everything needing rewritten... Oh the trials and tribulations of the uninformed !!!

'Dennis N' - Have you had any problems with Manjaro 17.0.6... '.xsession-errors or otherwise?

Mike

---

### Post by Dennis N on 2017-11-03
I haven't had any problems here. There is one .xsession-errors for current session and also for the previous session. Always small.

```
[dmn@Zotac ~]$ ls -alh | grep xsession
-rw-------  1 dmn  users 4.5K Nov  2 21:48 .xsession-errors
-rw-------  1 dmn  users 5.1K Oct 30 21:32 .xsession-errors.old

```
I never run GUI as root - only terminal bash commands, and nano text editor. That goes for Ubuntu as well.

Maybe refrain from starting Thunar or other gui applications as root and see if the writing to that file still continues. I am not even sure what is the recommended way to run a GUI application as root in Arch/Manjaro.

Did you post about this on the Manjaro forum? What did they say?

As to different isos, once all updates are done, they all would all have the same versions of installed applications, so it should not matter which one you use to install. Manjaro installed from 15.10 is the same as 17.04 once updated. That's how rolling release works.

---

### Post by Dennis N on 2017-11-03
> New Install: I mistrust installing Manjaro 17.0.6 over the top of Manjaro 17.0.4. I'm thinking going into Manjaro with Live-USB and dumping it's entries in /boot/efi... dump Manjaro /boot/grub/grub.cfg or just it's menuentry's or even all of it's /boot/grub, might be good to do. Anyhow, I'm guessing - and would like verification and/or ideas and/or thoughts and/or direction - simply deleting Manjaro partition ( /dev/sda8 ) is going to leave remnants and I don't know if the reality of Manjaro having an empty /boot/efi is going to account for that, or if a new install is going to rewrite everything needing rewritten... Oh the trials and tribulations of the uninformed !!!
No need to delete any partitions. For reinstall, just install root file system to the same partition you used before. Install grub bootloader files to same EFI system partition. When you specify formatting of the root partition during installation, that erases any traces of previous OS.

---

### Post by Mike Krall on 2017-11-03
Thanks for the help, Dennis...

I have not posted about this on Manjaro forum. If I can get it down to a small post (mentally, it's a really big-seeming thing to me) I'll do it. I should do it.  I'd find out some things.  

When I rt.-clk. a file in Ubuntu, there is an "Open as Administrator" option.  I've used it a lot.  I assumed (you know how that goes?) "Thunar Root" was same.  As I was typing this last, a thing dawned... "Opening" is different than "Editing"... which Thunar is/does.  I'll have to get around in Manjaro more than I have (not much)... find the differences.  I don't want to be building/moving custom menuentry's in Manjaro with a ticking, line-writing, time-bomb about to go off. There's Nano and there is CLI.  I may need to ask about CLI correctness in relation to permissions but maybe I've got stuff and examples on that already... via following 'oldfred' all over the internet... =]

And thanks for the line-out on reinstall.  Too late tonight, but it will be good exercise when I can. 

Mike

---

### Post by Dennis N on 2017-11-03
I was able to confirm the problem when I opened a folder as root by right click in the Thunar window. I then opened a text file in that folder in Mousepad. That alone resulted in 40 mB added to .xsession-errors. When I close this down, the writing to .xsession-errors stops.

Solution would be don't open files in Mousepad as root.

I didn't test other GUI editors. If you really want a GUI to edit as root, try geany instead and see if the same thing happens.

```
[dmn@Zotac ~]$ ls -lah | grep xsession
-rw-------  1 dmn  users  40M Nov  3 06:00 .xsession-errors
-rw-------  1 dmn  users 5.5K Nov  2 22:50 .xsession-errors.old
```

---

### Post by Mike Krall on 2017-11-03
I think maybe I just need to learn other procedures.  I've used Mousepad/Thunar as root more to look into directories and at files than anything else, by far.  

I noticed a thing in Manjaro 17.0.6 before it choked itself to death...  files without 'user' permissions.  A rt.-clk. had a new entry.  Something like "Open with permissions".  I tried that.  It popped a window with four choices.  Looked like it was set for "Enable".  Didn't open the files, though.  There was another choice... "Force Enable"... I didn't get that tried. 

What are the common (sensible?) ways to look at directories/files that don't have user permissions?

Mike

---

### Post by Dennis N on 2017-11-03
> What are the common (sensible?) ways to look at directories/files that don't have user permissions?
Like /boot/grub/grub.cfg in Manjaro, which is owned by root and with no read permission for 'other' (so you are unable to copy), sudo cp grub.cfg to somewhere in your home folder, then you can change owner of the copy and open it to read and copy from with text editor in normal use mode.
Directories without execute (can't open) or read (can't list) permission, use your admin. privileges (sudo) in terminal with your commands.

---

### Post by Mike Krall on 2017-11-03
> **Dennis N said:**
> Like /boot/grub/grub.cfg in Manjaro, which is owned by root and with no read permission for 'other' (so you are unable to copy), sudo cp grub.cfg to somewhere in your home folder, then you can change owner of the copy and open it to read and copy from with text editor in normal use mode.
Directories without execute (can't open) or read (can't list) permission, use your admin. privileges (sudo) in terminal with your commands.

Just to say:  

Ubuntu (with "defaults" in /etc/fstab  /efi/boot line)  /boot/grub/grub.cfg opens without root and  is Owner - root, Group - root, Other... none,   and all "read only".  Same "defaults" in Manjaro /etc/fstab /efi/boot line... grub.cfg has different file icon and also has "X"...  does not open without root...  has  Owner-Group-Other as root-Read and write... root- None...  -- None.  Differences in approach is what I connect it to, but not being able to open that Manjaro file to copy/paste w/o being root is where the .xsession-errors line-writing-starting started... =]

That was tough to write... persons finding "confusion", please notify and I'll try again. 

Mike

---

### Post by Dennis N on 2017-11-03
Right. as soon as you open mousepad from root file manager window, then it pours messages into .xsession-errors. It's a bug in mousepad, I assume. If you browse in file manager to /boot/grub, use the 'open terminal' option in Thunar. and in terminal run sudo cp grub.cfg to copy that file to a work folder in your home folder. You have to use sudo, because only owner (root) has read (and copy) permission. Once copied, change owner of your copied file so you can open it without using root permissions in a text editor. Then you can copy out the menu entries. I like geany for a GUI text editor, but which you use is up to you. It's also good for HTML work if you do any of that.

---

### Post by Mike Krall on 2017-11-04
> **Dennis N said:**
> Right. as soon as you open mousepad from root file manager window, then it pours messages into .xsession-errors. It's a bug in mousepad, I assume. If you browse in file manager to /boot/grub, use the 'open terminal' option in Thunar. and in terminal run sudo cp grub.cfg to copy that file to a work folder in your home folder. You have to use sudo, because only owner (root) has read (and copy) permission. Once copied, change owner of your copied file so you can open it without using root permissions in a text editor. Then you can copy out the menu entries. I like geany for a GUI text editor, but which you use is up to you. It's also good for HTML work if you do any of that.

Thank you...

I've got above post into my /mnt/data Permissions-'cp'-Nano file.  Spent time last night working with Nano, both via descriptive and hands-on.  I had no idea Nano was able to mouse-high light- rt.clk.-copy/paste.  Found need for Shift+Ctrl+v to paste outside info into Nano.  Not found CLI to do that... looking more. 

Looking at permissions in relation to making custom-menuentry in a work-directory ( /mnt/data )...  I've got 2 files.  One, after copy-paste of 40_custom, morphed into a 'shell script'.  The other did not... remains as 'plain text'.  There are differences in permission between the two.  And both of those permissions are different than permissions of /etc/grub.d and files within.  Only thing I know to do is build custom-menuentry... clk. 'save as'... name it... define place... and select.  I never looked at permissions of the created file in /etc/grub.d when doing this prior to Manjaro breaking.  Can you say if 'local permissions' are adopted or not?  If not, do custom-menuentry permissions need changed?

/etc/grub.d (in Ubuntu-unity)...
```
$ ls -l /etc/grub.d
total 84
-rwxr-xr-x 1 root root  9791 Jan 13  2017 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root 12512 Mar  1  2017 10_linux
-rwxr-xr-x 1 root root 11082 Jan 13  2017 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 Jan 13  2017 30_os-prober
-rwxr-xr-x 1 root root  1418 Jan 13  2017 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jan 13  2017 40_custom
-rwxr-xr-x 1 root root   216 Jan 13  2017 41_custom
-rw-r--r-- 1 root root  2410 Oct 13 19:22 bkp25_custom
-rw-r--r-- 1 root root   483 Jan 13  2017 README

```
Two different work-files in /mnt/data Menuentry work-folder 
```
-rw-r--r-- 1 waldo waldo 215 Nov  4 10:57 /home/waldo/Documents/LINUX_DOCS/Menuentries/Copy_40_custom

AND

-rw-rw-r--. 1 waldo waldo 214 Nov  4 00:20 /home/waldo/Documents/LINUX_DOCS/Menuentries/Copy_40-custom.txt

```
Mike

---

### Post by Dennis N on 2017-11-04
> Found need for Shift+Ctrl+v to paste outside info into Nano. Not found CLI to do that... looking more. 
In Nano, right-click and choose 'Paste', or use the terminal menu: Edit > Paste.
> One, after copy-paste of 40_custom, morphed into a 'shell script'. The other did not...
A shell-script is a text document that has **#!/bin/bash** in first line. path must be correct. 
> Can you say if 'local permissions' are adopted or not? If not, do custom-menuentry permissions need changed?
No. A file initially gets the default permissions based on the OS defaults. Those wouldn't change until changed by a chmod operation. Permissions stay with the file. Default can vary depending on the OS. Yours in /etc/grub.d are good. Same permissions as I have there.

---

### Post by Mike Krall on 2017-11-04
Thanks, Dennis...

Might get new- Manjaro in tonight... but then...  ???

I believe I've got making of custom-menuentry figured out to avoid Thunar-root/Mousepad, and get it to fit expected configuration correctly. 

First, Manjaro custom-menu... then Ubuntu-16.04-unity.  If primary menuentry from Ubuntu-unity doesn't want to stick, instead of messing and messing with it as I did last time,  I'll try primary menuentry for it from Manjaro's 
30_os-prober section of /boot/grub/grub.cfg... go from there. 

Mike

---

### Post by Mike Krall on 2017-11-07
'Dennis N'...

When (if) you did the Manjaro Nov 4 update, did you have problems afterwards?

Mike

---

### Post by Dennis N on 2017-11-07
> **Mike Krall said:**
> When (if) you did the Manjaro Nov 4 update, did you have problems afterwards?Mike
I haven't noticed any problems (3 computers updated for MATE and XFCE).

---

### Post by Mike Krall on 2017-11-07
Thanks, 'Dennis N'

References:

[https://forum.manjaro.org/t/unable-to-login-after-last-update/34193/6]("https://forum.manjaro.org/t/unable-to-login-after-last-update/34193/6")
[https://forum.manjaro.org/t/laptop-not-working-anymore/34090/10]("https://forum.manjaro.org/t/laptop-not-working-anymore/34090/10")
[https://forum.manjaro.org/t/stable-update-2017-11-04-kernels-gnome-deepin-mate-mesa-libreoffice/34030/31https://forum.manjaro.org/t/laptop-not-working-anymore/34090/10]("https://forum.manjaro.org/t/stable-update-2017-11-04-kernels-gnome-deepin-mate-mesa-libreoffice/34030/31https://forum.manjaro.org/t/laptop-not-working-anymore/34090/10")

Mike

---

### Post by Mike Krall on 2017-11-07
"A Comedy of Errors"...  If a person doesn't think what a check box might cause, they will find out later what it did. 

'Manual install' Manjaro 17.0.6 to replace 17.0.4 (the money move... "my choice" department) and 'format' (the check box) Swap-partition, instead of 'keep' (the other alternative), will install Manjaro, well and truly.  But, oh the poor 'multi-distros'.  Sloooooow boot (but does)... about 1 min. 30 sec. +/-.  So, I'm figuring it's a Manjaro thing (see post above) and/or another Grub thing, and/or ??? Run around, run around...  

It's " ??? ".  The 'swap' partition 'format' causes a new UUID to generate... fine for Manjaro, but not for "others".  Got that fixed (in "others" /etc/fstab's). 

Manjaro is at 17.0.4 now (figuring previous version worked... no change), and not set into /mnt/data system.  I'll put 17.0.6 back in... NOT reformat 'swap' when asked, and get it set into /mnt/data... again.  Then, in theory, establish custom-menus... 

In closing... a thing I heard a long time ago from a friend...  "In theory, yes... but everyone knows, 'in theory' means not really".  We'll see what tomorrow brings. At least... perhaps... we are back in the world of 'Separate-data-partitions'

Mike

---

### Post by Mike Krall on 2017-11-09
This is direct copy of the linux and initrd lines from (bottom of page): 
[https://help.ubuntu.com/community/Grub2/CustomMenus]("https://help.ubuntu.com/community/Grub2/CustomMenus")

linux /vmlinuz root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff{
initrd /initrd.img

This is direct copy of Ubuntu-unity 10_linux, but the forum here disallows more than single space... in the editor the two /boot are lined up, not offset as seen.   
linux   /boot/vmlinuz-4.10.0-38-generic.efi.signed root=UUID=0f47f885-3e8b-475b-9082-2ea2c05ff732 ro  quiet splash $vt_handoff
initrd  /boot/initrd.img-4.10.0-38-generic

Two questions:

*  Curly bracket at end of Grub2/CustomMenuentry's  'linux' line...  It is not a mistake, but what does it do? 

*  The two sets of linux - initrd lines have different spacing between end of linux - initrd and /.  Ubuntu-unity is set at Tab8 and Tab8, where CustomMenuentry is set at Tab8 and single space.  Looking at Ubuntu-unity 10_linux, then 30_linux entries (doing same in Manjaro), linux and initrd lines are consistent in 10_linux and 30_linux between OS's...  10_linux is Tab8 and Tab8...  30_linux is Tab8 and single space.  Does it make a difference which form is used in custom-menuentry's?  

Mike

---

### Post by oldfred on 2017-11-09
There is python which uses spaces & indents to separate sections of code.
But in C they use {} to separate sections of code.

So the grub stanzas are to be more C code like. Big parts of grub are coded in C. 

I have seen & copy pasted grub lines with different spacing on each line. 
It may be just that it has to be a new line?

---

### Post by Mike Krall on 2017-11-09
Thanks, 'oldfred'...

Mike

---

### Post by Mike Krall on 2017-11-10
Well, I got Manjaro custom-menuentry in and running.  A lot of back 'n ferth, though.  Did figure how to use Nano to edit and have the spacing from end of closing " } " to '### END, etc.' Ran cursor to left edge... ran it down to " } "... arrow down one more... where cursor is, is definition of end-of-file.  

A funny thing...  didn't get the end of custom-menuentry right the first time... one extra space 'cause I was thinking where the cursor was would be where '### END, etc.' would start.  Tried to edit directly in /etc/grub.d with "sudo nano..." and it wouldn't make the change (did make unexecutable first).  Had to goto original shell-script file and do it there, then 'cp' again to /etc/grub.d... check... make executable... check... 'update-grub'... check /boot/grub/grub.cfg... reboot... choose custom-menuentry... it boots and is OK.

Too late to do same with Ubuntu 16.04.3 LTS.  I'll try Ubuntu's 10_linux menuentry first, but I'm thinking I'll need to use Manjaro's 30_os-prober entry... or, that' my guess.

An aside... Odd thing...  Somewhere recently... between getting a Grub2 update and/or changing CentOS 'GRUB_DEFAULT=save' to 0... /boot/grub/grub.cfg in all Ubuntu's (5 of 7) changed CentOS entries.  Prior to, the primary menuentry was the CentOS 'Rescue' entry.  Now it's the regular menuenty.  Odder still... Manjaro is still showing CentOS 'Rescue' as primary in Manjaro's 30_os-prober.  While Manjaro was broke (not visible to Grub) my Grub menu was running out of Ubuntu 16.04 and CentOS would boot from that menu (prior had to boot it out of UEFI menu).  

'Dennis N'...  Has Manjaro not done recent Grub update yet (I tried looking and don't know where to find stuff like that).

Mike

---

### Post by Dennis N on 2017-11-10
> Too late to do same with Ubuntu 16.04.3 LTS. I'll try Ubuntu's 10_linux menuentry first, but I'm thinking I'll need to use Manjaro's 30_os-prober entry... or, that' my guess.
I found Manjaro won't use the entry copied from Ubuntu's grub.cfg without some minor editing. I remove the following lines, or else got warnings when booting:

[B]recordfail
gfxmode $linux_gfx_mode
[/B]
But I think you can use entry from Manjaro grub.cfg without changes. 
> An aside... Odd thing... Somewhere recently... between getting a Grub2 update and/or changing CentOS 'GRUB_DEFAULT=save' to 0... /boot/grub/grub.cfg in all Ubuntu's (5 of 7) changed CentOS entries. Prior to, the primary menuentry was the CentOS 'Rescue' entry. Now it's the regular menuenty. Odder still... Manjaro is still showing CentOS 'Rescue' as primary in Manjaro's 30_os-prober. While Manjaro was broke (not visible to Grub) my Grub menu was running out of Ubuntu 16.04 and CentOS would boot from that menu (prior had to boot it out of UEFI menu). 
 
May be partly due to CentOS updating grub. CentOS being in Fedora/RedHat family, maybe should use Watson's chainloading. Otherwise, you will soon need to edit the custom entry to reflect kernel version changes. Also, I see no reason to change CentOS GRUB_DEFAULT. Just leave it set to 0, since newest is always on top.   
> 'Dennis N'... Has Manjaro not done recent Grub update yet (I tried looking and don't know where to find stuff like that).
Yes: Look in Pamac > View History
```
[2017-11-06 05:24] [ALPM] upgraded linux49 (4.9.59-1 -> 4.9.60-1)
```
which forces an update-grub. Will not affect custom menu entries, however. Manjaro entry will continue to be correct unless you optionally switch to another kernel entirely, like kernel 4.13 in which case you need to do a one-time edit of the custom entry.

---

### Post by Mike Krall on 2017-11-10
> **Dennis N said:**
> I found Manjaro won't use the entry copied from Ubuntu's grub.cfg without some minor editing. I remove the following lines, or else got warnings when booting:

[B]recordfail
gfxmode $linux_gfx_mode
[/B]
But I think you can use entry from Manjaro grub.cfg without changes. 
 
May be partly due to CentOS updating grub. CentOS being in Fedora/RedHat family, maybe should use Watson's chainloading. Otherwise, you will soon need to edit the custom entry to reflect kernel version changes. Also, I see no reason to change CentOS GRUB_DEFAULT. Just leave it set to 0, since newest is always on top.   

Yes: Look in Pamac > View History
```
[2017-11-06 05:24] [ALPM] upgraded linux49 (4.9.59-1 -> 4.9.60-1)
```
which forces an update-grub. Will not affect custom menu entries, however. Manjaro entry will continue to be correct unless you optionally switch to another kernel entirely, like kernel 4.13 in which case you need to do a one-time edit of the custom entry.

A lot of help, 'Dennis N'... thank you very much.  

I've got the J.A Watson custom-menu script from your post #279 stuffed into /mnt/data (along with a bunch of other custom-menu-building facilities).  I was thinking last night after posting I'd ought to build other OS custom-menuentry's from Manjaro 30_os-prober... they all have "savedefault" as first of indented lines.  I'm wondering, with CentOS, if I might ought to put that in in the same position with J.A. Watson menu-script... along with a change of the "set root=" line from " set root='hdo,gpt10' " to "set root='UUID, etc.' "  I'd do one at a time to test... probably start with the "set root=" part (with or without the ' ' around the UUID section)... see if a "savedefault" line is necessary.  

*  Actually don't know what  having ' ' around a line or line-part does, given there are no spaces in the line-part  (would like to).  

To note:  I did all the base work on Manjaro custom-menu in /mnt/data from Ubuntu 16.04 (I know the system a little better and can use rt. clk. > *edit-as-administrator* where-and-if-needed).   Had it all set up... switched to Manjaro... did 'cp -a, etc.'... made executable... 'update-grub'.  Had to fuss with the line spacing, etc. as noted in Post #351.  In the end, last thing I did (and didn't mention) was using Nano on menu-build from Manjaro and redoing 'cp -a, etc.' to Manjaro /etc/grub.d.  I don't know how it would be possible for that to have made the difference... probably not...  I was "Mistakes 'R Us" all night, but after doing that, the custom-menu took.  

Re last sentence: "If a cat jumps on a hot stove (from back in the days of wood burning cook stoves, one assumes), it will never jump on the stove again, whether it's hot, or not..."

Mike

---

### Post by Dennis N on 2017-11-10
> Manjaro is still showing CentOS 'Rescue' as primary in Manjaro's 30_os-prober
As to 'rescue' kernel, that's the "Side problem" discussed by Mr. Dedoimedo in your link at #284. I think the best solution is to boot Fedora family distros with the method described by J.A. Watson. Dedoimeido does not mention this technique. (Instead, Dedoimedo suggests that a way to fix it is to make Fedora work like openSUSE or Ubuntu by creating a symlink in / pointing to the latest kernel, but he does not describe how to do that. I don't see how to do this, since it seems the link needs to be re-targeted by some part of the update script when a newer kernel is installed?)

---

### Post by Mike Krall on 2017-11-11
In this:
```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Manjaro Linux' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8093c5af-c92b-45f3-9e66-ee7a40102011' {
	savedefault
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt8'
	[COLOR="#0000CD"]if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  8093c5af-c92b-45f3-9e66-ee7a40102011
	else
	  search --no-floppy --fs-uuid --set=root 8093c5af-c92b-45f3-9e66-ee7a40102011
	fi[/COLOR]
	echo	'Loading Linux 4.9.60-1-MANJARO x64 ...'
	linux	/boot/vmlinuz-4.9-x86_64 root=UUID=8093c5af-c92b-45f3-9e66-ee7a40102011 rw  quiet resume=UUID=03058333-b9c0-4804-9238-f7bce11f45cc
	echo	'Loading initial ramdisk ...'
	initrd	/boot/intel-ucode.img /boot/initramfs-4.9-x86_64.img
}


```
What do the blue lines refer to, or do they stand on their own?  Wondering if they refer to " set root='hd0,gpt8', or ??? Seems they are a common, if not identical, entity in menuentry's.

Mike

**Edit:** [COLOR="#FF0000"]Checked Manjaro, Ubuntu 16.04.3, and CentOS-7.  Blue lines are identical in all.[/COLOR]

---

### Post by Mike Krall on 2017-11-12
Finally got Ubuntu 16.04.3 to work in custom-menuentry.  A simple thing, really, but... See this link and section from it in the Quote box: [https://help.ubuntu.com/community/Grub2/CustomMenus]("https://help.ubuntu.com/community/Grub2/CustomMenus")
> **Maintenance-Free Menuentries**
There is a potential drawback of a custom menu when the 10_linux and/or 30_os-prober scripts have been disabled. A copied Linux menuentry normally contains a specific kernel and initrd image version number (such as 3.2.0-24) and will not change if a new kernel is introduced. 

If the user wishes to always boot the current kernel, the linux and initrd lines of the can take advantage of the symlinks placed in /. These links always point to the most recent kernel. If they are referenced in the menuentry and the symlinks exist, the menuentry will always point to the latest kernel.

Replace the normal linux and initrd references, which normally contain the complete kernel version, with the following:

[I]linux /vmlinuz root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff[COLOR="#FF0000"]**{**[/COLOR]

initrd /initrd.img[/I]
The red " { " at end of 'linux' line... when I left it off my custom-menuentry, it worked... does not work with. That took a while.

Mike

---

### Post by Dennis N on 2017-11-12
> Finally got Ubuntu 16.04.3 to work in custom-menuentry.

That sounds good. Those errors like the extra opening brace {  are often hard to spot. There is just one pair of braces in a menu entry - one at the end of the 'menuentry' line, and one at the end the entry on it's own line. Always check that all grouping symbols are in matched pairs (opening and closing).

Using a text editor designed to work with computer coding helps see these pairings as they are highlighted by the editor. Examples of such editors are bluefish and geany. Check them out.

---

### Post by Mike Krall on 2017-11-12
> **Dennis N said:**
> That sounds good. Those errors like the extra opening brace {  are often hard to spot. There is just one pair of braces in a menu entry - one at the end of the 'menuentry' line, and one at the end the entry on it's own line. Always check that all grouping symbols are in matched pairs (opening and closing).

Using a text editor designed to work with computer coding helps see these pairings as they are highlighted by the editor. Examples of such editors are bluefish and geany. Check them out.

When I first noticed the 'linux' line's ending " **{ **" (a long time ago, now), I thought it odd, but then, I don't know much and, etc., etc.  When a person is left no where to go, they start looking hard at where they are.  The money move is asking "what would 'oldfred' do?"  (Many others too, of course)...  Check, cross check, re-check... 

I looked around on the 'Grub/CustomMenu' page a little to see if I could "fix it".  It looks like, not without jumping through a bunch of hoops though, and in the end, not at all sure I'd be allowed.  

Somewhere I've seen check-boxes for highlighting brackets, etc.  Might be KDE Neon (Plasma5).  I'll remember the *code-oriented-text-exitors* part, 'Dennis N'. Thanks for the pointing.

Mike

---

### Post by Mike Krall on 2017-11-14
> **Mike Krall said:**
> In this:
```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Manjaro Linux' --class manjaro --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8093c5af-c92b-45f3-9e66-ee7a40102011' {
	savedefault
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt8'
	[COLOR="#0000CD"]if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  8093c5af-c92b-45f3-9e66-ee7a40102011
	else
	  search --no-floppy --fs-uuid --set=root 8093c5af-c92b-45f3-9e66-ee7a40102011
	fi[/COLOR]
	echo	'Loading Linux 4.9.60-1-MANJARO x64 ...'
	linux	/boot/vmlinuz-4.9-x86_64 root=UUID=8093c5af-c92b-45f3-9e66-ee7a40102011 rw  quiet resume=UUID=03058333-b9c0-4804-9238-f7bce11f45cc
	echo	'Loading initial ramdisk ...'
	initrd	/boot/intel-ucode.img /boot/initramfs-4.9-x86_64.img
}


```
What do the blue lines refer to, or do they stand on their own?  Wondering if they refer to " set root='hd0,gpt8', or ??? Seems they are a common, if not identical, entity in menuentry's.

Mike

**Edit:** [COLOR="#FF0000"]Checked Manjaro, Ubuntu 16.04.3, and CentOS-7.  Blue lines are identical in all.[/COLOR]

Do I really need to mess with what I'm messing with?  I've got a 'perfectly serviceable' menuentry form for CentOS  from J.A. Watson, via 'Dennis N' use of it (Post #279).  Still, it seems the 'money move' is to have UUID in there some how ('oldfred', and a lot of others say so). So I mess...

From 'the blue lines'... 
[https://askubuntu.com/questions/833220/where-is-documentation-for-xfeature-xy-in-grub-cfg]("https://askubuntu.com/questions/833220/where-is-documentation-for-xfeature-xy-in-grub-cfg")... and there is more inference at GNU GRUB Manual 2.02 (Apr 25, 2017)... See Sec. 4 (all), 5(all), 6(all)... [https://www.gnu.org/software/grub/manual/grub/grub.html#Booting]("https://www.gnu.org/software/grub/manual/grub/grub.html#Booting")

Anyhow...

"It" is all in and working... Separate Data Partition (mostly) done/configured/copied/backed-up).

So, now what do I do ???

Mike

---

### Post by Mike Krall on 2017-11-14
I've questions:

I changed Manjaro /etc/default/grub... *GRUB_TIMEOUT=0* to =-1. That stopped boot countdown so Grub menu pops up, then sits there waiting.  Also uncommented Manjaro *GRUB_DISABLE_OS_PROBER=true* ('update-grub).  Reboot to Ubuntu-unity and Grub boot menu is same as Manjaro (all custom except what Manjaro '10_linux' adds to end... Manjaro w/ advanced menu option.  I would have thought I would see Ubuntu-unity view of the world (enabled '30_os-prober').  

*  To have /boot/grub/grub.cfg NOT have a ton of entries, I should uncomment *'GRUB_DISABLE_OS_PROBER=true'* there, and in other OS's... yes?

*  Does it seem better to make all OS *'GRUB_TIMEOUT=-1'*, also... ???

Mike

---

### Post by oldfred on 2017-11-14
I like timeout to 3 sec, so I have a chance to make a change, but not a long wait to boot into default install.

You can use set root= or the search by UUID.
Never have understood exactly how it works with both. I assume search overrides the set root= command if UUID found.

An older grub2 did have issue with system with many drives and not finding a flash drive that was sdf or sdg and search by UUID seemed to quit looking as there was a gap or no sde. But grub uses hd0, hd1, so I may use just set root=, and then have had that not work when I have a flash drive in and have to manually edit my set root.

---

### Post by Dennis N on 2017-11-14
> Reboot to Ubuntu-unity and Grub boot menu is same as Manjaro (all custom except what Manjaro '10_linux' adds to end... Manjaro w/ advanced menu option. I would have thought I would see Ubuntu-unity view of the world (enabled '30_os-prober').

If you see the custom entries, then that is not Ubuntu's grub menu (unless you added them to Ubuntu as well). You've booted into Manjaro again.
> To have /boot/grub/grub.cfg NOT have a ton of entries, I should uncomment 'GRUB_DISABLE_OS_PROBER=true' there, and in other OS's... yes?
Maybe. GRUB_DISABLE_OS_PROBER= is not in Ubuntu's /etc/default/grub, so you can't uncomment it. If you add it, it might work. I run in terminal **sudo chmod -x 30_os-prober** to disable it. 
> * Does it seem better to make all OS 'GRUB_TIMEOUT=-1', also... ???
No. Grub settings on the target OS are not active - unless you follow Watson - in that case, if target OS also has that setting, then 2nd grub menu would also pause.

---

### Post by Mike Krall on 2017-11-17
I awoke in a dream...

Yesterday morning I booted to CentOS and got a "couldn't find..." error.  Looking found a custom-menu entry that CentOS could not possibly boot from.  It was late when I finished building and 'cp' and 'update-grub' on CentOS. I must not have tried to boot into it.

This is 'Dennis N' / J.A.Watson-type from Post # 279 ( [https://ubuntuforums.org/showthread.php?t=2355551&page=28&p=13698629#post13698629]("https://ubuntuforums.org/showthread.php?t=2355551&page=28&p=13698629#post13698629") )
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'KORORA 26 menu' {
insmod part_gpt 
insmod fat
set root='hd1,gpt4'
chainloader /EFI/fedora/shim.efi 
}
```

After fixing, this is my current custom-menuentry for CentOS:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'CentOS (on /dev/sda10)' {
insmod part_gpt 
insmod fat
set root='hd0,gpt10'
chainloader /EFI/centos/shim.efi 
}
```

It doesn't boot CentOS... error is "can't find /EFI/centos/shim.efi"  I tried with both 30_os-prober on and off.  I've redone: check-menuentry... 'cp'... check... make executable... check... reboot... 'update-grub'... check in Manjaro /boot/grub/grub.cfg...  try boot,  three times.  The parts are correct as I understand them... lower case name of OS... my CentOS is on /dev/sda10.  I tried using the whole path in 'chainloader' line with error "not finding /boot/efi/EFI/centos/shim.efi"

I've looked around for understanding (not as much as I can, and will).  Any thoughts on why not working or steps I may have missed and/or not done correctly?

Mike

EDIT:  Thought a thing right after posting... no time to work on now.  I may have done all the CentOS custom-menuentry with GRUB_DISABLE_OS_PROBER=true uncommented in Manjaro.  Rather, I don't have notes or a clear recollection of that line being commented out.  I've no idea if that would make a difference.

---

### Post by oldfred on 2017-11-17
If you have two drives which drive are you booting from.
I only recently got Fedora to install to the ESP on sdb with install on sdb.
But I normally boot Ubuntu from sda or hd0 in grub.

Drive may then be seen as hd0 when directly booting sdb's ESP but seen as hd1 if booting a grub in ESP on sda.
I get this issue a lot as I directly boot ISO on either sda or sdb and normally boot sda, but then my sdb entries change, often if I plug in a flash drive making the entries on sdb, or hd1 become hd2. Keeps me confused, regularly.

---

### Post by Dennis N on 2017-11-17
> It doesn't boot CentOS... error is "can't find /EFI/centos/shim.efi"

There is a mistake in the menu entry:

**set root='hd0,gpt10'** should be set to the EFI system partition where CentOS installed its grub bootloader files.

---

### Post by Mike Krall on 2017-11-18
Thanks, 'oldfred'...  Thanks, 'Dennis N'

I'm going to have to look around for more understanding on why CentOS chainloader menuentry wants 'set root=' to be /efi/boot partition.  Every time I look at it, my brain goes, "No, wait..."

Really long day in town today.  Just got this done and in:
```
menuentry 'CentOS (on /dev/sda10)' {
insmod part_gpt 
insmod fat
set root='hd0,gpt1'
chainloader /EFI/centos/shim.efi
}
```
Works just fine now.  I'd have never gotten this figured out.  Thank you both again.

To note:  CentOS is the only of the 7-OS not working with Manjaro /etc/default/grub GRUB_DEFAULT=saved... GRUB_SAVEDEFAULT=true.  Selecting CentOS from boot menu moves to UEFI menu with hi-light on most recent kernel version. I assume a newer installed version will be the one hi-lighted.  

Mike

---

### Post by Dennis N on 2017-11-18
> I'm going to have to look around for more understanding on why CentOS chainloader menuentry wants 'set root=' to be /efi/boot partition.
chainload hands off boot process to another boot loader, while direct boot boots a linux kernel in target system.
> To note: CentOS is the only of the 7-OS not working with Manjaro /etc/default/grub GRUB_DEFAULT=saved... GRUB_SAVEDEFAULT=true. 
With any menu entry of that type the savedefault seems to be ignored. Explanation unknown. 
> Selecting CentOS from [COLOR="#FF0000"]boot menu[/COLOR] moves to [COLOR="#FF0000"]UEFI menu[/COLOR]... 
Just so I understand correctly:
[COLOR="#FF0000"]boot menu[/COLOR]: do you mean Manjaro grub menu?
[COLOR="#FF0000"]UEFI menu[/COLOR]: do you mean CentOS grub menu?
> ...with hi-light on most recent kernel version. I assume a newer installed version will be the one hi-lighted.
You are correct on that. Verify this by the kernel version numbers in the menu entry.

---

### Post by Mike Krall on 2017-11-19
> Just so I understand correctly:
[COLOR="#FF0000"]boot menu[/COLOR]: do you mean Manjaro grub menu?
[COLOR="#FF0000"]UEFI menu[/COLOR]: do you mean CentOS grub menu?

Power up... Manjaro menu screen w/ title "GNU GRUB Version 2.03".  This screen has Manjaro 'savedefault' function... green hi-light of last used OS (not if CentOS last OS).  Arrow to CentOS... 'Enter'... new screen (no title) w/ list of CentOS choices (like listed in CentOS '10_linux'... newest... next newest... oldest... 'rescue') (CentOS GRUB_DISABLE_OS-PROBER=true is uncommented).

Perhaps should have said "Grub boot menu"... yes?  Don't know where I got "UEFI menu".  Maybe from getting same menu for CentOS when the only way to boot it was: Power up... 'esc' (to UEFI boot menu)... arrow to CentOS... 'Enter' (Get same choices as mentioned (same screen... 'no title'... same list... same font.)) 
> chainload hands off boot process to another boot loader, while direct boot boots a linux kernel in target system.

I get this (in theory).  Thank you.
> With any menu entry of that type the savedefault seems to be ignored. Explanation unknown. 
After looking at the 'no savedefault function' for a while, I guessed it was bypassing Grub (or Grub protocol, or process, or ???) and going directly to /EFI/centos/shim.efi (for CentOS... Ubuntu-types use shimx64.efi., I think... Manjaro grubx64.efi ). 

Mike

---

### Post by Mike Krall on 2017-11-20
From Post # 361... top of this page..

> **oldfred said:**
> I like timeout to 3 sec, so I have a chance to make a change, but not a long wait to boot into default install.

I turn on my computer and start day dreaming... getting whatever-OS I was in last, whether I want it or not. And sometimes, it seems, having the menu staring back causes me to think about what I actually want, or need, or ought to do... works.
> You can use set root= or the search by UUID.
Never have understood exactly how it works with both. I assume search overrides the set root= command if UUID found.

Is this the "search by UUID" you mean?
```
if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  f52a4cdd-befe-4197-82dc-18a34eacf783
        else
          search --no-floppy --fs-uuid --set=root f52a4cdd-befe-4197-82dc-18a34eacf783
        fi
```
I ran into this... has a little to say about the use of both 'set root=' and search UUID... see Post 2 and 4
[https://www.linuxquestions.org/questions/linux-newbie-8/grub-2-when-why-i-need-both-in-grub-cfg-%3B-set-root%3D-and-search-set%3Droot-4175416157/#post4726377]("[URL="https://www.linuxquestions.org/questions/linux-newbie-8/grub-2-when-why-i-need-both-in-grub-cfg-%3B-set-root%3D-and-search-set%3Droot-4175416157/#post4726377")"][https://www.linuxquestions.org/questions/linux-newbie-8/grub-2-when-why-i-need-both-in-grub-cfg-%3B-set-root%3D-and-search-set%3Droot-4175416157/#post4726377]("https://www.linuxquestions.org/questions/linux-newbie-8/grub-2-when-why-i-need-both-in-grub-cfg-%3B-set-root%3D-and-search-set%3Droot-4175416157/#post4726377") 
Whole thing...
[https://askubuntu.com/questions/833220/where-is-documentation-for-xfeature-xy-in-grub-cfg]("https://askubuntu.com/questions/833220/where-is-documentation-for-xfeature-xy-in-grub-cfg")
There's a little thing under "Chain loading" a short way down this:
[https://www.ibm.com/developerworks/library/l-lpic1-102-2/index.html]("https://www.ibm.com/developerworks/library/l-lpic1-102-2/index.html")

Mike

---

### Post by oldfred on 2017-11-20
Yes that is the search commands.
Often the short cut boot commands we use in 40_custom do not include search but just a set root=. But then using device like that can cause issues. I have skipped a SATA port and second or third drive can change device settings if flash drive plugged in.

I used to use chain loading with grub legacy. I had one grub partition with my manually configured grub and each install had grub in PBR - partition boot sector. Grub2 is larger and they now have to convert to blocklists to fit a version of grub2 into a PBR. And blocklists are not reliable.

I have (had) a like to a Linux site that the expert had over 100 installs on two drives all chain loaded with grub legacy.
chainboot 145 systems - saikee
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by Mike Krall on 2017-11-20
Thanks, 'oldfred'...

I'm running around acting like I 'get' stuff... initrd and initramfs... what drives what... and on. 

Months past, somewhere (not finding in the wads of bookmarks) I came across a thing relative to menuentry...  the why of ' insmod ext2 '.  Something like it deals with fat32 (/boot/efi fs) but is Linux.  Seems like everything menuentry is ' insmod ext2 ', just prior to 'set root=' , just prior to 'search commands'... like it was a universal convention.  

What this is all about is I wonder if a person can make a maintenance-free menuentry for RHEL types without  chain loading...  not like chain loading doesn't work or is onerous in any manner.  Just this thing in my head about "why not?"

I found that ' $vt_handoff ' (red) (all Ubuntu-type ' linux ' line ending) is Ubuntu-type specific.  Think 'blue' might be Ubuntu-type specific, also, but haven't found 'yes or no'... only that all search hits on that line are Ubuntu-type related. 
```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-0f47f885-3e8b-475b-9082-2ea2c05ff732' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	[COLOR="#0000CD"]if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi[/COLOR]
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0f47f885-3e8b-475b-9082-2ea2c05ff732
	else
	  search --no-floppy --fs-uuid --set=root 0f47f885-3e8b-475b-9082-2ea2c05ff732
	fi
	linux	/boot/vmlinuz-4.10.0-40-generic.efi.signed root=UUID=0f47f885-3e8b-475b-9082-2ea2c05ff732 ro  quiet splash[COLOR="#FF0000"] $vt_handoff[/COLOR]
	initrd	/boot/initrd.img-4.10.0-40-generic
}
```

A couple of other things I've run into:

*  'initrd' is, most often, actually 'initramfs'... seems it doesn't matter if 'initrd' line is 'initrd'... actually works as 'initramfs'.  

*  RHEL-types are very specific... do not use 'update-grub'.... use the 'correct' 
```
~]# grub2-mkconfig -o /boot/grub2/grub.cfg
~]# grub2-mkconfig -o /boot/efi/EFI/centos/grub.cfg
``` 
instead... as well as different versions for BIOS/MBR and UEFI/ESP. (I think I came across a difference for Grub and Grub2, also... either lost somewhere or imagined).

*Manjaro does not easily boot CentOS (will if newest kernel version is picked out of list... the list is in reverse order of what a person might expect).  Ubuntu (with Nov. Grub update) will boot CentOS.  

CentOS 7 'Default' menuentry... see red:
```
menuentry 'CentOS Linux (3.10.0-693.5.2.el7.x86_64) 7 (Core)' --class centos --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-3.10.0-693.5.2.el7.x86_64-advanced-4d7429d0-2d26-4d49-806b-46629198f13b' {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  4d7429d0-2d26-4d49-806b-46629198f13b
	else
	  search --no-floppy --fs-uuid --set=root 4d7429d0-2d26-4d49-806b-46629198f13b
	fi
	[COLOR="#FF0000"]linuxefi /boot/vmlinuz-3.10.0-693.5.2.el7.x86_64 root=UUID=4d7429d0-2d26-4d49-806b-46629198f13b ro rhgb quiet 
	initrdefi /boot/initramfs-3.10.0-693.5.2.el7.x86_64.img[/COLOR]
}
```

Manjaro reads CentOS 'linux' and 'initrd' lines like this (and so does Ubuntu 16.04... identically):
```
linux /boot/vmlinuz-3.10.0-693.5.2.el7.x86_64 root=/dev/sda10
initrd /boot/initramfs-3.10.0-693.5.2.el7.x86_64.img
```

This is Ubuntu Community Grub2/CustomMenus 'Maintenance-Free Menuentries' 'linux' and 'initrd' line replacement:
```
linux /vmlinuz root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff

initrd /initrd.img
```

Seems like a maintenance-free menu entry for CentOS might work if a person showed CentOS what it would expect to see (+/-).  Maybe like:
```
menuentry 'CentOS Linux (3.10.0-693.5.2.el7.x86_64) 7 (Core)' --class centos --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-3.10.0-693.5.2.el7.x86_64-advanced-4d7429d0-2d26-4d49-806b-46629198f13b' {
	[COLOR="#0000CD"]load_video
	set gfxpayload=keep[/COLOR]
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  4d7429d0-2d26-4d49-806b-46629198f13b
	else
	  search --no-floppy --fs-uuid --set=root 4d7429d0-2d26-4d49-806b-46629198f13b
	fi
	linuxefi /vmlinuz root=UUID=4d7429d0-2d26-4d49-806b-46629198f13b ro rhgb quiet 
	initrdefi /initramfs.img
}
```

Maybe without blue lines... doesn't seem like maintenance-free menuentry find them necessary, but RHEL-types seem quite particular. 

Mike

---

### Post by oldfred on 2017-11-20
If you look in /boot/grub/x86_64-efi (with UEFI) you will see all the .mod files.

insmod ext2 loads the ext* driver which is for ext2, ext3 & ext4 formatted partitions.

If you have some of the distributions with LVM as default you need to insmod the lvm drivers, for example which Redhat uses by default (lvm).
There are many .mod files, not even sure what some of them are for. I think some distributions include some of them that they know they need already baked into their grub, so not needed to be added as grub loads. Others you need to add before you can get something to work.

---

### Post by Mike Krall on 2017-11-21
> **oldfred said:**
> If you look in /boot/grub/x86_64-efi (with UEFI) you will see all the .mod files.

insmod ext2 loads the ext* driver which is for ext2, ext3 & ext4 formatted partitions.

If you have some of the distributions with LVM as default you need to insmod the lvm drivers, for example which Redhat uses by default (lvm).
There are many .mod files, not even sure what some of them are for. I think some distributions include some of them that they know they need already baked into their grub, so not needed to be added as grub loads. Others you need to add before you can get something to work.

*  There are quite a few .mod files...  

*  Thank you for the understanding of insmod ext2, 'oldfred'.

*  I've not got any LVM in this machine... separate data partition is more than enough for me for a while, but I'll remember what you said here. 

I tried some versions of menuentry for CentOS... 'not find linuxefi'... 'file /vmlinuz not found'... 'need to load kernel first'... and on and on.  Figured, "Well, maybe if I learn a little more and try to look at the whole thing in other ways... same... same... same.  Hmmm.

The original chain loading menuentry does work, doesn't it?  Yes it does...  =]  

I won't be able to 'just stop' with this CentOS menuentry thing...  It will lay in the background and poke at me.  I'll do my best to ignore it.  

Mike

---

### Post by Dennis N on 2017-11-21
Hello.
> I tried some versions of menuentry for CentOS... 'not find linuxefi'
Manjaro grub does not understand 'linuxefi' and 'initrdefi'. Use 'linux' and 'initrd' and it will work.
> 'file /vmlinuz not found'
Investigate and check for the file vmlinuz in / of CentOS - what do you see?

---

### Post by Mike Krall on 2017-11-21
> **Dennis N said:**
> Hello.

Manjaro grub does not understand 'linuxefi' and 'initrdefi'. Use 'linux' and 'initrd' and it will work.

Investigate and check for the file vmlinuz in / of CentOS - what do you see?

As you said, tried this (linuxefi, initrdefi) and it didn't work:```

        insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  4d7429d0-2d26-4d49-806b-46629198f13b
	else
	  search --no-floppy --fs-uuid --set=root 4d7429d0-2d26-4d49-806b-46629198f13b
	fi
	linuxefi /vmlinuz root=UUID=4d7429d0-2d26-4d49-806b-46629198f13b ro rhgb quiet 
	initrdefi /initramfs.img
```

Made no changes other than dropping 'efi' from 'linux' and 'initrd'. That is when I got 'cannot find 'vmlinuz' file' and 'need to load kernel first'.  

'vmlinuz' in CentOS root:

4 - DOS/Windows executable (application/x-ms-dos-executable).  One each for 3 - kernel versions (vmlinuz-3.10.0-693.5.2.el7.x86_64 is 'default' and newest) and 1 - 'rescue' vmlinuz-0-rescue-<number> 

3 - Plain text. One each for kernel versions. All .vmlinuz 3.10.0-number (like recent -653.5.2.el7.x86_64.hmac... different versions)

Mike

---

### Post by Dennis N on 2017-11-22
> Made no changes other than dropping 'efi' from 'linux' and 'initrd'. That is when I got 'cannot find 'vmlinuz' file' and 'need to load kernel first'. 

That's not all that needs to be fixed. If you have /vmlinuz in the 'linux' line, then grub is looking in the root folder (and not into any sub folder of root) for a file with that exact name, and **vmlinuz-3.10.0-693.5.2.el7.x86_64** is not the same file name as **vmlinuz**. I think you won't find the file named vmlinuz in Fedora type OS, so you get the 'file not found' message.  

Since all your kernels are in **/boot**, you need to have, for example, **/boot/vmlinuz-3.10.0-693.5.2.el7.x86_64** in the 'linux' line to have a correct path to a bootable file.

True, Ubuntu has a file vmlinuz in / which is a symbolic link to the latest kernel, so your construct works in Ubuntu, but not in Fedora type OS, since the symbolic link is not there.

---

### Post by Mike Krall on 2017-11-22
'Dennis N'...  Thank you for that last post. It's up to me not knowing much, again, and that's fine.  I'd like to let this go.  I've got CentOS booting off of your original Post #279 chain loading menuentry, and that is what I need to have happen.  I was hoping to get CentOS to work with Manjaro's 'savedefault' system... nice pretty green highlight in the boot menu. That's more than a little silly.

I don't know what's next... maybe nothing. I'm going to sit on this a few days... see what occurs. 

Thank you again... Happy Thanksgiving to you and 'oldfred'... eat 'til you squeak... =]

Mike

---

### Post by Dennis N on 2017-11-22
Glad to hear the post is clear!

On set root='hd0,gpt1' and using UUID instead of this, I had no success. Used various syntax (like set root=UUID=94C3-7016), and none worked. Did you ever get this to work?

---

### Post by oldfred on 2017-11-22
I use this with my Ubuntu entries. And it works as Ubuntu puts a link in root to most current kernel. Not sure if other distributions do that or not.
```
menuentry "Ubuntu 17.10 (17.10) (on /dev/sdb8)" {
    set root=(hd1,gpt8)
        linux /vmlinuz root=/dev/sdb8 ro quiet splash
        initrd /initrd.img
}
/code]

I also like the configfile entry as I am often updating/adding ISO to boot with from my hard drive. And I think I always used to forget sudo update-grub when entries were directly in 40_custom. But with configfile I can manually edit the text files and configfile just loads it as long as it is valid grub boot stanza.

[code]menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,3)/livecdimage.cfg
} 

```
Ubuntu's UEFI now uses configfile in ESP to find full grub.cfg in /boot in the install.
```
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
#search.fs_uuid fabeeda1-ad36-4300-a7f8-73afba118f37 root hd1,gpt9 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```
 I think with my Fedora it just had the full grub.cfg in the /EFI/fedora folder in the ESP. So any chain load/configfile entry would have to be into ESP where grub is, not in the install. Not at system with my test Fedora install and that was just to understand grub install procedures, not to use Fedora. 
My Debian test install only had grubx64.efi,no shim for secure boot. And grub was built into grubx64.efi, so configfile entry not accessible. But full grub.cfg still in the install.

---

### Post by Mike Krall on 2017-11-23
> **Dennis N said:**
> Glad to hear the post is clear!

On set root='hd0,gpt1' and using UUID instead of this, I had no success. Used various syntax (like set root=UUID=94C3-7016), and none worked.[COLOR="#FF0000"] Did you ever get this to work?[/COLOR]

I haven't tried... 

I don't know that I need to now, though it is still on the list.

Only if it is easy to do...  What did you try?

Mike

---

### Post by Dennis N on 2017-11-25
> I don't know that I need to now, though it is still on the list. Only if it is easy to do... What did you try?

I put my money on the format I showed in the post:

[FONT=Courier New]**set root=UUID=94C3-7016**[/FONT]

No luck. Added some spaces, tried some quotes around it, etc. None of that helped. Leaving things as is. Not a big deal.

---

### Post by Mike Krall on 2017-11-25
GNU GRUB Manual:  
[https://www.gnu.org/software/grub/manual/grub/html_node/Multi_002dboot-manual-config.html]("https://www.gnu.org/software/grub/manual/grub/html_node/Multi_002dboot-manual-config.html")

See "Note:" at end.  I don't know if this pertains to chain loading. 

I've thought to add:
```

                if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  0f47f885-3e8b-475b-9082-2ea2c05ff732
		else
		  search --no-floppy --fs-uuid --set=root 0f47f885-3e8b-475b-9082-2ea2c05ff732
		fi
```
Just another of one of my random, wannabe-guesses, though...  And I dislike doing things based in the concept "what could it hurt?"

Mike

---

### Post by Dennis N on 2017-11-25
I can offer this:

None of these tried are correct:
```
set root=94C-7016
set root 94C-7016
set root=UUID=94C-7016
set root UUID=94C-7016

```
error messages:  'not an assignment' and/or 'no server is specified'

At grub menu, type 'c' for command line then type 'set' and enter for possible completions. Looks like only valid completion for **set** used with **root** is something akin to (these are examples) **root=hd0,gpt1** or **root=hd0,msdos1**. Apparently you don't need any quote marks but they are ok?

There is also a difference between **set** command and **--set** option in what can follow.

---

### Post by Mike Krall on 2017-11-26
> **Dennis N said:**
> I can offer this:

None of these tried are correct:
```
set root=94C-7016
set root 94C-7016
set root=UUID=94C-7016
set root UUID=94C-7016

```
error messages:  'not an assignment' and/or 'no server is specified'

At grub menu, type 'c' for command line then type 'set' and enter for possible completions. Looks like only valid completion for **set** used with **root** is something akin to (these are examples) **root=hd0,gpt1** or **root=hd0,msdos1**. Apparently you don't need any quote marks but they are ok?

There is also a difference between **set** command and **--set** option in what can follow.

**  Seems like every place I see hdX,gptY I see it with either **( )** or **' '**... but if root says so...  ???

I did a different thing.  Tried:
```
menuentry 'CentOS (on /dev/sda10)' {
	insmod part_gpt 
	insmod fat
	set root='hd0,gpt1'
        [COLOR="#0000CD"]if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  B70F-1399
	else
	  search --no-floppy --fs-uuid --set=root B70F-1399
	fi[/COLOR]
	chainloader /EFI/centos/shim.efi
}
```
It worked... BUT... still have to arrow-to-CentOS > Enter (takes to list of CentOS kernels and 'rescue' with newest -first in line- highlighted) > Enter (again). 

When that worked I added:
```
menuentry 'CentOS (on /dev/sda10)' {
	[COLOR="#FF0000"]savedefault[/COLOR]
	insmod part_gpt 
	insmod fat
	set root='hd0,gpt1'
       [COLOR="#0000CD"] if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  B70F-1399
	else
	  search --no-floppy --fs-uuid --set=root B70F-1399
	fi[/COLOR]
	chainloader /EFI/centos/shim.efi
}
```
Still have to do 'Enter' twice, but now CentOS is highlighted in Green at Grub menu...  =]

Trouble being, I have ZERO idea if adding the 'if-then-else-fi' has anything to do with anything about including UUID.  Could easily be it is ignored/bypassed instead of followed.  I don't know how to tell... I don't suppose taking out **set root='hd0,gpt1'** would work, either. I'm still not clear on what 'if - then -else -fi' is saying... like what, really, does **[ x$feature_platform_search_hint = xy ];** mean/do?

I wonder if **--set=root 94C-7016** would work... OR **set root=UUID=94C-7016**  (Last from this: [https://forum.manjaro.org/t/creating-a-new-os-independent-grub-2-bootloader/3150/4]("https://forum.manjaro.org/t/creating-a-new-os-independent-grub-2-bootloader/3150/4")... see 2/5's down.

There is actually a lot of interesting stuff in that link.

Ended up reading the comments at end of link.  Saw this... third from last:
> ps: search --file can be very useful too, like in search $isofile, /boot/intel-ucode, .....
ps: search command does not use /dev/sdxy
we can 'set root' (instead of search) with
set root=(hdx,y)
But it is not recommended.
[COLOR="#FF0000"]You see this 'set root=(hdx.y)' in all grub entries but always search line is below this 'set root' line and therefore supersede it. 
Try it out. Go put in a wrong (but valid) (hdx,y) and it will still get you to the right partition as spelled out by the search line.[/COLOR] That's what makes grub so .....er, usable dependable.

Mike

---

### Post by Dennis N on 2017-11-26
Good find on the tutorial. My first take-away is using the search command in place of set. I used 'set' only because in J.A. Watson's articles, he does it that way. 

In particular, maybe this syntax can replace **set** command, the **--set** option doing what the **set** command will not:
```
search --no-floppy --fs-uuid --set=root <uuid>
```

More possibly useful references:
[https://www.gnu.org/software/grub/manual/grub/grub.html#search](https://www.gnu.org/software/grub/manual/grub/grub.html#search)
[https://wiki.archlinux.org/index.php/GRUB](https://wiki.archlinux.org/index.php/GRUB)

---

### Post by oldfred on 2017-11-26
I may have posted this before?
But grub in the ESP uses a configfile to chain to the full install's grub.cfg in the Ubuntu / partition.
It uses this type of search.

```
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

I also use configfile with just partition info & no search to boot into ISO. I just did that to install 18.04 and it did not work as I had flash drive plugged in & I had to change hd1 to hd2 when booting.

```
menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,6)/livecdimage.cfg
} 

```

Fedora has this:
      The grub2-efi package installs a prebaked grubx64.efi on the EFI System partition, which looks for grub.cfg on the ESP in /EFI/fedora/ whereas the grub2-install command creates a custom grubx64.efi, deletes the original installed one, and looks for grub.cfg in /boot/grub2/.

---

### Post by Dennis N on 2017-11-26
It works!

I used the syntax in the code box of post #385 instead of the **set** command. I have now changed all my chainload style menu entries to use this syntax.

---

### Post by Mike Krall on 2017-11-26
> **oldfred said:**
> [COLOR="#FF0000"]I may have posted this before?[/COLOR]
But grub in the ESP uses a configfile to chain to the full install's grub.cfg in the Ubuntu / partition.
It uses this type of search.

```
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

I also use configfile with just partition info & no search to boot into ISO. I just did that to install 18.04 and it did not work as I had flash drive plugged in & I had to change hd1 to hd2 when booting.

```
menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,6)/livecdimage.cfg
} 

```

Fedora has this:
      The grub2-efi package installs a prebaked grubx64.efi on the EFI System partition, which looks for grub.cfg on the ESP in /EFI/fedora/ whereas the grub2-install command creates a custom grubx64.efi, deletes the original installed one, and looks for grub.cfg in /boot/grub2/.

Yes... Post #379 (and other posts with related bits and pieces).  It's a thing I've stored a number of times now, 'oldfred'... a thing I want to figure out better than I understand it now. It's one thing to go down a defined road. It's another thing to be able to see the parallel "ways" to the same (similar) place while going... to be able to recognize the sameness. And in all of that, there is convention underlying it... as in, "it doesn't work"... so, at what level and in what form does the wrongness lie?  Wrongness conceptually?  Wrongness logistically? Wrongness in format?  Wrongness in A, then B?  Wrongness in scripting or typing?  The only "un-steep" part of a learning curve is the part where a person* gets* to learn...  =]    

Mike

---

### Post by Mike Krall on 2017-11-26
> Good find on the tutorial. My first take-away is using the search command in place of set. I used 'set' only because in J.A. Watson's articles, he does it that way. 

In particular, maybe this syntax can replace set command, the --set option doing what the set command will not:

```
search --no-floppy --fs-uuid --set=root <uuid>
```

More possibly useful references:
[https://www.gnu.org/software/grub/ma...ub.html#search](https://www.gnu.org/software/grub/ma...ub.html#search)
[https://wiki.archlinux.org/index.php/GRUB](https://wiki.archlinux.org/index.php/GRUB)

I almost didn't read the 'gohlip' tutuorial end to end.  I'm happy to have it as reference.  'gohlip' is pretty prolific.  I did a [http://golip site:forum.manjaro.org]("http://golip site:forum.manjaro.org") search (Thanks again for that, 'oldfred'... one of my main finding-tools now).  LOTS of reading possible there... =]

Thank you for the "possibly useful references"... more reading.

I noticed in Post #387 the code line here worked... Nice!!!  

Now you don't have a 'set root=hdX,gptY' and are running off search only (UUID, too).  So, how come 'set root=...' persists?  As mentioned, it is in every menuentry in Ubuntu-types (my 5, at least... maybe all Debian), Manjaro (one presumes Arch and others based on it), RHEL/CentOS (Fedora, 'oldfred'?).  I wish I knew folks running Gentoo, Slackware, some Independents to see if it's there, too.

Just thought... "See what?".  Is it, everywhere Grub goes, it goes?  I guess that might be right. 

Oh, and 'gohlip' answered my wondering a few posts back, if my adding "if-then-else-fi" to my chainloader-menuentry actually functioned or not... and what it does is search... in the end, "else", it searches UUID.  I'm going to leave mine as is.    
```

        if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  B70F-1399
	else
	  search --no-floppy --fs-uuid --set=root B70F-1399
	fi
```

Mike

---

### Post by howtoget123 on 2017-11-27
[COLOR=#000000][INDENT]Oldfred started using a NTFS shared data partition with Windows XP back in 2006 or 2007. That was when I realized I could have the Thunderbird & Firefox profiles in the NTFS partition and not have to reboot back into Windows just for email & standard list of bookmarks. I later added a Linux formated data partition for most new data as I was planning on getting rid of Windows. But one application kept me in Windows for several years.

Then when I finally shut XP down for good I had all my /home type data including the hidden profile folders for Thunderbird & Firefox in my /mnt/data partition. I regularly copy partition from home computer in Ill. to home computer in Fla. I used to copy to laptop an take to Fla, but hated ergonomics on laptop and now in Fla more so built new desktop for Fla. I found my backups of /home & /mnt/data to flash drives easier to carry than laptop. :smile:[/INDENT]
[/COLOR]

---

### Post by Dennis N on 2017-11-29
> I noticed in Post #387 the code line here worked... Nice!!!
I think it is more reliable with the UUID, and it is working fine. I have Korora 26 GNOME, Korora 26 XFCE and Fedora 27 MATE all booting this way. 
> So, how come 'set root=...' persists?
It's clear it would only be in effect if the search command in the next section failed to make an assignment. **Search** would be more reliable than the **set** - case in point: once after deleting a partition, partitions after the deleted one got renumbered 1 less than before, making the **set root=** invalid, but the OS booted anyway because the **search** command reset root partition to the correct value by searching for the UUID, which did not change on those partitions.

---

### Post by Mike Krall on 2017-11-30
> **howtoget123 said:**
> [COLOR=#000000][INDENT]Oldfred started using a NTFS shared data partition with Windows XP back in 2006 or 2007. That was when I realized I could have the Thunderbird & Firefox profiles in the NTFS partition and not have to reboot back into Windows just for email & standard list of bookmarks. I later added a Linux formated data partition for most new data as I was planning on getting rid of Windows. But one application kept me in Windows for several years.

Then when I finally shut XP down for good I had all my /home type data including the hidden profile folders for Thunderbird & Firefox in my /mnt/data partition. I regularly copy partition from home computer in Ill. to home computer in Fla. I used to copy to laptop an take to Fla, but hated ergonomics on laptop and now in Fla more so built new desktop for Fla. I found my backups of /home & /mnt/data to flash drives easier to carry than laptop. :smile:[/INDENT]
[/COLOR]

I missed this... been doing the online Christmas shopping.

Sarah has a new laptop on the way. We were talking dual booting tonight and it dawned on me a /mnt/data partition on the Linux side - even with a single OS - would make a lot of sense.  It's been so long ago I started into separate-data-partition setup, all the good reasons for doing so I ran into before starting have memory-faded.  Thanks for the reminder.
--------------------------------------------------------

A side issue:

If I don't get it said now, I might not ever...  

This forum doesn't search well. Using a Google "site:" search helps (as mentioned in my last post).  One of the things I've historically done when working on something and getting information/help from forums was to look for and find good sources... individuals a person just knew were knowledgeable.  For me, the serious topics have been metallurgy, cast bullet technology, internal ballistics, fly tying.  All of the related forums I've frequented have a person search (advanced search for 'exact name') and all of those forums bring up every topic and/or post that person has been involved with.  Ubuntu forums gives a person-search return with what looks to be a maximum of 10 pages.  For one regularly posting member (just checked), those 10 pages go all the way back to the end of this last September.  

I don't like that.  I feel it's wrong. I think there are topics with a lot of history and evolution, whether quite general or quite specific. And I think the value of one persons historical/evolutionary knowledge is high.  I want access to that.   

Mike

---

### Post by oldfred on 2017-11-30
I lost posts and/or forgot or cannot find something I thought I posted, but then did not save in my notes (Zim files). I like Zim as links are directly clickable.

For example I thought I had helped someone with an Alienware, but did not have link in my signatures.
So I put this in Google.
site:ubuntuforums.org oldfred alienware
Only 321 results. :) Many are duplicates as some places copy forum data.

---

### Post by Mike Krall on 2017-11-30
> **oldfred said:**
> I lost posts and/or forgot or cannot find something I thought I posted, but then did not save in my notes (Zim files). I like Zim as links are directly clickable.

For example I thought I had helped someone with an Alienware, but did not have link in my signatures.
So I put this in Google.
site:ubuntuforums.org oldfred alienware
Only 321 results. :) Many are duplicates as some places copy forum data.

I'm learning to learn searching...

A great help of an 'exact name' search is the hits are chronological... place and time... the base definition for history.  

Mike

---

### Post by Mike Krall on 2017-12-01
> **Dennis N said:**
> I think it is more reliable with the UUID, and it is working fine. I have Korora 26 GNOME, Korora 26 XFCE and Fedora 27 MATE all booting this way. 

It's clear it would only be in effect if the search command in the next section failed to make an assignment. **Search** would be more reliable than the **set** - case in point: once after deleting a partition, partitions after the deleted one got renumbered 1 less than before, making the **set root=** invalid, but the OS booted anyway because the **search** command reset root partition to the correct value by searching for the UUID, which did not change on those partitions.

Sorry 'Dennis N'... I intended to get here a lot quicker than this.  

I got it in my head a while ago UUID was "the better way". I certainly see a lot of non-UUID directioning, so it certainly works, but ???  Me, I've just got to go blindly down the UUID road, necessary or not, 'cause I don't know any differently. 

Your "*case in point:*" really made the point for me.  It's not often I get a hard, clear view of cause and effect in this stuff like I did with this.  I appreciate it you giving it to me. 

Mike

---

### Post by Mike Krall on 2017-12-02
> **oldfred said:**
> I lost posts and/or forgot or cannot find something I thought I posted, but then did not save in my notes (Zim files).[COLOR="#FF0000"] I like Zim[/COLOR] as links are directly clickable.

When a person gets in over their head, has stopped, has looked around and there is no light to move to, they might just as well head in whatever direction seems interesting...

ZIM...
[http://zim-wiki.org/index.html]("http://zim-wiki.org/index.html")

Mike

---

### Post by Mike Krall on 2017-12-05
A problem popped up tonight.  Messing with Chromium 'sync' and Xmarks bookmark manager.... going from OS to OS to make sure all Chromium 'sync' switches set the same and all Xmarks settings the same.  Third in line, elementaryOS, and find small number of updates. Run them in while checking switches and settings. Clk. 'restart' and I end up at a Grub menu with only elementaryOS, Advanced, and Setup. 

A bunch of messing around later, I can get to normal Grub menu via: Start > 'esc' > Manjaro (out of UEFI boot menu). Brings up normal Manjaro Grub menu. Can get to any of 7-OS from there.  Picking any other than Manjaro from UEFI menu (except CentOS) takes to mentioned elemetaryOS-only screen. Has GNU GRUB at the top, same version as others.  Any restart from any OS takes to elemetaryOS-only Grub menu. 

What updates? Don't know and don't know where to find them, either.

Tried (best guess) "update-grub" in elementaryOS, Manjaro, Ubuntu 16.04. No change.

Looked at Manjaro /etc/grub.d... normal, but didn't dig into each and every entry. 

"efibootmgr" looks same as always... not right, but the same (I've got another copy of it while all was working):
```
:~$ efibootmgr
BootCurrent: 0005
Timeout: 2 seconds
BootOrder: 0000,0005,0001,0003,0004,0002
Boot0000* ubuntu
Boot0001* bodhi
Boot0002* CentOS Linux
Boot0003* neon
Boot0004* CentOS Linux
Boot0005* Manjaro

```

So you know, I've needed to "fix" UEFI boot menu. Need to figure out how first and haven't.  You can see there are not 7 entries, that CentOS is listed twice (both take to CentOS menu screen). The 'bohdi' is a remnant... installed elementaryOS over it a long time ago. Both Linux Mint and Ubuntu Budgie are missing. There is a similar (not identical) error structure in UEFI firmware under 'Advanced' > 'Boot Order'... I've ordered the entries as real as possible.  Haven't figured out how to 'Add' or 'Delete' entries... keep meaning to write to ASUS about that.

This is what the real world looks like... partitions and OS in proper order:
```
:~$ sudo parted /dev/sda unit s print
Model: ATA Micron_1100_MTFD (scsi)
Disk /dev/sda: 500118192s
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start       End         Size       File system     Name                  Flags
 1      2048s       1023999s    1021952s   fat32           EFI System Partition  boot, esp
 2      1024000s    49852124s   48828125s  ext4            16.04 LTS
 5      49852416s   98680831s   48828416s  ext4            elementaryOS
 6      98680832s   147509247s  48828416s  ext4            KDE Neon
 7      147509248s  196337663s  48828416s  ext4            LM-Cinnamon
 8      196337664s  245166079s  48828416s  ext4            Manjaro-Xfce
 9      245166080s  293994495s  48828416s  ext4            Ubuntu-Budgie16
10      293994496s  342822911s  48828416s  ext4            CentOS-7
 4      396591104s  494256127s  97665024s  ext4            Data Partition
 3      494256128s  500117503s  5861376s   linux-swap(v1)  Swap
```

It's too late to do any thing else...  would someone wave a magic wand, please... 

Mike

---

### Post by Dennis N on 2017-12-05
> A problem popped up tonight. Messing with Chromium 'sync' and Xmarks bookmark manager.... going from OS to OS to make sure all Chromium 'sync' switches set the same and all Xmarks settings the same. Third in line, elementaryOS, and find small number of updates. Run them in while checking switches and settings. Clk. 'restart' and I end up at a Grub menu with only elementaryOS, Advanced, and Setup.

Sounds like grub was reinstalled - did that happen in those updates? In addition, sounds like the os prober is disabled in elementary. Is that the case? 

Is EFI boot menu display current? (after the problem was seen). It shows boot will default to Ubuntu (0000). Is Elementary* based on Ubuntu? Does Elementary* use Ubuntu installer? If so, Elementary* could register in EFI menu as Ubuntu like many Ubuntu derivatives (Linux Mint, for example) would. If so, this is also consistent with grub reinstall from Elementary*.

Boot order in EFI needs to be changed back to 0005 first in the boot order. (Use efibootmgr -o 0005)

*never tried this particular distro, and know little about it.

---

### Post by oldfred on 2017-12-05
You also can use efibootmgr to delete older or duplicate entries in UEFI, if you do not do it from inside your system's UEFI. See this and more examples in link in oldfred's signature.
man efibootmgr 

sudo update-grub is a link or shortcut. Many systems do not have shortcut and use full grub-mkconfig command which may vary somewhat on details.

fred@Asusz97:~$ whereis update-grub
update-grub: /usr/sbin/update-grub /usr/share/man/man8/update-grub.8.gz
fred@Asusz97:~$ cat /usr/sbin/update-grub
#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

---

### Post by Mike Krall on 2017-12-07
Sorry... I'm here. 

Looked at elementaryOS /var/log/apt/history.log to see what the last update was.  The file is empty and so is the same file in the historical .gz for the same.  Not so in Ubuntu 16.04... recent updates are listed and .gz for same are populated. Who knows why not in elementaryOS.  

The estimate elementary had overwritten 'ubuntu' in /boot/efi/EFI was correct.  I put it back to Ubuntu 16.04... added Ubuntu 16.04 line and commented out elementaryOS line.  Also went into UEFI > Advanced mode > Boot... and reset Manjaro to first in line. Everything went back to 'as was'. Then I started reading. I don't get it any more than I did before.  Thanks for the clues and I'll keep on with it.  I do need to make all the pieces in this be right and I may as well do it now.
-----------------------------------

'Dennis N'...  
* os prober is disabled in all OS. 
* elementaryOS is Ubuntu LTS based... so it lags. I'm on same kernel as Ubuntu 16.04, though. 
* Basically elementaryOS is a sort-of-Mac-like form with a distinct effort to "just have a computer to run"... simple and quiet.  Upshot is, lots of stuff done easily in many Linux OS are not simply available in elementary.  And it is considered to be very pretty.  I've messed with it a little bit.  Right now, it's just too easy to work in Ubuntu or Manjaro.

Looks like this now:
```
~$ efibootmgr
BootCurrent: 0005
Timeout: 2 seconds
BootOrder: 0005,0000,0001,0003,0004,0002
Boot0000* ubuntu
Boot0001* bodhi
Boot0002* CentOS Linux
Boot0003* neon
Boot0004* CentOS Linux
Boot0005* Manjaro
```
I got a letter off to ASUS about add/delete UEFI Boot order.  Mostly it's about what the entry-path is supposed to be. My friend the Internet not helpful this time. 

Mike

---

### Post by Mike Krall on 2017-12-07
> **oldfred said:**
> You also can use efibootmgr to delete older or duplicate entries in UEFI, if you do not do it from inside your system's UEFI. See this and more examples in link in oldfred's signature.
man efibootmgr 

sudo update-grub is a link or shortcut. Many systems do not have shortcut and use full grub-mkconfig command which may vary somewhat on details.

fred@Asusz97:~$ whereis update-grub
update-grub: /usr/sbin/update-grub /usr/share/man/man8/update-grub.8.gz
fred@Asusz97:~$ cat /usr/sbin/update-grub
#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

I ran into the 'update-grub' short cut thing in CentOS.  Not usable there, and due to Grub2 and/or UEFI  there is a tweak on the form you show... CentOS goes: *grub2-mkconfig -o /boot/efi/EFI/centos/grub.cfg.*  Part of the difference is the different 'grub.cfg' location you noted pages ago. 

I've got a little folder with 'efibootmgr' stuff in it.  I've been through it a few times and looking to go around enough to deal with things.  Going to find your signature link reference now. 

My* 'whereis update grub', etc.* (from elementaryOS) looks same as yours (from Ubuntu, I presume):
```
~$ whereis update-grub
update-grub: /usr/sbin/update-grub /usr/share/man/man8/update-grub.8.gz
waldo@11:~$ cat /usr/sbin/update-grub
#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"
```
Mike

---

### Post by Dennis N on 2017-12-07
I define an alias in ~/.bashrc:
```
alias update-grub='sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg'
```

---

### Post by Mike Krall on 2017-12-07
> **Dennis N said:**
> I define an alias in ~/.bashrc:
```
alias update-grub='sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg'
```

I remember it now, 'Dennis N'.  Thanks for reminding. I've made area in /mnt/data for each OS... things I've done.  Got this in CentOS now... along with '.bash.history' with notes, copies of changed stuff, etc.

Why did you make your alias 'update-grub' and not 'sudo update-grub'? 

Mike

---

### Post by Dennis N on 2017-12-09
> Why did you make your alias 'update-grub' and not 'sudo update-grub'?
The command defined by alias needs to be one word. sudo update-grub is two words. Also, if you define:
```
alias update-grub='grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg'

```
it fails when you then attempt to use it with sudo, as **sudo update-grub**. Seems reasonable, but gives an error. Only the version in post #402 works for me and you must use just 'update-grub' as the command. I think I only have updated grub once since installing fedora, and that was to get rid of the os prober entries; leaving these will just make update-grub in the controlling OS take longer to sort it all out.

---

### Post by Mike Krall on 2017-12-10
> **Dennis N said:**
> The command defined by alias needs to be one word. sudo update-grub is two words. Also, if you define:
```
alias update-grub='grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg'

```
it fails when you then attempt to use it with sudo, as **sudo update-grub**. Seems reasonable, but gives an error. Only the version in post #402 works for me and you must use just 'update-grub' as the command. I think I only have updated grub once since installing fedora, and that was to get rid of the os prober entries; leaving these will just make update-grub in the controlling OS take longer to sort it all out.

Thanks, 'Dennis N'.  I see it !

I don't know how much 'update-grubbing' I'll be doing from now on... at least compared to the amount I was doing getting the separate-data-partition menuentry in, then straightened out.  I'm going to set up an alias for CentOS, even though I've got the '*grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg*' command noted in my */.bash.history*.  Keeps things simple-er... 

Mike

---

### Post by Mike Krall on 2017-12-10
Still on *'efibootmgr'*.  Got an answer from ASUS to a question I didn't ask.  I'll get it straightened out there sooner or later (e-mail support from ASUS takes time).  Reread 'oldfred' signature-link under *'find' efibootmgr'*.  While waiting on ASUS, went on a search for '*efibootmgr'*... what is?... how to use?... etc. Collected some links... got rid of some links... towards the end of searching found these two.  Both are a long row to hoe.  The first is a lot easier on the halt and the blind.  As in 'oldfred' signature-link, I got to *'efibootmgr'* specifics using *'find'*.

Adam Williamson "AdamW" "Happy Assassin" - Jan. 2014:
[https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/]("https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/")

Arch Wiki - Unified Extensible Firmware Interface.... last edit Dec 3, 2017...  lots of connected articles and links:
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface]("https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface")

As 'efibootmgr' is a tool used in UEFI, reading the whole of both of them seemed the thing to do.  This will take me a while. 

Mike

---

### Post by oldfred on 2017-12-11
See also  for specific commands, parameters and examples:
man efibootmgr

---

### Post by Mike Krall on 2017-12-24
I've gotten side tracked... this thread is not forgotten or thought about, though.  Still, it is almost Christmas.  Merry Christmas to you, 'OldFred',  and Merry Christmas to you, 'Dennis N'.

Mike

---

### Post by oldfred on 2017-12-24
And a Merry Christmas to you.

---

### Post by Dennis N on 2017-12-25
Happy holidays to you. Have you got all the multibooting issues sorted out? I see you have had no further questions posted for a while.

---

### Post by Mike Krall on 2017-12-26
> **Dennis N said:**
> Happy holidays to you. Have you got all the multibooting issues sorted out? I see you have had no further questions posted for a while.

All the OS's are up and running.  There are tag ends needing dealt with... bits and pieces of this and that... a lot of them, actually.  

Everything is a "little by little" endeavor for me. There are some major topics brought up during this thread I've not dug into enough to work well with...  backups, for one. I've got info and suggestions, just need to do it.   

I mentioned getting side-tracked.  Specific to UEFI and Grub menu's... as in 'oldfred' post a few back > See also for specific commands, parameters and examples:
man efibootmgr. It's a matter of me re-reading the collected info and getting focused enough to figure out necessary questions needed asked (or not)... then straightening the menu's out.  I'm going to have to contact American Megatrends about ASUS firmware in this laptop and specifics of adding/deleting/creating correct naming and paths (if I want to be able to do menu stuff directly, as opposed to using 'efibootmgr'... or knowing both). ASUS didn't have anyone I could talk (e-mail) to who knew about it... =[

Thanks for asking, 'Dennis N'... it helps me keep this mentally current.

Mike

---

### Post by Mike Krall on 2018-01-10
Turns out American Megatrends (my UEFI version is 302) acts like they work with the "end users" but the reality is, tech. support e-mails won't send with common e-mail accounts (g-mail, yahoo, ISP provider) and I've not figured a way around that.  So it's* efibootmgr* or nothing. 

I did a "Fred-search" for oldfred+efibootmgr and one for Dennis N+efibootmgr, too (site:ubuntuforums.org).  Pages and pages.  Added *+2016* to the 'oldfred' line and got the number down to 146... duplicates, if any, will likely be in multiple-post use of *efibootmgr*.  Problem I find with the Google return-format is it's not pointed well to giving a person an idea of contents (not like what a person gets in a straight Ubuntu Forums search return). Sigh...     

Mike

---

### Post by Mike Krall on 2018-01-10
Low and behold, I do, actually, have a question...

Looking through *efibootmgr* search-hits mentioned in last post. Found one with both of 'oldfred' and 'Dennis N'.  Had a fair amount of command line using *man efibootmgr* options...
```
waldo@11:~$ efibootmgr -h
efibootmgr version 0.12
usage: efibootmgr [options]
	-a | --active         sets bootnum active
	-A | --inactive       sets bootnum inactive
	-b | --bootnum XXXX   modify BootXXXX (hex)
	-B | --delete-bootnum delete bootnum (hex)
	-c | --create         create new variable bootnum and add to bootorder
	-C | --create-only	create new variable bootnum and do not add to bootorder
	-D | --remove-dups	remove duplicate values from BootOrder
	-d | --disk disk       (defaults to /dev/sda) containing loader
	-e | --edd [1|3|-1]   force EDD 1.0 or 3.0 creation variables, or guess
	-E | --device num      EDD 1.0 device number (defaults to 0x80)
	-g | --gpt            force disk with invalid PMBR to be treated as GPT
	-i  | --iface name     create a netboot entry for the named interface
	-l  | --loader name     (defaults to \EFI\redhat\grub.efi)
	-L | --label label     Boot manager display label (defaults to "Linux")
	-n | --bootnext XXXX   set BootNext to XXXX (hex)
	-N | --delete-bootnext delete BootNext
	-o | --bootorder XXXX,YYYY,ZZZZ,...     explicitly set BootOrder (hex)
	-O | --delete-bootorder delete BootOrder
	-p | --part part        (defaults to 1) containing loader
	-q | --quiet            be quiet
	-t | --timeout seconds  set boot manager timeout waiting for user input.
	-T | --delete-timeout   delete Timeout.
	-u | --unicode | --UCS-2  pass extra args as UCS-2 (default is ASCII)
	-v | --verbose          print additional information
	-V | --version          return version and exit
	-w | --write-signature  write unique sig to MBR if needed
	-@ | --append-binary-args file  append extra args from file (use "-" for stdin)
	-h | --help             show help/usage

```
How does a person figure how to order the options?  Is there a logic to it?  I've thought , with some 'man' pages, the listing of the options was the logic... as in, if a person wanted to set as active (-a -- active), it would be the first thing in a command expression.  Other times the options look like they do here "purely alphabetical" and not likely a logic.  

Mike

---

### Post by oldfred on 2018-01-10
The few times I have seem multiple options like when  adding a new entry, it does not seem to matter on order.
Most of the time I am just copying what someone else posted as a working command, with updates for details.

the man command also has some examples.

---

### Post by Dennis N on 2018-01-10
We need to check the man page to see the structure of a bash command with regard to arguments and options. Order of any options included usually does not matter (ls -al = ls -la). The man pages are generated by some files in /usr/share/man, so they can vary in appearance according to how the author wants them to look.

---

### Post by Mike Krall on 2018-01-10
Thank you both... helps.

'oldfred' said:
> The man command also has some examples
I searched 'man command' and found these...  
[https://www.computerhope.com/unix/uman.htm]("https://www.computerhope.com/unix/uman.htm")
[http://www.linfo.org/man.html]("http://www.linfo.org/man.html")

The link at the end of the second link doesn't seem to go where the description indicates... maybe just takes more time to look/find.  Sounds to be a place I should be (beginner).

Mike

---

### Post by oldfred on 2018-01-10
Should have been more clear. Man is the manual for commands.
Or 
man efibootmgr

---

### Post by Mike Krall on 2018-01-11
OK, I've got it now.  Thanks, 'oldfred'

Mike

---

### Post by Mike Krall on 2018-01-12
I need to delete one of two CentOS in ESP boot menu. 
```
waldo@11:~$ efibootmgr -v
BootCurrent: 0005
Timeout: 2 seconds
BootOrder: 0005,0000,0001,0003,0004,0002
Boot0000* ubuntu	HD(1,GPT,591246c8-678b-4b3a-a890-0a0db0402efc,0x800,0xf9800)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* bodhi	HD(1,GPT,591246c8-678b-4b3a-a890-0a0db0402efc,0x800,0xf9800)/File(\EFI\BODHI\SHIMX64.EFI)
Boot0002* CentOS Linux	HD(1,GPT,591246c8-678b-4b3a-a890-0a0db0402efc,0x800,0xf9800)/File(\EFI\CENTOS\SHIM.EFI)
Boot0003* neon	HD(1,GPT,591246c8-678b-4b3a-a890-0a0db0402efc,0x800,0xf9800)/File(\EFI\NEON\SHIMX64.EFI)
Boot0004* CentOS Linux	HD(1,GPT,591246c8-678b-4b3a-a890-0a0db0402efc,0x800,0xf9800)/File(\EFI\CENTOS\SHIMX64.EFI)
Boot0005* Manjaro	HD(1,GPT,591246c8-678b-4b3a-a890-0a0db0402efc,0x800,0xf9800)/File(\EFI\MANJARO\GRUBX64.EFI)
```

Ran into this link (See end of code line near top):
[https://noobient.com/post/165797742756/fixing-the-efi-bootloader-on-centos-7]("https://noobient.com/post/165797742756/fixing-the-efi-bootloader-on-centos-7")

That and some looking into the two CentOS boot menu entries a few months ago leads me to thinking "\SHIM.EFI" is the one I want to keep.  I've got a vague memory of events causing second entry and why, but I can't get it pinned. Anyhow, both 'oldfred' and 'Dennis N' have RHEL-like OS installed.  Is "\SHIM.EFI" the native install form? 

A thing also noted in the code line was the use of the word for the option, as opposed to the letter (--label label instead of -L label).  Seeing the names used makes 'man efibootmgr' make a lot more sense for me.  

Continuing with --label label...  looking at names in code lines above... I wondered what causes the name, as in, where does it come from? I'm dead sure Manjaro made it's label and am pretty sure CentOS Linux did also (twice). Then there are the rest. Did KDE Neon make it's label 'neon'?  Asking because it seems like using what the OS wants (uses) is the right and proper way.  (I do need to go into GPartEd and create labels (per, long past, 'oldfred' rational here... one of the many little bits and pieces still lying around in the dirt.)  My original thought was to label in GPartEd as I choose, but wondering if using OS self naming as labels for use in GPartEd and 'efibootmgr' work is more right.  

So, again, where do the 'efibootmgr' names come from?

Mike

---

### Post by Dennis N on 2018-01-12
I don't have CentOS, but Fedora 27's EFI folder contains:

```
[root@Zotac EFI]# ls fedora -1
BOOT.CSV
BOOTX64.CSV
fonts
fw
fwupx64.efi
grub.cfg
grubenv
grubx64.efi
mmx64.efi
MokManager.efi
shim.efi
shimx64.efi
shimx64-fedora.efi

```
> Is "\SHIM.EFI" the native install form?
On Fedora 27, mine is booting to shim.efi. Korora is the same. I think that is the default when installed. 

> where do the 'efibootmgr' names come from?
I believe it comes from what the label option is set to when you installed.

---

### Post by oldfred on 2018-01-12
I may have posted before. In several threads.

I long ago filed a bug report so a second install could have its own UEFI entry. Every install of any flavor except kubuntu overwrites /EFI/ubuntu. About the same time they updated grub to allow kubuntu as an entry. 
I have created unique entries, just be changing the default in /etc/default/grub. But it still is hard coded to find grub.cfg from /EFI/ubuntu so does not really work.
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR='Ubuntu16.04_Xenial'

It looks like many distributions use this, as the efi_distributor is the variable that is the name in the UEFI entry and bootloader_id 
 efi_distributor = bootloader_id; 
But Ubuntu does this for every reference of efi_distributor.

 efi_distributor = "ubuntu" 
But then did the change, with  just an if type statement, that if Kubuntu use kubuntu, not ubuntu.

Distributions that will boot with UEFI Secure Boot use shimx64.efi  which is the shim between secure boot and grub. I believe shimx64.efi works with secure boot off, so have not understood why grubx64.efi still is added to efi menu.

Fedora also has this and they use the full grub.cfg in the ESP, not the configfile that Ubuntu uses for the full grub.cfg in /boot in the install:

 Fedora
grub2-install shouldn't be used on EFI systems. The grub2-efi package installs a prebaked grubx64.efi on the EFI System partition, which looks for grub.cfg on the ESP in /EFI/fedora/ whereas the grub2-install command creates a custom grubx64.efi, deletes the original installed one, and looks for grub.cfg in /boot/grub2/.
efi_distributor = bootloader_id;
alias update-grub='sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg'

---

### Post by Mike Krall on 2018-01-12
> [QUOTE]where do the 'efibootmgr' names come from?
I believe it comes from what the label option is set to when you installed.[/QUOTE]

I didn't label anything but ESP (sda1) when installing... none of OS's or Swap.  Or, not in GPartEd, at least.  Maybe somewhere else, but not remembering and notes don't show it.  I'm going to create labels in GPartEd anyhow.  Will see if anything changes... (not betting that way, though).

Thanks, 'Dennis N'...

Mike

---

### Post by oldfred on 2018-01-12
Labels on partitions are only used for default mounts instead of UUIDs.
Some partitions I mount with fstab and label then does not matter. I have labeled partitions DATA and mounted in fstab as /mnt/data and gotten confused.
And to add to confusion, gpt has its own labels.
But I label partitions so I know what is in my other partitions that I do not mount.
And a new install with format, erases labels.

To see labels:
 UUID & labels
ls /dev/disk/by-label -lah
sudo blkid -o list
lsblk -f -o +PARTLABEL /dev/sda

---

### Post by Dennis N on 2018-01-12
> I didn't label anything but ESP (sda1) when installing... That 'label option' was a reference to whatever the installer supplies to UEFI firmware for the boot manager display label. Probably a poor choice of words on my part.

There is a label option in the efibootmgr, and you can use it in changing the display label after installation. I have done that a couple of times.

---

### Post by Mike Krall on 2018-01-13
> **Dennis N said:**
> That 'label option' was a reference to whatever the installer supplies to UEFI firmware for the boot manager display label. [COLOR="#0000FF"]Probably a poor choice of words on my part.[/COLOR] 

[COLOR="#FF0000"]There is a label option in the efibootmgr, and you can use it in changing the display label after installation. I have done that a couple of times.[/COLOR]

[COLOR="#FF0000"]Thanks, 'Dennis N'... another piece to the 'efibootmgr' puzzle... changes possible (without repercussion).[/COLOR] 

[COLOR="#0000FF"]Or poor choice of interpretation on my part...  =][/COLOR]

Mike

---

### Post by Mike Krall on 2018-01-14
> **oldfred said:**
> I may have posted before. In several threads.

I long ago filed a bug report so a second install could have its own UEFI entry. Every install of any flavor except kubuntu overwrites /EFI/ubuntu. About the same time they updated grub to allow kubuntu as an entry. 
I have created unique entries, just be changing the default in /etc/default/grub. But it still is hard coded to find grub.cfg from /EFI/ubuntu so does not really work.
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR='Ubuntu16.04_Xenial'

It looks like many distributions use this, as the efi_distributor is the variable that is the name in the UEFI entry and bootloader_id 
 efi_distributor = bootloader_id; 
But Ubuntu does this for every reference of efi_distributor.

 efi_distributor = "ubuntu" 
But then did the change, with  just an if type statement, that if Kubuntu use kubuntu, not ubuntu.

Distributions that will boot with UEFI Secure Boot use shimx64.efi  which is the shim between secure boot and grub. I believe shimx64.efi works with secure boot off, so have not understood why grubx64.efi still is added to efi menu.

Fedora also has this and they use the full grub.cfg in the ESP, not the configfile that Ubuntu uses for the full grub.cfg in /boot in the install:

 Fedora
grub2-install shouldn't be used on EFI systems. The grub2-efi package installs a prebaked grubx64.efi on the EFI System partition, which looks for grub.cfg on the ESP in /EFI/fedora/ whereas the grub2-install command creates a custom grubx64.efi, deletes the original installed one, and looks for grub.cfg in /boot/grub2/.
efi_distributor = bootloader_id;
alias update-grub='sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg'

Yes, part of this posted in this thread and I've found like-bits in other threads.  

Section above on '*shimx64.efi*' caused me to look.  All my OS (most Ubuntu-base with Manjaro and CentOS) have '*shimx64.efi*' in /boot/efi/EFI/<name> except Manjaro. Manjaro has only *'grubx64.efi'*.  

I have had Secure Boot off from the beginning. 

CentOS booted on *'shim.efi'* and '*shimx64.efi*'.  I still don't know how I got CentOS '*shimx64.efi*'.  Likely doing something I didn't understand well enough to do.  I have a '*grubx64.efi*' in '*/boot/efi/EFI/centos'*, along with the two mentioned and a '*shimx64-centos.ef*i'.  Don't know how to tell if I've got unwanted stuff or not.  Feel certain I did not use '*grub2-install*' command. Have used

** I want to verify...  A person should do 'efibootmgr' commands from Live-USB or not necessary?  Asking because I ran into a reference mentioning Live-USB and lost it... can't find it now to re-learn if it was specific to what I'm going to be messing with, or not.  

Have used CentOS/Fedora/etc. version of '*update-grub*'. 
--------------------------------------------------------------

I've got time constraints now through ??? I don't want to risk computer booting problems until I've got open-space to fix them... that is not now. I may get some more learning/understanding done (hope to).  Thank you both.

Mike

---

