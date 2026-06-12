---
title: "Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by rdnavarre on 2014-02-05
I recently got Ubuntu 13.10 to work on my Samsung ATIV Book 9 Plus ultrabook and wanted to share some tips. I know some have had problems with the Samsung ATIV Book Lite, which is very similar, so I thought I'd share my experience. The following tips assume you have a bootable Ubuntu 13.10 USB stick..

**Setting up the BIOS/UEFI firmware** - The first problem I ran into was getting the UEFI firmware on my Samsung ATIV Book 9 Plus setup correctly. UEFI is the new 64-bit BIOS interface. Initially I got the "All Boot Options Are Tried" message because the Secure Boot and Fastboot options were enabled. Disabled them, insert your USB stick, and then save & reset your BIOS/UEFI firmware.


[LIST]
[*]Disable Secure Boot
[*]Select the CSM OS Option (Compatibility Support Mode)
[*]Disable Fastboot (Skips USB Detection when Enabled)
[*]Save & Reset
[/LIST]

**Disabling the FRAMEBUFFER** - The second problem I ran into was booting up to a blank screen. Because the BIOS/UEFI firmware is setup in CSM mode (which emulates old fashioned 16-bit BIOS calls) the installer's generic video drivers won't recognize your Intel Haswell ULT Touchscreen Graphics card which ultimately results in booting up to a blank screen. There's an easy way and a hard way to fix this:

 
[LIST]
[*]When the GRUB bootloader prompts you to Install Ubuntu, Press F6 (this is the easy way). Pressing F6 will display some options and you want to select the very last option NOMODESET which disables a portion of the RAM [framebuffer] that's built-in to your Intel Haswell graphics card. The active drivers on the bootable USB installer don't know how to utilize this yet.
[/LIST]


[LIST]
[*]Use the GRUB prompt (hard way) if necessary to edit "quiet splash" command which you can simply replace with "nomodeset" before GRUB mounts the Kernel and boots Ubuntu.
[/LIST]

**Partitioning your SSD Hard Drive** - Depending on how you choose to install Ubuntu you might be asked to partition or re-partition your hard drive. Just make sure you follow a "Global Partitioning Table" or GUID Partition Table (GPT format):


[LIST]
[*]1st Partition = FAT32 (500MB)
[/LIST]


			Mount Point: /boot/efi
			Flags: boot



[LIST]
[*]Additional Partitions = ext4 (115GB)
[/LIST]


			Mount Point: /
			Flags: (none)



[LIST]
[*]LAST Partition = linux/swap (4GB)
[/LIST]


			Mount Point: (none)
			Flags: (none)


**Install Ubuntu 13.10 **- Install Updates & Third Party Software

**Adjust Firmware Setup** - This is important because the third party drivers that are installed with Ubuntu will support your Intel Haswell graphics card and UEFI interface. If you try to reboot without adjusting your firmware you will get the "All Boot Options Are Tried" error message again. Don't forget to adjust your firmware:


[LIST]
[*]Keep Fastboot DISABLED
[*]Keep Secure Boot DISABLED
[*]Select UEFI OS
[*]Save & Reset
[/LIST]


**Install Boot Repair Tool **- There are two scenarios. 1. Your UEFI detects the GRUB bootloader (BEST CASE SCENARIO) or 2. Your UEFI doesn't detect the GRUB bootloader (NEXT BEST CASE SCENARIO). Either scenario is equally possible depending on how your partitioned your hard drive and whether or not your UEFI firmware is looking for a Windows bootloader or a Linux bootloader. Use the Boot Repair Tool to make sure your UEFI looks for the correct bootloader and also that your bootloader (GRUB) is installed in the correct partition. Open a Terminal (Alt+Ctrl+T) and enter the following commands to download and install the Boot Repair tool:


[LIST]
[*]~$ sudo add-apt repository ppa:yannubuntu/boot-repair && sudo apt-get update
[*]~$ sudo apt-get install -y boot-repair && (boot-repair &)
[/LIST]


**Reboot & Enjoy Ubuntu 13.10 **(Good luck!)

[LIST]
[*]~$ sudo shutdown -r now
[/LIST]

---

### Post by icypunkpixie on 2014-02-05
Isn't there a command to reboot without using the shutdown command?

---

### Post by nothingspecial on 2014-02-05
> **icypunkpixie said:**
> Isn't there a command to reboot without using the shutdown command?

Yeah, the command is ```
reboot
```

---

### Post by bc.haynes on 2014-02-05
I am sorry, but the second line doesn't sense make  to me (a noob). What did you intend to do with it? Why the parentheses?
```
    ~$ sudo add-apt repository ppa:yannubuntu/boot-repair && sudo apt-get update
    ~$ sudo apt-get install -y boot-repair && (boot-repair &)
```

---

### Post by Vladlenin5000 on 2014-02-06
Indeed. I think he meant something like:

```
sudo apt-get update && sudo apt-get install -y boot-repair
```

(Update is required whenever a PPA repository is added)

---

### Post by asoundmove on 2014-03-11
> **bc.haynes said:**
> I am sorry, but the second line doesn't sense make  to me (a noob). What did you intend to do with it? Why the parentheses?  ```
    ~$ sudo add-apt repository ppa:yannubuntu/boot-repair && sudo apt-get update
``` The above means add a repository to the database and update to see what's in it. ```
    ~$ sudo apt-get install -y boot-repair && (boot-repair &)
