---
title: "acpi force is required"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by pieniaszek on 2008-07-03
I installed Ubuntu on an older Gateway (G6-400) and received this message each time I boot up:

BIOS age (1999) fails cutoff.acpi force is required to enable APCI.

System still boots up.  

Do I have to update the BIOS, if I can?

---

### Post by dizee on 2008-07-03
So long as everything is working alright you can safely ignore that message.

If, however, you're having issues such as the computer failing to power off fully when it shuts down, then forcing acpi would be required. I doubt a BIOS update would be available for such an old computer, anyway it is much easier to add the "acpi=force" command to your "/boot/grub/menu.lst" file. Change the line that looks something like ```
kernel          /boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash
```
to
```
kernel          /boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash **acpi=force**
```

---

### Post by spiderbatdad on 2008-07-03
have not seen good results with boot parameters unless "quiet splash" is deleted:
```
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=####'s ro acpi=force
```

---

### Post by Rocket2DMn on 2008-07-03
If you add that to the GRUB list, you will want to add it where it says
```
# defoptions=splash quiet
```
so that it is
```
# defoptions=splash quiet acpi=off
```
You can do the same for "# altoptions=".
Save and close, then run
```
sudo update-grub
```

Using this method means that when kernel upgrades come along, it won't erase your changes and will automatically add the options to your new kernel.

---

### Post by spiderbatdad on 2008-07-03
> **Rocket2DMn said:**
> If you add that to the GRUB list, you will want to add it where it says
```
# defoptions=splash quiet
```
so that it is
```
# defoptions=splash quiet acpi=off
```
You can do the same for "# altoptions=".
Save and close, then run
```
sudo update-grub
```

Using this method means that when kernel upgrades come along, it won't erase your changes and will automatically add the options to your new kernel.


That may work, but I have not had success with defoptions or alt options.
Instead I use the section:

```
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=true

```

Setting savedefault to true will prevent kernel upgrades from overwriting the settings entered in the kernel options section:

```
## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID= ro acpi=force
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
Edit the section above...not defoptions.

---

### Post by Rocket2DMn on 2008-07-03
Do whatever works best, I use the defoptions and altoptions, but the other method should also work.  Don't you need to add "savedefault" as the last line for the kernel?

---

### Post by spiderbatdad on 2008-07-03
I haven't. I have only edited the value savedefault to true. IDK why adding the parameters to defoptions didn't work on either of my laptops. I had read that was the proper way to add options to menu.lst, so I did that, and boot hung for about 10 minutes. So I tried editing the kernel line directly, and I get desired results.

Regarding default, a kernel upgrade asks me what to do about menu.lst, default choice is to keep current.

---

### Post by bab1 on 2008-07-03
> **pieniaszek said:**
> I installed Ubuntu on an older Gateway (G6-400) and received this message each time I boot up:

BIOS age (1999) fails cutoff.acpi force is required to enable APCI.

System still boots up.  

Do I have to update the BIOS, if I can?

By all means update the BIOS.  I just did an update on a P3 450 MHz machine (1999 BIOS).  This will solve the problem.  Locating the correct BIOS will be the problem.  Do you know the chipset and the BIOS version?

Here is the location of Gateway support: [http://support.gateway.com/support/default.asp](http://support.gateway.com/support/default.asp)

If you know the systems serial #  you will be able to get the download the correct BIOS. 

-BAB1

---

### Post by Rocket2DMn on 2008-07-04
> **spiderbatdad said:**
> I haven't. I have only edited the value savedefault to true. IDK why adding the parameters to defoptions didn't work on either of my laptops. I had read that was the proper way to add options to menu.lst, so I did that, and boot hung for about 10 minutes. So I tried editing the kernel line directly, and I get desired results.

Regarding default, a kernel upgrade asks me what to do about menu.lst, default choice is to keep current.

Did you run the update-grub command after you made the changes?  defoptions controls for your normal kernel, altoptions is for the recovery mode kernel.

---

### Post by pieniaszek on 2008-07-04
I found an updated BIOS file at the Gateway site, downloaded it created a floppy, but can't install it.  When I reboot, even after I set system to start with floppy first, Grub by-passes that and I am instructed to remove this floppy.

Isn't there someway to 1. bypass Grub to start from a floppy, 2. go to as command line and return to the startup BIOS area.  3: download a file in Ubuntu and copy it on the floppy., 4,  download that BIOS update on a USB memory device

I had to go back to Windows to download a file and copy it on a floppy.  I have been able to download and copy a CD in Ubuntu, but don't know where to get the applciation for copying a floppy.

---

### Post by Rocket2DMn on 2008-07-04
The site should have directions for doing this.  I think usually you have to extract an installer file to the floppy drive and possibly make it bootable (this may require the disk to be formatted this way in advance).  I'm afraid it has been many many years since I did this with floppies, so I don't have a detailed answer for you on that one.

---

### Post by bab1 on 2008-07-04
Good morning all,

Yes -- the floppy must be bootable and yes when you format it you can select that it be made bootable.

Then you can extract the downloaded files to the floppy.

What is the serial number of the PC?  I will go to Gateway's site and read the instructions.

---

