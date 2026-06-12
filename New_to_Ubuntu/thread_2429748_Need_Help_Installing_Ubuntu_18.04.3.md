---
title: "Need Help Installing Ubuntu 18.04.3"
date: 2019-10-22
forum: New to Ubuntu
---

### Post by jasperstrange on 2019-10-22
Hey Ubuntu Community,

      I am not the most knowledgeable in this field, and I am having a tough time installing Ubuntu on my computer, where I partitioned the disk. I followed this [guide]("https://www.tecmint.com/install-ubuntu-alongside-with-windows/") and got to the point where I can "try ubuntu without installing" or "install Ubuntu".

I spent a couple hours reading about ways to get rid of the errors that pop-up, and have solved a couple but I've hit a wall.

Error Message: 

```

[     11.614739] Couldn't get size: 0x80000000000000e
[     11.791712] ACPI BIOS Error (bug): Could not resolve [\_SB.PEGO._PRT.ARO
[     11.791747] ACPI Error: Method parse/execution failed \_SB.PCIO.PEGO._PRT, AE
[     11.791888] ACPI BIOS Error (bug): Could not resolve [\_SB.PEGO._PRT.ARO
[     11.791935] ACPI Error: Method parse/execution failed \_SB.PCIO.PEGO._PRT, AE
[     11.792174] ACPI BIOS Error (bug): Could Not resolve [\_SB.PEGO._PRT.ARO
2], AE_NOT_FOUND (20181213/psargs-330)
[     11.792186] ACPI Error: Method parse/execution failed \_SB.PCIO.PEGO._PRT, AE
_NOT_FOUND (20181213/psargs-531)
[     11.930914] nouveau 0000:01:00.0: bus: MMIO read of 000000000 FAULT at 022554
[   IBUS  ]
[     11.941837] nouveau 0000:01:00.0: bus: MMIO read of 000000000 FAULT at 10ac08 [ IBUS ]

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3.2) built-in shell (ash)
Enter 'help'for a list of built-in comands.

(initramfs) mount: mounting /cow on /root failed: Invalid argument
overlay mount failed

```

My computer is a Lenovo Y50-70
-nvidia GTX 960M
-Intel(R) Core(TM) i7-4720HQ CPU @2.60GHz

I was able to get rid of some error messages with:

```

nouveau.modeset=0

```


But i have yet to be able to actually use Ubuntu.


Thanks in Advance for any help

---

### Post by oldfred on 2019-10-22
Often ACPI errors can be ignored.

If not mounting the / from installer, I would first confirm you downloaded it correctly lwith md5sum.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Some also report that different port, different flash drive or using a different installer solves issues. No one issue.

You will need nomodeset to boot both live installer & first boot of install or until you install the nVidia driver.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by jasperstrange on 2019-10-24
Thanks A lot. I was able to get Ubuntu up and running with ease after your help. Now I am trying to figure out why I have no WiFi...

---

