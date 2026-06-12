---
title: "FTP refuses to work - won't install / strange errors"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by Toriku on 2012-11-16
I am trying to achieve an FTP service on a machine running Ubuntu Server. I have tried a the 64bit version of 12.10 on one machine and the 32bit version of 12.04 on another, and on either machine when I install proftpd or vsftpd through apt-get (using sudo) the config files aren't generated, I'm assuming there will be other files missing as well.

 I've always been able to solve problems with enough time or finding solutions online, but I've never had any luck with FTP, I'm hoping to change this ASAP.

 Last week I managed to get an FTP server working through vsftpd, I couldn't upload/download any files, always getting a 553 error, even though there were no files to overwrite....

 Any help in getting FTP working on my system with virtual users would be much appreciated, I've followed so many tutorials and threads on here only to find nothing works at the "congratulations your server is ready" stage.

---

### Post by Toriku on 2012-11-20
The Solution was to "apt-get --purge", and "apt-get --reinstall", all the missing files were regenerated

---

