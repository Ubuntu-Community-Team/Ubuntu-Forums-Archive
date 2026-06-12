---
title: "How do I remove printers???"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by sillyboy on 2008-08-27
I have 2 printers I want to remove from Ubuntu. A HP printer is no longer
hooked up (but still shows up in the list of printers) and the ML2010 needs to be reinstalled.  Any help would be wonderful.

Thanks

---

### Post by swegner on 2008-08-27
Go to System > Adminstration > Printing, which opens the printer configuration.

Select the printer you want to remove, and press "Delete".

---

### Post by bobnutfield on 2008-08-27
To do it from the desktop, go to System>Administration>Printing.  This will open the printing config GUI.  Just highlight the printer you want to delete, and delete it from there.

If you want to do it from the command line:

> sudo lpq

This will list the names of your printers, then

> lpadmin -r <name of printer from above command>

---

