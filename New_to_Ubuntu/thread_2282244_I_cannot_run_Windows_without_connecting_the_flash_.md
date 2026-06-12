---
title: "I cannot run Windows without connecting the flash drive in which linux was installed"
date: 2015-06-12
forum: New to Ubuntu
---

### Post by emre4 on 2015-06-12
[COLOR=#111111][FONT=Ubuntu]I've installed Linux into my flashdrive from another flash drive while windows 7 is running. When I start up my computer with the flash drive in which linux installed , it appears 4 options ( Linux, Linux recovery, window , windows recovery ).Linux used to work smoothly but something happened and I could not open linux again. Terminal screen appears but it says there is a problem with system file . But I still get 4 options in start-up and I can open windows 7 if I connect the flash drive.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]But the problem is I cannot run Windows without connecting the flash drive in which linux was installed.When I disconnect the flash drive and start up the computer in a usual way, windows logo never appears and black screen appears and it says like " welcome to grub..there is no such a device..recovery mode.."[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So how can I run windows directly like in the past? I worry if I lose the flash drive I will not able to run windows either.[/FONT][/COLOR]

---

### Post by cariboo on 2015-06-12
It seems you have installed grub on your flash drive, start windows using the usb device, then once booted into windows, open a command prompt:

```
Start->cmd
```

then use the following command:

```
BootRec.exe /fixmbr
```

once that's done you should be able to boot into windows without the flash device plugged in.

---

### Post by yancek on 2015-06-12
The error you are reporting is the result of using MBR to boot windows/Ubuntu and accepting the default of installing Grub code to the MBR of the first drive, the one with windows on it.  When you boot, this code looks for the Grub files, almost all of which are on the partition on which you installed Ubuntu.  Since those files are on the flash drive which is not attached, you get that error.  The commands suggested by cariboo should fix the problem.

---

### Post by efflandt on 2015-06-13
However, once you get Windows to boot directly you will not be able to boot Ubuntu on the flash drive. But you seem to have some trouble with the file system on the flash drive, so it may be easiest to reinstall Ubuntu on the flash drive, but when it comes to partitioning select Other, select whatever partition(s) on that, and make sure that you put grub on the flash drive (/dev/sdx where x is whichever device it is without a number). In BIOS you would need to set the boot order to boot USB before the hard drive, but you might still need to press a hotkey during the BIOS splash screen to select booting from USB.

---

