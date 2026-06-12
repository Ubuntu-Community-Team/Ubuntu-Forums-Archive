---
title: "Acrobat Reader Printer Selection"
date: 2007-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by jimcooncat on 2007-01-18
Using Acrobat Reader 7.0, I had the annoyance that it would only print to my printer, and I couldn't send it to another printer in the office -- though I had it set up on my Ubuntu box.

When I hit the print button, a dialog pops up that says, Printer Command: /usr/bin/lp

I changed that command to /usr/bin/gtklp

Now I have all kinds of options to handle the print job. Though the most important to me is to be able to choose which printer to print to.

If this doesn't work, check to see if you have gtklp installed.

---------- Subforum checklist for this tip --------------
1) Credit to the base of your info unless you wrote the guide from scratch.
From scratch, trial and error.

2) The version of Ubuntu you tested it on this including architecture (eg. 32/64bit).
Breezy Badger, 32 bit

3) A detailed explanation of what the guide/script/etc does.
Sends acroread print jobs to a GUI print job selector.

4) A complete list of what is needed to install the program/script/etc in your guide.
sudo apt-get install gtklp

5) A way of uninstalling or undoing any changes made
Change Acroread's print command back to /usr/bin/lp

6) All commands posted in the thread should be on separate lines and please use the CODE tags so they are easier to read.
n/a

7) You must be willing to support the guide you post *OR* post a warning that there is no support, and the guide is to be used at your own risk.
No support, feedback appreciated though.

---

### Post by timcredible on 2007-02-14
fantastic!  thanks for the tip.

---

### Post by jimcooncat on 2007-02-15
I see that in the Acrobat Reader that I installed on my Dapper machine that the print dialog has full functionality, and lets me select the printer from there. So I guess this tip is outdated.

---

### Post by firekat on 2007-04-16
feisty amd 64 installation of acrobat reader just shows "Custom" printer in the dialog.  Cannot select anything else.  Installing the gtklp did allow me to select a printer.  Not as straight forward as just selecting a printer but it allows me to print.

Thanks

It still would be nice if it would work normally.

---

