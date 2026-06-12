---
title: "Installing Ubuntu from USB in legacy mode"
date: 2017-06-25
forum: New to Ubuntu
---

### Post by bernardlxy on 2017-06-25
Hi everyone,

I'm working with a windows 10 laptop that has previously been installed with windows 7. I've checked my boot options and windows is currently booting in Legacy Mode, with UEFI and secure boot options turned off. The problem is when I try to load Ubuntu from the USB, the only option to load Ubuntu is through EFI. 

And when I try to install it, I get the message: 
 "This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later.

If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here. If you wish to keep the option to boot an existing operating system, you should choose NOT to force UEFI installation here.


As far as I can tell, the problem lies with windows booting in Legacy Mode and me loading Ubuntu in EFI. Is there anyway to load EFI in Legacy mode?

---

### Post by RobGoss on 2017-06-25
>  to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later.  

I'm a bit confused about this section of your post, you mention** Debian**, what version of Ubuntu are you trying to install or are you trying to install Debian? it has been my experience when installing Ubuntu on a system using UEFI, you need to install Ubuntu in UEFI, if this system is fairly  new then it should be UEFI. On older systems that is Legacy / BIOS you should be able to DUAL boot if installed it legacy mode

If you install Ubuntu in UEFI and Windows is installed in BIOS you will not be able to choose between the two systems to boot your machine, you will have to access the BIOS and change the configurations to switch between each OS, if you don't really use Windows then it might not be a big deal as it was not for me at one point 


Here's some good documentation on how to dual boot your system using UEFI

How to dual boot Windows and Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

UEFI help
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Is this a fairly new machine?

---

### Post by bernardlxy on 2017-06-25
I'm actually really new to Linux systems, so I'm not sure what Debian is. I downloaded Ubuntu 16.04.2 LTS and download/mount it onto a USB using Rufus. 

I'm working on a DELL inpsiron 5737 that I got about 3 years ago. It came with a windows 7 and I upgraded it to windows 10. In the system information, it says that the BIOS mode is Legacy

I've checked out the Dual Boot documentation, but it doesn't really help

---

### Post by yancek on 2017-06-25
In the second paragraph of your initial post you mention "Debian" which is probably what RobGoss was referring to.

If you go to the Ubuntu documentation link, second link in his post, you will see that if you boot Ubuntu UEFI there is a black screen with white text.  If Legacy, you should see  purple screen as shown at that site.  Booting in Legacy mode is something you will have to change in the BIOS of whatever laptop you are using.  Methods vary from manufacturer to manufacturer and you haven't indicated what you are using.

---

### Post by RobGoss on 2017-06-25
> I'm actually really new to Linux systems, so I'm not sure what Debian is 

