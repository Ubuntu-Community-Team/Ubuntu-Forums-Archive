---
title: "Samsung R60 plus - ubuntu Hardy Heron 8.04 installation"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by beN..87 on 2008-06-24
_**HOW TO - Samsung R60 plus - ubuntu Hardy Heron 8.04 installation**_

*from Live CD - to fully configured system connected to the wireless network*

_- ubuntu Hardy Heron 8.04 installation (ubuntu / Vista dual boot) and configuration for Samsung R60 notebook, including configuration of ATI radeon graphics, and Aetheros Wireless cards._

N.B. This may also be helpful for those installing ATI graphics drivers for the X1250 chip and Aetheros Wireless 5007 drivers.


For those of you who would like to install ubuntu on this notebook, and have a dual boot ubuntu/Vista, or for those of you who are having problems with your restricted drivers and getting your wireless working on the samsung r60; i present the following instruction.

The information gathered for this howto came from blood sweat and plenty of tears,(which i hope i can save at least one other person by writing this)the ubuntu forums, and other linux community help pages. May i give due credit to (ubuntu forum username) nicedude, from whom the information regarding wireless configuration comes, his post on wireless configuration for Aetheros Cards can be found here [http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984) .

If you are a new linux user may i welcome and congratulate you! My hope is that this guide will serve to eliminate all pain and frustration in migrating to dual boot windoze / linux on your notebook. _If you have a Notebook pre-installed with Vista, this guide will leave you with a 'dual boot' machine. At boot up you will have the choice to boot either Vista or Linux_

My intention is to both outline and explain each step in a manner in which those with little knowledge of linux may easily understand and follow the process, that they may escape the agony of Vista, for those of you who are experienced users, please do not feel i am being intentionally patronizing in explaining simple processes, these are intended simply to help a new user understand what it is they are executing, and *learn along the way.*

Though this guide will allow for other configurations of the notebook - i will mainly assume in some explanations that the reader has the notebook pre-installed with Vista.
[B][U]
***-- Please read this guide carefully, and input all codes as they are written in to a terminal, followed by the enter key.[/U][/B]

If you have any questions, please post below and myself or others will try to assist as well and as quickly as possible. If you find this guide useful, please click the star! If you have any suggestions for editing please comment.

[U]
What you will need:[/U]

-Samsung R60 plus notebook
-USB flash drive (or similar media - At least 128mb space) (you can also burn a CD if you do not have one)
-Computer capable of burning discs and downloading files from the internet (may be the same computer you wish to install on)
-Blank 700mb CD


_Before you get started:_

Prepare a partition ( by default the R60 pre-installed with Vista comes with the Hard Drive split in two anyway) this separate partition on your hard drive will be for the ubuntu installation, seperate form your Vista, if you don not already have a spare partition, you can create one using software called Gparted, or also i beleive Vista now has an option to do this. 
( IMPORTANT! If this involves shrinking a windows partition, be sure to back-up beforehand as squashing up a windows partiton can sometimes cause data loss).

Get the iso (disc image) needed to burn an ubuntu Alternate Install disc from here 

