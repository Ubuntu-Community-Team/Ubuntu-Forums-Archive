---
title: "MS Office and Wine"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by ExSuSEusr on 2008-08-16
Here's the deal.  I have installed MS Office via Wine.  However, when I start one of the apps - say MS Word for example I get "Change Preferred Use in ~./wine/system.reg" and "Change Preferred Organization......"
 
Ok - so I open system.reg with gedit and change the user and organization - save and close.  Open Word again and the same exact error pops up.
 
Any ideas?
 
And yes I know all about openoffice but I believe MS Office is superior :)

---

### Post by infinitejones on 2008-08-16
First of all - what version of MS Office?

Have a look here [http://appdb.winehq.org/objectManager.php?sClass=application&iId=31]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=31") at other people's experiences of using MS Office under Wine.

One thought is that it might be something to do with the permissions on the file you're editing in the .wine directory and/or the .wine directory itself but I don't have MS Office so I can't try it myself.

If all else fails, try giving Open Office a go. I use it for everything at home and I use MS Office for everything at work, and with the latest version of Open Office I haven't found anything that it can't do that MS Office can...

---

### Post by ExSuSEusr on 2008-08-16
Thanks for the link, but I couldn't find anything that dealt with this specific problem.
 
I run 2007 on my Windows machine and am trying to run 2000 on Ubuntu.  Open Office is a good product, but I am determined to get it working just out of spite now.

---

### Post by Sirron on 2008-08-16
I believe those two settings are actually on the About tab of the wine configuration tool, you could try changing them there

---

