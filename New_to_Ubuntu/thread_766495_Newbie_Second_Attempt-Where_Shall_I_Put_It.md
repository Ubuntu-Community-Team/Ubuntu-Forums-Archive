---
title: "Newbie Second Attempt-Where Shall I Put It?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by johnwillyums on 2008-04-25
****Hi All.
About 6 months ago I got a new PC running Windows Vista 64 bit. Soon after that I installed Gutsy Gibbon on a small partition and ran a dual boot system.
This might have been a bit ambitious and I don't think I really got to grips with Ubuntu as I was busy wrestling with problems in Vista.
Quite recently a catastrophic failure with Vista SP1 caused me to have to do a complete Vista reinstall. This wiped my Ubuntu install as well.

Now I have another hard drive and my setup is as follows:
HDD 1= c\ 259GB of which 165 GB is Vista 64x+progs and apps
       c\L\ 205 GB free space
HDD 2= d\ 441 GB of which 267 GB is media files and Vista backup
       d\k\ 23 GB free space

All of these partitions are NTFS.

My Gutsy install was originally on what is now HDD 2 partition k\ 23 GB. (This HDD was my original c\ drive previously.)
Now that Hardy Heron is here and I seem to have my problems with Vista sorted out (mostly) I'd like to try again with a dual boot and have ordered a 64x Hardy cd from Shipit.

So what I need to know is: can I do another dual boot?, Can I put Hardy on the small k\ partition as before? will I be able to boot into either OS as before?

As I say I think I messed up with my attempts with Gutsy. I overloaded it with unnecessary software- too many media players and other apps some of which I didn't know what they were for. I struggled with mythtv and miro, trying to get a DVB-tv stick to work, trying to configure wine so I could run photoshop and so on.

I received tremendous support from various people on these forums so I'm hoping someone can point me a way forward so I can continue to get to grips with Linux. The whole philosophy appeals to me and from my short time with Gutsy I was impressed with the speed and solidity of the OS but, as you can probably tell, I'm an experimenter with very little tech knowhow.

Any suggestions would be most welcome and as the disk from Shipit hasn't arrived yet I have plenty of time to prepare.

Thanks in advance, John:)

[I]specs: Asus P5N-E SLI, Q6600 CPU, BFG 8800GTS OC 512 MB GPU, 4GB RAM, 2x500GB Samsung HDDs, Thermaltake 650 watt PSU, Thermaltake Golden Orb Cooler, Thermaltake Tsunami case, Vista HP 64 bit with SP1
, [/I]

---

### Post by Toadinator on 2008-04-25
sure! it should work just as well as last time. I could give you support over IM if you need it.

---

### Post by PmDematagoda on 2008-04-25
You should be able to dual boot Ubuntu 8.04 with Vista, also, I hope you ordered the 64-bit version of Ubuntu instead of the 32-bit one since you need the 64-bit version to use all 4Gb of RAM.

---

### Post by johnwillyums on 2008-04-25
Thanks very much for the encouragement and yes PmD, I have ordered the 64 bit version of Hardy.
I suppose that'll take a few weeks to arrive so I imagine I'll be back on then for methods to install on my small partition and set up the dual boot etc.
So until then thanks very much for your input, John

---

### Post by aeiah on 2008-04-25
installing windows on one and ubuntu on another hard drive is a great idea. ive been doing it like that for a while now, and it makes upgrades and reinstallations a lot easier. i have ubuntu and grub on one hdd, so if windows messes up, i can reinstall it and it wont ruin my grub. if ubuntu and grub fail on me, i can go into my bios and set the windows hard drive to boot first and can still make use of my computer whilst i get things sorted.

---

### Post by johnwillyums on 2008-04-25
Thanks for that aeiah. 
I had an idea that it might work out better on 2 HDDs in case of screw ups on either one.
Is it easy to do? Won't it just try to install on my c\ drive?
Also would it mean booting through GRUB into either OS?
Hmmn, so many questions. 

Cheers, John

---

### Post by PmDematagoda on 2008-04-25
> **johnwillyums said:**
> Thanks for that aeiah. 
I had an idea that it might work out better on 2 HDDs in case of screw ups on either one.
Is it easy to do? Won't it just try to install on my c\ drive?
Also would it mean booting through GRUB into either OS?
Hmmn, so many questions. 

Cheers, John

If you use two hard drives then the dual-boot should be more easier to setup. Ubuntu will not attempt to install on the c drive as long as you instruct it not to which should be easy to achieve if you recognise the different hard drive information. And yes, you will be dual booting with the use of GRUB.

---

