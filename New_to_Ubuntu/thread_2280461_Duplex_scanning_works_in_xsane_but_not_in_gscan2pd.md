---
title: "Duplex scanning works in xsane but not in gscan2pdf or simple-scan"
date: 2015-05-30
forum: New to Ubuntu
---

### Post by triciasurfer on 2015-05-30
Scanner: Brother ADS-2000
gscan2pdf version: 1.3.2 (latest version in PPA right now)
xsane: 0.998
simple-scan: 3.12.1
--------------
Hello,
I can get duplex scanning to work in xsane. But in gscan2pdf or simple-scan, I can't. 

 The frontend options in gscan2pdf are libsane-perl, scanimage, scanimage-perl, scanadf-perl, scanadf.

Single-sided scanning works with *scanimage* or *scanadf *as the frontend. 
I suppose *scanimage* is really just for one-sided scanning, and that if I want to do duplex scanning, I must use  *scanadf*. But when I choose *scanadf*, I get an error message:> [INDENT] scanadf: rounded value of br-x from 215.9 to 215.88 
scanadf: rounded value of br-y from 355.6 to 355.567
 [/INDENT]

How can I get duplex scanning to work in gscan2pdf or simple-scan?


Thanks.

---

### Post by Michael_Schievelbein on 2015-06-22
Make sure that AFTER you click on the 'Scan' button, on the 'Scan Document' screen that pops up, on the 'Standard Tab' you select "Scan Source" to "ADF Duplex" or it will only scan the front.

---

