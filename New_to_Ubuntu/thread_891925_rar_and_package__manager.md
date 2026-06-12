---
title: "rar and package  manager"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by bregale on 2008-08-16
hi all i have recently downloaded a file which is zipped using rar my problen is i cannot un zip them anybody know what i use ?

   my second question is on the package manager i have read the faq it says that you need to reload them is this true i have hardy 8.04 and it is set for the smart update , does it also clean up the extra entries as there are loads listed 


           thanks

---

### Post by jualin on 2008-08-16
Install unrar using Synaptic Package Manager or using the terminal > sudo apt-get install unrar

---

### Post by jualin on 2008-08-16
For the second question (which I didn't see before :) ) You only need to reload the package manager when you change the repositories. If you don't change that then the Update Manager should look for new updates automatically. Good luck!

---

### Post by bregale on 2008-08-16
thanks for your help i will do that.

---

### Post by jualin on 2008-08-16
Glad it helped and Welcome to Ubuntu!

---

### Post by ThaRabbit on 2008-08-17
Concerning this, I would like to point out PeaZip:
[http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)

Graphical tool capable of handling a great amount of archives, including rar.

It installed fine on 8.04 LTS

To install:
Scroll down to find the Linux download links
Select the DEB link
Doubleclick the file once it has completed downloading
The installer application should take care of any missing thing you might need
Once installed, the application will be available under "Applications" - "System Tools"

---

### Post by DezSP on 2008-08-17
If you install unrar then Ubuntu's graphical utility (file-roller) will be able to handle RAR files on its own. :)

---

