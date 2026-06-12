---
title: "Problems 'finding' Office 2007 after installing on Ubuntu"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by dmahoon on 2012-09-19
Hi there,

Second post for me...I'm still in the steep end of the learning curve here.

I've installed Ubuntu 12.04 successfully and Wine 1.0.4 to help out with Windows applications.

I was hoping that I wouldn't need to use Windows anymore but my work involves a lot of editing of word documents that need to be sent back to people that are not running on Linux.  I've done some experimenting with Libre, and I quite like it, but when I email work back to my colleagues, they can't see what I've done or they just can't open the files.  Bad news!

Last week I attempted to install Office 2010 into ubuntu by downloading it from the technology website at the university where I work.  It got about 3/4 of the way through the install and I got an error message.  

Next I went to the Wine website and found that Office 2007 was somehow more compatible and I performed the same exercise.  I downloaded the file from the tech website, ran it and successfully installed it.  Good news!

Next I did some experimenting with files that were sent to me as attachments by email....usually .doc files.  When I click on the file, a Wine window pops up and asks me if I want to use Libre or 'Other application' to open the file.  If I click on 'Other' I can't seem to 'find' Office 2007.

Now, I wonder if I've actually installed the Office file.  Have I missed performing something at the end of the installation?  Do I need to do something in Wine to make it 'recognise' the file I've installed?

Any information would be most appreciated by this greenhorn...

---

### Post by androssofer on 2012-09-19
> **dmahoon said:**
> Hi there,

Second post for me...I'm still in the steep end of the learning curve here.

I've installed Ubuntu 12.04 successfully and Wine 1.0.4 to help out with Windows applications.

I was hoping that I wouldn't need to use Windows anymore but my work involves a lot of editing of word documents that need to be sent back to people that are not running on Linux.  I've done some experimenting with Libre, and I quite like it, but when I email work back to my colleagues, they can't see what I've done or they just can't open the files.  Bad news!

Last week I attempted to install Office 2010 into ubuntu by downloading it from the technology website at the university where I work.  It got about 3/4 of the way through the install and I got an error message.  

Next I went to the Wine website and found that Office 2007 was somehow more compatible and I performed the same exercise.  I downloaded the file from the tech website, ran it and successfully installed it.  Good news!

Next I did some experimenting with files that were sent to me as attachments by email....usually .doc files.  When I click on the file, a Wine window pops up and asks me if I want to use Libre or 'Other application' to open the file.  If I click on 'Other' I can't seem to 'find' Office 2007.

Now, I wonder if I've actually installed the Office file.  Have I missed performing something at the end of the installation?  Do I need to do something in Wine to make it 'recognise' the file I've installed?

Any information would be most appreciated by this greenhorn...

When you install it in wine, you need to open Office 2007 via the wine menu, then open the document that way..

However I havent used it in a few years, so dont know if this is still the case. Nor how to open it in the unity interface... :-(..

if you dont mind scripts there is a section on this page :

[https://help.ubuntu.com/community/Wine#Creating_file_associations](https://help.ubuntu.com/community/Wine#Creating_file_associations)

that tells you how to aim certain files to wine applcations. Look under the "Creating File associations" section

---

### Post by MG&amp;TL on 2012-09-19
> **androssofer said:**
>  Nor how to open it in the unity interface... :-(..


The same way. Just open wine and open as per usual.

---

### Post by Mark Phelps on 2012-09-19
Just so you know ... WINE is not a miracle cure.  MS Office is one of the things that doesn't work well in Wine, the newer the version, the poorer it works.

MS Word, as can be seen in the link below, gets a Silver rating -- meaning some functions simply won't work:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=10]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=10")

IF you have to rely on MS Office components on a daily basis, you would do better to run MS Windows in dual-boot mode, or in Virtualbox.  You will find the Wine implementation comes with lots of limitations.

---

### Post by dmahoon on 2012-09-19
Thanks for the replies, I'll keep plodding along with this and see what happens.

---

