---
title: "PC borked after upgrade"
date: 2014-06-18
forum: New to Ubuntu
---

### Post by jan_jan_64 on 2014-06-18
So I was upgrading my PC to 14.04 today, and during the process the computer crashed. I had to turn the power off and on again, and now I cant even boot it up properly. I get the 'ubuntu 14.04' loading screen, then some red strings pop up (but a little to fast for me to really read what they are) and then it goes to a black screen with just a few strings on it (which are not aligned properly and running off the edge of the screen):  'speech dispatcher disabled; edit /etc/default/speech-dispatcher'  '*starting tor daemon... [OK]'  'saned disabled; edit /etc/default.saned'  If I press the power button, a get a whole bunch of strings that pop up just before it turns itself off, too.  So now I dont really know what to do - I cant even boot it properly and I have 0 idea of what Im doing when it comes to re-installation etc.  Any help is greatly appreciated. Thanks!

---

### Post by SuperFreak on 2014-06-18
Can you boot to a live Disc/USB?
If that is possible you should save any data you need from your Home directory to an external device and a clean install maybe in order

---

### Post by jan_jan_64 on 2014-06-18
I could possibly do that, but I have no idea actually HOW to. Complete beginner, here, I didnt even install my Linux myself in the first place - ex boyfriend did it and I have pretty much no clue how to do most things on the techinical side.  As far as I know, I cant access ANYTHING. I cant get past the boot process.

---

### Post by SuperFreak on 2014-06-18
Did your boyfriend leave you with a DVD or USB copy of 14.04? If not can you get onto another computer and follow these directions? [http://www.ubuntu.com/download/desktop]("http://www.ubuntu.com/download/desktop") Note towards bottom of page "Easy ways to switch to Ubuntu 14.04 LTS"

---

### Post by jan_jan_64 on 2014-06-18
He didnt leave me anything, he installed it a year ago so ive been using older versions already, he taught me some basics on doing updates/upgrades etc but when something goes wrong I havent any deeper knowledge of Linux to know how to fix things. Im currently using my netbook right now so I will check out the link you gave and see if theres something I can do. Thanks :)

---

### Post by stalkingwolf on 2014-06-18
if it gets to the grub screen try running the recovery mode. Then select fix broken packages. make sure you are connected to internet.

---

### Post by SuperFreak on 2014-06-18
> **stalkingwolf said:**
> if it gets to the grub screen try running the recovery mode. Then select fix broken packages. make sure you are connected to internet.

That makes sense. You may have to hold the SHIFT key during boot to get to the GRUB menu

---

### Post by jan_jan_64 on 2014-06-19
Thanks guys! Im going to give this a try now before I try the USB boot. Also, was wondering - is there anything I can do before I re-install it (apart from trying this on the grb screen) to access any of my files? It'd be nice if I didnt lose everything again T-T

---

### Post by jan_jan_64 on 2014-06-19
OK, I booted holding shift, managed to access the GRUB screen and boot in recovery mode. I selected 'repair broken packages' and I got the message 'Continuing will remount your / filesystem in read/write mode and mount any other filesystem defined in /etc/fstab. Do you wish to continue?' I selected yes, and I got the strings underneath reading: 'fsck from util-linux 2.20.1' '/dev/sda3: clean, 766504/31850496 files, 77123143/127371520 blocks'. It is now waiting for me to make some input but I dunno what to do from here...

---

### Post by SuperFreak on 2014-06-19
> **jan_jan_64 said:**
> Thanks guys! Im going to give this a try now before I try the USB boot. Also, was wondering - is there anything I can do before I re-install it (apart from trying this on the grb screen) to access any of my files? It'd be nice if I didnt lose everything again T-T

Sorry I can't help you with your last post however it should be fairly easy to recover your files from the live USB/DVD.
Boot up your computer with the LIve USB/DVD inserted, and enter the BIOS or UEFI and set the boot order so the USB or DVD player is the 1st item to boot (whichever you are using Live USB or DVD). then proceed. You should be brought to a screen that offers either to install or try Ubuntu. Choose **TRY** and the Ubuntu OS should start. From there you can use Nautilus (the file manager) to look for your PCs hard drive and retriev the files. You may have to transfer these files to an external hard drive or other media to save them. At this point you have not installed Ubuntu you are running the OS off of the DVD and RAM but you now can either shut down or install .

---

### Post by jan_jan_64 on 2014-06-20
OK well thats a plus at least :) Its a shame to lose all my settings for programs, though... I am assuming then that there is no way to use this method to also get the packages I may need to repair my Ubuntu instead of a complete new installation, then?

---

### Post by SuperFreak on 2014-06-20
Using the LiveUSB/DVD in TRY mode will not change anything on the hard drive(so no configuration files will change) but should give you access to the drive. I am not familiar with the Recovery process StalkingWolf mentioned hopefully he will answer you.

---

### Post by stalkingwolf on 2014-06-20
it is probably waiting for you to ok instalation / removal of new packages.  I have this happen on my netbooks the info is below the edge of the display. I just hit Y and enter and it goes on.   I have had no ill effects from that.

using the live disk or usb you should be able to copy your entire home folder to another location.  Make sure to open your home folder choose view and show hidden before you do.

---

