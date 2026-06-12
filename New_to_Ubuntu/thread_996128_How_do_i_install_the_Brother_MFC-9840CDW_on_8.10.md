---
title: "How do i install the Brother MFC-9840CDW on 8.10"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Cytomax on 2008-11-28
Hello all...
I have a Brother MFC-9840CDW hooked up with an ethernet cable to my router and i would like to install it on my new Ubuntu 8.10 laptop....

I went to this website and i followed the directions....
[http://www.pyrosoft.co.uk/blog/2008/07/28/installing-the-brother-mfc-9840cdw-on-ubuntu/](http://www.pyrosoft.co.uk/blog/2008/07/28/installing-the-brother-mfc-9840cdw-on-ubuntu/)
    * Open up Synaptic Package Manager.
    * Search for 9840 and install the packages.
    * Set it up under System > Printers.


The first 2 steps went great, Synaptic Package Manager found and installed the following 2 files  

brother-cups-wrapper-ac
brother-lpr-drivers-ac

Now i go to 
System--> Administration --> Printing --> New --> Brother MFC-9840CDW (and the ip address where it is located)

Then it searches for drivers and takes me to page that gives me 3 options...

Select Printer from Database
Provide PPD file
Search for a printer driver to download

How do i tell the computer that i already downloaded the stuff with Synaptic package manager?

So this is the step that i am stuck at can somebody please help me

THanks in Advance
Eddie

---

### Post by Cytomax on 2008-11-30
Just a friendly bump
Eddie

---

### Post by plucky on 2008-12-01
> Now i go to
System--> Administration --> Printing --> New --> Brother MFC-9840CDW (and the ip address where it is located)


Does it find the printer?

> Then it searches for drivers and takes me to page that gives me 3 options...

Select Printer from Database
Provide PPD file
Search for a printer driver to download



Use "Select Printer from Database" and the Select "Brother" and then scroll through and select your printer.This is what tells the system which driver to use.

Try a test print.


See this [link](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-9840CDW) for the Brother website.This has some good information.


Another good resource is to open CUPS interface from your Browser.Just input into address bar the following ```
http://localhost:631/admin/
```

Good Luck.

---

### Post by Cytomax on 2008-12-01
Thank you for the reply...
Yes the computer picks up the printer when i go to

System--> Administration --> Printing --> New 

It lists the Brother MFC-9840CDW as one of the printers... i just wanted to know how to tell the computer that i already downloaded the drivers for it through Synaptic Package Manager and to use those drivers....

Ill try out what you said when i go home
Thanks for the help
Eddie

---

