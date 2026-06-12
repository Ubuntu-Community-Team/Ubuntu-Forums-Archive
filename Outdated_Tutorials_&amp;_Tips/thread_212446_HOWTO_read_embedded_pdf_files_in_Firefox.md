---
title: "HOWTO read embedded pdf files in Firefox"
date: 2006-07-09
forum: Outdated Tutorials &amp; Tips
---

### Post by aam-aadmi on 2006-07-09
I had been having problems with the adobe plug-in in Mozilla. Whenever I tried to read an embedded pdf file in Firefox, I would get a blank page. Though I had installed the acroread package and the plug-ins, it was still not working. 

A little more searching in this forum led me to a thread where this had been solved; I followed the advice and things now work. I thought I should write up the solution breifly, and here it is.

Download and save the following:
[http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0.5/enu/AdobeReader_enu-7.0.5-1.i386.tar.gz](http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0.5/enu/AdobeReader_enu-7.0.5-1.i386.tar.gz)
(I saved it on my Desktop.)

Extract the files on the Desktop. You will be able to see a folder called AdobeReader.

Open AdobeReader, then open ILINX.TAR, then open Browser, then open Intelinux. You will see the following file: nppdf.so

Extract nppdf.so to the Desktop.

Now open the terminal and type the following command:
 ```
sudo cp /home/username/Desktop/nppdf.so /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
```
(replace "username" with whatever is relevant for you in the first part of the above command)

Now re-start Firefox and you should be able to read embedded pdf files from within Firefox!

---

### Post by Steve S. on 2006-10-15
Worked great!  Thanks for the fix!

---

### Post by desperado666 on 2006-10-15
What about attaching this file ??????

---

