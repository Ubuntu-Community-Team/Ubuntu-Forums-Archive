---
title: "Grub error"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by quarkhirad on 2012-02-27
In windows 7 i was resizing my partitions, by mistake i have deleted my root partition of my ubuntu 11.04 setup. Now when i restarted my laptop it gives the following error

> 
error: no such partition.
grub rescue>

I understood that my MBR is corrupt. How do i repair my MBR without installing ubuntu all over again. 
[B]
Please note:[/B] i have found solutions which say insert windows 7  cd (example is given below ). The trouble is i dont have a windows 7 cd. How do i do it using my ubuntu 11.04 setup cd. If you recommend another software please indicate where i can download it from.

[HTML]
http://www.ehow.com/how_4836283_repair-mbr-windows.html[/HTML]

---

### Post by audiomick on 2012-02-27
I daresay your MBR is not corrupted so much as looking for a partition that is not there anymore.

You say you have deleted your ubuntu partition. The only solution to that is probably to re-install. If you are really lucky, you may be able to re-construct what you deleted using data rescue tools if you haven't been using the drive since. The data is still there, as far as I know, until you save something over it. This is unfortunatly beyound my skills.

If there are no files on the Ubuntu install that you desperately absolutely have to recover, then I would suggest re-installing. I take it the Windows install still works? Doing a re-install should sort out your grub too.

If you haven't already, you might consider making a seperate partition for your /home. That would allow you to just re-install the Ubuntu OS and re-use the existing /home, which is where all your files and config files is.

---

### Post by oldfred on 2012-02-27
The Windows boot loader in the MBR is actually pretty simple. All it does is look for a active partition (boot flag) and jump to the partition boot sector to continue booting. Many other boot loaders use similar booting methods and will work to boot Windows.

The newest versions of Ubuntu may not have synaptic installed and I do not know how to turn on the universe repository from command line. 

If issues install synaptic and then enable universe as a source.
sudo apt-get install synaptic

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

Another way that installs the syslinux boot loader:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Once you get Windows booting:
Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by sidzen on 2012-02-27
OP said, ". . . by mistake i have deleted my root partition . . ."

Only option is reinstall, this time doing as audiomick says and create a */home* partition.

We all make mistakes, then we have to fix them -- Welcome to Linux, which assumes you know exactly what you are doing (as a Mod's signature states)!

---

