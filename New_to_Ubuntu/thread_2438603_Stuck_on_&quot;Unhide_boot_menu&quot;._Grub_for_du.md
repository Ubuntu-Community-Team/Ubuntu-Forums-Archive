---
title: "Stuck on &quot;Unhide boot menu&quot;. Grub for dual boot recover after motherboard replacement"
date: 2020-03-14
forum: New to Ubuntu
---

### Post by vasko-rak on 2020-03-14
Dual boot Windows 10 and Ubuntu 18.04
Trying to recover grub after motherboard replacement. 
I stoped the process. And turned off computer.
Computer automaticaly booted to Windows previously. Now i get Grub 2 terminal on boot, just 
 grub> 
What should I do?

Here is the boot repair info I got: [http://paste.ubuntu.com/p/w6y4MSFqHp/](http://paste.ubuntu.com/p/w6y4MSFqHp/) 

Last lines of code from boot-repair log before it stuck on "Unhide boot menu":

```
SET@_label0.set_text('''Purge and reinstall the GRUB of: sdb4 (fin). This may require several minutes...''')
SET@_label0.set_text('''Unhide boot menu. This may require several minutes...''')
Unhide GRUB boot menu in sdb4/etc/default/grub
[debug] sda1 ends at 525336064GB. not-far
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sdb4/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sdb4/boot/efi/EFI/Boot/bootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sdb4/boot/efi/EFI/Boot/fbx64.efi
SET@_progressbar1.pulse()
[debug] sda3 ends at 111896461824GB. farbios
[debug] sda3 ends at 111896461824GB. farbios
[debug] sda4 ends at 112790076928GB. farbios
[debug] sda4 ends at 112790076928GB. farbios
[debug] sda5 ends at 126870355456GB. farbios
[debug] sda5 ends at 126870355456GB. farbios
[debug] sda6 ends at 128035323392GB. farbios
[debug] sda6 ends at 128035323392GB. farbios
[debug] sdb2 ends at 751754542592GB. farbios
[debug] sdb2 ends at 751754542592GB. farbios
SET@_progressbar1.pulse()

=================== sdb4/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Mar 14 21:45 grub.d
drwxr-xr-x  5 root root     4096 Mar 14 21:37 grub.d.bak
total 76
-rwxr-xr-x 1 root root 10046 Nov 11 05:52 00_header
-rwxr-xr-x 1 root root  6258 Mar 18  2019 05_debian_theme
-rwxr-xr-x 1 root root 12693 Nov 11 05:52 10_linux
-rwxr-xr-x 1 root root 11298 Nov 11 05:52 20_linux_xen
-rwxr-xr-x 1 root root 12059 Nov 11 05:52 30_os-prober
-rwxr-xr-x 1 root root  1418 Nov 11 05:52 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Nov 11 05:52 40_custom
-rwxr-xr-x 1 root root   216 Nov 11 05:52 41_custom
-rw-r--r-- 1 root root   483 Nov 11 05:52 README




=================== sdb4/etc/default/grub :
        
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
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



/boot/efi detected in the fstab of sdb4: UUID=3883-5F9E     (sda1)
[debug] sdb4 ends at 1000204542976GB. farbios
[debug] sdb4 ends at 1000204542976GB. farbios
SET@_progressbar1.pulse()
[debug]End fix /mnt/boot-sav/sdb4/etc/grub.d/

```

---

### Post by oldfred on 2020-03-15
See line 462 which shows UEFI boot entries.
from
sudo efibootmgr -v

It shows no Ubuntu entry. UEFI stores that inside the motherboard, so new motherboard does not have Ubuntu entry. Many UEFI find a Windows entry in ESP - efi system partition, but not others. So you have to manually add it.
You can just use efibootmgr which grub also uses with a full reinstall of grub.

Check entry is there before & after.
sudo efibootmgr -v 
Entry default to first drive, so extra parameters for drive & partition are not required in your case since sda1.
sudo  efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" 

For others if ESP not sda1, replace sdX for drive & partition for Y or if any NVMe partition.
sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/sdX -p Y
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p Y

See also 
man efibootmgr

More examples in link in my signature.

---

