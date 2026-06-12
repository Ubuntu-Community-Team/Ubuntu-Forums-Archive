---
title: "scan to pdf/print"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by weezyrider on 2012-02-06
Is there any app that does this? I tried one from software - said saving as PDF, but looked more like a variant. Gimp would open it, but couldn't print it. You simply cannot adjust the scanner settings. The scanning software also would not let me add the HP printer. Tried to print from Gimp, and the printer just sat there and chewed on it. 

The scanner and the printer both work in Ubuntu - just can't turn the scanner into a copier.

---

### Post by wolfen69 on 2012-02-06
Have you tried *gscan2pdf* ?

---

### Post by bluexrider on 2012-02-06
> **wolfen69 said:**
> Have you tried *gscan2pdf* ?

+1 works well


Only two clicks are required to scan several pages and then save all or a selection as a PDF or DjVu file, including metadata if required.

gscan2pdf can control regular or sheet-fed (ADF) scanners with SANE via scanimage or scanadf, and can scan multiple pages at once. It presents a thumbnail view of scanned pages, and permits simple operations such as cropping, rotating and deleting pages.

OCR can be used to recognise text in the scans, and the output embedded in the PDF or DjVu.

PDF conversion is done by PDF::API2.

The resulting document may be saved as a PDF, DjVu, multipage TIFF file, or single page image file.

---

### Post by techvish81 on 2012-02-07
+1 to gscan2pdf , i've never found such a gem in windows too

---

### Post by HiImTye on 2012-02-07
you can *print to file* and choose to save it as a .pdf  instead of a .ps

the document viewer should be able to print .pdf files (I use it to do so all the time)

---

### Post by Linux Dutchman on 2012-02-07
????? Why using those tools???
 
Xsane and the standard scan tool Simple scan does the work for you. Just a matter of setting the extension rigth!

---

### Post by farrinux on 2012-02-07
I too use xane and also simple scan.  One other thing that may help is to install cups-pdf it allows you to print any document to pdf.  When you install, it shows up as a printer on your system. It also puts a folder in your home directory labeled PDF that it prints the file too.  One thing to remember is it gives everthing it prints the same name. So when you print to it make sure you go and rename your file.

---

### Post by weezyrider on 2012-02-07
I tried Xane. It saved a multiple document file in some kind of subformat as I had the setting for pdf checked. Simple scan wouldn't read it, I tried another pdf reader from Software, and that wouldn't open it. It opened in Gimp, but if I tried to save it to another format I got the warning that all content would be lost. 

I had one software that wouldn't even download. It could have been gscan. Said it wasn't compatible or something missing. I'm on a laptop now so will have to look later.

I was using an Epson Perfection I bought around 1996. It had a copy utility in Windows which disappeared during an upgrade to the computer. (XP is on its own hard drive, not a partition) The Epson is finally quitting, and I installed a Canon Lidoscan. That also works in Ubuntu, but will have to try the scanning software again with the Canon.

I want all those saved files, but how can I save them in a format I can print? I don't want to lose the info.

BTW, I installed the HP toolbox or whatever Linux calls it, and it can't find the printer, either. Printer works from software with no problem. Printing from anywhere gives me the choice of the HP laserjet or the Canon Pixma.

I'm using 11.04

---

### Post by weezyrider on 2012-02-07
Gscan2pdf gives me the error "dependencies can't be resolved." If I can't install it, I can't use it.

---

### Post by bluexrider on 2012-02-07
Did you try ```
sudo apt-get -f install gscan2pdf

```

---

### Post by Linux Dutchman on 2012-02-07
> **bluexrider said:**
> Did you try ```
sudo apt-get -f install gscan2pdf

```

This is a good tip! If you want to know what's going on during an installation, always do it in a terminal. Any errors will be made better visible and much more clearer!

I always use the terminal for removing and installing software just for this reason.

---

### Post by weezyrider on 2012-02-07
Here's the error from Software Center:


Depends: liblocale-gettext-perl (>= 1.05) but 1.05-6 is to be installed 
Depends: sane-utils (>= 1.0.17) but 1.0.22-2ubuntu1 is to be installed 
Depends: libtiff-tools but it is not going to be installed Depends: libconfig-general-perl (>= 2.40) but it is not going to be installed 
Depends: libarchive-tar-perl but it is a virtual package 
Depends: libset-intspan-perl (>= 1.10) but 1.16-1 is to be installed Depends: libreadonly-perl but it is not going to be installed  


???????????????

---

### Post by bluexrider on 2012-02-08
> **weezyrider said:**
> Here's the error from Software Center:  

again, have you tried 
```
sudo apt-get -f install gscan2pdf

```

all of these dependencies are updates in perl, so the -force install should take care of that issue
> 
Depends: liblocale-gettext-perl (>= 1.05) but 1.05-6 is to be installed 
Depends: sane-utils (>= 1.0.17) but 1.0.22-2ubuntu1 is to be installed 
Depends: libtiff-tools but it is not going to be installed Depends: libconfig-general-perl (>= 2.40) but it is not going to be installed 
Depends: libarchive-tar-perl but it is a virtual package 
Depends: libset-intspan-perl (>= 1.10) but 1.16-1 is to be installed Depends: libreadonly-perl but it is not going to be installed  

make sure your software sources are enabled from the universe and multiverse then

```
sudo apt-get update && sudo apt-get upgrade 
```

Then try to reinstall gscan

I have it working on my Natty-box

---

### Post by weezyrider on 2012-02-09
How do I make sure that multiverse is installed? I checked Software center, found the description of multiverse, and there is a green check alongside.

I got the same error using the terminal as software center.

The only updates I've seen are for Chrome browser which I am thinking of getting rid of. I don't use it.

---

