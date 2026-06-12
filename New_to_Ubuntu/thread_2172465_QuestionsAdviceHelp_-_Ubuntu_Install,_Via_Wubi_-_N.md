---
title: "Questions/Advice/Help - Ubuntu Install, Via Wubi - New Windows 8 Preinstall"
date: 2013-09-05
forum: New to Ubuntu
---

### Post by balkrish999 on 2013-09-05
Hello, I have a Windows 8 Pre installed, Laptop- It has that UIFE Secure boot trash.   

1) Since it has UEFI,  If i use WUBI installer, will i need to Disable it?/ will it cause conflict?

2) I will also be dual booting Windows 7 to this laptop,  and hopefully have W8,7 and Wubi Ubunut.  - Question is that, Do you recogmened to Dual boot W7 and 8 FIRST Then Wubi,   or Wubi and W8  THEN 7?


Thank You. :)

---

### Post by newb85 on 2013-09-05
I haven't dual-booted Windows or used Wubi, but given that Wubi adds an entry for Ubuntu to the Windows bootloader, my fear would be that adding W7 after Wubi might remove this entry.  But as I said, I'm not speaking from direct experience.

I generally recommend using Live media to do a traditional install of Ubuntu on a dedicated Ext* partition because troubleshooting is usually easier.

---

### Post by Impavidus on 2013-09-05
I never tried it myself (never having user Win8, Win7 or wubi), but I've read wubi doesn't work well with Win8, UEFI, GPT partitioning and that kind of things. Wubi is being phased out for that reason. I generally recommend traditional dual boots. Its easiest to install Ubuntu last, but when installing your windowses, leave some unallocated space on your drive large enough to install Ubuntu.

---

### Post by TheFu on 2013-09-05
Start by reading this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I would avoid WUBI - never use it.
If you want to avoid the entire UEFI issue, just load up virtualbox and load Ubuntu inside a VM. You won't be playing games and it is best to avoid Unity, but it works great with the right DE - desktop environment, provided you make the best virtual machine setup. There are lots of VBox tuning how-tos on the internet. I'm partial to my own.

---

### Post by balkrish999 on 2013-09-05
> **Impavidus said:**
> I never tried it myself (never having user Win8, Win7 or wubi), but I've read wubi doesn't work well with Win8, UEFI, GPT partitioning and that kind of things. Wubi is being phased out for that reason. I generally recommend traditional dual boots. Its easiest to install Ubuntu last, but when installing your windowses, leave some unallocated space on your drive large enough to install Ubuntu.


