---
title: "Cannot boot Ubuntu 10.04 after install from live cd. Win7"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by krager54 on 2012-09-16
Hello all,

I picked up a new laptop (Asus U47A) because I am going back to school. Decided I want to play around with Linux, so I downloaded 10.04 and burned it as an iso file. 

I then booted into bios and switched the boot order so my disc drive will boot first. I then restarted and went through the install prompts. I elected to let the installation wizard partition my HDD automatically, so I don't frag anything. 

When the installation was successful, I then removed the disc and rebooted when prompted. I was greeted with the "Reboot and select proper boot device." I figured I needed to switch the boot order back. No dice.

I then thought that I may need to include my hard drive in the boot options since that's where Ubuntu and grub are, but I don't even have that option. 

Now, upon boot I'm greeted with the option to open windows or Ubuntu, but when I pick Ubuntu I get the "the selected entry could not be loaded because the application is missing or corrupt."

As far as I know, I didn't do anything wrong. Help guys? Thanks!

PS: I google searched like crazy, but never found anything that matched my issue. Typically I'll see problems with being able to see the Ubuntu screen and whatnot, but simply cannot access Ubuntu.

---

### Post by krager54 on 2012-09-16
Error code I get when selecting Ubuntu from menu:

file: \ubuntu\winboot\wubildr.mbr

Status: 0xc000000f

Info: The selected entry could not be loaded because the application is missing or corrupt.

---

### Post by Bashing-om on 2012-09-16
krager54; Hi ! welcome to the forum .

The error "file: \ubuntu\winboot\wubildr.mbr" indicates windows ...and you attempted a "wubi" install -> giving ubuntu to run inside of windows.

Was it your intent to install ubuntu alongside windows as a dual boot operating system ?


[INDENT]kindest regards <==BDQ

[/INDENT]

---

### Post by krager54 on 2012-09-16
> **Bashing-om said:**
> krager54; Hi ! welcome to the forum .

The error "file: \ubuntu\winboot\wubildr.mbr" indicates windows ...and you attempted a "wubi" install -> giving ubuntu to run inside of windows.

Was it your intent to install ubuntu alongside windows as a dual boot operating system ?


[INDENT]kindest regards <==BDQ

[/INDENT]

Yes I was attempting a dual boot set up.

Could my problem stem from the fact that I didn't specify a partition? Should I attempt another install and maually set my partition?

---

### Post by critin on 2012-09-16
> **krager54 said:**
> Yes I was attempting a dual boot set up.

Could my problem stem from the fact that I didn't specify a partition? Should I attempt another install and maually set my partition?

Did you choose to install side-by-side windows?  It should have done it.  Hope you didn't say to use entire hdd.
> 
wubildr.mbrThis looks like wubi install, but you don't go to bios and choose alternate boot up to install wubi.  It's done from the desktop until install is finished, than it can be booted.  But the cd never goes into the cd tray at all. Not with Wubi Windows Installer.

It sounds like you installed the real thing to a real hdd.  
  Do you have the windows cd?

** Insert** the live iso again and boot it.  Run it TRY.  When on the desktop look for gparted in system tools and take a look at the hdd.

---

### Post by krager54 on 2012-09-16
> **critin said:**
> Did you choose to install side-by-side windows?  It should have done it.  Hope you didn't say to use entire disk.  Do you have windows cd?

No I don't. Windows is fully functioning. I performed a chkdsk and everything was golden. Should I attempt another install?

I selected install side by side, and elected to use the largest continuous free space.

Edit: current Ubuntu install is using 313gb under dev/sda6 partition.

---

### Post by critin on 2012-09-16
>  Windows is fully functioning

Thank the stars, I was worried for you!

No, I wouldn't install that copy again.  There's something amiss with it.
Be sure to download from the official ubuntu downloads, and burn it as slowly as your app will let you.

313gb is plenty.  lol  I have 5 partitions on a 160 hd.  


Good luck!

---

