---
title: "Some PDFs print blank pages"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by dover19 on 2008-05-08
I've been trying to print something in Ubuntu and every time I sent it to the printer it came out as a blank page. Then I tried 2 other printers...same thing.

So I did a print preview and it shows up white in there too. Any ideas?

Here's a PDF that acts this way.
[http://www.dustbane.ca/msds/Acclamation_en.pdf](http://www.dustbane.ca/msds/Acclamation_en.pdf)

---

### Post by bone2006 on 2008-05-08
have you tried another pdf viewer?  Do other documents print alright except for PDF files?
If that's the case I'd probably try using another PDF viewer.  I'm not sure, but kpdf is pretty popular, to install it type in the terminal
sudo apt-get install kpdf

If you want adobe acrobat's priority viewer, go a google search for medibuntu, in which you can add their repository and then install their software if you think that will help.

---

### Post by dover19 on 2008-05-15
I installed KPDF and it seams to work fine. But now I want to remove Document Viewer and jsut keep KPDF and I get the following error:

Cannot remove 'evince'

One or more applications depend on evince. To remove evince and the dependent applications, use the Synaptic package manager.

I've never really used Synaptic before but it looks simple enough. the only thing that's worrying me is the "dependent applications" part. Will removing this screw something up? If so then maybe I should jsut pade KPDF as the default PDF viewer or something.

---

