---
title: "PDF stopped working, reinstall fails"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by lile001 on 2013-08-22
I noticed that in trying to use PDF printing from an application, I got an error message "Unable to get list of paper sizes from Printer".  No PDFs for you, sucker!  This had been working smoothly as recently as yesterday.  Ubuntu wanted to do some kind of major software upgrade this morning which may have caused the change.  

I go to the CUPs server on [http://localhost:631/admin](http://localhost:631/admin) and find out that the PDF printer is stopped and there are jobs stuck in it.  (All the stuff I had attempted to print earlier). I cancel the jobs but still cannot print anything, not even a test page.  I delete that printer and reinstall cups-pdf from a terminal using sudo apt-get install cups-pdf.  

I do find the PDF printer now when I go to system settings>Printers.  However, a test page does not produce any output.  Applications still can't print.  

I found an old HOWTO [here]("http://ubuntuforums.org/showthread.php?t=188860") but the instructions were not relevant to the version I am running now (12.04 with Unity removed)  and following them as well as I could didn't change anything.  I can see the PDF printer but it doesn't print anything.  

I can't see the PDF printer at all at the cups server [http://localhost:631/admin](http://localhost:631/admin)  but I can see it from system settings>Printers.  

What is going on, and how can I get PDF printing working again?

---

### Post by lile001 on 2013-08-22
I believe I was able to blunder through this.  It looks like there were permission problems with the file /usr/lib/cups/backend/cups-pdf.  And I had compounded this by trying to set these permissions using the old HOWTO referenced above, which seems to steer one wrong.  BLundering around in SUDO NAUTILUS and a terminal, I finally set the permissions of cups-pdf to OWNER: ROOT READ ONLY and GROUP: ROOT READ ONLY.  I also made an attempt at restarting the CUPS printing service, which did not seem to work (generating error messages) but that may have had something to do with the output.  I haven't the foggiest idea what I am doing so mostly I am just trying random things found on some random web page, that never seem to be written for the system I am using.  Anyway I believe this made PDFs start printing, if that is worth anything for others who run into this problem.

---

