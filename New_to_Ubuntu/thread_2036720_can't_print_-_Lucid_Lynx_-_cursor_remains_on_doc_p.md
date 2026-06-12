---
title: "can't print - Lucid Lynx - cursor remains on doc pages - scanner not hooked to comput"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by desertoasis on 2012-08-02
I'm about the most absolute newbie to Linux you will ever see.

I had so much trouble with Windows, though I loved XP, that I went to the library, checked out a book about Lucid Lynx 10.04 and made a dual boot.  It's been wonderful, BUT a steep learning curve FOR ME.  Nobody else I suspect.  I do my own maintenance, and cannot really depend on anybody locally to help.  Just so you know. :popcorn:

Now then,  I had to go out and buy a new printer, since none of the older ones were compatible with drivers, etc.  I bought a HP4620 because HP supports linux drivers. It has worked fine except for two things, the oldest one being that though I followed the directions so far as I know that came (manual, etc.) with the all-in-one, the computer does not recognize the USB port connection.  Not sure if it's a linux problem or HP problem.  Have posted at HP, but nothing has come of it.

The second, later, but more serious problem, is this.  I was printing away and things were going well, when it stopped printing.  The jobs are in the queue, but they do not print.  Often they say processing.  In addition, and this might be a BIG clue, when I cut and paste a doc, I cannot get the cursor to go away.  If I save the doc or whatever, it does not print.  It may have an easy solution, but I don't know what it is.  I checked with some of the replies to similar problems, but they don't seem to help.

Right now it says not connect, but when I check it says "connected to localhost" - so I am mystified.  

Long post, but I thought it was better to try every thing.  I checked
system -> administration -> printing

It is all okay.  *I've checked and rechecked all physical connections.  All okay*

---

### Post by irv on 2012-08-02
Lets start by cleaning things up. 
First, go to your print Q and delete all the print jobs.
Next, go to your printer setup and remove your printer.
Next, reinstall your printer. If it is a network printer let setup find it, then install the driver from the list of printer drivers.
Do a test print. If it works, then try printer something from one of your apps.

EDIT: re-read your post and see it is a USB printer/scanner etc. Ubuntu should work with USB printers.
Also, after you get the printer working, install Xsane, and with the printer/scanner plugged in run this app and see if it fines your scanner. I have an old USB scanner and it works without installing any drivers. Xsane just finds it.

---

### Post by mapes12 on 2012-08-03
With a standard Ubu installation the HPLIP driver will be installed by default. That's why you have some printer functionality. However, the standard driver in your installation is out of date. If you go to the HPLIP website (Google it) you can download and install the most up to date driver. This should solve your problem.

There are 2 parts to the installation. The first is downloading the driver. It will probably go to your **Download** folder. Drag it to your Desktop then follow the Terminal commands given on the HPLIP website exactly as described and the driver will then unpack and install.

I maintain 3 Ubu machines connected to a variety of HP printers and all in ones. Once you get the updated driver installed you will be good to go.

As you can see with Ubu there can be a number of tweaks to get your system just how you want it. If your system ever crashes it can be a pain to go through all of this again. To save yourself some hassle I recommend you get familiar with Remastersys (Google it) and make yourself a custom installation .iso of your system. Then if anything goes wrong you can install your system back to exactly how you like it with one installation disk.

---

