---
title: "Access Windows Shared Documents and Printers"
date: 2009-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by GTdenver on 2009-05-11
Besides making sure Samba is enabled and is running, I used the following method to setup my Windows shared Printers and Documents in Ubuntu 9.04 on a home network with a wireless router.

You'll need your Windows computer IP address and Shared Printer and Document Names.
[U][B]

TO GET WINDOWS[/B]** IP:**[/U]
START>RUN>CMD
Then type -  IPCONFIG /ALL

This will give you your Windows Computer IP address like 192.168.1.2
[U][B]
TO GET SHARED NAMES:[/B][/U]
START>RUN>CMD
Then type - NET SHARE

This will tell you the names of all your shared Printers and Folders.
Please note that names may be case-sensitive so capitalize only when needed.
[U][B]
SETTING UP UBUNTU TO ACCESS WINDOWS SHARED DOCUMENTS:[/B][/U]
In Ubuntu...
Click Places> Connect to Server
Change Service Type to "WINDOWS SHARE"
In SERVER type the Windows IP like 192.168.1.2
In FOLDER type SHAREDDOCS to access all shared folders.
[U][B]
SETTING UP UBUNTU TO ACCESS A WINDOWS SHARED PRINTER:[/B][/U]
In Ubuntu...
Click SYSTEM>ADMINISTRATION>PRINTING.
Click NEW>NETWORK>WINDOWS PRINTER VIA SAMBA.
Type Windows IP/Shared PrinterName in the SMB:// Box
Like 192.168.1.2/SamsungC


Well I think that's it. I'm just a newbie so I can't offer too much more tech support in this area. Let me know if I need to clarify.

---

### Post by jpeddicord on 2009-05-12
Thank you for your tutorials & tips contribution, approved! :)

---

### Post by Warren Watts on 2009-05-18
Great Tip!  

I had access to a windows share on my home network set up and working in less than a minute.

Thanks!

---

