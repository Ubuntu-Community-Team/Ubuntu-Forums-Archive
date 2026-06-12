---
title: "Canon printer install"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by Chris611 on 2012-01-15
I'm trying to install a Canon MX410 printer with Ubuntu 10.04.  I followed the how-to on this site and it worked until the last step where it registered the printer.  It could not find the ppd file.  I looked in the error log and see that it's looking in the usr/share/cups/model folder.  There is a ppd file in there but it doesn't have the same name as it's looking for.  I have a ppd file with the exact same name on it, but don't have permission to put it in the usr/share/cups/model folder.  I know basically nothing about using the terminal commands.  So please don't assume I know how to do what may be considered basic stuff...  Any help would be appreciated.

Thanks
Chris

---

### Post by Rodney9 on 2012-01-15
Open a terminal and use this 

sudo cp /home/yourname/?.ppd /usr/share/cups/model

presuming the ppd file is in your home directory and use the full ppd name plus finish /usr/share/cups/model

Rodney

---

### Post by Chris611 on 2012-01-15
Thanks, that worked perfectly.

Chris

---

