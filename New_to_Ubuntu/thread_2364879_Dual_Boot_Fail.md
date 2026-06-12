---
title: "Dual Boot Fail"
date: 2017-06-29
forum: New to Ubuntu
---

### Post by aphro2 on 2017-06-29
I was attempting to dual boot win 10 and linux ubuntu however encountered a 'region violation' type error (I have attached an image.. i think. The blue pen marks are there coz I wasn't sure if it's sensitive information). I intended for each OS to go on separate OS ssd's. 

currently running win 10, [COLOR=#111111][FONT=Ubuntu]nvidia geforce gtx970, Intel i7 4790K 4.0GHz ,[/FONT][/COLOR]used rufus to create live USB and dl Ubuntu 17.04 from a local based mirror. I hope I've included enough information!

---

### Post by kc1di on 2017-06-29
Hello aphro2 and Welcome to Ubuntu, 
your thumbnails does not show much of use. 
[here is a tutorial]("http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html") on how to dual boot windows 10 and ubuntu. 
follow the instructions and it should work ok.

---

### Post by yancek on 2017-06-29
The official Ubuntu documentation on the subject is at the site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-06-29
If separate SSD, you need to manually partition in advance and use Something Else to install/use partitions you create.
Or disconnect Windows SSD (physically or in UEFI if available) and fully install Ubuntu. 
But you must install both systems in same boot mode. 
New hardware systems are UEFI, but both Windows & Ubuntu can be installed in the 35 year old BIOS/MBR or newer UEFI/gpt configuration.

 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
      
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    
For more info on UEFI install, see link below in my signature.

[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)

---