I see, ..... Those bloddy *******   Well that sucks, stupid W8 and Stupid UEFI.  I was hoping to use Wubi, the main problem why i cant install it on a another partion is , my laptop came with 5 pre install  (3 recovery) :(

Crap...... Will see what happens,

---

### Post by TheFu on 2013-09-05
> **balkrish999 said:**
> I see, ..... Those bloddy *******   Well that sucks, stupid W8 and Stupid UEFI.  I was hoping to use Wubi, the main problem why i cant install it on a another partion is , my laptop came with 5 pre install  (3 recovery) :(

Crap...... Will see what happens,

Virtualbox.  Your machine is fast enough and has plenty of RAM.  In 30 minutes, you could be done. It is fairly painless.
Use Ubuntu 12.04.3 from an ISO file and follow these settings: [http://www.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://www.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

---

### Post by newb85 on 2013-09-05
> **balkrish999 said:**
> I see, ..... Those bloddy *******   Well that sucks, stupid W8 and Stupid UEFI.  I was hoping to use Wubi, the main problem why i cant install it on a another partion is , my laptop came with 5 pre install  (3 recovery) :(

Crap...... Will see what happens,

If your machine has UEFI (GPT partitioning), the number of existing partitions shouldn't matter, since you're not limited like you would be with MBR (which limits to 4 primary partitions).

---

### Post by Jonathan Precise on 2013-09-05
> **balkrish999 said:**
> I see, ..... Those bloddy *******   Well that sucks, stupid W8 and Stupid UEFI.  I was hoping to use Wubi, the main problem why i cant install it on a another partion is , my laptop came with 5 pre install  (3 recovery) :(

Crap...... Will see what happens,

Use the windows partitioning tool to re-size the windows partition. Then boot to a live DVD of the latest ubuntu version (13.04 64-bit), and use the "Something Else" option in partitioning. Make an "ext4" partition with mount-point as "/" (make it occupy _**MOST**_ of the free space_**,**_ but _**NOT ALL!!!!!!!**_). On the remaining free space, make a "swap" partition (no mount point). Then click install. As mentioned, UEFI uses GPT partitioning, which odes not have the limitation of having only 4 partitions, as in MBR partitioning.

I recommend you _**NOT USE THE GPARTED PARTITION EDITOR OR THE UBUNTU PARTITIONER **_**(based on GParted)**_**, AS IT CAN CAUSE WINDOWS TO NOT BOOT AT ALL!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!**_

Also, use Boot-repair found in Linux Secure Remix, as a bug in "os-prober" (the one that looks for other OS's) puts the wrong windows entries (based on the BIOS entries). Boot-repair will fix it.

(What is about to come is just a boring explanation of why _**WUBI does NOT work with UEFI**_. Feel free to skip this.) Wubi places a file called root.disk inside a folder called ubuntu in your C drive (or whatever drive you choose during the installation). This also places a file (in your drive) called wubildr.mbr. MBR is used by traditional BIOS computers (and what the UEFI legacy-support module does, also called CSM). UEFI looks for EFI files. For example, grubx64.efi, shimx64.efi. MBR is not supported unless you activate legacy or CSM (which does not look at EFI files).

---

### Post by balkrish999 on 2013-09-05
> **TheFu said:**
> Virtualbox.  Your machine is fast enough and has plenty of RAM.  In 30 minutes, you could be done. It is fairly painless.
Use Ubuntu 12.04.3 from an ISO file and follow t[rtualbox]("http://www.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox")

No,Virtual Machine is definitely NO. I want the full thing

> **newb85 said:**
> If your machine has UEFI (GPT partitioning), the number of existing partitions shouldn't matter, since you're not limited like you would be with MBR (which limits to 4 primary partitions).

Umm, didnt know this, Thank You

> **Jonathan Precise said:**
> Use the windows partitioning tool to re-size the windows partition. Then boot to a live DVD of the latest ubuntu version (13.04 64-bit), and use the "Something Else" option in partitioninuring the installation). This also places a file (in your drive) called wubildr.mbr. MBR is used by traditional BIOS computers (and what the UEFI legacy-support module does, also called CSM). UEFI looks for EFI files. For example, grubx64.efi, shimx64.efi. MBR is not supported unless you activate legacy or CSM (which does not look at EFI files).


Okay, Thank you for that,     Could i do this,  Put, Windows 7 dual boot with 8 pre install,     Then run Wubi FROM 7?    I used, Wubi on my previous desktop, and two laptops and it worked perfectly. 


Thank You

---

### Post by oldfred on 2013-09-05
Most Windows 7 system are BIOS based and you have to convert it to be a UEFI installer. I have not done this but have these links.
       Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

More info on UEFI in my signature.

Windows 7 also will not work with secure boot. Also a few Windows 8 systems will only boot with secure boot on. Hope you have one that boots Windows 8 with secure boot off. 
Do not install Ubuntu or Windows 7 in CSM/BIOS mode as it is very difficult to dual boot. You have to go into UEFI/BIOS and turn on or off CSM to boot one system or the other.

Also make sure fast boot is off in Windows 8 as it is an issue booting any other system not just dual booting Windows & Ubuntu.
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by Jonathan Precise on 2013-09-05
> **balkrish999 said:**
> Okay, Thank you for that,     Could i do this,  Put, Windows 7 dual boot with 8 pre install,     Then run Wubi FROM 7?    I used, Wubi on my previous desktop, and two laptops and it worked perfectly. 

Thank You

Do **_NOT USE WUBI WITH UEFI EVER, EVEN IF IT HAS WINDOWS 7!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! THIS WILL CAUSE ERRORS WITH BOOTING!!!!!!!!!!_**:!: Install windows 7 first (disable secure-boot). Then install ubuntu with the instructions I posted. Then run Boot-repair's "Recommended repair". Note the address (example *pastebin.ubuntu.com/whatever*). If it works, mark this thread as solved. If not, give us the link and anything that the result gives.

---

### Post by TheFu on 2013-09-05
> **balkrish999 said:**
> Okay, Thank you for that,     Could i do this,  Put, Windows 7 dual boot with 8 pre install,     Then run Wubi FROM 7?    I used, Wubi on my previous desktop, and two laptops and it worked perfectly. 

Anyone else think this is making it too hard?  

WUBI is to be avoided unless there absolutely is not any other choice. I beleive this is a common opinion from the gurus here.  The OP can dual boot and run ubuntu under UEFI. After the install, nobody will notice the UEFI, right?  Just disable secure boot, create partitions under Windows to hold Ubuntu, then do the install.

Is there some reason the OP is trying to avoid this? 

Did prior dual boot attempts on this exact hardware fail?

I should say that I don't dual boot much - just a netbook. All my other machines boot Linux and use virtualization. Virtualization works well enough that my daily desktop runs in a VM inside a "private cloud."

---

### Post by kurt18947 on 2013-09-05
> **balkrish999 said:**
> No,Virtual Machine is definitely NO. I want the full thing



Umm, didnt know this, Thank You




Okay, Thank you for that,     Could i do this,  Put, Windows 7 dual boot with 8 pre install,     Then run Wubi FROM 7?    I used, Wubi on my previous desktop, and two laptops and it worked perfectly. 


Thank You

A very quick search about UEFI says you can have 128 partitions.  That should last a while :D.  I couldn't find anything about how many operating systems can be installed but if there's support for that many partitions, I'd think you should be able to have at least a couple dozen operating systems without trying to fit one inside another like WUBI does.  Though I have no experience with UEFI, I'm using a 3rd party boot manager that offers some of the benefits of UEFI.  It's nice to be able to run each O.S. like it's the only one installed.

---

### Post by oldfred on 2013-09-05
The issue with wubi is not Windows 8, nor UEFI per se. But with gpt partitioning which UEFI has as default and Windows 8 uses.

       Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)
[http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)

---

