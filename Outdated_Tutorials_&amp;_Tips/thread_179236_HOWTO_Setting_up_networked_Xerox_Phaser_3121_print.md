---
title: "HOWTO: Setting up networked Xerox Phaser 3121 printer on Dapper Drake 6.06"
date: 2006-05-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Ingwar on 2006-05-19
This is for all who has problems installing their networked Xerox Phaser 3121 printer on Dapper Drake 6.06. I have two networked laptops connected through a NETGEAR router. One of them has a mentioned above printer attached and is more sort of a desktop PC. Each laptop is accessing Internet through NETGEAR router. With my Toshiba Tecra M4 laptop I connect to LAN to browse the Internet or to get access to share folders on the Dell ("Desktop"). I had a problem trying to set up my Xerox printer on Toshiba as Xerox does not officially support Linux for this printer. After experimenting for a few days, here is my solution.
1) Once PC is running and connected to the Internet->
2) Go to: System -> Administration -> Printing
3) Click "Global Settings" and make sure the "Detect LAN Printers" choice is marked.
4) Doubleclick on "New Printer"
5) Select "Network Printer" and on the right from it choose "Windows Printer (SMB)"
6) A window will pop up (Authentication Required). Make sure the User name and the Password fields are blank. Hit Connect.
7) Click the arrow on the right of the "Host" field. This will tell you the name of all of the computers connected to your LAN except the one you are working on right now. Choose the name that your Xerox printer is directly connected to (In my case through USB).
8 ) A window will pop up (Authentication Required). Make sure the User name and the Password fields are blank. Hit Connect.
9) Click "Forward"
10) In Manufacturer window choose Samsung -> Model: ML-1750 -> Driver: pxlmono. Click "Forward" -> then click "Apply"
11) In the "Printers" window doubleclick on your new ML-1750 printer icon.
12) Go "Printer" -> "Properties" 
13) Select "Driver" and choose:
14) Manufacturer: Samsung -> Model: ML-1710 -> Driver: GDI
Then hit "Print Test Page" if it succeeds, you're all set.

This seem to be the only solution so far, and directly selecting Model: ML-1710 from the start didn't work. 

GBU

---

