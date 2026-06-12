---
title: "Partition install, afraid of writing over windows files."
date: 2013-09-30
forum: New to Ubuntu
---

### Post by tucker3 on 2013-09-30
Recently installed Ubuntu and am liking it so far. I used the installer that comes with 12.04 version and installed it to a separate partition on the hard drive. Upon booting up and now using it, it seems to not have installed on the partition but rather the main Windows partition. I am thinking this because when I open disk usage analyzer it shows my whole drive. When I look had my partitions set in windows it had a 50 GB partition that I was putting Ubuntu onto (now it has changed). I'm rather new to this (hence absolute beginners section) and maybe someone could explain where any data that I will be saving will be saved to and or maybe allocating more space to Ubuntu (without going into my windows partition). Thank you. I've attached some photo to help with the explanation.

---

### Post by oldfred on 2013-09-30
Please change your inline screen shots to attachments. You can easily attach screen shots with the paperclip icon in the Go Advanced editor.

You show /host which means you install wubi inside Windows. Wubi is for an extended test over liveCD or flash drive installer version, but is not intended for long term use. It also saves repartitioning which many users do not want to do.

       wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)


 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

      
 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

     


      
 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by Impavidus on 2013-10-01
You installed Ubuntu in the 54GB partition, but it's still a Windows partition. You'll find some huge files there, which are used for the virtual Linux partition used by Ubuntu. All your files are safe and at the location where they used to be. Any files you save in Ubuntu will by default end up on the virtual partition, stored in the file named root.disk on the 54GB Windows partition.

Your virtual partition can be at most 30GB in size. If you want more (suggested by the fact you made a 54GB partition to install Ubuntu), you'll have to do a side-by-side installation on a separate partition, which this is not.

---

### Post by tucker3 on 2013-10-01
Thank you, I will follow the migration instructions to get the wubi install on another partition. Quick question though when I do that will it mess up the windows boot loader and no be able to get into Ubuntu once I move it?

---

### Post by oldfred on 2013-10-01
A full install will put the grub2 boot loader into the MBR. And grub will offer to boot Windows. Only in rare cases may you have issues booting Windows if Windows otherwise boots. Grub will not get you into a non-working Windows. Best to have a Windows repairCD or flash drive.
You can also uninstall wubi from Windows and need to remove the wubi entry from the Windows boot menu or BCD.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by newb85 on 2013-10-01
Once you migrate to a real partition, your machine should load the Grand Unified Bootloader (GrUB), which will load Ubuntu or chainload Windows.

---

