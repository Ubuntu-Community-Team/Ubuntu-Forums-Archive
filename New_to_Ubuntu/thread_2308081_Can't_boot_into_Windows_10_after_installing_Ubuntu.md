---
title: "Can't boot into Windows 10 after installing Ubuntu 14.04.3 LTS"
date: 2015-12-30
forum: New to Ubuntu
---

### Post by Alex_Rodriguez on 2015-12-30
Hi, 
 
I initially had Windows 10 installed. I then installed Ubuntu 14.04.3 LTS. 
I can boot into Ubuntu but I can not boot into Windows can you help me? 
The URL generated from Boot Repair tool is: 
 
[http://paste.ubuntu.com/14280349]("http://webmail2.bigpond.com/webedge/do/redirect?url=http%253A%252F%252Fpaste.ubuntu.com%252F14280349&hmac=b8b2e5b86f571d5b3ecc8f92a8284d22") 

System info taken from within Ubuntu:
Memory: 15.6 GiB
Processor: intel Xeon (R) CPU E3-1270 V2@3.50 GHz x 8
Graphics: Gallium 0.4 on NVC3
OS type: 64-bit
Disk: 153.8 GB

Hope this info is helpful. 
 
Hope you can help? 
 
Cheers, 
 
Alex

---

### Post by oldfred on 2015-12-30
With nVidia you often need nomodeset on linux line in grub menu.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

I do not know Xeon model numbers, of if this may apply:

 Xeon Skylake Users May Run Into Display Problems With Current Distributions Dec 2015
[http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset](http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset)

[URL="http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"]
[/URL]

---

### Post by Alex_Rodriguez on 2015-12-30
I had a look at the links you mentioned but I have a feeling I have not explained my problem well enough. When I start-up or restart my computer a menu comes up on a purple screen I think its called the grub menu. On the grub menu I am given two options first one is Ubuntu and the second one is Ubuntu Advanced Options, what is missing is a Windows option. How do I repair the boot to get this Windows option back? I can successfully boot into Ubuntu though.

---

### Post by oldfred on 2015-12-30
Have you run this from your Ubuntu installs terminal?
sudo update-grub

When you booted into Boot-Repair you booted in UEFI boot mode. But your installs are BIOS/CSM boot with MBR partitioning.
UEFI & CSM are not compatible, so an update of grub from UEFI would not add the Windows boot entry which needs to be BIOS entry.
Since your installs are BIOS, always boot in BIOS boot mode.

---

### Post by Alex_Rodriguez on 2016-01-01
No I had not run that command from the installs terminal. I ran the command as follows:   	 	 	 	   sudo update-grub  
 [sudo] password for  &#8230;....:  
 Generating grub configuration file ...  
 Found linux image: /boot/vmlinuz-3.19.0-42-generic  
 Found initrd image: /boot/initrd.img-3.19.0-42-generic  
 Found linux image: /boot/vmlinuz-3.19.0-25-generic  
 Found initrd image: /boot/initrd.img-3.19.0-25-generic  
 Found memtest86+ image: /boot/memtest86+.elf  
 Found memtest86+ image: /boot/memtest86+.bin  
 Found Windows Recovery Environment (loader) on /dev/sda1  

 Found Windows Recovery Environment (loader) on /dev/sda2  
 done  


I then restarted the computer and the grub menu displayed the following:
Ubuntu
Advanced options for Ubuntu
memory test
memory test....
Windows Recovery Environment (loader) on /dev/sda1  

Windows Recovery Environment (loader) on /dev/sda2  

If I click one of the windows recovery environment options will that give me the Windows option in the future next time I restart. i.e. to allow me to boot into Windows 10 should I want to?

By the way my BIOS is UEFI. I don't know anything about it except how to get into it.

---

### Post by greggfowler on 2016-01-01
I would go ahead and select the Windows recovery envronment on sda2 personally and see if I could recover/make windows boot properly. The smaller partition likely sda1 is a recovery partition and the larger contains the OS. Without more information I can't tell more, but it will definitely not hurt to "try" and boot into the recovery environment.

---

### Post by Alex_Rodriguez on 2016-01-01
I can now boot into Windows 10 using the Windows recovery environment on sda2 by selecting that option on the grub menu on start-up. I re-ran the command: sudo update-grub  
 [sudo] password for  &#8230;....:  
 Generating grub configuration file ...  
 Found linux image: /boot/vmlinuz-3.19.0-42-generic  
 Found initrd image: /boot/initrd.img-3.19.0-42-generic  
 Found linux image: /boot/vmlinuz-3.19.0-25-generic  
 Found initrd image: /boot/initrd.img-3.19.0-25-generic  
 Found memtest86+ image: /boot/memtest86+.elf  
 Found memtest86+ image: /boot/memtest86+.bin  
 Found Windows Recovery Environment (loader) on /dev/sda1  
 Found Windows Recovery Environment (loader) on /dev/sda2  
 done  

and received the same results for the terminal output in Ubuntu as shown above and on restart the grub menu is identical as before i.e.:

Ubuntu
Advanced options for Ubuntu
memory test
memory test....
Windows Recovery Environment (loader) on /dev/sda1  
Windows Recovery Environment (loader) on /dev/sda2 (**How do I change this line to just "Windows"?**)

If you require further info about my operating system and boot just look at the first post if you require more info please specify and I will provide it (if I can) in order to solve the problem.

Update: I went into the Windows recovery Environment on sda2. I tried to reset Windows 10 in order to fix the grub menu listing but the reset failed. The idea was to reset Windows 10 then update the grub using the above commands. But as the reset failed I am stuck. Any suggestions?

Update 2: At the grub menu I selected sda1 and got into the Windows Recovery Environment. Selected reset Windows and it worked. Was able to reboot into Windows. However the name on the Grub Menu is still "Windows Recovery Environment (loader) on /dev/sda1." I tried to change the name to Windows 10 using the grub-customizer ( see [http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183) ) in Ubuntu but without success. I think I will just leave it. Unless someone out there has a solution, will check back in a week or so?

---

### Post by oldfred on 2016-01-03
Grub has not been updated to search for Windows 10 yet. It goes thru all the other versions and if description does not match it uses recovery as the Windows entry. I would expect grub to eventually be updated, but who knows when?

You can create your own boot entries in 40_custom. And then you can name them anything you want.
Find Windows boot stanza:
gedit /boot/grub/grub.cfg
Copy boot stanza into this and edit description:
gksudo gedit /etc/grub.d/40_custom
sudo update-grub

Once your new entry works, turn off os-prober, so old entries are not created:
      
 In /etc/default/grub I added this line for os-prober:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true

Then 
sudo update-grub

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
       
 [URL="https://help.ubuntu.com/community/Grub2/CustomMenus"]https://help.ubuntu.com/community/Grub2/CustomMenus
[/URL]
 [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

[URL="https://help.ubuntu.com/community/Grub2/CustomMenus"]
[/URL]

---

### Post by Alex_Rodriguez on 2016-01-09
Thanks, I will look into it at some later stage. I believe this solves the problem. Cheers.

---

