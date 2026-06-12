---
title: "Can you help me with this aMSN install error?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by psam3 on 2008-10-29
I was installing aMSN with some linux packager thing and it did a bunch of stuff in a terminal window and said it is now ok to install. So I clicked run on the package and it started but then I got this error:

Checking for required C library versions ... OK
Checking for X ... OK
Checking for TCL Scripting Language ... failed
-------------------------------
Error: Could not find 'TCL Scripting Language'. Try using the native package manager for Ubuntu 8.04.1 (apt-get) to install a package with similar name to 'tcl'. 

Error: Unable to prepare package AMSN MSN client.

I can't this TCL thing in the add/remove programs. 

Thanks

---

### Post by brandoncolorado on 2008-10-29
Try this:

System -- administration -- Synaptic package manager.

Search for TCL and check those boxes.

Edit:  Changed to add this:

Your same problem
[http://ubuntuforums.org/archive/index.php/t-505239.html](http://ubuntuforums.org/archive/index.php/t-505239.html)

SHORT ANSWER:

Use that synaptic package manager to install AMSN.  Just search AMSN there, check the box and it will install the required files for you!

---

### Post by jenkinbr on 2008-10-29
> **psam3 said:**
> I was installing aMSN with some linux packager thing and it did a bunch of stuff in a terminal window and said it is now ok to install. So I clicked run on the package and it started but then I got this error:

Checking for required C library versions ... OK
Checking for X ... OK
Checking for TCL Scripting Language ... failed
-------------------------------
Error: Could not find 'TCL Scripting Language'. Try using the native package manager for Ubuntu 8.04.1 (apt-get) to install a package with similar name to 'tcl'. 

Error: Unable to prepare package AMSN MSN client.

I can't this TCL thing in the add/remove programs. 

Thanks

Try:
```
sudo apt-get install tcl
```
I've noticed that add/remove applications does not always list all possible software (especially libs and -dev packages), which is probably what you are experiencing.  You can also search for the 'tcl' package in synaptic.

---

### Post by psam3 on 2008-10-29
Thanks, that worked great.

---

