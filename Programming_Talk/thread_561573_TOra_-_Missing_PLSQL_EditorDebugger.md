---
title: "TOra - Missing PL/SQL Editor/Debugger"
date: 2007-09-27
forum: Programming Talk
---

### Post by horrendo on 2007-09-27
I built my own version of TOra (1.3.22) and it mostly seems to work fine but I don't see the PL/SQL debugger. If I look in the src directory I see tora-todebugxxx.o files, but I can't find any menu option or button to invoke the debugger. I also don't see any way to Edit PL/SQL packages, triggers, etc. In the Schema Browser I can click on the 'Code' or 'Triggers' tabs and view the code but I don't see how to edit it. Yes, there is the script tab which I can edit, but surely that's not the TOra way of doing things. 
 
For some reason my Help is also not working. If I click 'Help', 'Contents', I see the Help Browser and in the LHS I see "TOra manual", but when I click on it I get nothing in the RHS. 
 
Other (possibly irrelevant) data : 
 
OS = Ubuntu 7.04 
Oracle client = Instant client 10.2.0.3 
Oracle server = 9.2.0.8 
configure command line = ./configure --with-instant-client --with-oracle-includes=/etc/opt/oracle/product/10_2/include --without-kde --without-rpath --with-oracle-libraries=/etc/opt/oracle/product/10_2/lib 
 
Thanks for any suggestions/clues.

---

