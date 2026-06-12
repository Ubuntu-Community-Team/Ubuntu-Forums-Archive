---
title: "Excel file made from ubuntu could not be open in microsoft."
date: 2013-04-15
forum: New to Ubuntu
---

### Post by nhono on 2013-04-15
Hi,

I'm a new user of ubuntu. We are 4 in the ooffice and and 3 of my work mates are using ubuntu. My laptop is the only one that has a windows 7 installed. This week, when I used their computer and make an excel report using the Libre Office calculator, I like how it works. However, when I opened it in my laptop, it says :" _Excel found unreadable in "name of file". Do you want to recover the contents of this workbook? if you trust the source, click yes. _"

This is how the message appears and when I try to click yes, it will open but the file is not the same as what it should be. I tried to save the file with the type: "_Microsoft Office Excel 97-2003 Worksheet (.xls)_" but still it doesn't works. On the other hand, the excels files from windows 7 works well if I open in ubuntu.

Would  somebody help me please? I tried to search in forums what to do but I couldn't find a good answers and sometimes their are but could not understand a lot since I'm not really good in understanding the commands in computer. I tried to upload the file here as attachment but it says the file is invalid... :(.. I run out of ideas already on what to do..

Emman

---

### Post by nerdtron on 2013-04-15
What is the complete filename of the file you created in Libre Office Calc in Ubuntu? Also, are there any illegal characters in the filename you saved like /\": etc.
I suggest you open the file in question in Libre Office and be sure to save it again with a file extension of .xls for microsoft office compatibility.
Still, though, the formatting will not be 100% presevered but it should be pretty close to what you have done in Libre Office.

---

### Post by sachindhiman on 2013-04-15
> **nerdtron said:**
> What is the complete filename of the file you created in Libre Office Calc in Ubuntu? Also, are there any illegal characters in the filename you saved like /\": etc.
I suggest you open the file in question in Libre Office and be sure to save it again with a file extension of .xls for microsoft office compatibility.
Still, though, the formatting will not be 100% presevered but it should be pretty close to what you have done in Libre Office.


this problem is there, even i used with libreoffice v4.0.2.2. 
I have noticed that if .xlsx file has freeze pane, then libreoffice can open it and save also, but when we open this again in MS Excel then file looks corrupted and when microsoft excel repair this then i noticed that my excel sheets are corrupted. I see only one sheet and rest are i get only if i drag from left side of excel sheet.

Please help us in this matter.

- sachin

---

### Post by nhono on 2013-04-15
I save it with a normal file name..no special characters.. but still it could not be opened.

Are their ways to save a file so that we could open it in ms excel? My files becomes corrupted if I choose to repair it. Please help us how to solve this.

---

### Post by Impavidus on 2013-04-15
Libreoffice can save in MS excel format, but the older formats, which are more reliable, don't support all recent features. On the other hand, MS excel should be able to onderstand the native libreoffice format, but I don't think Microsoft has fully implemented that. Why would they support the file format of their competitor? So it may work using the older xls format, as long as you don't use the more recent features.

A completely different solution would be to install LibreOffice on your Windows laptop. It runs on Windows too. See [http://www.libreoffice.org/](http://www.libreoffice.org/)

---

### Post by nhono on 2013-04-15
Thanks.. Your right. I try to save it using the ms 95 format from the computer running LibreOffice and I was able to open it in win 7. However, some of the features were not the same. I could say its almost close to 90% of the original file. 

If I install the LibreOffice in my windows laptop, I'm curios to what will happen. Will I have 2 separate programs or I will still have windows 7 but with a mixed of LibreOffice? I'm sorry for the questions. Please enlighten me. I'm a newbie with these kind of programs.

---

### Post by mastablasta on 2013-04-15
> **nhono said:**
> If I install the LibreOffice in my windows laptop, I'm curios to what will happen. Will I have 2 separate programs or I will still have windows 7 but with a mixed of LibreOffice? I'm sorry for the questions. Please enlighten me. I'm a newbie with these kind of programs.

if you install libre office in win7 it will be just another office suite you have installed. i have it also on XP along with MS office. 

libre office also has a portable version (alooign with many other opensoruce programmes) you can put on USB stick and take with you wherever you go (as long as you go to windows mashcine)...

---

