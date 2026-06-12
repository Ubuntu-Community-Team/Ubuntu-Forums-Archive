---
title: "HOWTO: Sharing Printers"
date: 2006-03-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Dylan103 on 2006-03-01
****Note- Only Tested On HP Deskjet 810C and worked.


Linux Operations
---------------------------------
System > Administration > Printing
Now click Add New Printer.
Select Netowork Printer.
Then Windows Printer(SMB)
See Windows Operations for required information and next steps.

Windows Operations
---------------------
Go Start > Run and type in CMD
Then type ipconfig in the dos window.
Find and write down your IP Adress.
Then,
Start > Control Panel > Printers And Other Hardware > Printers And Faxes. Then Right click the current printer and click Sharing.
Click the checkbox beside Allow Sharing, and give it a name such as Printer or something.

Linux Operation Part2
------------------------
In The Host area put the IP adress of the Windows Computer.
In the Printer area put the name of the printer in the sharing ( My example printer ).
Now hit Forward, Then chose your Printer Manufacturer and Series.
Then hit Apply.

---

