---
title: "Problems with installation"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Crabcalf on 2008-05-18
Today I downloaded 8.04, and burned it into a CD.  I have checked the CD, and it is fine.  I intended to install Ubuntu onto a spare hard drive, which has been formatted previously by Windows.  I did this by disconnecting my other drives, just to be on the safe side, and setting the computer to boot up from the CD drive.  I get a screen asking me to select a language, and than a screen of options for installation.  

I selected 'Normal Install', and then got the Ubuntu loading screen.  But when the loading finishes, the computer automatically reboots, and eventually ends up on the screen asking to select a language.  The process just continues in a gigantic loop.  I have tried various other ways of installing, including the installation as a demo, but the same thing happens every time.

I am completely ignorant of Linux and Ubuntu, so I am aware that I might have done something wrong.  Any help would be appreciated.

---

### Post by overdrank on 2008-05-18
> **Crabcalf said:**
> Today I downloaded 8.04, and burned it into a CD.  I have checked the CD, and it is fine.  I intended to install Ubuntu onto a spare hard drive, which has been formatted previously by Windows.  I did this by disconnecting my other drives, just to be on the safe side, and setting the computer to boot up from the CD drive.  I get a screen asking me to select a language, and than a screen of options for installation.  

I selected 'Normal Install', and then got the Ubuntu loading screen.  But when the loading finishes, the computer automatically reboots, and eventually ends up on the screen asking to select a language.  The process just continues in a gigantic loop.  I have tried various other ways of installing, including the installation as a demo, but the same thing happens every time.

I am completely ignorant of Linux and Ubuntu, so I am aware that I might have done something wrong.  Any help would be appreciated.

Hi and welcome, the first thing that comes to mind is the jumpers on the drive if is was set to slave that may cause a issue. But the live cd should still boot and run the live session. you may want to do a checksum 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Patb on 2008-05-18
Crab, does your bios recognise your "spare hard drive"?.  During boot-up, go into the bios menu and see if there is a way to check that it does.  

If this or Overdrank's advice works, please mark the thread solved.  If it doesn't, post again with what you have found.  

Cheers, Pat.

---

### Post by Crabcalf on 2008-05-18
> **overdrank said:**
> Hi and welcome, the first thing that comes to mind is the jumpers on the drive if is was set to slave that may cause a issue. But the live cd should still boot and run the live session. you may want to do a checksum 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Ok - yes, the drive might well be a slave.  If that is a problem, then I won't be able to load Ubuntu at all.

So far as the checksum is concerned, I have a log on the CD which gives a pageful of checksums for what appear to be many of the files on the CD.  It would take hours, literally, to compare these with checksums on a website.  Is there a particular file on the CD that I should be checking?  I haven't yet been able to find a likely candidate, especially as the names are not particularly helpful.

---

### Post by Crabcalf on 2008-05-18
> **Patb said:**
> Crab, does your bios recognise your "spare hard drive"?.  During boot-up, go into the bios menu and see if there is a way to check that it does.  

If this or Overdrank's advice works, please mark the thread solved.  If it doesn't, post again with what you have found.  

Cheers, Pat.

Yes, the drive is recognised by the BIOS and by Windows.

---

### Post by overdrank on 2008-05-18
> **Crabcalf said:**
> Ok - yes, the drive might well be a slave.  If that is a problem, then I won't be able to load Ubuntu at all.

So far as the checksum is concerned, I have a log on the CD which gives a pageful of checksums for what appear to be many of the files on the CD.  It would take hours, literally, to compare these with checksums on a website.  Is there a particular file on the CD that I should be checking?  I haven't yet been able to find a likely candidate, especially as the names are not particularly helpful.

Maybe here 
[https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24](https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24)

---

### Post by Crabcalf on 2008-05-18
> **overdrank said:**
> Maybe here 
[https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24](https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24)

That particular file, nor anything like it, is on the CD.  

I would have liked to have tried out another operating system, but it looks as though this isn't going to work.  :(

---

### Post by overdrank on 2008-05-18
> **Crabcalf said:**
> That particular file, nor anything like it, is on the CD.  

I would have liked to have tried out another operating system, but it looks as though this isn't going to work.  :(

