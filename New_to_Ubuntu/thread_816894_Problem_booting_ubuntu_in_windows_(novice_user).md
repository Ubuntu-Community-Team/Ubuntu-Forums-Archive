---
title: "Problem booting ubuntu in windows (novice user)"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by new214 on 2008-06-03
heya all, im new to ubuntu and wanted to install it as dual boot with my windows xp laptop. I found out how to dual boot linux with windows from:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

I also intend to use the parition tool (that comes with the ubuntu os - as shown in the tutorial link)


using the tutorial i tried to:

Firstly I downloaded the ubuntu 8.04 desktop download (ISO file) from ubuntu.com. 
I then burned the ISO file to a DVD+RW
I then booted my laptop with the dvd inside
Then I proceeded to try install the o/s or run the o/s in windows

The problem is that after trying to run the DVD and install it (an hour of processing) nothing happens, after 
about 30mins it comes up with a cream background and then a black screen (whilst the DVD drive is 
working like mad). My laptop has 30GB of free space, 224MB RAM, 1 GHZ speed

I was reading something about using an Alternate install CD - is this an option that should show when booting with ubuntu? From my dvd it wasnt even showing?:confused:

---

### Post by sayakb on 2008-06-03
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
Download ubuntu Alternate install disk by **checking  **the *"Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."* checkbox under Start Download link

You cannot run the LiveCD because LiveCD needs atleast 384MB of RAM. You might also try [Xubuntu]("http://www.xubuntu.org/get"), which shall be faster on your config.

---

### Post by new214 on 2008-06-03
will i still be able to partition my windows using the alternate cd? 

what do you mean it has a text based installer - will this mean i have to install through commands rather than graphical options?

Finally, if i partion and dual boot windows xp with ubunutu - is there any way to get rid of ubuntu/dualboot/partition - if I wish to do so in the future?:confused:

---

### Post by mcduck on 2008-06-03
> **new214 said:**
> will i still be able to partition my windows using the alternate cd? 

what do you mean it has a text based installer - will this mean i have to install through commands rather than graphical options?

Finally, if i partion and dual boot windows xp with ubunutu - is there any way to get rid of ubuntu/dualboot/partition - if I wish to do so in the future?:confused:

The alternate CD is able to partition your hard drive just like the desktop CD.

The installer uses simple, text-based graphics, you don't need to type any commands or anything like that, you simply move through the installers dialogs with arrow keys & enter. Actually if you don't mind the uglier looks it could be considered easier than the graphical installer is..

If you decide that you don't want to keep Ubuntu you can get rid of it by reformatting it's partition from Windows, ir if you want, using some partition editor to merge Ubuntu's parrtition back together with the Windows partition. After that you can use Windows install diks to re-create MBR to get rid of Ubuntu's boot menu.

---

### Post by new214 on 2008-06-03
> If you decide that you don't want to keep Ubuntu you can get rid of it by reformatting it's partition from Windows, ir if you want, using some partition editor to merge Ubuntu's parrtition back together with the Windows partition. After that you can use Windows install diks to re-create MBR to get rid of Ubuntu's boot menu. 

so what your saying is that i would just use a 3rd party software such as partition magic to merge the 2 partions back together?

You mentioned i could use the > windows install disks to re-create MBR to get rid of Ubuntu's boot menu  - what do you mean by this?
:confused:

---

### Post by mcduck on 2008-06-03
> **new214 said:**
> so what your saying is that i would just use a 3rd party software such as partition magic to merge the 2 partions back together?

You mentioned i could use the  - what do you mean by this?
:confused:

Yes, you can use 3rd party tools to merge the partitions. Actually you coul use the GPArted that's on Ubuntu's desktop CD, but as your computer doesn't have enough RAM to run the desktop CD that would be a bit of a problem.. Some more lightweight live-CD would also be a possible solution.

Of course you can just leave them as 2 separate partitions and use them like that in Windows.

Then the MBR thing:

