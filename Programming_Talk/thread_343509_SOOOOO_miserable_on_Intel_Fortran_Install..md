---
title: "SOOOOO miserable on Intel Fortran Install."
date: 2007-01-21
forum: Programming Talk
---

### Post by hopestorm on 2007-01-21
Always tell me the Serial number is registered to another account. If use the license file, it always returns to the first page and willn't start to install at all.

Tried 3 emails already, all got the same results.. This happens to anybody else?

---

### Post by fadder on 2007-01-22
Have you read the various HOWTO's which can be found on these forums? 
The solutions are different for edgy and dapper, so make sure you have the right ones.

I can't quite remember all the steps I did, but one source of problems
was that /bin/sh was linked to dash instead of bash in edgy. Changing this
helped a lot (since bash allows "source" to work if I remember right).

Then used alien -k .....rpm

And copied all license file to /opt/...

but check out the other mails

---

### Post by neoflight on 2007-01-22
i have it in edgy....same problem with the numbers...
use the file....do not use the numbers.... 

save the lic file and gave the path to the file to the installer....

---

### Post by mazzanti on 2007-02-05
This is driving me mad, guys. I've read all (I believe) post regarding Intel fortran installation on Edgy and none seems to help here.
I have the same trouble: Serial number doesn't work... but feeding in the path to the license file doesn't help either. It always spits me back to the original screen, stating that my license is not valid. Now I have three of these licenses and none of them work here, while I can use them safely in other computers I have at work. that means the license files are right, but the intel installation script refuses to understand them on Eegy.
I have tried to convert the rpm's to deb's, to edit the install.sh and the bin/ifort and bin/ifortvars.sh as stated in other posts, but that doesn't work either.
Going to install_fc.sh there is this >INSTALLDIR> reference in the  variables, and the scripts do not understand what that means since (I believe) I haven't gone through a standard installation.
So my problem is at the license detection stage... Anybody knows how to proceed?

thanks a lot,

Ferran.

> **neoflight said:**
> i have it in edgy....same problem with the numbers...
use the file....do not use the numbers.... 

save the lic file and gave the path to the file to the installer....

---

### Post by jeremytaylor on 2007-02-08
The simple solution is just to edit those scripts and replace INSTALLDIR with the correct path....

jeremy

---

### Post by mazzanti on 2007-02-08
But I have done this also and still refuses to work! It complains about ifortbin not exsting, while I can see it when I do an 'ls -als' and it has read and execute permissions for everybody...
Any other hint?

> **jeremytaylor said:**
> The simple solution is just to edit those scripts and replace INSTALLDIR with the correct path....

jeremy

---

### Post by lauralee on 2008-01-11
I'm having *exactly* the same problem, with the license detection:
"Serial number doesn't work... but feeding in the path to the license file doesn't help either. "

Has anyone figured it out? I've read and read on the net and really not found a solution.

---

