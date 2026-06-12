---
title: "HPLIP toolbox"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by vegas89 on 2014-03-05
[INDENT]                     
[TABLE="class: cms_table_list"]
[TR]
[TD]I am running ubuntu 12.04
[/TD]
[/TR]
[/TABLE]
How do I enable the printer and scan fuctions?   :confused:  I have the HPLIP-GUI installed. When I go to setup the OS does not show my  printer. But the CUPS web interface shows the printer as follows. 
[TABLE="class: cms_table_list"]
[TR]
[TD][deskjet3512]("http://localhost:631/printers/deskjet3512")[/TD]
[TD]deskjet3512[/TD]
[TD][/TD]
[TD]HP Deskjet 3500, hpcups 3.12.2[/TD]
[TD]Idle[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
 How do I get the  HPLIP toolbox to fuction? Thanks for the Help                 
[/INDENT]

---

### Post by buzzingrobot on 2014-03-05
You may need one of HP's proprietary drivers.  Install hplip-gui and run it.

Many HP printers require an HP driver on Linux.

---

### Post by Portaro on 2014-03-05
hp-setup -a to see if the problem is the default config of package hplip on your type of printing software, and proceed to install in  this GUI mode the print.

---

### Post by tgalati4 on 2014-03-06
Some Deskjets are not supported by* hp-toolbox*.  Try installing the printer through the web interface:

[http://localhost:631](http://localhost:631)

---

