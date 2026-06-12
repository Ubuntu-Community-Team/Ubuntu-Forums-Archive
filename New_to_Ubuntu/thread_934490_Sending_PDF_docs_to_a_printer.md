---
title: "Sending PDF docs to a printer"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by know-it-some on 2008-09-30
Hi,  I print to a Savin 8025, which the openprinting DB says should work just fine.  However, I can send anything to it for printing except for PDF files.

Whats different about PDF's in terms of printing?

---

### Post by terry_gardener on 2008-09-30
are you getting any errors or what is happening when you send the print. 

also make sure that when you select file-print that you select pdf from the list and NOT print to file.

---

### Post by know-it-some on 2008-09-30
> **terry_gardener said:**
> are you getting any errors or what is happening when you send the print. 

Nope, no errors, it just never shows up at the printer.

> **terry_gardener said:**
> also make sure that when you select file-print that you select pdf from the list and NOT print to file.

There is no PDF option in my list, just:

print to file
Savin

I am trying to get a paper copy of the PDF, I am not trying to create a PDF.

---

### Post by richg on 2008-09-30
I use a PC with Ubuntu 8.04 and with a PDF open using KPDF. I select Print and Ubuntu automatically selects Epson C82, my printer. I have never done anything special since installing the printer after I installed Ubuntu 8.04.
CUPS+Gutenprint v5.0.2 Simplified

Rich

---

### Post by terry_gardener on 2008-10-01
i also didn't have to do anything special for it to work with epson printer. 

have you tried selecting the savin option in the list and clicking print. 

also what pdf viewer software are you using.

---

### Post by aeiah on 2008-10-01
see what your cups server control panel is saying over at localhost:631 (put this in your web browser)

---

### Post by know-it-some on 2008-10-01
> **terry_gardener said:**
> also what pdf viewer software are you using.

This was the ticket.  I was using the default PDF viewer that installs with ubuntu, which is called Evince.  I installed KPDF and it prints just fine!

---

### Post by terry_gardener on 2008-10-01
glad that it is printing ok in kpdf it is better IMO to the default software evince. 

there is a printer setup in evince click file-printer setup. 

then click file-print select than printer in the window for example savin then click.

---

