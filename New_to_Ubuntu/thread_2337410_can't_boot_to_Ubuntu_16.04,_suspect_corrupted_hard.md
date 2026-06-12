---
title: "can't boot to Ubuntu 16.04, suspect corrupted hard drive"
date: 2016-09-17
forum: New to Ubuntu
---

### Post by infinityloops on 2016-09-17
TL;DR: I can't boot to Ubuntu 16.04 after trying to create a dual boot system on 2 separate internal hard-drives. Boot problems started with my computer unexpectly rebooting every so often without prompt. Boot-Repair doesn't seem to be working and hangs for a very long time on purging kernels and reinstall last kernal mapper/ubuntu-vg-root(ins). I'm guessing my boot partion is corrupted, but unsure? Looking for advice on how to solve this problem or whether I need to reinstall Ubuntu. Thanks!!!!


Here is my pastebin file: [http://paste2.org/80phmcKH](http://paste2.org/80phmcKH)

The Long story:
Hi, I'm new to both the forum and linux. Ubuntu is my first distro. I've been using Ubuntu 16.04 for the past month or so, no heavy usage...just playing around mostly. Anyway, I started running into problems yesterday. It started with me installing a second internal hard-drive. The HD was off an old computer that I was disposing of. I wiped the drive and had the intention of loading Elementary OS and another distro (tbd) onto this hard drive it so I could check them out. I used gparted to format and partition the new hard drive. I was making 3 partitions so I could run 2 distros and have some extra space. I downloaded a live ElementaryOS to a usb and was trying to install it to a partition when trouble began. I was unable to install ElementaryOS to one of the partitions I created and I ended up editing the partitions of the new HD in the installer. Watching youtube videos it seemed that I needed to  I could to reformat the new HD and then create a couple partitions for boot,root, swap, home. I started this process  and then ended up walking away for a bit to help my wife. When I came back, my computer was frozen. I did a hard reset and rebooted and started the process again....I get to the ElementaryOS installation set-up again and my computer reboots.....I shut down an let it sit for a couple hours. I come back and restart just trying to get into Ubuntu and I make it!!!....then it reboots.....I go into Bios and check settings and try to load in fail-safe and it shuts down in Bios. The shutting down/restart goes on for quiet a while and I get to various points in the boot-up...sometimes fully booted and then 10 min go by and shut down, sometimes it make it 2 seconds on a reboot before shutting down. I trouble shoot this and remove the CMOS battery on my mobo, remove and reseat RAM, Remove and reseat graphics card, unhook the second internal drive, dust a bunch of stuff, etc. Upon starting up, everything seems to be running stable again, no reboots and I'm still able to load Ubuntu. I decide to run a memtest on my RAM overnight to check it. Wake up, passed 4 tests with no errors...so I end the test. I reboot again and get into Ubuntu desktop and work in it a bit and feel like everything seemed to be okay. I decide to shut it down and reattach the second hard drive (just attach, not boot to it). Upon doing this, I start to run into trouble again. It doesn't reboot, but just won't load Ubuntu. So I unattach the drive and reboot. Doesn't boot to Ubuntu. I grab my live USB and boot to the live Ubuntu USB and download boot info and boot repair. I run boot repair and I get it hangs up on "Purge Kernels then reinstall last kernel mapper/ubuntu-vg-root(ins) . It's been running for about an hour and nothing happening.

---

### Post by DuckHook on 2016-09-18
Welcome to the forums, infinityloops.

Sorry that your introduction to Ubuntu had to start this way. If I understand you correctly, your problems started when you physically installed the second HDD. As an old-hardware hound, I have had a number of run-ins with older HW. When I hear symptoms that coincide with a change in HW, one of my suspicions is always HW failure. Given the pattern of your problems, I would suspect either a failed disk controller, a failing MOBO, failing PSU or bad SATA wiring/connectors. As is the case with all diagnostic efforts, I could be completely and hopelessly wrong, so don't go buying new equipment on the strength of my poor guesses. But, for what it's worth, yours sounds very similar to HW issues that I've wrestled with in the past.

Please provide a full description of your HW. We need proper info in order to help. Examples of the sort of info can be found in my signature link: How to Ask for Help.

It is also very possible that your cause is not HW, but a corrupted OS from the succession of failed installs. Do you have complete backups of all your data? If not, then your first order of business is to back up, using your LiveUSB. If yes, then are these backups reliable (have you tested them for restore integrity)?

I'm turning in for tonight, but please post as much info as possible along with answers to the above questions. Anyone who can help will appreciate having it handy.

---

### Post by infinityloops on 2016-09-18
Thanks for the reply! everything started to fall apart with setting up the second internal harddrive. I've run tests on both drives and they seem to be okay from an HD hardware standpoint. 

my system specs are as such:


[FONT=arial]CPU:[/FONT][FONT=arial] Intel Core 2 Quad Q6600 Kentsfield 2.4GHz LGA 775 Quad-Core

[/FONT][FONT=arial]MotherBoard: [/FONT][FONT=arial]GIGABYTE GA-EP45-UD3L LGA 775 Intel P45 ATX Intel Motherboard

[/FONT]Video card:[FONT=arial]EVGA 512-P3-N871-AR GeForce 9800 GTX

[/FONT][FONT=arial]Power Supply: [/FONT][FONT=arial]CORSAIR CMPSU-450VX 450W ATX12V V2.2 80 PLUS

Internal Hard Drive #1: [/FONT][FONT=arial]Western Digital Caviar SE16 WD6400AAKS 640GB 7200 RPM SATA 3.0Gb/s Hard Drive[/FONT][FONT=arial]Internal 

Hard Drive #2 (repurposed from my wife's old computer): Hitachi Deskstar [/FONT]HDT722525DLA380 320GB
[FONT=arial]
Ram: 2 sticks [/FONT][FONT=arial]A-DATA Vitesta 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)[/FONT]
[FONT=arial]Dual Channel Kit Desktop Memory Model ADQVD1B16K