Master Boot Record is a section in the beginning of your first hard disks first partition (usually) that contains information about which partition your computer should start reading when yuou boot the machine. Windows places it's own bootloader there. When you install Ubuntu, the installer creates you a nice menu that allows choosing which operating system you wan to start, and doing this will require writing of some parts of the menu program into MBR, overwriting what was previously there.

Now if you remove Ubuntu, you also want to get rid of the boot menu and make your computer boot into windows instead. So you'll need to recreate the MBR that Windows used before installing Ubuntu. This can be done with the windows install disk.

---

### Post by new214 on 2008-06-03
> Actually you coul use the GPArted that's on Ubuntu's desktop CD, but as your computer doesn't have enough RAM to run the desktop CD that would be a bit of a problem.. Some more lightweight live-CD would also be a possible solution

In refernce to the above quote - isnt the GParted facility available on the alternate CD? In the tutorial link 

> [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

- it shows how to partition and dual boot windows/linux - woudl this partiton facility be there?

You mentioned the Master Boot Record would need to be replaced/installed (if ubuntu was uninstalled) - so after uninstalling ubuntu - wouldnt this make the laptop unbootable?? and how would you re-install the MBR (if the laptop is unbootable)? Would this mean a clean installiion of windows xp again?
:confused:

---

### Post by mcduck on 2008-06-03
> **new214 said:**
> In refernce to the above quote - isnt the GParted facility available on the alternate CD? In the tutorial link 



- it shows how to partition and dual boot windows/linux - woudl this partiton facility be there?

You mentioned the Master Boot Record would need to be replaced/installed (if ubuntu was uninstalled) - so after uninstalling ubuntu - wouldnt this make the laptop unbootable?? and how would you re-install the MBR (if the laptop is unbootable)? Would this mean a clean installiion of windows xp again?
:confused:

No, the alternate CD has a partition editor, but as GParted is a graphical program and alternate CD doesn't have a graphical environment it's not possible to use gparted from the alternate CD.

For the second question, yes and no. Immediately after removing Ubuntu you won't be able to boot into Windows. But you are still able to boot from a CD, so you can start the computer with the Windows install CD and use that to recover the MBR. But that's all you need to do, it takes no more tha n copule of minutes to do and you do not need to reinstall Windows.

---

### Post by new214 on 2008-06-03
> No, the alternate CD has a partition editor, but as GParted is a graphical program and alternate CD doesn't have a graphical environment it's not possible to use gparted from the alternate CD

So is the alternate cd a graphical operating system like windows cus youve mentioned above that the "alternate CD doesn't have a graphical environment"?

So you boot the computer via cd, would u use the > **fixmbr** command to recover the MBR?

The issue for me is that when i brought my laptop - they said to burn a cd/dvd which contained the windows xp o/s on the laptop. However I check the files on the cd/dvd that i burned and there seems to be no setup file, but the rest of the files look like there windows :confused:

---

### Post by mcduck on 2008-06-03
> **new214 said:**
> So is the alternate cd a graphical operating system like windows cus youve mentioned above that the "alternate CD doesn't have a graphical environment"?

So you boot the computer via cd, would u use the  command to recover the MBR?

The issue for me is that when i brought my laptop - they said to burn a cd/dvd which contained the windows xp o/s on the laptop. However I check the files on the cd/dvd that i burned and there seems to be no setup file, but the rest of the files look like there windows :confused:

The alternate CD runs a text-based installer that installs a graphical desktop for you. So when running from the CD there is no graphical environment.

And yes, "fixmbr" is the command used to ficx the MBR. Icanät really say anything about your Windows install CD, I hardly use Windows at all and it's been years since I've installed it last time. Not to mention that laptops manufacturers have a bad habit of using non-standard install disks. (but you can actually use _any_ windows install disk to do that, as you aren't really installing windows, only fixing the MBR)

edit: If you have ever installed Windows 95/98, (or if I remmeber right even 2000) the installer on the alternate CD is very similiar. No fancy graphics, keyboard-based navigation, but you don't need to know any technical stuff or commands to use it (at least not any more than you need installing any operating system)

---