### Post by krager54 on 2012-09-16
> **critin said:**
> Thank the stars, I was worried for you!

No, I wouldn't install that copy again.  There's something amiss with it.
Be sure to download from the official ubuntu downloads, and burn it as slowly as your app will let you.

313gb is plenty.  lol  I have 5 partitions on a 160 hd.  


Good luck!

Yeah I thought I fragged my brand new computer at first lol.

Great I'll do this and report back, thanks for the help!

---

### Post by Bashing-om on 2012-09-16
well... the accepted method: Windows tools for windows problems, linux tools for ubuntu situations.

short synopsis:
It is suggested to use windows disk utility to make free space for ubuntu. Keep in mind can only have 4 primary partitions to each disk drive. If you have made adjustments to windows or used it extensively..it is suggested to de-frag windows
 In the ubuntu installer choose the "something else" option to install along side existing os.Then do some light partitioning.  At the final confirmation screen insure that grub (grand unified boot loader) is set to the booting drive (ie sda).
This link is a good tutorial
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
and ours:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

I would suggest to keep the boot priority set to boot the cd first and hard drive second. ( I boot different distros from cd many times so I leave the cd as first boot priority)

Look these over ..if you have questions or require any further assistance, We are eager to help!

I think you have a partial wubi install as of now ..no big deal as it is a file within windows ...identify that file and delete it ...suggest doing a google search with term "wubi ubuntu".. should get you back on the right track. (never experienced wubi so my directives are lax)[INDENT]regards <==BDQ
[/INDENT]

---

### Post by krager54 on 2012-09-16
> **Bashing-om said:**
> well... the accepted method: Windows tools for windows problems, linux tools for ubuntu situations.

short synopsis:
It is suggested to use windows disk utility to make free space for ubuntu. Keep in mind can only have 4 primary partitions to each disk drive. If you have made adjustments to windows or used it extensively..it is suggested to de-frag windows
 In the ubuntu installer choose the "something else" option to install along side existing os.Then do some light partitioning.  At the final confirmation screen insure that grub (grand unified boot loader) is set to the booting drive (ie sda).
This link is a good tutorial
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
and ours:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

I would suggest to keep the boot priority set to boot the cd first and hard drive second. ( I boot different distros from cd many times so I leave the cd as first boot priority)

Look these over ..if you have questions or require any further assistance, We are eager to help!

I think you have a partial wubi install as of now ..no big deal as it is a file within windows ...identify that file and delete it ...suggest doing a google search with term "wubi ubuntu".. should get you back on the right track. (never experienced wubi so my directives are lax)[INDENT]regards <==BDQ
[/INDENT]

Thank you for the info! 

I did a search for wubi in my computer. Discovered multiple wubi.mo files. These should all be deleted, yes?

---

### Post by Bashing-om on 2012-09-16
wubi.mo: I really can not give solid advise. I have not to this time had any experience with a wubi install. But, as it is wubi and you are going to reinstall; I can see no problem with deleting the wubi.mo (.mo=module files). 

  Are you seeing these wubi.mo files from within windows ? I seem to recall reading at some point that there is a uninstall wubi routine within windows to uninstall wubi.

working to get you up on ubuntu ==> BDQ

---

### Post by Wim Sturkenboom on 2012-09-16
> **krager54 said:**
> Discovered multiple wubi.mo files. These should all be deleted, yes?Be carefull. As far as I know you can uninstall your Wubi install like you uninstall all Windows programs (via control panel in Windows). After that you can cleanup leftovers.

---

### Post by critin on 2012-09-17
> **Wim Sturkenboom said:**
> Be carefull. As far as I know you can uninstall your Wubi install like you uninstall all Windows programs (via control panel in Windows). After that you can cleanup leftovers.

Yes, Wubi is uninstalled from Add/Remove in control center, BUT as windows will, scraps and bits of it are left behind.  Wubi has a hard time reinstalling with these bits and pieces in the way.  It thinks it's already installed. It won't overwrite as windows programs do.

