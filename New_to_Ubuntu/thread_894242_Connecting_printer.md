---
title: "Connecting printer"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by audreymac on 2008-08-19
system - printing - shows Lexmark as default printer.
Status: idle.


Problem is when I try to print, the print icon shows up for about 30 seconds on the toolbar and then disappears....

---

### Post by tarps87 on 2008-08-19
How is the printer connected?

---

### Post by audreymac on 2008-08-19
Connected to back of my tower- USB?
Where do I check for more info for you?

---

### Post by tarps87 on 2008-08-19
What Lexmark printer is it?
I'm assuming that Ubuntu recognises the printer but try
```

lpinfo -v

```

---

### Post by prshah on 2008-08-19
> **audreymac said:**
> 
Problem is when I try to print, the print icon shows up for about 30 seconds on the toolbar and then disappears..

Open a browser, and browse to ```
http://127.0.0.1:631
``` On the page that loads, click on [Manage Jobs] -> [Show All Jobs]. Are your jobs listed there? What is the status of the jobs? Maybe you should  cut'n'paste the results shown.

---

### Post by audreymac on 2008-08-19
Lexmark 1100.
Tried lpinfo in terminal - no such file or directory.

Previously I ran windowsxp but wiped it,in error, and have not connected back....

---

### Post by tarps87 on 2008-08-19
I'll check that it got the command right when i get back to my Ubuntu pc. Id Ubuntu automaticaly find the printer drivers.
also what happens when you try what prshah said:
> **prshah said:**
> 
Open a browser, and browse to
```

http://127.0.0.1:631
```
On the page that loads, click on [Manage Jobs] -> [Show All Jobs]. Are your jobs listed there? What is the status of the jobs? Maybe you should cut'n'paste the results shown.

---

### Post by audreymac on 2008-08-19
prshah - connected to http:etc and it said 
no jobs....

---

### Post by prshah on 2008-08-19
> **audreymac said:**
> prshah - connected to http:etc and it said 
no jobs....

I don;t think you've clicked on "Show all jobs"; can you post a screenshot?

---

### Post by audreymac on 2008-08-19
yes, clicked show all jobs - no jobs.
It says:
printer driver: lexmark1020 business foomatic//pcl3 (recommended)
printer state:idle, accepting jobs,published
Device url:usb:lexmark%20/x1100%series.
Sorry can't cut and paste.

---

### Post by audreymac on 2008-08-19
You are right - its showing 19 jobs - stated as all completed.
Err...how DO I post the screenshot?

---

### Post by prshah on 2008-08-19
> **audreymac said:**
> its showing 19 jobs - stated as all completed.
how DO I post the screenshot?

Don't need the screenshot now. In the first column of the jobs list, what is the printer+job ID? What does it give in the corresponding "State" column? Does the printer name match the same name as listed in the CUPS printer admin page (Home-Manage Printers)?

---

### Post by audreymac on 2008-08-19
State column - completed on and the date and the time and then IST. Control col. is blank.
I.D. column - lexmark x1100series2 and a number 1-19 (19 jobs listed total)

---

### Post by audreymac on 2008-08-19
printer home page lists 3 0f 3 printers:
PDF

x1100series  - print driver generic text-only printer.

x1100series2 default printer - print driver1020business footmatic/etc

---

### Post by prshah on 2008-08-19
OK, to rule out problems with the printing subsystem, print something to the PDF printer and check if it is printed correctly. The PDF file will be available in a directory called "PDF", which will be under your home directory.

If it successfully produces a proper PDF, attempt to print that PDF to your printer, does it work OK?

---

### Post by audreymac on 2008-08-19
saved to home directory -PDF file is blank (hidden files box not ticked...)

---

### Post by tarps87 on 2008-08-19
What are you printing from?

---

### Post by audreymac on 2008-08-19
Firefox browser - trying to save/print page on screen

---

### Post by tarps87 on 2008-08-19
Have you tried a test page? Also have you any addons?

---

### Post by prshah on 2008-08-19
> **audreymac said:**
> saved to home directory -PDF file is blank (hidden files box not ticked...)

Is the file blank or the directory blank? If the file is blank, what is the filename and create date/time?

---

### Post by audreymac on 2008-08-19
home - PDF- filebrowser various pdf files.
Tried to print one - as before printer logo appears bottom r.h. of screen for about 30 seconds then disappears....
Add-ons its a multimedia and includes a scanner and a fax facility.

---

### Post by audreymac on 2008-08-20
My Update today -
Printer logo bottom r.h. of screen says 2 documents queued but then a pop-up 'printer may not be connected etc'.
I ran some sudo commands in
the terminal re z600 driver.
Do you think the Lexmark 1100series2 is compatible at all?

---

### Post by Sef on 2008-08-20
Have you checked [Openprinting.org]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-1100")?  It has a way to make the Lexmark 1100 work partially.

---