### Post by johnwillyums on 2008-05-15
Hi Folks, My CD from Shipit with Ubuntu 8.04 Desktop Edition (64 bit) just dropped through my letter box. Not bad eh? I thought it would take longer than this.
I'm dying to put it in and try to install it but scared of making a mess of the dual boot.
If you could refer to my initial post you'll see I have two 500GB HDDs partitioned as follows:

Disk 1= c\259 GB- Vista 64 bit install + programs etc.
        l\204 GB- free space

Disk 2= d\441 GB- all media files, music, movies, photos etc
        k\23 GB- free space

I'd like to put Ubuntu onto k\ on the second disk away from my Vista install and then dual boot.

Could someone run through the initial stages so I make sure I get it where I want it and don't mess up my Windows install or wipe it.
I find this partitioning stuff pretty scary and can't remember how I did it last time- more by luck than judgement I think.
As far as I know all the partitions are now NTFS since my recent reformat and reinstall of Vista reinstall. Not sure whether this matters.

Thanks in advance for any help, John

---

### Post by hyper_ch on 2008-05-15
Vista has a partitioning tool... start it and delete that partition that you want to use for Linux... in your case just delete the 23 GB partition.

DO NOT CREATE a partition, just delete it and let it be.

Then start the installation of Ubuntu and select there "Use largest continouse empty space". Since all other partitions are allocated and only the 23 GB is available, it will install there.

Btw: You should be able to use all your 4gb ram (and more) with the server-kernel instead of the generic one... just in case you have too much trouble with 64bit

---

### Post by issih on 2008-05-15
I'm not 100% sure about this as I've only installed ubuntu from scratch a few times (and some of those were messing around with usb flash drive instalations which isn't the same) but in my experience, whilst installing windows on one drive and ubuntu on another works well, there is one little quirk.... The installer tends to install grub onto the master boot record of your primary hard drive, typically that will be your windows drive. This works fine, and is in fact how my pc is set up, but it does mean that if grub gets messed up in some way, you will not be able to boot either os without a live cd and a fair bit of fiddling.

Configuring things so that grub is installed on the same drive as the actual ubuntu installation and then making that drive the first boot device in bios ought to mean that the windows drive (and its mbr/bootloader) are untouched and can then be accessed by changing the boot order in bios if errors occur, as suggested earlier. To do this hit the advanced button on the last page of the installation wizard, and tell the installer to install grub on the right drive.

It'll all work even if you forget to do this, but its what I'd do if I was starting from scratch again

Most importantly, enjoy your experimenting

---

### Post by johnwillyums on 2008-05-15
Thanks to both of you. I know Vista has a partitioning tool but I can't find it and a search doesn't either.
I've seen it before when exploring the system I'm sure.
Sorry. I'm crap at this, John

---

### Post by johnwillyums on 2008-05-15
Forget that. I found it and have now deleted it as suggested. I'm going for it now with the cd. Fingers crossed, Thanks, John

---

### Post by hyper_ch on 2008-05-15
just make sure to select "Use largest continuous empty disk space" or "Use largest continuous free disk space"...

When in doubt, note the options and ask for confirmation here :)

---

### Post by candtalan on 2008-05-15
Grub stuff and booting - with separate hard drives with ubuntu on the second HD, and using the (semi) automatic install proceses, then you will get the grub files installed (as usual) in the Ubuntu drive in the system partition.

However, the first (windows) hard drive (the active partiton or drive) is the one which is first seen after the bios wakes up - it looks at the MBR master boot record (is in the initial sectors I think). This MBR is used to direct attention then to the linux grub boot information, which is when you choose either ubuntgu or windows.

When windows is installed or reinstalled later, it is its need to re write (or 'repair') the MBR which then stops ubuntu from being easily booted, th enew MBR only includes reference to windows, and not to the linux grub boot loader which contains windows and ubuntu.

Other things being equal, the MBR can be re written with grub to get back to a dual boot system if needed, without a re install of ubuntu.

---

### Post by johnwillyums on 2008-05-15
Well I don't seem to be able to boot off the cd.
I put it in my dvd rom drive and ran it-on the first box I chose "demo and install".
I then picked "reboot now" and it booted into Windows.
I tried again, entered the setup menu in BIOS navigated to BOOT and selected DVD ROM drive. Pressed enter then F10 to save and exit plus said yes to that a second time. The system just booted into Windows again.
So I went back and started again with the cd- on the second box I chose " help me boot from cd" and installed the cd booter. This seemed to install ok.
I then went through the same procedure as above and it still just booted into Windows.
I must be doing something simple wrong. Can someone help me out?
Thanks, John

Said I was crap at this.

---

