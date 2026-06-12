---
title: "Printer Issues"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by TOMM_1230 on 2008-11-05
My printer does not print in Kubuntu 8.04 Hardy KDE3 64-bit.  It shows up, and the printer manager shows the document as processing but never spits it out. :confused: I am using a Lexmark 3400 series USB printer. it shows up as a _3400_series and under details even says it is a Lexmark 3400. :confused: I am I missing a driver or something? Pardon the Windows lingo, I do not know the Linux equivalent yet.

---

### Post by platinumits on 2008-11-05
First at all, let's to check the printer, can you print a test or demo page? alone the printer, it means all printers has a process to print a test page.

Then try to print a test page from the printer manager, when you select your printer at settings tab there is a bottom <print test page> if you receive an error message please let me know.

---

### Post by TOMM_1230 on 2008-11-05
> **platinumits said:**
> First at all, let's to check the printer, can you print a test or demo page? alone the printer, it means all printers has a process to print a test page.

Then try to print a test page from the printer manager, when you select your printer at settings tab there is a bottom <print test page> if you receive an error message please let me know.

It works fine on its own and in windows.

And I do not get any errors in Linux it just ?hangs?
I hit the test page button in the linux print manager, or send a document from OO.o writer. the task says ".processing" It never prints just sits there. Sooooo frusterating.  :mad:

I wish it would give an error. Then I could look up the fix.

---

### Post by platinumits on 2008-11-05
Ok, let's to do this.

Go to Printer Manager and select the printer
At the middle of the page say: Make and Model, click the bottom Change
Select the lexmark at the list and click Forward bottom
Select 3000 or 3200 models and test with them.

Good look

---

### Post by arochester on 2008-11-05
Have a look at [http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-3400](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-3400)

It says the printer works perfectly and recommends a driver: epsonc

---

### Post by sqrooup on 2008-11-05
If all the drivers are present try the following (it worked for me on a Lexmark Z605):

Applications>Accessories>Terminal

Type in; sudo /etc/init.d/cups restart
You will be prompted for a password (Some instructions tell you to use "/etc/init.d/cupsys", but this is for earlier versions of Ubuntu and Linux, the filename was changed to "cups" for Ibex)

Let me know if this works

---

### Post by TOMM_1230 on 2008-11-05
> **sqrooup said:**
> If all the drivers are present try the following (it worked for me on a Lexmark Z605):

Applications>Accessories>Terminal

Type in; sudo /etc/init.d/cups restart
You will be prompted for a password (Some instructions tell you to use "/etc/init.d/cupsys", but this is for earlier versions of Ubuntu and Linux, the filename was changed to "cups" for Ibex)

Let me know if this works

I am using 8.04 Hardy so which command do I use?

---

### Post by sqrooup on 2008-11-06
Try both;

sudo /etc/init.d/cups restart
or 
sudo /etc/init.d/cupsys restart

If one gives an error try the other

---

### Post by TOMM_1230 on 2008-11-10
reply this is the dot matrix printer.  I guess mine is the X3400 or something like that. It is an All-in-One laser printer.

---

