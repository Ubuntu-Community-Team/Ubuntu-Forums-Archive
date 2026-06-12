---
title: "Brother printer install"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Gosling on 2008-07-15
Help. A total ubuntu nooby here. Lots of Windows experience, but absolutely none with Ubuntu. 

I need specific (do this, then do that)instructions how to install drivers for a Brother MFC-240C printer.

Where to get the drivers
Where to put them
How to access them when installing printer.

Anything else that will make this job easier.

At the same time, can anyone recommend a book dealing with Ubuntu?

Many thanks for any assistance.

Mike Robinson

---

### Post by bigken on 2008-07-15
Take a look here [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html) for your drivers 
then search the forum for brother MFC you will find loads of answers

---

### Post by plucky on 2008-07-15
If you are running Ubuntu Hardy 8.04,the Brother printer drivers are in the Ubuntu repositories.Open synaptic package manager **System > Administration > Synaptic Package Manager** and search for **Brother MFC-240C** Select both the LPR and CUP wrapper drivers and **Apply** This will install the drivers.

Then open the Printer installer **System > Administration > Printing** and select "New Printer" and it should find and install your printer.

Good Luck

---

### Post by Gosling on 2008-07-15
Thanks Plucky: Did what you suggested and now have functioning printer. Really, really couldn't have done it without your input.

Cheers,

MikeR (Gosling)


> **plucky said:**
> If you are running Ubuntu Hardy 8.04,the Brother printer drivers are in the Ubuntu repositories.Open synaptic package manager **System > Administration > Synaptic Package Manager** and search for **Brother MFC-240C** Select both the LPR and CUP wrapper drivers and **Apply** This will install the drivers.

Then open the Printer installer **System > Administration > Printing** and select "New Printer" and it should find and install your printer.

Good Luck

---

### Post by aouie on 2008-07-17
I haven't tried the scanner on Ubuntu 8.04 as yet, but printing via USB on MFC-420CN was quite easy.
Installed brother-cups-wrapper-extra from synaptic. Then in printing I had to change the Make and model for the printer by selecting the ppd file at [ /usr/share/ppd/YourPrinterName.ppd ]. Print a test page.
Sincerely,
Aouie

---

### Post by Eric_Denison on 2008-07-21
Thanks Plucky, also a new user and your directions on the printer install cleared up a lot of confusion.  Printing up a storm and feel chuffed enough to tackle the scanner.

---

### Post by Gosling on 2008-07-31
> **plucky said:**
> If you are running Ubuntu Hardy 8.04,the Brother printer drivers are in the Ubuntu repositories.Open synaptic package manager **System > Administration > Synaptic Package Manager** and search for **Brother MFC-240C** Select both the LPR and CUP wrapper drivers and **Apply** This will install the drivers.

Then open the Printer installer **System > Administration > Printing** and select "New Printer" and it should find and install your printer.

Good Luck

Now that we've got the printer functioning, how about the scanner? Any ideas?

TIA

Cheers,

MikeR

---

### Post by bigken on 2008-07-31
you can download the scanner driver from the brother web site

---

### Post by Gosling on 2008-08-03
Have installed the drivers and xsane recognizes the scanner. It will scan a document but when the scan is completed I receive the following message:

"Error during CMS conversion
Could not open scanner ICM profile"

I'm obviously getting closer, but not close enough.

Any assistance greatly appreciated.

Cheers,

MikeR

---

### Post by Elfy on 2008-08-03
Have you seen this site, it might help - linked from a buntu thread 

[http://ubuntuforums.org/showthread.php?t=675684&page=2](http://ubuntuforums.org/showthread.php?t=675684&page=2)

[http://www.iclbiz.com/brothermfc/](http://www.iclbiz.com/brothermfc/)

---