``` This one means get and install boot_repair, then run it in the background and give me my prompt back (does not run the install in the background, just boot_repair).

---

### Post by rizwan5 on 2014-04-15
Hi i have installed ubuntu and did that my removing windows 8.1 and replacing
i have done all these instructions and after installation i get the "All boot options are tried". even though i edjust my firmware i still get the same error.
What do i do?

---

### Post by enrish on 2014-04-21
Hi everyone, I just successfully installed Ubuntu 14.04 alongside Win 8.1 on this Ativ Book 9 Lite. And the procedure was simpler than the one described, i.e. no problems at all. I think much is due either to the new bios from Samsung or to the latest version of Ubuntu. 

Here are the exact step i took, on this machine (version with amd cpu): 
[B]
in Windows[/B]:

- i updated everything and the bios, to version P11RBV, using the samsung update  utility (it should be accessible via the samsung support center app you will find on your pc).

- I launched disk management and shrinked the main windows partition (in my case it was C) so to create some unallocated space for Ubuntu to install. I left it unallocated, without formatting it.

- I disabled fast start up: go to 
Control Panel --> Power Options --> Choose what the power button does

In here click on "Change settings that are currently unavailable" , **Uncheck** the option that says "Turn on fast startup". (credit to [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported))

Then I shut down. I inserted my live pen drive with Ubuntu 14.04 and turned on while pressing f2 to get to the bios.

**In the Bios**:

- I disabled fastboot

- I changed the boot order and moved the flash usb drive option on top

Just these two steps, i didn't disable secure boot or anything else.

I saved and exit. 

**Ubuntu installation**: 

The pc rebooted into the grub menu. 

-I picked "try ubuntu". Everything loaded normally so I choosed "install" ubuntu from there.

[SIZE=2]- Ubuntu did not see any windows partition, so it proposed to erase disk and install. I choosed "something else" (do not remember the exact label, anyway it was the last option)
[/SIZE][SIZE=3][SIZE=2]
[/SIZE] 
[SIZE=2]- I clicked on the unallocated space I previously prepared in Windows and formatted it to ext 4. Mount point:/[/SIZE]
[/SIZE] 
[SIZE=2][FONT=Times New Roman]
[/FONT][/SIZE][SIZE=2]I left everything as primary partition.[/SIZE]
[SIZE=2]
[/SIZE][SIZE=2]Once install was finished, I simply restarted and unplugged the flash usb drive. [/SIZE]
[SIZE=2]
[/SIZE][SIZE=3][SIZE=2]No need to go back to the bios,  it works just fine as is. [/SIZE]
[SIZE=2]
[/SIZE][SIZE=2]Once in Ubuntu remember to install the ati propietary drivers for the ati graphic card. [/SIZE]
[SIZE=2]
[/SIZE][SIZE=2]Hope it helps :)[/SIZE]
[/SIZE]

---

### Post by M!K3_$ on 2014-05-10
Has anybody tried this with 14.04 yet?

---

### Post by prontospray on 2014-05-12
> **M!K3_$ said:**
> Has anybody tried this with 14.04 yet?

I've been using Ubuntu on my ATIV Book 9 Plus (NP940X3G) frm the day I bought it. 
I actually completely removed the Windows (and associated recovery partition) and installed 13.x on it in December. 
I also recently completely reinstalled 14.04 on it and it works very well (HiDPI in Unity is nice).

---

### Post by prdfd on 2014-05-21
Does the touchpad in Samsung ATIV Book 9 Plus work out of the box with any version of Ubuntu? I've installed 14.04 in a new Samsung ATIV Book 9 2014 edition ( NP930X5J ), and the touchpad doesn't work at all (neither clicks nor scrolls), and I haven't found a fix yet (it does not even show in the Mouse & Touchpad options). I wonder if there's a driver available, or a command that will enable this.

---

### Post by rajeshxsankaran on 2014-07-05
> **prdfd said:**
> Does the touchpad in Samsung ATIV Book 9 Plus work out of the box with any version of Ubuntu? I've installed 14.04 in a new Samsung ATIV Book 9 2014 edition ( NP930X5J ), and the touchpad doesn't work at all (neither clicks nor scrolls), and I haven't found a fix yet (it does not even show in the Mouse & Touchpad options). I wonder if there's a driver available, or a command that will enable this.

I had the same problem. This is a kernel bug and you should be able to get your trackpad working by installing the 
Linux 3.15.0-031500-generic kernel. I am however unable to left click and select a region or text using using the 
trackpad. Any luck anyone?

---

### Post by felipemdra on 2014-09-10
I've installed 14.04 LTS today successfully. All drivers and software are OK.

Thanks [**[COLOR=#000000]rdnavarre[/COLOR]**]("http://ubuntuforums.org/member.php?u=1895020")

---

### Post by viltrio on 2015-06-01
Hello All,

I bought a second-hand samsung ativ 9 lite.
I followed several instructions from this thread and the laptop is working fine.

The main problem is that while the BIOS shows 4 Gb of RAM (and that was what the vendor also said), Ubuntu recognizes just 3.3.

I looked for solutions, but I did not really find anything relevant (most of them refer to old ubuntu versions or non-64bit kernels).
I finally ran a memtest and the result is that the amount of reserved memory is *very* high, at least by comparing it with results I have seen googling around:

Cached: 3527 M
RsvdMem 6144K

Could this be an index that something is not OK? Do you have any suggestions?

Thank you in any case, and thanks for the previous indications as well.
Cheers,

Vittorio

---

