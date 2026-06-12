---
title: "ISO CD won't boot on new Comp. Newbie day 1."
date: 2012-06-06
forum: New to Ubuntu
---

### Post by stevemav on 2012-06-06
Hi there, I've downloaded Ubuntu on my Laptop, burnt the image ISO to a DVD, and restarted the Laptop to explore Ubuntu. This worked fine. The Laptop is running Vista.

However, I've placed the DVD into the DVD drive of my brand new comp, to no avail. The new comp is without an OS.

The BIOS screen shows briefly, then the pink/purple screen that has only a small bar and little man in a circle shows up The screen hibernates and the comp seems to keep running, with nothing showing on the screen. I've been turning off the comp at the back for a couple of hours, as I can't simply press the power button at the front. 

I attempted to change the boot sequence in the BIOS with no change being observed after that.

As I didn't assemble the comp, I'd like to try and rule out any newbie problems before I try checking for hardware problems. 

Many thanks if you can shed some light on the issue.

---

### Post by choppyfireballs on 2012-06-06
> **stevemav said:**
> Hi there, I've downloaded Ubuntu on my Laptop, burnt the image ISO to a DVD, and restarted the Laptop to explore Ubuntu. This worked fine. The Laptop is running Vista.

However, I've placed the DVD into the DVD drive of my brand new comp, to no avail. The new comp is without an OS.

The BIOS screen shows briefly, then the pink/purple screen that has only a small bar and little man in a circle shows up The screen hibernates and the comp seems to keep running, with nothing showing on the screen. I've been turning off the comp at the back for a couple of hours, as I can't simply press the power button at the front. 

I attempted to change the boot sequence in the BIOS with no change being observed after that.

As I didn't assemble the comp, I'd like to try and rule out any newbie problems before I try checking for hardware problems. 

Many thanks if you can shed some light on the issue.

Did you try burning another copy of the cd maybe your current one is damaged

---

### Post by stevemav on 2012-06-06
I have checked the disc, it booted ubuntu on my laptop perfectly.

---

### Post by arochester on 2012-06-06
Does your computer have a MAKE and MODEL, or what are it's basic specs?

Particularly, do you know what video card you have?

---

### Post by steeldriver on 2012-06-06
agreed it sounds like it *is* booting, but can't display on your graphics hardware 

try pressing the shift key right as soon as you see that purple screen flash up - that should get you into the advanced boot options menu which will allow you to change to a fallback graphics mode (usually 'nomodeset' works)

