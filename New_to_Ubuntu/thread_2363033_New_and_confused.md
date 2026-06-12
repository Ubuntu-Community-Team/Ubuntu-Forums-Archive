---
title: "New and confused"
date: 2017-06-05
forum: New to Ubuntu
---

### Post by wicki on 2017-06-05
Hi I have been on Ubunto 16.04lts since Christmas this last week things have been very flakey unstable,Printer not working and could not get it to work,software center seams to be down today,  lots of freezes. this hapend before each time it seams to be after installing OS updates.

I work self employed I need a reliable pc can ubuntu be reliable ? should I have instaled a particular flavour of ubuntu like Kubuntu or would Mint or Gnome be better, I am no command line wizard,

I need photo editing word processing and email any advice would be greatly appreciated.

---

### Post by ian-weisser on 2017-06-05
My Ubuntu does not 'freeze', printing works well, nothing is flaky or unstable.

What changes do I need to make to my system behave like yours?
Can you tell us more about which release/flavor of Ubuntu you are running, and on what sort of hardware?

---

### Post by Bucky Ball on 2017-06-05
It's Ubuntu 16.04, but please tell us more about hardware, as ian-weisser requests. 

> **wicki said:**
> Hi I have been on Ubunto 16.04lts since Christmas ... Printer not working and could not get it to work,software center seams to be down today,  lots of freezes.

So these things were working without issue previously, before you did an update?  

> **wicki said:**
> this hapend before each time it seams to be after installing OS updates.

So you fix it, then do an update and it breaks things every time you do an update? How are you updating? Sorry, it's not real clear. Please give some clarity. ;)

Open a terminal and paste these commands one at a time, hitting enter after each. You will be asked for your password. it will be invisible. This is normal.
```

sudo apt update
sudo apt full-upgrade
```

If it throws errors, please post them here between code tags (see link in my signature for how).

---

### Post by wicki on 2017-06-05
Hi 

I downloaded 16.04 lts i dont have a "Flavour"

I run Libre office it has everything i need also Gimp and Darktable.

Twice now after installing OS updates I have lost printing, printer is HP 3050  after a lot of research and probably making things worse through my ignorance  i reinstalled ubuntu and lost all my files,

I am updating through the software center.

pc is a dell xps420 it is very old s maybe thats the problem but money is tight so i dont want to throw it out the hardware is ok.

graphics is an old Nvidia 550gtx.

and yes all worked fine before the updates then like a fool i see "OS updates security and stability bla bla bla" i install and it all goes messed up.

---

### Post by yancek on 2017-06-05
The problems you are experiencing are often the result of failing hardware or an operating system which is too "heavy" for your hardware.  The second option seems more likely in your case.  Did you check the Ubuntu site for the minimum hardware requirements?  Old is a relative term, when was it manufactured would be more useful but I think a better option for you would be to switch to LUBUNTU rather than Ubuntu and the Unity Desktop.

---

### Post by QIII on 2017-06-05
Breakage occuring consistently after updates, particularly kernel updates, often points to the use of drivers (graphics generally) installed from outside the official repositories.

Have you installed your Nvidia driver from Nvidia or a third party source?

We are asking a lot of questions to gather info to make a diagnosis, not to be belligerent or belittling

---

### Post by wicki on 2017-06-06
Hi 

Yes I have installed the Nvidia driver i find the system totally unstable under the other drivers using chromium browser it just freezez and locks all the time.

The system is 2009/10 I know its old but I have no money and was hoping it would do until the business makes its firs sale the printer is also 2010.

If the system is not up to the job then I will try to afford a second hand thinkpad I must have a PC the job is totaly PC dependant.

