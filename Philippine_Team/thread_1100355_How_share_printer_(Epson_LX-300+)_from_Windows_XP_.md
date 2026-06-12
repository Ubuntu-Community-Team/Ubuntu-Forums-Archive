---
title: "How share printer (Epson LX-300+) from Windows XP to Ubuntu 8.10?"
date: 2009-03-19
forum: Philippine Team
---

### Post by SHENGTON on 2009-03-19
Hello, good evening. :)

I have two desktop computers here with one printer. The Operating System of PC1 is Windows XP Professional and PC2 is Ubuntu 8.10. My printer model is Epson LX-300+.

The printer is connected in PC1 and I want to share it with PC2. I don't know if what I should do first then the next. Obviously I newbie in Linux world. I want to study more about Linux.

Can anyone help me how to share printer from Windows XP to Ubuntu 8.10?

Thanks and God bless. :)

---

### Post by loell on 2009-03-19
this should still work

> 

The Windows XP Machine (The Print Server)

   1. Install your printer.
   2. Open your Control Panel, then open your "Add or Remove Programs"
   3. Click on "Add/Remove Windows Components" located on the left side of the dialog box
   4. Put a check on "Other Netwrok File and Print Services" then click "Details" make sure that the "Print Services for Unix" is selected. (you may need your XP CD and a reboot)
   5. Open "Printer and Faxes" then right click on your printer then "Share", give your printer a share name that is short and with no special characters or spaces (ex. "HP940c" quotations not inclucded). This Share Name would later be used as the Print Queue on your Linux machine.
   6. The Windows Firewall may block Linux machines from printing, turn off your firewall for the meantime.. we will turn it back on later.
   7. Make sure that your Windows' IP number is Static.

The Ubuntu x.x Machine (Print Client)

   1. From the panel (default is on top) open System>Administration>Printing
   2. Click on "New Printer"
   3. Select "Network Printer" then use "Unix Printing LPD"
   4. Type on the "Host" Field the IP number of your Windows Print Server (ex. 192.168.0.101)
   5. Type on the "Queue" field the Share Name of the printer, in our example we used "HP940c" (quotations not included)
   6. Click "Forward" then select the manufacturer and model of your printer from the list. Then click "Apply".
   7. Your new printer will now appear in the dialog box. Print a test page to make sure that the paper settings and print out mode are in the right settings..



from a very old [howto ]("http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html") :)

---

### Post by SHENGTON on 2009-03-19
Hello Sir loell, good morning. :)

Yesterday I figured it out. I tried searching for thousand times and finally I found the answer.

I just finished my blog regarding my problem yesterday. Here's the link of my blog --> [HERE](http://blog.shengton.co.cc/2009/03/network-printing-ubuntu-client-windows-xp-printer-server/)

Thanks for the effort Sir loell and God bless. :)

---

### Post by badrra on 2009-03-23
thanks for letting us know. magagamit ko ito later on.

---

### Post by SHENGTON on 2009-03-24
Your welcome badrra. :)

---

