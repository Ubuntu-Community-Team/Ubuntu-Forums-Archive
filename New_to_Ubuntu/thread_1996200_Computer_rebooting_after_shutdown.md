---
title: "Computer rebooting after shutdown"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by Webgazer on 2012-06-04
I am a beginner to linux, and recently got a new computer and installed Ubuntu on it. It's working well except for one problem, as described in the title:

Every time I shut down the computer, it reboots after a few second wait.

I did some searching and read another person's [account]("http://ubuntuforums.org/showthread.php?t=1833115") who discovered the cause was that they had an old kernel running. I thought that could be the cause of my problem too since I had some problems when first installing and might have installed more than once.

I followed these instructions:

[http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/)

And purged the older of the two.

And now all I have left is:

ii  linux-image-3.2.0-24-generic-pae       3.2.0-24.39                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic-pae                3.2.0.24.26                             Generic Linux kernel image

So I think there are no older installed kernels on my machine.

Any way, that didn't fix the problem. The machine is still rebooting a few seconds after shutdowns.

*Edit, I tried:

sudo shutdown -h now

but still got the same auto-restart problem.

Any suggestions would be greatly appreciated

---

### Post by idoitprone on 2012-06-04
> **Webgazer said:**
> I am a beginner to linux, and recently got a new computer and installed Ubuntu on it. It's working well except for one problem, as described in the title:

Every time I shut down the computer, it reboots after a few second wait.

I did some searching and read another person's [account]("http://ubuntuforums.org/showthread.php?t=1833115") who discovered the cause was that they had an old kernel running. I thought that could be the cause of my problem too since I had some problems when first installing and might have installed more than once.

I followed these instructions:

[http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/)

And purged the older of the two.

And now all I have left is:

ii  linux-image-3.2.0-24-generic-pae       3.2.0-24.39                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic-pae                3.2.0.24.26                             Generic Linux kernel image

So I think there are no older installed kernels on my machine.

Any way, that didn't fix the problem. The machine is still rebooting a few seconds after shutdowns.

*Edit, I tried:

sudo shutdown -h now

but still got the same auto-restart problem.

Any suggestions would be greatly appreciated

ACPI aka Abominable crap produce by intel aka advance configuration and power interface a very complex specification that irrates all kernel developers

please post your make of make of your pc and chip and etc
```
 dmidecode -t 0
```people here will need to know if you chipset is new and etc

i only here to start this thread, since i am an idoit and the Abominable crap produce by intel is beyond me

---

### Post by Webgazer on 2012-06-04
Thanks for the suggestion.

Here's what I got:


SMBIOS 2.7 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Intel Corporation
	Version: SLZ7710H.86A.0055.2012.0319.2140
	Release Date: 03/19/2012
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 8192 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
		UEFI is supported
	BIOS Revision: 4.6

---

### Post by idoitprone on 2012-06-04
> **Webgazer said:**
> Thanks for the suggestion.

Here's what I got:


SMBIOS 2.7 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Intel Corporation
    Version: SLZ7710H.86A.0055.2012.0319.2140
    Release Date: 03/19/2012
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 8192 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 4.6
processor?
computer manufacter?

---

### Post by Webgazer on 2012-06-04
The processor is an Intel Core i5-3450, and the system is custom built.

---

### Post by idoitprone on 2012-06-04
> **Webgazer said:**
> The processor is an Intel Core i5-3450, and the system is custom built.

you might need to install a newer kernel

[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds#Kernel.2BAC8-FAQ.2BAC8-DebuggingMainlineBuildsSupport.Does_the_kernel_team_support_the_mainline_kernel_builds.3F](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds#Kernel.2BAC8-FAQ.2BAC8-DebuggingMainlineBuildsSupport.Does_the_kernel_team_support_the_mainline_kernel_builds.3F)

go to that wiki
there should be links to the latest kernel builds for ubuntu
download the kernel that matches your archtecture 64 bit or 32
and matches your kernel version. This might help 

in the mean time
when you get to grub
I believe the the command prompt is the c key
press c
type halt 
press enter 

to shutdown your computer

---

### Post by Webgazer on 2012-06-05
Thanks for the reply.

I don't see the Grub menu as it automatically transfers me to the kernel when booting up.

Regarding the kernel, I'll try to do what you suggested and install the newest one. Shouldn't I have the newest kernel now since I downloaded the latest version of Ubuntu? Or does the latest release of Ubuntu not include the latest kernel?

---

### Post by NikTh on 2012-06-05
> **Webgazer said:**
> Thanks for the reply.

I don't see the Grub menu as it automatically transfers me to the kernel when booting up.

Regarding the kernel, I'll try to do what you suggested and install the newest one. Shouldn't I have the newest kernel now since I downloaded the latest version of Ubuntu? Or does the latest release of Ubuntu not include the latest kernel?

When pc boots you can hold down or press up-down(quickly)  the "Shift" key to see the grub menu. 
Try all suggestions above but try this also to see if works 
When you are to the grub menu at the first option (its the ubuntu entry that you will boot) press 'e' , then with arrow keys go to the third line(4th line i don't remember exactly , sorry) and after "quiet splash" options leave a space and write **reboot=a,w** 
Then press F10 to boot and try to reboot to see if this option fixed your problem. 
If yes we can do it permanently then.

---

### Post by Brandel Valico on 2012-06-05
Here is something you can try.

Fair warning this did work for me. But I can't promise it will work for you.

Open a terminal and type "sudo gedit /etc/default/grub" minus the "" into the terminal. Then type in your password.

You made need to use this command "sudo nano /etc/default/grub" as an alternate if gedit is not installed on your computer.

In the window that opens you need to add some things to a cmd line
 
You should see a line that looks like the one below. You need to add the bolded text.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **i8042.nomux=1 i8042.reset**"


Give it a try and see if it works. if it does then great. If it doesn't then revert the changes.

---

### Post by idoitprone on 2012-06-05
> **Webgazer said:**
> Thanks for the reply.

I don't see the Grub menu as it automatically transfers me to the kernel when booting up.

Regarding the kernel, I'll try to do what you suggested and install the newest one. Shouldn't I have the newest kernel now since I downloaded the latest version of Ubuntu? Or does the latest release of Ubuntu not include the latest kernel?

Nope, a distro process is long and slow. By the time the linux distro is released, a new kernel is released. Linus and group do not sit around. They continue to keep merging changes to the kernel constantly.

Ubuntu 12.04 kernel is 3.2
Newest kernel version right now is 3.4

@Brandel Valico
Isnt that suggestion is little archaic in comparison to the OP's new Ivy Brigde PC

---

### Post by Brandel Valico on 2012-06-05
Yeah, it is, its also archaic compared to my own system. But it worked.

---

### Post by Webgazer on 2012-07-25
The only solution that works is typing 'halt' in the command line when I reach GRUB. The machine will automatically reboot after it turns off otherwise.

---

