---
title: "Dual / Triple Book Question"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Tex786 on 2008-05-05
Hi Eeveryone,

I just got a new laptop on Ebay, Here is what it has. [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=330231132121]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=330231132121")

It has brand new installs of XP and Vista.

From what you all think about Vista do you think i should just Install Ubuntu over Vista and just forget about it or should i get complicated?

I know that i could just format Vista off my harddrive and have an easy install of Ubuntu but I want to keep as much as I can. I have 60 Gigs to work with on this harddrive.

Can someone please explain how I would install Ubuntu Both ways so that I don't screw up my machine?

Thanks

---

### Post by bumanie on 2008-05-05
I would take a look at easybcd bootloader [here]("http://neosmart.net/dl.php?id=1") or read grub page (site down at writing). http//:[www.users.bigpond.net.au/hermanzone/p15.htm](www.users.bigpond.net.au/hermanzone/p15.htm) (I think).

---

### Post by Tex786 on 2008-05-05
Please explain why i need to visit this page.

I am new to linux and all this stuff is over my head.

---

### Post by bumanie on 2008-05-05
easybcd is a bootloader that has a good reputation for being able to triple boot computers. Some people use it in preference to the linux grub bootloader for their linux machines. The grub page is an extensive document on grub bootloader and may give you some tips on how to achieve a triple boot using grub - it's all to do with chainloading one OS after another and probably setting up a specific grub partition as well. I'm reasonably proficient at dual boot systems, but have never tried a triple boot, as I have not had the need to. I have read about it and as far as I know, easybcd bootloader is  the best tool to use. 
With triple booting, (with two windows OSes and a linux), problems arise with the windows bootloaders. They recognise each other, but aren't compatible with each other, in as far as they won't boot each other, so one has to start putting boot.ini files from xp into vista's bootlader etc., etc and then loading grub after that. As far as I understand, easybcd has the capacity to do this for you and has a function that recognises linux installations on a system and achieves triple boot systems easier than with grub.
Sorry I can't be of more help, that's basically all I know - I'm not an expert on triple booting, but it can be done (according to the documentation available on the internet), but it's not necessarily easy to do.

---

### Post by kirios on 2008-05-05
It seems to have Vista Release Candidate 1, not the final version. In any case, I wouldn't try to run Vista on a Pentium 4-M 1.8 GHz laptop. Also, 60GB is probably not enough for a triple-boot if you intend to keep Vista. 

I'd suggest you keep XP and dual-boot Ubuntu. Install XP first, then Ubuntu. The Ubuntu installer will create an entry for Windows in the boot menu during the install process.

> [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=330231132121]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=330231132121")
- Software-
- Windows XP SP3RC2/Windows Vista RC1 Dual Boot

> **Tex786 said:**
> 
It has brand new installs of XP and Vista.

From what you all think about Vista do you think i should just Install Ubuntu over Vista and just forget about it or should i get complicated?

I know that i could just format Vista off my harddrive and have an easy install of Ubuntu but I want to keep as much as I can. I have 60 Gigs to work with on this harddrive.

---

### Post by bumanie on 2008-05-05
> In any case, I wouldn't try to run Vista on a Pentium 4-M 1.8 GHz laptop. Also, 60GB is probably not enough for a triple-boot if you intend to keep Vista.
Agree with the above sentiments. 60gb is a small drive for three OSes. My g'friends daughter has a 3ghz celeron with 1.5gb ram, vista's performance on that computer is lacklustre, at best.

---

### Post by jboy012000 on 2008-05-05
or you could save yourself all the trouble, just install Ubuntu 7.10, then install vmware server create a virtual machine with XP and you are well away. 

Below is one link for downloading Ubuntu 7.10 and a link for downloading and installing vmware.

Be aware that Ubuntu 8.04lts does not yet support vmware so I would stick with 7.10.

Cheers

---

### Post by Xiong Chiamiov on 2008-05-05
You are of course assuming that he has an XP disc, while it is more than likely that he doesn't even have a system recovery disc...

If you don't have any discs (or a license key), then I'd probably recommend you back up your XP partition to an image file.  We can help you out with that later if you need to.

---

### Post by Tex786 on 2008-05-05
I understand installing ubuntu is easy if you just toss in the disk and install ubuntu over an already standing partition.

I am not even thinking of tripple boot now.

I know nothing about linux and much of what is said here about bootloaders is nothing i know of.

i am just going to go into XP and format the drive that my vista OS is on and reboot my computer with the ubuntu disk in my CD-ROM.

