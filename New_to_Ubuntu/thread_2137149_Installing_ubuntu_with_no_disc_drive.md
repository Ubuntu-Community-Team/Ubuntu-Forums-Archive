---
title: "Installing ubuntu with no disc drive"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by shelznoct7 on 2013-04-19
I have just purchased a new dell inspiron 13z with windows 8 already installed. I have no disc drive. Windows 8 is complete garbage! I've been considering using linux for years and as of yet have not. I know very little about computers though I've been using them for quite a while. My question is, "can I install remove windows 8 and install ubuntu without a disc drive? I have a 16g usb thumb drive and several 1tb ext. drives. Ryan

---

### Post by Ender Shadow on 2013-04-19
Indeed you can. Check this link:

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Also, if you're installing Ubuntu on a Windows 8 laptop, use a 64-bit version of Ubuntu if possible.

---

### Post by pqwoerituytrueiwoq on 2013-04-19
1st thing to do is to decide on a desktop environment (Unity [Ubuntu],KDE [Kubuntu],XFCE [xubuntu],LXDE [lubuntu],Gnome [ubuntu gnome],Cinnamon [Linux Mint Cinnamon edition],Mate [Linux Mint Mate edition])
i would suggest using [unetbootin]("http://unetbootin.sourceforge.net/"), also i would recommend disabling this think called "secure boot" in your bios, it is a think that prevents boot loaders from being installed that MS has not signed off on being allowed to boot (not all version of linux can boot with it enabled)

the next version of ubuntu 13.04 comes out on the 25th the current testing stage is release candidate so i suggest just using that version (saves you the time of upgrading later), but use 64bit (aka amd64)
just google "xubuntu raring daily iso" (replace xubuntu with ubuntu, kubuntu, etc. if you want)

edit: here is a list of download links for the different versions:
ubuntu - [http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso)
xubuntu - [http://cdimage.ubuntu.com/xubuntu/daily-live/current/raring-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/daily-live/current/raring-desktop-amd64.iso)
kubuntu - [http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.iso](http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.iso)
lubuntu - [http://cdimage.ubuntu.com/lubuntu/daily-live/current/raring-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/daily-live/current/raring-desktop-amd64.iso)
ubuntu gnome - [http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/raring-desktop-amd64.iso]("http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/raring-desktop-amd64.iso")
mint cinnamon - [http://www.linuxmint.com/edition.php?id=118](http://www.linuxmint.com/edition.php?id=118)
mint mate - [http://www.linuxmint.com/edition.php?id=120](http://www.linuxmint.com/edition.php?id=120)

---

### Post by Hobao on 2013-04-19
I suggest you to download Ubuntu and Mint Cinnamon isos, to write the iso on a usb stick and to try both as live... so you can see if you like more Unity or Mint Cinnamon.
To be honest I prefer Mint Cinnamon over Unity but It is only a visual choice because both are great.

---

### Post by squakie on 2013-04-19
Since it is a new computer with Windows 8 pre-installed, you need to be very careful about UEFI before you try things.  I would recommend you PM user OldFred just asking them to look at your thread (include a link). It will be important to do this before attempting things.  I have PM'd an expert and asked them to check your thread, and they are experts regarding UEFI and what your options my be if you decide to completely punt Windows and go with Ubuntu (be sure to create your factory restore disks before doing anything ;) ).

---

### Post by DuckHook on 2013-04-19
> **squakie said:**
> Since it is a new computer with Windows 8 pre-installed, you need to be very careful about UEFI before you try things.  I would recommend you PM user OldFred just asking them to look at your thread (include a link). It will be important to do this before attempting things.  I have PM'd an expert and asked them to check your thread, and they are experts regarding UEFI and what your options my be if you decide to completely punt Windows and go with Ubuntu (be sure to create your factory restore disks before doing anything ;) ).

+++1

Excellent advice from @squakie.

I would only add that people often underestimate their reliance on Windows and sometimes come to regret their decision after Windows has already been nuked from their system. Given your confessed unfamiliarity with Linux, in addition to @squakie's advice, I encourage you to read these links to see if Ubuntu really is for you (and this is coming from a long-time Linux enthusiast).

"Linux is not Windows" http:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

General Ubuntu Intro:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

---

### Post by andrew.46 on 2013-04-19
> **shelznoct7 said:**
> I have just purchased a new dell inspiron 13z with windows 8 already installed. I have no disc drive. Windows 8 is complete garbage!

It does have some uses, perhaps try Ubuntu in VirtualBox before wiping your drive?

---

### Post by oldfred on 2013-04-19
squakie suggested I add my 2 cents.

While a few users have erased Windows and make the system only Ubuntu, I cannot recommend it, especially if you are not a seasoned Linux user. It took me about 5 years to stop dual booting and it was just one application that I got fairly quickly down to only booting Windows a couple of hours per week. But just about everyone has one application or game that they feel they need Windows for and it takes time to learn Linux.

If you may sell computer, you need to have Windows back on system. You should keep recovery partition, make complete set of DVDs to reinstall and/or do a full backup of the main system install and the efi partition. 

Since you have secure boot, you need the 64 bit version of any Ubuntu. Not sure but I do not think any of the other Ubuntu spin-offs have the secure boot UEFI. You can turn secure boot off and just boot in UEFI mode or even totally convert to BIOS mode, but then you cannot use Windows at all.

Some systems will boot Windows 8 with secure boot off. Some have to have it on and some only boot the Windows efi boot file and we have to do a work around so system thinks it is booting Windows but is really booting grub2's shim file that has the Microsoft signing key.

You should use Windows disk tools to shrink Windows partition and reboot several times to let Windows run chkdsk and make repairs due to knew size. 

      
 How you boot install media, live flash drive installer is how it will install. So you want to boot in UEFI mode.You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.

Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

Some other Dells that should be similar:
      
 Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)

 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)

---

