---
title: "GIMP cannot render WMF in Natty"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Paddy Landau on 2011-10-15
In 8.04 and 10.04, I was able to open and convert WMF files (from Microsoft) in GIMP.

I have installed 11.04, and find I cannot do so. When opening the WMF file in GIMP, GIMP seems to think that the file is of size -1x-1 pixels and therefore cannot convert it (see screen shot).

I have tested this with the same file that I used before I installed 11.04, and I get the same error.

What can I do to fix GIMP for WMF files? I already have libwmf-bin and libwmf0.2-7 installed.

---

### Post by Paddy Landau on 2011-10-17
Bump

I desperately need this, if anyone can help, please?

---

### Post by thatguruguy on 2011-10-17
Will it open in Inkscape?

---

### Post by Paddy Landau on 2011-10-17
Thank you for your reply.

I've just installed Inkscape, and sadly, no. When I open the file, Inkscape "opens" a blank document. There is no error message, even when I run it from the terminal.

---

### Post by Paddy Landau on 2011-10-17
I've run GIMP from a terminal, and I see these errors at the point of trying to open the WMF file:
```
(file-wmf:6443): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion `width >= -1' failed
ERROR: font.c (1334): wmf_ipa_font_map: failed to load *any* font!

(file-wmf:6443): LibGimpWidgets-CRITICAL **: gimp_preview_area_draw: assertion `buf != NULL' failed
```I have seen the message about wmf_ipa_font_map on forums for recent upgrades to Mint, too. Unfortunately, I do not know how to interpret these error messages or what to do about them.

---

### Post by thatguruguy on 2011-10-17
Did you look at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/libwmf/+bug/629153") and try the work-around?

Also, does the .wmf open in LibreOffice?

---

### Post by Paddy Landau on 2011-10-17
Thanks for the bug report. I have added my vote and a comment.

The workaround gives me a solution as follows:

[LIST=1]
[*]Convert the WMF file to EPS with:```
wmf2eps --wmf-fontdir=/usr/share/fonts/type1/gsfonts -o output.eps input.wmf

```
[*]Open the EPS file in GIMP.
[/LIST]
 
A bit of a pain, but better than being unable to proceed.

The WMF file does open in Libre Office. I need to convert WMF files to JPG, though, otherwise the Libre Office file becomes way too large (each WMF image is measured in MB rather than the few KB that the equivalent JPG does).

---

### Post by Paddy Landau on 2012-05-19
I have raised a further bug report for this.

If it affects you, please [vote for the bug]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1001570") (green writing at the top-left of the page).

---

