---
title: "Troubleshooting Common Installation Problems"
date: 2008-09-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Vivaldi Gloria on 2008-09-15
Here is a general list of things to try if ubuntu cd does not start or if it hangs during installation. There are some pages/videos linked at the end if you are looking for an installation guide.

Make sure that you have the latest ubuntu version downloaded from [[COLOR="Sienna"]download[/COLOR]]("http://www.ubuntu.com/getubuntu/download").
 
To learn how to burn an iso file to cd see [[COLOR="Sienna"]BurningIsoHowto[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto"). Also look at the videos [[COLOR="Sienna"]Infra_Recorder[/COLOR]]("http://screencasts.ubuntu.com/Infra_Recorder") and [[COLOR="Sienna"]Ubuntu_ISO[/COLOR]]("http://screencasts.ubuntu.com/Downloading_and_Burning_an_Ubuntu_ISO").


If ubuntu does not install then go through the following list.


**[COLOR="Blue"]1.[/COLOR]** Don't forget to choose "boot first from cd" in your bios settings.

**[COLOR="Blue"]2.[/COLOR]** Check the md5sum of the cd you are using (see [[COLOR="Sienna"]guide[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")) and burn it slow. 

**[COLOR="Blue"]3.[/COLOR]** Check that your sytem has the minumum specs:

> Ubuntu is available for PC, 64-Bit PC and Intel based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space.

If you're trying a [[COLOR="Sienna"]cli-only or server[/COLOR]]("http://ubuntuforums.org/showthread.php?t=882596") version of ubuntu then you need at least 128MB of ram. 

If your system doesn't satisfy the specs then may be you should look for a lighter OS: [[COLOR="Sienna"]ubuntuforums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=575456") - [[COLOR="Sienna"]floppy[/COLOR]]("http://www.linuxlinks.com/Distributions/Floppy/")

**[COLOR="Blue"]4.[/COLOR]** Google your computer model (or motherboard) and ubuntu. Seach [[COLOR="Sienna"]launchpad[/COLOR]]("https://launchpad.net/ubuntu") bug reports and [[COLOR="Sienna"]search[/COLOR]]("http://ubuntuforums.org/search.php") ubuntu forums. You can find a solution of your problem most of the time.

**[COLOR="Blue"]5.[/COLOR]** In the ubuntu install menu press F6 and play with [[COLOR="Sienna"]boot_options[/COLOR]]("https://help.ubuntu.com/community/BootOptions").

For example try 'noacpi' or 'noapic' or 'all-generic-ide'. If you are using a pre-2000 computer then you may also need an "acpi=force" line, see [[COLOR="Sienna"]this[/COLOR]]("https://answers.launchpad.net/ubuntu/+question/38113").

**[COLOR="Blue"]6.[/COLOR]** Sometimes an [[COLOR="Sienna"]error[/COLOR]]("http://www.proposedsolution.com/solutions/ps0017.php") can occur if you have installed Ubuntu on an NTFS Windows partition and Windows was incorrectly shutdown:

**[COLOR="Blue"]7.[/COLOR]** Get rid of every bit of non-essential hardware during installation. Unplug USB gadgets, remove unnecessary cards, disks etc. 

Also you might have a bad ram stick. Remove all ram sticks but one and change it with another one (incase it's the bad one) if it doesn't still install.

**[COLOR="Blue"]8.[/COLOR]** Try the alternate cd. You can download it from [[COLOR="Sienna"]download[/COLOR]]("http://www.ubuntu.com/getubuntu/download") by checking the box "Check here if you need the alternate desktop CD". Alternate CD only uses a text based installer so if the reason of your problems is graphics related then using alternate CD might help.

**[COLOR="Blue"]10.[/COLOR]** If you hava SATA problems look at these forum threads: [[COLOR="Sienna"]thread1[/COLOR]]("http://ubuntuforums.org/showthread.php?t=820161") - [[COLOR="Sienna"]thread2[/COLOR]]("http://ubuntuforums.org/showthread.php?t=912681").

**[COLOR="Blue"]11.[/COLOR]** I've seen a couple of computers in which all regular ubuntu CDs failed for some reason but only installing a [[COLOR="Sienna"]cli-only[/COLOR]]("http://ubuntuforums.org/showthread.php?t=882596") base system worked. After you install a base cli-system system, you can add a desktop environment. For example:

```
sudo apt-get install ubuntu-desktop
```

installs gnome.

Note that because of a bug in Hardy installer you need at least 128 MB ram to install cli-only ubuntu.

**[COLOR="Blue"]12.[/COLOR]** If nothing works then ask in the Installation & Upgrades [[COLOR="Sienna"]subforum[/COLOR]]("http://ubuntuforums.org/forumdisplay.php?f=333") and/or file a bug [[COLOR="Sienna"]report[/COLOR]]("https://launchpad.net/ubuntu").



**Ubuntu Installation Guides:** [[COLOR="Sienna"]Install[/COLOR]]("https://help.ubuntu.com/8.04/installation-guide/i386/index.html") - [[COLOR="Sienna"]All[/COLOR]]("https://help.ubuntu.com/community/Installation")

**Ubuntu Installation Videos:** The following videos are for a previous version of ubuntu but they are still helpful: 
[[COLOR="Sienna"]Install1[/COLOR]]("http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1") - [[COLOR="Sienna"]Install2[/COLOR]]("http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2") - [[COLOR="Sienna"]Xubuntu[/COLOR]]("http://screencasts.ubuntu.com/Installing_Xubuntu") - [[COLOR="Sienna"]Windows_Dual-Boot[/COLOR]]("http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot")

**Installing on a USB disk:** See the guides [[COLOR="Sienna"]here[/COLOR]]("http://www.pendrivelinux.com/").

**OS for old computers:** [[COLOR="Sienna"]ubuntuforums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=575456") - [[COLOR="Sienna"]floppy[/COLOR]]("http://www.linuxlinks.com/Distributions/Floppy/")

.

---

### Post by Vivaldi Gloria on 2008-09-15
This thread is intented as a general list of possible solutions to installation problems. Do not ask about your particular installation problems here. For that use the Installation & Upgrades subforum [[COLOR="Sienna"]here[/COLOR]]("http://ubuntuforums.org/forumdisplay.php?f=333") or wubi subforum [[COLOR="Sienna"]here[/COLOR]]("http://ubuntuforums.org/forumdisplay.php?f=234") if you are trying wubi.

Additions, corrections, and questions are welcomed. Especially, if you know another solution of various installation problems then please post it.

---

