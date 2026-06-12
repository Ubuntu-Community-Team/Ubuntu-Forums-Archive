---
title: "Accidentally formatted EFI partition - Boot-repair did not solve the problem"
date: 2018-08-05
forum: New to Ubuntu
---

### Post by oli-h2o on 2018-08-05
I wanted to remove Windows from my dual-boot Windows/Ubuntu using OS-Uninstaller. This uninstallation apparently formatted my [FONT=courier new]/dev/sda1[/FONT] partition (to ntfs), which used to be my EFI system partition (previously mounted as [FONT=courier new]/boot/efi[/FONT]). The other partitions seem untouched.

I ended up unable to boot anything but my Ubuntu live-USB.

I read that the problem could be solved by:
1) Reformatting [FONT=courier new]/dev/sda1[/FONT] to FAT32 and making sure the "boot" and "esp" flags are set on it (I did it with GParted)
2) Running the "Recommended repair" of Boot-Repair (I did it and can post the pastebin if needed). This repair ended with the following message:

[FONT=courier new]GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again. Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.[/FONT]

Unfortunately** t****his did not solve my problem** (I still get a "[FONT=courier new]No bootable devices[/FONT]" at startup).

I am only interested in being able to boot again my Ubuntu installation (I do not care about Windows anymore).

I read also that the next step would possibly be to use the Advanced options in Boot-Repair, or to copy the file [FONT=courier new]/EFI/BOOT/bootx64.efi [FONT=Arial](see for example [https://superuser.com/questions/764799/how-to-create-an-efi-system-partition](https://superuser.com/questions/764799/how-to-create-an-efi-system-partition))[/FONT][/FONT][FONT=courier new][FONT=arial], but I am not sure about these next steps and I am afraid to screw things up. I would greatly appreciate detailed explanations on how to proceed.[/FONT][/FONT]

---

### Post by oldfred on 2018-08-05
If Boot-Repair is asking for a bios_grub partition, it is trying to install the BIOS boot version of grub.

You want to boot live installer in UEFI boot mode from UEFI boot menu, add Boot-Repair so in UEFI mode and install the UEFI version of grub2.

UEFI should offer two ways to boot live installer. Once is UEFI and other is BIOS.
You may have to change settings in UEFI to allow USB boot and USB boot in UEFI mode.
Then you have to make sure UEFI is set to boot in UEFI mode from installed system. That may be a separate setting.

---

### Post by oli-h2o on 2018-08-06
Ok, I thought I had changed all the parameters to UEFI in my BIOS, but maybe not. Although when I boot in the live session, the boot menu says "UEFI: PMAP" to identify the live-USB...
Is it possible that there are also some Boot-Repair parameters to make sure it installs the UEFI version of grub2?

Anyway I will explore more in depth my BIOS parameters later today when I have access to my computer.

---

### Post by oli-h2o on 2018-08-06
I had a better look at my BIOS settings, and I didn't find more options related to EFI than those that are already set:
- the legacy ROMs are disabled:
[ATTACH=CONFIG]280658[/ATTACH]
- UEFI boot is selected instead of Legacy:
[ATTACH=CONFIG]280659[/ATTACH]

Any ideas why Boot-Repair is not installing the EFI version of grub2?

---

### Post by oldfred on 2018-08-06
On my system pmap is the BIOS boot and that is on the internal drives. 
I have another that will say UEFI:flash where flash is name or label of flash drive.

Which start up screen are you getting from booting flash drive? Purple or grub?
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oli-h2o on 2018-08-06
To boot on the live-USB, I need to access a menu called the "one-time boot menu", which looks like a very simple BIOS (I access it by pressing F12 on the startup screen, while to access BIOS I press F2).

It is on this "one-time boot menu" that I see "UEFI: PMAP". (By the way, the only other boot options are "ubuntu" and "Windows", but neither of the two work. For example if I choose "ubuntu", I get the same message "No bootable device"). See the photo:
[ATTACH=CONFIG]280661[/ATTACH]
Once I have selected "UEFI: PMAP", I get the grub with "Try Ubuntu" and "Install Ubuntu" of my live-USB. That is how I access a live session.

If I don't press F12 before startup, I get the usual "No bootable devices" message, but I don't know any other means to boot the live-USB... Should it boot without me going through this "one-time boot menu"?

---

### Post by oldfred on 2018-08-06
If you are getting the grub menu as shown in link in my previous post, then that is the UEFI boot.
F12 is common for the one time boot or the UEFI boot menu.

Do not know then why Boot-Repair would want to install a BIOS version of grub?
Post this from live installer in UEFI mode, it will not be HDD.
       Query to see if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"  

If EFI boot add ppa for Boot-Repair and in advanced options reinstall grub and check the box to install latest kernel.

I prefer forum for most issues. The simple question and simple answer format of AskUbuntu does not lend itself to back & forth or more complicated issues.

---

### Post by oli-h2o on 2018-08-06
The command
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
resulted in "EFI boot on HDD", so now it is 100% sure that the live-USB boots in EFI.

What do you mean by > If EFI boot add ppa for Boot-Repair and in advanced options reinstall grub and check the box to install latest kernel?
Why installing the latest kernel? Will it overwrite my installed Ubuntu?

I opened Boot-Repair.
Here are all the the advanced options BEFORE I change anything:
[ATTACH=CONFIG]280666[/ATTACH][ATTACH=CONFIG]280665[/ATTACH][ATTACH=CONFIG]280664[/ATTACH][ATTACH=CONFIG]280663[/ATTACH]
          screen 1                            screen 2                          screen 3                           screen 4

Could you please tell me what I have to change on each screen?

---

### Post by oldfred on 2018-08-06
I think you can just run defaults.

Sometimes users need newest kernel. If system was up to date, then it would not change anything.

---

### Post by oli-h2o on 2018-08-06
Yes my system was up to date before the problem.

> I think you can just run defaults.
But I already ran the recommended repair. So will it change anything?
On the second screen (Boot Location), I can see that the box "Separate /boot/efi partition at sda1" is not checked. Should I check it or not?

---

### Post by oldfred on 2018-08-06
It should automatically see that. 
I would check that, but make sure it is FAT32 with boot and/or ESP flags.

---

### Post by oli-h2o on 2018-08-07
Problem solved: checking the "Separate /boot/efi partition" in the advanced options of Boot-Repair did the job!

For those having the same problem, you will find the full summary of the steps I followed at [https://askubuntu.com/questions/1061990/invalid-partition-table-after-removing-windows-with-os-uninstaller/1063319#1063319](https://askubuntu.com/questions/1061990/invalid-partition-table-after-removing-windows-with-os-uninstaller/1063319#1063319).

---

