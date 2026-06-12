---
title: "can't read pdf - &quot;later version of acrobat needed&quot;"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by lila on 2012-11-13
Hello,
All my updates are up to date, my computer tells me it doesn't need anything.  
But I need to download a form from a French government website (about registering a used car I bought). And the website tells me I need a later version of Adobe Acrobat.  This has never happened to me before, these things have always updated themselves...

Can you help?
Lila

---

### Post by ubudog on 2012-11-13
Ubuntu comes with a document viewer that should be able to read it.  Are you able to get the pdf itself from the website?

Best,
ubudog

---

### Post by Pilot6 on 2012-11-13
There is no Adobe Acrobat reader by default in Ubuntu, but you can install one. It is called acroread.

---

### Post by andrew.46 on 2012-11-13
I grew tired of Adobe's bloated acrobat reader and now simply open pdfs with the Firefox built in viewer:

Enable the builtin PDF viewer in Firefox
[http://docs.slackware.com/howtos:software:firefox_pdf_viewer](http://docs.slackware.com/howtos:software:firefox_pdf_viewer)

Perhaps this will also work with the problem page for you?

---

### Post by audiomick on 2012-11-13
> **lila said:**
> But I need to download a form from a French government website (about registering a used car I bought).

There are pdf's which include fields for putting in information. In my experience, these don't always work with the document reader in Ubuntu. I expect that the formula in question is one of these. Try acroread, as suggested. It is bloated, and it has a couple of other issues involving it's ability to communicate back to somewhere else, but it is the most likely thing to work for that instance. Just don't let it set itself to be the standard document reader and only use it for things like the task in question. I don't like using proprietary software, but sometimes you have to cut your losses... ;)

---

### Post by monkeybrain2012 on 2012-11-13
> **audiomick said:**
> There are pdf's which include fields for putting in information. In my experience, these don't always work with the document reader in Ubuntu. I expect that the formula in question is one of these. Try acroread, as suggested. It is bloated, and it has a couple of other issues involving it's ability to communicate back to somewhere else, but it is the most likely thing to work for that instance. Just don't let it set itself to be the standard document reader and only use it for things like the task in question. I don't like using proprietary software, but sometimes you have to cut your losses... ;)

Acroread is bloated and slow. For forms with Formulae I use pdf-xchange viewer which runs perfectly in wine, install cups-pdf then you can print it out (in /home/username/PDF) You need to print the file instead of saving it or it will show up blank in Adobe. It is a lot lighter than acroread.   [http://www.tracker-software.com/product/pdf-xchange-viewer](http://www.tracker-software.com/product/pdf-xchange-viewer)

I would rather not use WINE but unfortunately this is the only way I know for sure that works for forms with formulae (other than acroread, which is undesirable for many reasons: it is bloated, slow and not only proprietary but also Adobe and god knows when will Adobe drop its support for Linux given recent trend)

If there is no formula Okular would work and it works better than Document Viewer but again need to print out the form instead of saving it (same goes with editing because Okular saves the changes in a separate file rather than the document itself)

There is also something called cabaretstage which runs natively in Linux (no need to install, just unzip and go to the subfolder bin and click the .sh script (before that right click it, choose properties > Permission and check allow running file as a program) I have not tried it on forms with formulae though I read somewhere that it works.
[http://www.cabaret-solutions.com/en](http://www.cabaret-solutions.com/en)

There is also an online pdf editor [http://www.pdfescape.com/](http://www.pdfescape.com/)

---

### Post by audiomick on 2012-11-13
@ monkeybrain: thanks for that, good to know. I haven't looked into that stuff, because I only need to view something that Document Viewer wont handle about once a year. ;)

---

