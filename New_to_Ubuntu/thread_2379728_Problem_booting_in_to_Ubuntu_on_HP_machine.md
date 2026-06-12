---
title: "Problem booting in to Ubuntu on HP machine"
date: 2017-12-08
forum: New to Ubuntu
---

### Post by wrongusername2 on 2017-12-08
I am very new to Ubuntu.
I installed Ubuntu on HP 8470p. There is only one OS and that is Ubuntu.

**Problem**
When I boot the machine, I get the error "No bootable OS found" (see the attached the picture)
I resolve this by going in to BIOS and selecting Ubuntu (see the attached picture)
[B]
BIOS Settings[/B]
In order reach this stage I had to select "Custom Boot" + "UEFI" (see the attached pictures)
Secure - off
UEFI Native - On
Custom Boot - On (without this Ubuntu will not appear in Boot menu)

**efibootmgr Output is as follows**.
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000
Boot0000* ubuntu

How to void going in to BIOS every time and select Ubuntu? One of the forum entries suggested to rename EFI file. Should I try that?
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Thanks

(Note: Webpage said I do not have permission to upload attachments, that is why I am not uploading any attachment)

---

### Post by oldrocker99 on 2017-12-08
Your motherboard MIGHT have a "legacy" option, which allows for non-UEFI booting. Check your BIOS.

---

### Post by wrongusername2 on 2017-12-09
> **oldrocker99 said:**
> Your motherboard MIGHT have a "legacy" option, which allows for non-UEFI booting. Check your BIOS.
Thanks for responding.

First I tried Legacy mode, and did not help. Then enabled UEFi-Native and also "Custom Boot" option. That some how made Ubuntu show up in boot menu (shown inside BIOS).  Every time I boot the machine, I have to go in to BIOS and select Ubuntu. For some reason this selection does not stick. Note this is not a dual boot. 

Ultimately I plan to install Ubuntu on my main laptop(Hp Zbook). Before that I want to resolve small issues like this.

---

### Post by yancek on 2017-12-09
Did this computer have some windows version previously installed?  I would be very surprised if an HP did not come originally with some version of windows.
Use the Ubuntu DVD or flash drive you used to install and boot it and open a terminal and run the following command and post the output here:

```
sudo parted -l
```

Lower case Letter L in the command.  THis will give partition information. 

I think your best option would be to get the ppa for boot repair from the link below using the UBuntu DVD or flash drive.  After downloading boot repair you can run it by selecting the option to Create BootInfo Summary and do NOT try to make repairs.  It will give you a link you can post here with some details and someone should be able to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2017-12-09
HP is one that violates UEFI standard and uses description as part of boot. And of course only valid description is "Windows Boot Manager".

If only booting Ubuntu you can use efibootmgr to change name to Windows but really boot Ubuntu.
Or use the fallback boot entry /EFI/Boot/bootx64.efi. If your system has that file, it is just a copy of Windows .efi boot file. We can make that be a copy of shimx64.efi. Then if you have a hard drive UEFI boot entry it will boot Ubuntu.

Boot-Repair does the copy of shim to bootx64.efi if you check the "use the standard efi file" option in advanced options. It may be doing it all the time, as every recent report I have seen shows a backup of bootx64.efi. You can manually copy files also, as these users did before Boot-Repairs copy.
       HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 
    
       From link below in my signature on UEFI work arounds. Also other work arounds are there.
 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1. Additional parameters required if not sda1, see man efibootmgr.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by wrongusername2 on 2017-12-09
> **yancek said:**
> Did this computer have some windows version previously installed? I would be very surprised if an HP did not come originally with some version of windows.
Use the Ubuntu DVD or flash drive you used to install and boot it and open a terminal and run the following command and post the output here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks for responding.
HP shipped the Laptop with Win10. When installing Ubuntu, I chose the option to totally clean the machine. I will run boot-repair and post the outcome.

---

### Post by wrongusername2 on 2017-12-09
> **oldfred said:**
> HP is one that violates UEFI standard and uses description as part of boot. And of course only valid description is "Windows Boot Manager".

If only booting Ubuntu you can use efibootmgr to change name to Windows but really boot Ubuntu.

sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"


Thanks for responding.
I will try this on Monday. I had to educate myself about "shim" by reading [https://wiki.ubuntu.com/UEFI/SecureBoot/Testing?action=show&redirect=SecurityTeam%2FSecureBoot#Testing_Secure_Boot]("http://wiki.ubuntu.com/UEFI/SecureBoot/Testing?action=show&redirect=SecurityTeam%2FSecureBoot#Testing_Secure_Boot")
Based on my understanding, shimx64.efi is already signed by 'Microsoft Corporation UEFI CA'. But that is not enough for booting because Firmware expects the name to be "Windows Boot Manager" also. 
My guess is, after changing the name, output of "sudo efibootmgr" command should show "Windows Boot Manager" instead of 'ubuntu'.

---

### Post by oldfred on 2017-12-09
That is what you should see with efibootmgr. You may want to delete old or obsolete entries in your UEFI with efibootmgr.

And then you have converted a Windows entry to boot shimx64.efi which is a signed version of grub. It will work with Secure boot on or off. But if secure boot is on, you also have to have the signed kernel. And then cannot install proprietary drivers.

---

### Post by wrongusername2 on 2017-12-11
> **oldfred said:**
> 
But if secure boot is on, you also have to have the signed kernel. And then cannot install proprietary drivers.
Thanks that is good info.


My problem got solved after running following commands.

    sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"  //This command added* Boot0001* Windows Boot Manager*
    sudo efibootmgr -b 0 -B   //This command removed the* Boot0000* ubuntu* as this was not required

I need help in cleaning the boot manager. I am not sure whether I should clean this up by changing 'Boot0001' to 'Boot0000'.
Current state is as shown below.
[I]BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001
Boot0001* Windows Boot Manager[/I]


I would LIKE it to be as shown below. 
[I]BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000
Boot0000* Windows Boot Manager
[/I]
Please let me know what command I should run for changing 'Boot0001' to 'Boot0000'.

---

### Post by oldfred on 2017-12-11
You cannot change.
I think you just do delete and add again.

---

### Post by wrongusername2 on 2017-12-11
> **oldfred said:**
> You cannot change.
I think you just do delete and add again.

Thank you, it worked.

Thanks for all your help my issues got resolved

---

### Post by oldfred on 2017-12-11
You are welcome.
You can change to [Solved].

---

