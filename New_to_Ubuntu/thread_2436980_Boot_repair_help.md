---
title: "Boot repair help"
date: 2020-02-16
forum: New to Ubuntu
---

### Post by jpa210 on 2020-02-16
I am trying to repair my boot loader. After installing ubuntu in another disk I lost my old boot file for Windows 10. Now I boot directly to Linux, if I change the boot order in Boot manager to boot first Windows I receive the following message '... The boot configuration Data file doesn't contain valid information for an operating system.'
I have  tried to use the Boot REpair tool, but it didn't fix my problem. I followed the instructions here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
The following message appears when I choose option &#340;ecommended repair': (IT is in portuguese)
GPT detectado. Por favor, crie uma partição BIOS-Boot (>1MB, sistema  de ficheiros não formatado, flag bios_grub). Isto pode ser feito via  ferramentas como Gparted. Então, tente novamente.
Alternativamente, talvez você queira tentar novamente depois de ativar a opção [Partição /boot/efi separada :].

the translation would be something like this: GPT detected. Please, create a BIOS-Boot partition (>1MB, file system not formatted, flab bios_grub). This ca be done using a tool like Gparted. Then , try again- Optionally , maybe you can try again after enable the option {Partition /boot/efi separated}

This is the booting URL  [https://paste.ubuntu.com/p/tjwppMjHDj/](https://paste.ubuntu.com/p/tjwppMjHDj/)

---

### Post by yancek on 2020-02-16
You booted and installed Ubuntu  in UEFI mode while your windows is in Legacy mode.  You have overwritten the windows boot code on the MBR of its drive so it probably would not work to set the windows drive to first boot priority.  Have you tried that?

Grub installed in UEFI mode will not boot a Legacy install of windows which you have.
Boot repair is written by Linux developers to repair boot problems with LInux bootloaders (Grub) although in some instances it can repair it to boot windows.

Ubuntu is on a GPT drive booting in UEFI mode.  What the message is telling you is that you need to boot in Legacy mode with a bios-grub partition, that's what the message is saying.  All of this is explained in detail at the Ubuntu site at the link below and I expect if you had read the instructions here before trying to install you would not have had the problems you now have.  When you go to that page, scroll down to the section Converting Ubuntu to UEFI or Legacy mode.  Legacy is what you want.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2020-02-16
Probably best to convert Ubuntu install to BIOS boot.
But since hardware is UEFI, why is not Windows in newer UEFI boot mode?
Microsoft has required vendors to install Windows in UEFI/gpt mode since Windows 8 released in 2012. So most hardware is UEFI.

You can add a tiny 1 or 2MB unformatted partition anywhere on sdb with gparted on live installer. Set flag to bios_grub.  Then use Boot-Repair advanced options when booted in BIOS mode to totally uninstall UEFI version of grub & reinstall bios version of grub.

       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jpa210 on 2020-02-17
I have tried to access the link you mentioned, but it didn't work:
 [h=1]Internal Server Error[/h] The server encountered an internal error or misconfiguration and was unable to complete your request.
 Please contact the server administrator,  [no address given] and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 More information about this error may be available in the server error log.

---

### Post by yancek on 2020-02-17
I'm not sure which link you are referring to but I just accessed the link I posted as well as the ones posted by oldfred without problems.

---