[/FONT][FONT=arial]2 sticks of (recently bought from ebay): [/FONT]G.SKILL PI Black 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model F2-6400CL4D-4GBPI-B[FONT=arial]Hardrive

Rams seems okay based on memtest86 I've run yesterday/today. 

This computer was my first and only home build which is why it holds a special place in my heart. It was made in early 2009 and ran Windows XP until 2014 when support stopped. At that point, I basically haven't touched it and in the process I switched to an Apple Macbook for work and personal life. Not wanting to rid of this piece of my personal history, I decided to breathe new life into it with some cheap ram I found on ebay and Ubuntu 16.04. 

I plan to use this computer, eventually, as my main squeeze for editing photos, videos, other media, etc. I familiar with darkroom and other heavy apps. Regardless, I feel like my old system is still pretty capable by today's standards. [/FONT]

---

### Post by DuckHook on 2016-09-19
> **DuckHook said:**
> …Do you have complete backups of all your data? If not, then your first order of business is to back up, using your LiveUSB. If yes, then are these backups reliable (have you tested them for restore integrity)?Please provide answers to above. No matter what course of action you take, your data integrity must always come first.> **infinityloops said:**
> …Not wanting to rid of this piece of my personal history, I decided to breathe new life into it with some cheap ram I found on ebay and Ubuntu 16.04. 

I plan to use this computer, eventually, as my main squeeze for editing photos, videos, other media, etc. I familiar with darkroom and other heavy apps. Regardless, I feel like my old system is still pretty capable by today's standards.I admire your desire to repurpose older HW instead of just adding to our mountains of e-waste. Good on you.

Your HW may be older, but it should handle one of the current 'buntus with no problem. The only suggestion that I might make would be to change to one of the lighter flavours like Lubuntu, Xubuntu or Ubuntu-MATE. Any of these three should offer you improved performance and response times. Most importantly, they leave you more overhead for the graphically-intensive apps that you want to run. Note that apps evolve to make use of the more powerful HW current with our times. Therefore, "heavy apps" may not work that well on your HW. Linux is not a magic wand and it cannot make old HW behave beyond its capacity.

Now, on to your problem. I'm trying to look at your situation from a bird's eye view rather than focusing on the lower-level issues, and what I see is the following:

[LIST=1]
[*]
[*]You are running a resource-heavy flavour that is not the best one for your HW.
[*]You've already spent dozens of hours trying to chase down the problem in both HW and OS.
[*]Even if we eventually could find the problem (which is far from guaranteed), it will likely take many more hours/days.
[/LIST]
Since a new install takes far less time than the hours you've spent diagnosing, why not just do so? If you are treating this problem as a challenge that you want to go through for learning purposes, then that's a different matter. But you've already stated that the intent is to make it useful as a productivity tool. If so, then there doesn't seem to be much point in chasing ghosts.

