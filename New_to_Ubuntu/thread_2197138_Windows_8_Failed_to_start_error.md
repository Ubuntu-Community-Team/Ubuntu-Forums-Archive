---
title: "Windows 8 Failed to start error"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by veeraeka175 on 2014-01-02
Hi i bought new Acer laptop with Pre Installed Windows 8 with C drive only. I have created One more Partition named E drive by shrinking and created unallocated space. Then i installed ubuntu 13.10 in that.   But after that while Booting when i Select Windows Option...I am getting the screen with "Windows 8 failed to start error". The only thing i can do is Press "ESC" to go to UEFI settings and make windows boot manager as first Priority and Restart the System .  Please help me , Thanks in Advance.

---

### Post by Jonathan Precise on 2014-01-02
Hello veeraeka175. Welcome to the forums!

This is normally caused by filesystem errors. We are probably going to need more information:

Please tell us the exact error message that appears.

Did you use the windows partitioner to shrink the drive, or did you use the installer to shrink the drive (Or GParted. We have received a lot of cases where the ubuntu installer or GParted corrupts the windows partition)?

If you used the windows partitioning tool, then did you reboot twice after shrinking the drive before installing ubuntu? (This is so windows can repair any filesystem errors after shrinking.)

Please post the specs of the computer.

In UEFI settings, change the priority to the windows boot manager. After the BIOS/UEFI initialization, can you immediately press F8, and choose "Safe Mode with Networking"? Or "Command Prompt"

--Jonathan

---

