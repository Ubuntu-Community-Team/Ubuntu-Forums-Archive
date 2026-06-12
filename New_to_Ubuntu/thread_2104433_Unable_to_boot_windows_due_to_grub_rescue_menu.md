---
title: "Unable to boot windows due to grub rescue menu"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by Smog555 on 2013-01-13
I can't boot to windows because grub rescue menu shows up. Fortunately I have a live usb that has ubuntu, which is how I am able to post this. Anyway I tried the boot tool and have a summary [http://paste.ubuntu.com/1526802/](http://paste.ubuntu.com/1526802/). 

What I wanted was to install ubuntu on a external hdd, which I did it worked out fine. Until I disabled the guest session by editing something and pasting something along the lines of " guest=false" or something like that. Then I decided to retore guest by simply editing again by deleting "guest=false" and hit save. Following that the external hdd would no longer allow me to boot ubuntu properly. 

My next step was to boot windows, format the external hdd and re-install ubuntu on it, however I was met with the grub rescue screen. which no matter what command I used it said "Unknown command".

I would greatly appreciate any help I recieve and I am new to the whole ubuntu area. Let me know any additional info I can provide to help you help me.

---

### Post by Smog555 on 2013-01-13
This second post was made to simply subscribe to myslef.

---

### Post by von Corax on 2013-01-13
If I've understood you correctly, I think you've done the same thing I did the first time I tried to install to and external HD. If, when you first installed, your internal HD was still connected, you overwrote your Master Boot Record with Grub. I did that, and then I couldn't boot back into Windows unless my Ubuntu drive was connected. Then when you reinstalled, you probably changed the identity of your Ubuntu volume somehow so Grub no longer recognizes it and panics.

If this is the case, the recovery turns out to be fairly simple, as long as you have either your Windows (I'm assuming Win7) install disc, a Win7 recovery disc, or access to another Win7 machine and a blank CD.

If you don't already have a recovery disc, find another machine, insert a blank disc, the go to **Start->All Programs->Maintenance->Create a System Repair Disc** and follow the instructions.

Once you've done that, boot from your new recovery disc, drop to a command prompt, and run the command [FONT="Courier New"]bootrec.exe /FixMbr[/FONT].
You should now be able to boot from the machine's internal HD. If that doesn't work, apparently the next step is [FONT="Courier New"]bootrec.exe /FixBoot[/FONT]. Beyond that, Google "bootrec.exe" to find out what the bigger hammers are.

To create a stand-alone bootable HD without fnrgling the host machine's MBR, everything I've read says you have to unplug the host machine's internal HD first, to force the installer to write Grub to the external drive. I've got that working up to a point, although the "portable" aspect still eludes me and I have my own thread asking for help with that.

Hope this helps.

---

### Post by audiomick on 2013-01-13
> **von Corax said:**
> 
To create a stand-alone bootable HD without fnrgling the host machine's MBR, everything I've read says you have to unplug the host machine's internal HD first, to force the installer to write Grub to the external drive. 

Unless the installer has changed, this is not true. There is a step in the installer where you can tell it where to write grub to.

I think von Corax is on the right track, though. I don't understand everything in the boot info, but your boot info shows that grub was indeed installed to sda, which is the drive that windows is on. If you want to be able to boot into windows without the external unplugged, you will need to set the mbr on that drive back to a windows mbr. You would need the grub install on the external, and the boot order in the bios set to look for the external first and then the drive with windows on it, so that it reads grub first if it is there, and reverts to the windows mbr when the external is not plugged in.

Looking at this
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

which is presumably the "boot tool" you referred to, I can see a little way down the page in this section
[https://help.ubuntu.com/community/Boot-Repair#Advanced_options]("https://help.ubuntu.com/community/Boot-Repair#Advanced_options")

that boot repair offers an option to restore a windows mbr. This would save you having to make a windows boot repair disk.

---

### Post by Smog555 on 2013-01-13
Thanks for responding.
 I managed to get to windows(I'm on Vista BTW) and did so by reconnecting the external hdd and a purple menu appeared. I assume its the grub. Anyway I will do as you say I have a question though, I have done recovery disks in the past and it took 16 DISCS, is it the same type of recovery discs? 
Also I'm afraid to turn of my machine only to not be able to boot to windows again, unless I get the recovery disc. 
Once again tanks for the response.

---

### Post by Smog555 on 2013-01-13
Also I will no longer be able to use the same technique(I think) to boot to windows since I formatted the partition on the external hard drive that had ubuntu on it. Unless I install  it again to it.
Anyway it may be a little side tracked but when im on the purple screen(grub?) or when windows is resuming the screen is a little cut off so part of the left side is missing or when windows shuts off in a not proper way and the options to start windows normally and the like the screen there is cut off as well. Do I need to install drivers?

---

### Post by Smog555 on 2013-01-13
> **audiomick said:**
> that boot repair offers an option to restore a windows mbr. This would save you having to make a windows boot repair disk.

I actually tried the fix mbr and checked the box but it did not work.

---

### Post by von Corax on 2013-01-13
> **Smog555 said:**
> Thanks for responding.
I have a question though, I have done recovery disks in the past and it took 16 DISCS, is it the same type of recovery discs?


I don't think so. That sounds like you did a full backup, intended to restore most or all of your files onto a blank hard drive. The Windows repair disc I made took up less than one CD, and is meant to repair a damaged operating system, not to reinstall it or to recover any user files.

It's probably worth making a repair disc anyway, as it will have system maintenance tools on it that cannot be run on the active startup volume.

---

### Post by von Corax on 2013-01-13
> **audiomick said:**
> 
[QUOTE=von Corax;12452893]To create a stand-alone bootable HD without fnrgling the host machine's MBR, everything I've read says you have to unplug the host machine's internal HD first, to force the installer to write Grub to the external drive.

Unless the installer has changed, this is not true. There is a step in the installer where you can tell it where to write grub to.
[/QUOTE]
It may have changed. I was installing 10.04 LTS (to replicate the school lab systems) and I don't recall seeing that function.

---

### Post by oldfred on 2013-01-13
The various options on how to install vary on whether you get a choice on where to install the boot loader - grub2.

Autoinstall essentially assumes you are installing to one drive and installs grub to sda. Usually BIOS is set to boot from sda, so then you can boot with grub.  But if installing to an external or any second drive, that may not be where you want grub. If you use the Something else or manual install, then you get the option of a combo box at the bottom of the partitioning screen on where to install the grub2 boot loader. It usually presents partitions also which you almost never should use.

The Windows repairCD or flash is only about 256K.
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
 [http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by presence1960 on 2013-01-13
you can get windows to boot by installing lilo from the ubuntu live cd/usb. Boot from the ubuntu live cd/usb. When desktop loads open a terminal and run ```
sudo apt-get install lilo
```

ignore warning and continue. Once installed run in terminal ```
sudo lilo -M /dev/sda mbr
```

once completed reboot without live cd/usb and you should boot right to windows.

---

### Post by Smog555 on 2013-01-13
Alright it has been solved, thank you all who have contributed to my solution.
Now I just need to mark as solved.

---

