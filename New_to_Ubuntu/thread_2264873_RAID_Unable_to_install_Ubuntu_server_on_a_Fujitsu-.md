---
title: "RAID: Unable to install Ubuntu server on a Fujitsu-Siemens Rx100 first gen"
date: 2015-02-10
forum: New to Ubuntu
---

### Post by rhaf on 2015-02-10
Hi folks,

I am pretty new to Linux in general, but still I hope you you will be able to help me solve an issue that is really frustrating.

I would like to install Ubuntu Server 14 on a Fujitsu-Siemens RX100 Gen1 server HW unit.

Specs:
Intel® Pentium® 4 processor with up to 
2.66 GHz and 533 MHz FSB, or Intel® 
Celeron® with 2.0 GHz and 400 MHz FSB 
ƒ Up to 3 Gbyte ECC protected DDR-SDRAM 
memory 
ƒ Onboard 2-channel IDE controller with 
RAID-0/1 functionality for striping and 
mirroring of the hard disks 
ƒ Max. 240 Gbyte internal hard disk 
capacity with up to 2 hard disks (IDE) 
ƒ 2 free PCI slots, 64-bit / 33 MHz 
ƒ Onboard 1 Gbit and 10/100 Mbit Ethernet 
LAN controller 
ƒ [http://www.erkawe.be/hardware/datasheet/primergy-rx100.pdf](http://www.erkawe.be/hardware/datasheet/primergy-rx100.pdf)



Every time i try to install this system it fails.
I believe the main problem is the Onboard 2-channel IDE controller. It is a Fasttrak controller based on a Promise 20270 chipset.
This SATA raid environment is not recognised and therefor there is nowhere for Linux to install.

Surely there must be a way to install this system with Ubuntu?  Eventually I would like to use it as a webserver.

All help is much appreciated.

Regards

---

### Post by mörgæs on 2015-02-11
Are you able to disable RAID in BIOS?

---

### Post by rhaf on 2015-02-11
Yes, but then it would seem that Linux sees no disks?

Do I then need to use some special install settings etc?

Thanks

---

### Post by mörgæs on 2015-02-12
Don't disable the hard drives completely, just see if there's an option to disable the RAID part, separating the drives.

I am wondering that you might have [Fake RAID]("http://skrypuch.com/raid/").

---

### Post by nerdtron on 2015-02-12
Some systems won't let you disable RAID completely. If you want to use JBOD (Just a bunch of Disk), either you select JBOD from the RAID controller or you set each of the drives as individual RAID 0 disks.

---

### Post by SeijiSensei on 2015-02-12
My first suggestion would be to try and install [CentOS]("http://www.centos.org/") on the machine rather than Ubuntu.  CentOS has better support out-of-the-box for RAID controllers since it's a RedHat derivative designed to run on servers.  I prefer Ubuntu on desktops, but RedHat or CentOS on servers.

---

### Post by rhaf on 2015-02-12
Hi SeijiSensei, I did have the same thought so I did try CentOS, but that got stuck even sooner.
Somewhere I read that sofar only SuSE enterprise was the only linux version to install without an issue, but they didn't explain why.

Anyhow, in the Bios I can choose to Disable Onboard Raid
Then under boot devices I get the option Boot from Harddisk -> 1st = Other 2nd = E-IDE (Options are grayed out)
Under 1st = Other there are two sub options:
Legacy PCI SCSI
Promise IDE Raid

I did find this on the Fujitsu site under RedHat:


[http://support.ts.fujitsu.com/Download/Showdescription.asp?SoftwareGUID=1DDFB39E-6A6A-4848-9498-DCF0DEE09E5C](http://support.ts.fujitsu.com/Download/Showdescription.asp?SoftwareGUID=1DDFB39E-6A6A-4848-9498-DCF0DEE09E5C)


But I have no idea what this means. 


All I get on screen is Found Something at drive - 80
Bootlogo


BLACK SCREEN

---

### Post by rhaf on 2015-02-14
Ok, i got a little further...

Up until now I had been trying to install Ubuntu Server Ubuntu 14.10 (Utopic Unicorn).

I have started installing Ubuntu 14.04.1 LTS (Trusty Tahr). This versions guides me through the whole process up to the point where I need to indicate on what drives to install.  I did see a message that spmething with ATA Raid had been found, but I pressed enter a little to fast to read the exact question.
I am then presented a screen requiring me to indicate which drive(s) I want to use and it shows an iSCSI option, an empty line, a line to effect changes to partitioning and a line for finish.  Unfortunately, I can still not see my real disk ....


+++ UPDATE +++
Ok left RAID in system bios ON
CTRL-F into Promise Fasttrak and deleted all array info.
Rebooted with single drive connected to motherboard
Ubuntu now finds the single disk.


Will now try to see whether I can get two drives to work as a raid set spanning the capacity.

---

### Post by rhaf on 2015-02-15
Well folks, it seems to have worked.
Basically set up a two disk ide span in the Promise tool (Ctrl-F)
And with Ubuntu 14.04 all was found and installed without any more problems.

I now have a Joomla 3.3.6 webserver running.

Thanks for your help.

---

### Post by mörgæs on 2015-02-15
Good, please mark the thread 'solved'.

---

