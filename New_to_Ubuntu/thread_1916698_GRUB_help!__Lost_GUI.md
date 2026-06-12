---
title: "GRUB help!  Lost GUI"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by GnuHouse on 2012-01-28
Hi,

I seem to have lost my GRUB GUI upon start up.  When I booted up in the past, I would be presented with a simple GUI that would allow me to arrow through a selection of OS's (well, really just one) and then select the OS to load.  Yesterday, when I rebooted my laptop, I did not get the GUI but was brought to a grub> command line.  I don't know how to load Ubuntu from here so my laptop, at the moment, is a very expensive paperweight.

Can anyone give me insight as to:
1) How to load Ubuntu from the GRUB command line?
2) Get my GRUB GUI back?

Thanks so much in advance

---

### Post by bogan on 2012-01-28
Hi!, **GnuHouse**,

Wild Guess!

 Try Pressing 'Esc'

or pressing 'Shift' at the beginning of boot up.

It **might** put you back to the Grub Menu.

Chao!, **bogan**

---

### Post by GnuHouse on 2012-01-28
> **bogan said:**
> Hi!, **GnuHouse**,

Wild Guess!

 Try Pressing 'Esc'

or pressing 'Shift' at the beginning of boot up.

It **might** put you back to the Grub Menu.

Chao!, **bogan**

Thanks for the suggestions.  I tried both methods and no such luck :(

---

### Post by drs305 on 2012-01-28
If it is a "grub" prompt and not a "grub rescue" prompt things can probably be fixed without too much trouble.

The easiest thing is probably to boot the LiveCD, install Boot Repair, and let it fix your OS.

If it fails, it can give you an option to run the boot info script. Posting the contents of the file it generates, RESULTS.txt, will help us if Boot Repair can't fix things.

See the Boot Repair link in my signature line.

---

### Post by BC59 on 2012-01-28
With sudo nano /etc/default/grub you can change the settings of the grub.
If you prefer GUI install startup manager.

---

### Post by Double.J on 2012-01-28
Hi there, 

The usual cause of this is a change in the partitions on the disk... but not always!
I'd recommend using a live cd/usb to repair grub. Boot up the live medium and first try chrooting and up-dating grub to fix. To do this, open a terminal and 
```
sudo fdisk -l
``` to get your partition number of your ubuntu root partition - for example /dev/sda2. Make a note of this number and use it in the following example:

To chroot, and update grub:
```

sudo mkdir /fix
sudo mount /dev/sdaX /fix
sudo mount --bind /dev /fix/dev
sudo mount --bind /var /fix/var
sudo mount --bind /sys /fix/sys
sudo chroot /fix
sudo update-grub

```

If this doesn't work, you can reinstall grub by changing the last command in the sequence to "grub-install /dev/sda"

Hope it helps :)

A second, graphical approach can be achieved with boot-repair, but this requires internet access and adding a repo... ubuntu info [here]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by GnuHouse on 2012-01-29
> **drs305 said:**
> If it is a "grub" prompt and not a "grub rescue" prompt things can probably be fixed without too much trouble.

The easiest thing is probably to boot the LiveCD, install Boot Repair, and let it fix your OS.

If it fails, it can give you an option to run the boot info script. Posting the contents of the file it generates, RESULTS.txt, will help us if Boot Repair can't fix things.

See the Boot Repair link in my signature line.

I did as suggested and no luck.  Here is a link to the results file

[http://paste.ubuntu.com/821390/](http://paste.ubuntu.com/821390/)

Thnx

**EDIT**
And, as a special addition, now I can't boot from my Live CD.  My boot sequence remained the same, but now it seems like I just skip over the DVD drive and go straight to grub.

From the grub command line I typed "exit" (one of the possible commands listed).  I got a listing of the laptop's start up sequence from the bios and the first three options (DVD, HDD, LAN) all indicated that there was no valid operating system.  I don't know if it means anything but thought I would mention it

---

### Post by drs305 on 2012-01-29
Thanks for posting RESULTS.txt.

Let's just try reinstalling Grub to the MBR. Boot Repair should have been able to do this, but it's a first step to making sure we cover all the possibilities.

Boot an 11.10 LiveCD, mount the Ubuntu partition and reinstall Grub2:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
Do NOT include the partition number in the second command.

Reboot.
If it doesn't boot, at the grub prompt, run the following commands and answer the questions posed after the # symbol:

```

ls (hd0,5)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,5)/boot # Do you see the kernel and initrd image files ?
ls (hd0,5)/boot/grub # Do you see lots of *.mod files and grub.cfg ?
```

Added Later: After studying the RESULTS.txt, I see that grub.cfg does not include the 10_linux section. Since grub-install writes to the MBR but doesn't generate a new grub.cfg file, the above would correctly point to the correct partition but still wouldn't produce a usable menu.

---

### Post by GnuHouse on 2012-01-29
> **drs305 said:**
> Thanks for posting RESULTS.txt.

Let's just try reinstalling Grub to the MBR. Boot Repair should have been able to do this, but it's a first step to making sure we cover all the possibilities.

Boot an 11.10 LiveCD, mount the Ubuntu partition and reinstall Grub2:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
Do NOT include the partition number in the second command.

Reboot.
If it doesn't boot, at the grub prompt, run the following commands and answer the questions posed after the # symbol:

```

ls (hd0,5)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,5)/boot # Do you see the kernel and initrd image files ?
ls (hd0,5)/boot/grub # Do you see lots of *.mod files and grub.cfg ?
```

Answers to the questions are all Yes

---

### Post by drs305 on 2012-01-29
Your Grub menu is missing some major components, but we should be able to boot from the grub prompt and then rebuild the grub.cfg file.

At the grub prompt:

```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```

I believe the necessary modules are already loaded. If you get an error message about a missing module, run this command with the module name:
```
insmod (hd0,5)/boot/grub/<module_name>.mod
```

Once it boots, run
```
sudo update-grub
```
then run this command to see if the proper menuentries were generated. You should have at least one menuentry with "3.0.0-15-generic" as an available kernel.
```
grep "menuentry" /boot/grub/grub.cfg
```

I see you have some 10_linux proxy files - perhaps you tried Grub Customizer?

Make sure your scripts in the /etc/grub.d folder are executable if you still don't have at least one menuentry:
```
sudo chmod +x /etc/grub.d/10_linux /etc/grub.d/30_os-prober
sudo update-grub
```

---

### Post by GnuHouse on 2012-01-29
Success!  Thank you very much for your help

---

### Post by drs305 on 2012-01-29
Glad it's working. :-)

Do you know how the grub menu became corrupted? I saw some proxy file references - Grub Customizer is the only app I know that creates them but I'm always interested if there are others.

P.S. You can mark the thread SOLVED via the 'Thread Tools' link near the upper right of the first post if you don't have any other issues related to this thread. Thanks.

---

### Post by GnuHouse on 2012-01-29
> **drs305 said:**
> Glad it's working. :-)

Do you know how the grub menu became corrupted? I saw some proxy file references - Grub Customizer is the only app I know that creates them but I'm always interested if there are others.

P.S. You can mark the thread SOLVED via the 'Thread Tools' link near the upper right of the first post if you don't have any other issues related to this thread. Thanks.

Not sure how it became corrupted.  I used Grub Customizer in the past to remove some obsolete references when I updated Ubuntu, but I haven't used that in a while.

---

