---
title: "Not just the plain old External Hard Drive Question!"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by mirage22 on 2008-08-18
Hello to all,

This is my first post.... :KS

i searched the forums for quite some time, but did not get the specific answer I am looking for! 

So here goes?... hope u dont find it too repetitive :)

1) I have 2 laptops and a desktop. (one of the laptops being an office laptop, but with no restrictions on usb / internet etc etc)

2) I want to purchase an External HDD. Most likely a Seagate.

3) The plan is, to format the External HDD to give it enough space to load Ubuntu from it. (if needed, allow enough space for a future upgrade too)

4) However, the rest will be an NTFS partition - which Ubuntu can access. - Right?

[B]can i do the following? (all systems allow booting from USB)
[/B]
a) for my desktop and personal laptop, if i attach the USB before powering it 'ON', - can I boot from the External HDD. - I know the answer is YES - if GRUB is loaded on the EXT HDD. - Learnt it in the forums. But will it create Driver issues?
Tomorrow if i try booting it from another system (not mentioned above)... will it boot normally?

b) For my office laptop, can I run Linux just by attaching linux, when Windows Vista is running? and just click Ubuntu - from some shortcut in the NTFS partition, that will wake up the sleeping giant - ubuntu?
Something like how the persistent linux installation does. But of course, Linux would be installed in an unreadable partition to Microsoft Windows - I do not want to install a VM or some drivers to the office laptop.

I want to know this, so that I can also make it work on laptops of colleagues by just plugging in my linux hardrive to their laptops and work... or say, in a cybercafe, where you can just plugin and work when you want, on your own system, while the background OS still runs!

Thanks a lot in advance...

and I hope this is a challenging question for you... :)

---

### Post by nicedude on 2008-08-18
Nope what you are asking is a quick trip to a tale of woe. You can't install to an external and then access that install on multiple computer makes by just booting up. I would not even attempt this at all as the only way I see it working anyway is if the PC's were the exact same model and even then it would take some major doing if you wanted them to still boot to windows without that external plugged to them. You see GRUB's files go in 2 locations , first the hard disks MBR and then usually your Ubuntu partition. So if you left laptop A and plugged into laptop B then laptop A would no longer have access to vital files it needs from the /boot/grub/ directory on the Ubuntu partition and therefore would not boot.

Researching dual booting is a much more sane project, good idea you had it just won't work. So instead think about resizing some Vista partitions and installing Ubuntu to the laptops themselves GRUB and all and then you can still use a portable hard drive to transfer data between the machines.

Sorry to be a party pooper on this one, but I am glad you posted that before you tried it as fixing that would be a major job :-)

EDIT

oops I forgot, Welcome to Ubuntu

---

### Post by ingeva on 2008-08-18
> **nicedude said:**
> 
Sorry to be a party pooper on this one, but I am glad you posted that before you tried it as fixing that would be a major job :-)



A Better idea for an external drive would be to use it only for data files, and make the computer be dual-bootable from the hard disk. It could well be an NTFS disk, or with both NTFS and Linux partitions, because Linux can use both but Windows of course only Windows partition formats (FAT32 or NTFS).

Both Linux as well as Windows will mount such drives when you plug them in, but it's important to dismount them before pulling the plug, to ensure that the disk is "closed" and everything is written to the disk before you do.

---

### Post by mirage22 on 2008-08-18
> **nicedude said:**
> So if you left laptop A and plugged into laptop B then laptop A would no longer have access to vital files it needs from the /boot/grub/ directory on the Ubuntu partition and therefore would not boot.

EDIT

oops I forgot, Welcome to Ubuntu


Thank you for the welcome, and thank you for the details...

argument: [http://ubuntukids.org/blog/?p=69](http://ubuntukids.org/blog/?p=69)

What it tells here, is  how to install GRUB excusively to the External Hard-drive, and how to avoid it touching your Laptop.

So will I be able to port this external hard-drive anywhere, and just plug it into any laptop or PC?

thanks a lot for your quick help!

---

### Post by kansasnoob on 2008-08-18
> But will it create Driver issues?

That would be my greatest fear. All three machines would have to have basically the same audio & video requirements! The graphics thing scares me the most! You could cook a display with improper settings!

Would they all three even have the same screen resolution? Same drive layout? Same network abilities?

But, if you decide to risk it the easiest way I've found to install Ubuntu to an external drive is to physically disconnect all internal drives, and make sure your BIOS is set to boot from usb before booting from the internal drive.

---

### Post by nicedude on 2008-08-18
He should in no way do this, if he does he will be borrowing a PC to come here and post a tale of woe. You cannot install Ubuntu to an external and then just install Grub on 2 laptops and a desktop and expect it to work. Please forgive me to the person who asked this, I see you thanked me but I am saying it again for all to see, in case someone sees this and thinks it works.

DO NOT DO WHAT THIS NICE PERSON ASKED YOU WILL BE SORRY I PROMISE YOU THAT

---

### Post by kansasnoob on 2008-08-18
> **nicedude said:**
> He should in no way do this, if he does he will be borrowing a PC to come here and post a tale of woe. You cannot install Ubuntu to an external and then just install Grub on 2 laptops and a desktop and expect it to work. Please forgive me to the person who asked this, I see you thanked me but I am saying it again for all to see, in case someone sees this and thinks it works.

DO NOT DO WHAT THIS NICE PERSON ASKED YOU WILL BE SORRY I PROMISE YOU THAT

What, you don't like the smell of burnt 'tronics? :)

