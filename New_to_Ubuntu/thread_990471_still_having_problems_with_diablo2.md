---
title: "still having problems with diablo2"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Dontechjuan on 2008-11-22
Hi, I've been trying to get diablo 2 to play on wine and I still can't get it to work! It seemed to install just fine but every time I try to play it the following message shows up.

Diablo II was unable to detect a disc in your CD-ROM drive. PLease make sure your Diablo II Expansion Disk is in your CD-ROM drive, then click on 'Retry'.

This message is in a warning note on the wine database howto, but i followed the instructions the best I could (though I'm not sure I followed them correctly). Below are the instructions from wine database...
-------------------------------------------------------
Running Diablo 2 under Wine

by Jesse Allen the3dfxdude at gmail com

minor updates by Jasmine Iwanek

Last updated 2008-07-11 - wine-1.0.0/1.1.1

Before you get started

This HOWTO only lists information specific to this app. Please keep comments and test reports brief. Please don't post copies of wine logs here! If you have trouble, see other ways of getting help.

Wine+Diablo 2 Status

Generally perfect for Linux users since wine 0.9.12. FreeBSD kernel 6.2 might work, but copy protection will likely be broken.

Minimum Requirements

    * winecfg: A drive letter for your cdrom, and running as Win2k, XP or later.
    * Support for 640x480 and 800x600 video modes.
    * Correct network configuration for online play.
    * A REAL COPY OF THE GAME -- The game probably won't work right if you don't have a real copy.

Recommended Requirements

    * Wine 0.9.20 or later
    * Linux kernel 2.6.17+ OR FreeBSD 6.2
    * Video card and driver that supports hardware based acceleration with OpenGL.

**Bad Versions**

It's recommended to not use these versions of software because they break the game's copy protection:

    * Linux vanilla x86 kernel: 2.6.9, 2.6.10
    * Linux vanilla x86-64 kernel: 2.6.9-2.6.15
    * Linux kernel versions less than 2.6
    * Wine built with GCC 4.0.0-4.0.2
    * Native msvcrt.dll
    * Fedora core 6 modified linux kernel, unless updated to 2.6.18-1.2784.fc6 or later.
    * FreeBSD
    * Incorrectly installed video drivers

Additionally, FreeBSD kernels less than 6.2 might not work with current versions of wine at all.

Installing the Game

Launch winecfg to perform the following tasks:

    * Make sure the Windows version for Diablo 2 is NT 4.0, 2000, XP, or 2003 for correct copy protection support. Diablo 2 supports Win NT 4.0 or later.
    * Create a drive letter for your cdrom if you have not already. For each cdrom drive letter, click advanced, and set the drive type from automatic to cdrom.

It helps to add a device node symlink, so do the following. If your cd-rom drive letter in winecfg is d: and the corresponding device node to your mount point is /dev/hdc then run the following command:
$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
Note, you *must* have two colons! You can tell what your device node is in /etc/fstab or viewing your boot-log.

For running the multi-disk install, it helps to run the install using the drive letter and to not switch your shell to the cdrom's path. For example:
~/.wine/drive_c$ wine "D:\setup.exe" (where D: is the assigned letter of your CD drive).
If you run while having a current working directory of /mnt/cdrom, for example, then you will lock the drive and you won't be able to eject the disk.

If during the game's install the progress bar stops, the game is probably prompting you for the next disc, but the dialog is under the installer's window. For full install, the order is Install Disc, Play Disc, then Cinematics Disc. Just swap discs and hit enter when the progress stops.

Running and Playing Diablo 2

Do not use the '-opengl' switch to run the game. Blizzard never completed OpenGL support so they removed it, but left the switch in. All you see when you run it is a badly initialized DDraw mode.

If you use the window option "-w", the game will drop to ddraw mode no matter what.

Do not use virtual desktop with the game! It's not designed to be windowed like that! It still thinks it's full-screen!

If you have missing in-game speech, animation, videos, or crashes between acts, these problems are typically from using a modified executable. Install your game properly.

Multiplayer Setup

Make sure you have the correct ports open. Open outbound and inbound, TCP and UDP, port 6112 and 4000. More on Network Ports

If you are going to play a direct TCP/IP game and the game tells you that it could not detect a valid address, make sure about things:

   1. Have a valid internet addressible IP address for internet play or proper NAT forwarding.
   2. Have a hostname other than localhost.
   3. In /etc/hosts, have a valid hostname of your computer listed with your current IP address you want to use and do not have your hostname listed with 127.0.0.1. Do not have "localhost 127.0.0.1" listed first either.

patching and running without cds

after you install the 1.12a patch copy as needed the files d2music.mpq from the play disk and d2xmusic.mpq from the expansion disk (if using Lord Of Destruction)
	

	
 
Warning

Copy Protection Final Word

Patch 1.12 from Blizzard disables the CD check.

If you ever get "Please insert disc", this is NOT a problem with detecting the CD. The protection system is probably still built into the game even though the CD check itself is disabled. Make sure you use version 1.12 or later. If you get this problem after having this version installed, you are likely suffering from a buggy video driver as this is the only known (and proven possible) cause at this point.

DO NOT USE NOCD PATCHES - They are pointless, and won't fix the real problem.
	

	
 
Warning

ALT-KEY COMBO WARNING

Window managers often have the alt key bound to certain features, especially the alt-click. THIS IS NOT A WINE BUG. If you have problems with the alt key in any way DO NOT REPORT IT. Fix your window manager. I'm not going to list steps for every one because there are too many possibilites. Figure out yourself or ask in a help forum (here is okay... but be warned all I use is TWM). If you are desperate, turn off window manager managed windows in winecfg.

KDE

Go into KDE Control Center, expand Desktop, click window behavior, then click window actions tab. You can turn off the alt-combos. If you want to make window specific settings, click on window specific settings under window behavior on the side.

GNOME

The option to change the key binding is in System Menu -> Preferences Menu -> Windows.
	

	
 
HOWTO: Blizzard Downloader

for wine versions 1.1.2 and earlier:

you need a native mshtml.dll and wininet.dll from ie6sp1 in ~/.wine/drive_c/system32

dont forget to set them as native in winecfg 
---------------------------------
Like I said I have it installed and supposedly patched (though I had to do that by downloading the patch directly from blizzard.com and running the patch). So what did I do wrong or what do I still need to do? And please put it in simple terms, I'm not a computer programmer and the instructions I listed above were a bit above my head (that's why I'm not sure I did it correctly). please help me.

---

