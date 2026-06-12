---
title: "BusyBox and Initramfs- All help appreciated"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by DanceTheTango on 2008-10-26
Hello all,

I am VERY new to the world of Ubuntu, and would appreciate it if all responses were in simple, newbie language. I have read quite a few threads about this topic, but once people start inserting random letters and whole lines of strange code, I'm lost. Please be gentle! Thanks :-) 

I have just purchased a new computer with the following specifications:

- CPU: Intel Core 2 Quad Q9400 2.66GHz/6MB/FSB1333/LGA775
- MB: GA-EP45-DS4 S775 P45 FSB1600 DDR2 2xPCIEx16 SATA2 3x1394a 2xGBLAN ATX
- RAM: Kingston 4GB HYPERX 1066Mhz (PC2-8500) DDR2 CL5 (x 2 equal to 8GB)
- HDD: Seagate 500GB SATA 7200RPM 32MB ST3500320AS (x 2 equal to 1TB)
- Graphics: MSI N9600GT 512M DDR3 2xDVI-I HDMI HDTV PCI-E VGA

I have downloaded Ubuntu 8.04, burnt it to a DVD, and have reached the point on my new computer where I have selected my language and chosen to Install. It then freezes on the following: 

BusyBox v1.1.3 (debian 1:1.1.3-Subuntu12) Built-in Shell (ash)
Enter 'help' for a list of commands

(initramfs) _ 

I have taken out/reinserted the DVD, turned the computer on and off, and pulled the power.

I have no idea where to go from here, and none of the other threads have been of help due to the technical 
complexity in the answers. I'm hoping someone out there has the patience to help me out!

Thanks so much.

---

### Post by louieb on 2008-10-26
1st thing is to check the CD for defects. It just takes a few twisted bit to give weird results.

Check for a good download download  [HowToMD5SUM - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowToMD5SUM")

Burn to disk slow I use 2X - no faster that  4 x.

Select the check media for defects option.

---

### Post by DanceTheTango on 2008-10-26
Thanks for that. I'm trying both options now. Any other ideas are always appreciated!

---

### Post by DanceTheTango on 2008-10-26
Ok- I've run the MD5 check and the sums are equal.

When I initially burnt the disk, I did it at 8x and I verified contents. Should I be burning it again at 2x anyway?

Thanks!

---

### Post by epidemiks on 2008-10-26
there's some epic threads floating about regarding this error.
what worked for me was the boot options "all_generic_ide irqpoll floppy=off"

try booting to the live desktop with those options. I think it's F4 or F6 to add boot options

---

### Post by louieb on 2008-10-26
Usually the busy box prompt shows up  before you can start the install. Its just a generic catch all. All its telling you is I can't continue and I can't tell you why.  

If it passed the media check then shouldn't have to burn another. But it won't hurt either. 

Does this PC have an OS currently installed? 

Just wondering if the hard drives are being detected. For a quick check 

Boot to the live CD desktop. Open system>administration>partition editor. click the drop down in the upper right corner and see if both drives are listed.

others like **epidemiks**  will probably tell what work for them.

---

### Post by DanceTheTango on 2008-10-26
Ok!

I have re-burnt the DVD at 4x and 2x, and both get me to the same place. 

I have figured out how to get to the Boot Options- F6. I don't know if I've done the next bit right, though. 

When the Boot Options are on, I get an extra line of text that changes according to which option I'm on- eg. "Install Ubuntu" or "Check CD" (or something similar :-) ). Neither of these lines reflect the "all_generic..." line. I have erased the line of text that comes up when I've highlighted the "Install Ubuntu" option, then entered the line you have provided (quotation marks included).

This takes me to a black screen that whizzes through a whole stack of writing, then ends with the last three lines being something similar to:

Cannot open root device "<NULL>"...
Please append a correct "root=" boot option; here are the available partitions 
<163.840271> Kernel panic- not syncing: VFS: Unable to mount root fs on unknown-block (8,1)

Is this where I'm meant to be?

And no, there is no other OS installed- this is a brand new home-built PC and it came with no software.

Would it be worth installing Ubuntu 8.10 instead? Does anyone know if it's had this error also?

And how do I boot to the live CD desktop?

Thanks for your help so far!

:-)

---

### Post by louieb on 2008-10-26
Sorry but its time to get technical. Seems like its a hardware detection problem now. Not all Linux distros use the same options. But theres a way to change that.
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions") 
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")  like Ubuntu Knoppix is based on Debian. Has great hardware detection. One of best. I keep a Knoppix CD around just for recovery. 

Did a [Google Linux Search]("http://www.google.com/linux") on your mother board. Nothing much came up. So can't tell if it worked or didn't work for others.  

Right now its just try this and that. Next thing I would do is go into the BIOS setup and look at how the hard drives are setup.  If you have an option to use something call **IDE compatibility mode** try that.  

> Kernel panic... not syncing: ...Would it be worth installing Ubuntu 8.10 instead? Does anyone know if it's had this error also? 
Kernel panic is the Linux equivalent of the blue screen of death.  
Won't hurt to try 8.10. or even some other Linux distros.

---

### Post by DanceTheTango on 2008-10-28
Hi All!

I just wanted to let you know that I resolved the issue by installing Ubuntu 8.10 beta. Everything works perfectly. Thanks so much for all of your help.

:):KS

---

