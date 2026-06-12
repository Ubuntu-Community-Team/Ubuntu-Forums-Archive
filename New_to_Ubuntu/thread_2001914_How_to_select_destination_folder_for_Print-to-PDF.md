---
title: "How to select destination folder for Print-to-PDF"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Ralph L on 2012-06-11
I have installed cups-pdf to perform the print-to-pdf function.  However, it always puts the output file in Home/PDF.  It is a nuisance to always have to move the file.  Is there a way under cups-pdf to set the destination folder during the print function?  Or is there another print-to-pdf program that would fix the deficiency?  If I install the print-to-pdf addon to Firefox, I am able select the destination folder so I know it can be done.  Running Lucid and soon Precise.

Thanks in advance.

Ralph

---

### Post by Cheesemill on 2012-06-11
You don't need to install any software, not even cups-pdf.

Just select Print to File from the Print dialog, select PDF as type and you can choose where the output goes.

---

### Post by Ralph L on 2012-06-17
Thanks a lot.  I missed that option and feel a little foolish.  What you suggested was exactly what I wanted.  Really appreciated the reply.

Ralph

---

### Post by bab1 on 2012-06-17
> **Ralph L said:**
> I have installed cups-pdf to perform the print-to-pdf function.  However, it always puts the output file in Home/PDF.  It is a nuisance to always have to move the file.  Is there a way under cups-pdf to set the destination folder during the print function?  Or is there another print-to-pdf program that would fix the deficiency?  If I install the print-to-pdf addon to Firefox, I am able select the destination folder so I know it can be done.  Running Lucid and soon Precise.

Thanks in advance.

Ralph

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=4318842&postcount=12") for the answers.  This is not just "change the settings in the cups/pdf conf file".  You will have to modify the apparmor too.

Edit:  The Google search for additional info is [**_[COLOR="Blue"]here[/COLOR]_**]("https://www.google.com/search?q=ubuntu+cup%2Fpdf+apparmor&btnG=Go!#hl=en&sclient=psy-ab&q=cups-pdf+ubuntu+apparmor&oq=ubuntu+cups%2Fpdf+apparmor&aq=0bK&aqi=g-bK1&aql=&gs_l=serp.1.0.0i8i30.5461.5461.0.7389.1.1.0.0.0.0.166.166.0j1.1.0...0.0.By14E7oNT0c&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=fb4c575ddcccef5a&biw=1201&bih=651").

---

