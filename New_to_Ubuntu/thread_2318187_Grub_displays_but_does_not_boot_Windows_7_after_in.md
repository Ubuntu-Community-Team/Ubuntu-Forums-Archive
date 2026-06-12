---
title: "Grub displays but does not boot Windows 7 after installing Grub Customiser"
date: 2016-03-23
forum: New to Ubuntu
---

### Post by Soumya_Roychoudhur on 2016-03-23
Hello everyone,

I have a minor problem. 

I have a computer which dual boots Ubuntu 14.04.3 64 bit and Windows 7 32 bit. I use Easy BCD to manage dual boot from Windows. Grub  & Ubuntu partition is on sda4 while windows c drive containing Easy BCD is on sda2. First the Easy BCD displays with option to boot to Windows or Ubuntu. On choosing Ubuntu Grub is displayed. 

Grub was working ok till I installed Grub customiser. Previously Grub displayed windows 7 loader on sda1 and sda2 and displayed Easy BCD boot menu again from sda2  . Now it displays Windows 7 loader on sda1 and sda2 but after that just hangs. Ubuntu boots ok via Easy BCD & Grub and Windows also boots ok via Easy BCD.

I have since removed grub optimiser and updated grub but the issue remains.

/etc/default/grub file details are as follows. What could be wrong ? Please help.


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by grahammechanical on 2016-03-23
What did you use Grub Customiser to do? Installing Grub Customizer does not change anything. Loading Grub customiser does not change anything. What we do with it has the potential to change things.

Can you load Windows 7 from the Grub menu entry on sda1? And from sda2?

Regards.

---

### Post by Soumya_Roychoudhur on 2016-03-24
I changed the background picture and font colours. Then I deleted the Windows Loader on sda1 entry thinking it was unnecessary. After that I could not boot Windows from sda2. Then I restored the sda1 entry. The grub displayed both Windows sda1 & sda2 entries but couldn't boot from either. I have since reverted to previous grub settings( default background picture and font colours), removed grub customiser and updated grub. Ubuntu boots fine but windows doesn't boot from either sda1 or sda2. Should I reinstall grub ? 

Regards

---

### Post by oldfred on 2016-03-24
Windows not booting is usually a Windows issue, not grub. Grub really only boots working Windows.
All grub does is chainload to the Windows PBR or partition boot sector in the same way the Windows boot loader loads the PBR from the MBR Windows boot.

Often grub2's chain to PBR is too quick for Windows f8 to work. A few could use it if pressed at almost same time after several tries.
You can use Boot-Repair to temporarily restore a Windows boot loader to MBR and fix Windows. Then restore grub to MBR.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

[/URL] While a few primarily Windows users do use EasyBCD, it requires grub2 to install to PBR. And grub2 does not recommend installing to PBR as it has to convert to blocklists which are unreliable. You may have to reinstall grub after grub/kernel updates to PBR, or have Boot-Repair flash drive handy.

---

### Post by Soumya_Roychoudhur on 2016-03-25
Thanks for your reply. My Ubuntu system is 64 bit and Windows is 32 bit. So which version of Boot Repair should I install - 32 bit or 64 bit ? Also please explain what is meant by PBR.

---

### Post by oldfred on 2016-03-25
PBR or partition boot sector is just like MBR, but first sector of a partition. May just be Boot Sector (BS) or other terms. Used by Windows and Windows type boot loaders, but not grub normally.

 MBR(msdos) [URL="http://en.wikipedia.org/wiki/Master_boot_record"]http://en.wikipedia.org/wiki/Master_boot_record
[/URL]
 [http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html) 

 
Usually easier just to install Boot-Repair to live installer you used, which then was the 64 bit. And Boot-Repair is primarily for Linux. It can only make minor fixes to Windows, so you want your Windows repair flash drive for Windows repairs. You make your Windows repair disk from inside Windows before you start to have issues.

---

### Post by Soumya_Roychoudhur on 2016-03-26
I downloaded Boot-Repair iso 64 bit. Is there a way to install that iso to the Ubuntu 14.04.3 live USB installer I used to install Ubuntu or do I have to use another USB or CD ? 

 Currently in my PC Easy BCD is managing the dual boot in the MBR and I want to keep it that way till I gain more knowledge of Linux . Grub boot loader has been installed in sda4, which is the Ubuntu partition. Will Boot Repair reinstall grub to sda4 or will it overwrite the MBR ?

---

### Post by oldfred on 2016-03-26
Do not use auto-fix in Boot-Repair. It defaults to installing grub to MBR.
You should be able to use advanced options to choose a system and where to install.

There are two ways to use Boot-Repair. 
Download ISO and create a bootable system. 
Or just install inside your live installer. You have to redo that every time you reboot, but it is quick. If you have persistence on, it can save download, but still needs reinstall.

---

### Post by Soumya_Roychoudhur on 2016-03-26
Tried using advanced options in Boot-Repair. No luck. The os-prober detects both Ubuntu and Windows partitions but the only available location to install grub is sda . I believe that is the MBR. There seems to be no option to reinstall grub in sda4.

---

### Post by oldfred on 2016-03-26
Is your system UEFI?
Post link to summary report from Boot-Repair.

---

### Post by Soumya_Roychoudhur on 2016-03-31
My system is BIOS.

The link is given below
[http://paste.ubuntu.com/15570015/](http://paste.ubuntu.com/15570015/)

---

### Post by oldfred on 2016-03-31
The only Windows issue I see is that you have boot flag on sda2, but looks like sda1 is the Windows boot partition.
You show the normal bootmgr & BCD in both partitions, so either should boot.
But perhaps BCD is different.

I might try moving boot flag to sda1.
Do not know anything about EasyBCD as it uses the very old grub4dos to chainload.
Nor do I know about grub customizer, other than sometimes it makes changes that can cause issues.

---

