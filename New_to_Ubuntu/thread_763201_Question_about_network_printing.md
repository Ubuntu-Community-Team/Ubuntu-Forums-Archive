---
title: "Question about network printing"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by ngutman on 2008-04-22
I am a complete novice on this. I have a WinXP computer A connected with an Ethernet cable to dual boot Ubuntu/WinXP computer B.
How can I make a printer attached to computer A available to computer B when computer B is running Ubuntu?
Thanks for any help,
Nathan

---

### Post by Diabolis on 2008-04-22
computer A
1.- right click on the printer and make it a shared printer.
2.- go to control panel->connections, right click on the first icon and configure a new network. The wizard will guide you, is quite simple. In my case the only thing I had to configure was the name of the network.

computer B
System / administration / Printing (the second one). click the icon to add a new printer. Then follow the wizard, the first options you have to pick are network printer and windows(smb).

---

### Post by stevek123 on 2008-04-22
I am also a noob at this but I just got mine to work this morning:). In the Ubuntu unit, in Admin -> Printing my description has the name of my printer [mine is PSC_1600], The location line is blank. The device url says smb://home/(network name)/Printer. When I tap 'change' for the device (on the right), it gives me some options and a button to 'verify' the printer. This tells you if you got it right. Took me several tries. Something I had missed is another button in Admin -> Shared Folders. It was necessary to open the General Properties tab on top and tap the "This computer is a WINS server" box". I think this turns on formatting to the windows printer in Comp.A. I had file sharing OK but it wouldnt print anything until I did this last Shared Folders thing..... I hope this helps.

---

