---
title: "Dual boot - No Grub Menu"
date: 2023-07-13
forum: New to Ubuntu
---

### Post by subcook on 2023-07-13
Hi all,

I know this is probably very elementary but need a bit of help.   I've run into this problem many times.

I have two SSD drives, the first has Windows 10, the other I just installed Kubuntu, whatever the current LTS version is.


When I boot in, there is bootloader/GRUB menu, so ever timetime I boot in I would have to boot into BIOS to pick my OS...by default it goes straight to windows.

I just want to have the bootloader menu avaiable to me. 

I can tell you that if the two OS's shared tyhe same drive it wouldn't be a problem, but when I give each OS their own drive, this always happens.


Thank you in advance for your help

---

### Post by tea for one on 2023-07-13
Does your Windows drive have priority in your PC boot menu?
You will have to jump into UEFI settings to change the disk priority.
This should allow your Ubuntu disk containing grub to boot first.

---

### Post by subcook on 2023-07-13
I'm rusty...


How do I access the UEFI setting again ?    Through BIOS, right ?

---

### Post by subcook on 2023-07-13
Isn't the Safeboot (win) a potential issue as well ?

---

### Post by tea for one on 2023-07-13
> **subcook said:**
> How do I access the UEFI setting again ?    Through BIOS, right ?
Power on and use the dedicated key for your PC.
e.g. F2 for Lenovo

---

### Post by subcook on 2023-07-13
So I went into BIOS and there weren't a lot of options to to mess w/ UEFI settings.

Went to the boot manager to adjust boot priority.  I know I picked the correct SSD as it is now booting directly into Kubuntu.  Still no grub/boot menu though.

I'm stumped.

---

### Post by grahammechanical on 2023-07-13
> o ever timetime I boot in I would have to boot into BIOS to pick my OS.[QUOTE][/QUOTE]

UEFI is the modern version of the BIOS. So, you already know how to enter the UEFI. Now you have to set boot priority to the SSD drive that holds Ubuntu. When you load Ubuntu run

```
sudo update-grub
```

The printout should show the Windows OS detected.

Regards.

---

### Post by tea for one on 2023-07-13
> **subcook said:**
> I know I picked the correct SSD as it is now booting directly into Kubuntu.  Still no grub/boot menu though.
Your Kubuntu grub configuration may need to be edited.
```
sudo nano /etc/default/grub

```

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false -[COLOR="#0000FF"] Do you have this parameter?[/COLOR]

```
The default for Ubuntu 22.04 is GRUB_DISABLE_OS_PROBER=true

Don't forget to run [COLOR="#0000FF"]sudo update-grub[/COLOR] to save the new configuration.

---

### Post by subcook on 2023-07-13
I updated grub ....  still boots directly to Kubuntu.


Than I saw your second post and went ahead and nano'd/edited my /etc/default/grub file, also updated grub there too to be safe .......still boots directly to Kubuntu.

I'm just really not sure what I'm missing here ...

---

### Post by tea for one on 2023-07-13
Please post the file /etc/default/grub (within code tags for legibility)

---

### Post by subcook on 2023-07-13
[FONT=monospace][COLOR=#000000]menu# If you change this file, run 'update-grub' afterwards to update[/COLOR]
[COLOR=#18B2B2]# /boot/grub/grub.cfg.[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# For full documentation of the options in this file, see:[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]#   info -f grub -n 'Simple configuration'[/COLOR][COLOR=#000000][/COLOR]

GRUB_DEFAULT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

[COLOR=#18B2B2]# Uncomment to enable BadRAM filtering, modify to suit your needs[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# This works with Linux (no patch required) and with any kernel that obtains[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"[/COLOR][COLOR=#000000][/COLOR]

[COLOR=#18B2B2]# Uncomment to disable graphical terminal (grub-pc only)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]#GRUB_TERMINAL=console[/COLOR][COLOR=#000000][/COLOR]

[COLOR=#18B2B2]# The resolution used on graphical terminal[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# note that you can use only modes which your graphic card supports via VBE[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# you can see them in real GRUB with the command `vbeinfo'[/COLOR][COLOR=#000000][/COLOR]

