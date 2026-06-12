---
title: "Lexmark network printer won't print"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by tallpaul66 on 2008-09-05
I have a USRobotics wireless router with built in print server. My printer is a Lexmark C500n laser printer. The connection from router to printer is USB. Windows applications print to it with no problem but Ubuntu will not. I have followed the instructions for the router and for installing a printer in Ubuntu. When I click on the Print Test Page button I get a popup saying that the test page was submitted and the button changes to say Cancel Tests. Printer State says processing but nothing happens after that. I have waited several hours and no printing occurs and the Printer State always says processing. I went to the Lexmark website and could not find any linux drivers for it. Ubuntu lists the C500 so I selected that, and when that did not work I tried the generic drivers with the same results. Any help would be great!
Paul in Pa

---

### Post by wolfen69 on 2008-09-05
did you install the proper PPD file? [http://openprinting.org/show_printer.cgi?recnum=Lexmark-C500n](http://openprinting.org/show_printer.cgi?recnum=Lexmark-C500n)

---

### Post by alienexplorers on 2008-09-05
Lexmark printer mainly do not run under Linux.  Lexmark or no one else makes drivers for them.  You may not have any luck runing it from Ubuntu.

---

### Post by tallpaul66 on 2008-09-05
Thanks for the reply. I guess it is not looking good for the home team. I also have a Lexmark X3300 all in one hooked up but that one is not in any list anywhere.  I can't even find XP drivers for that on the Lexmark site anymore.

---

### Post by Sef on 2008-09-05
> Thanks for the reply. I guess it is not looking good for the home team. I also have a Lexmark X3300 all in one hooked up but that one is not in any list anywhere. I can't even find XP drivers for that on the Lexmark site anymore.

First did you install [smbfs]("https://help.ubuntu.com/community/SettingUpSamba") in Ubuntu.

Second, did you set XP to printer to share? Right click on the print icon.

Third, the XP drivers for your printer are [here]("http://downloads.lexmark.com/perl/downloads/downloads.cgi").  Lexmark won't let you go directly to the site, but the drivers for your printer are there.

---

### Post by tallpaul66 on 2008-09-05
> **Sef said:**
> First did you install [smbfs]("https://help.ubuntu.com/community/SettingUpSamba") in Ubuntu.

Second, did you set XP to printer to share? Right click on the print icon.

Third, the XP drivers for your printer are [here]("http://downloads.lexmark.com/perl/downloads/downloads.cgi").  Lexmark won't let you go directly to the site, but the drivers for your printer are there.

I just now installed smbfs and it did not help. I do not understand what you mean by setting XP printer to share. The printer is hooked to the router which has a built in print server so I don't think XP is even a factor here. I did find linux drivers on the Lexmark web site but I have no clue which one I should get. I downloaded a couple of them and extracted them but they are meaningless to me. There are no instructions included that I could find.

---

### Post by NullHead on 2008-09-05
I can't remember, but I tried a similar setup with my lexmark and it won't work on my dlink dwa-665 router. I had to connect it to a computer and share it before I could print over the network.

---

### Post by Mr.Pickels on 2008-09-05
This sounds exactly like the problem I was having with my network attached Konica Printer.  This morning there were 6 updates to SAMBA through the update manager.  I deleted the printer (that didn't work) rebooted, and made a new printer with a PPD (no real drivers for my printer) and it worked like a 'Hot-Damn'.  Better and faster then windows ever did *grin*

there is a tiny bit of info in my old thread
[http://ubuntuforums.org/showthread.php?t=909863]("http://ubuntuforums.org/showthread.php?t=909863")

---

### Post by tallpaul66 on 2008-09-05
I went through all of the installation steps again and it still did not work. I tried getting the 3300 series printer which is hooked to the computer with USB and nothing there either. On a lark I disconnected the USB cable from the router and plugged it into the computer and Ubuntu found it immediately but complained about not having the right drivers. When I try to print a test page it says: "CUPS server error There was an error during the CUPS operation: 'client-error-document-format-not-supported' " Is this something that can be fixed?

---

### Post by tallpaul66 on 2008-09-05
Okay, I sort of fixed it. I changed the drivers for the laser printer from the generic to the lexmark, clicked on print test page and the printer spit one out. It did not print in color like it was supposed to. I tried printing an email from Thunderbird and it put out one blank page and one with about an inch of text on it. I tried printing an office (word) document and out came a blank piece of paper. I could be wrong but I am guessing that the imperfect print problems are due to incorrect drivers, but that would not explain why Ubuntu will not print through the print server, or does it?

---

