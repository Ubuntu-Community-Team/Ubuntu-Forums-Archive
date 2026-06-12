---
title: "Hating Windows 8, NTFS, &amp; Many other things. Looking for change."
date: 2013-03-21
forum: New to Ubuntu
---

### Post by GiveMeYourBacon on 2013-03-21
Hi I might quite possibly be in the wrong forum but I'm looking for some assistance with my transition from Windows 8 to Ubuntu. I was running Windows 7 for quite some time and I did the upgrade to Windows 8 and since that moment I realized that was one of the few mistakes I have ever made when it comes to my computers. Currently I have 3 desktops & a laptop I am looking to reformat this weekend but I want to make sure that Ubuntu would be a solid choice for me, I have had a lot of friends rave about the Ubuntu OS and how switching from Windows 7/8 helped simplified their life, but I am one of those people who was raised on Windows. Starting from 3.1 on up to 95,98SE and so on.

I want to write this post so that anyone that can help me will know what hardware I am dealing with and if it will be possible to make the conversion to a new OS. So I'm listing the specs of each machine below (laptops included) and hopefully someone will be nice and understanding to help me.

My primary machine is and AMD 6 core CPU with 32gb of DDR3 RAM, The motherboard is a Gigabyte 990FXA-UD5, a 240gb SSD Boot drive, one optical BD-RW and the rest is hard drives ranging from 1.5tb to 4tb, this machine also has 4 external WD MyBook USB 3.0's plugged in. I use this machine for various things, gaming being one of them, however I was told I could VM Install Windows 7 and install my games to that and be able to play them if they have any trouble with WINE. Currently I play WoW, FFXIV, FFXI, SimCity (new one) I also play several games that are outdated and retired from over 15 years ago (i.e. Space Quest, RailRoad Tycoon, and so on) Due to Windows 8 not allowing me to play these games has well upset me in ways I cannot handle. A friend did recommend I go back to Windows XP 64 bit but to be honest that's not something I'm willing to do unless there is no other option. I also do a lot of video editing, making home movies (not the dirty kind.) so space and ram is important to Windows for this but I am sure that Ubuntu has several applications that run more efficiently.  

My secondary machine is an First Generation i7. I have used this machine as a Windows Home Server for almost 15 months for storage of media and PC backups. This is a server I have in the house that my family & friends can stream from with the WD TV Lives which I have 2 of that are hooked up. I recently added not to long ago a Sans Digital Tower 5 Bay in JBOD, they also included this eSata RocketRaid 622 card that my research has led me to believe is not very Linux capable. This rig has 16gb of RAM, 1 Optical BD-RW, several internal drives as well. I am not looking to enable the RAID function as the drives included are *not* enterprise or RAID qualified drives. Leaving them as JBOD has worked for me just fine, however the NTFS file system has me pulling my hair out, both this machine and my primary machine usually end up heavily fragmented on several drives and that means I have to use a Defragger. From what I read on EXT3/4 converting to that file system would rid me of defragging all together thus saving me more headaches. Also WHS doesn't recognize all 16gb of RAM just the first 8gb. That right there sent me looking for other alternatives.

My third machine is being used as a Linux Gateway with ClearOS. Its configured to have the cable modem run the internet through it and then I separate my network through two workgroup switches I have a families switch and my own switch. I do web hosting with another company and I am looking to save as much money as I can by hosting from home, which I am allowed to do through my ISP as of this month. Several of the domains I host do not get that much traffic (yet) and I was wondering if I should leave ClearOS on it or does Ubuntu have a variant that can make it work like ClearOS does. This machine is an AMD QuadCore with 8gb of DDR2, it has a RealTek 10/100/1000 onboard, and 2 Intel PCI 10/100/1000 adapters running to two different switches. I built this rig to help control the flow on the LAN side as well the WAN side with family & friends playing MMORPGS, Streaming Netflix, Hulu+ my $49 router I had could not handle the load that was being thrown at it. 

Lastly is my laptop. I recently got from Dell, its an Inspiron Series Core i5 Sandy Bridge with 6gb of RAM. I use this laptop for when I am out in the field, I do computer repair for several people and new builds. I also use this laptop as home as a way to "Remote Assistance" into my own desktops. 

