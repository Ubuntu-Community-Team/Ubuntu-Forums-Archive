---
title: "Need Printing Help"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by Ahart on 2013-01-26
Hey all,

I am running Ubuntu 12.10 (amd 64) on a Dell Inspiron 5520. I recently purchased a Dell B1160w wireless printer and the box indicates the printer can be compatible with Linux. The drivers and utilities cd does not work with any Linux distro.

I tried downloading the drivers for the printer directly from Dell; however, Akamai NetSession keeps giving me an error message that it has been interrupted (I have Wine, so I can open executable files - not sure why the Dell download manager is still not working).

I also tried the CUPS site, but my printer drivers are not supported through them either (even though I was able to add my printer to the system). My computer seems to recognize the printer is there, it just automatically cancels all print jobs because I don't have the required drivers. Any ideas on how I can get this thing working? 

Thanks,

Ariel

---

### Post by raziel09 on 2013-01-26
Hmm did it state exactly which version of linux was supported?

I checked the dell website for the model that you mentioned and can only find drivers for red hat enterprise 5/6:

[http://www.dell.com/support/drivers/uk/en/ukbsdt1/Product/dell-b1160w](http://www.dell.com/support/drivers/uk/en/ukbsdt1/Product/dell-b1160w)


It looks like the printer isn't compatible with Ubuntu.

---

### Post by frank604 on 2013-01-26
At a brief glance I came upon this ftp site

[http://ftp.dell.com/Pages/Drivers/dell-b1160w.html](http://ftp.dell.com/Pages/Drivers/dell-b1160w.html)

Search for term "ubuntu" will lead to this driver

[http://ftp.dell.com/FOLDER00947576M/1/B1160_B1160w_UnifiedLinuxDriver_1.01.tar.gz](http://ftp.dell.com/FOLDER00947576M/1/B1160_B1160w_UnifiedLinuxDriver_1.01.tar.gz)

Give it a shot, not certain this will work or not.  But here is a guided question/answer to installing a tar.gz for printer in ubuntu [http://askubuntu.com/questions/170880/how-do-i-install-the-tar-gz-for-my-printer-drivers](http://askubuntu.com/questions/170880/how-do-i-install-the-tar-gz-for-my-printer-drivers)

---

