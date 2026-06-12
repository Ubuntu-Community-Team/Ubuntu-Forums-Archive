---
title: "Weird LibreOffice PDF output"
date: 2012-08-18
forum: New to Ubuntu
---

### Post by duncan12 on 2012-08-18
The attached ODG, when exported as PDF with LibreOffice, turns out like the attached PDF (weird blue arrow on first page)

Also appears like that when printing ](*,)


Here's some screenshots:

Preview that appears when printing, and the output of Export to PDF:

[IMG]http://img100.imageshack.us/img100/6144/weirdy.png[/IMG]

The document (note how words go beyond page boundary):

[IMG]http://img809.imageshack.us/img809/8813/normr.png[/IMG]
How can I get rid of the blue arrow?

Thanks

---

### Post by duncan12 on 2012-08-20
bump

---

### Post by duncan12 on 2012-08-21
Any ideas?

---

### Post by duncan12 on 2012-08-21
Weird bug. Worked around it by using one page, but annoying that I have to make compromises :mad:

---

### Post by Zill on 2012-08-21
duncan12:  It looks to me that you simply need to rescale the graphic to fit within the page boundary.  The arrow seems to indicate that it exceeds this and shows that it has needed to wrap to another page.

---

### Post by duncan12 on 2012-08-24
> **Zill said:**
> duncan12:  It looks to me that you simply need to rescale the graphic to fit within the page boundary.  The arrow seems to indicate that it exceeds this and shows that it has needed to wrap to another page.

Well you wouldn't expect such an arrow when printing, similarly to how the red lines under misspelled  words don't show when printing..

Anyway resolved it in the end by doing just that, problem is it meant I had to split it into two and the style wasn't carried between them (see how the fontwork starts thin and gets thicker in the middle - had to remove that to be able to split it into two)

Oh well was fine in the end, with a compromise ;)

---

### Post by Zill on 2012-08-24
> **duncan12 said:**
> ...Anyway resolved it in the end by doing just that, problem is it meant I had to split it into two and the style wasn't carried between them (see how the fontwork starts thin and gets thicker in the middle - had to remove that to be able to split it into two)...
Sorry, but I don't quite see what the problem was here.

I simply selected the graphic, then clicked on the lower-right corner and dragged this in to fit the page.  The graphic then fits correctly in both .odg and .pdf view.  See attached example.

---

### Post by duncan12 on 2012-08-25
> **Zill said:**
> I simply selected the graphic, then clicked on the lower-right corner and dragged this in to fit the page.

Sorry I had a long, better explanation then clicked back and lost it :evil:

Basically I wanted a graphic that streched across two pages. I did this by having two pages where there was half of the full graphic showing on the page. That's how I wanted to print it, at that size, only printing what was on the page, no blue arrow.

In the end I split it into "Sound in" and "sulation". However, there's normally an effect where the graphic starts thin, is thick in the middle, and thin again at the end. I had to disable this when splitting into two.

Sorry if I didn't explain well earlier.. anyway don't worry cause I finished the project that involved this a while ago now, using the workaround.

---

