---
title: "sound is dead please help"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by xmunk on 2008-09-23
Hi Im running hardy and suddenly my sound just died. was watching youtube then stopped to eat came back no sound in firefox, vlc, mplayer, audacious, or anything else. i've switched my sound settings to alsa to pulse, to oss, and still nothing. I'm at a bit of a loss. tried [http://ubuntuforums.org/showthread.p...+sound+problem](http://ubuntuforums.org/showthread.p...+sound+problem) didn't work tried switching sound servers after all that and still doesn't work.

any help will be appreciated

---

### Post by skippuff54 on 2008-09-23
what kind of soundcard are u workin with? sometimes u need to follow specific instructions for certain cards. to check do in terminal ```
sudo lspci
```

---

### Post by xmunk on 2008-09-23
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GS (rev a2)

---

### Post by kansasnoob on 2008-09-23
Have you also been experiencing Firefox crashes? Flash video not working like it should?

---

### Post by xmunk on 2008-09-23
ive been running this install without a single problem for 3 months till last night.  i paused a youtube video went for a cig and came back to no sound at all from anything. restarted alsa and the computer hopin it might work itself out but seems that was wishfull thinking lol

---

### Post by kansasnoob on 2008-09-23
Well I found an excellent solution to flash/pulse audio problems. Look at post #7 here:

[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)

This is for Hardy only!

---

### Post by bumanie on 2008-09-23
Same happened to me with a kernel update. If you've had a kernel update, boot with the previous kernel.

---

### Post by xmunk on 2008-09-23
kansa i tried that and it didn't work.  I have no sound anywhere in my system.

bumanie oddly i looked in my grub and i only have one kernal 2.6.24-19-generic.   coulda swore i had more was that the one you had problems with?

---

### Post by bumanie on 2008-09-23
Never tried kernel 2.6.24-19-generic, but kernel 2.6.24-21-generic wouldn't work. Sound is fine on kernel 2.6.24-18-generic for me. I put a bug report into launchpad. kernel 2.6.24-21-generic was a proposed release kernel - obviously it's not quite ready yet. Have a look at your /boot/grub/menu.lst - it will have all the kernels you have listed. If kernel 2.6.24-18-generic is in the list, you can comment out the other kernels and try that one.

---

### Post by xmunk on 2008-09-23
hmm went looking through and all i found was .19  im a lil new at this been doin real good with the probs but this ones a lil beyond me lol.  anyways heres a copy

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4c1c84a6-f3f4-4ed1-82d9-8b1ea4c70ed7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4c1c84a6-f3f4-4ed1-82d9-8b1ea4c70ed7 ro quiet
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4c1c84a6-f3f4-4ed1-82d9-8b1ea4c70ed7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bumanie on 2008-09-23
Looks as though that is the only kernel you have - you must have been mistaken when you thought you had more than 2.6.24-19-generic. Can't explain the sudden sound loss. Sorry.

---

### Post by xmunk on 2008-09-24
oh well thanx anyways 
unless anyone else has any suggestions to try ima reinstall this weekend

---

