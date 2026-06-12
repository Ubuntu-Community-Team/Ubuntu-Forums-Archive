---
title: "Trouble dualbooting Windows 7 and Ubuntu"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by sheherezade on 2012-12-07
I'm trying to set up a dual boot between Windows 7 and Ubuntu. I'm also looking to have windows bootloader as my primary one, and for it to let me select if I want to start W7 or Ubuntu when I power up my pc.

I downloaded version 12.04 LTS from the Ubuntu website, and burned it to a DVD as pr the instructions on the site. The installation process worked fine but in the end when the computer was going to reboot in order to finish the installation process it got stuck on a screen with the following text: 
 
* Checking battery state                   [OK]
* Stopping System V runlevel compatibility      [OK]
acpid: exiting
Checking for running unattended upgrades:
                                                       speech- dispatcher disabled;
                                                       edit/etc/delfault/speech dispatcher
*Asking all remaining processes to terminate           [OK]

I had to kill the power in the end. After restarting the computer went straight into Windows. I then went into BIOS and set Ubuntu as my primary boot, rebooted and got the following message: unknown file sytem, grub rescue.

Any advice?

---

### Post by audiomick on 2012-12-07
I am not aware of any way of making the windows bootloader offer you any OS to boot other than a Microsoft product. It refuses to recognise anything other than windows. Microsoft user friendliness...

If you want to dual boot Windows with a Linux system, you will have to use Grub (the standard bootloader in Ubuntu and several other Linux distributions) or Lilo or one of the other boot loaders available for Linux. I don't see any reason for using anything other than grub, myself.


As far as fixing your boot goes, look here.
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

The repair function might well get you going. Failing that, follow the instructions regarding the boot info and post the link to it here so we can see what state the system is in.

---

### Post by sheherezade on 2012-12-07
I ran the boot-repair, but it terminated saying "You have installed on sda 8 a Linux version which is not EFI-compatible, and is probably not compatible with your computer....."

From what I've googled, this has something to do with booting, but I'm pretty new to Linux in general so would anyone mind explaining what this actually means?

---

### Post by audiomick on 2012-12-07
> **sheherezade said:**
> .. a Linux version which is not EFI-compatible, and is probably not compatible with your computer....


Ahh. I'll leave you with this link
[http://en.wikipedia.org/wiki/Extensible_Firmware_Interface]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface")

to read a bit about EFI. I believe that 12.10 is EFI compatible, and that the next 12.04 iso, I think 12.04.03,  is planned to be. I haven't, however, really looked into all of that, so I wont try and give any advice. I am sure someone will come along who has more experience with the matter.

---

### Post by sheherezade on 2012-12-08
I changed to Ubuntu 12.10 which works fine, but I'm still not able to dual boot with windows. I have what I assume is the Ubuntu boot manager on screen. Choosing Ubuntu works fine, but when I chose the Windows loader I get an error message so I have to go into BIOS and change the boot order from there in order to revert back to Windows again.

I had a look at this tutorial: [http://www.liberiangeek.net/2012/10/dual-booting-windows-7-and-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/10/dual-booting-windows-7-and-ubuntu-12-10-quantal-quetzal/) which says to select "Something Else" during the installation process. I selected delete Ubuntu 12.04LTS and replace with 12.10. Could this be the reason for the trouble?

---

### Post by mlentink on 2012-12-08
Could you please elaborate on the options you chose during install? You said you chose 'do something else' but what exactly did you select? In particular: did you maake ant choices as to where to install the Ubuntu boot loader (GRUB)?

I dual boot my work laptop, but I prefer the GRUB bootloader, as it recongnizes all windows versions as well as all linux versions automatically.

---

### Post by oldfred on 2012-12-08
Still best to post the link to the BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by sheherezade on 2012-12-08
As I wrote I selected to replace Ubuntu 12.04LTS with 12.10. 
There were two options which was to wipe the harddrive completely and install ubuntu 12.10, delete Unbuntu 12.04 and replace it with version 12.10 , but leave Windows 7 alone, then a couple that were greyed out, and then the `something else` option at the bottom. I chose the  install 12.10, but leave Windows 7 option.

 I found the link with the tutorial after when I begun to search for answers regarding the trouble I was having with dual boot, so that  was when I begun to wonder if I should have chosen the `something else` option instead.

Here is the link generated by the boot repair: [http://paste.ubuntu.com/1420030/](http://paste.ubuntu.com/1420030/)

---

### Post by oldfred on 2012-12-09
The default installs give you / (root) & swap with all sorts of defaults. The Something Else is a manual install where you choose partition size, format, mount point like / (root)  and then have the option to add additional partitions like a /home as a separate partition. Its is more complicated but gives more control over sizes & configuration.

You have Windows in UEFI with gpt partitioning. Your first install of Ubuntu was in BIOS mode which does not work wtih UEFI Windows. You have to use the 12.10 64 bit versions and from the UEFI menu boot the install flash drive in UEFI mode not BIOS mode. How you boot installer is how it installs.

Boot-Repair will convert a BIOS install of the 64bit version to UEFI by uninstalling grub-pc and installing grub-efi. Ubuntu does not change, just the grub2 boot loader.

Grub2 also has another bug that Boot-Repair will fix. Grub creates the old style BIOS chain load entries to Windows. They do not work as you need an efi chain entry. Any  entry that looks like this will not work.
       'Windows ...) (on /dev/sdXY)'
Wrong style chain boot entry
 [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)


Can you Boot Windows directly from UEFI/BIOS? And Ubuntu?
If Windows works from UEFI menu then use boot repair to add correct chain load entry and you then can set Ubuntu as default in UEFI and boot either Ubuntu or Windows from the grub menu.

---

