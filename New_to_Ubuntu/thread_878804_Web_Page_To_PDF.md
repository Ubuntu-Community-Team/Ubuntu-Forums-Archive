---
title: "Web Page To PDF?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by wpwend42 on 2008-08-03
In Windows I was using PDF Creator via Firefox to convert web pages to PDF for printing or offline viewing.  What is the best way to do this in Ubuntu using Firefox3?  I tried the PDF Download extension, but the site keeps saying it is too busy.  Thanks in advance for your help!

---

### Post by billgoldberg on 2008-08-03
> **wpwend42 said:**
> In Windows I was using PDF Creator via Firefox to convert web pages to PDF for printing or offline viewing.  What is the best way to do this in Ubuntu using Firefox3?  I tried the PDF Download extension, but the site keeps saying it is too busy.  Thanks in advance for your help!

Wait a while. There servers can't handle it I think.

---

### Post by northern lights on 2008-08-03
Theoretically, if this is Hardy you should have 'cups-pdf' installed. In Firefox, simply try to the 'Print' dialog - no PDF printer?

If not, run ```
sudo apt-get install cups-pdf
```

You might have to add the printer manually.

> **wpwend42 said:**
> PDF Download
As far as I know, this extension literally is meant to download .pdf files.

---

### Post by billgoldberg on 2008-08-03
> **northern lights said:**
> 

As far as I know, this extension literally is meant to download .pdf files.

No this can do more:

pdf to html, html to pdf, ...

But it's depending on the servers of the people behind the add on.

So it the servers are off-line of getting to much traffic, the add on stops working.

---

### Post by blue_shift on 2008-08-03
If you need a quick-and-dirty solution you can try the command line programme html2text, then take the data from there.
```
sudo apt-get install html2text
html2text myfile.html | nano
```
or whatever you want to do with it.

---

### Post by jubilee0824 on 2008-08-03
If you just want to create a PDF from a website, I would suggest using CUPS-PDF printer as northern lights says. In this way, you can create a PDF off anything on any program...(so long as it supports printing) The created PDF will be insude your-home-folder/Documents/

---

### Post by wpwend42 on 2008-08-03
*If you just want to create a PDF from a website, I would suggest using CUPS-PDF printer as northern lights says. In this way, you can create a PDF off anything on any program...(so long as it supports printing) The created PDF will be insude your-home-folder/Documents/*

Yep I figured it out.  Thanks everyone!

---

