---
title: "[SOLVED] XSane, .pnm files and GIMP"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by roquefilipe on 2008-10-05
hi, 

I wanted to scan some pages into a pdf file, so I used xsane in multipage mode, which saved the files in .pnm format. 

I also wanted to edit a few of those pages, but since the xsane editor is pretty low in features, I turned to GIMP. 

After editing, xsane doesn't seem to handle those edited files. 

Has anyone encountered such problems before, and or is capable of reproducing the problem? Also, what solutions might there be? 

It seems to me that there might be a bug somewhere, but exactly where: xsane or gimp?

---

### Post by roquefilipe on 2008-10-05
ok, I was still exploring the matter and come across this:

this is the edited file in GIMP.
```
$ head -c 1000 image-0001.pnm 
P6
# CREATOR: GIMP PNM Filter Version 1.1
850 1169
255

```

this is a file unedited in GIMP, that xsane is able to read.
```
$ head -c 1000 image-0003.pnm 
P6
# XSane settings:
#  resolution_x    =  100.0
#  resolution_y    =  100.0
#  gamma      IRGB = 0.90 1.00 1.00 1.00
#  brightness IRGB =  0.0  0.0  0.0  0.0
#  contrast   IRGB =  0.0  0.0  0.0  0.0
#  color-management= 0
#  cms-function    = 0
#  cms-intent      = 0
#  cms-bpc         = 0
#  icm-profile     = 
# XSANE data follows
00850 01169
255
```

So it seems to me that this comments might be responsible for xsane not being able to read them. If so, then how to make GIMP, preserve the original comments?

---

### Post by BandD on 2008-10-05
I'm not exactly sure where the problem lies.  I've never tried exactly what you are trying to accomplish.

However, as an immediate sloppy workaround, you can import the files to Gimp.  Touch them up.  Save them as a.tiff or .jpg (depending on how much resolution you need to keep).  Then open them in OpenOffice Draw and export them to PDF from there. 

I needed to turn a flyer I put together in GIMP into a pdf, and obviously GIMP doesn't support exporting as a PDF.  So this is the easiest workaround I came across.

Not the best fix, but you'll get your PDFs in the end.

---