[http://releases.ubuntu.com/8.04/ubuntu-8.04-alternate-i386.iso](http://releases.ubuntu.com/8.04/ubuntu-8.04-alternate-i386.iso)

(note: you must use an Alternate CD for installation on a Samsung R60 , and this guide is for 32 bit installation not 64 bit!)

burn the image to disc using nero or other ( IMPORTANT!!- this is a disc image - it will burn multiple files to the CD, and create a clone of an ubuntu CD - if you have burnt it correctly, you should have a disc contaiing many files, rather thean the iso file alone - DO NOT simply copy the iso file to the disc as data

_download the following packages:_

ati graphics driver- [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

(this is the proprietry (non open-source) driver from AMD/ATI for your ATI radeon graphics chipset)

madwifi wireless patch - [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

(this is a patch to get your Aetheros Wireless card working with linux -- you MUST use this 3366 version for your Aetheros Wireless)

wicd network manager - [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

(this is a Network / internet connection manager)

Put those 3 packages on CD or USB flash drive; for an easy life later on; put them in two folders, one called ati (with the ati-driver inside it) and another caled wifi (with thte other two insde) (IMPORTANT!! use clean CDs and healthy drives, - the ati-driver-installer needs to be 100% clean and perfect lest you will be faced with the white screen of death later on)

If at this point you will be installing on the same machine you are using now, simply print this page. You now no longer need an internet connection until you have one up and running on your new system.

_Installation_

Get the Ubuntu CD in the drive and restart so it's in there as soon as you boot

(your machine should boot from the CD and start the LIVE CD environment - if this fails, you may have a bad CD burn, or you may need to press the appropriate function key to enter your BIOS and tell the computer to boot from CD instead of from HD)

Using the arrow keys and enter to control this environment do the following:

Select your language

Check CD for Defects

when all reports as good and you are back to the menu

Press F6 

enter code:

noapic

(this adds a parameter to the boot to stop a I/o error on your screen so you can see the menus)

(press enter to start install)

Follow the menus to select your language, detect your keyboard layout

select 'Do not configure network at this time'

enter hostname, for example: ubuntu-notebook

Partitioning - select 'Manual'

select your empty partition - you may be able to recognise it by is size/number/name ect (IMPORTANT: be sure NOT to write over you Vista Partition!)

select the following options

Use as: ext3
Format Partition: Yes
Mount Point: / (the root file system)
Mount options: relatime (this should be the default selection)
Label: ubuntuhardy (or whatever you want it labelled as)
Reserved blocks: 5% (this should be the default selection)
Typical usage: standard (this should be the default selection)
Bootable flag: off (IMPORTANT - this must be set to off , so that the Vista Longhorn Bootloader works properly, we will install GRUB boot-loader later)

select 'Done setting up the partition'

select 'Finish partioning and write changes to disk'

It will now ask you to install swap space - don't worry this isn necessary, but if you want to , and know enough about what you're doing, go ahead)

Do you want to return to the partitioning menu?

Select 'no'

Write these changes to disk? (Check you're good to go - this is the point of no return when you hit enter!)

Select 'Yes'

select your username and password

the installation will now continue and take about 30 mins - (tip: go and get a half-time sandwich and a drink! ... oh and go and search for wherever you left that big long number for your wireless access key... thats right , this aint a normal installation how-to , no ,no no, we're gonna get you hooked up to the net aswell! )

Install GRUB bootloader?

select 'Yes'

select continue to now reboot without the CD in the drive

GRUB bootloader will display upon boot

tip for later use of your machine: 
here will now display your different operating systems - listed is ubuntu generic, the recovery mode and mem testing, and also your Windows Vista -- Windows Vista Longhorn loader may be listed twice - one of these will be samsung recovery solution, and one will be normal Vista boot - should you pick the wrong one, and recovery system boots - fear not! your Vista should still be there , just restart and choose the alternative Vista longhorn loader on the list - and you should get your normal Vista

select 'ubuntu generic'

your computer will now boot into your installed ubuntu system - without your graphics installed , you will be met by some code and a screen that will flash for 10 seconds or so, when its stopped flashing

press Alt and F2

login prompt: enter your username and password as instructed

enter the following code:

sudo bash
(enter pasword)   

(this now gives you root privelages to do system administration, usually you will be logged in under your username to stop you inadvertently damaging the system)

we will now mount your flash drive and transfer the packages - if you have burnt them to a CD or are using some kind of memory card, you will have to mount that but pretty much do the same thing, i will not explain two methods here as it may confuse others using a usb flash dirve.

insert your media ( for ease on the samsung r60 insert it at the left side so the code will be the same as mine in a few steps)

(your terminal may display a' cache write through' message when it recognizes the drive - hit enter to get back to prompt

enter the following code:

mkdir /mnt/usb

(mkdir is the command to make a new directory (or folder)- in which go files, the directory being made is in the mount folder called /mnt and the full path is /mnt/usb - this is where you will mount your usb flash drive.

enter the following code:

mount /dev/sdb1 /mnt/usb  (this tells the system mount the device /sdb1 at mount point /mnt/usb  - your mount point may be sda1 ,sda2 ,sdb1, sdb2 or similar depending on which slot you have used)

enter the following code:

ls /mnt/usb 

(this tells the system to list the folders located at /mnt/usb - it should return showing the folders you created earlier - ati , and wifi

cp -R /mnt/usb/ati /ati  

(this tells the system to copy the folder (cp) /mnt/usb/ati  , and all its contents ( -R ) to the root directory ( / )  in a folder called 'ati' - /ati

this is a fairly large file - it also needs to copy across nice and clean or you may get the white screen of death later if the ATI driver gets corrupted, let it do its thing for a minute or so until its done before you carry on

enter the following code:

ls /ati

this should return showing you - ati-driver-installer-8-5-x86.x86_64.run

enter the following code: (tip - hit your up arrow key a couple of times until you find the command where you mounted -- left arrow to the beginning ans pop a u in front - and hey presto!)

umount /dev/sdb1 /mnt/usb

this should return showing you ' umount: /dev/sdb1: not mounted ' (this unmounts the volume - note: umount NOT unmount)

enter the following code:

reboot

you should reboot at this point as the current session is the first boot into the new system , some configuration files will be written to the system during this first boot, in order that your ATI graphics are installed correctly, you must reboot before the next step

GRUB bootloader will display upon boot

select 'ubuntu generic'

your computer will now again boot into your installed ubuntu system - without your graphics installed , as before you will be met by some code and a screen that will flash for 10 seconds or so, when its stopped flashing

press Alt and F2

login prompt: enter your username and password as instructed

enter the following code:

sudo bash
(enter pasword) 

enter the following code:

cd /ati

(this tells the system to change your working directory (the one you're in ) to /ati

enter the following code:

pwd 

(print working directory - tell me whih one i am currently in) - this should return  ' /ati '

enter the following code:

whoami

(who am i? this should return 'root')

enter the following code:

ls

(this shoudl return the name of your ATI installer ' ati-driver-installer-8-5-x86.x86_64.run ' so you can easily look up and check you are spelling it correctly in the next step)

enter the following code:

sh ati-driver-installer-8-5-x86.x86_64.run

(your ati driver installer will now run an installation menu - accept all default settings - literally just hit enter each time to accept the defaults)

now that it has finished - wait 2 minutes - just let it do its thing while the system updates - be patient - better to wait 2 minutes then have to reinstall your entire system


enter the following code:

reboot

in GRUB select ubuntu generic again

you should now have a graphical login screen in pretty pretty brown!

enter username
enter password

pray that you see the heron smiling back - if you've just been greeted by the white screen of death - my heartfelt sympathy is with you, i have felt your pain -but all is not lost!  again,  this ati-installer is very sensitive - i'm not sure if its a bug , or the samsung r60 - , or the file being corrupted when copied -- but ive done it a few times now and sometimes it works, sometimes not - with the SAME METHOD, someone else on the forum had the same problem, but solved it with a fresh USB drive not full of rubbish ... anyway if you get the white screen, try again, in fact - this is the only way to install the ati drivers - and my method seems to stop any corruption by rebooting and being patient before continuing after the ati install;  make sure you are using a CLEAN usb drive, and are giving ample time for the file to be copied and installed, and you reboot after the first boot before running the installer - God willing, it will work.

now you should have an ubuntu desktop

wait about 2 minutes for the various system files to update

you should now see an icon appear in the top right with a green square and a padlock, this is you restricted driver manager (which manages the non- open source drivers for you ATI graphics and you Aetheros Wireless card.

click on it - enter your password

LEAVE THE BOX ALONE THAT IS TITLED 'ATI Fire GL' - this is your graphics driver  management for that you just installed - DO NOT untick this box

un-tick the following boxes

Atheros Hardware Access Layer (HAL)
Support for Aetheros 802.11 wireless LAN cards

These are your restricted drivers for Aetheros Wireless - fortunately there are open-sources patches available so you dont need them

close the box and now restart your machine

log in 

check your restricted drivers again - it should now say 'not in use' for those two

open system > administration >synaptic package manager

type: netw

scroll to find the packages:

network-manager
netwok-manager-gnome

mark them for removal and apply, shut synaptic

insert your install cd

open a terminal at applications > accesories > terminal

enter the following code:

sudo bash

enter the following code:

apt-cdrom add

(this will add your CD to the list of software sources - if this works skip the following step under **NOTE and go to ***<< Note finishes >>)

***NOTE -- there is a bug on the Hardy 8.04 CD here  on some installs this will fail - not to worry - if it fails do the following - 

enter the following code:
gedit /etc/fstab
now change the part of the line that deals with the cdrom - it will look something like this
/dev/scd0   /media/cdrom0   udf,iso9660
/dev/cdrom   /media/cdrom0   udf,iso9660

either way the /dev/cdrom/ section will be wrong - it should be:
/dev/cdrom/   /media/cdrom0   udf,iso9660

( where it is listed as /cdrom/  rather than /cdrom   (without the / after cdrom) or /dev/scdo which is even more wrong!

save and exit fstab

you will now need to reboot in order for fstab to load up correctly before carrying on after opening your terminal - be sure to run sudo bash to get root privelages, run apt-cdrom add again - carry on following instructions

***<< Note finishes >>

enter the following code:

apt-get install build-essential

( packages essential for building drivers should now install if it can't find the sources see the note above)

after its done - eject the cd

open your home folder in  places > home folder

now to build your wifi patch;

insert your usb stick

it should recognise it - if not, mount it up in the terminal

copy the folder wifi from your usb stick into  home

unmount and eject usb stick

open a terminal at applications > accesories > terminal

enter the following code (where yourname is your user name):

cd /home/yourname/wifi

enter the following code:

sudo bash
 
(enter password)

enter the following code:

ls

(for easy spellchecking of madwifi name)

enter the following code:

tar -xvzf madwifi-nr-3366+ar5007.tar.gz

(this will upack the archive)

(tip: press up a couple of times on your arrow key and edit the previous command to the following)

enter the following code:

cd madwifi-nr-3366+ar5007

enter the following code:

make

when it's done and returns to prompt enter the following code:

make install

enter the following code:

modprobe ath_pci

(this sets your wireless module)

enter the following code:

sudo gedit /etc/modules

add the following two lines to the file (this makes your wifi modules load upon boot)


ath_hal
ath_pci

save and exit

close the terminal when done

go to your home folder /wifi

click on the wicd_1.4.2-1-all.deb

install wicd network manager

(an error message will display after install saying 'could not find some resources' dont worry thats fine it still works)

open menu > Applications > Internet > Wicd

in wicd - go to preferences

check both interfaces are listed

Wireless interface: ath0
Wired Interface: eth0

change WPA supplicant Driver in drop down menu to ' madwifi'

reboot the system

open wicd, click refresh  

if there are any wireless access points in range it should now recognise them

click on advanced next to the wireless detected

consult your network owner / ISP for you Pass Key - make sure WEP or Hex is used for the correct key type

enter it and connect up

open up firefox and hit google to see if you're up and running

if so - :popcorn: !! congratulations !! :guitar: you now have a dual boot Vista / Ubuntu notebook connected up to the web.... my money says you'll hardly ever use the Vi-****-sta now!

Good Luck and happy computing with your ubuntu!



BEWARE!

When installing updates be VERY AWARE to check for all instances of, and avoid like the plague
linux-restricted-drivers
linux-restricted-modules

or anything else that might interfere with your driver set up that you are prefectly capable of now managing yourself!


Known Problems on the R60:

Video flickering due to Compiz 3d desktop on the Samsung R60 with ATI Tadeon graphics 1250

- solution for those who wish to use compiz see here to configure your video to get rid of the flicker

[http://forum.compiz-fusion.org/showthread.php?t=1152](http://forum.compiz-fusion.org/showthread.php?t=1152)

this should be fixable fairly soon as soon as compiz get their act together, for those of you who are not bothered about fancy 3d desktop graphics simply uninstall compiz

apt-get remove compiz


Troubleshooting

---White Screen of death

Your ATI driver hasnt installed properly, reinstall ubuntu, and follow the guide again properly, make sure of the followwing:
you are using a healthy, uncluttered usb drive
the file is uncorrupted
you are following the guide correctly
you are rebooting after the first boot into a fresh system BEFORE installing the ATI driver

---Followed everything fine, cannot find my wireless singnal and i am 100% the box is OK - 

have you got rid of gnome network manager and installed wicd?
have you checked wicd preferences list both ath0 and eth0 and madwifi as your supplicant driver?
have you added ath_hal and ath_pci to you etc/modules?
have you rebooted after configuring your wirless settings?

if so - go to you restricted driver manager again - turn the wireless drivers on - and then back off again

reboot

refresh wicd - any signal ?

if not enter the following code:

sudo bash 
cd madwifi-nr-3366+ar5007
make uninstall
make clean
make
make install
reboot

---

### Post by freon27 on 2008-07-08
This is great.  I was really struggling to get Ubuntu on my R60 and Vista was making me very sad.  I installed Kubuntu so I was able to use the included network manager but a nice simple walkthrough on how to get the ATI drivers installed and the wireless card working was exactly what I needed.  Thanks so much.

---

### Post by beN..87 on 2008-07-08
> **freon27 said:**
> This is great.  I was really struggling to get Ubuntu on my R60 and Vista was making me very sad.  I installed Kubuntu so I was able to use the included network manager but a nice simple walkthrough on how to get the ATI drivers installed and the wireless card working was exactly what I needed.  Thanks so much.

"very sad" lol you bet!! installing on this machine without the exact method is just a nightmare! i was nearly crying at some points!

anyways glad it helped you out, and keep that lid nice and shiny as long as you can!

---

### Post by StressedOne on 2008-07-16
Hey guys,

first of all - thanks for that nice instruction, i also used it to install Debian. Though, Debian pretty bugged my brain with several errors, hence why I switched to Ubuntu, without having any problems..

.. I thought! I wonder if it's just me.

Don't any of you guys experience the problem with a "freezing" GUI? 
It's not really freezing, hard to describe, everything that contains text and/or graphics that are frequently updated "hangs" as long as I'm not moving my mouse / doing keyboard Input.

This is such a strange one - since it starts appearing quite random, like 20-40 Minutes after Bootup, it lasts pretty constantly though.

Anyone? Or is it just me? I'm pretty, well... :popcorn:

Sincerely

---

### Post by CryptSphinx on 2008-07-17
Thanks ben, my dad was all up for giving the penguin team a go on his new laptop and without this I would have been royally screwed trying to get it working, he now boots into his 'other' OS rarely.

Only problem I had was repeatedly getting white screens of death.
(though I found they could be bypassed by using the failsafe-gnome login)

Many Thanks.

---

### Post by beN..87 on 2008-07-17
> **CryptSphinx said:**
> Thanks ben, my dad was all up for giving the penguin team a go on his new laptop and without this I would have been royally screwed trying to get it working, he now boots into his 'other' OS rarely.

Only problem I had was repeatedly getting white screens of death.
(though I found they could be bypassed by using the failsafe-gnome login)

Many Thanks.

did you get the whitescreen of death sorted ? its very strange that it sometimes works sometimes doesnt ..... obviously you can login failsafe but then theres no 3d compiz fun!

as for why the ati-driver doesnt work sometimes i have no idea - i just found that on some installs it worked, on some it didnt - and kept doing it the same way until it worked without whitescreen ...

ps for anyone using compiz on this notebook - you'll be getting the video flicker - solutions here >  [http://forum.compiz-fusion.org/showthread.php?t=1152](http://forum.compiz-fusion.org/showthread.php?t=1152)

---

### Post by BjoernVDM on 2008-08-03
Hiya, 

got mine running from the alternate install CD without too many troubles, then used **Envy-ng** to get the video drivers.

(I had the alternated CD (Kubuntu in this case) and an Ethernet cable though)

I do have some ACPI troubles, regarding brightness controls, and I think the fan is not properly controlled. **powertop** never shows less then 23 Watts or thereabouts. Do the brightness controls work out-of-the-box for anyone? Else we have to start futzing with the whole map-key-to-acpi-script stuff?


**Wireless,** *Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)*

Didn't patch anything for the wireless, rather installed the latest madwifi and madwifi-hal from svn (no idea whether this will survive Ubuntu updates).
Prerequisites: **build-essentials** and **subversion**.

```

svn checkout http://svn.madwifi.org/madwifi/trunk madwifi-ng 
cd madwifi-ng
make
sudo make install


svn checkout http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6
cd madwifi-hal-0.10.5.6
make
sudo make install

sudo modprobe ath_pci

```



The newest HAL fixed a "HAL doesn't support MAC revision 0xe2" for me.

---

### Post by MrPatton84 on 2008-08-05
Just a quick question about partitioning before I go ahead and do this. 

I know that Vista on this laptop already has the Hard Drive partitioned into C and D. So, does this mean I don't have to partition again - or do I need to make a third partition?

I've read in your instructions where you give directions for partitioning (making sure to emphasise that I mustn't write over the Vista partition!) How can I be sure I don't do this accidentally? 

Thanks for any help and extra information here - I'm just being cautious so I don't screw this up :)


*EDIT* Can I just select the D drive partition (already set up with the laptop) for the Ubuntu install, or do I have to create a third partition prior to install? :S

---

### Post by beN..87 on 2008-08-07
> **MrPatton84 said:**
> Just a quick question about partitioning before I go ahead and do this. 

I know that Vista on this laptop already has the Hard Drive partitioned into C and D. So, does this mean I don't have to partition again - or do I need to make a third partition?

I've read in your instructions where you give directions for partitioning (making sure to emphasise that I mustn't write over the Vista partition!) How can I be sure I don't do this accidentally? 

Thanks for any help and extra information here - I'm just being cautious so I don't screw this up :)


*EDIT* Can I just select the D drive partition (already set up with the laptop) for the Ubuntu install, or do I have to create a third partition prior to install? :S

when the partitioner is up and running it should give you some indication as to which one has the vista on it - ie disk usage and NTFS file system .... mine came with an empty partition for backupo - so i deleted it and partitioned the empty space ..... if you choose guided partitioning of the empty space it will set up swap for you automatic

---

### Post by BjoernVDM on 2008-09-09
StressedOne:
> Don't any of you guys experience the problem with a "freezing" GUI?
It's not really freezing, hard to describe, everything that contains text and/or graphics that are frequently updated "hangs" as long as I'm not moving my mouse / doing keyboard Input.

Same problem here. Problem with the hardy kernel. Try appending the nohz=off to your kernel boot line in grub.

---

### Post by marcordenis on 2008-09-28
Help... I wanted to install Hardy on my new Samsung R60 Plus. I followed the guide all the way, up until the point > Install GRUB bootloader?

select 'Yes'
It got up to 50%, I think, and then I got the following error
> Error executing "grub-install (hd0)" failed.
Fatal Error
Then I just followed the steps out of this by clicking on Next or something, and said finish installation (or something similar). So I suppose I have Ubuntu installed, but cannot boot it as I do not get the GRUB menu. 
I tried exactly the same installation and got to the same point again.
BTW I also have Vista installed.
What can I do?
Hope someone can help.

UPDATE:
I managed to sort it out (though I don't know how). Thank you very much for this tutorial, it did help a lot. By the way I'm using the default GNOME Network Manager because the wicd program somehow didn't work. Thanks again.

UPDATE 2:
I was trying to make my desktop look funky and turned on the Advanced Desktop Effects. When I rebooted, I got a white screen right after logging in. How can I turn these effects off again to make my laptop work again? Thanks in advance.

---

### Post by marcordenis on 2008-09-30
Sorry Ubuntu, but I think I will be giving up on Ubuntu on my laptop. I installed everything again after having gotten the white screen. Problem was, I updated my system once I had gotten everything working, rebooted, and here I was again, same white screen as before. I suppose there's something you shouldn't update, but I don't know what. Well, at least Ubuntu works on my desktop...

---

### Post by BjoernVDM on 2008-10-19
After an upgrade Wireless was broken.

error was dmesg:  HAL doesn't support MAC revision 0xe2

Tried reinstalling from svn. Gave me errors: ath_pci: disagrees about version of symbol ieee80211_input_monitor

See: [http://madwifi.org/ticket/1114](http://madwifi.org/ticket/1114), reply by danino.

Fixed by uninstalling "restricted modules" and reinstalling Madwifi from SVN. 

No ill effects from uninstalling restriced modules so far (but I installed graphics drivers with envy).

---

### Post by iner on 2008-10-23
Thank u so much for that tut. it helped me alot, im new to ubuntu and after installing i got stucked in commanline for about 3 hours till i found out that ich have to write this "mkdir /mnt/sdb1" in order to use ur command.

but now my ubuntu works, the only problem is, i dont get a connection to the internet, and i dont know why.

im not using WLAN, i use a lan cable.

can someone help me?

Edit:
now im stuck in commandline again. it sais after restart: 

Loading, please weit...
kinit: name_to_dev_t(/dev/disk/by-uuid/eb15d1b2-f522-4f30-8d13-6a4c29489f49) = sda1(8,1)
kinit: trying to resume from /dev/disk/by-uuid/eb15d1b2-f522-4f30-8d13-6a4c29489f49
kinit: No resume image, doing normal boot...

what to do?

---

### Post by Natovr on 2009-02-01
Thanks :D I wish I saw this earlier though... I was dual booting Ubuntu with Vista on an R60 Plus laptop, and had to figure out all the atheros and ATI problems myself! :|
I'll definitely save this somewhere in case I need to re-install :)

---

### Post by bumdrew on 2009-02-26
Thank you for posting this excellent guide.

I am having issues with getting the display driver to install.

It just refuses to go in.

I notice the version of this driver now available is a different one to what it was when this guide was posted.

Does anyone know where I might be able to download the archived file from? rather than trying to get this new one working?

Thanks In Advance
Bumdrew
Intel Inside-Idiot Outside

---

