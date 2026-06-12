---
title: "Ubuntu fails to start"
date: 2018-12-10
forum: New to Ubuntu
---

### Post by oskarskula on 2018-12-10
I just installed Ubuntu on a Lenovo ThinkStation and get this error message:

Failed to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load image \EFI\BOOT\mmx64.efi: Not Found
Failed to start Mok Manager: Not Found
Something has gone seriously wrong: impor_mok_stat() failed

This shows for a few seconds and then the computer turns off

Booting from USB does not work.

It does not allow me to get into the BIOS 

Is this something that is known?

---

### Post by bradleypariah on 2018-12-10
How did you install Ubuntu - Use whole disk, or Guided?  If guided, where did you install the bootloader?  Is SecureBoot enabled in your BIOS?

Is it possible to boot from different disks when your turn your machine on?

---

### Post by oskarskula on 2018-12-10
I installed from USB following the instructions provided here [https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop)

I am not sure were I installed the bootloader or if SecurBoot is enabled in my BIOS. 

I did actually install Ubuntu twice ... first by erasing Windows and I had no problems in that round, but in the second round I did everything the same but now installing Ubuntu erasing the earlier setup.

---

### Post by oskarskula on 2018-12-11
I found out how to get into the setup/BIOS so this is not as serious as it seemed. Has probably to things that have been covered in other threads before.

---