choose a language, and then you should get a menu including 'F6 Other Options' - press F6 and choose 'nomodeset' from the submenu then ESC; now you should be able to boot one of the main options (I'd recommend 'try without installing' at first)

---

### Post by stevemav on 2012-06-06
> **arochester said:**
> Does your computer have a MAKE and MODEL, or what are it's basic specs?

Particularly, do you know what video card you have?

I've got an AMD APU, with integrated Radeon graphics. I'm attempting to look up the specifics from my online order, however mwave's site seems to have been taken offline at the moment. I will notify you when I have all the specs.

For now I know I have the ASRock A 75M-HVS Motherboard,

---

### Post by stevemav on 2012-06-06
> **steeldriver said:**
> agreed it sounds like it *is* booting, but can't display on your graphics hardware 

try pressing the shift key right as soon as you see that purple screen flash up - that should get you into the advanced boot options menu which will allow you to change to a fallback graphics mode (usually 'nomodeset' works)

choose a language, and then you should get a menu including 'F6 Other Options' - press F6 and choose 'nomodeset' from the submenu then ESC; now you should be able to boot one of the main options (I'd recommend 'try without installing' at first)

Great, I followed what you've said and it's loading up. What steps can I take to sort this out for the future?

Also, I forgot to mention that this is a custom build PC.

---

### Post by steeldriver on 2012-06-06
OK that's good, perhaps you could mark the thread SOLVED (via 'Thread Tools')

FWIW I have mythbuntu on an AMD A6 (with an ASUS M/B) and THAT needed nomodeset to boot properly with a VGA monitor - it boots fine with an HDMI display

I'm hesitant to suggest a long term fix - you *may* find it just works if you install the AMD/ATI proprietary driver (fglrx) but I'm still having OTHER problems with fglrx (breaking HDMI sound output, screwed up modes for DVD/TV playback)

**How do I install the ATI driver? --> **[http://ubuntuforums.org/showthread.php?t=1982640](http://ubuntuforums.org/showthread.php?t=1982640)

---

### Post by stevemav on 2012-06-06
@[steeldriver]("http://ubuntuforums.org/member.php?u=1627500") 

Changing to nomodset- does that mean it will boot every time, or are there other tweaks I'll need to do before I install the OS?

---

### Post by steeldriver on 2012-06-06
to make an *installed* system use 'nomodeset' on every boot you would 

1. edit your /etc/default/grub file, adding nomodeset on the GRUB_CMDLINE_LINUX_DEFAULT line

2. run update-grub to write the new config

Running permanently with 'nomodeset' will likely not give you very good graphics performance so I would suggest you go ahead and do the install - it *may* just work once the install process fully configures the X server for your hardware - if it doesn't you can interrupt the installed system's boot in a similar way (shift - then 'e' for edit) as you did for the LiveCD boot and add nomodeset as a one-off on the boot line to get you in - you can THEN add the nomodeset boot option permanently if you really must

---

### Post by stevemav on 2012-06-06
> **steeldriver said:**
> OK that's good, perhaps you could mark the thread SOLVED (via 'Thread Tools')

FWIW I have mythbuntu on an AMD A6 (with an ASUS M/B) and THAT needed nomodeset to boot properly with a VGA monitor - it boots fine with an HDMI display

I'm hesitant to suggest a long term fix - you *may* find it just works if you install the AMD/ATI proprietary driver (fglrx) but I'm still having OTHER problems with fglrx (breaking HDMI sound output, screwed up modes for DVD/TV playback)

**How do I install the ATI driver? --> **[http://ubuntuforums.org/showthread.php?t=1982640](http://ubuntuforums.org/showthread.php?t=1982640)

I don't use HDMI at all, I'll install the driver you link to if you think that will help.

I've just gotten this message while the installation was going through-

Executing 'grub-install /dev/sdb' failed

This is a fatal error.

Sort of a little upset and worried now

**EDIT** Now I'm given the options to either chose a different device to install the bootloader on- /dev/sda(SSD 64 GB), /dev/sda1(No idea waht this could be, other than partition that the installation performed itself), /dev/sdb(1TB HDD) 

or I can continue without a bootloader,

or cancel the installation 

under this message box, I'm getting another box telling me installation is complete.

---

### Post by choppyfireballs on 2012-06-06
> **arochester said:**
> Does your computer have a MAKE and MODEL, or what are it's basic specs?

Particularly, do you know what video card you have?

Ok well sometimes people don't check the disk so i was just wondering I recommend finding out your specs and sharing them here as arochester has recommended above

---

### Post by stevemav on 2012-06-06
> **choppyfireballs said:**
> Ok well sometimes people don't check the disk so i was just wondering I recommend finding out your specs and sharing them here as arochester has recommended above

The site is back up, so the specs that I'd think are important are:

AMD A6-3500 Triple Core Fusion APU - Socket FM1 - 2.1GHz - 3MB L2 Cache -  Integrated Radeon HD6530D Graphics - TDP 65W - Llano - Fan Included 

    ASRock A75M-HVS Motherboard -  AMD Socket FM1 - AMD A75 FCH Chipset - 2x DDR3-2400 - 1x PCIe x16, 1x  PCIe x1 & 1x PCI - 6x SATA3 - 4x USB3.0 - D-Sub & HDMI - 5.1  Channel Audio - Gigabit LAN - Micro ATX

I don't have a graphics card, as I am mostly using the PC for web browsing.

---

### Post by steeldriver on 2012-06-06
> **stevemav said:**
> I don't use HDMI at all, I'll install the driver you link to if you think that will help.

I'd stick with the default driver (radeon) until you get the system basically up and running

> **stevemav said:**
> 
I've just gotten this message while the installation was going through-

Executing 'grub-install /dev/sdb' failed

This is a fatal error.

Sort of a little upset and worried now

OK tell us about your drive(s) and whatever partition options you chose at install time

---

### Post by stevemav on 2012-06-06
[QUOTE=steeldriver]


OK tell us about your drive(s) and whatever partition options you chose at install time[/QUOTE]

    Crucial M4 64GB SATA 6GB/s Solid State Drive - 2.5" - 500MB/s Read & 95MB/S Write - NAND Management 

and

    Western Digital WD Caviar Blue 3.5" 1TB SATA 6.0Gb/s 7200RPM 32MB Hard Drive 

I opted to use the full 64 GB SSD at the initial install. I'm guessing that I should have asked for a small partition occurring there?

**Edit** the partition of the 64GB SSD ended up being 60 in sda1 (ext4) and then 4GB in sda5(linux-swap)

---

### Post by steeldriver on 2012-06-06
I would think grub should be installing on the SSD, no? did you tell the install to use the WDC drive at all (did you choose a mount point for it?)

**NB you have to read carefully when you get to the partition/install screen - the block device naming is quite likely to change between boots (it depends on the order in which the devices respond I think) so you need to make sure it is choosing the device you think it is for the grub install**

---

### Post by stevemav on 2012-06-06
> **steeldriver said:**
> I would think grub should be installing on the SSD, no? did you tell the install to use the WDC drive at all (did you choose a mount point for it?)

**NB you have to read carefully when you get to the partition/install screen - the block device naming is quite likely to change between boots (it depends on the order in which the devices respond I think) so you need to make sure it is choosing the device you think it is for the grub install**

Can I chose the grub to go on  the SSD as well as the other partitions going on there?

---

### Post by steeldriver on 2012-06-06
yes it's normal to put grub on the device with the / partition (or /boot partition if you have a separate one)

there would likely be other issues booting from the 1TB disk anyway (at least without making an explicit GPT / UEFI boot partition - in fact that may be why grub is refusing to install there - I don't really know anything about those things)

---

### Post by stevemav on 2012-06-06
> **steeldriver said:**
> yes it's normal to put grub on the device with the / partition (or /boot partition if you have a separate one)

there would likely be other issues booting from the 1TB disk anyway (at least without making an explicit GPT / UEFI boot partition - in fact that may be why grub is refusing to install there - I don't really know anything about those things)

It seems to want to put itself there every time I let it chose- are you able to help me set up in detail the partitions I need, so there's less that's likely to go wrong?

---

### Post by steeldriver on 2012-06-06
well what are you trying to use the big disk for? how fancy do you want to get?

if you go through the 'Do something else' option you can manually choose  mount locations AND manually choose the grub install location (I would  think that the grub install location *should* be choosable in the  regular install - but I don't know because I never use it)

if you just want to use the 1TB disk as 'storage' you can leave it out  of the mix for now and then later create a mount point and fstab entry  for it

with an SSD  system drive there are good arguments for putting /var (and /tmp - if you are not using tmpfs) on the conventional disk - but you can just put everything on the SSD for now and then fix that after when you have a better understanding of the pros and cons and exactly how you want to do it (actual /var and /tmp partitions? or LVM logical volumes?)

---

### Post by stevemav on 2012-06-06
> **steeldriver said:**
> yes it's normal to put grub on the device with the / partition (or /boot partition if you have a separate one)

there would likely be other issues booting from the 1TB disk anyway (at least without making an explicit GPT / UEFI boot partition - in fact that may be why grub is refusing to install there - I don't really know anything about those things)


Hope I don't catch you too late, I've used this guide-

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/2/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/2/)

to attempt to create the relevant partitions. I varied the sizes of my partitions only a little, mainly due to my desire to not dual boot, and knowing I had another 1TB available. 

If the error occurs again, I'll need to sleep on it and come back for another assault. Hopefully something I do will sort it out fairly soon. 

If this resolves it, I will update my first post as solved.

---

### Post by stevemav on 2012-06-06
> **steeldriver said:**
> well what are you trying to use the big disk for? how fancy do you want to get?

if you go through the 'Do something else' option you can manually choose  mount locations AND manually choose the grub install location (I would  think that the grub install location *should* be choosable in the  regular install - but I don't know because I never use it)

if you just want to use the 1TB disk as 'storage' you can leave it out  of the mix for now and then later create a mount point and fstab entry  for it

with an SSD  system drive there are good arguments for putting /var (and /tmp - if you are not using tmpfs) on the conventional disk - but you can just put everything on the SSD for now and then fix that after when you have a better understanding of the pros and cons and exactly how you want to do it (actual /var and /tmp partitions? or LVM logical volumes?)

Sorry for the double notif. 

As I have zero idea what those terms are, I'll be happy to learn about them later :). I'll most likely use the 1TB for storage of a little music, ebook files and comics, if the file types are supposed in Linux.

---

### Post by stevemav on 2012-06-06
I'm wrong, it's still coming up with the same message.

I can't stay up any longer, hopefully some magic can be worked tomorrow.

---

### Post by choppyfireballs on 2012-06-07
> **stevemav said:**
> Sorry for the double notif. 

As I have zero idea what those terms are, I'll be happy to learn about them later :). I'll most likely use the 1TB for storage of a little music, ebook files and comics, if the file types are supposed in Linux.

Out of curiosity do you have another hard drive we can test this on that you can put in the computer that's not working? If it has something to do with a grub you might be able to boot with a different hdd installed in that machine? I'm kind of new to grub and those things too I'm just thinking out loud and throwing ideas around.

---

### Post by traditionalist on 2012-06-07
> **stevemav said:**
> Crucial M4 64GB SATA 6GB/s Solid State Drive - 2.5" - 500MB/s Read & 95MB/S Write - NAND Management 

and

    Western Digital WD Caviar Blue 3.5" 1TB SATA 6.0Gb/s 7200RPM 32MB Hard Drive 

I opted to use the full 64 GB SSD at the initial install. I'm guessing that I should have asked for a small partition occurring there?

**Edit** the partition of the 64GB SSD ended up being 60 in sda1 (ext4) and then 4GB in sda5(linux-swap)


There are some problems with default installs when you have ( a couple of)  normal disks and an SSD. It nearly drove me nuts trying to install my first setup because of this. For some reason Ubuntu always wants to put the loader on one of the other disks and also sets up a swap partition on the SSD which is useless. (Worse than useless actually as if much swapping occurs it will wear out your SSD much more quickly!).

You must choose "Something Else"  when the installation asks you and set up the partitions yourself.

First you need to set up the partition on the SSD correctly.  There are a more or less infinite number of ways to set things up and people have varying ideas on what is best. This is how I did it. Here is the general plan;

I chose ext4 as a format. ( Info here;  [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4) )

I just put /  on the SSD  and /home on one of my other drives;

[[IMG]http://img407.imageshack.us/img407/394/informationaboutdevsdc1.th.png[/IMG]]("http://img407.imageshack.us/i/informationaboutdevsdc1.png/")

[[IMG]http://img256.imageshack.us/img256/8755/informationaboutdevsda1.th.png[/IMG]]("http://img256.imageshack.us/i/informationaboutdevsda1.png/")

I found the easiest way to redirect the folders was this;

[[IMG]http://img140.imageshack.us/img140/5302/ubuntutweak001.th.png[/IMG]]("http://img140.imageshack.us/i/ubuntutweak001.png/")

[[IMG]http://img403.imageshack.us/img403/5302/ubuntutweak001.th.png[/IMG]]("http://img403.imageshack.us/i/ubuntutweak001.png/")

this is what you see and can access when SDA1 is mounted, you can set it to automount;

[[IMG]http://img690.imageshack.us/img690/7451/sda1data001.th.png[/IMG]]("http://img690.imageshack.us/i/sda1data001.png/")

I put the swap partition on one of my other drives. I [COLOR=Red]DO NOT[/COLOR] want a swap partition on my SSD. I used 8 GB as a swap partition on another disk. Set this up first and Ubuntu will not bother you with various things when you set up to use the whole SDD as your Ubuntu root and boot partition. If you have no swap partition set up somewhere it will moan at you that you have not set up a swap partition.  I have 8 GB RAM in this machine and it rarely if ever uses the swap partition but you still need to set one up. I used a swap partition of 8 GB, as I don't really care about 8 GB on a conventional terabyte disk. However, I object strongly to losing 4 GB from my SSD! If you have several  disks then use the least used one for your swap partition. This disk must then be mounted at all times of course as otherwise the swap partition is not accessible.

This setup has a number of advantages.  The root is completely separate from any data etc.  It is very very fast to run a backup and there is no confusion at all, because that is all there is on the SSD.  You CAN place your /home on the SSD as well, and this speeds up loading applications etc, but I found no appreciable advantage in doing this.

You must be very careful to tell Ubuntu that it should place the loader on the SSD as it otherwise defaults to putting it on another drive. This setting is at the bottom of the configuration menu and easily overlooked! Ubuntu will also [COLOR=Red]CHANGE[/COLOR] that setting  after you have made other changes! Make absolutely sure that the loader is set to be mounted on the SSD before you leave the configuration menu. If you do not do this and overlook the setting the loader will be placed on the wrong drive.

[COLOR=Red]**ATTENTION!  If you do this on a machine which has running partitions from another operating system then it will render that partition useless. If this is a boot partition from Windows 7 for instance, then Windows 7 will not boot any more.  There are doubtless ways and means to repair this, but it is best to avoid it in the first place.**

[COLOR=Black]If you need more detailed information on this, or anything is not clear then just post again. I wasted a great deal of time when I first tried to set up. If you follow the above it should be quick and painless!  :)

Finally, to save yourself a lot of time and frustration down the road, after you have your system set up,  install this software before you do anything else;

[http://www.remastersys.com/](http://www.remastersys.com/)

This will allow you to restore your system easily at any time just by booting a DVD.  Once again there are untold numbers of ways to back up, so many in fact that it will make your head spin trying to find one that works and suits you.  This system is easy, reliable, and very fast.

For data etc ;

[[IMG]http://img710.imageshack.us/img710/193/ubuntusoftwarecenter015.th.png[/IMG]](http://img710.imageshack.us/i/ubuntusoftwarecenter015.png/)
[/COLOR] [/COLOR]

---

### Post by stevemav on 2012-06-08
Hi there traditionalist, I've had a little trouble logging back in here. I've taken your very detailed help into account. Unfortunately, the images you linked from imageshack, I have no idea what they mean, sorry. 

I don't understand the redirecting etc, as my primary concern at the moment is simply getting the comp to load, it's being very resistant to the idea.

The comp currently waits until the Bios screen finishes, and then the monitor goes to sleep. 

I've installed the OS as far as I'm aware, it got to the end and asked to reboot, ejected the bootDVD, then the screen went blank.

I'm at a total loss and rather upset. 

any further help will be greatly appreciated.

---

### Post by steeldriver on 2012-06-08
Hi again - it sounds like we are back to your original problem (kernel mode graphics)

You need to interrupt the boot like you did before (press shift key) but this time

- press the 'e' key ('e' for edit)

- use the arrow keys to navigate to where it says 'quiet splash' and type nomodeset right after

- press Ctrl-X to continue the boot

If all goes well we can then set about permanently fixing

---

### Post by traditionalist on 2012-06-08
Try what steeldriver suggested first. 

Another option which will simplify things greatly is to unplug the SSD and install on your other drive. This is not really a permanent option as you doubtless wish to use the SSD, but it obviates a great many problems which are difficult for a beginner and will almost certainly get you up and running much more quickly.

Or, and probably better, unplug your other drive so that the SSD is the only one on the system. Ubuntu will then install to it with no possibility of any grub errors etc.  When you later plug your other drive back in, Ubuntu will allow you to set it up.

---

### Post by stevemav on 2012-06-09
> **steeldriver said:**
> Hi again - it sounds like we are back to your original problem (kernel mode graphics)

You need to interrupt the boot like you did before (press shift key) but this time

- press the 'e' key ('e' for edit)

- use the arrow keys to navigate to where it says 'quiet splash' and type nomodeset right after

- press Ctrl-X to continue the boot

If all goes well we can then set about permanently fixing

> **traditionalist said:**
> Try what steeldriver suggested first. 

Another option which will simplify things greatly is to unplug the SSD and install on your other drive. This is not really a permanent option as you doubtless wish to use the SSD, but it obviates a great many problems which are difficult for a beginner and will almost certainly get you up and running much more quickly.

Or, and probably better, unplug your other drive so that the SSD is the only one on the system. Ubuntu will then install to it with no possibility of any grub errors etc.  When you later plug your other drive back in, Ubuntu will allow you to set it up.

I tried to add nomodset as you described, however it simply tries to restart and goes to sleep.

Took out my 1TB and going to attempt the SSD install first.

---

### Post by steeldriver on 2012-06-09
yes that sounds like a good idea - there are definitely more things that can go wrong with the 1TB drive (GPT partition tables and so on)

on the mythbuntu box I just built I put everything on the SSD to start and then added 2x2TB data drives with all the trimmings (RAID, LVM) later

---

### Post by stevemav on 2012-06-09
> **steeldriver said:**
> yes that sounds like a good idea - there are definitely more things that can go wrong with the 1TB drive (GPT partition tables and so on)

on the mythbuntu box I just built I put everything on the SSD to start and then added 2x2TB data drives with all the trimmings (RAID, LVM) later

There's been no change, still requires me to hold shift to select the OS I want. Once selecting the OS, the screen goes blank while the comp. continues to run.

---

### Post by steeldriver on 2012-06-09
OK and when you select the OS and **before** you press 'Enter' (or before it times out and boots automatically) have you pressed 'e' and edited the grub boot line as I suggested (adding no**mode**set - not no**mod**set - after quiet splash)? 

If nomodeset worked for your hardware booting off the LiveCD it *should* also work for the installed system... I think :confused:

---

### Post by stevemav on 2012-06-09
> **steeldriver said:**
> OK and when you select the OS and **before** you press 'Enter' (or before it times out and boots automatically) have you pressed 'e' and edited the grub boot line as I suggested (adding no**mode**set - not no**mod**set - after quiet splash)? 

If nomodeset worked for your hardware booting off the LiveCD it *should* also work for the installed system... I think :confused:

Wow. So it worked, I'm in, What steps should I take to keep this from happening again? I'm not after great graphics, I plan on using this comp primarily for web browsing.

I've headed over to the system settings to download the ATI/AMD proprietary FGLRX graphics driver, perhaps that will help.

Ok, that's a wrap. Thanks to all of you for helping out!

---

### Post by steeldriver on 2012-06-10
OK! Progress!

If the new driver doesn't fix things, you can make the 'nomodeset' a permanent part of your boot line as follows:

1. open your /etc/default/grub file in a text editor; either

```
gksudo gedit /etc/default/grub
```or, for a terminal based editor

```
sudo nano /etc/default/grub
```2. find the line that starts GRUB_CMDLINE_LINUX_DEFAULT and add 'nomodeset'

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash "
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

```Save and close the  /etc/default/grub file

3. run update-grub to regenerate the actual bootloader configuration - in a terminal, type

```
sudo update-grub
```The next time you boot it should just fire right up.

---

### Post by stevemav on 2012-06-11
The updated driver solved the problem, cheers :).

---

### Post by steeldriver on 2012-06-11
Great! good on you for sticking at it - I know how frustrating these things can seem

---

