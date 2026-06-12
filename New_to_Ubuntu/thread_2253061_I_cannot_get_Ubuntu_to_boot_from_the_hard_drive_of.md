---
title: "I cannot get Ubuntu to boot from the hard drive of a laptop running Windows 8.1"
date: 2014-11-16
forum: New to Ubuntu
---

### Post by Jon_Lambert on 2014-11-16
So, I have a laptop. It has Windows 8.1 on it. I used a USB flash drive to download and then use Ubuntu for a while. When I installed the OS, I allotted it 70 gigabytes of my hard drive and the install went well. Only, now, when I start up my PC, it automatically goes to the "HP" symbol with a little loading sign below it and flows to Windows. It never even gives the options of operating systems.

The goal was to create a dual-boot system with a choice between Ubuntu and Windows 8.1 upon startup. 

I have UEFI enabled now, but I had it turned off during installation. I can enable it again at need.

pls halp

---

### Post by grahammechanical on 2014-11-16
> [COLOR=#000000]I have UEFI enabled now, but I had it turned off during installation. I can enable it again at need.[/COLOR]

There you have it. Windows 8 is installed in EFI mode and by turning it off you installed Ubuntu in legacy mode. If you turn EFI back off you will be able to load Ubuntu but not Windows.

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by oldfred on 2014-11-16
You can use Boot-Repair's advanced settings to convert a BIOS install if on gpt partitioned drive and if you have efi partition to a UEFI boot. All it really does is uninstall grub-pc(BIOS) and install grub-efi(UEFI).

Also HPs do not directly boot Ubuntu from UEFI menu. You have to use one of the work arounds, most rename bootx64.efi.
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
            script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

            It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

            HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try different USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by Jon_Lambert on 2014-11-17
So, according to the first reply (I think), if I turn UEFI off, I will start booting in Ubuntu, but to boot in Windows again, I'll have to re-access it and switch it over. Hmm...

The other option seems to be to use various tools and tricks and workarounds that will take more knowledge than I have. Hrrmm...

So, I ask this: will the second commenter's suggestions cause loss of windows data or useability?

---

### Post by oldfred on 2014-11-17
Some systems require you to go into UEFI/BIOS and turn on/off UEFI or CSM/BIOS/Legacy mode. Some will auto recognize and you can use f10 or f12 one time boot key to choose which to manually boot. But you cannot use grub menu to choose.

You still need to have Windows set to not use fast boot and need to be careful not to write or not write much into Windows system partition from Linux.
       WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 

    
 UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)


 The main points are:

       EFI-mode booting can be faster. The difference can be several seconds, contrary to what K. Darien Freeheart wrote, but the difference also varies from one computer to another; on some computers, the speed benefit can be non-existent. The effect is felt mainly in the firmware initialization, not in the Linux boot process itself.
    An EFI-mode boot gives the OS access to certain EFI features. Today, the biggest of these is the ability to control the firmware's built-in boot manager, via the Linux efibootmgr utility. The kernel can also log crash data in NVRAM, but that's mainly of interest to developers. In the future, the number of things that can be done with an EFI-mode boot from a booted Linux distribution may increase.
    The much-maligned Secure Boot can actually provide some security benefits, if you choose to configure it properly. You might never need or notice these benefits, but if, at some point in the future, some pre-boot malware spreads and can infect Linux-based computers, you might be glad to have Secure Boot active.
    EFI provides new and different boot manager and boot loader options. In addition to GRUB, which is available for both BIOS and EFI, you can use rEFInd or gummiboot to choose the OS, and ELILO or the EFI stub loader to boot the kernel. See my page on EFI boot loaders for Linux for more on this topic.
    On some computers, booting from a GPT disk in BIOS mode requires jumping through some extra hoops. Thus, booting in EFI mode may save you a bit of effort if you've got an over-2TiB disk or if you just plain like GPT.

   Overall, these benefits are unlikely to be compelling for most people. Fortunately, switching boot modes is pretty easy. You can try it on a single-boot basis with most computers by preparing a CD-R or USB flash drive with my rEFInd boot manager. Boot to it and it should detect your Linux kernel(s) and let you boot it/them. (If you use a separate /boot partition, though, you'll need to add a root={whatever} kernel option by hitting F2 or Insert twice once you highlight the kernel.)

---