[LIST=1]
[*]
[*]If the problem is your HW, a new install (this time with the second HDD attached) will show that up definitively.
[*]If the problem is a corrupted OS, then a new install will make chasing down the cause moot.
[*]A new install gives you the opportunity to replace Ubuntu with a lighter-weight flavour that leaves you more resources for what you really want to do.
[/LIST]
Does this sound like a reasonable course of action?

---

### Post by infinityloops on 2016-09-19
> **DuckHook said:**
> Please provide answers to above. No matter what course of action you take, your data integrity must always come first.I admire your desire to repurpose older HW instead of just adding to our mountains of e-waste. Good on you.

Yeah, I've got my data backed up, I'm good to go there. 

> **DuckHook said:**
>  HW may be older, but it should handle one of the current 'buntus with no problem. The only suggestion that I might make would be to change to one of the lighter flavours like Lubuntu, Xubuntu or Ubuntu-MATE. Any of these three should offer you improved performance and response times. Most importantly, they leave you more overhead for the graphically-intensive apps that you want to run. Note that apps evolve to make use of the more powerful HW current with our times. Therefore, "heavy apps" may not work that well on your HW. Linux is not a magic wand and it cannot make old HW behave beyond its capacity.

I've got an image of ElementaryOS Loki that I believe is considered a lightweight OS. I was planning on dual installing Elemetary OS and Ubuntu which would give me some flexibility. I generally thought my hardware specs were enough to run the heavier Ubuntu, but I might take the opportunity to try out Ubuntu Mate. 


> **DuckHook said:**
>  a new install takes far less time than the hours you've spent diagnosing, why not just do so? If you are treating this problem as a challenge that you want to go through for learning purposes, then that's a different matter. But you've already stated that the intent is to make it useful as a productivity tool. If so, then there doesn't seem to be much point in chasing ghosts.

[LIST=1]
[*]If the problem is your HW, a new install (this time with the second HDD attached) will show that up definitively.
[*]If the problem is a corrupted OS, then a new install will make chasing down the cause moot.
[*]A new install gives you the opportunity to replace Ubuntu with a lighter-weight flavour that leaves you more resources for what you really want to do.
[/LIST]
Does this sound like a reasonable course of action?

I was looking at the problem as a possible learning opportunity and a challenge since it was kind of  a low pressure situation. My main computer right now is an Apple MBP with OSx and I was considering this old desktop as something to experiment with linux and learn on a bit as I've become intrigued by it since I started building raspberry pi projects as a hobby early this year. That said, I spent 2 days trying to resolve the boot problem to no avail and I've decided to do a reinstall as you recommend. It'll give me the opportunity to partition the drives better and do some research on the best way to do a dual or triple boot system with the 2 HDDs. Thanks for the recommendations and help!

---

### Post by oldfred on 2016-09-19
It looks like you have a corrupted sda1, the /boot partition of your LVM install. I have never used LVM, but many who want/need full drive encryption have to use it. 

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

Then rerun Boot-Repair to update grub on sda.

Boot-Repairs report seemed to show partitions inside the LVM, but if you have to run fsck on them, you have to mount the lvm first.
 
You are not showing sdb drive, other than your flash drive installer. Is second drive plugged in?
Forced shutdown, power failures or other abnormal halts often damage file system and you need fsck to repair it.

You system should run full Ubuntu. My 2006 build was rebuilt in 2009 and very similar to yours. When UEFI systems came out I wanted a new shiny UEFI system. But Microcenter had a small SSD below $100 which I figured I would use in new build about 2011. But my old system then became so fast I could not justify new UEFI build to myself, much less my spouse. I finally did build new system about 2 years ago.
I think old system ran Unity ok, as I had nVidia 9600 video which was a good card. Your 9800 also is a better card. But I always immediately converted to fallback(now gnome-panel) which was the old menu system as my monitor is an older 4:3 and menu on top is better. Fallback is similar to some of the other older menu flavors. But I am still running fallback in 16.04 without major issues.
      
 Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)

---

### Post by DuckHook on 2016-09-19
@infinityloops

oldfred is now onto your situation and I leave you in his capable hands.

---