### Post by johnwillyums on 2008-05-15
Success! I don't know whether this is normal but I tried to install again and put the disk in my  DVD RW drive by mistake and it worked. I haven't tried the Windows dual boot yet but Ubuntu looks lovely and I'm just looking around and trying to remember how to enable restricted drivers etc.
I've logged onto gmail and it looks really ugly. There's no sidebars just my inbox spread right across the screen. That can't be right can it?
Thanks for your support all, John:)

---

### Post by hyper_ch on 2008-05-15
did you install it or are you using the liveCD?

---

### Post by candtalan on 2008-05-15
> **johnwillyums said:**
> Success! I don't know whether this is normal but I tried to install again and put the disk in my  DVD RW drive by mistake and it worked. I haven't tried the Windows dual boot yet but Ubuntu looks lovely and I'm just looking around and trying to remember how to enable restricted drivers etc.
I've logged onto gmail and it looks really ugly. There's no sidebars just my inbox spread right across the screen. That can't be right can it?
Thanks for your support all, John:)

Your PC BIOS will probably be set up to boot from only one CD or dvd drive, that looks like your RW drive in this case.
You now have the live CD running. Good time to check out stuff - you might need to add flash to the browser if web pages use it for example.

If you continue with the live CD running, you can click the  Install icon and the installer will begin. IIRC you have an unused space now on your HD? There will be an option in the install on that drive (drive b?) for use of uncommitted space install.

hth

---

### Post by johnwillyums on 2008-05-15
Hi and thanks to you both. I seem to have Ubuntu successfully installed where I wanted it. Also the dual boot is working. I get a choice at boot whether to go into Ubuntu or Vista.
Now I'm nearly at the point I was at before with my previous attempt.
I can't seem to enable the cube effect. I've got Compiz installed plus various connected lib files but I don't get the cube. If I press ctrl-alt and use the arrows I can go from one open desktop to the next but no 3D cube.
I've made my printer default(Canon i9950) and I think I've got the canon drivers but if I try and print a picture I can't input what type of paper or page layout etc. Everything wants to print horizontally across the middle of a piece of A4 photopaper.
I've also tried to install medibuntu as I seem to recall it being useful last time but I can't find a way to add it to software sources.
Is Automatix still around. That seemed to help last time, also Firestarter but I can't find either of them. 
Do I need security, firewalls etc?
Oh well. I seem to have forgotten everything I tried to learn 6 months ago with Gutsy and am stumbling around in the dark again.
Suppose I should make specific posts with these issues.
Thanks again for getting me started but I've already come up against the brick wall of tech ignorance that I met last time. In fact I got more going straight off (compiz effects for example) with Gutsy than this and this was supposed to be idiot proof.
Oh well, John

---

### Post by hyper_ch on 2008-05-15
- Cube
(1) you need to have 4 desktops
(2) you have to install to compiz control settngs manager (or similar called... search synaptic)
(3) in ccsm you have to enable to cube ;)

- Printer
hmmm, you have to try there or check if canon has specific drivers on their homepage

- Medibuntu
On the medibuntu homepage there is a repository howto that tells you the two steps involved to add the repos ;) (just copy'n'paste)

- Automatix
iieeeeks, don't use that... it also doesn't exist any longer (there's not really a need for it anymore)

- Security
you use linux, you are a lot more secure than on windows ^^

- Firewall
you have already one installed, but it is unconfigured... do you have a modem with an integrated router? If so, configure the firewall on there and not in ubuntu

- Antivirus
useless... malware targets windows and antivirus products for linux also remove (only) windows malware... if you operate a fileserver you might have a use for antivirus or if you want to protect others... but I think each one is responsible for their own box... it's not my job to make them secure.

---

### Post by johnwillyums on 2008-05-15
Hyper_ch, thanks for your help but I still can't do it.

I looked in synaptic and there are several compiz files installed- compiz, compiz-core, compiz-fusion-plugins-extra and more. So that seems to be alright.
However I can't seem to figure out how to get more than two desktops. I can switch between these by clicking on them but don't know how to get two more. Also don't know what CSSM is I'm afraid so don't know how to enable cube in there.

I went to the medibuntu site and found the hardy heron version. I then opened system-administration-software sources-third party software.
The instructions seem to be to copy and paste this:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

into the box saying "Enter the complete APT line of the repository you wish to add as source" so I did. Copied the whole line and pasted in but it won't. The "+ Add Source" box is greyed out and the "+ Add" in the main box does nothing.

I'm struggling here. Not even sure why I need medibuntu. Got wobbly windows though so somethings happening on the graphics front.Also have the Nvidia driver for my 8800GTS 512 GPU installed.

I must be missing something with both of the above issues. I'm not sure I have the knowledge base to do this and everywhere I look people are posting things I don't understand assuming a level of knowledge I don't have.

Any ideas on the above?, John

---

