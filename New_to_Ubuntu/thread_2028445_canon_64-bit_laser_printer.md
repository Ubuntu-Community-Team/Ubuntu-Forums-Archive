---
title: "canon 64-bit laser printer"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by krishnan t s k on 2012-07-18
And so upon upgrading to the LTS release, i let my laser printer gather dust for the past few months before i decided to reconfigure it today... i followed the steps in
[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)
but now i'm getting this error in the printer status:Idle - File "/usr/lib/cups/filter/pstocapt" not available: No such file or directory
Please help!!!
i'm using canon LBP2900 and OS is ubuntu 12.04 64-bit
the same printer was working well in ubuntu 11.10
thanks in advance for your help :)

---

### Post by krishnan t s k on 2012-07-21
ok i managed to solve the pstocapt error... but i ran into another one now

```
sudo ccpdadmin

Usage: 
  ccpdadmin [-p Printer-name -o Printer-dev-path]
  ccpdadmin [-x Remove-Printer-name]


 CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787

 Entry Num  : Spooler    : Backend    : FIFO path        : Device Path     : Status 
 ----------------------------------------------------------------------------
     [0]    : Canon-LBP2900-CAPT-English     :          :                     : /dev/usb/lp0     : invalid Spool Name
     [1]    : LBP2900     : ccp         : /var/ccpd/fifo0     : /dev/usb/lp0 : 

```i'm getting two printers and the CAPT printer with invalid spool name... what am i doing wrong and how should i proceed
please help!!

---

### Post by krishnan t s k on 2012-07-21
help needed very urgent... someone please reply!!!

---

### Post by chandraubunt on 2012-07-24
> **krishnan t s k said:**
> help needed very urgent... someone please reply!!!
  hai  I am also having the same problum with my lbp 2900b printer and ubuntu 12.04. when I  send an  e-mail to the Canon company,they  said that lbp2900 b didn't support ubuntu , that is all !!. Now I am looking through this community for help.

---

