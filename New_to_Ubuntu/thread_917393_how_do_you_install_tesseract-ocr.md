---
title: "how do you install tesseract-ocr"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by fredstevens on 2008-09-11
Hi...
Could someone please explain how to install tesseract-ocr for Ubuntu? I tried both synaptic package manager and the terminal but after it installs I can't find tesseract-ocr in the menu. Do I also need to install an interface for tesseract? Thank you.
Fred

---

### Post by srt4play on 2008-09-11
It's a command line program only.  After installing it, open a terminal (Applications -> Accessories -> Terminal) and type 

```
man tesseract
```

to see how to use it.

---

### Post by Patb on 2008-09-12
> **srt4play said:**
> It's a command line program only.  After installing it, open a terminal (Applications -> Accessories -> Terminal) and type 

```
man tesseract
```

to see how to use it.

My Tesseract man page consists of just 114 words! That doesn't do justice to this advanced OCR program.

That said, it is fairly simple, albeit command line stuff.  From memory, the input file must be in uncompressed tif format. Beware many existing tif files are compressed but you can convert to uncompressed without difficulty.  So the syntax is something like:
```
tesseract inputfile.tif outputfile.txt
```
You can use a config file for settings too but I don't use it so I'll leave you to the tender mercies of Dr Google on that.  

That's another 72 words ;). Hope it helps. Cheers, Pat.

---

### Post by james.math.u on 2008-10-08
Please try this link. 

[http://freethots.wordpress.com/2008/08/26/installing-ocropus-on-debianubuntu/](http://freethots.wordpress.com/2008/08/26/installing-ocropus-on-debianubuntu/)

---

### Post by Goedman on 2009-09-13
I think ... I managed to install tasseract on Ubuntu Jackalope but I am having problems:

When I try and convert a document it gives the following error:

jaco@max:~$ tesseract /Documents/AM.tif AMT
Unable to load unicharset file /usr/local/share/tessdata/eng.unicharset
jaco@max:~$ 

I checked to see if there was a tessdata directory in the share folder and it does contain the "eng.unicharset" that the program is looking for.

Any idea why the program is unable to read that file?

:(

---

### Post by shadesofevil on 2009-09-24
install the tesseract-data package or manually train it

---

### Post by patocardo on 2009-10-07
> **shadesofevil said:**
> install the tesseract-data package or manually train it
How do I do it?

---

### Post by Crick on 2009-10-17
> **patocardo said:**
> How do I do it?

```
sudo apt-get install tesseract-ocr-eng
```
To use the program, the image needs to be a tiff file I believe. So you'd do this to execute:
```
tesseract in.tiff out.txt
```

---

