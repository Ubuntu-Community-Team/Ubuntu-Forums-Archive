---
title: "Fingerprint scanner locked me out"
date: 2014-03-07
forum: New to Ubuntu
---

### Post by panorain on 2014-03-07
I messed up my /etc/pam.d/common-auth file when I was setting up my fingerprint reader in Lusicd Lynx 10.04. I created a usb bootable image with ubuntu 12.04 lts installed on it. how can I edit the /etc/pam.d/common-auth file and remove my 2 bad entries? The system is asking for my password which I have but then asks me to swipe my index finger and after that authentication always fails. The drive shows up as /dev/sda under fdisk -l

Please help.

Thank You,

---

### Post by raja.genupula on 2014-03-07
If you are sure that you can identify the wrong entries you made then Run the Live mode and then open your files system( not live one) then open your terminal . CD into that and then 

sudo <path>

---

### Post by panorain on 2014-03-08
I was able to mount the existing harddisk with a bootable .iso image. I was then able to modify the file after I mounted the harddisk. Thank you for your help.

Thank you,

---