Debian is another Linux operation system you can read about it here, [https://www.debian.org/intro/about#what](https://www.debian.org/intro/about#what) 

The setup is much different then Ubuntu and for new users it can be problematic trying to install it that's why I ask what OS were you trying to install

---

### Post by Impavidus on 2017-06-25
But Ubuntu is based on Debian and sometimes you may see a reference to Debian that the developers forgot to change to Ubuntu. Rare, but not unheard of.

It should be possible to boot an Ubuntu live disk in legacy mode. Maybe it works if you use a different tool to make the live disk. There are several.

---

### Post by RobGoss on 2017-06-25
>  It should be possible to boot an Ubuntu live disk in legacy mode. Maybe it works if you use a different tool to make the live disk. There are several.  

Yes he can boot and install Ubuntu into Legacy mode along with Windows, I had that setup like that for sometime until I got tired of Windows

---

### Post by bernardlxy on 2017-06-26
Yancek,

When I load Ubuntu, I got the black screen with white text and I'm aware that I'm loading it using UEFI. My question is how do I load and install it in Legacy mode? 

I'm using a DELL INSPIRON 5737, windows 10 upgraded from windows 7 previously, if that helps

Rob Goss

What tool did you use to make the live disk? I used RUFUS, it would be great if you can recommend me the one that made yours work in Legacy

---

### Post by RobGoss on 2017-06-26
> **bernardlxy said:**
> Rob Goss

What tool did you use to make the live disk? I used RUFUS, it would be great if you can recommend me the one that made yours work in Legacy

I have always used the Linux** image writer,** tool for all my USB drives, you are trying to dual boot correct?

---

### Post by CatKiller on 2017-06-26
FWIW, my understanding is that if the installer is booted as a UEFI device, the installation will be done as an EFI install. If it's booted as a Legacy device, the installation is done as a Legacy install.

The mode that the installer is booted in is a BIOS option at boot time.

---

### Post by bernardlxy on 2017-06-26
> **RobGoss said:**
> you are trying to dual boot correct?

Yeah that's right

---

### Post by RobGoss on 2017-06-26
Try using USB installer to create your bootable USB [https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

If you can boot Windows and it loads you can install Ubuntu the same way, if your machine is in Legacy which I'm assuming it is because you can boot in to Windows then just boot the maching, hit F12 then run the live desktops to see how everything works

If all is OK just proceed with the installation, you will have the option to choose to install alongside Windows, if you choose this option the installer will do everything for you including assigning disk space for the new partition 

Most people like to choose their own partition disk space. Make sure you have a full backup of your Windows partition just in case some goes worng

---

### Post by CatKiller on 2017-06-26
> **RobGoss said:**
> if your machine is in Legacy which I'm assuming it is because you can boot in to Windows

Not necessarily. It depends on the mode of the device that was used to install it, at the time that it was installed. My install uses BIOS rather than UEFI because the card reader I used to install it only booted in Legacy mode. If I were to reinstall today it would be in UEFI mode because I now have a thumb drive that can boot as a UEFI device.

You can still boot a UEFI-capable device in Legacy mode, though, as a boot option, which is what the OP should do if he wants everything to continue working.

Edit: Actually, that was what the OP asked how to do in the very first post, so I'll elaborate. Going into the BIOS, when I select the boot order, the first option is for [UEFI]name-of-my-thumb-drive, but I can select a different entry whose tag I can't currently remember because I'm no longer in the BIOS. Selecting that would let me install as a Legacy device.

Reinstalling Windows as a UEFI-aware OS is another option. Possibly because it was originally Windows 7 is the reason it's still Legacy even with the upgrade.

---

### Post by RobGoss on 2017-06-26
**Catkiller,** Good points that is correct, the OP would have to access the BIOS to see what mode the machine is booting in then install Ubuntu in the same mode

---

### Post by bernardlxy on 2017-06-26
> **RobGoss said:**
> Try using USB installer to create your bootable USB [https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

If you can boot Windows and it loads you can install Ubuntu the same way, if your machine is in Legacy which I'm assuming it is because you can boot in to Windows then just boot the maching, hit F12 then run the live desktops to see how everything works



Problem is after using the link above to write the Ubuntu image to the USB, I no longer see my USB appearing on the boot menu. It just doesn't recognise my USB where else previously, my USB was listed under UEFI, now there's just no UEFI boot option and the USB isn't listed under the Legacy boot option either

> **CatKiller said:**
> 

Edit: Actually, that was what the OP asked how to do in the very first post, so I'll elaborate. Going into the BIOS, when I select the boot order, the first option is for [UEFI]name-of-my-thumb-drive, but I can select a different entry whose tag I can't currently remember because I'm no longer in the BIOS. Selecting that would let me install as a Legacy device.

Reinstalling Windows as a UEFI-aware OS is another option. Possibly because it was originally Windows 7 is the reason it's still Legacy even with the upgrade.

Reinstalling Windows is not something I'm very keen on doing. 

As for the boot order, I have seen screenshots of others wheres there's an option for UEFI USB and just USB(Legacy) but mine just has the option of the UEFI

---

### Post by CatKiller on 2017-06-26
> **bernardlxy said:**
> Reinstalling Windows is not something I'm very keen on doing. 

As for the boot order, I have seen screenshots of others wheres there's an option for UEFI USB and just USB(Legacy) but mine just has the option of the UEFI

That's a pain. Can you get hold of something that isn't capable of booting in UEFI mode? Ubuntu should still install fine. In my case, it was a USB SD card reader. Otherwise, [this page]("https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode") suggests that it may be possible to install Ubuntu in UEFI mode alongside your existing Windows install and then change it to Legacy mode afterwards. It's not something that I've ever tried.

Back up your Windows install, regardless of what you do next.

---

### Post by RobGoss on 2017-06-26
Have you accessed your BIOS to see if Windows is in fact installed in Legacy / UEFI mode?

I know having to reinstall Windows will be a pain but unless Windows is installed in UEFI it may be the only option to get this dual boot up and running

As I mentioned I had one of my machines which had windows installation in Legacy mode then I installed Ubuntu in UEFI so when I wanted to boot in to Windows I had to change the boot options to start Windows, still it was all that bad because I didn't really use Windows

---

### Post by bernardlxy on 2017-06-26
> **CatKiller said:**
>  Can you get hold of something that isn't capable of booting in UEFI mode? Ubuntu should still install fine. In my case, it was a USB SD card reader. Otherwise, [this page]("https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode") suggests that it may be possible to install Ubuntu in UEFI mode alongside your existing Windows install and then change it to Legacy mode afterwards.

I'll take a look and see what I can do about that. In the meantime, any ideas on why this is happening? I've been scouring the web for 2 weeks but couldn't find a proper answer

---

### Post by CatKiller on 2017-06-26
> **bernardlxy said:**
> I'll take a look and see what I can do about that. In the meantime, any ideas on why this is happening? I've been scouring the web for 2 weeks but couldn't find a proper answer

That bit is quite straightforward: for some reason, your Windows install was done using Legacy BIOS; possibly because it was Windows 7 initially. UEFI is quite recent, after all.

The reason you can't mix-and-match is because [bootstrapping]("https://en.wikipedia.org/wiki/Bootstrapping") is actually a hard problem to solve. Once there was a solution that worked, no one messed with it for the longest time - until there were enough new features in the replacement to be worth the effort and pain.

I don't know for sure why your chipset won't let you boot your thumbdrive in Legacy mode; probably cost. Either to the chipset maker or to the thumbdrive maker.

EDIT: I haven't used Windows for over a decade, but it's also [apparently possible]("https://www.tenforums.com/tutorials/81502-convert-windows-10-legacy-bios-uefi-without-data-loss.html") to convert Windows 10 from Legacy BIOS to UEFI without data loss.

---

### Post by yancek on 2017-06-26
> As for the boot order, I have seen screenshots of others wheres there's  an option for UEFI USB and just USB(Legacy) but mine just has the option  of the UEFI 				

That seems very strange since you originally had an older MBR install which was the default for windows 7 and that would be a Legacy install.  You probably need to explore the BIOS setup options a little more closely rather than the boot options.  The Ubuntu iso should be able to boot either, it did when I booted to install and from what I remember it was the different settings in the BIOS which made the difference.

---

### Post by Geoffrey_Arndt on 2017-06-27
Yes, Yancek is on the right track.   Many PC's have multi-layered hidden screens in the BIOS.   For example, on Acer systems, one has to set up a Supervisor Password for the Firmware (BIOS and UEFI).   Only when the Supervisor password is used upon next access to the BIOS (e.g., after the initial setup, you may have to re-access the BIOS but now using the Supervisor password).    Then, more options are opened up for doing things like special one-time boot keys, and setting boot cycle to CSM Legacy mode.

95% are the odds Legacy boot is supported - - you just have to find out how.   You may need to access the original owners or technicians manual PDF via the PC makers website.   Keep looking . . .

---

### Post by bernardlxy on 2017-06-27
> **RobGoss said:**
> Have you accessed your BIOS to see if Windows is in fact installed in Legacy / UEFI mode?




 [ATTACH=CONFIG]275783[/ATTACH]

Yeah this is a screenshot of my system

---

### Post by bernardlxy on 2017-06-27
> **yancek said:**
>  You probably need to explore the BIOS setup options a little more closely rather than the boot options.  The Ubuntu iso should be able to boot either, it did when I booted to install and from what I remember it was the different settings in the BIOS which made the difference.


Thanks, I'll look more into that!

---

