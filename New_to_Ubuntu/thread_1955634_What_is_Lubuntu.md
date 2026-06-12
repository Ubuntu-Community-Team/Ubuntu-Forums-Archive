---
title: "What is Lubuntu?"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by JXR on 2012-04-09
For three weeks I’ve been unable to successfully install Unbutu (Unbutu 10.04 is installed but the keyboard/keypad on the Dell Inspiron 2650 are disabled; Windows XP is also installed [dual boot] but multiple install attempts resulting in multiple Linux swap partitions have rendered it fairly limp) on the laptop. From the response I am getting a 30+ GB / 256 MB is too little to run Unbutu.
   
  So I’m taking some of the advice I was given and am trying to install Lubuntu from a LiveCD.
   
  If I attempt to run it with no F6 options enabled I get a blinking cursor on a black screen.
  If I attempt to run it with F6/acpi off the Lubuntu blue install screen (with white lettering and the Ubuntu dots)  I get a black screen terminal window allowing me to enter command lines in sudo.
   
  Is Lubuntu a graphical interface OS or just a command line interface?

---

### Post by Frogs Hair on 2012-04-09
It reads like you may be having problems with your disks . Try burning them at a slow speed and you can also run a check sum . [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Lubuntu is not a console/ terminal  environment see LXDE . [http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce](http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce)

---

### Post by Cheesemill on 2012-04-10
256MF of RAM may be too little memory to run the graphical installer.
You might be better off trying with the Alternate install CD:
[http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/)

---

### Post by JXR on 2012-04-10
I doubt 256 MB RAM is too little to mount the graphical interface, since it mounted Ubuntu OK. In fact, I am sending this through Ubuntu / Firefox running an external (USB) keyboard and mouse.  

I recopied onto another CD at 16x speed (InfraRecorder) and the install proceeds the same way:
.     - Boot without any Fkey change and I just get a flashing cursor
.     - Boot with F6 NOACPI and the Lubuntu screen comes up (blinking dots and all) but eventually returns me to a black screen that reads:

Welcome to Ubuntu 11.10...
To run a command as administrator...
...
ubuntu@ubuntu:~$

I believe the problem lies in the machinations my numerous attempts to load  Ubuntu has caused. It looks like a real mess! I've attached a GParted screenshot of the partition configuration. How can I get rid of unused partitions in such way as to make them available to Lubuntu (leaving on Windows XP and Ubuntu 10.04 at least until I can mount Lubuntu).

---

### Post by euphoric_anomaly on 2012-04-10
I also used InfraRecorder to burn the Ubuntu 10.04LTS iso to a cd-rw. I set my write speed @ 4x, yes it takes awhile, but it works wonders.

---

### Post by JXR on 2012-04-10
Before copying it at 4x did Lubuntu mount the way I described?

---

### Post by Dumpy Dumpster on 2012-04-10
I have installed Lubuntu 10.04 on a Dell L400 PIII/800Mhz/256Mgb and it runs like a dream!  I recommend it in full, but _only_ as a single OS, as I have no experience of dual booting with XP on a low powered machine. Just burn your install CD at the lowest possible speed and wipe your disc clean with GParted before installation.  You will not miss XP!
Good Luck!

---

### Post by snowpine on 2012-04-10
If you are already running Ubuntu then there is no need to reinstall. 

```
sudo apt-get install lubuntu-desktop
```

To clean up Gnome: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

---

### Post by Rodney9 on 2012-04-10
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by JXR on 2012-04-10
Snowpine

I'm running the sudo you recommended!  Later I'll ask you what happened, but (for someone who doesn't know what is happening) it looks promising!) 

1) I'm at the point where it's asking me to specify the Default display manager. Do I want to specify "gdm" or "lxdm"?  (Will I be aked any questions after this...that you need to answer?)

2) Aftr this you've suggested I clean up Gnome. What does that mean? (Is this what I need to do to clean up the disk partitioning?)

---

### Post by snowpine on 2012-04-10
> **JXR said:**
> Snowpine

I'm running the sudo you recommended!  Later I'll ask you what happened, but (for someone who doesn't know what is happening) it looks promising!) 

1) I'm at the point where it's asking me to specify the Default display manager. Do I want to specify "gdm" or "lxdm"?  (Will I be aked any questions after this...that you need to answer?)

2) Aftr this you've suggested I clean up Gnome. What does that mean? (Is this what I need to do to clean up the disk partitioning?)

1) I have never used lxdm so I don't know much about it; gdm has always worked fine for my needs.

2) The tutorial I linked to on the psychocats website will remove the Gnome environment and leave you with "pure" LXDE. This step is not necessary, but it will free up some hard drive space and make your menus less cluttered.

---

### Post by Jerry N on 2012-04-10
> **JXR said:**
> I doubt 256 MB RAM is too little to mount the graphical interface, since it mounted Ubuntu OK. In fact, I am sending this through Ubuntu / Firefox running an external (USB) keyboard and mouse.  

