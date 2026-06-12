---
title: "UEFI: Ubuntu doesn't boot after clean install. Boot-repair-disk doesn't boot."
date: 2014-04-20
forum: New to Ubuntu
---

### Post by goldblatt on 2014-04-20
I'm attempting to install Ubuntu on a new Win 8.1 laptop (Satellite E55-A5114). The installation process completes flawlessly, but the restart immediately following the installation results in this screen:

[[IMG]http://i.imgur.com/hQVykBEl.jpg[/IMG]](http://imgur.com/hQVykBE)

I have attempted this installation multiple times with both 14.04 and 13.10 with the exact same result.

My inadequate sleuthing skills led me to believe that there is a problem with GRUB, as this error message appears to have been produced due to an inability to reach GRUB. For this reason, I followed the general google suggestions and downloaded boot-repair-disk and put it on another flash drive. However, that simply boots to a blank, black screen.

Please help me. I don't want to use Windows on this computer.

---

### Post by shadytv on 2014-04-20
Did you disable "secure boot" in the bios? Most newer laptops have issues with unsigned (Non-Windows OS's).

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Hopefully this helps.

---

### Post by goldblatt on 2014-04-20
> **shadytv said:**
> Did you disable "secure boot" in the bios? Most newer laptops have issues with unsigned (Non-Windows OS's).

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Hopefully this helps.

Yes

---

### Post by goldblatt on 2014-04-20
Bump

---

### Post by tripp98 on 2014-04-20
how many hard drives do you have?

When you go through the install are you removing the previous os's or is this a dual boot?
Does the install ask you to restart the pc?

---

### Post by goldblatt on 2014-04-20
> **tripp98 said:**
> how many hard drives do you have?

When you go through the install are you removing the previous os's or is this a dual boot?
Does the install ask you to restart the pc?

1 hard drive
The drive is formatted by the installer before installation (erase all previous OS)
Yes, it prompts for a restart

---

### Post by oldfred on 2014-04-21
Error message may be from UEFI/BIOS.
Did you install in UEFI or BIOS mode, and then are you booting in the same mode.
If secure boot is on, only systems installed in secure boot mode will be available to boot.

And if you only have Ubuntu, you will not get a grub menu by default. 
With BIOS you have to hold shift key from BIOS until menu appears, but with UEFI it may be escape key.

And then it may be a video issue.

---

### Post by WoodenWalker on 2014-04-21
As oldfred stated, it could be due to UEFI/Legacy boot settings. Was it installed while the setting was UEFI or BIOS mode? Have you changed this since then? Have you tried running your installation CD as live boot and running boot repair from within that session? Any information you can give would help, please and thank you.

---

### Post by monkeybrain20122 on 2014-04-21
If you have only Ubuntu I would just turn of uefi and do everything in bios. It makes life a lot simpler.

---

### Post by goldblatt on 2014-04-21
I don't believe my computer supports booting from BIOS/Legacy Mode. Nevertheless, it is installed in UEFI.

---

### Post by WoodenWalker on 2014-04-21
Did you try running boot-repair from the live disk after install?

---

### Post by oldfred on 2014-04-21
If you are getting black screen it probably is a video issue.

What video card/chip do you have?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by goldblatt on 2014-04-22
> **oldfred said:**
> If you are getting black screen it probably is a video issue.

What video card/chip do you have?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

I did do this. The problem only occurs with boot-repair-disk, the ubuntu live cd does not have a black screen.

---

### Post by oldfred on 2014-04-22
The Boot-Repair disk may be based on an older version of Ubuntu and need the boot parameters where the newer versions have updated kernels  and video drivers and do not need them.

---

### Post by goldblatt on 2014-04-27
> **oldfred said:**
> The Boot-Repair disk may be based on an older version of Ubuntu and need the boot parameters where the newer versions have updated kernels  and video drivers and do not need them.

Boot-repair-disk with nomodeset flag:
[IMG]http://i.imgur.com/u7h0dLX.jpg[/IMG]

My graphics card is Intel® HD Graphics 4400

---

### Post by oldfred on 2014-04-27
With Intel video, usually nomodeset does not work but one of the settings suggested by ubfan1 in post #12 does. Different versions of Intel seem to need different settings.
With 14.04 many report Intel just works.

these improvements also helped older Intel based systems.
 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)
Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

---

### Post by goldblatt on 2014-05-23
> **oldfred said:**
> With Intel video, usually nomodeset does not work but one of the settings suggested by ubfan1 in post #12 does. Different versions of Intel seem to need different settings.
With 14.04 many report Intel just works.

these improvements also helped older Intel based systems.
 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)
Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)
Boot repair disk still does not boot.

I tried many of the options in various combinations.

---

### Post by oldfred on 2014-05-23
Can you boot Ubuntu live installer?
You can add Boot-Repair into that.
Not sure if you would need boot parameters or not?

Some other Toshiba:
  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by goldblatt on 2014-05-24
> **oldfred said:**
> Can you boot Ubuntu live installer?
You can add Boot-Repair into that.
Not sure if you would need boot parameters or not?

Yeah, that's how I installed ubuntu. It boots into the installer without configuration but the OS just fails after a clean install.

---

### Post by oldfred on 2014-05-24
Do you get black screen? 
If you only have one operating system, you do not get grub menu as it knows which system you normally boot. If BIOS shift key should bring up menu, if UEFI escape key often works. Then you can add boot parameters or boot in recovery mode if necessary.

If you cannot get to grub menu install Boot-Repair into Ubuntu live installer. Then post link to BootInfo report.

---

### Post by goldblatt on 2014-05-25
> **oldfred said:**
> Do you get black screen? 
If you only have one operating system, you do not get grub menu as it knows which system you normally boot. If BIOS shift key should bring up menu, if UEFI escape key often works. Then you can add boot parameters or boot in recovery mode if necessary.

If you cannot get to grub menu install Boot-Repair into Ubuntu live installer. Then post link to BootInfo report.

[http://paste.ubuntu.com/7513905/](http://paste.ubuntu.com/7513905/)

---

### Post by oldfred on 2014-05-25
You show no grub.cfg or menu and Boot-Repair wanted to run the purge & re-install, but cancelled it.
Do you have Internet working with Live installer?
Have you connected with wired Ethernet? Often wi-fi does not work until it can download drivers using wired connection.

---

