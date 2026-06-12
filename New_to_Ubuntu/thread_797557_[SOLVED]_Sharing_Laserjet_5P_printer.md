---
title: "[SOLVED] Sharing Laserjet 5P printer"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Contemporani on 2008-05-17
Hi!

I am trying to share my HP Laserjet 5P printer connected via LTP to a Ubuntu 8.04 machine.

After installing Ubuntu, I installed the printer with the options by default and printed a test page, successfully.

The next step was checking if it was connection between this machine and others using the "ping" command.

Later, I added a "new printer" to another Ubuntu machine. The "HP_Laserjet_5P" did not appear within the listed devices and I added "other" with the URL "http://192.168.1.33:631/printers/HP_Laserjet_5P". It did not give any error message but when printing a test page it just does not work.

Finally, I tried to add the printer to a Windows XP Pro machine using the "Add Printer Wizard", with the option "Connect to a printer on the Internet or on a home or office network" with the URL "http://192.168.1.33:631/printers/HP_Laserjet_5P". I got the message "Windows cannot connect to the printer. Either the printer name was typed incorrectly, or the specified printer has lost its connection to the server".

Any suggestions to make the printer "visible" in the other Ubuntu and in the other Windows machines?

Thanks in advance.

---

### Post by dstew on 2008-05-17
On the computer that the printer is connected to, in System --> Administration --> Printing, click on the Server Settings tab, and check the box "Share published printers connected to this system". In the Local Printers tab, select the printer, and in the Policies tab, State, check "Shared".

---

### Post by Contemporani on 2008-05-18
Thanks!

It solved my printing problem both in Ubuntu and Windows.

---

