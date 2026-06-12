---
title: "How to: Use the CUPS web interface to install your printer"
date: 2005-10-10
forum: Outdated Tutorials &amp; Tips
---

### Post by 11hjpphty76lkjj on 2005-10-10
Issue:  Unable to install printers using the standard CUPS web interface and would like to be able to have that funtionality instead of using the Ubuntu Gnome and KDE methods.

Steps:
Open Terminal
sudo gedit /etc/cups/cupsd.conf

Find the section:
"<Location /admin>
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks.  You can change
# the group name using the SystemGroup directive.
#

AuthType Basic
AuthClass System"

Modify this section to:
"<Location /admin>
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks.  You can change
# the group name using the SystemGroup directive.
#

#AuthType Basic
#AuthClass System"

Save
Exit
restart cups (sudo /etc/init.d/cupsys restart)
Go to localhost:631 in your browser.

This will enable you to add printers using the CUPS web interface. 

There may be security implications to making this change--so please take that into consideration before making this modification.  I found it easier to add/remove printer using the CUPS interface than the Ubuntu add printer interface.  But it's all a personal preference.

Aaron

---