[COLOR=#18B2B2]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]#GRUB_DISABLE_LINUX_UUID=true[/COLOR][COLOR=#000000][/COLOR]

[COLOR=#18B2B2]# Uncomment to disable generation of recovery mode menu entries[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]#GRUB_DISABLE_RECOVERY="true"[/COLOR][COLOR=#000000][/COLOR]

[COLOR=#18B2B2]# Uncomment to get a beep at grub start[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]#GRUB_INIT_TUNE="480 440 1"[/COLOR][COLOR=#000000][/COLOR]
GRUB_TIMEOUT_STYLE="menu"
GRUB_TIMEOUT="10"
GRUB_THEME="/boot/grub/themes/fallout/theme.txt"
GRUB_GFXMODE="auto"


[/FONT]

---

### Post by tea for one on 2023-07-13
From post no. 8
```
GRUB_DISABLE_OS_PROBER=false - [COLOR="#0000FF"]Do you have this parameter?[/COLOR]
```

---

### Post by subcook on 2023-07-13
No

---

### Post by subcook on 2023-07-13
Any ideas ?

---

### Post by tea for one on 2023-07-13
Add this to your grub configuration
```
GRUB_DISABLE_OS_PROBER=false
```
Then ```
sudo update-grub
```
Assuming that both Windows 10 and Kubuntu are installed in UEFI mode, you should see something like this:-
```
edited@edited-xubuntu23-04:~$ sudo update-grub
[sudo] password for edited: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-24-generic
Found initrd image: /boot/initrd.img-6.2.0-24-generic
Found linux image: /boot/vmlinuz-6.2.0-20-generic
Found initrd image: /boot/initrd.img-6.2.0-20-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
[COLOR="#0000FF"]Found Windows Boot Manager on /dev/sda4@/efi/Microsoft/Boot/bootmgfw.efi [/COLOR]
Adding boot menu entry for UEFI Firmware Settings ...
done
edited@edited-xubuntu23-04:~$ 

```

---

### Post by subcook on 2023-07-13
Can't get grub to update.   Current file looks like this :

[FONT=monospace][COLOR=#ffffff]  GNU nano 6.2                   /etc/default/grub                             [/COLOR][COLOR=#000000] [/COLOR]
menu# If you change this file, run 'update-grub' afterwards to update
[COLOR=#18B2B2]# /boot/grub/grub.cfg.[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# For full documentation of the options in this file, see:[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]#   info -f grub -n 'Simple configuration'[/COLOR][COLOR=#000000][/COLOR]

GRUB_DEFAULT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

[COLOR=#18B2B2]# Uncomment to enable BadRAM filtering, modify to suit your needs[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# This works with Linux (no patch required) and with any kernel that obtains[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"[/COLOR][COLOR=#000000][/COLOR]

[COLOR=#18B2B2]# Uncomment to disable graphical terminal (grub-pc only)[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]#GRUB_TERMINAL=console[/COLOR][COLOR=#000000][/COLOR]

[COLOR=#18B2B2]# The resolution used on graphical terminal[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# note that you can use only modes which your graphic card supports via VBE[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# you can see them in real GRUB with the command `vbeinfo'[/COLOR][COLOR=#000000][/COLOR]

[COLOR=#18B2B2]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]#GRUB_DISABLE_LINUX_UUID=true[/COLOR][COLOR=#000000][/COLOR]

[COLOR=#18B2B2]# Uncomment to disable generation of recovery mode menu entries[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]#GRUB_DISABLE_RECOVERY="true"[/COLOR][COLOR=#000000][/COLOR]

[COLOR=#18B2B2]# Uncomment to get a beep at grub start[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]#GRUB_INIT_TUNE="480 440 1"[/COLOR][COLOR=#000000][/COLOR]
GRUB_TIMEOUT_STYLE="menu"
GRUB_TIMEOUT="10"
GRUB_THEME="/boot/grub/themes/fallout/theme.txt"
GRUB_GFXMODE="auto"
GRUB_DISABLE_OS_PROBER=false

[/FONT]

...I than do sudo update-grub, and this is what I get :

[FONT=monospace][COLOR=#000000]Sourcing file `/etc/default/grub'[/COLOR]
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: menu#: not found

[/FONT]
I don't remember this being so hard

---

### Post by tea for one on 2023-07-13
```
sudo nano /etc/default/grub
```
Use the following as your grub configuration, just to see if it works OK.
Then, if it is functional, we can add the other parameters, which you deem essential.

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false
```

```
sudo update-grub
```

Please post the output (within code tags) after executing the update-grub command

---

### Post by bobunderwood99 on 2023-07-13
First line of grub:

not "menu#..." but

```
[FONT=monospace]
# If you change this file, run 'update-grub' afterwards to update[/FONT]
```

---

### Post by subcook on 2023-07-14
yea, I get that.   I clearly did something wrong.  I get this :


[FONT=monospace][COLOR=#54FF54]**pleh@PLEH**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo update-grub[/COLOR]
[sudo] password for pleh:  
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: menu#: not found

[/FONT]

---

### Post by tea for one on 2023-07-14
```
[COLOR="#FF0000"]menu[/COLOR]# If you change this file, run 'update-grub' afterwards to update
```
Remove the red text from the first line of your /etc/default/grub file.

---

### Post by Impavidus on 2023-07-14
If Windows is hibernated / FastStartup is enabled, update-grub may fail to detect Windows, even if OS-prober runs.

---

### Post by ajgreeny on 2023-07-14
Simply get rid of those quotation marks from the line 
GRUB_TIMEOUT_STYLE="menu"

It should be 
GRUB_TIMEOUT_STYLE=menu
then run ```
sudo update-grub
```

---

