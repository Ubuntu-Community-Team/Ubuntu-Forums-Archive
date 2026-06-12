---
title: "Uncompression error when booting Ubuntu 18.04 from a live USB"
date: 2018-05-20
forum: New to Ubuntu
---

### Post by eraserhouse on 2018-05-20
I wanted to try ubuntu for the first time and thought that the live USB approach would be the fastest and easiest to set up. I followed the official instructions, set up the 4GB 2.0 USB with Rufus and restarted the PC. 
After selecting Try Ubuntu without installing in grub loader i get to this screen: 
[https://tutorials.ubuntu.com/bundled/src/codelabs/try-ubuntu-before-you-install/img/edb2670b0022f931.png](https://tutorials.ubuntu.com/bundled/src/codelabs/try-ubuntu-before-you-install/img/edb2670b0022f931.png)
Where i once again select Try without installing.
After that i just get a dark screen with 
   Uncompression error 
   --system halted
in the upper left corner.

My PC:
Windows 10
Radeon r9 280 
AMD Phenom II x4 960T
8GB Kingston HyperX DDR3 RAM
Gigabyte 970A-DS3P 

Other threads that I searched were either for older Ubuntu versions or I had no idea what people were talking about since I am completely new to Linux.  
Thank you in advance.

---

### Post by yancek on 2018-05-20
Did you download your Ubuntu iso from the Ubuntu site?  If so, which iso did you download?  Did you verify the download as explained at the Ubuntu site below?  Did you read the Ubuntu documentation at the second link below on dual booting windows/Ubuntu?

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldrocker99 on 2018-05-20
The first thing your should do, before anything else, is to select "Check disk for defects."

It might not find any errors (it's happened to me), but if it does, obviously you need to redownload the .ISO and make absolutely sure that the USB is formatted for DOS, NOT NTFS.

---

### Post by eraserhouse on 2018-05-20
I downloaded the 18.04 LTS from the Ubuntu website.
When i select Check disk for defects the same thing happens, black screen with "Uncompressed error system halted message" the only thing I can start from that screen is the "Test memory" option which reports no errors.
The USB is formated as FAT32.

---

