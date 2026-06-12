---
title: "HowTo: Ubuntu on HP DV6636NR"
date: 2008-07-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Dark_Stang on 2008-07-26
****IMPORTANT**** I am no longer supporting this guide. This laptop is now retired because the hardware is starting to fail after 2.5+ years of hard use. Thank you, Ubuntu Community, for your enthusiasm. (6/1/2010)

This is a continuation from an archived thread, located [here.](http://ubuntuforums.org/showthread.php?t=575750) As it is archived I can no longer edit it.

Notes: This guide is designed for my laptop and for Ubuntu 8.04LTS, Ubuntu 9.04, Ubuntu 9.10, or Ubuntu 10.04. 8.10 **DOES NOT WORK** on this model. Go to the end to see a few special notes on Ubuntu 9.10 or 10.04. If you have a laptop similar to mine, this guide *should* work for you. See the hardware section so you can compare what will or will not work for you.

Notes to newbies: Relax, this is mostly a step-by-step guide. It is a little outdated (the last time I ran a non-minimal install was 8.04 to test) but it's mostly the same. If you get hung up anywhere or have any questions do two things: 
   1. Search google
   2. If google doesn't work for you, post your question

**Chapters**
32 bit vs. 64 bit
Hardware
Pre Installation
Installation Walk Through
Post Installation Setup (nvidia card, wireless card, lightscribe)
Ubuntu Minimal - Experienced Users only
Ubuntu 9.04 Status Report
End Notes (including notes on 9.10 and 10.04)

[SIZE="3"]**32 Bit vs. 64 Bit**[/size]
We could all get into a heated debate here on this, but I'm going to boil it down to being very simple. If you want great compatibility with software, ease of use, and want to have a very stable system and don't want to deal with crashing. Use 32 bit (x86).

If you want to try 64 bit, be prepared. Flash does not have a native 64 bit driver. Neither does Java. Nor have I gotten lightscribe working on 64 bit yet. There is no Adobe Reader plugin for 64 bit. You will run into issues, you need to be prepared to fix them. If you want a challenge, go for it. 

I am currently running a modified version of 64 bit. (minimal install + what i want) However if you want functionality and an OS that "just works", keep it 32 bit.

[SIZE="3"]**Hardware**[/SIZE]
Processor: AMD Turion X2 - TL58
Graphics Card: NVIDIA 7150M
Wireless Card: Broadcom BCM94311MCG wlan mini-PCI (rev 02) .... Now recognized as BCM4311
Memory: 4 Gb (upgraded from stock 2 Gb)
Hard Drive: 160 gb 5400 rpm
Disk Drive: CD/DVD Multi with Light Scribe (lightscribe only works with 32bit at this point)
Card Reader: Works by default
Webcam: Works by default
Microphones: Work by default
Speakers: Excellent sound, no distortion.
Media Remote: Works be default

So basically, if you have a laptop with an AMD processor, a broadcom wireless card, and an nvidia graphics card then this guide should work for you. You won't find out unless you try it, and you've got nothing to lose.

[SIZE="3"]**Pre Installation**[/size]
What do you need?
Ubuntu 8.04 Disk or 9.04 Disk
RJ-45 (Ethernet) Cable and Working High Speed Internet Connection
An Open Mind

[SIZE="3"]**Installation Walk Through**[/size]
After you get your OS disk burned, pop it in the cd drive and boot to it. When the menu comes up go ahead and Start Ubuntu.

**Temporary graphics improvement:**
*this seems to relate to 8.04 only, 9.04 goes straight to 1280x800*
Once Ubuntu loads up and you have your little desktop go to System > Administration > Screens and Graphics. Once the window loads click the box next to Model: Now, select Generic as the manufacturer, and Monitor 1024 x 768. Do this even though this isn't correct. This is just to make our lives easier for this installation. We will install the nvidia drivers later.

**Shrinking Vista**
Now, some of you may want to keep Vista on your system still. I did in the beginning just in case I was going to have some major problems with Ubuntu. This part is for you. Go to System > Administration > Partition Editor. Now right click on your Windows partition, and click resize. Enter it's new size in MB, and click resize. I shrank mine down to about 40000mb. If you'll be using Windows a lot more than Ubuntu, or are just testing Ubuntu out, don't shrink it down that much. Now that you've selected what size you want it to be, click apply. We won't bother making the other partitions for Ubuntu just yet.

**Installing Ubuntu**
Now, go ahead and double click the install icon on the desktop. The first few steps are self explanatory. Select your language, your time zone (which is actually dumb because my timezone isn't on there...). Then select your keyboard layout. Now, it's going to say &#8220;Starting up the Partitioner.&#8221; Select Manual, and go Forward. Now you should see your shrunken Vista partition and the HP Recovery partition if you kept them, and your free space. I now have two ways for you to do this.

1.     If you're just trying Ubuntu out, and didn't shrink Vista that much, do this method. Select your free space, and click &#8220;New partition&#8221;. For type of partition select logical. For new partition size just do 1000. For location select beginning. Use as swap. And click okay. Now click the rest of your free space and create another new partition. Select primary for the type, all the space left for the size, beginning for the location, and use as ext3. Now click your partition you just created, click edit, and select &#8220;/&#8221; as your mount point.

2.     For those of you who will be using Ubuntu as our main or only operating system we should do this. Go to the free space and click &#8220;New partition&#8221;. For the type select logical, for the size do 2000, for the location select beginning, and use as swap. Now click okay. Create another new partition, for the type select primary, for the size do 10000 to 20000 (this will be the operating system's partition), and use as ext3 (or if you have another preference use it). Now create another partition, for type use primary, use the rest of the available space for your size, and use as ext3. Now we need to go back and edit the partitions. For the first one make the mount point &#8220;/&#8221;, for the second one make the mount point &#8220;/home&#8221;. This keeps all your files on a separate partition so you can reformat the Ubuntu partition without fear if you completely screw something up, or want to do a fresh upgrade/install.

Now go ahead and click forward. Ubuntu is going to tell you there were no users or operating systems suitable for importing from. Go ahead and click forward again.

Now just fill out the information in front of you. And click forward again.

Now you have a summary of your settings so far. If you see something incorrect, go back and fix it. If everything is okay, click install. After the installation is finished go ahead and restart your laptop.

[SIZE="3"]**Post Installation Setup**[/size]
First, hook your laptop up to your internet connection with the RJ-45 cable.

**Unlocking All Repositories and Picking The Best Server**
Go System > Administration > Software Sources. On the first tab make sure everything is checked except for the CD. Then click the Download From" button. Click other. Click "Select Best Server." After it finds the best server for you go ahead and close it. And when it asks if you want to reload go ahead and do that.

There, you just chose the best server to download software from and updated your repositories. At this point I'm sure Ubuntu is telling you that you have updates, ignore them until you get everything setup.

**Nvidia Graphics Card**
Go System > Administration > Hardware Drivers. There should be a couple drivers there for you. I installed the older nVidia driver because it works well for me, but feel free to try the latest. Check the box by the nvidia driver of your choice (ignore the broadcom driver for now). After you give it the okay it will install your nvidia driver and ask you to reboot. Reboot then go onto the wireless card section.

**Broadcom Wireless Card**
**UPDATE**
The latest kernels have new broadcom drivers in them. To install the new drivers simply hook up your ethernet cable. Update. Reboot. Then go System > Administration > Hardware Drivers and check "Broadcom STA Wireless Driver." If you've already installed the broadcom drivers with my script simply run the uninstaller, reboot, and then follow the previous steps.

*****The following has been left here in case the STA drivers do not work for you. If you are using the STA Drivers DO NOT do the next step*****
You need to be online for this, but I have made this insanely easy for you. Simply download this package [here.](http://darkstang.com/uploads/broadcom_install.tar.bz2) Extract the contents anywhere. Then run the installer script in a terminal. (to do this you can either double click it then select run in terminal, or you can do it manually in a terminal)

The package comes with the broadcom drivers, a script to install everything automatically for you, and a script to undo what the install script did.
*****end of broadcom/ndiswrapper drivers*****

**Lightscribe**
This lightscribe support is only available for 32 bit (x86) machines. You will need both.
[Lightscribe Drivers]("http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814")
[LaCie Labeling Software]("http://www.lacie.com/products/product.htm?pid=10803")

[SIZE="3"]**Ubuntu Minimal**[/size]
If you're like me, you're very happy with Ubuntu. It runs well, but it has a lot of things you just don't care about. On top of that you just don't feel like removing all the unwanted packages. Well, thankfully, there is an Ubuntu minimal installer. You can pick this thing up from [this link.](https://help.ubuntu.com/community/Installation/MinimalCD)

What will this do for you? It guides you through a text-based installation. It is a net-based installer so you will have to be hardwired on a network for it to work. Also, this means it will be downloading everything it installs. After this, it dumps you into a command line interface. Once you hit the command line you can run the following command to give yourself a gnome environment to work in, a web browser, a couple system tools, and some graphical package managers.
```
sudo aptitude install x-window-system-core gnome-core gdm firefox synaptic xubuntu-system-tools gnome-app-install powernowd
```
Now you can install and remove any packages you want through synaptic. (as in, your hardware drivers, alsa, etc)

[SIZE="3"]**End Notes**[/size]
**Overheating?** A while back (late 2007) many people thought there were overheating issues with these laptops. I e-mailed AMD about the temperatures I was getting while my laptop was under a lot of stress and they reported that I am well within the safe operating range. 

**Notes on 9.10 - GDM, clicks and pops, some good and bad**
First off... GDM. New GDM is a pretty large step back in my opinion so I'm sticking with GDM 2.20. If you don't like the new GDM feel free to install the old GDM via synaptic. However, when you install the new GDM it's going to want to install a few other items. There are three problem children here and they are... alsa-base, alsa-utils, and linux-sound-base. So go ahead and check GDM-2.20 and tell it to install. After it checks those three items, go through and uncheck them anyway. If you don't do this you will have random pops and clicks coming out of your speakers. On the bright side, pulse-audio works wonderfully now.

Boot times have been drastically decreased, at least with the 64 bit system. From the grub menu to GDM takes 18-20 seconds. Then from there it depends on whether or not you're running compiz. Without compiz you're at your desktop almost instantly, with compiz it takes just a few more seconds. I'm quite impressed with this.

All hardware works fantastically with 9.10 as long as you aren't using Alsa for your sound. Webcam works out of the box. Wireless card and video card both work after installing the restricted drivers. I ran the net installer last night and installed all my software today.

**Notes on 10.04**
10.04 works perfectly fine after a clean network install. The biggest pain is the graphics are absolutely terrible until you get the video card driver installed, or at least it was for me. But once the nVidia driver is installed everything runs wonderfully. This will likely be the last update from me on this laptop as I will be getting a new laptop in a few months.

---

### Post by akbeancounter on 2008-08-07
In the words of the late Lester Burnham, I think you just became my personal hero.  I've been trying since Fiesty to get Ubuntu to work on my laptop, and it just wouldn't do what I wanted.  Part of it was just that the dev community had to catch up with the technology, but that Broadcom/ndiswrapper thing would never work the way everybody said it should.  [Sorry Mr. Softy, but now that I have wireless, I think it's time we went our separate ways.]

My next project is to get Ubuntu (or perhaps more accurately, GRUB) to play nice with other Linuxes; I'd like to dual-boot Ubuntu & openSUSE 11, plus have a sandbox partition for trying new releases (or eventually beta versions, once I develop the chops for it.), all sharing one /home.  I think I know what I'm doing, but it should be easier now that I don't care about preserving a Vista partition.

Thanks!

**Edit 8/7/08 19:09 EST:**
Actually, I did have one question, something you said in the "Installing Ubuntu > Shrinking Vista" section:
1) Did you resize your Vista partition from the Ubuntu installer?  I've heard elsewhere that Vista may get mad and refuse to boot.  I, for one, didn't get an install disk; I had to create a rescue disk that would reset everything (including the partition table) to factory default.  If I kept Vista, I'd like to shrink it down to ~40GB, plus a 40-50GB NTFS partition for media files.  Vista's not that friendly, though, and after a clean install, the Shrink function is only willing to go down to about 100GB (which sounds the same, except that that puts all my media on the Vista partition, so I'd have to restore all my tunes again if Vista broke.)

-- A.

---

### Post by Dark_Stang on 2008-08-08
Before I did anything I made recovery discs for my laptop. When I got my laptop the graphics card and wireless card were both fairly new and I didn't want to end up being without a computer for a while. I used the partitioner in the Ubuntu disc, which is just gparted (the gnome partition editor). And yes, if gparted doesn't do it's job properly, you may screw up your file system. This is true with any partitioner. However, now my laptop is running only Ubuntu because it works so well.

The partitioner built into vista is horrible, just use gparted. Also, you should always backup your data before repartitioning. You never know what may happen. The partitioner may fail, the power may go out, your motherboard might decide to fail. And if anything interrupts the process, chances are you'll be re-loading everything onto the hard drive, or sending your drive off for data recovery and you'll be out $500+.

---

### Post by akbeancounter on 2008-08-08
> **Dark_Stang said:**
> if gparted doesn't do it's job properly, you may screw up your file system. This is true with any partitioner. 

I know that, perhaps a little too well.  Still, installers and partitioners are a heckuva lot more friendly now than they were even five years ago.  I remember trying to install Red Hat 6.0 back in the day, and when it finally worked on the fourth try, my desktop appeared in 320x240 or some insanely tiny resolution.  I was basically clicking blindly and trying every keyboard shortcut I could think of to fix it, but to no avail.  Good times.

> The partitioner built into vista is horrible, just use gparted. 
The Vista partitioner works okay-ish.  It does what it claims to do, which isn't saying much.  I just take a offense at a partitioner that tells me *how much* of the free space it feels like releasing.  What I'd heard elsewhere, though, was that Vista would often fail if you ever dared to use another partitioner.  Now that I know it's relatively safe to corner Vista into a 30-40GB partition, I might hold onto it and quad-boot Vista, Ubuntu, SuSE, and the sandbox.

-- A.
* See also: MIT OpenCourseWare, [http://ocw.mit.edu/](http://ocw.mit.edu/)

---

### Post by Dark_Stang on 2008-08-09
> **akbeancounter said:**
> What I'd heard elsewhere, though, was that Vista would often fail if you ever dared to use another partitioner.  Now that I know it's relatively safe to corner Vista into a 30-40GB partition, I might hold onto it and quad-boot Vista, Ubuntu, SuSE, and the sandbox
That can't be true. I use a partitioner on vista machines several times a week at work and have never had an issue. For working with hard drives I normally use Acronis and Partition Magic at work, as these are the approved company tools. At home I always use gparted and have yet to need to clone a drive. Hopefully I didn't jinx myself there.

Side note: Red Hat 6, wow. In '99 I was still in grade school and was just beginning to play with qbasic.

---

### Post by feelinggood on 2008-10-09
Thank you so much for this thread, I am finally loaded up and loving it.  Compiz-fusion is loaded up and it is awesome.  Thanks again for this post.  Steve:popcorn:

---

### Post by sergiom99 on 2008-10-16
dark_stang did you try this??
[http://ubuntuforums.org/showthread.php?t=880218&highlight=broadcom+sta](http://ubuntuforums.org/showthread.php?t=880218&highlight=broadcom+sta)

---

### Post by Dark_Stang on 2008-10-19
> **sergiom99 said:**
> dark_stang did you try this??
[http://ubuntuforums.org/showthread.php?t=880218&highlight=broadcom+sta](http://ubuntuforums.org/showthread.php?t=880218&highlight=broadcom+sta)
I have not, I will definitely be looking into this one. If this works without ndiswrapper maybe I can start running airsnort/aircrack and getting some real work done...

Edit: Testing it out now. I will be playing with this over the next week or two to make sure it's solid. At this point it seems to be working fine with Open and WEP encrypted networks. Tuesday and Thursday I will be at school so I'll make sure it works with hidden networks and the VPN. I'll also test out WPA encryption, and of course... aircrack and airsnort...

---

### Post by sergiom99 on 2008-10-19
how can I be sure that I am using the new driver and not your old ndiswrapper script??
B/c in the restricted driver manager it appears unchecked. I check it an reboot and still unchecked. Any way to tell for sure?

 [[IMG]http://img169.imagevenue.com/loc1094/th_59040_snap7_122_1094lo.jpg[/IMG]](http://img169.imagevenue.com/img.php?image=59040_snap7_122_1094lo.jpg)

---

### Post by Dark_Stang on 2008-10-20
Did you run the uninstaller? If you run that it will get rid of ndiswrapper, the entries for startup, and the scripts for startup so there is no chance of it being there. That's all I did.

---

### Post by sergiom99 on 2008-10-20
yes I did, and it didn't show any errors, so I assume its OK. but since the driver always show disabled in the drivers manager I want to make sure i am testing it.

---

### Post by random turnip on 2008-10-20
Is this likely to work on a HP Pavillion as i have had the exact same problems (screen res and wireless not working properly).

Actually im gonna try this and I'll post back telling you the results.

[EDIT]
The graphics card works, but im having problem with installing the driver for the Wireless card.

---

### Post by Dark_Stang on 2008-10-20
> **sergiom99 said:**
> yes I did, and it didn't show any errors, so I assume its OK. but since the driver always show disabled in the drivers manager I want to make sure i am testing it.
Huh... So you've got the latest kernel and uninstalled and you still cant get it? You ran the uninstaller as root, correct? Here's a screenshot of my restricted drivers manager window.
[img]http://darkstang.com/uploads/broadcom_sta.png[/img]
Go System > Administration > Services and make sure "wifiFix.sh" isn't in there still. If it is let me know.


> **random turnip said:**
> Is this likely to work on a HP Pavillion as i have had the exact same problems (screen res and wireless not working properly).

Actually im gonna try this and I'll post back telling you the results.

[EDIT]
The graphics card works, but im having problem with installing the driver for the Wireless card.

What model is your HP?
Also, post the output of this for me...
```
lspci | grep -i 'wlan'
```
The HP laptops that came out after mine were equipped with atheros cards in them. So if you have one of those then these broadcom drivers will not work for you.

---

### Post by sergiom99 on 2008-10-20
I use Kubuntu, so the screens are different. but its unchecked anyway.
And I ran it with sudo. do I need to change to "full" root?

---

### Post by Dark_Stang on 2008-10-20
sudo should have worked for you... Is the wireless card still working? Is ndiswrapper still installed on the machine?

---

### Post by sergiom99 on 2008-10-20
yes, sudo worked.
wifi card never stopped working, but i assume i'm now using STA drivers b/c my interfase changed from wlan0 to eth1.
and no ndiswrapper stuff shows as installed in Adept.

so maybe i am using the new driver. I just wanted to be sure to report it as succesful.
Thanks dark_stang!

---

### Post by cessnasoarer172 on 2008-10-22
I have installed the wireless as you said on my computer, but I have not been able to get it to work, do you know how it is possible to make it work in Kubuntu 8.10, which is what I have?

---

### Post by Dark_Stang on 2008-10-22
> **cessnasoarer172 said:**
> I have installed the wireless as you said on my computer, but I have not been able to get it to work, do you know how it is possible to make it work in Kubuntu 8.10, which is what I have?

> **Dark_Stang said:**
> Notes: This guide is designed for my laptop and for Ubuntu 8.04LTS. 8.10 **DOES NOT WORK** on my laptop.

...

---

### Post by APer3Caper on 2008-10-30
Since Ubuntu 8.10 Intrepid Ibex was officially released today:guitar:, how does it work on the dv6636nr? I installed the RC last week from Hardy and it made my Internet wonky and booting up sometimes failed:(. I reinstalled Hardy and now I fear that installing this will cause things to go awry again. What do you guys think?

---

### Post by Dark_Stang on 2008-10-30
Unless a lot has changed from the RC it isn't going to work smoothly on a dv6636nr. When I get some free time I will download the minimal install iso and see how that goes. However the standard install disk is a definate "hell no" for right now.

On the bright side broadcom's new drivers work out great. I will be editing the howto to include how to get the installed properly. I will leave the ndiswrapper stuff up as well just in case.

---

### Post by Dark_Stang on 2009-03-05
Updated this guide with a few notes on how I feel about 9.04, Ubuntu minimal, and just cleaned up a little.

---

### Post by Dark_Stang on 2009-05-01
Updated the guide again. 9.04 works great now! I'm currently listening to my music collection (sound works), watching glx gears run smoothly (3d video works), and surfing the web wirelessly (networking works). Now all I have to do is pass all my final exams, turn in my final papers, and pull in a couple web design contracts for some extra summer cash.

---

### Post by APer3Caper on 2009-05-05
I need some help. I installed Ubuntu 9.04 on my DV6636NR as described in the guide. The install went well and I rebooted. As the computer began to boot up after I selected Ubuntu from the GRUB menu, a cryptic error message appeared on the screen. It read:

Boot from (hd0,3) ext4 94e74c61-38cc-4220-a3eb-6baed6869a06
Starting up...
[     23.636028] ata5: SRST failed (errno=-16)
[     33.648028] ata5: SRST failed (errno=-16)
[     68.692028] ata5: SRST failed (errno=-16)

After that message pops up on the screen, the regular boot process will continue and I can login. This problem is more of a nuisance than anything but adds a good 30 seconds onto the boot time. Any ideas why this is happening and how can I fix it? The optical drive in my laptop recently went bad (not sure what the problem is yet). Could that be the cause of this? Any help would be greatly appreciated. Thank you.

---

### Post by Dark_Stang on 2009-05-06
> **APer3Caper said:**
> I need some help. I installed Ubuntu 9.04 on my DV6636NR as described in the guide. The install went well and I rebooted. As the computer began to boot up after I selected Ubuntu from the GRUB menu, a cryptic error message appeared on the screen. It read:

Boot from (hd0,3) ext4 94e74c61-38cc-4220-a3eb-6baed6869a06
Starting up...
[     23.636028] ata5: SRST failed (errno=-16)
[     33.648028] ata5: SRST failed (errno=-16)
[     68.692028] ata5: SRST failed (errno=-16)

After that message pops up on the screen, the regular boot process will continue and I can login. This problem is more of a nuisance than anything but adds a good 30 seconds onto the boot time. Any ideas why this is happening and how can I fix it? The optical drive in my laptop recently went bad (not sure what the problem is yet). Could that be the cause of this? Any help would be greatly appreciated. Thank you.
After researching the issue it looks like the problem is related to one of three things.
1. Software glitch with certain mobo or mobo+hard drive configurations.
2. Software glitch with certain optical drives and the optical drives are not recognized in Linux because of it.
3. Failing drives.

Can you still boot from a disc? If so, can you boot from CDs and DVDs or just CDs? If you can boot from both CDs and DVDs, but you can't access the drive in Linux you've probably got a software problem. If you know for sure your drive is bad, that's probably what's causing it.

---

### Post by APer3Caper on 2009-05-06
> **Dark_Stang said:**
> After researching the issue it looks like the problem is related to one of three things.
1. Software glitch with certain mobo or mobo+hard drive configurations.
2. Software glitch with certain optical drives and the optical drives are not recognized in Linux because of it.
3. Failing drives.

Can you still boot from a disc? If so, can you boot from CDs and DVDs or just CDs? If you can boot from both CDs and DVDs, but you can't access the drive in Linux you've probably got a software problem. If you know for sure your drive is bad, that's probably what's causing it.

Unfortunately, my drive is bad. It's been this way since October. It doesn't show up anywhere, Windows or Ubuntu. Occasionally, it'll come back to life for a few hours but then it goes away again. I got Ubuntu installed by booting off a USB stick. I just had a thought. Would the Netbook Remix fix the problem? A lot of netbooks don't have optical drives. Anyway, thanks for the help.

---

### Post by Dark_Stang on 2009-05-06
> **APer3Caper said:**
> Unfortunately, my drive is bad. It's been this way since October. It doesn't show up anywhere, Windows or Ubuntu. Occasionally, it'll come back to life for a few hours but then it goes away again. I got Ubuntu installed by booting off a USB stick. I just had a thought. Would the Netbook Remix fix the problem? A lot of netbooks don't have optical drives. Anyway, thanks for the help.
The netbook remix is very stripped down, I wouldn't recommend it for anything other than a netbook. I doubt that would solve the issue anyway. You could try commenting out the line for the optical drive in /etc/fstab.

---

### Post by APer3Caper on 2009-05-06
> **Dark_Stang said:**
> The netbook remix is very stripped down, I wouldn't recommend it for anything other than a netbook. I doubt that would solve the issue anyway. You could try commenting out the line for the optical drive in /etc/fstab.

Thank you for all the help you have been providing me. I must ask though, how would I got about commenting out the line for the optical drive? I opened up /etc/fstab and this is what I see:
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=94e74c61-38cc-4220-a3eb-6baed6869a06 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=24daa829-2ce1-4ca6-801d-b3c1221cb878 none            swap    sw              0       0
```

Once again, thank you so much for the help.

---

### Post by Dark_Stang on 2009-05-06
Heh, well... If your optical drive was in there you would see a line like this...
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
Obviously, your optical drive isn't in your fstab, so that idea is gone. This is a little beyond me. You may want to get with your local Linux Users Group (if you have one) for some extra help or contact a forum admin to see if they know something.

---

### Post by APer3Caper on 2009-05-07
> **Dark_Stang said:**
> Heh, well... If your optical drive was in there you would see a line like this...
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
Obviously, your optical drive isn't in your fstab, so that idea is gone. This is a little beyond me. You may want to get with your local Linux Users Group (if you have one) for some extra help or contact a forum admin to see if they know something.

Well thank you for your help anyway. I'll be sure to check around other places to see if anyone can assist me. You and your guide have been quite helpful getting me up and running with Ubuntu.

---

### Post by avngrboy on 2009-05-17
Thanks Dark Stang for the write up. it helped me out. THANKS:D

---

### Post by sergiom99 on 2009-05-23
Hi Dark_Stang, great to see it worked out fine.
I upgraded to Kubuntu32 JJ (fresh install) myself and most things worked out, but when I started laptop on battery, the weirdest thing happened:
It stopped at a black screen after the GRUB and then I realized that if I pressed a key it kept moving on, so I pressed n times the space key and sort of "manual started" it, like the antique planes that you have to crank em up to get the engine started.
Anyway, the most bizarre thing I've seen.

Any ideas?

---

### Post by Dark_Stang on 2009-05-23
Wow sergiom. I did not have that problem at all starting with Ubuntu Minimal and working my way up. But if I had to guess I'd have to say it might have something to do with acpi or apm. I don't have apmd installed, just acpi and acpid. Check to see if you have apmd installed. If you do I'd try removing it and rebooting to see if it happens again.

---

### Post by sergiom99 on 2009-05-24
and what might be the drawback of removing apmd?
Kubuntu-desktop has dependency on it. I cannot remove it.

---

### Post by Dark_Stang on 2009-05-25
> **sergiom99 said:**
> and what might be the drawback of removing apmd?
Kubuntu-desktop has dependency on it. I cannot remove it.
You can remove it. As far as I know, our laptops don't need it. Kubuntu-desktop is just a blanket package that includes it. Uninstalling apmd doesn't remove Kubuntu or KDE or any of your desktop environment.

For example: Because I start with Ubuntu Minimal and just install only the packages I want, I don't have the "Ubuntu Desktop" blanket package installed. Actually, if I were to install it it would be installing about 200 packages that I don't have, don't want, and don't need.

---

### Post by sergiom99 on 2009-05-28
Here are my dmesg and syslog when I booted on battery to see if they help someone figure it out.
Thanks!

---

### Post by sergiom99 on 2009-06-25
got a work around by fixing the DSDT. Now it runs cooler and quiet.
Take a look at [1] for an awesome how-to to fix buggy DSDTs
Good luck- Sergio

[1] [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by Dark_Stang on 2009-09-16
Attention user: 2optimize

I tried to reply back to your PM but when I did I received a message stating that you weren't allowed to receive PM's or you chose not to. Anyway, we can try to work your problem out in here or through e-mail if you would prefer. Contact me at [email]DarkStang@gmail.com[/email] or just reply to this message if you see it.

---

### Post by Dark_Stang on 2009-10-28
Just booted and installed 9.10. Did a network install from the minimal iso and I'm reinstalling all my extra software now. Seems to be running pretty smooth up to this point.

There was an issue with a few files causing some odd audio pops. I've noted this in the first post. Everything else seems fine. Hibernate and Suspend work without anything extra. Webcam and microphone work out of the box. The quickplay buttons still work fine.

---