By doing a thorough search and deleting it all, it's clean and ready to go.

---

### Post by varunendra on 2012-09-17
Hi krager,
First, let me have the privilege to welcome you to the forums - Welcome aboard! :)

Next, assuming it's the 'Preinstalled-Windows' on your laptop, **please create a set of backup DVD's from win's backup option in the control panel**** first**,  if you haven't already done that. It will save you from losing your  'expensive' OS in case something ever goes wrong with its installation  or the partitions/drive itself. (Your current, inexperienced attempts to  restore/reinstall a second OS have a high risk of causing such  trouble!).

Once you have done that, please boot with your Ubuntu live cd, install [boot-repair]("https://help.ubuntu.com/community/Boot-Repair")  on the live session and run it. Then post back here the 'pastebin' link  it gives you, or the contents of "Results.txt" file it creates (in  'root's' home directory I guess. It should give us a clean and complete  picture of what is where on your hard disk. *(You might wish to save  the downloaded files on your disk (located in /var/cache/apt/archives)  since live session is volatile and the installation will be gone at  reboot)*.

But please make sure to create a backup of your win installation first, just in case things go worse!

**PS:**
*@critin*,
> **critin said:**
> This looks like wubi install, but you don't go to bios and choose alternate boot up to install wubi.  It's done from the desktop until install is finished, than it can be booted. [COLOR=Red]** But the cd never goes into the cd tray at all. Not with Wubi Windows Installer.**[/COLOR].
The initial part is correct. But the latter part (highlighted in red) isn't. If things have not changed radically in the recent versions, the WUBI  installation DOES use the cd if it is run (just like any 'autorun' cd in windows) from there. It only attempts  to download and install from the iso (which I think you implied) if you  have copied (or downloaded) it separately somewhere on the hard disk.  But if you run it from within the cd, it installs ubuntu from the cd  itself. Also, if you run it from a folder on your hard disk, but also  keep the downloaded iso in the same folder, it will install ubuntu from  that iso and won't attempt to download it again.

However, since it is at least 2years since I have used it, so I may be wrong and please excuse me if indeed I am.

---

### Post by critin on 2012-09-18
> **krager54 said:**
> Hello all,

I picked up a new laptop (Asus U47A) because I am going back to school. Decided I want to play around with Linux, so I downloaded 10.04 and burned it as an iso file. 

I then booted into bios and switched the boot order so my disc drive will boot first. I then restarted and went through the install prompts. I elected to let the installation wizard partition my HDD automatically, so I don't frag anything. 

When the installation was successful, I then removed the disc and rebooted when prompted. I was greeted with the "Reboot and select proper boot device." I figured I needed to switch the boot order back. No dice.

I then thought that I may need to include my hard drive in the boot options since that's where Ubuntu and grub are, but I don't even have that option. 

Now, upon boot I'm greeted with the option to open windows or Ubuntu, but when I pick Ubuntu I get the "the selected entry could not be loaded because the application is missing or corrupt."

As far as I know, I didn't do anything wrong. Help guys? Thanks!

PS: I google searched like crazy, but never found anything that matched my issue. Typically I'll see problems with being able to see the Ubuntu screen and whatnot, but simply cannot access Ubuntu.

krager,  This is Wubi window installer for 10.04.  You're not using this are you?  It's the easiest and safest way to install inside windows, if you still wanted to go that way.    When I say Wubi, this is what I mean.  There are other ways, but for anyone not experienced, this is the best.

[http://www.liberiangeek.net/2010/03/how-to-install-ubuntu-10-04-lucid-lynx-with-wubi/](http://www.liberiangeek.net/2010/03/how-to-install-ubuntu-10-04-lucid-lynx-with-wubi/)

Another idea to avoid messing with the windows partition is to install VMware  and point the installer to the iso already downloaded.   A safe and easy way to explore, try and actually use ubuntu.


Good luck!

---

