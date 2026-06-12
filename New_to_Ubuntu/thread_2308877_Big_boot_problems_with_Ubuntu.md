---
title: "Big boot problems with Ubuntu"
date: 2016-01-06
forum: New to Ubuntu
---

### Post by Matthew_Twine on 2016-01-06
Hey there!

So I decided to try and install Ubuntu on my laptop from a USB alongside windows, after doing this, the only way to access Ubuntu was by booting from the USB and selecting the install option and then closing the installer.

I made attempts to fix this, the most recent of which was erasing all data from my hard driving and installing Ubuntu on it's own, even after doing this and removing the USB I was shown a 'No bootable device' notice after starting up my laptop

I hope someone will be able to help me on this one, I just want Ubuntu to launch straight after pressing the power button, without a USB to boot from.

Thank you!

---

### Post by leunam12 on 2016-01-06
Run boot-repair from the USB session.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Matthew_Twine on 2016-01-06
I made a boot repair USB, ran it, allowed it to do it's thing, it told me to reboot so i did, only to be greeted by "No bootable device"

---

### Post by grahammechanical on 2016-01-06
> the only way to access Ubuntu was by booting from the USB and selecting the install option and then closing the installer.

Did you not get an option to Try Ubuntu without installing it? When you selected the Install Ubuntu option did you choose Erase disk & install Ubuntu? Did you go through these installation instructions?

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

What version of Windows was installed? Is the motherboard boot system BIOS or UEFI?

Boot Repair will produce a boot info summary. It will provide a URL to where the summary is stored online. If you post that URL in your thread then we can see the information provided in the summary. At the moment you are no further forward & we are no clearer as to what the problem is.

The message "No bootable device" can mean that the motherboard boot system cannot find a device with a computer operating system on it. If we have set the motherboard to look to a USB port for a bootable device and then remove the USB memory stick with Ubuntu on it, we may get that message because the motherboard boot system (BIOS/UEFI) is only looking to a USB port and not to an internal hard drive.

You may need to enter the BIOS/UEFI boot system and direct it to look to a hard disk for a boot loader.

But this is all snatching at straws because based on the little information that you have provided I am unclear as to what you have done. I am not even sure if you have installed Ubuntu.

Regards

---

### Post by Matthew_Twine on 2016-01-06
The Boot repair gave this URL [http://paste.ubuntu.com/14419559/](http://paste.ubuntu.com/14419559/)

As far as I know, I have erased my disk and installed Ubuntu after booting it from my USB drive.

My BIOS boot priority is set to boot from my main HDD, which is what I can only assume to be the install location of Ubuntu, as I do not know how to check.

I did get an option to try Ubuntu without installing it, this also works as a way to access the OS

---

### Post by leunam12 on 2016-01-06
Enter your UEFI settings and try disabling fast boot and secure boot. I can only boot my computer if I disable MSI Fast boot. Also it wouldn't hurt to boot a live session and check the hard drive's health.

[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html)

---

### Post by oldfred on 2016-01-06
What brand model system?
Some like Acer require you to set a supervisor password and set trust on ubuntu/grub efi boot files.
Some other systems like HP & Sony violate UEFI spec that says not to use description in UEFI boot. And only valid description is "Windows". If that is the case we can just change ubuntu description to Windows to boot Ubuntu/grub2's shim file.

 From link in my signature below on resolving issues:
       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by Matthew_Twine on 2016-01-06
> **oldfred said:**
> What brand model system?
Some like Acer require you to set a supervisor password and set trust on ubuntu/grub efi boot files.

It turns out that was the issue, I set a supervisor password and enabled ubuntu grub as a trusted boot method, my laptop now boots straight into Ubuntu.

Thank you ever so much!

---

