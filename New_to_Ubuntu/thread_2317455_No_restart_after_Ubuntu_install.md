---
title: "No restart after Ubuntu install"
date: 2016-03-16
forum: New to Ubuntu
---

### Post by richard151 on 2016-03-16
I have downloaded Ubuntu 15.10 to a 64 GB flash drive. I have installed it alongside win. 10. When asked to restart after a successful  install, it boots right into windows. i've been chasing this for three days now and although frustrated, i'm not giving up. Any help would be greatly appreciated. By the way, I have a Lenovo idea pad 64 bit system with UEFI. I have changed UEFI to Legacy mode thinking it might be in the way.

---

### Post by Geoffrey_Arndt on 2016-03-16
Edit:   I deleted my earlier response, as I see I didn't read your original post closely enough (thought you installed to an external drive).   Anyway, Graham's post below is the place to start (boot repair report).   His assessment sounds right, because Win 10 doesn't install in legacy mode by default.   In short, each OS must be installed in same firmware mode (uefi or legacy for BOTH).   That way, there are no mismatching partitions and underlying disk protocol.

---

### Post by grahammechanical on 2016-03-16
Windows 10 will have been installed in EFI mode. That means that Ubuntu musy also be installed in EFI mode. Was it?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Run a Ubuntu live session. Install Boot Repair & create a Bootinfo summary and paste the URL to the summary report in this thread.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

 Regards

---

