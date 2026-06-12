---
title: "Can't access grub ubuntu 12.10"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by artyfin on 2013-02-11
I installed ubuntu 12.10 on a new hp envy laptop with an amd processor. Everything went fine until I tired to boot into it. I can't access grub and my computer keeps automatically booting into windows 8. Please help

---

### Post by squakie on 2013-02-11
I just got answers on a thread I had about Ubuntu and Windows 8.  As it turns out, you can't just install when Windows 8 is involved - there are some extra steps.  It appears to be a common problem.

Here's a reply from that thread by someone who really knows their stuff.  I hope it can help you. 

[IMG]http://ubuntuforums.org/images/rebrand/statusicon/post_old.gif[/IMG] 			22 Hours Ago 			 			 		 		 			  			#[**4**]("http://ubuntuforums.org/showpost.php?p=12502557&postcount=4") 			 		 	   	  			 				 				[[COLOR=#DD4814]**oldfred**[/COLOR]]("http://ubuntuforums.org/member.php?u=852711") 				 				 			
  			Forums Moderator
 			[IMG]http://ubuntuforums.org/images/rebrand/ranks/rankstaff.png[/IMG]
 			  			  			 				 
				Join Date: Jun 2009
 				Location: Chicago Suburbs
 				 	  					Beans: 23,016 				
 			       Ubuntu 12.04 Precise Pangolin  				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				 				**Re: Windows 8/virtual box/ubuntu** 			
 			 			 		   		 		 		It depends on  what vendor and model you have. Some work well, some have to have  several work arounds and some just do not work dual boot UEFI Windows 8  secure boot with Ubuntu. Ubuntu is using the same key, so it should work  for everyone. If a Samsumg be hesitant. 

       You will need to use the 64 bit version of 12.10 and from the  UEFI menu boot the flash drive in UEFI mode. That way it will install in  UEFI mode.
Best to turn off secure boot in UEFI/BIOS, but keep in UEFI mode. Varies  how you turn on or off as each vendor does it differently.
Systems need quick boot or fast boot turned off. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
Actually with UEFI and then gpt partition the partitions are easy. There is no more 4 primary partition limit, it now is 128 :smile: .  All partitions then in gpt partitioning are, in effect, primary.

But really good backups are required both the efi partition and the  Windows partitions. Do not delete any Windows partitions as some have  issues booting without them.

       The vendor recovery DVDs are just an image of your drive as  purchased. If you have housecleaned a lot of cruft normally included,  run many updates with many reboots, and added software you may want a  full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
    
Use Windows Disk Tools to shrink the Windows partition and make  unallocated space for Ubuntu. Reboot a couple of times to let Windows  run chkdsk and make any other repair due to partition size change.

How you boot live installer is how it will install and it should be in UEFI mode, but some will only install in BIOS mode.

If you have an UltraBoot with Intel SRT that adds complications,

I have links to threads (or you can search forum for your brand) on  successful (sometime with effort) installs for Lenovo, Dell, HP, Sony,  Asus etc. But it may vary by model.

There is a bug in grub2's os-prober. It still creates BIOS entries which do not work with UEFI.
       grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+s...b2/+bug/807801]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801")
grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+s...2/+bug/1024383]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383")
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    Boot-Repair can auto fix that issue and some others with UEFI.

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.p...769482&page=71]("http://ubuntuforums.org/showthread.php?t=1769482&page=71")

            Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

       Dell XPS13 Details on how to install - UEFI and Intel SRT  in Post #10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)

And some vendors just do not have UEFI correct. It even corrupts system with Windows.
       [http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?pag...tem&px=MTIyOTg]("http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg")
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)
 		                   		  		  		 		 			 				__________________
				[COLOR=Navy]Let us know what works and to mark your thread as[/COLOR] [SOLVED][COLOR=Navy], use [COLOR=Red]Thread Tools[/COLOR] on forum page. 
Howto: [https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")
[/COLOR] 			
 		 		  		  		 		 			 				 				* 					 						Last edited by oldfred; 22 Hours Ago at 12:35 PM.. 					 					 				*

---

### Post by squakie on 2013-02-11
Someone also pointed me to this as well:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

