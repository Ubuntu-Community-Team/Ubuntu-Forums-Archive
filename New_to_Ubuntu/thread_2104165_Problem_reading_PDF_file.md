---
title: "Problem reading PDF file"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by Mariane on 2013-01-12
Hi, 

I have a pdf file which I did not manage to open properly. I tried with Konqueror, xpdf and pdfedit. What is displayed is this message:

```

To view the full contents of this document, you need a later version of the PDF viewer. You can upgrade to the latest version of Adobe Reader from www.adobe.com/products/acrobat/readstep2.html
For further support, go to www.adobe.com/support/products/acrreader.html

```

Which program should I use to open this file, please? 

Mariane

---

### Post by krustenBrot on 2013-01-12
Do the following in a terminal:
> pdfinfo yourfile.pdf

To get additional information on your document it might be encrypted.

---

### Post by Mariane on 2013-01-12
```

pdfinfo cerfa.pdf 

```

Answer:
pdfinfo: /opt/Druide/Antidote7/Programmes32/lib/libjpeg.so.62: no version information available (required by /usr/lib/libpoppler.so.13)
Creator:        Adobe LiveCycle Forms 8.2
Producer:       Adobe LiveCycle Forms 8.2
CreationDate:   Thu Nov  3 14:36:49 2011
ModDate:        Thu Nov  3 14:36:49 2011
Tagged:         yes
Pages:          1
Encrypted:      no
Page size:      612 x 792 pts (letter)
File size:      1239892 bytes
Optimized:      no
PDF version:    1.6

I tried okular and evince but I have the same result: 
"To view the full contents of this document, you need a later version of the PDF viewer. You can upgrade
to the latest version of Adobe Reader from [www.adobe.com/products/acrobat/readstep2.html](www.adobe.com/products/acrobat/readstep2.html)
For further support, go to www.adobe.com/support/products/acrreader.html"

I found a page with instructions about how to solve this on debian-based machines but we don't have the packages they speak about, or I should add a repository and I'm not going to do that unless someone tells me it is OK to add these to Kubuntu:
[http://forum.linuxmint.com/viewtopic.php?f=47&t=70040](http://forum.linuxmint.com/viewtopic.php?f=47&t=70040)

---

### Post by Mariane on 2013-01-12
I installed libreoffice-pdfimport and then tried to open the file with LibreOffice. I got 848 pages of something which looks like formatting script:

><caption placement="right" reserve="26mm"
><para vAlign="middle"
/><font size="8pt" typeface="Arial"
/><value
><text

etc. etc. etc.

some stuff like:

6f72706f7261746564311d301b060355040b131441646f6265205472757374205365727669636573311630140603550403130d41646f626520526f6f7420434130820122300d06092a864886f70d01010105000382010f003082010a0282010100cc4f5484f7a7a2e733537f3f9c12886b2c9947677e0f1eb9ad1488f9c310d81df0f0d59f690a2f5935b0cc6ca94c9c15a09fce20bfa0cf54e2e02066453f3986387e9cc48e0722c624f60112b035df55ea6990b0db85371ee24e07b242a16a1369a066ea809111592a9b08795a20442dc9bd73388b3c2fe0431b5db30bf0af351a29feefa692dd814c9d3d598ead313c407e9b913606fce25c8dd18d26d55c45cfaf653fb1aad26296f4a838eaba6042f4f41c4a3515cef84e22560f9518c5f8969f9ffbb0b77825e9806bbdd60af0c674949df30f50db9a77ce4b7083238da0ca7820445c3c5464f1eaa230199fea4c064d06784b5e92df22d2c967b37ad2010203010001a382014f3082014b301106096086480186f8420101040403020007

and some non-printable characters which are displayed as a question mark.

---

### Post by heheinrich on 2013-01-12
You may have tried this already, but Adobe makes a .deb download of its pdf viewer. I had a similar problem to yours, and the only thing that fixed it was getting the Adobe version.

---

### Post by sudodus on 2013-01-12
The file seems to be created 2011, so it is not brand new.

Which version of Kubuntu are you running? Would there be a chance to find a newer version of the libraries used to read pdf files, if you try with the newest version. You need not install it, test it live from a CD or USB drive!

Or have you checked with some cloud service to read documents, for example Google Documents.

---

### Post by Mariane on 2013-01-12
I finally got adobe's version, I'll just have to remember to switch off my internet connection before I view this pdf... 

Adobe has included javascript in it's new version, now when you open a pdf document with adobe's reader, the document can "phone home" without your knowledge (or authorisation!) and tell some server what you are doing with the file... 

Ref: [http://lwn.net/Articles/129729/](http://lwn.net/Articles/129729/)

So I still hope someone will tell me which open source program I could use to view this type of file. 

Meanwhile, people experiencing the same problem can install acroread with:
```

sudo add-apt-repository "deb http://archive.canonical.com/ natty partner"
sudo apt-get update
sudo apt-get install acroread

```

---

### Post by howefield on 2013-01-12
> **Mariane said:**
> Adobe has included javascript in it's new version, now when you open a pdf document with adobe's reader, the document can "phone home" without your knowledge (or authorisation!)

So much changes in software in a short space of time, it would be good to have a reference more recent than 8 years ago.

Even if this is still the case, it would probably be easier to switch off the js. 

> So I still hope someone will tell me which open source program I could use to view this type of file.

Could try Chrome web browsers built in pdf viewer.  

> Meanwhile, people experiencing the same problem can install acroread with:

Hopefully not... given that natty has gone end of life.

---

### Post by sudodus on 2013-01-12
> **howefield said:**
> ... natty has gone end of life.
+1
According to the line about the added repository, you are still running Natty, an old version of Ubuntu, that no longer receives security updates. Is that really so, or did you cut and paste from some web page and post it before editing the version (e.g natty --> precise)?

Running Kubuntu without security updates is a bigger security hazard than reading a single file with Acroread.

Also, it is quite possible that new versions of Kubuntu have updated libraries, that can read your pdf file with open source software (for example evince).

---