My primary concerns would be the game playing on my primary rig, my server has this RocketRaid card with outdated drivers for Linux unless I install a very old distribution of Ubuntu, going back to 9.10. The ClearBox is not a major concern however I have found some web hosting software that would save me money each month by doing it from home. My laptop I've considered a dual booting. I have a week off starting Friday and I figured this would be the best time to get started on a large project like this, any help would be appreciated.

Also the remote assistance into my desktops is a major necessity as well. I know that being able to VNC would work but I am all about keeping the computers secure from unwanted intruders.

---

### Post by fantab on 2013-03-21
Linux/Ubuntu will work on most of the [Hardware]("http://www.ubuntu.com/certification/"). The important thing you missed to mention is about your Graphics Cards on your computers. Not all Graphics Cards manufacturers provide "decent" open source drivers.
I don't know much about running Servers, but AFAIK Linux fares far better than any other proprietory OS here. Someone with more hang of Ubuntu Server Edition will be able to guide you.

About games and Wine: not ALL Windows games are supported through Wine.. [See Here]("http://appdb.winehq.org/") for details. If you don't see your favorite game to work with wine on Linux then you have no other option but to DUAL BOOT, Windows and Linux/Ubuntu. Also Wine seems to work better in dual boot environment. You can install Windows7 just to play your games and/or other sotware that is either not available on Linux or does not have a equivalent alternative in Linux.

[Linux filesystems]("https://help.ubuntu.com/community/LinuxFilesystemsExplained") ([another source]("https://wiki.archlinux.org/index.php/File_Systems")) like ext4,[ LVM]("http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/"), etc, AFAIK don't have Defrag issues. I suggest you read about linux filesystems before you proceed.

Personally, I would suggest that you try [other Linux Distros]("http://distrowatch.com/dwres.php?resource=major") as well. You have to find your own flavor of Linux. Find out which Linux is best suited for your needs. We all have different needs.

If you have any other questions ASK here and/or search WWW.

Good Luck...

Edit: changed link to LVM.

---

### Post by carl4926 on 2013-03-21
First and foremost, let me suggest that you get the feel of things with the Live system. Either from a CD or a USB.
It's extremely unlikely you are going to make the transition in one step. So I suggest you dual boot.
I was brought up on win 3.1 > to XP
It took a couple of years for me to completely drop windows, but 10 years ago Linux didn't work quite as well as it does now.

Listing your hardware is OK, but pretty difficult for us to know. Running the system Live will give you a good idea.

The biggest problem areas today are:
UEFI
Hybrid Graphics
And any machine with Win8 pre-installed.

---

### Post by arpanaut on 2013-03-21
For starters, don't go crazy and start wiping all your machines and going linux until you get some experience.

Machine one, your gaming rig, you are not going to get the gaming experience you are used to on linux,
If this is te rig you upgraded to win8, can you downgrade to seven and go from there. 
Cut out some space on one of your drives and install Ubuntu and dual boot to get some experience.

Machine two, leave this be untill you get some experience with linux and KNOW that you can get the same functionality from Ubuntu.

Machine three, leave it be and study up on transitioning and learning what you need.

Lappy, partition out some space to dual boot and learn linux, It's not an either/or situation if you have the space you can have both.

Don't go blowing away your Windows installs until you are sure Linux can satisfy all your needs.
It takes time to learn new operating systems so don't limit yourself by giving into your frustrations and going crazy.
Don't cut off your nose to spite your face.  Take your time Linux can probably satisfy most of your needs, but give the transition time.
You will probably need to keep at least one Win install for your gaming fix, but that is changing with linux these days, so the experience is getting better.

Good Luck.

---

### Post by GiveMeYourBacon on 2013-03-21
I knew I left out the video cards. 

My Primary machine runs Dual 
AMD Radeon HD 6670 (XFX Pine Group)
AMD Radeon HD 6670 (XFX Pine Group)
CrossFire Disabled

It has a 3x monitor setup, a 32" LED & 2x24" LCD's the reason crossfire is disabled is because those cards didn't look like they could be cross fired. Everyone has told me to try the Live CD and that is what I plan on doing this weekend. I am working with some hardware that might not work with Linux, or Ubuntu. As for the games I did some more research to find that several will not work in a WINE environment, and some will so my best interest is dual booting, however the Live USB/CD will give me the entire opportunity to see what will or won't work and I can further make more of a decision to what needs to be done. The Gigabyte Mainboard I have in the past gave me some issues with booting even from the BDRW with OS's to install. 

