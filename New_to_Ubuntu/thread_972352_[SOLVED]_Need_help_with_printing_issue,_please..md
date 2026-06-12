---
title: "[SOLVED] Need help with printing issue, please."
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Tom.Servo on 2008-11-05
Hello all,
  I have searched and turned up drivers for my Canon MP600 All In One. I have done as instructed and used alien to convert from an RPM to a DEB and have sucessfully installed the drivers. I then added the printer via Admin/Printers and all *appears* ok. The printer shows up and is showing as "Idle", however when I print a test page, nothing happens. I installed the scanner tools and the scanner portion works fine, I just get nothing when trying to print. 

I ran across several installs and used this one: 
[http://ubuntuforums.org/showpost.php?p=2763437&postcount=4](http://ubuntuforums.org/showpost.php?p=2763437&postcount=4)

However, when I try to complete these steps:
[B]sudo apt-get install libxml1
sudo apt-get install libglib1.2
sudo apt-get install libtiff4[/B]

I get the following error:
[I]Package libxml1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxml1 has no installation candidate[/I]

However, I'm not sure that's what's keeping me from printing, although it might be. Any help would be GRACIOUSLY appreciated. Thanks

EDIT: I would also like to note that I can see the job going through the Print Queue as well, but nothing prints.

---

### Post by Tom.Servo on 2008-11-05
Quick bump. Anyone have any idea? I appreciate it!

---

### Post by squeabs on 2008-11-05
Have you tried installing the driver from the manufacturer's website in wine and using it in ubuntu? It might help.

---

### Post by Tom.Servo on 2008-11-05
Hmm. No I never thought of going that route. I have wine installed for Photoshop, so using it isnt a problem. Are drivers something that can be sucessfully installed and used via Wine?

---

### Post by squeabs on 2008-11-05
I suppose it would work the same way. There are multiple guides for wireless network drivers that have you install them via wine. I don't think a printer driver would be very different, although I've never tried it before.

---

### Post by Tom.Servo on 2008-11-05
Cool. I knew there were ways to install Windows wifi drivers but that was via NDISWrapper I didnt think you could use Wine for drivers as its usually application only, but I'll definitely check into it. Thanks for your input.

---

### Post by ad_267 on 2008-11-05
I'm pretty sure you can't install windows printer drivers for Ubuntu using wine.

Have you tried the PIXMA MP610 drivers that are included in Ubuntu? That printer looks very similar.

This might help if that doesn't work: [http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html](http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html)

---

### Post by Tom.Servo on 2008-11-05
Problem has been fixed. ad_267 thanks for your link, this is what fixed it(from ad_267s link):

[I]Other than those files, you need some old library to support it like libtiff3 and libpng3. I can't find the libtiff3 on the repository so I make softlink to point libtiff3 to libtiff4. Without this installation, you won't be able to print anything.

cd /usr/lib/
sudo ln -s ./libtiff.so.4.2.1 ./libtiff.so.3[/I]

Thanks a million!

---

### Post by shane19174 on 2008-11-12
Just to clarify, you're using both the printer and scanner driver that you downloaded directly from canon, right? I've got an MP600 that prints but without any of the fancy functions it's capable of under windows (I haven't even set up scanning as of yet). So I'm interested to know exactly which route you followed and how pleased you are with the results. (Unfortunately, I don't have a lot of time to experiment on my own right now.)

Thanks

---

### Post by Tom.Servo on 2008-11-12
> **shane19174 said:**
> Just to clarify, you're using both the printer and scanner driver that you downloaded directly from canon, right? I've got an MP600 that prints but without any of the fancy functions it's capable of under windows (I haven't even set up scanning as of yet). So I'm interested to know exactly which route you followed and how pleased you are with the results. (Unfortunately, I don't have a lot of time to experiment on my own right now.)

Thanks

Correct. And you are also correct in stating a lot of the fancy printing settings are not available, but there are enough to get the job done. And as far as scanning, it works great. 

All I did was convert the Canon downloaded files to deb and run the installers. The scanner installer needed nothing after the install, it just worked. For the printing I first made sure CUPS was installed and updated and did the following and it all worked:

[I]Other than those files, you need some old library to support it like libtiff3 and libpng3. I can't find the libtiff3 on the repository so I make softlink to point libtiff3 to libtiff4. Without this installation, you won't be able to print anything.

cd /usr/lib/
sudo ln -s ./libtiff.so.4.2.1 ./libtiff.so.3[/I]


Let me know if you have any questions and I'll try to help.

---

