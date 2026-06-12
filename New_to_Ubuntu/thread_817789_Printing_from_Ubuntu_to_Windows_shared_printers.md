---
title: "Printing from Ubuntu to Windows shared printers"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by thinking2loud on 2008-06-03
Having problems getting Windows networking configured.  Sorry, have to use it to support other hardware like the wife's work laptop.  I had a configuration such that I could print from WinXP to the computer with the printer, so I know that I had the Windows part of the Windows networking close to being OK.  I can't see, find the Windows workgroup, or do anything related to Windows from Ubuntu.  Any assistance appreciated.

---

### Post by Sef on 2008-06-03
Do you have Samba installed?  

If not, then Applications > Add/Remove > show: change to All Available Applications > Search: Samba > Click on Samba > Click Apply Changes > Apply > Close.

---

### Post by thinking2loud on 2008-06-04
Yeah, got that.  I strongly suspect my problem is that I have samba configured wrong.  I can use networking (using it now).  I can ping the WinXP box.

---

### Post by cariboo on 2008-06-04
Cups makes it pretty easy to setup a printer on a remote windows computer. Just click System-->Adminstration--Printing. When the windows opens click the New Printer button, In the Select Connection window click on Windows Printer via Samba, click the Browse button. A window should pop up with Workgroup in it, click the arrow beside Workgroup and it should expand to show your connected printers. highlight your printer and click OK. Next click the Forward button. This will bring you to the Printer Driver window. Select your printer from the list. The program will give you a couple of driver choices, pick the default, click forward. In the New Printer window add the information it asks for and click apply and your done.

This assumes you have a printer that is supported and you have set up printer sharing on your windows computer.

Jim

---

### Post by thinking2loud on 2008-06-04
Jim:

     I got something set up wrong with samba and I know it but I have no idea what it is.  I get to the point where it shows the workgroup that I have assigned, but when I click on the triangle nothing shows up.  There might be something else done wrong on the WinXP end, but I had this working from Windows to Windows before.  I can just type in the share name of the printer, but this doesn't do me a lot of good because the print jobs go in and never complete.

-B

---

### Post by thinking2loud on 2008-06-05
OK, now I have a Windows XP machine here too (besides the one with the printer).  It can print to the printer, and I can see folder shares on it.  But from Ubuntu, when I try to see the folders (using Places->Connect to Server...->Service type=Windows share, I get:

Can't display location "smb://[server_name]/"  No application is registered as handling this file.

---

### Post by thinking2loud on 2008-06-07
Got it.  Started by plowing through various man pages.  Tried to use nmblookup.  Got 'ERRNO=Operation not permitted'.  That's the critical clue.  The problem was a firewall was blocking the SMB traffic.

P.S. Ubuntu is cool.  Ubuntu is so cool.  Even the printer test page is cool!

---