The server also has an AMD Video Card but its a 5670 AMD Radeon. Although most servers don't run a GUI I would have to put one on it just in case. My biggest issue with Windows is now Windows 7 & 8 have some horrible networking issues and sharing with the WDTV Lives has proven to be very difficult, I thought WHS (Windows Home Server) would ease everything but I've had nothing but issues with that as well. To be honest, since Vista my faith in how well Microsoft treats their OS's has been extremely horrible, when these drives get fragmented streaming media from them can be a nightmare. Plus with WHS you have to buy the plug-ins to defrag and so on. That right there just sickens me, pay for an OS then I got to pay for key features. 

I did find out from a friend that the ClearOS box can host web sites itself with ease, it was just turned off by default so I can simply turn it on and setup my domains without any trouble. He also suggested I don't race into reformatting all of my computers because its likely I *will* run into some issues and the more frustrated I get the easier it will be for me to turn and re-install Windows. I do appreciate the replies and I would like to make Ubuntu or the KDE spin of Ubuntu my primary on all my systems (except the server, that may require a different distro altogether)

---

### Post by mastablasta on 2013-03-21
you will need to load proprietary graphics to get anything done on those maschines. i am not sure if that can be done on live. at leats oyu would need a persistant live image (on USB for example) so you could save the drivers on it for reboot.

---

### Post by midfingr on 2013-03-21
First of all. That's a very nice primary system--wow!

I would suggest backing up your Win8 install; Clonezilla, Macrium Reflect, Windows System image, etc. You may want to do a secure wipe of the SSD if and when you decide to install another OS; it only takes a few seconds, but preparation takes some time.

Have you looked into DOS Box for those older games? I have no idea if they'd work however, doesn't hurt to try. If not try WinXP (32-bit) in VMWare Player to see if those games will work. Also, compatibility mode, any luck there?

My system is very similar, a Gigabyte 990FXA-UD3, AMD 1090T 6-core, AMD 6870. What are you using for sound? Currently running Ubuntu 13.04 (alpha) on a separate hard drive, grub booting from the same drive, i.e. bootloader is not on a Windows drive. I too have Win8 Pro x64, but play newer games and those from GOG.

---

### Post by MaxLinuxLover on 2013-03-21
If you hate Windows, get Ubuntu.

---

### Post by oldfred on 2013-03-21
I suggest dual booting. I retired 6 years ago & converted to Ubuntu but dual booted XP because of one application until last year. I kept saying I would stop XP but it took forever for me to get used to the Linux app. 
I also took a while to really feel comfortable in Linux. It is different. But I really like having almost all the apps in the repository and one update not the many updates & reboots that Windows makes you do. 

 Linux is not Windows:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

   Ubuntu is not Windows
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

Some that attempt to convert to fast, come back and want help on reinstalling Windows. Best to dual boot, or at least do a full back up of Windows so you can reinstall if need be.

Many say games will not run at full speed or with best graphics in Virtual installs, dual booting may be required. There just are some games and some applications that while there are Linux equivalents they are not as good or take major effort to convert. But in other cases the Linux apps are actually better, but there still is a learning curve that takes a bit to get over that hump to feel comfortable with Ubuntu.

---

### Post by DuckHook on 2013-03-22
You are probably well aware of the general consensus by now: we are always happy to see new Linux users, but you will still need Windows for quite some time.

My two pennies: the biggest impediment to easy adoption of Ubuntu are new users themselves. The tendency is to bring Windows mindset, practices, habits of a lifetime and unrealistic expectations with them. This simply cannot be helped. It's just human nature. The first exposure is usually a "Wow, this OS is pretty cool", but the first real Ubuntu problem will result in frustration and a sense of being lost at sea. The best remedy is to set up a proper dual boot, so that you can approach Ubuntu with a sense of play and experimentation with no production pressure. Over time, you will gain an understanding of the vastly different approaches, design philosophies, cultures, etc. You then control the transition process instead of it controlling you and when the time comes to transition, it will be almost painless.

---

