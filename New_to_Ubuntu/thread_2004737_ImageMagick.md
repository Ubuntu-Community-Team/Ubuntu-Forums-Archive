---
title: "ImageMagick"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-16
Hi,

I am using Ubuntu since 12.04 release and very happy with it. Only a few more quirks I have to solve and could then delete Windows for good.

One annoying thing I have realized is how painful it is to scan a document from with my wireless Canon MG6150 All-in-one printer.

The Canon linux drivers - unlike the Windows version - doesn't allow to save in PDF with a HIGH compression, neither can I convert multiple documents into one file.  (How could the developers miss this feature?)

So I have to save each scanned document as a JPEG file and go to terminal and run ImageMagick:

```
convert *.JPG -compress JPEG output.pdf
```

At least this way I can have multiple documents into one PDF, which is good.

Despite using compression parameter, it is still quite bad compared to that on Windows. Is there anyway to increase the compression rate?

Many Thanks,
Houman

---

### Post by N0oki3 on 2012-06-16
You can try using of of these programs :

**XSane** looks powerful, but not really suitable as a workflow solution;


**gscan2pdf** is a bit closer to the "push the button, get the PDF" ideal, but still not 100% there

---

### Post by Houmie on 2012-06-16
> **N0oki3 said:**
> You can try using of of these programs :

**XSane** looks powerful, but not really suitable as a workflow solution;


**gscan2pdf** is a bit closer to the "push the button, get the PDF" ideal, but still not 100% there

Neither XSane, nor gscan2pdf can scan the network for scanners. :( It is a wireless scanner.

---

### Post by Houmie on 2012-06-16
Unless I imported the jpegs into gscan2pdf and create the PDF from there.

I have two Jpeg files, each 1.3 mb.  If I selected 75% JPEG quality in gscan2pdf, I get a pdf file with 2.1mb size.

Thats huge.  Imagine I was going to scan my 40 pages contract.

The Windows driver were superior in this case.  Darn...[-(

---

### Post by ajgreeny on 2012-06-16
Are you sure xsane can not scan over the network?  I use a wireless HP multifunction scanner printer with no problem over wireless.  Perhaps you just need to set up the scanner properly, though I hasten to add, my knowledge of Canon and linux is very limited so I have no idea how you attempt to do that.

What about Simple-Scan, where you can set the scan resolution depending on Text or Photo in **Document > Preferences** menu, then if you use the **Document > Scan** menu item, not the scan toolbar button, you can choose whether to use the higher or lower resolution, irrespective of whether it is text or photo.

See my screenshots

---

### Post by Houmie on 2012-06-16
Hey thanks for the reply.

Simple Scan says this:

[IMG]http://i.imgur.com/s9cAj.png[/IMG]


Xsane says:

[IMG]http://i.imgur.com/Drz1O.png[/IMG]

[IMG]http://i.imgur.com/LxRMT.png[/IMG]


If I run the Canon ```
scangearmp
``` from the terminal though, I get this:

[IMG]http://i.imgur.com/6q1wo.png[/IMG]

The way canon driver works is not the standard way. :(

Painful...](*,)


> **ajgreeny said:**
> Are you sure xsane can not scan over the network?  I use a wireless HP multifunction scanner printer with no problem over wireless.  Perhaps you just need to set up the scanner properly, though I hasten to add, my knowledge of Canon and linux is very limited so I have no idea how you attempt to do that.

What about Simple-Scan, where you can set the scan resolution depending on Text or Photo in **Document > Preferences** menu, then if you use the **Document > Scan** menu item, not the scan toolbar button, you can choose whether to use the higher or lower resolution, irrespective of whether it is text or photo.

See my screenshots

---