Output of *sudo lshw -short*
```
H/W path                 Device           Class       Description
=================================================================
                                          system      Dell XPS420
/0                                        bus         0TP406
/0/0                                      memory      64KiB BIOS
/0/400                                    processor   Intel(R) Core(TM)2 Quad CP
/0/400/700                                memory      32KiB L1 cache
/0/400/701                                memory      8MiB L2 cache
/0/1000                                   memory      4GiB System Memory
/0/1000/0                                 memory      1GiB DIMM DDR2 Synchronous
/0/1000/1                                 memory      1GiB DIMM DDR2 Synchronous
/0/1000/2                                 memory      1GiB DIMM DDR2 Synchronous
/0/1000/3                                 memory      1GiB DIMM DDR2 Synchronous
/0/100                                    bridge      82X38/X48 Express DRAM Con
/0/100/1                                  bridge      82X38/X48 Express Host-Pri
/0/100/1/0                                display     GF116 [GeForce GTX 550 Ti]
/0/100/1/0.1                              multimedia  GF116 High Definition Audi
/0/100/6                                  bridge      82X38/X48 Express Host-Sec
/0/100/19                enp0s25          network     82566DC-2 Gigabit Network 
/0/100/1a                                 bus         82801I (ICH9 Family) USB U
/0/100/1a/1              usb3             bus         UHCI Host Controller
/0/100/1a.1                               bus         82801I (ICH9 Family) USB U
/0/100/1a.1/1            usb4             bus         UHCI Host Controller
/0/100/1a.2                               bus         82801I (ICH9 Family) USB U
/0/100/1a.2/1            usb5             bus         UHCI Host Controller
/0/100/1a.7                               bus         82801I (ICH9 Family) USB2 
/0/100/1a.7/1            usb1             bus         EHCI Host Controller
/0/100/1a.7/1/2          wlx001349906e16  network     ZyXEL G-202
/0/100/1a.7/1/6                           generic     XPS MiniView
/0/100/1b                                 multimedia  82801I (ICH9 Family) HD Au
/0/100/1c                                 bridge      82801I (ICH9 Family) PCI E
/0/100/1d                                 bus         82801I (ICH9 Family) USB U
/0/100/1d/1              usb6             bus         UHCI Host Controller
/0/100/1d.1                               bus         82801I (ICH9 Family) USB U
/0/100/1d.1/1            usb7             bus         UHCI Host Controller
/0/100/1d.1/1/2                           input       USB Keyboard
/0/100/1d.2                               bus         82801I (ICH9 Family) USB U
/0/100/1d.2/1            usb8             bus         UHCI Host Controller
/0/100/1d.2/1/1                           input       USB Optical Mouse
/0/100/1d.7                               bus         82801I (ICH9 Family) USB2 
/0/100/1d.7/1            usb2             bus         EHCI Host Controller
/0/100/1d.7/1/2          scsi6            storage     CA-200
/0/100/1d.7/1/2/0.0.0    /dev/sdb         disk        USB   HS-CF Card
/0/100/1d.7/1/2/0.0.0/0  /dev/sdb         disk        
/0/100/1d.7/1/2/0.0.1    /dev/sdc         disk        USB   HS-xD/SM
/0/100/1d.7/1/2/0.0.1/0  /dev/sdc         disk        
/0/100/1d.7/1/2/0.0.2    /dev/sdd         disk        USB   HS-MS Card
/0/100/1d.7/1/2/0.0.2/0  /dev/sdd         disk        
/0/100/1d.7/1/2/0.0.3    /dev/sde         disk        USB   HS-SD Card
/0/100/1d.7/1/2/0.0.3/0  /dev/sde         disk        
/0/100/1d.7/1/3                           printer     Deskjet 3050 J610 series
/0/100/1d.7/1/6                           multimedia  Webcam C270
/0/100/1e                                 bridge      82801 PCI Bridge
/0/100/1f                                 bridge      82801IR (ICH9R) LPC Interf
/0/100/1f.2                               storage     SATA Controller [RAID mode
/0/100/1f.3                               bus         82801I (ICH9 Family) SMBus
/0/1                     scsi0            storage     
/0/1/0.0.0               /dev/sda         disk        500GB WDC WD5000AAKS-7
/0/1/0.0.0/1             /dev/sda1        volume      461GiB EXT4 volume
/0/1/0.0.0/2             /dev/sda2        volume      4028MiB Extended partition
/0/1/0.0.0/2/5           /dev/sda5        volume      4028MiB Linux swap / Solar
/0/2                     scsi1            storage     
/0/2/0.0.0               /dev/cdrom       disk        DVD+-RW AD-5170S
alec@alec-Dell-XPS420:~$ 



```

does this help ?

PS: thank you very much ! ask as many questions as you want free help is very much appreciated:)

---

### Post by Bucky Ball on 2017-06-06
Where did you install the NVidia driver from? Third-party (the NVidia site or somewhere else other than Additional Drivers)? Additional Drivers is the place to start. The recommended driver should be there for your card.

---

### Post by wicki on 2017-06-06
> **Bucky Ball said:**
> Where did you install the NVidia driver from? Third-party (the NVidia site or somewhere else other than Additional Drivers)? Additional Drivers is the place to start. The recommended driver should be there for your card.

Yes from additional drivers

---

### Post by HermanAB on 2017-06-07
Most Linux issues are due to finger trouble.  If the machine is working properly, then an update can only make it the same, or worse, it cannot make it better...

So, in general, once you got it working, it is best to only do security updates once in a blue moon, until you are more familiar with everything and don't do feature updates at all, since those can change the system behaviour, look and feel and leave you scratching your head.

---

### Post by wicki on 2017-06-07
Ok Herman that sounds like good advice.

---

### Post by Topsiho on 2017-06-08
Just an idea: when updating, a lot of update files are downloaded, which remain on the computer after use. Same with updating the kernels.
This goes on until there is not room enough anymore, resulting in an unresponsive system.

So, you could try, in a terminal:

sudo apt clean

and enter your password when asked. This clears all the update files that are not of any use anymore

Then you enter:

sudo apt autoremove

which removes all kernel images except for those of the last two kernels (always saving one kernel extra for just in case).

This might clear a lot  of gigabytes of disk space, and get your computer on it's rails again :)

Topsiho

---

### Post by mörgæs on 2017-06-09
> **HermanAB said:**
> Most Linux issues are due to finger trouble.  If the machine is working properly, then an update can only make it the same, or worse, it cannot make it better...

So, in general, once you got it working, it is best to only do security updates once in a blue moon...


These repeat postings about ignoring security updates are getting a little ... tiresome. 

By default Buntu checks for security updates daily which is the way it should be. If you have a compelling reason to think this is wrong then I think you ought to send Canonical a line asking for it to be changed; don't mislead new users.

**@wicki**, all operative systems need security updates without delay. One of the reasons that GNU/Linux is safer than other operative systems is that the developers begin bug fixing right away if an important security bug is reported, and often only a few days pass before a patch is delivered. 

The [security notices]("https://www.ubuntu.com/usn/") show how fast bugs fixes are made available. Failing to appreciate the gift that someone offers this kind of system hardening is asking for trouble. No operative system is complete at the day of release and updates can only make it safer.

---

### Post by DougieFresh4U on 2017-06-09
Also please don't do 'partial updates' as that can 'bork' your system

---

### Post by mörgæs on 2017-06-09
I have only seen partial updates in the development version but yes, if they appear then better to let them pass and check again the next day.

---

