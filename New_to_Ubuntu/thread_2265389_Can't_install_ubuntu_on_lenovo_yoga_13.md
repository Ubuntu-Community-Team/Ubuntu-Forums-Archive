---
title: "Can't install ubuntu on lenovo yoga 13"
date: 2015-02-14
forum: New to Ubuntu
---

### Post by martijn8 on 2015-02-14
Hi all,

I am new here and searched allready for sme answers. I have a lenovo yoga 13 and tried to install ubuntu on it from usb. But it won't work. My lenovo wil not boot from usb. And i allready tried to format the usb with ntfs and fat32. Both don't work. Also when i am in my bootmanager my bootmanager don't see the usb stick.

How can i install ubuntu?

Thanks in advance

---

### Post by maclenin on 2015-02-14
**martijn8!**

I faced a similar challenge with a different (Windows 8) machine - Acer - and think the [steps you might need to take]("http://acer--uk.custhelp.com/app/answers/detail/a_id/27044/~/changing-bios-mode-from-uefi-to-legacy") are also similar. With additional reference to this [post]("http://answers.microsoft.com/en-us/windows/forum/windows_8-security/access-bios-from-boot-on-windows-8-lenovo-yoga/43b71aec-a0c9-4ed8-a237-c100a38bbd84") - try hitting **F2** when your computer restarts to access the bios and switch the computer's "Boot Mode" to "Legacy Bios". Then toggle the boot priority order (while still in the bios) to make certain the laptop finds / boots from the usb (HDD) - make usb number 1, for example. Save your changes and then reboot with the ubuntu usb stick in one of the usb ports. That should do it!

Note: The ubuntu usb stick should be created in a way recommended by ubuntu - [very simple]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") - assuming you're making it from Windows - if not, here's a [linux guide]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu"). I used the Startup Disk Creator utility from a second linux machine to create the LiveUSB stick for my Acer install....

Good luck!

---

### Post by yancek on 2015-02-14
Are you saying your computer is not capable of booting from a usb?  If so, why bother creating it?  Or do you mean this specific usb?  What software did you use to create a bootable flash drive?  Some of this software requires FAT32 format.  I wouldn't bother trying ntfs.  What bootmanager are you referring to?  Do you have another operating system?  Does your BIOS recognize the usb?  Do you have a DVD drive you could use?

---

### Post by sammiev on 2015-02-14
On my son's lenovo computer I had to change the Bios from "Boot Mode" to "Legacy Bios" to boot from USB as posted above by maclenin.

---

