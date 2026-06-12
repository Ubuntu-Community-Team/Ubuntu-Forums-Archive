---
title: "No bootable device -- insert boot disk and press any key"
date: 2018-05-30
forum: New to Ubuntu
---

### Post by sed_faster on 2018-05-30
Hello folks,

I installed the ubuntu server on disk SATA 80GB which are connect in this board: Intel® Desktop Board D945GCLF ([https://www.intel.com/content/dam/support/us/en/documents/boardsandkits/desktop-boards/945/D945GCLF/D945GCLF_ProductGuide04.pdf](https://www.intel.com/content/dam/support/us/en/documents/boardsandkits/desktop-boards/945/D945GCLF/D945GCLF_ProductGuide04.pdf)).

It happens that after installation the pc is stuck on screen whith this message "No bootable device -- insert boot disk and press any key".

This disk it is works well, because before I used this drive to storage data. In BIOS the parameters are these: [https://drive.google.com/drive/folders/1g6il21jNPUqlYPXxrKWIZQYgfKrh6Ln4?usp=sharing](https://drive.google.com/drive/folders/1g6il21jNPUqlYPXxrKWIZQYgfKrh6Ln4?usp=sharing)

What can I do to fix this problem?

Thanks

---

### Post by oldfred on 2018-05-30
I could not easily tell. Are drives set for AHCI, not RAID nor IDE?

Did you use gpt partitioning, and if so include bios_grub partition for BIOS boot or ESP for UEFI boot?
Does your board even support UEFI, it may not.

If you can download & run the Desktop installer in live mode, you can run this:
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If not run this, it is about the first third, of the above report:
       Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

---

### Post by sed_faster on 2018-06-01
Please see this photos: [https://snag.gy/waGjus.jpg](https://snag.gy/waGjus.jpg) and [https://snag.gy/ieWvZs.jpg](https://snag.gy/ieWvZs.jpg) (this is in this folder: [https://drive.google.com/drive/folders/1g6il21jNPUqlYPXxrKWIZQYgfKrh6Ln4](https://drive.google.com/drive/folders/1g6il21jNPUqlYPXxrKWIZQYgfKrh6Ln4))

Maybe the problem is related with this steps.

Thanks

---

### Post by leunam12 on 2018-06-01
If you are not dual booting with Windows 8 or 10 it is probably easier to just format the HDD as MBR (BIOS) and install again. It seems to me that the HDD is formatted with a GPT partition table which requires UEFI installation. If you prefer UEFI, then read the Wiki very carefully for UEFI installation.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by sed_faster on 2018-06-01
I should use live usb with e.g. ubuntu server and format the HDD as MBR? How should I formatting in HDD?

---

### Post by oldfred on 2018-06-01
If you have a bios_grub partition with gpt, you do not need to convert to MBR. But you can if you know MBR better.
Your error seemed like it could not see the bios_grub. Is it also unformatted?

If system is very old, it may have issues with gpt, but my desktop from 2009 worked with BIOS and gpt partitioning, but I had to have the bios_grub partition. I used BIOS boot with gpt for several years on multiple drives until I got a new UEFI system.  UEFI strongly suggests using gpt.

---