Hi and I am at a loss, did you burn the cd as a iso 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Patb on 2008-05-19
> **Crabcalf said:**
> ... I have checked the CD, and it is fine.  
I assume you mean you chose the "Check CD for defects" option and that it went through that process and gave you an "all OK" or whatever at the end.  

If that is correct, I don't think you need to do anything further regarding md5sums because that process checks the md5sums of a whole range of files on the CD (Please correct me if I'm wrong, Overdrank).  It also indicates that your system can read the CD okay because it uses it to boot up a minimal operating system to perform the md5sums.  

So sorry to ramble but I'm at a loss too.  It might be worth trying to install from an alternate CD but that might be a bit tedious for a beginner.  Sorry I can't be more help.  
> 
I might have done something wrong.
Not evident from anything you have posted here.  But something interesting just might come up if you post your basic computer specs. 

Cheers, Pat.

---

### Post by rockerphil on 2008-05-19
ok, here's my advice, pull the hard drive you're attempting to install Ubuntu on to and look for the switch on the back, there's gonna be a few options, you want to set it to M for Master and connect it to your main hard drive slot. cus it sounds like you're trying to install it as a Slave drive running through one of your alternative drive connections. hopefully this will do it, if not then just reconnect all your other drives as normal and when the installer comes to the option where you choose what drive to install to just make sure it's instlaling and partitioning to the drive you want. hope this helps

---

### Post by Crabcalf on 2008-05-19
> **overdrank said:**
> Hi and I am at a loss, did you burn the cd as a iso 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Not sure what an ISO is, but the burn was made by Nero.

---

### Post by Crabcalf on 2008-05-19
> **Patb said:**
> I assume you mean you chose the "Check CD for defects" option and that it went through that process and gave you an "all OK" or whatever at the end.  



Not evident from anything you have posted here.  But something interesting just might come up if you post your basic computer specs. 

Cheers, Pat.

Yes, that is correct.

Here are the computer specs.  A bit long, I'm afraid, but I am not sure what to leave out.

Processor
Model : Intel(R) Pentium(R) 4 CPU 2.60GHz
Speed : 2.60GHz
Performance Rating : PR3458 (estimated)
Cores per Processor : 1 Unit(s)
Threads per Core : 2 Unit(s)
Internal Data Cache : 8kB Synchronous, Write-Thru, 4-way set, 64 byte line size, 2 lines per sector
L2 On-board Cache : 512kB ECC Synchronous, ATC, 8-way set, 64 byte line size, 2 lines per sector

Mainboard
Bus(es) : ISA AGP PCI IMB USB FireWire/1394 i2c/SMBus
MP Support : 1 Processor(s)
MP APIC : Yes
System BIOS : American Megatrends Inc. V2.4
System : MICRO-STAR INC. MS-6758
Mainboard : MICRO-STAR INC. MS-6758
Total Memory : 2GB DDR-SDRAM

Chipset 1
Model : Micro-Star International Co Ltd (MSI) 82875P,E7210 Memory Controller Hub
Front Side Bus Speed : 4x 200MHz (800MHz data rate)
Total Memory : 2GB DDR-SDRAM
Memory Bus Speed : 2x 166MHz (332MHz data rate)

Video System
Monitor/Panel : Plug and Play Monitor
Adapter : NVIDIA GeForce 6800 GS/XT
Imaging Device : USB2.0 PC Camera (SN9C201)

Physical Storage Devices
Removable Drive : Floppy disk drive
Hard Disk : Maxtor 6Y120L0 (114GB)
Hard Disk : Maxtor 6Y120M0 (114GB)
Hard Disk : MAXTOR STM3250820A (233GB)
CD-ROM/DVD : HL-DT-ST CD-ROM GCR-8523B (CD 52X Rd)
CD-ROM/DVD : HP DVD Writer 1040r (CD 48X Rd, 48X Wr) (DVD 6X Rd, 6X Wr)

Logical Storage Devices
Hard Disk (C:) : 233GB (7.1GB, 3% Free Space) (NTFS)
Local Disk (E:) : 114GB (29GB, 26% Free Space) (NTFS)
Ubuntu (D:) : 114GB (114GB, 100% Free Space) (NTFS)
Ubuntu 8.04 i386 (G:) : 699MB (CDFS)
CD-ROM/DVD (F:) : N/A
3.5" 1.44MB (A:) : N/A

