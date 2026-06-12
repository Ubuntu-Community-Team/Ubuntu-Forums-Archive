---
title: "HOWTO: Convert .ps to PDF...a few tricks"
date: 2005-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by buldir on 2005-06-03
If you would like to save multiple web pages (from many sources) for off-line viewing in PDF format, these simple scripts are for you.  In Firefox, for example, simply click on the printer icon, select "Print To" File, name the file what you like (with a .ps extension), and hit "Print".  The first script (makepdf) converts multiple .ps files in a given directory to corresponding multiple PDFs with the same name, while the second script (cat_ps2pdf) converts multiple .ps files to one PDF with a file name chosen by you.  Enjoy!

makepdf
```
#! /bin/bash

for ps_file in *.ps; do
base=${ps_file%%.*}
gs -q -dBATCH -dAutoFilterColorImages=false -sColorImageFilter=FlateEncode -dNOPAUSE -sDEVICE=pdfwrite -sOutputFile=${base}.pdf ${ps_file}
done
```

cat_ps2pdf
```
#! /bin/bash

echo "Enter the output PDF filename (without pdf extension): "
read output_file
ps_files=`ls *.ps`
gs -q -dBATCH -dAutoFilterColorImages=false -sColorImageFilter=FlateEncode -dNOPAUSE -sDEVICE=pdfwrite -sOutputFile=${output_file}.pdf ${ps_files}
```

---

### Post by buldir on 2005-06-03
Here is another option for KDE users via the "kprinter" command:

[http://www.granneman.com/webdev/browsers/mozillafirefoxnetscape/linuxspecific/kdeprintinginmozilla/](http://www.granneman.com/webdev/browsers/mozillafirefoxnetscape/linuxspecific/kdeprintinginmozilla/)

---

### Post by az on 2005-06-03
[http://test.wiki.ubuntu.com/forum/software/cups-pdf](http://test.wiki.ubuntu.com/forum/software/cups-pdf)

---

### Post by manishsingh4u on 2008-03-17
Thanks. It works great.

---

### Post by Geekkit on 2009-06-25
> **buldir said:**
> If you would like to save multiple web pages (from many sources) for off-line viewing in PDF format, these simple scripts are for you.  In Firefox, for example, simply click on the printer icon, select "Print To" File, name the file what you like (with a .ps extension), and hit "Print".  The first script (makepdf) converts multiple .ps files in a given directory to corresponding multiple PDFs with the same name, while the second script (cat_ps2pdf) converts multiple .ps files to one PDF with a file name chosen by you.  Enjoy!

makepdf
```
#! /bin/bash

for ps_file in *.ps; do
base=${ps_file%%.*}
gs -q -dBATCH -dAutoFilterColorImages=false -sColorImageFilter=FlateEncode -dNOPAUSE -sDEVICE=pdfwrite -sOutputFile=${base}.pdf ${ps_file}
done
```

cat_ps2pdf
```
#! /bin/bash

echo "Enter the output PDF filename (without pdf extension): "
read output_file
ps_files=`ls *.ps`
gs -q -dBATCH -dAutoFilterColorImages=false -sColorImageFilter=FlateEncode -dNOPAUSE -sDEVICE=pdfwrite -sOutputFile=${output_file}.pdf ${ps_files}
```

I hope it's not too late to say thanks but THANK YOU! This is a great little script and works like a charm. :))

---

### Post by kingnebby on 2009-06-27
Thanks a bunch, just what I was looking for!!!!:D

---

