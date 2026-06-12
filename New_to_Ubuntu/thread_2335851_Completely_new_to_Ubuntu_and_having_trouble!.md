---
title: "Completely new to Ubuntu and having trouble!"
date: 2016-09-01
forum: New to Ubuntu
---

### Post by battlepants on 2016-09-01
I recently switched from Windows 10 to the latest version of Ubuntu. Downloading the iso file and burning it onto a completely new CD. Went through the installation process with one hiccup. While it booted from the disk it had a strong screen error that had the screen filled with a fairly used cutting board display. Filled with black and orange striped of the same colors of the original background. After a few minutes it cruised into the installation process. 
  
  The problem I now face is after restarting a few dozen times the computer asks to "Reboot and select proper boot device or insert a proper boot device and press any key to continue." 

  I've tried my own troubleshooting from reinstalling and boot repair from USB and disk, neither of which has worked to well but here is the URL from boot repair which successfully went through by USB.

  [http://paste.ubuntu.com/23122489](http://paste.ubuntu.com/23122489)

  I'd love any assistance or guidance in this new OS! 

  -Austin

---

### Post by Bucky Ball on 2016-09-02
Welcome. Try this. Launch boot repair. There is a tab where you have the option to install grub manually. Go there and install grub to sda (NOT sda1 or sda2, but just _sda_). Once that's done, reboot and see what happens. On the way, when you boot your machine, go to the BIOS and make sure you have the hard drive Ubuntu is on selected as first boot device, not USB or DVD.

At the bottom of the boot info you posted, you have this:

```
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!
```

That is a clue. Guess at the moment it's not. Just one other thing: You are across the UEFI stuff? I'm figuring you are as you've installed in UEFI mode and not legacy. That was intentional? No problem with that, but just to confirm and for clarity.

---

### Post by battlepants on 2016-09-02
After switching the installation of the Grub file in boot repair an error appeared:
   
   "! GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again. Alternatively, you can retry after activating the [Seperate /boot/efi partition:] option."

   I wouldn't know which mode I currently have on my computer, just the one from the download page as an iso file in 64bit.

---

### Post by Bucky Ball on 2016-09-02
Is this a brand new disk with a new partition or you were running Windows on it and have deleted the partitions and are trying to install Ubuntu on it? This is a guess, but when you installed Ubuntu, there are two options in BIOS when you select the boot device. One of them has 'UEFI' next to it (for instance, your USB install stick would have two entries, one with 'UEFI' and one not). I'm wondering if the disk was set up for UEFI previously somehow and you've tried to install in GPT.

I think there is a way to fix this without a reinstall, maybe even with boot repair, but I'm not au fait with it. That's a clue for where to look, though, until someone who can help arrives.

What I can't figure is that on a single boot Ubuntu machine on a blank drive it shouldn't matter which you install in, UEFI or the other. :-k As I say, I'm no expert.

---

### Post by battlepants on 2016-09-02
Deleted the partions and used a brand new CD for the installation. Using a computer which has had Win 8, Win 10 and now the installation process for Ubuntu.Thank you for your help even if you're not an expert it was still helpful for me to learn more of boot repair!

---

### Post by Bucky Ball on 2016-09-02
Ah, if you are happy to reinstall, then ...

Boot the install media, disk or USB, 'Try Ubuntu', when you are at a desktop, launch Gparted, right click and delete all partitions on the drive. 

Now go to the Device drop-down menu and select 'Create partition table'. Choose the default msdos.

When this is all done, reboot and start the install again, choosing the UEFI entry if you want UEFI or the other if not. Let us know how that goes.

(PS: Do you mean you installed from DVD rather than CD? Ubuntu won't fit on a CD. You are trying with the latest 16.04 LTS?)

---

### Post by mook765 on 2016-09-02
Disable secure-boot in UEFI-Bios an try if it boots normaly then.

---

### Post by battlepants on 2016-09-02
After deleteing the partitions and creating the partition table with the default msdos there is another error. (Installation with the UEFI)

   Grub installation failed
The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installation system will not boot.

    After hitting okay, the only option, the installer crashed. Redid the whole process, Ubuntu successfully installed asked to restart now. Booted up and the sane error of 
"Reboot and select proper boot device or Insert Boot Media in selected Boot device and press a key"
   
 (Yes DVD, I just think all disks are CDs since that's what the name was when I grew up *.*)

---

### Post by leunam12 on 2016-09-02
I second the last post from Bucky_Ball, you have to create a new partition table using the default msdos. Then create your partitions and re-install.

---

### Post by battlepants on 2016-09-02
There is no option that I see for any UEFI-BIOS. If you're talking about the on board Bios then the only option there is for booting config is Change Boot Order.

---

### Post by mook765 on 2016-09-02
Your boot-repair summary looked like a clean install.
Your Bios is EFI-compatible, you even ran boot-repair in UEFI-mode.
If you install in UEFI-mode, you need ESP (EFI System Partition), and Grub will install automatically in ESP. Everything looked fine in the boot-repair-summary.
Some hardware is a bit tricky, specially some laptops or machines with a poor UEFI-implementation.
Could you provide information about your hardware please.

---

