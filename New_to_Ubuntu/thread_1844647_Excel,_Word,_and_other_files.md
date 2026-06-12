---
title: "Excel, Word, and other files"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by Sheenders on 2011-09-15
:guitar:I recently installed 11.04 and am working with it to better understand.  How do I find Excel, Word, and other files (photos, music, etc.) that were installed and still exist on Windows Vista, which is also still on this computer?  Anything you could help with finding the files and opening them in Libre Office would be helpful.

Sheenders

---

### Post by coffeecat on 2011-09-15
Welcome to the forum!

Open a nautilus file browser by clicking on the home folder icon at the top of the launcher bar - if you are running the Unity desktop. If the classic desktop go to the Places menu. The next bit depends on how you installed Ubuntu.

If you installed Ubuntu to its own partition as a conventional dual-boot, you'll see your Windows C: partition in the left Places pane of the nautilus window. It'll show as either the size of the partition, or the partition label if it is labelled. Simply click on it.

If you installed Ubuntu in wubi, which is a way of installing it in the Windows partition, click on "File System" on the left. Then open the host folder.

**EDIT**: I should have added that you will see the folders of your C: drive, plus a few folders and files that are hidden in Windows. You need to open the folder with the user accounts, then your account folder and then you should be able to find your Office files. If you double-click in the normal way, they will open in Libre Office.

---

### Post by vasa1 on 2011-09-15
> **Sheenders said:**
> ... opening them in Libre Office would be helpful.
...

One more precaution is to save each file in the corresponding LibO format --- .odt or .ods --- as soon as you can and then work on those files saved in the LibO format. LibO can misbehave if made to work on files which are still in the .doc or .xls formats.

Also, you should consider if you will be exchanging documents & spreadsheets with users of MS Windows systems. In that case, it maybe better to leave the files on the ntfs partition. People with more experience please chip in :)

---

### Post by P05TMAN on 2011-09-15
> **vasa1 said:**
> One more precaution is to save each file in the corresponding LibO format --- .odt or .ods --- as soon as you can and then work on those files saved in the LibO format. LibO can misbehave if made to work on files which are still in the .doc or .xls formats.

Also, you should consider if you will be exchanging documents & spreadsheets with users of MS Windows systems. In that case, it maybe better to leave the files on the ntfs partition. People with more experience please chip in :)

I am currently a student I use LibreOffice for all of my assignment needs. My school uses MOffice. I have never experienced an issue outside the occasional minor line break inconsistencies saving to the original Microsoft extension, be it Excel, Word or even Power Point.

---

### Post by vasa1 on 2011-09-15
> **P05TMAN said:**
> I am currently a student I use LibreOffice for all of my assignment needs. My school uses MOffice. I have never experienced an issue outside the occasional minor line break inconsistencies saving to the original Microsoft extension, be it Excel, Word or even Power Point.

I'm not implying there will be problems in *saving* to Microsoft formats. I'm suggesting that it isn't a good idea to *work* in those formats.

---

### Post by P05TMAN on 2011-09-15
> **vasa1 said:**
> I'm not implying there will be problems in *saving* to Microsoft formats. I'm suggesting that it isn't a good idea to *work* in those formats.

Oh, I guess I didn't catch that...cheers

---

### Post by madjr on 2011-09-15
> **Sheenders said:**
> :guitar:I recently installed 11.04 and am working with it to better understand.  How do I find Excel, Word, and other files (photos, music, etc.) that were installed and still exist on Windows Vista, which is also still on this computer?  Anything you could help with finding the files and opening them in Libre Office would be helpful.

Sheenders

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Sheenders on 2011-09-15
Thank you for the welcome and for the help with finding the files.  The process worked perfectly (I guess you already knew that it would).  Now I can get down to exploring Ubuntu and what it can do.  I did a lot of navigating through files I found before I asked my question but just didn't get the right one.
Thanks very much for your help.
Sheenders

---

### Post by wildmanne39 on 2011-09-15
Hi, I am glad you got it worked out.

I would like to add if you plan on putting your files in ubuntu from windows it is best to copy them instead of move them, I have seen people move them and lose them where copy seems to always work.
Thank you

---

