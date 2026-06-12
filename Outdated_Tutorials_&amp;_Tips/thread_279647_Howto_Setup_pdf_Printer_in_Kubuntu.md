---
title: "Howto Setup pdf Printer in Kubuntu"
date: 2006-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by hogman23 on 2006-10-18
There are a lot of threads about setting up the pdf printer in Ubuntu, but none about setting it up in KDE, so here you go:

sudo apt-get install cups-pdf

sudo chmod +s /usr/lib/cups/backend/cups-pdf

Go to System Settings:
Under Hardware, click on Printers
Click Add
Click Add Printer/Class
Click Next
Other Printer Type
Scroll down and select: Virtual Printer [PDF Printer]
Click Next
Select: Raw Printer (no driver needed)
Click Next
Click Next again on Printer Test
Click Next again on Banner Selection
Click Next on Printer Quota Settings
Click Next on User Access Settings
On General Information type pdfPrinter under Name
Click Next
And finally Finish

Now you can print to you pdfPrinter and the pdf's will go to home/PDF by default.

---

### Post by Charles Hand on 2007-01-16
My PDF printer quit working. It looks like it's printing, but nothing comes out in ~/PDF. I have thre different PDF printers, including the one described in this thread. None of them create any output, but none of them complain.

BTW, is there any way to make output go someplace other than ~/PDF?

-Charlie

---

### Post by Charles Hand on 2007-01-18
I have ripped out the entire cupsys (except I didn't let synaptic remove kubuntu-desktop and ubuntu-desktop like it wanted to - thought that would be removing too much), and re-installed it. Then reinstalled cups-pdf as in this thread. Still nothing happens. No error message, no output. 
Any help?

---

### Post by oenggun on 2007-04-27
thanks .. this tutorial works for me on Kubuntu 7.04.

---

### Post by therandman on 2007-05-06
> **oenggun said:**
> thanks .. this tutorial works for me on Kubuntu 7.04.

Me 2, 2 thumbs up, works perfectly on Feisty! :D

---

### Post by sehe on 2007-05-24
Thanks here 2. Also tried and works on Kubuntu Feisty

On a separate note: it seemed that the default installation created something of a printer target 'Print to file (PDF)' out-of-the box (I sure as hell didn create it :)) but it did not work... Strange

---

### Post by kevdog on 2007-05-24
As far as changing the default location of the printouts, you need to configure as root the /etc/cups/cups-pdf.conf file.  There should be a section labeled ${HOME}/PDF as the default output location.

I did sucessfully set up a default PDF printer through the use of various tutorials I have found, however later found it easier to use kprinter especially if you have KDE installed.  Typing kprinter --help at the command line will give you the options.  This command can basically substitute for lp or lpr.

---

### Post by nadrach on 2007-12-29
The instructions work for Kubuntu 7.10, except that any print job created sits in the printer queue  as "Held" and will not go to any file destination, even if you try to force the print job to complete. HOWEVER ... if you set the "Print to file" flag at the time of choosing the PDF printer, you can decide wherever you wish to put the resulting PDF file on an individual basis, including any directory. This works for me.

---

### Post by shaulreznik on 2008-01-04
For me the follow commands worked:

sudo apt-get install cups-pdf

System settings > Printers > Add > Add Printer/Class > Other printer type > Print into PDF file [Generic PDF file generator] > Check "PostScript Printer"

---

### Post by nadrach on 2008-02-01
Thank you. It was setting the printer type to "Raw Printer" in the original instructions that caused a problem. Also, the output when I set to "print to file" was only usable in Ghostview, but not in any PDF reader. Changing to "Postscript Printer" type fixed the situation, and the resulting files turn up in $home/PDF. They open in any PDF reader.

---

### Post by dcottingham on 2009-02-24
With Kubuntu 8.10, had to "mkdir $HOME/PDF" myself before anything would work.

This is probably a bug -- I don't think I had to do this with any earlier version.

To be clear, the only two steps I needed to do were install cups-pdf (I used synaptic FWIW), and then "mkdir $HOME/PDF".

---

