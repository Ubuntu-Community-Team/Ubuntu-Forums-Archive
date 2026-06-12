---
title: "UEFI dual booting linux mint and Ubuntu (17.1/14.04 respectively)"
date: 2015-01-01
forum: New to Ubuntu
---

### Post by jim50 on 2015-01-01
Hi all,

Just got myself my first UEFI laptop. I had read that there would be a lot of problems but there havent really been. Ubuntu installed fine without secureboot, as did open suse and PC-BSD needed legacy mode, but once i turned UEFI back on ubuntu's grub could boot it fine.

The only problem I'm having is a conflict between linux mint and Ubuntu. Before UEFI, I used GPT disks with a bios partion and installed ubuntu's grub into it. Every other OS I just installed it's bootloader into it's boot partition and chainloaded. it meant that ubuntu was always incharge so I didnt loose the ability to boot after an update, and each OS updates its own bootloader so I always load the latest kernal image. This is what I am trying to replicate with UEFI. I set up a 100MB efi partition on /dev/sda2 and installed ubuntu's grub into it. When I installed mint, I set up a 100MB efi partion on /dev/sda8 and told it to put it's grub there. when I rebooted, I found that it had installed itself into /dev/sda2 and overwritten ubuntu. I went into ubuntu and ran update grub, but linux mint is still in charge.

I've tried reinstalling and the sme thing happens. I think its because they use the same installer and are both essentially ubunutu. I've kind of accepted that linux mint has an unhealthy obsession with /dev/sda2, so I'd like to just get round it by reinstalling grub into /dev/sda8 from ubuntu, then telling the BIOS to boot from there. Anyone got any ideas how to reinstall UEFI grub? or if this will resolve the problem?

Thank you so much!

Jim

---

### Post by yancek on 2015-01-01
I don't use UEFI but, my understanding is that the various Ubuntu derivatives like Mint use the same file names for their efi boot.  Thus when Mint installs, it overwrites the Ubuntu efi files.  You might check your install media for each as I'm just guessing.  Running update-grub from Ubuntu would not be expected to change, running it from Mint should add Ubuntu to the Mint menu on a standard MBR install.  I don't know if that would work on efi.  I'm sure someone else more familiar with UEFI will be along to help.

---

### Post by jim50 on 2015-01-01
UPDATE!

I have been able to reinstall ubunut's grub on /dev/sda8. The problem was a corrupt file system, but a reformat made it possible.

The only problem now is that I can't work out how to make ubuntu's grub chainload linux mints so I dont have to update grub in ubuntu every time mint has an update. I'm starting to think that kicking linux mint out of the UEFI party is the answer, and having it load MBR grub2 in its own partition to resolve the conflicts?

---

### Post by Dennis N on 2015-01-01
> when Mint installs, it overwrites the Ubuntu efi files. You might check your install media for each as I'm just guessing. Running update-grub from Ubuntu would not be expected to change, running it from Mint should add Ubuntu to the Mint menu on a standard MBR install.

100% correct. This is exactly what happens with the ubiquity installer - the EFI partition folder is always 'Ubuntu'. The effect is you will boot into grub on the most recent OS installed. Then you can select the previous OSes from the Grub menu, just like installing on a older BIOS computer.

---

### Post by Dennis N on 2015-01-01
> **jim50 said:**
> UPDATE!

I have been able to reinstall ubunut's grub on /dev/sda8. The problem was a corrupt file system, but a reformat made it possible. The only problem now is that I can't work out how to make ubuntu's grub chainload linux mints so I dont have to update grub in ubuntu every time mint has an update. I'm starting to think that kicking linux mint out of the UEFI party is the answer, and having it load MBR grub2 in its own partition to resolve the conflicts?

If you did this I don't think Ubuntu is installed in UEFI mode. UEFI install mode will only install grub files to a EFI system partition. So this reinstall must be in Legacy (BIOS) mode. Mint must also be in BIOS mode. No problem with that, however.

To solve your updating issue, you need to get into custom menu entries which require no maintainance.

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by grahammechanical on 2015-01-01
I do not have practical experience with UEFI. What I know comes from a wiki Ubuntu article that says if one OS is installed in EFI mode than all the other OSes must also be installed in EFI mode and if one OS is installed in Legacy (not EFI) mode then all the other OSes must also be installed in Legacy mode.

I also know that the Ubuntu installer defaults to installing Grub into sda and not a partition unless we specifically instruct the installer to install grub into a partition. But that installing Grub into a partition is possible but not necessarily a good thing to do.

I also know that there are 2 related Grub commands that is it useful to know

```
sudo update-grub
sudo grub-install /dev/sda
```

I am sure that if you run those 2 commands from Ubuntu then the Grub belonging to Ubuntu will be in charge of the Grub boot menu.  Of course we can change /dev/sda to /dev/sda2 or some other partition if we want.

I have many installs of Ubuntu and its flavours on 2 hard drives. I select one OS to be the main OS and I run those 2 commands from that OS whenever I need to to keep it in charge. I have not installed Linux Mint but it seems that Linux Mint is writing its Grub configuration file to every /boot/grub/grub.cfg in every partition that has a /boot/grub/grub.cfg. This behaviour used to happen with legacy Grub but I have not seen it happen with Ubuntu's Grub 2.0. May be the Linux Mint developers are deviating a little bit from Ubuntu practice. It may also be why the better behaviour of Ubuntu's Grub is not managing to override the Linux Mint Grub configuration.

I have sometimes found that update-grub is not enough to change the boot menu. We also need grub-install /dev/sda. 

Regards.

EDIT:

> [COLOR=#333333][FONT=Ubuntu]The bootloader information does not have to be installed to the embedded area of the MBR. It may also bypass the MBR entirely and be installed to a specific partition. In doing this, the location of the GRUB 2 files are specified by using blocklists. This option is not available via an Ubuntu GUI installation but can be made via the terminal after installation. Even then this method is not as reliable as writing to the MBR and is not recommended by the GRUB developers. [/FONT][/COLOR]

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Dennis N on 2015-01-03
> I also know that the Ubuntu installer defaults to installing Grub into sda and not a partition unless we specifically instruct the installer to install grub into a partition.

If you are installing in UEFI mode, ubiquity will not install Grub into any partition except for the EFI system partition. So choosing sda3 for example, is fruitless - it will just ignore your choice and install to the EFI system partiton. If you have two disks each with an EFI system partition, I found that specifying the EFI on sdb is ignored, and the grub install is done to sda! (I have twice tried to do this with the same outcome). From what I have gathered from reading, other OSes with other installers allow you to choose.

---

### Post by oldfred on 2015-01-03
I had the same issue as Dennis N.
I did a second install of Ubuntu on sdb with an efi partition on sdb. I am pretty sure I specified sdb as location of grub and it totally overwrote my grub in the efi partition on sda. Of course I tell everyone to backup efi partition and had not backed it up. So I copied efi partition from sda to sdb, booted into install in sda and reinstalled grub in UEFI mode.

You do have to have all installs in same boot mode, either both UEFI or both BIOS to boot from grub menu. Once system starts booting you cannot change boot modes. They just are not compatible. You can select from UEFI mode or one time boot key.

Only one efi partition per hard drive. It acts as the MBR, but every system installs its own folder with its own boot loader. Like having many MBRs. But if grub version has same label like ubuntu then it will overwrite an existing efi folder. But actually the only difference is a tiny grub.cfg in the efi partition that does a configfile (chain) entry to the grub.cfg in the working install.

---

### Post by monkeybrain20122 on 2015-01-03
Why don't you just use legacy mode for everything as you are not running Windows 8 on this machine?

---