How does this sound? I know ubuntu is easy why people make it so difficult i don't know.

---

### Post by Xiong Chiamiov on 2008-05-05
You can do all of your partition work inside the Ubuntu installer.  You'll want to, anyways, because XP won't let you partition to ext3, which is what you'll want.

The reason we talk about all this "difficult stuff" is because you're talking about triple-booting.  Whether or not Ubuntu is a fairly easy Linux distribution, you're still talking about having multiple operating systems on your computer.  You need to accept the fact that you're going to have to learn what a bootloader is.

---

### Post by Tex786 on 2008-05-05
> **Xiong Chiamiov said:**
> You can do all of your partition work inside the Ubuntu installer.  You'll want to, anyways, because XP won't let you partition to ext3, which is what you'll want.

The reason we talk about all this "difficult stuff" is because you're talking about triple-booting.  Whether or not Ubuntu is a fairly easy Linux distribution, you're still talking about having multiple operating systems on your computer.  You need to accept the fact that you're going to have to learn what a bootloader is.


I don't think i am going to do the tripple boot now. Vista sucks and i don't see myself getting much out of it. 

Should i formatt the vista portion of my harddrive or will ubuntu just take care of that for me?

Do i just need to select with partition i want to install to?????

Thanks everyone for your help. Means a lot.

---

### Post by stchman on 2008-05-05
> **Tex786 said:**
> Hi Eeveryone,

I just got a new laptop on Ebay, Here is what it has. [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=330231132121]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=330231132121")

It has brand new installs of XP and Vista.

From what you all think about Vista do you think i should just Install Ubuntu over Vista and just forget about it or should i get complicated?

I know that i could just format Vista off my harddrive and have an easy install of Ubuntu but I want to keep as much as I can. I have 60 Gigs to work with on this harddrive.

Can someone please explain how I would install Ubuntu Both ways so that I don't screw up my machine?

Thanks

Yes, I would get rid of Vista.  That laptop does not have enough power to run Vista in a satisfactory way.  My laptop with its 1.73GHz Celeron M run Vista like cr@p.  I installed Ubuntu and have been happy ever since.

Actually if you have no use for XP(like myself) and do not want to game on the laptop make it an Ubuntu only machine.

What brand of wireless card does the laptop have?

---

### Post by Tex786 on 2008-05-05
> **stchman said:**
> Yes, I would get rid of Vista.  That laptop does not have enough power to run Vista in a satisfactory way.  My laptop with its 1.73GHz Celeron M run Vista like cr@p.  I installed Ubuntu and have been happy ever since.

Actually if you have no use for XP(like myself) and do not want to game on the laptop make it an Ubuntu only machine.

What brand of wireless card does the laptop have?

I have no clue as to what kind of wireless card it has. My laptop stays at at the desk, so its on a cat 5.

I don't want to wipe off XP. I have some things that i need  that Ubuntu does not support. 

I am excited about ubuntu. change is easy for me so getting started with ubuntu and staying loyal is easy!

---

### Post by tjwoosta on 2008-05-05
first you will want to defragment windows xp a couple of times (just to make sure the data is all at the beginning of the partition instead of all spread out)

then boot the ubuntu live cd

once its all booted up go to System-Administraiton-Partiton Editor  

here you will delete the useless vista partition and resize the xp partition as desired  (leave enough unallocated space to install ubuntu on)

then click apply and gparted(the partition editor) will resize and delete like you said

then go back to the desktop and click the install icon

once it askes you how youwant to install it select 
"Guided Install: use lagrest continuous free space"

this will install ubuntu to the unallocated space that you made from deleting vista 
(also it will install GRUB boot loader automatically for you)

---

### Post by Tex786 on 2008-05-05
> **tjwoosta said:**
> first you will want to defragment windows xp a couple of times (just to make sure the data is all at the beginning of the partition instead of all spread out)

then boot the ubuntu live cd

once its all booted up go to System-Administraiton-Partiton Editor  

here you will delete the useless vista partition and resize the xp partition as desired  (leave enough unallocated space to install ubuntu on)

then click apply and gparted(the partition editor) will resize and delete like you said

then go back to the desktop and click the install icon

once it askes you how youwant to install it select 
"Guided Install: use lagrest continuous free space"

this will install ubuntu to the unallocated space that you made from deleting vista 
(also it will install GRUB boot loader automatically for you)

thanks alot !!

I'll do that.

---

