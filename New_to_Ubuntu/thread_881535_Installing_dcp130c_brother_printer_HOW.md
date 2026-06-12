---
title: "Installing dcp130c brother printer HOW???"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by pdhb on 2008-08-06
I have recently installed Ubantu 8.04 on my system and am keen to rid myself of windows, my last obstacle is getting my Brother DCP130C printer to operate.

can anyone help with this?

thanks in advance

---

### Post by plucky on 2008-08-06
> **pdhb said:**
> I have recently installed Ubantu 8.04 on my system and am keen to rid myself of windows, my last obstacle is getting my Brother DCP130C printer to operate.

can anyone help with this?

thanks in advance

Open **Synaptic Package Manager** and search for **brother dcp-130c**
 and it should display "brother-cups-wrapper-bh7" and brother-lpr-drivers-bh7".Tick the two boxes and apply.

This will install the drivers for your printer.**Turn on printer**

The go to **System > Administration > Printing** and select **New printer**.Cups should find and install your printer.

If you have any problems,the best method of troubleshooting is to open Firefox and put ```
http://localhost:631
``` into the address bar.This will open the CUPS interface which gives you access to the error logs and config data.

Good Luck

:)

---

### Post by pdhb on 2008-08-08
Hi plucky,

thank you very much. I did just what you said and it worked perfectly. i have been trying to get this going for weeks now.

thanks again
pdhb

---

### Post by nepo125 on 2012-07-25
I tried what u said but still I cant print. I have BROTHER DCP-130c printer/scaner...


I hope you can help me install the printer as well as the scanner. I really need it. please. I'm a newbie, using Lubuntu 12.04. I don't know many about linux things.

please help me. I am willing to learn through this.

Thank you in advance.

---

### Post by uzumakifahim on 2012-07-25
@[nepo125]("http://ubuntuforums.org/member.php?u=1409286"), at Lubuntu 12.04 you don't get Synaptic Package Manager by default. You have to install that first. You can do that by Lubuntu Software Center. Please also describe your issue more clearly, so that everyone can understand easily and can solve your problem ASAP.

Thanks.

---

### Post by Ruhani04 on 2012-10-06
Just follow this:

[http://voices.yahoo.com/the-retail-detail-brother-releases-drivers-installer-7131276.html?cat=15](http://voices.yahoo.com/the-retail-detail-brother-releases-drivers-installer-7131276.html?cat=15)

---

