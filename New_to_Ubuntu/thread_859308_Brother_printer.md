---
title: "Brother printer"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by amin1990 on 2008-07-14
I am having problem printing the brother mfc-3240c on ubuntu.  I couldnt print it, because of CUPS problem.  What should i do?

---

### Post by plucky on 2008-07-14
> **amin1990 said:**
> I am having problem printing the brother mfc-3240c on ubuntu.  I couldnt print it, because of CUPS problem.  What should i do?

You need to install the printer drivers:-

From **System > Administration > Synaptic Package Manager** Search for **Brother mfc-3240c** and install the drivers for your printer.You need to install both the cups and lpr drivers.

Once the drivers are installed open **System > Administration > Printing** and select new printer.Cups will then search for your printer and should install it.


Good Luck

:)

---

### Post by amin1990 on 2008-07-14
> **plucky said:**
> You need to install the printer drivers:-

From **System > Administration > Synaptic Package Manager** Search for **Brother mfc-3240c** and install the drivers for your printer.You need to install both the cups and lpr drivers.

Once the drivers are installed open **System > Administration > Printing** and select new printer.Cups will then search for your printer and should install it.


Good Luck

:)

Thanks for the direction and I followed it, but still doesnt work.  Cups didnt find my brother printer driver that i installed on ubuntu. Maybe restarting might help.

---

### Post by amin1990 on 2008-07-14
> **amin1990 said:**
> Thanks for the direction and I followed it, but still doesnt work.  Cups didnt find my brother printer driver that i installed on ubuntu. Maybe restarting might help.

Also, when i found the driver and tried to print it, but i got this error message  (CUPS operation: 'client-error-document-format-not-supported').  I dont what that suppose to mean.  Maybe do i have to download the document format support??

---

### Post by ramjet_1953 on 2008-07-14
This link may be of help to you:

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143)

Also is this printer a 3240c or a 3420c?

I can't find any listing for a 3240c.

Have you loaded the Brother print driver, available from the Brother website?

Regards,
Roger :cool:

---

### Post by plucky on 2008-07-15
amin1990,

In the Firefox address bar,put ```
http://localhost:631/admin/
``` and see what cups thinks about your printer.

Can you see your printer?
Can you change the document type?
Can you print a test page?
What does the error logs say?

Good Luck

---

### Post by amin1990 on 2008-07-17
> **ramjet_1953 said:**
> This link may be of help to you:

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143)

Also is this printer a 3240c or a 3420c?

I can't find any listing for a 3240c.

Have you loaded the Brother print driver, available from the Brother website?

Regards,
Roger :cool:

This printer is 3240c.  I tried to load the driver from the Brother website, but it didn't work either.  I tried your link and it doesnt work too.

---

### Post by amin1990 on 2008-07-17
> **plucky said:**
> amin1990,

In the Firefox address bar,put ```
http://localhost:631/admin/
``` and see what cups thinks about your printer.

Can you see your printer?
Can you change the document type?
Can you print a test page?
What does the error logs say?

Good Luck

I put the link you gave me and it doesnt work.  My printer is not listed in that website.  Maybe ubuntu dont support my printer model.

---

### Post by phidia on 2008-07-17
> **ramjet_1953 said:**
> This link may be of help to you:

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143)

Also is this printer a 3240c or a 3420c?

I can't find any listing for a 3240c.

Have you loaded the Brother print driver, available from the Brother website?

Regards,
Roger :cool:

The openprinting.org database doesn't show a 3240c either but the [3420c works perfectly]("http://openprinting.org/show_printer.cgi?recnum=Brother-MFC-3420C").

---

### Post by plucky on 2008-07-17
> **amin1990 said:**
> I put the link you gave me and it doesnt work.  My printer is not listed in that website.  Maybe ubuntu dont support my printer model.

That link I gave you is not a link to a website,but opens the CUPS interface on your computer.It is used to troubleshoot your printer problems.

Which drivers did you install from synaptic?

What does firefox do when you put that address into the address bar?

Is the printer connected by USB cable direct to your computer?

Open a terminal and post output of these two commands```
lsusb
lpstat -v
```

Good Luck

---

### Post by amin1990 on 2008-07-17
> **plucky said:**
> That link I gave you is not a link to a website,but opens the CUPS interface on your computer.It is used to troubleshoot your printer problems.

Which drivers did you install from synaptic?

What does firefox do when you put that address into the address bar?

Is the printer connected by USB cable direct to your computer?

Open a terminal and post output of these two commands```
lsusb
lpstat -v
```

Good Luck

the driver i install from synaptic package manager was brother-lpr-drivers-extra.  The printer is directly connected to my computer by USB. The firefox shows me the cups printer page, but it doesnt said 3240c in there. This shows up in my terminal.
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0733:0430 ViewQuest Technologies, Inc. Intel Pro Share WebCam
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 04f9:0173 Brother Industries, Ltd 
Bus 001 Device 005: ID 046d:c509 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 
device for MFC-3240C: usb://Brother/MFC-3240C
device for PDF: cups-pdf:/
It recognize my printer, but I couldnt print it.  I dont know why. I restart the CUPS and it didnt work.  I uninstall and reinstall CUPS and that didnt work too.  I dont know what to do.

---

### Post by plucky on 2008-07-18
> the driver i install from synaptic package manager was brother-lpr-drivers-extra.


You also need to install the **Brother-cups-wrapper-extra** from Synaptic,which is probably why it is not printing,because it is the actual printer driver.

I would delete the printer you have installed,install the cups wrapper and then add the printer in again.

What happened when you put ```
http://localhost:631/admin/
``` into the Firefox address bar? Did cups page open?

Good Luck

---

### Post by hansdown on 2008-07-18
> **amin1990 said:**
> I am having problem printing the brother mfc-3240c on ubuntu.  I couldnt print it, because of CUPS problem.  What should i do?

I hate to be the one to give youthis news, but the brother web site says this printer is compatable with mac and ms.[http://www.brother.ca/en/products/description.asp?Prodid=7780173493338101142&features=on](http://www.brother.ca/en/products/description.asp?Prodid=7780173493338101142&features=on) Most hp printers are compatable. You will probably need to instal hplip and python-qt3 from systems> preferences> synaptic package manager.

---

### Post by amin1990 on 2008-07-18
> **plucky said:**
> You also need to install the **Brother-cups-wrapper-extra** from Synaptic,which is probably why it is not printing,because it is the actual printer driver.

I would delete the printer you have installed,install the cups wrapper and then add the printer in again.

What happened when you put ```
http://localhost:631/admin/
``` into the Firefox address bar? Did cups page open?

Good Luck

Thanks dude.  I installed the brother cups wrapper extra and it works!!!!! Wow, i really learn something.  Thank you for helping me with this problem.

---

