---
title: "[SOLVED] Can print test page but nothing else"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by RichardParkr on 2008-08-22
I'm a brand new linux user, having just installed xubuntu for the 1st time last week.

Xubuntu automatically recognized my hp psc 1210 printer, and I was able to print w/o problems for a few days.  However, I refilled my black ink cartridge yesterday and since then have not been able to print.  Xubuntu gives me the "low on ink" message and if I try to print the printer takes the page through without printing anything.

Strangely though (to me), I can go to Applications > Printing and print a test page perfectly.  I'm stumped trying to isolate the problem :confused: Thanks for any input.

---

### Post by st33med on 2008-08-22
Have you tried replacing the color ink as well?

---

### Post by RichardParkr on 2008-08-22
My color ink cartridge is out of ink so I was previously printing with Printout Mode changed to "Normal grayscale (Black cartridge)."  When I print a test page now, it prints in grayscale.

---

### Post by bumanie on 2008-08-22
This may not sort out the problem, but you could try and reinstall hplip via synaptic and see if that helps. You could also go to add/remove and install the hp tool box which will give you a familiar gui as per the one used under windows. You can also go to hp linux site and and download and get the self-extracting installer to reinstall the printer.

---

### Post by RichardParkr on 2008-08-22
Following Bumanie's advice, I installed hplip from the hp website.  Their instructions for working in the terminal were straightforward.

After that, I was able to print a webpage through firefox.  But I cannot print a pdf, opened with evince the default xubuntu pdf reader.  So maybe this is a problem w printing pdfs specifically?

---

### Post by RichardParkr on 2008-08-22
I used to add/remove to install xpdf and was able to print my docs w/o any problem.  I think there must have been some problem w printing from evince.

---

### Post by alienexplorers on 2008-08-22
I could not print from Evince so I added Adobe Reader form the medibuntu repositories.  I think it is listed as Acroread or something like that.  Now I have no problems printing .pdf files.

In the terminal type in:
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

### Post by linuksamiko on 2008-08-26
I also just installed acroread but this not a solve for the problem it is just a work around. I still don't know why evince is not printing. Everything worked so fine until two or three weeks ago, what happened and how can I make evince print again?

---

### Post by lunatico on 2008-08-27
Might these issues be related. [This]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5674482#post5674482") and [this]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=852007&highlight=firefox+print"). It looks familiar to me... anyone any luck?

---

