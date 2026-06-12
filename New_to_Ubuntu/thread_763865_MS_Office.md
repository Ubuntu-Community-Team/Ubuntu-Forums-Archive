---
title: "MS Office"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by tngrl on 2008-04-23
I ugpraded my Linux to 7.10 and now I am unable to use my MS Office nor will it allow me to print my worksheets (spreadsheets) from my printer. The printer recognizes but will not print horizontally. Also, I believe I can only open the MS Office via Wine. I do not know what else to do. Please help.

---

### Post by Het Irv on 2008-04-23
Were you running MS Office under something other than WINE?
What printer do you have?

---

### Post by Oldsoldier2003 on 2008-04-23
> **tngrl said:**
> I ugpraded my Linux to 7.10 and now I am unable to use my MS Office nor will it allow me to print my worksheets (spreadsheets) from my printer. The printer recognizes but will not print horizontally. Also, I believe I can only open the MS Office via Wine. I do not know what else to do. Please help.

Try running Office from within a virtual windows session such as from with VirtualBox. Of course this depends on you having a valid windows cd to install windows in the VM but its probably the best solution for running MS Office on your linux machine. Some versions of Office don't cooperate with wine very well, for more information on that you can look at the app db at winehq.org

---

### Post by Toadinator on 2008-04-23
One thing you could do is tell me your Printer and if you have the right driver installed.

The next step would be to either use the *built in* OpenOffice.org which is an amazing, almost fully-featured office suite that can accept MS Office documents with very little errors and works naturally under Ubuntu, or download WINE from Add/Remove programs by selecting the "All Available Programs" option from the menu at the top and typing in 'wine' in the search box.

I hope that I've helped!

---

### Post by tngrl on 2008-04-23
I have Wine already installed and everything seems to be ok except for printing my spreadsheet from my printer which is an HP LJ 4M.

---

### Post by stchman on 2008-04-23
> **tngrl said:**
> I ugpraded my Linux to 7.10 and now I am unable to use my MS Office nor will it allow me to print my worksheets (spreadsheets) from my printer. The printer recognizes but will not print horizontally. Also, I believe I can only open the MS Office via Wine. I do not know what else to do. Please help.

Openoffice does support Excel .xls spreadsheets and very well.

I find that for my office tasks I don't miss M$ Office at all.

---

### Post by SunnyRabbiera on 2008-04-23
well please keep in mind that sometimes upgrading the system can possibly effect wine, what worked before might not work now unless you tweak around.
Remember that WINE is an experimental piece of software, it does its job but sometimes it messes things up.
If you keep on having issues you may wish to invest in crossover office, its a non free program but it sometimes works better then normal wine (at this point and time)

---

### Post by Oldsoldier2003 on 2008-04-23
> **SunnyRabbiera said:**
> well please keep in mind that sometimes upgrading the system can possibly effect wine, what worked before might not work now unless you tweak around.
Remember that WINE is an experimental piece of software, it does its job but sometimes it messes things up.
If you keep on having issues you may wish to invest in crossover office, its a non free program but it sometimes works better then normal wine (at this point and time)

+1 Throughout the development cycle of Hardy WIne has broken and fixed itself several times. Actually I'm almost certain Hardy broke and fixed wine several times since I didn't notice wine updates and I stayed with the repo version.

another +1 for crossover, since unlike Cedega, crossover contributes back to wine and the devs actually respond.

---

### Post by analoog on 2008-04-23
Did you already try OpenOffice?

---

### Post by StefAndrew on 2008-04-23
If you were using WINE installed on an earlier version of Ubuntu and upgraded to 7.10, this could very well have "broken" WINE.  Upgrading has been known to cause these kind of issues because of the newer libraries used in the upgrade.  Something you might try to do if you still have your Office install CD(s) is to try to remove Office and then reinstall it.  That would be my first step especially after upgrading.  I would also try to update WINE as well, maybe even before reinstalling Office.

---

