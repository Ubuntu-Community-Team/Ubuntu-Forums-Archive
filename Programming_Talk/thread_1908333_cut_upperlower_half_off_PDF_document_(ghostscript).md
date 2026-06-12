---
title: "cut upper/lower half off PDF document (ghostscript)"
date: 2012-01-13
forum: Programming Talk
---

### Post by CryptKeeper777 on 2012-01-13
I have a bunch of PDFs with to presentation slides on each page. I want to convert the PDFs so that each page contains only one slide. I have to split the PDF into single pages, then duplicate the pages, cut the lower half off every second and the upper half off the rest of the pages, and then merge them all together in the end.

I can handle the splitting and merging of the pages, but I don't know how to crop one half off a page. I suppose that could be done with ghostscript, printing the A4 PDFs to A5 paper size so that one half of the A4 page gets printed into the new PDF and the other half is lost (I'm OK with A5 PDFs as output).

But I don't know ghostscript. I took a look at the documentation, but didn't spot a quick solution, and I don't have the time at the moment to really learn it...

Thanks in advance for any suggestions.

---

### Post by CryptKeeper777 on 2012-01-13
Alright, I solved it myself after a lot more googling and trying around:

```

...
   gs \
          -sDEVICE=pdfwrite \
          -o "$pdf.upper" \
          -c "[/CropBox [0 $((height/2)) $width $height] /PAGES pdfmark" \
          -f "$pdf"
   gs \
          -sDEVICE=pdfwrite \
          -o "$pdf.lower" \
          -c "[/CropBox [0 0 $width $((height/2))] /PAGES pdfmark" \
      -f "$pdf"
...

```

---