I recopied onto another CD at 16x speed (InfraRecorder) and the install proceeds the same way:
.     - Boot without any Fkey change and I just get a flashing cursor
.     - Boot with F6 NOACPI and the Lubuntu screen comes up (blinking dots and all) but eventually returns me to a black screen that reads:

Welcome to Ubuntu 11.10...
To run a command as administrator...
...
ubuntu@ubuntu:~$

I believe the problem lies in the machinations my numerous attempts to load  Ubuntu has caused. It looks like a real mess! I've attached a GParted screenshot of the partition configuration. How can I get rid of unused partitions in such way as to make them available to Lubuntu (leaving on Windows XP and Ubuntu 10.04 at least until I can mount Lubuntu).

You don't have nearly enough space left in your NTFS partition to run Windows and you don't have nearly enough space left in your EXT4 partition to run Ubuntu or Lubuntu.  You might try deleting every partition except sda1 and sda2.  If you want to run Windows, use gparted to expand the NTFS partition to about 20gb (you could also try cleaning out some stuff from Windows.  Like temporary files).  Then make about a 1gb swap partition and partition the rest as EXT4.  Use manual partitioning for the install, don't let it try to "install beside Windows".

Jerry

---

### Post by cortman on 2012-04-10
> **snowpine said:**
> 1) I have never used lxdm so I don't know much about it; gdm has always worked fine for my needs.

2) The tutorial I linked to on the psychocats website will remove the Gnome environment and leave you with "pure" LXDE. This step is not necessary, but it will free up some hard drive space and make your menus less cluttered.

You want to select lxdm; if you uninstall ubuntu-desktop you'll lose your GDM. No great loss though.
I'm running the LXDE spin of Fedora 16 on my netbook, and am really enjoying the speed. (to OP, that's the same as Lubuntu, just a tad different).

---

### Post by Alphamonkey on 2012-04-10
I'm not familiar with using lubuntu but you want to use LXDM. I found this typing lxdm into google if you want to know why " *LXDM* is the lightweight display manager aimed  to replace gdm in LXDE distros. The UI is implemented with GTK+. It is  still in early stages of development." GDM on the other hand is for gnome. "*GDM* - The *GNOME Display Manager*. *GDM* is the *GNOME Display Manager*, a graphical login program."

---

### Post by Peripheral Visionary on 2012-04-10
> **JXR said:**
> ... you've suggested I clean up Gnome. What does that mean? (Is this what I need to do to clean up the disk partitioning?)

Click on the link Snowpine provided. It isn't about your partitions at all, but removing the Gnome **desktop environment**. Gnome is a heavyweight that will slow down that old computer. Lubuntu is built for the ultralight [LXDE]("http://lxde.org") desktop environment.

---

### Post by snowpine on 2012-04-10
> **JXR said:**
> I believe the problem lies in the machinations my numerous attempts to load  Ubuntu has caused. It looks like a real mess! I've attached a GParted screenshot of the partition configuration. How can I get rid of unused partitions in such way as to make them available to Lubuntu (leaving on Windows XP and Ubuntu 10.04 at least until I can mount Lubuntu).

I overlooked your Gparted screenshot in my original answer. You will need to clean up your partitions before you do anything, as they are quite full. :(

An Ubuntu/Lubuntu live CD running GParted will allow you to resize partitions. 15gb is the recommended minimum for Ubuntu according to: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by JXR on 2012-04-10
Uh oh...I went with gdm...

And I do want to uninstall Ubuntu (I don't know why I want to, except that I want a usable dual boot computer...and somewhere along the line I hope the Dell keyboard will work in Linux...)

So, what should I do now?
.     a) run 
sudo apt-get install lubuntu-desktopagain?
.     b) try deleting every partition except sda1 and sda2.  If you want to run  Windows, use gparted to expand the NTFS partition to about 20gb (you  could also try cleaning out some stuff from Windows.  Like temporary  files).  Then make about a 1gb swap partition and partition the rest as  EXT4.  Use manual partitioning for the install, don't let it try to  "install beside Windows"?
.     c)  linked to on the psychocats website will remove the Gnome environment  and leave you with "pure" LXDE...to  free up some hard drive space and make your menus less cluttered. (why do I want my menus less cluttered? The more things in the menu, the more options, right?)?

---

### Post by Alphamonkey on 2012-04-10
> **JXR said:**
> Uh oh...I went with gdm...

