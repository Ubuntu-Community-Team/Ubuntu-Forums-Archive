---
title: "Unable to open saved excel files (.xlsx) and word files (.docx)"
date: 2018-07-29
forum: New to Ubuntu
---

### Post by parottrajesh on 2018-07-29
Installed MS office 2007 using playonlinux, then its created the icons of ms office word and excel on desktop. While trying to save the documents after typing on it allows save as option and saving with extension ".xlsx" for excel and ".docx" for word. While trying to open it asking for select application, open with option not showing the ms word in the list of installed applications which actually installed using "playonlinux"

---

### Post by Mark Phelps on 2018-07-30
What version of MS Office did you install? Asking because only the really OLD versions (i.e., 2010 and prior) work in Wine.

---

### Post by fyfe54 on 2018-07-31
Libreoffice opens, reads, saves MS Office formats.  I hear that complicated MS formatting sometimes doesn't convert exactly, but I have never had trouble.  My formatting needs are modest however and have not caused issues.

---

### Post by parottrajesh on 2018-08-01
Hi Mark,
I am new to linux, installed ms office 2007 successfully and its automatically created the icons of word,excel and powerpoint on desktop. After opening the word icon from the desktop and type something to save it allows to do save as only and saving the file with0 .docx extention. while trying to open it system doesnt showing the ms office word application in installed list.

---

### Post by Mark Phelps on 2018-08-01
From what I recall, the docx and xlsx format first appeared with Office 2007 -- but I believe the DEFAULT was to save in the old .doc and .xls formats.

You might try saving in the old formats -- but understand any Windows PC that you exchange these files with will probably automatically convert them to the newer formats when first opening them.

As to MS Office alternatives, I tried a recent 2016 version of WPS Office (the new name for Kingston Office) and it had no problems with the newer docx and xlxs files.

---

### Post by Impavidus on 2018-08-02
> **parottrajesh said:**
> while trying to open it system doesnt showing the ms office word application in installed list.

So, right now you open the file manager, navigate to the file and double-click it, hoping that the file manager knows what application to start and how to instruct it to open that file, which apparently doesn't work. Instead, you could try and start word/excel, click "open", navigate to the file and open it. You can run those applications, it's how you created the files.

BTW, I think that if you create an appropriate .desktop file, the file manager should recognise your word/excel application and know how to use it to open a file. With the icon already on your desktop, it seems a .desktop file exists. You may have to edit it.

---

### Post by deanr2 on 2018-08-02
> **Mark Phelps said:**
> From what I recall, the docx and xlsx format first appeared with Office 2007 -- but I believe the DEFAULT was to save in the old .doc and .xls formats.

You might try saving in the old formats -- but understand any Windows PC that you exchange these files with will probably automatically convert them to the newer formats when first opening them.

As to MS Office alternatives, I tried a recent 2016 version of WPS Office (the new name for Kingston Office) and it had no problems with the newer docx and xlxs files.

I second the use of WPS office. YOu can get it here: [http://wps-community.org/downloads](http://wps-community.org/downloads)

---

