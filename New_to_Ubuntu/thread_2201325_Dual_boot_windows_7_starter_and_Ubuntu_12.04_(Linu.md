---
title: "Dual boot windows 7 starter and Ubuntu 12.04 (Linux Lite 1.08)"
date: 2014-01-23
forum: New to Ubuntu
---

### Post by ohjrson on 2014-01-23
Alright 
I seem to have made a big problem. I had tried to install Linux Lite 1.06 to my Dell Inspiron Mini 1010. It never booted into the Linux lite as it for some reason could not load the right video for the GMA500 that the Dell has. I was advised to do a upgrade install of 1.08 so I tried that, however it stalled at the user entry page and never would finish (even after waiting for 6 hours or more) . I rebooted and now the only thing I get when starting up the netbook is error: unknown file system then gives me a prompt of: grub rescue> 

[FONT=Verdana, Arial, sans-serif][COLOR=#000000]I can still load the Linux Lite 1.08 from the USB drive and it works just fine. when I chose to install by installing along side the multiple OS, I then select the advanced to show the additional partitions and when I click install it tells me: no root file system is defined   Please correct this from the partitioning menu.[/COLOR][/FONT]

[FONT=Verdana, Arial, sans-serif][COLOR=#000000]What do I do now? In the installation type window it gives me 2 drives sda2 15728mb, sda3 72236mb (partitions) with ntfs which is Win 7 I know, then 2 that are EXT4 for linux, sda6 70971mb, sda5 1061mb and then 1 that is sda1 fat16 41mb (this is for Dell utilities), I see no sda4 though. Just a sda that has no number. The drive is supposed to be 160 gigs. The Win 7 is the Win7 starter that it came with. No backup cd. [/COLOR][/FONT]

[FONT=Verdana, Arial, sans-serif][COLOR=#000000]I have no idea which Linux Lite is installed. However it seems that I have no grub to boot up or something. Now, A little about me. I am a newbie to the linux Ubuntu community. I love the way these OS work and I am what you would call very green. I have a limited knowledge of entering programming and know only a few commands.  As a result you will have to explain things in a bit of detail. Also the netbook that I am installing/messing things up on is without a CDRom, there is not ever a slot in it. Here are the details of the Netbook : Intel Atom processor x2 at 1.33, Video in Intel GMA500 and it has a few other things on it. If you need more information please let me know. 

Desperately seeking help....Thanks[/COLOR][/FONT]

---

### Post by mikewhatever on 2014-01-23
You can google, and find [this question]("http://askubuntu.com/questions/80455/no-root-file-system-defined-error-while-installing-ubuntu"), which will help you to define the root file system. 
Other then that, prepare for a rough ride, cause Dell's Mini 1010 is a [vicious beast]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Dell_Mini_10_.28Inspiron_1010.29").

---

### Post by ohjrson on 2014-01-26
> **mikewhatever said:**
> You can google, and find [this question]("http://askubuntu.com/questions/80455/no-root-file-system-defined-error-while-installing-ubuntu"), which will help you to define the root file system. 
Other then that, prepare for a rough ride, cause Dell's Mini 1010 is a [vicious beast]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Dell_Mini_10_.28Inspiron_1010.29").


OK this is what I did to SOLVE my problem. Clicked on the link you provided and did what was suggested in the 2nd answer with the pictures. I paid close attention to them as I had tried this once before but I did not click the box labeled format drive.... Once I did that everything finished installing and everything seems to be back and operating like it should. 

So Many many many thanks. It worked. 

This is what I did....: when the install came to the partitioning of the drive I clicked on the EXT4 drive that was already created and selected the change tab where I selected the EXT4 again and then checked the box to format drive then hit install.... everything else went according to a regular install.

---

