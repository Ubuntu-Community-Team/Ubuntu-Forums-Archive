---
title: "[SOLVED] Steps to install printer from terminal"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by jerrallan on 2008-05-05
A couple of years ago I installed a printer driver using the tar.gz file. 

I have looked on Ubuntu, and  other sources and can't find the complete code to enter from the terminal to install.  Everything seems to be automated or semi-automated and I have been unable to find a package to install "automatically".

I have a Lexmark 3470 and am trying to install what looks like a comparable HP printer.
I have 8.04. Would like to install HPLIP-2.8.4.tar.gz.

Could somebody provide me the complete process [tar,make,install,etc] or refer me to a link.

I would appreciate it.

---

### Post by njparton on 2008-05-06
Isn't there a readme file contained in that compressed tar file?
 
```
 
gunzip HPLIP-2.8.4.tar.gz
tar -xvf HPLIP-2.8.4.tar

```
 
Then hunt for a readme or similar file.

---

### Post by jerrallan on 2008-05-09
There isn t a readme file. I downloaded hplip from sourceforge. I just couldn't get any of the all-in-ones of hp to work with my Lexmark.  Gonna have to try out an HP.

---

### Post by glennric on 2008-05-09
I don't know if this will help or not, but there is a howto for some Lexmark printers.  It is [here]("http://ubuntuforums.org/showthread.php?t=49714&highlight=howto+lexmark")

---

### Post by jerrallan on 2008-05-09
Thanks. I tried to install the z600 cups from that post. Had a problem with tail. Couldn t get it to work no way  had the gz.sh part of it to tail and the terminal went crazy with gibberish.  -n +143 did that. I couldn't get any other combination of tail to work. I followed tail --help.

But problem solved. My son and I swapped printers.  I gave him my Lexmark for his HP. 3 seconds after I plugged in the usb cord to the computer, Ubuntu told me it had been installed.

---

