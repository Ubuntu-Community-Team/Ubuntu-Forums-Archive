---
title: "Missing print filter"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by Dibbling Dave on 2012-01-25
I am running Ubuntu 11.10 and am trying to use my Canon LBP6000 printer. The printer is recognised and I installed the drivers for it. However when I try to print I am told I am missing file pstocapt3. How do I solve this?

Dave.

---

### Post by kc1di on 2012-01-25
There is a problem with the Cups Driver for your printer.
delete the printer in Cups and download and install the following printer driver from:

[http://support-au.canon.com.au/P/search?model=LASERSHOT+LBP6000&menu=download&filter=0&tagname=g_os&g_os=Linux]("http://support-au.canon.com.au/P/search?model=LASERSHOT+LBP6000&menu=download&filter=0&tagname=g_os&g_os=Linux")
Then re-install the printer using the new driver.

That should work for you.

---

### Post by Dibbling Dave on 2012-01-25
No, it didn't work. I must be doing something wrong but I don't know what. 

Dave.

---

### Post by kc1di on 2012-01-25
Are you still getting the same error? or something different?

---

### Post by Dibbling Dave on 2012-01-25
Still getting the same error.

---

### Post by kc1di on 2012-01-25
since I no longer have my cannon printer I can't test this anymore but here are a couple of pages that may be of help.

[https://help.ubuntu.com/community/CanonCaptDrv190]("https://help.ubuntu.com/community/CanonCaptDrv190")

[http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/]("http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/")

perhaps someone else will chime in that has one running also.
Good luck,
dave

---

### Post by Dibbling Dave on 2012-01-25
Thanks for the links. I think where I am going wrong, my system is 64-bit and I installed the 32-bit Debian drivers. I am not very good at this sort of thing but will try the 64 bit rpm files. 

Dave.

---

### Post by Dibbling Dave on 2012-01-25
Can anyone help by explaining how to instal the rpm files or convert them to Debian. I have followed the instructions here [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190) but I just get command not found. At least I think that is what I need to do, please advise if I am going wrong.

Dave.

---

### Post by Dibbling Dave on 2012-01-25
I have converted the rpm files to Deb and installed them, deleted my printer and reinstalled. I now get this as the printer status Idle - File "/usr/lib/cups/filter/pstocapt3" not available: No such file or directory.

Sorry to keep posting, but I need to sort this.

Dave.

---