Peripherals
Serial/Parallel Port(s) : 4 COM / 1 LPT
USB Controller/Hub : VIA Rev 5 or later USB Universal Host Controller
USB Controller/Hub : VIA Rev 5 or later USB Universal Host Controller
USB Controller/Hub : Standard Enhanced PCI to USB Host Controller
USB Controller/Hub : Standard Universal PCI to USB Host Controller
USB Controller/Hub : Standard Universal PCI to USB Host Controller
USB Controller/Hub : Standard Universal PCI to USB Host Controller
USB Controller/Hub : Standard Enhanced PCI to USB Host Controller
USB Controller/Hub : Standard Universal PCI to USB Host Controller
USB Controller/Hub : USB Root Hub
USB Controller/Hub : USB Root Hub
USB Controller/Hub : USB Root Hub
USB Controller/Hub : USB Root Hub
USB Controller/Hub : USB Root Hub
USB Controller/Hub : USB Root Hub
USB Controller/Hub : USB Root Hub
USB Controller/Hub : USB Root Hub
USB Controller/Hub : Unknown Device
USB Controller/Hub : Generic USB Hub
USB Controller/Hub : USB Composite Device
USB Controller/Hub : Generic USB Hub
USB Controller/Hub : Generic USB Hub
USB Controller/Hub : Generic USB Hub
FireWire/1394 Controller/Hub : OHCI Compliant IEEE 1394 Host Controller
FireWire/1394 Controller/Hub : VIA OHCI Compliant IEEE 1394 Host Controller
Keyboard : PS/2 Keyboard
Mouse : Logitech HID-compliant Cordless Mouse
Human Interface : HID-compliant consumer control device
Human Interface : HID-compliant device
Human Interface : HID-compliant device
Human Interface : Bluetooth HID Enum Device
Human Interface : USB Human Interface Device
Human Interface : USB Human Interface Device

MultiMedia Device(s)
Device : Creative SB Audigy 2 ZS (WDM)
Device : Creative Game Port

Communication Device(s)
Device : Bluetooth Fax Modem
Device : Bluetooth DUN Modem
Device : Bluetooth LAP Modem
Device : Bluetooth LAP Modem #2

Printers and Faxes
Model : hp LaserJet 1005 DOS
Model : hp LaserJet 1005

Power Management
AC Line Status : On-Line

Operating System(s)
Windows System : Microsoft Windows XP/2002 Home 5.01.2600 (Service Pack 2)

Network Services
Adapter : Realtek RTL8139 Family PCI Fast Ethernet NIC #2

---

### Post by Crabcalf on 2008-05-19
> **rockerphil said:**
> ok, here's my advice, pull the hard drive you're attempting to install Ubuntu on to and look for the switch on the back, there's gonna be a few options, you want to set it to M for Master and connect it to your main hard drive slot. cus it sounds like you're trying to install it as a Slave drive running through one of your alternative drive connections. hopefully this will do it, if not then just reconnect all your other drives as normal and when the installer comes to the option where you choose what drive to install to just make sure it's instlaling and partitioning to the drive you want. hope this helps

Yes, good point.  That was something I hadn't considered.  But in fact the drive is set up as a Master.  And indeed, when I run the CD, it doesn't even get to the point of accessing the drives; it just loads, and then reboots the computer.

---

### Post by overdrank on 2008-05-19
> **Patb said:**
> I assume you mean you chose the "Check CD for defects" option and that it went through that process and gave you an "all OK" or whatever at the end.  

If that is correct, I don't think you need to do anything further regarding md5sums because that process checks the md5sums of a whole range of files on the CD (Please correct me if I'm wrong, Overdrank).  It also indicates that your system can read the CD okay because it uses it to boot up a minimal operating system to perform the md5sums.  



You maybe correct Patb, I have had user's report that the cd returned no errors but the MD5SUM did not match on the iso. As for me I have had errors on cd's and the MD5SUM did not match. This is the why I just suggested checking to rule out. ANd to the op the cd should run on the system even with no hard drives in place. Good luck

---

### Post by elord on 2008-05-19
Is this problem solve already..? i have same problem in installing Ubuntu 8.04 since it's in ISO format already when i boot it in CD it can't detect.. Is there any problem in my Software?

---

