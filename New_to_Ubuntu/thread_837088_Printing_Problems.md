---
title: "Printing Problems"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Kavkaz86 on 2008-06-22
Hi Members, 

I'm having troubles with my printer. 

The error message I keep getting while trying to print a test page is : - 
"CUPS server Error - There was an error during the CUPS operation;'client-error-document-format-not-supported" .

My Printer is LEXMARK X1185 

Any help would be very much appreciated;

kavkaza

---

### Post by fatality_uk on 2008-06-22
OpenPrinting says this installs and work perfectly.
[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X1185](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X1185)

Can you print a test page from within CUPS?
[http://localhost:631/](http://localhost:631/)

---

### Post by impman2005 on 2008-08-22
How do I log in as root?  (Complete newb here, sorry)

---

### Post by JillSwift on 2008-08-22
> **impman2005 said:**
> How do I log in as root?  (Complete newb here, sorry)You can't - root's login is disabled by default as a security measure.
You can run commands as root, however, with "sudo".

Just put "sudo" in front of the command you need to run as root and it will ask you for your password (give it your account's password - it will not give you any feedback) and it'll run the command passed to it as root.

---

### Post by MyR on 2008-08-29
> **impman2005 said:**
> How do I log in as root?  (Complete newb here, sorry)

sudo su

use with caution.

exit to exit.

peace

---

