---
title: "Uncompression Error- System Halted"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by Deaner13 on 2013-04-02
Hey all,

Yesterday I created a flash drive with Lubuntu 12.10 on it for diagnosing and fixing computers. I went through the process of installing a few programs (GIMP, wine, LibreOffice, AVG, etc.) and then tried to boot to the drive using a different computer. The computer hung on a black screen for a couple of minutes so I did a hard shut down so that I could try again, but now the USB key is giving me the error "Uncompression Error- System Halted" after displaying a menu for Ubuntu, Ubuntu Advanced Options, Memtest. 

I have tried a couple of programs that I have found through the forums that are supposed to fix boot problems, but they do not seem to work. I have also run Memtest (suggested in forums too) and found that it runs fine from a CD, but when running through this USB it shows hundreds of thousands of errors.

Does anyone have any suggestions on how to fix this? I would really prefer not having to start all over again with this install.

---

### Post by tgalati4 on 2013-04-02
How did you set up the USB stick for booting?  If you did not leave enough room for your (large) installed programs, then you have a botched USB stick.  The memtest on some 12.10 Ubuntu distros is defective--giving an error at ~128MB during test #7.  You can safely ignore it. It has been patched with an update.  

Take a new USB drive and reinstall 12.10, but don't add any programs and make sure it boots.  It's possible that the USB stick is defective or worn out or full and needs erasing.

---

### Post by Deaner13 on 2013-04-02
The USB stick is 32GB and I did not change the default partition sizes. That could be a problem.

Are the default partition sizes too small to add these programs to?

---

### Post by tgalati4 on 2013-04-03
Yes.  They are designed to hold a minimal operating system with a maximum /home or /data partition.  That leaves little space to add programs.  You can change it, but you have to go through some steps to install the programs properly then respin the entire OS so that it is compressed and written as a self-extracting, bootable system.

---

