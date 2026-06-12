---
title: "LibreOffice Writer won't print graphics"
date: 2014-11-19
forum: New to Ubuntu
---

### Post by gtg207v on 2014-11-19
When I paste graphics/images into an odt file in LibreOffice Writer the graphics do not print out. Furthermore, when I include bullets in the document, the bullets are printed at the very edge of the paper. The print preview shows up correctly. However, printing the document produces the failure.

I printed the document from two Linux machines: Ubuntu 14.04 and Linux Mint. The error occurs when printing from both of those operating systems. However, when I print the same file from a MacBook Pro, the print out comes out as expected. The printer that I have is a Kodak All-In-One C310.

Thank you in advance. Any help with be great.

---

### Post by ajgreeny on 2014-11-19
In the print dialogue box, make sure that the option to print pictures is selected.  It does not matter whether you have the LO Print dialogue box or your OS's version; they both have the option available in the **LibreOffice Writer** tab

---

### Post by gtg207v on 2014-11-20
Thanks for your response. Unfortunately, I've tried that already. The check box to print pictures is marked by default. Unchecking the box removed the pictures from the preview. After marking it again, the problem still persists.

---

### Post by amanchesterman on 2014-11-20
Can you print an image successfully? I mean a photo or graphic, not using LibreOffice but using an image viewer program instead. I'm wondering if the problem is to do with your printer driver, I don't know how well that model is supported in Linux.
For comparison, I have a HP Deskjet 1000 and it works perfectly with LibreOffice 4.3.3.2, so the issue is something particular with your setup.

---

### Post by gtg207v on 2014-11-22
When I print a simple pdf, the pdf comes out as expected. However, when I open the pdf in gimp and cut a part of the image and paste it into a Libre Office Writer, the image does not get printed from Libre Office. Even when I try to export the odt as a pdf, it does not come out correctly. I thought upgrading my LO would work, but the problem still exists for me for 4.3.3.2.

---

### Post by amanchesterman on 2014-11-24
There are one or two other threads about similar issues so it seems you aren't alone. Some people found a solution by changing the image format. You say the problem arises when you cut a part of the image and paste it into LibreOffice Writer: what format are you using? The posts I have read suggest that .png images can be problematic but that they print OK when converted to .jpg.
Have you tried cutting and pasting using LibreOffice Draw, rather than Gimp? It may be that if you use Draw, the image pasted into Writer will already be converted into the right format -- whereas Gimp, presumably, does not make that conversion.
Also you may find some help in this thread: [http://en.libreofficeforum.org/node/692](http://en.libreofficeforum.org/node/692) Although the initial post is from 2011 and relates to an older version of Writer, the final post at the bottom is from 2014 and relates to the 4.2 release. The author of the post explains how he solved the problem by altering the printer settings.

As a general point, if you have problems with LibreOffice you may find it easier to get help in the LibreOffice forums. You're welcome to post your query here in the Ubuntu forums too, but many Ubuntu users don't use LibreOffice much and (like me) don't have the specialist knowledge to answer your query.

---

### Post by gtg207v on 2014-12-07
I apologize for using the wrong forum. I thought my problem may be specifically related to Ubuntu.

However, as an update, I tried to open the pdf in Libre Draw. I was halted by a dialog asking for a password. I tried doing the same thing on a macbook and was visited by the same problem. It seems that the file may be encrypted which may be causing the print problems I've been having. I opened up the pdf in GIMP exported it as a pdf. It was then I was able to open the newly exported pdf in Libre Draw. I was able to then do the copy and paste from Draw and insert it into the Writer doc. Overall, it seems that I found a work around. The real problem may be that the pdf was encrypted the entire time. 

I'll mark this solved and may visit a LibreOffice forum if necessary. Thanks for everyone who helped out with suggestions!

---

### Post by bapoumba on 2014-12-07
To note, pdf can be created preventing parts of the document or the whole document to be copied or printed. Where was that pdf from ?

---

