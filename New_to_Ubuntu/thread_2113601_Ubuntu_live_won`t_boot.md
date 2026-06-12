---
title: "Ubuntu live won`t boot"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by harrydawizard on 2013-02-07
I installed ubuntu 12.04 from a usb and everything worked fine except my partitions. I know how to fix my partition but I need to boot ubuntu live to do so. The problem is I can`t seems to boot from usb anymore. It just goes directly to the usual purple menu where I can select ubuntu, windows, etc. It seems to just skip the usb. Any suggestions . . .
Also, I most definitely set my computer to boot from usb.

---

### Post by Enigmapond on 2013-02-07
You need to change the boot order in the BIOS. Go to the setup as it's re-starting.

---

### Post by harrydawizard on 2013-02-07
I have changed the order. I selected it to boot from USB just as I originally did when installing from my usb. It even recognised the name of my usb ``kingston . . .`

---

### Post by DuckHook on 2013-02-07
Do you have a new UEFI system? Is it a WUBI install? It would really help to provide full system info when posting. Then we can bypass all sorts of preliminary detective work. Please provide. While in Ubuntu, do:

```
cat /etc/default/grub
```...and post output back here. Also, ```
cat /etc/fstab
``` can be helpful. X out your private info like UUIDs if you want.

Instead of changing BIOS, can you boot holding down <F10>, <F8>, <F2> or <Del> key (whichever your system uses) to bring up one-time boot menu? This may get you where you want to go and make all foregoing academic.

---

### Post by harrydawizard on 2013-02-08
xxxxxxxxxxxxy-AOD257:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
xxxxxxxxxxxxxxx-AOD257:~$ 




Is this what you mean?
And the second one:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=21b45e6b-05b4-46fa-b34e-be63420ddb00 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=aeb703a6-cf1a-439e-a514-1bb31afdc875 none            swap    sw              0       0





Also I tried the one time boot menu but I can't find the button for it. I've tried all the ones you suggest, and looked up on the internet which it should be for an ASPIRE netbook and it said f12 but it does seem to work.

---

### Post by DuckHook on 2013-02-08
> **harrydawizard said:**
> Also I tried the one time boot menu but I can't find the button for it. I've tried all the ones you suggest, and looked up on the internet which it should be for an ASPIRE netbook and it said f12 but it does seem to work.

Ah. An Aspire notebook. So, no CD/DVD and only USB as an option.

I'm unfamiliar with the Aspire, but on some laptops, you must hold down a <Fn> key while pressing <F12> because the key serves dual purposes.

Your grub and fstab look very simple and generic, so the problem is unlikely to be there. They would have little bearing in any case unless your system uses UEFI.

I doubt that your netbook uses UEFI, so we can rule that out. It is possible that your USB has become corrupted or the boot flag has become unset, so that the system just bypasses it. Have you tried booting any other computer with the same USB stick? Once the computer boots, does it recognize and read the stick? If so, then while in Ubuntu, please bring up *gparted* and see if the USB is recognized. If so, is the boot flag set? Be careful in *gparted*. It's a partition editor and can bork your system if you are careless. However, just looking around with it will do no harm. Just don't go changing settings without knowing exactly what you are doing.

---

### Post by harrydawizard on 2013-02-08
I checked the boot flag in gparted and it seems all in order but when I tried booting from the same USB stick in another computer it came to a black screen which reads:
error: no such device: 21b45e6b-05b4-46fa-b34e-
grub rescue>


Perhaps I will try remaking the ubuntu boot usb to see if that makes a difference.

---

### Post by harrydawizard on 2013-02-08
Well it seems that remaking a bootable usb fixed my problem. haha That turned out to be easy.
Mighty thanks!

---

### Post by oldfred on 2013-02-08
That is the UUID you show as your install in the hard drive. Some computers promote the flash drive to sda during install and grub normally defaults to installing into sda. So it seems like grub is in USB flash drive and when booting from it you are having issues booting system. It should still let you boot and then you could install grub to MBR of drive. 

But if not booting hard drive from USB then you will have to recreate live install on flash drive. It probably just needs syslinux boot loader not grub in the MBR of the flash drive, but it may just be easier to recreate it.

---

