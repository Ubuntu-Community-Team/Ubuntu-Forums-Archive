---
title: "Phaser 7760 printer drivers"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by tmalone on 2008-05-28
I am trying to help my office, and know nothing about Ubuntu or Linux in general. I am trying to find the correct drivers for our Phaser 7760 and install them.  Would anyone be able to help me here? I've trolled the forums and googled for nearly an hour and am still stumped. Any help would be appreciated :) Thanks in advance!

---

### Post by halitech on 2008-07-03
download the CUPS Printer package from here

[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=7760&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=7760&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=)

and extract.

Then go to System - Administration - Printing and add a printer. For the connection, select AppSocket/HP JetDirect. Leave the port on 9100 and add the IP address of the printer. Then Select Provide PPD file and browse to where you extracted the files and select the model you have. Then select any additional options you have like extra ram, trays and a hard drive. Give it a name and finish. You should then be up and running

---