And I do want to uninstall Ubuntu (I don't know why I want to, except that I want a usable dual boot computer...and somewhere along the line I hope the Dell keyboard will work in Linux...)




I am not quite sure what you mean when you say that you want to uninstall ubuntu? Do you actually want to remove the entire ubuntu install and start fresh or do you just want it to run the lightweight desktop environment offered in Lubuntu? If you want to do a reinstall just burn a disk and it should come up with replace existing installation or upgrade (upgrade if you want to keep personal files). If you just want the LXDE then i believe this command should help. 

```
$ sudo dpkg-reconfigure gdm
```

This website describes changing your default display manager.

[http://linuxandfriends.com/2008/09/06/change-default-display-manager-ubuntu-linux/](http://linuxandfriends.com/2008/09/06/change-default-display-manager-ubuntu-linux/)

---

### Post by snowpine on 2012-04-10
Log out, and now from your login screen, you should be able to choose Sessions, LXDE (Lubuntu). :)

---

### Post by JXR on 2012-04-10
WOW! I'm running Lubuntu!!!

Which brings me back to my original question: "What is Lubuntu?"

I assumed--since everyone told me I couldn't run Ubuntu with my RAM/dis configuration--that it was some sort of "L"ightweight Ubuntu and that after I installed it I would find that I had less available (programs) and much more available space, and therefore it would run faster... And I hoped I would finally be able to use my Dell Inspiron 2650 keyboard--(but that seems impossible--every suggestion has done nothing to relieve this problem). But the interface looks the same and all the same programs are available.

So...How is Lubuntu different from Ubuntu?   Since it seems no smaller, is it just better written code?

One thing it did do, that Ubuntu didn't. It immediately informed me "This computer has only 116.1 Mb disk space available." So rather than gaining space, it seems I lost space.  (GParted reports exactly the same partitioning schema - see original attachment) and the Disk Usage Analyser reports as attached.

When I start up I am given the following options (none of which I understand, except the top one is LUmbutu and Windows is Windows.

Ubuntu with Linux 2.6.32-33-generic
Ubuntu with Linux 2.6.32-33-generic (recovery mode)
Memory test (memtesst 86+)
Memory test (memtesst 86+) serial console 115200 
Windows...
Ubuntu with Linux 2.6.35-32-generic   (on dev/sda5)
Ubuntu with Linux 2.6.35-32-generic (recovery mode)
Ubuntu with Linux 2.6.35-40-generic    (on dev/sda5)
 Ubuntu with Linux 2.6.35-40-generic (recovery mode)
Ubuntu with Linux 2.6.35-33-generic     (on dev/sda5)
 Ubuntu with Linux 2.6.35-33-generic (recovery mode)

It seems something needs to go. Isn't there some sort of generic program that will clean things up?

---

### Post by snowpine on 2012-04-10
LXDE is a "desktop environment" (like Unity/Gnome). It appears the way you have things set up, you can switch back and forth between LXDE and Unity, depending on your mood that day.

If you want to remove Unity and have LXDE only then see here: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

LXDE is only a desktop environment or "skin." If your keyboard doesn't work in Unity then it probably won't work in LXDE either, I suggest starting a new thread for that problem with a descriptive title. :)

As for the disk space problem, I recommend using Gparted (from a live cd) to allocate at least 15gb for Ubuntu (you only have 2.4gb, too small). Back up all data before proceeding in case anything goes wrong.

---

### Post by JXR on 2012-04-10
While you were writing your reply I ran (I'll spare you the whole line) the 
**Remove Ubuntu**
Paste this command into [the terminal]("http://www.psychocats.net/ubuntu/terminal"): [the one that applies to Ubuntu 11.04]

It doesn't seem things went well.
I pasted it in and IMMEDIATELY got the following:

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package appmenu-gtk[/B]

Rechecking GParted everything seemed the same.
Ran the command again with the same result. (Am I right to assume nothing was deleted.)

Then I went to the page specific to Ubuntu 10.10 (since at some point I was trying to upgrade to this version in order to solve the keyboard problem) pasted its command into the Terminal and got the response:

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package baobab is not installed, so not removed
E: Couldn't find package brasero-cdrkit

[/B]So, now, not only do I seem to have multiple copies of Ubuntu installed and taking up disk space, I also seem not to be able to delete any files.

What now?

---

### Post by Jerry N on 2012-04-10
> **snowpine said:**
> As for the disk space problem, I recommend using Gparted (from a live cd) to allocate at least 15gb for Ubuntu (you only have 2.4gb, too small). Back up all data before proceeding in case anything goes wrong.

If the OP allocates 15gb for Ubuntu, there won't be enough space left for XP on that 30gb drive unless the space usage of XP is drastically reduced first.

---

### Post by snowpine on 2012-04-10
You are confusing two different solutions for two different problems.

Installing lubuntu-desktop is task 1.

Fixing your partitions using Gparted is task 2.

Let's worry about task 1 for the moment. You say you have installed lubuntu; did you do so by a) installing lubuntu-desktop in your existing ubuntu, or b) installing lubuntu on its own partition using a lubuntu cd?

---

### Post by snowpine on 2012-04-10
> **Jerry N said:**
> If the OP allocates 15gb for Ubuntu, there won't be enough space left for XP on that 30gb drive unless the space usage of XP is drastically reduced first.

I agree.

Fortunately storage is very cheap. A $99 replacement hard drive would give plenty of room for both Windows and Ubuntu. :)

---

### Post by JXR on 2012-04-10
I tried to install Lubuntu by installing it from the CD (multiple CDs actually)--with odd results (please see previous posts on this thread).

It was suggested I get to Lubuntu by issuing the command (within Ubuntu/Terminal)
sudo apt-get install lubuntu-desktop
I thought this was a way around the LiveCD Lubuntu installations that were not working. Now I wonder if this amounted to  " installing lubuntu-desktop in your existing ubuntu"

...which (if this means I have to keep a lot of useless luggage) is not what I wanted since it seemed I was once able to run Ubuntu and XP on this computer and was told to install Lubuntu because it would work better than Ubuntu (on this computer).   And...it does seem a bit faster...and by the way, it seems I CAN use the keyboard in Lubuntu.

(Yes I can trash a perfectly good harddisk--and XP in the process--or use an external harddisk which defeats the purpose of having laptop computer--I just want a clean Lubuntu [ install with the ability to get into XP to learn what the advantages of a dual boot are and get rid of all the baggage (disk partitions, etc.) that my repeated attempts to install Ubuntu caused.)

So what do I NOW need to do to solve Task #1: Installing lubuntu-desktop?

---

### Post by snowpine on 2012-04-10
If you have installed Lubuntu separate from Ubuntu then you can ignore the Psycocats tutorial; it does not apply to your situation. 

Am I correct that you now have a working fresh install of Lubuntu? (except for the keyboard and low disk space issues)

---

### Post by JXR on 2012-04-10
The good news:
.     -When I boot and choose the top option, Lubuntu comes up.

.     -The keyboard works (Yay!!); the touchpad works (I could care less. People who use touchpads are gluttons for punishment.)

The bad news:
.     - GParted indicates that a ton of space on the harddisk is devoted to Linux-swap and other Linux-related activities (I suspect it has to do with all my previous Linux mount attempts.)

.     - When Lubuntu comes up it complains that there is very little space left on the harddisk, (This complaint never happened when I booted off Ubuntu, leading me to believe that there is a ton of useless stuff on the harddisk.)

---

### Post by CoDeHacKer on 2012-04-10
if it was my machine, I'd boot into winxp and fix that partition, then I would boot to the cd that worked partition and format the rest of the drive, and do a fresh install of the one that worked.  

I wouldn't want all those partitions on a small drive that I couldn't use.

---

### Post by mastablasta on 2012-04-11
or simply launch live CD, delete all linux partitions and start over from the start. fresh install on empty disk space.
 
use alternate Lubuntu CD to install it, because the liveCD has a bug that causes crashes on install with less than 256Mb RAM. alternate (text based installer) should work fine.
with only lubuntu i think you could get away with 8-10GB, but you will have to save data to XP part of disk.
 
another option for old maschines that is also very nice and fast is Bodhi linux (based on Ubuntu, but uses Enlightenment desktop environment).
 
LXDE is lighter because it is missing some features that Gnome and KDE have when rendering windows.

---

### Post by ld114 on 2012-04-11
Mmm you seem to have got in a bit of a muddle, so in your position I would stop and take stock before doing anything else. 

Your goal is to have XP and Lubuntu running, so first boot up a live cd and use gparted to clear out all the linux and linux swap partitions on your hard disk. Select each partition in turn and then delete it. This will leave only the partitions which are used for windows XP.

Then reboot your machine, and XP should come up. Now run the Lubuntu alternate installer (it is often the case that the graphic installers won't work when the finished installation will). Lubuntu is a "lighter" version of Ubuntu with the LXDE desktop (it sounds like you might have installed the lighter version of ubuntu but with the gnome desktop, so not so light in the end).

You should now end up with XP and Lubuntu on your system. There should be only two partitions for Lubuntu if you use the default options - the ext4 partition with Lubuntu and a swap partition. 

Lubuntu should be a good system for you.

---

### Post by mastablasta on 2012-04-11
> **ld114 said:**
>  
Then reboot your machine, and XP should come up. Now run the Lubuntu alternate installer (it is often the case that the graphic installers won't work when the finished installation will). Lubuntu is a "lighter" version of Ubuntu with the LXDE desktop (it sounds like you might have installed the lighter version of ubuntu but with the gnome desktop, so not so light in the end).
 .
 
no it won't! because Grub is still there. to have windows XP boot normall one would need to use windows XP install disk, go to repair console and restore the master boot record using fixmbr command in console.

---

### Post by snowpine on 2012-04-11
> **JXR said:**
> The good news:
.     -When I boot and choose the top option, Lubuntu comes up.

.     -The keyboard works (Yay!!); the touchpad works (I could care less. People who use touchpads are gluttons for punishment.)

The bad news:
.     - GParted indicates that a ton of space on the harddisk is devoted to Linux-swap and other Linux-related activities (I suspect it has to do with all my previous Linux mount attempts.)

.     - When Lubuntu comes up it complains that there is very little space left on the harddisk, (This complaint never happened when I booted off Ubuntu, leading me to believe that there is a ton of useless stuff on the harddisk.)


Great! Now here's what I recommend you do next:

1. Get a **pencil and paper**. (In Lubuntu) launch Gparted and examine your current partitions. Figure out which partitions you want to keep and write down the details on your paper. (Maybe draw a little sketch too.) It sounds to me like you want to keep: Dell utility /dev/sda1, Windows /dev/sda2, the extended partition /dev/sda3, your Linux root partition (it will show a key icon and mount point /), your active swap partition (also with a key icon). Write down the names of the partitions you want to keep, and the partitions you want to get rid of.

2. BACK UP all data you want to keep in Windows and Linux (or skip this step, but at your own risk).

3. Boot from a Linux Live CD and use Gparted to achieve the partition scheme you wrote down on your paper. Be patient, it will take a while to resize.

(Optional: I think you really should clean up some space in your Windows partition; Windows does not run well when it is almost full... but that's irrelevant to your Lubuntu experience.)

---

### Post by ld114 on 2012-04-11
Oh yes grub. Quite right. The windows boot option should still be in the grub list all the same if you want to be sure XP is still working.

However if you now have Lubuntu running ok, then Snowpine's advice about backing up and writing all the partition info down is sound!

It's still not clear which desktop you have running (Gnome or LXDE) so you may have to reinstall Lubuntu with LXDE at some point for standard Lubuntu.

---

### Post by JXR on 2012-04-11
Good morning all. Now the laptop keyboards not working again (drat!) but  at least I'm getting somewhere... (I'll switch back and forth between  keyboards and report when the other comes on--maybe someone will have an  idea why.)

> **snowpine said:**
> 

1. Get a **pencil and paper**. (In Lubuntu) launch Gparted and examine your current partitions. Figure out which partitions you want to keep and write down the details on your paper. (Maybe draw a little sketch too.) It sounds to me like you want to keep: Dell utility /dev/sda1, Windows /dev/sda2, the extended partition /dev/sda3, your Linux root partition (it will show a key icon and mount point /), your active swap partition (also with a key icon). Write down the names of the partitions you want to keep, and the partitions you want to get rid of.

_.         I like the paper/pencil option. I also like getting to know GParted. _

2. BACK UP all data you want to keep in Windows and Linux (or skip this step, but at your own risk).

_.         This is not an issue. I backed up everything (and then deleted a slew of it) before venturing into Linux and since the Ubuntu 10.04; 10.10; 10.11; Lubuntu adventure have done nothing productive by way of generating files. _

3. Boot from a Linux Live CD and use Gparted to achieve the partition scheme you wrote down on your paper. Be patient, it will take a while to resize.

_.         OK   I did try before (two weeks ago, I think) to repartition my drive using GParted (an extended partition was suggested) but found that most of my options were greyed out in GParted (which was a drag considering I needed to use some of them [e.g. unmount] according to the manual). So if I encounter this again I suspect my next post will consist of a list of partitions followed by the (right click) available menu options._

(Optional: I think you really should clean up some space in your Windows partition; Windows does not run well when it is almost full... but that's irrelevant to your Lubuntu experience.)

_.            I would like to clean up space in the Windows partition. It  NOW complains that I only have 700 Mb available, and shows an E drive  with no space used and no space available._



onward...

---

### Post by JXR on 2012-04-11
Bad news (I think)

(per the GParted screenshot posted early in this thread)I followed your directions: 

The partitions I wanted to keep were sda1, sda2, and sda3.

I wanted to delete sda5, sda9, sda6

I was able to delete sda 9 while in Lubuntu.

I had to use LiveCD to delete the others.

.     - When I tried to delete sda5 it told me I would have to start with higher numbers.
.     - I put SwapOn sda5 and deleted sda8 successfully
.     - Deleted sda6 successfully
.     - Everything looked good: Two large unallocated spaces (one near windows, one near lubuntu)

Shut down and restarted Lubuntu.

error: no such partition
grub rescue> _


What now...........................

error:

---

### Post by snowpine on 2012-04-11
> **JXR said:**
> The partitions I wanted to keep were sda1, sda2, and sda3.

If those are the only 3 partitions you kept, then you have deleted Linux.

You can reinstall Lubuntu in the free space. :)

If I misunderstood your post (and you have other partitions in addition to sda1, sda2, and sda3) then please post a GParted screenshot, thanks.

---

### Post by JXR on 2012-04-11
What I suspect (not knowing at all) is happening is that Lubuntu is not able to find the swap partition it wanted (sda8 - the one with the lock on it). Since I could only delete partitions starting at the highest number I figured that if I enabled sda5 (SwapOn) and deleted the others that Lubuntu would find and use it.

Guess not.

Is there a way, through GRUB (command line) of reassigning this swap partition?

(By the way, currently I am able to access NOTHING. I don't even have the option of opening Windows since no preliminary "choose what OS you want to boot off" screen shows up.)

---

### Post by JXR on 2012-04-11
I don't know how to post a GParted screenshot. If I bring up the "TryMe" Ubuntu (remember, the Lubuntu LiveCD does not do the TryMe or install, unless there's a sudo way of doing it off the command line) program and take a screenshot of GParted, there's no way of saving it and no way of posting it via Firefox since the TryMe version does not enable wireless.

---

### Post by snowpine on 2012-04-11
It sounds like you deleted your root partition ("mount point /").

From the command-line you can type:

```
sudo fdisk -l
```

to list all partitions. (Note that's a lower-case 'L' and not the numeral '1').

---

### Post by JXR on 2012-04-11
grub rescue> sudo fdisk -l
unknown command 'sudo'
grub rescue> fdisk -l
unknown command 'fdisk'

seems grub rescue and sudo don't understand each other.

---

### Post by snowpine on 2012-04-11
> **JXR said:**
> grub rescue> sudo fdisk -l
unknown command 'sudo'
grub rescue> fdisk -l
unknown command 'fdisk'

seems grub rescue and sudo don't understand each other.

Sorry, I meant to reboot from your Live CD an then issue that command from the Terminal. :)

The GRUB screen is not likely to get you anywhere.

---

### Post by JXR on 2012-04-11
Device Boot|Start |End|Blocks|Id|System

/dev/sda1|1|4|     32098+|dc|Dell Utility
/dev/sda2|5|2322|18614194+|7|HPFS/NTFS
/dev/sda3|2691|3648|7693313|5|Extended
/dev/sda4|2691|3213|4198286|82|Linux swap/Solaris

(vertical bars mine to indicate spaces)

---

### Post by snowpine on 2012-04-11
Lubuntu is **gone** so I recommend deleting the /dev/sda4 swap partition using GParted and then reinstalling Lubuntu in the free space (I think the installer has a "use largest free space" option, but if not, write back and we can help with the Manual option).

---

### Post by JXR on 2012-04-11
Oops I misspoke. 
What I recorded was sd4 is actually sd5. 

I assume I should still delete sd5, right?
(What, about the terminal response, told you Linux wasn't there? How would the line have read if Linux were there?)

---

### Post by snowpine on 2012-04-11
> **JXR said:**
> Oops I misspoke. 
What I recorded was sd4 is actually sd5. 

I assume I should still delete sd5, right?
(What, about the terminal response, told you Linux wasn't there? How would the line have read if Linux were there?)

Correct, you can delete the swap partition (whatever it's called) as the Lubuntu installer's default behavior is to create a new one (unless you choose Manual partitioning).

If you had a Linux partition, there would be a partition that says Linux in the System column.

---

### Post by JXR on 2012-04-11
I....think.....it's installed.....(what no one told me was to wait forever [without any warning screen or cpu light blinking] for Lubuntu to start the install from the LiveCD)

Per instructions, I've ejected the media; closed the CD ROM drive, restarted, and instructed (L)ubuntu to come up.  It's thinking about it.....

Need to leave for about an hour. Hope by that time it'll be up and running. Will get back to you to let you know... If it comes up I'll have ONE more question. [then I'll mark this thread solved.]

---

### Post by JXR on 2012-04-11
I can't believe it!  I came back (from conducting computer classes!!) to find the laptop still black with a blinking cursor.  Restarted and checked again to make sure... Then booted from LiveCd and brought up Terminal

sudo fdisk -l

Boot|Start|End||Id|System
/dev/sda1|  |1|4|de|Dell Utility
/dev/sda2|*|5|2322|7|HPFS/NTFS
/dev/sda3|  |2322|3648|5|Extended
/dev/sda5|  |2322|3591|83|Linux
/dev/sda6|  |3591|3648|82|Linux Swap/Solaris

I wish Linux were about something more than installing Linux.

---

### Post by snowpine on 2012-04-11
Your partitions look correct, at least. :)

---

### Post by JXR on 2012-04-11
Well the good news, productivity wise, is that Windows XP works (though with Linux taking up a bunch of space Windows only has 330 Mb available.)

It's frustrating. After a month I succeed in cleaning the drive of rogue Linux-induced partitions; install Lubuntu; and...nothing but a blinking cursor.

(by the way, I set Lubuntu to Auto Log on (in the window where you set your Linux password. Could this be a Lubuntu bug?)

Now what.....

---

### Post by Jerry N on 2012-04-11
Do you still have that 2.82gb of unallocated space after sda2?  If so you could expand your NTFS partition into that space and get some of your WinXP performance back.  

Jerry

---

### Post by GregA on 2012-04-12
OK JXR  . . . 

Your system is extremely marginalized in it's current state.  The XP install is nearly out of resources, and the Lubuntu install has issues with your embedded video hardware.   Given this undesireable state, the fixes are complex.

But, there is an alternate solution that _DEPENDS on whether you can, and are willing to get rid of XP from your laptop_.

That solution installs an excellent version of linux that is even lighter than Lubuntu . . . "antiX" . . . which uses the Fluxbox and Ice window managers.   On the antiX forums, users report running hardware with Pentium II processors and 128 meg of ram (versus your 256).

Here's a link:  [http://distrowatch.com/table.php?distribution=antix](http://distrowatch.com/table.php?distribution=antix)

So, if you can live without XP on this lappie, the steps to enable a pretty decent functional OS are:

1.   Copy off all your critical files to an external USB drive or large thumbdrive.

2.   Download from the link above, the latest version of antiX (as an iso image).  Burn it at about 8x.

3.   Test the antiX live CD which you just burned.  IF it recognizes your system hardware (especially the mobo's integrated graphics), then, 

4.   Run the install application from the antiX desktop, AND let antiX install to your "entire" hard drive.   This will overwrite XP and Lubuntu, and all the other cruft and partitions on your hard drive, and you'll have a fast, useable, single system on your 28 gig hard drive.  Be sure to let the installer load the "Grub" bootloader to the MBR (master boot record - - answer yes to the prompt). 

If this sounds complex or radical - believe me, it's a LOT easier than the path you've been down so far.  

The user community at antiX, and at Mepis (which is antix's parent distro), are very helpful and will respond to your needs.  I used to run these distros along with Ubuntu and Suse Linux, although my newer systems are all on Kubuntu these days.  

Note:  the remaining option (in my view) is just to keep XP running on your system as long as you can - - if you're at all doubtfull about implementing the above steps, stick to XP until you can upgrade your hardware to a larger drive, more ram, etc.

---

### Post by JXR on 2012-04-12
GregA

I am sooooooooooooo confused about (the different flavors of) Linux. 

I only went with Ubuntu (and then Lubuntu because I was told my computer wouldn't run Ubuntu--which it turned out was the only version of Linux to date it DID run) because friends had recommended it. But then Ubuntu folk came in and recommended Bodhi, the "Lubuntu alternate installer", etc. Since Lubuntu was a derivative I bookmarked/read about Ubuntu "Derivatives." [http://www.ubuntu.com/project/about-ubuntu/derivatives](http://www.ubuntu.com/project/about-ubuntu/derivatives) called these derivatives "recognized Ubuntu flavors" but even that was confusing: For example I thought Ubuntu Studio was a software suite. How can a software suite be a "flavor" of Ubuntu like Lubuntu--since when is software that runs on an operating system an operating system? Is Ubuntu Studio software or is it an operating system? 

And doesn't all gnu/open source software run on all Linux platforms?

I don't even know why I wanted a dual boot, except that I thought this was the most reasonable way--go back and forth from a familiar environment to an unfamiliar one--to proceed into Linux. I can't find any place that tells me why a dual boot environment might be uniquely useful.

And now distro...(and mint? and.....)  

The only thing anyone has said about the different flavors of Linux is that they are based on different kernel programs but that doesn't answer simple practical questions like what does it do; how well does it do it; and how is it different from another competing Linux flavor. 

ISN'T THERE SOME SORT OF SPREADSHEET that lists the differences between all the flavors in a way that has something to do with the hardware the Linux flavor will work on and FUNCTIONALITY (i.e., programs one can run). Isn't ther a place that presumes to tell how one flavor of Linux is better than another (isn't there a single BEST?). It's like finding out the difference between a Chevy, a Ford, and a Chrysler is that one is made out of steel; one out of iron; and one out of brass (or one runs on 73 proof unleaded gas; one on 87 proof; and one on 93 proof).

There are a number of reasons I want to look at Linux. The two most important are:
1) How do Linux programs compare with the MS Office Suite and the Adobe Suite (both of which I am very well acquainted with). Can I work in the Linux equivalent of these suites and present my clients with work that is as good and in a form they can work with (e.g., as a .pdf or, preferably for government work, back into a docx or pptx format for contracts that require work be submitted as these files.
2) How do Linux programs work with manipulating sound in real time. Looping/recording, etc programs. This kind of specialized sound software is expensive in the Windows or Mac environment and not worth the expense just to find out the latencies involved won't cut it.

Now I realize that my Dell Inspiron is not going to glow in either of these endeavors but I hope it will give me a flavor of what Linux can do. 

And by the way, with all I've gone through, is there any carryover that I can take from this (Ubuntu/Lubuntu...GParted, Terminal commands...) experience that applies to, say, distro? 

The only thing I've learned so far is that the Ubuntu support community is very generous. 

(I will try your suggestion. It seems obvious Lubuntu, Dell Inspiron notwithstanding, has lots of install problems. But if I acquire a better computer on which to run Linux, is Unbutu a platform worth looking into?)

---

### Post by Peripheral Visionary on 2012-04-12
Well it isn't exactly a spreadsheet, but it's the best "layman's language" explanation of the different Linux desktops I've ever read! [Linux Desktops]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893") 

Most of the "flavors" of Ubuntu are built either for a specific *desktop environment* or for a specific *use* or niche. There's Ubuntu Student, Ubuntu Studio, etc for specific *applications, *and Xubuntu, Kubuntu, and Lubuntu for specific *desktop environments*. See the link above to explain what the different Linux desktops are about.

---

### Post by snowpine on 2012-04-12
> **JXR said:**
> 1) How do Linux programs compare with the MS Office Suite and the Adobe Suite (both of which I am very well acquainted with). Can I work in the Linux equivalent of these suites and present my clients with work that is as good and in a form they can work with (e.g., as a .pdf or, preferably for government work, back into a docx or pptx format for contracts that require work be submitted as these files.

I recommend 1. Use Gparted to delete Linux and enlarge your Windows partition back to the full disk size; 2. Reinstall the Windows boot loader following [these instructions]("http://chrisburgess.com.au/reinstalling-or-repairing-the-windows-xp-bootloader/"). 

I work in publishing and can tell you: There is no Linux substitute for Adobe Creative Suite, and I have not found .docx's created with LibreOffice to be 100% compatible with MS Office. Windows is the best choice for your work needs, in my professional opinion.

I like your idea to experiment with Ubuntu at a future date when you can upgrade to a newer computer. :) [This list]("http://www.ubuntu.com/certification/") will help you shop, or your best option may be to buy an Ubuntu-preinstalled computer from a vendor like Asus, Dell, or System 76.

---

### Post by GregA on 2012-04-12
Well JXR,  maybe I can help clear up a few things, so you can recognize your options and make the best choices - - here are just a few basics:

Linux is comprised of the Linux kernel, and the core supporting applications and libraries - a collection of thousands of files (we're talking 25-40 thousand files make up the typical distro (distribution).  Distro is short for distribution, and distribution means a "version" of Linux.   If you look over the whole "distrowatch.com" site, you'll see there are literally hundreds of distros or variations of Linux.  If you click on these distros in the page hit section, you'll get a fact sheet with links to their home pages, user forums, and so on.

There are less than a dozen &#8220;core&#8221; or primary Linux distributions - - all the rest are spin-offs or &#8220;flavors&#8221; of these core distributions.   Examples of core distributions include &#8220;Red Hat, Debian, Slackware, OpenSuse, Gentoo, Arch, and a few others that are more obscure.  Even Ubuntu is a spin-off of its parent distribution &#8211; Debian.   Now there are probably Fifty or more spin-offs of Ubuntu.  (they're like grand-children of Debian),  Examples include Linux Mint, Bodhi, and so on.  The reasons for so many distros are many - - mostly because the world of &#8220;free&#8221; software is dynamic and full of specialized needs, wants, styles.  Also, some distros handle particular hardware better than others.  Plus, the world of &#8220;free&#8221; software (free as in speech, versus free as in beer) consist of &#8220;Communities&#8221; - small to large groups of friends from across the world that share certain ideals and principles about software, freedom, etc.  Google &#8220;Richard Stallworth&#8221;, and Linus Torvalds among others and view some of the videos on YouTube.

In Debian and Ubuntu software databases (called &#8220;repositories&#8221; by Linux users), contain upwards of 30,000 &#8220;packages&#8221; that are either applications or files that support applications (aka &#8220;dependencies&#8221;).    There is a matrix on the web that provides info as to what Linux applications replace what Windows applications (see [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)).   This site is a bit busy and somewhat dated, but you'll get the point - - that there are replacements for 90%+ of purely Windows software.  And more are added daily as the trend is to build &#8220;cross-platform&#8221; apps that run in many OS's, especially the web/cloud environment. In my experience, it is rare to have a Windows file so complex and involved, that there isn't a two way conversion process (albeit manual in some cases).

Each distro and version of the distro (e.g., Ubuntu 10.4 versus Ubuntu 12.4) has it's own repositories of packages that are intended &#8220;specifically&#8221; for that distro AND version.  So Linux users don't really surf the web (or go to Amazon) for software.   We use our Package Managers (e.g., Ubuntu Software Center, or Synaptic, or Apper) to access these repositories and download the correct updates and software for our local machines.   This is a MUCH better method than Windows utilizes.  (due to security, and compatibility).

JXR, if you are using your PC for important things (job, health, financials, etc.) - - why not check into a more current system?   IF you want your best possibility to have a dual-boot with let's say . . Windows 7 and any major Linux distro, start with a good system known for being Linux friendly (Lenovo comes to mind, as well as Dell - - again Google before you buy.).

Re the Terminal (aka console,konsole,command line), it is optional except for system admins and/or Linux enthusiasts.  It provides a non-gui environment that allows for maximum speed and flexibility to run apps, configure your network/hardware, troubleshoot, etc., but again, it's optional for most users

Hope this helps.

---