---

### Post by thestig_992 on 2008-08-18
if you really want to have an os that you can use on multiple computers, try some of the tutorials at [www.pendrivelinux.com](www.pendrivelinux.com) . You can do ubuntu on an external drive, but i havnt tried yet. I have done pendrive linux though, which is specially configured for USBs...and that works fine across multiple computers because the BIOS boots from USB before booting grub on ur main hdd. you can also point grub at the main drives from ur USB or vice versa. 
Still, becareful of driver issues...dont go formatting untill youve done some proper testing...

---

### Post by euffth on 2008-08-18
Dear mirage 22

I will tell you what installation I have done, and I hope it's of interest to you.

I have a desktop computer and a laptop. They are both not of the last generation (both have WindowsXP on them).

On each of them I added 3 (or more) different LINUX-Systems on the hard disc that work OK, but that's not your question.

Then I started using usb-HDD's (and usb-memory sticks, for that matter). When I put a Linux-System on a usb-HDD I added a starting entry to the already existing Grub-Loader on the IDE-HDD. That worked.

But I wanted to start up Linux from the usbHDD without the help of the IDE-HDD, so the usb-Linux can start even with no IDE-HD inside the computer.
First I installed debian Lenny on the usb-HDD. When the boot loader install chapter came, I installed it into the MBR of the usb-HDD.
Now, after restart, I had to choose 'USB-HDD' in the Boot sequence of the BIOS. The debian Lenny started OK. Then I shut down and connected the usb-HDD to my Acer Laptop. In the Acer-BIOS I moved the usb-HDD up as first boot device.
The debian Lenny started then up without any problems. No problem with drivers, no problem with the display, no problem with a installed wlan. No smell of burnt electronics... I could now move the usb-HDD freely forth and back from the Laptop to the Desktop and start that Lenny as often as I wished, just by choosing 'usbHDD' in the BIOS.

Then I put on the same usbHDD, on another two different partitions, 1. a Ubuntu Hardy heron and 2. a mixture of Ubuntu and Kubuntu (possibility to switch the Desktoop between KDE and gnome). I added the necessary boot entrys by hand in the already existing menu.lst of the debian Lenny system. Now both these new systems work well, on the Desktop computer as well as on the laptop.
I also installed a debian Lenny onto a usb memory stick with the grub loader into its MBR. This system also worked well on the Desktop computer and on the Acer laptop.(Long operation of such a system is not recommended as the allowed write cycles of the memory stick are reached soon).

==================================================================================
Now comes the HOWEVER:

I recently bought a new desktop computer (for my wife to watch the internet) that has WinVista preinstalled.
With this computer I cannot start my usbHDD-LINUX as I had hoped for. It just won't start.
I understand that the new AHCI-BIOS in connection with the TPM mechanism is intended to prevent malicious modification of the MBR and boot sector. But still, it seems to harden the cooperation of Vista and grub...
As I understand, there is a new loader (WUBI) for this, but I haven't read enough about it so far.
The only thing I succeeded so far was to make a special boot CD for that computer that boots and then I change over to the usbHDD, not a very elegant solution.
==================================================================================

NOTE:
When I wrote above about moving the usbHDD freely between the Desktop computer and the laptop, I didn't mention I am using two different entrys in the menu.lst. The different line is:
kernel		/vmlinuz root=/dev/sdb1 (for the laptop)
kernel		/vmlinuz root=/dev/sdc1 (for the desktop computer).
This is due to the fact that the laptop has one IDE-HDD and the desktop computer has two. (This is a debian Lenny menu.lst. I think a Ubuntu menu.lst should avoid this by using the UUID-Identifikation for the HDD.)

If you have any questions don't hesitate to ask.

---

### Post by cosine352 on 2008-08-18
I have installed Ubuntu in an external hard drive and it works great in different computers (totally different computers). I installed it using my notebook (I removed the internal hard drive during the installation). I can use it in different computers in my work. It works for me.

---

