---
title: "help in installing ubuntu"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by shashwat0805 on 2008-05-05
i have a windows xp service pack 2 so all i need to lnow is hat can i have ubuntu and xp both simultaneously on my system

---

### Post by logos34 on 2008-05-05
Sure, no prob:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by HunterThomson on 2008-05-05
1- back up important data
2- defrag windows
3- set BIOS to boot from cd
4- pop in ubuntu cd and reboot
5- run live cd
6- use Gparted or whatever the partitioner their is on the live cd to shrink the windows partition down about 20GB or more at lest 8GB i think
7- reboot and leve the cd in so it boots into the live cd agin
8- on the desktop of the OS on the live cd there is a icon to install click on it
9- in the partitioning section select the option to install to the longest continues free space and use 100% of it.
all should be chary now

:guitar:

---

### Post by Paqman on 2008-05-05
> **shashwat0805 said:**
> can i have ubuntu and xp both simultaneously on my system

Absolutely. You can try out Ubuntu without making any changes to your system by booting up the LiveCD.

If you're happy with it, the easiest way to install is to pop in your Ubuntu CD (when you're in Windows) and follow the prompts.

---

### Post by HunterThomson on 2008-05-05
> **Paqman said:**
> Absolutely. You can try out Ubuntu without making any changes to your system by booting up the LiveCD.

If you're happy with it, the easiest way to install is to pop in your Ubuntu CD (when you're in Windows) and follow the prompts.

So the installer will resize the window$ partition then... Well that is EZ. I didn't know that. That installing in widow$ new thing seems like a bad idea to me. If for no other reason it would be harder to to rid the computer of the Window$ worm latter... Right?

---

### Post by Paqman on 2008-05-05
> **HunterThomson said:**
> So the installer will resize the window$ partition then... Well that is EZ. I didn't know that. That installing in widow$ new thing seems like a bad idea to me. If for no other reason it would be harder to to rid the computer of the Window$ worm latter... Right?

If you install the way I mentioned (called Wubi) you don't have to resize any partitions at all. It installs Ubuntu into a virtual hard drive on the same partition that Windows is on.

If you want to transform that into a traditional Ubuntu install later on, you can use LVPM to move it to it's own partition. You could then delete Windows if you wanted.

---

### Post by sailor2001 on 2008-05-05
a suggestion:  in windows, download and print-out BELARC so you have an information copy of all your hardware in case you need it to set-up wireless or graffic card in ubuntu.

---

