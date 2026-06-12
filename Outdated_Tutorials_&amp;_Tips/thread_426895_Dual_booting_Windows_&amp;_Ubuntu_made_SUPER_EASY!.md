---
title: "Dual booting Windows &amp; Ubuntu made SUPER EASY!!!"
date: 2007-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by LIVEFRMNYC on 2007-04-28
This is what I like to do to make my Dual Booting experince easy and less of a headache to deal with. I think the chances of any Grub or Bootloader problems decrease too. Not to mention it's prettier and slighty more secure. This method works great for me, so I decided to share. This is mainly for Newbies and Beginning Novices like my self. 

[SIZE="3"]Please note:[/SIZE]  I know this is NOT necessary, but I found it to be easier and safer. You no longer have to worry about messing up your Windows Partition Or Getting rid of Grub in your MBR.  Also this give you a easier fool proof MAIN Bootloader that you can easily config over & over without messing anything up. **PLEASE READ WHOLE POST BEFORE YOU DECIDE IF THIS IS WHAT YOU WANT TO DO. **


[SIZE="5"]**Step 1:**   [/SIZE]

Make sure you have Windows already loaded into one partition. And make sure you have another blank partition at least 15GB in size. If you need to resize the Windows Partition to make space for a 15+GB partition, do so now. I suggest you use [Gparted]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") for resizing and creating partitions before setup.  Make the 15+GB partition any format as you will most likely delete it, change format, and allocate a gig to a Swap partition from the Ubuntu installation setup. 

[SIZE="5"]**Step 2: ** [/SIZE]

Install Ubuntu from Live CD.  Select Manual install. Enter nessecary info until you hit the Partition editor. Delete the 15+GB that you just made and allocate 1GB as a SWAP Partition, then use the remaining mem as your EXT Partition. **Ubuntu will not let you make a mistake here. ** Also, check the format box if unchecked on both SWAP and EXT Partitions. 

**[SIZE="3"]VERY IMPORTANT PART OF STEP 2:[/SIZE]  **
When you get to the screen that looks like the Pic Below. Click on the (HD0) button shown in pic. **Type (HD0,1) instead.**  This will install your Grub Bootloader on your Ubuntu(15+GB) Partition instead of touching anything in the MBR or Windows. 
[IMG]http://xs314.xs.to/xs314/07175/ubuntuinstallpart5.png[/IMG]

Now just let Ubuntu Install.

[SIZE="5"]**Step 3: ** [/SIZE]

Once you got Ubuntu installed. Let it reset and go back in to Windows. Download [GAG-BootLoader]("http://gag.sourceforge.net/") and burn it on to a DVD or CD. Then reset and boot up from the GAG disc you just created. 

GAG is Extremley super easy to config, so I really don't have to explain much here. Just create new menus that point to the right Partitions, name them, select a pic for them, set up a timer & default OS, and even create a password for each one if you want. Test out the settings as many times as you want with out changing a thing on your drive. Once your satisfied with settings, then select the "Save in HardDrive" button. Once you select "Save in HardDrive" you will not need the GAG disc to config anymore.   
[IMG]http://xs314.xs.to/xs314/07175/gagn3.gif[/IMG]


Once you completed this ..... When turn on your PC, the GAG bootloader will 
appear. 
Selecting the Windows button will take you to the Windows Bootloader. 
Selecting the Ubuntu button will take you to the Grub bootloader.  
Nice how every thing is kept completely separate. :D


[SIZE="5"]**HERE ARE MY PERSONAL SCEENSHOTS .............**[/SIZE]


[SIZE="4"]GAG Menu [/SIZE]
[IMG]http://xs314.xs.to/xs314/07175/00002.jpg[/IMG]


[SIZE="4"]Windows Booter loader menu, After I press the "Windows XP" button on GAG[/SIZE]
[IMG]http://xs314.xs.to/xs314/07175/00003.jpg[/IMG]


[SIZE="4"]GRUB Bootloader after I press the "Ubuntu Linux" button on GAG[/SIZE]
[IMG]http://xs314.xs.to/xs314/07175/00004.jpg[/IMG]


[SIZE="4"]The Windows and Grub Bootloader are on the default timer. 
Windows about 2sec and Grub is about 5sec.  I set my GAG boot loader to Windows as default on a 3sec timer.  The reason I mentioned this is so you get the idea that this method of dual boot is just as fast. Don't be fooled by the three differ boot screens. I usually don't even notice the GAG bootloader when I reset. 
[/SIZE]

---

### Post by jpeddicord on 2007-04-30
Out of curiosity, why wouldn't you want to use the default GRUB bootloader? It detects your Windows install by default, and is as safe to use (if not safer) than installing a third bootloader.

---

### Post by LIVEFRMNYC on 2007-05-01
> **jacobmp92 said:**
> Out of curiosity, why wouldn't you want to use the default GRUB bootloader? It detects your Windows install by default, and is as safe to use (if not safer) than installing a third bootloader.

I'm still using GRUB as seen in screenshot, I just installed it in the same Partition as Ubuntu instead of the MBR to avoid problems of messing up other partitions. This makes it safer. 

The method that I use allows for reinstalling Windows or Ubuntu without overwriting any Bootloaders or changing anything on another partition. It's also the Safest way to experiment with Ubuntu besides using a Live CD.

This prevents messing up Windows when installing Ubuntu the default (Grub in mbr) way. Many are not capable of fixing Windows when this happens. So this prevents the need to reinstall Windows.  This is also true for Vice Versa.    

Also GAG as the MAIN bootloader is MUCH EASIER (basically fool proof) to configure.  A huge plus for newbies.

---

### Post by glennric on 2007-05-04
This doesn't really solve the problem you seem to be claiming it solves.  You see, GAG installs into the MBR anyway.  Why not just use grub.

---

### Post by davin on 2007-05-04
yes man using grub is just fine why separate ??

---

### Post by zmike1 on 2007-05-05
I'm considering going the GAG route myself. (Independent Newbie POV).

Why?
well, I did the default install of feisty last week.  Of course, GRUB overwrote the MBR.  Both XP and Ubuntu worked; however, the accursed Dell Media Direct button now resulted in bad problems.  While trying to fix the Media direct problems, I trashed XP but learned some things in the process.  Then, I reinstalled Media Direct, and Windows then Ubuntu after messing around (some) with partitions.  I had a working (almost) system but there were ugly things with partitions I couldn't unmount (newbie, here) so, in the process of working on that, I messed up Ubuntu.  So, I started over.

Now, I'm just trying to get my hard drive partitioned (again!) so I don't have to mess with this any longer and can just start to learn how/if Unbuntu is really for me.
It might be easier to go the GAG route.

---

### Post by BLTicklemonster on 2007-05-05
Now all we need is for someone to make an OS called Maggot.


That was we could Gag a Maggot.


Move along, move along.

---

