---
title: "lubuntu cut paste pdf formatting"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-10-04
In Lubuntu when I cut and paste from a pdf file in Evince Document Viewer 3.4.0 Using poppler/cairo (0.18.4), much formatting is lost (eg italics, paragraph breaks).

I tried the same from xpdf (that crashes all the time) and gpdftext (even worse than ordinary highlight then cut and paste).  Any ideas?

---

### Post by rsgangr on 2013-10-05
Hi Kevin: Yes, copying from Document Viewer 3.4.0 and pasting into a word processor, e.g. OpenOffice Writer, will give you only the text, no formatting. For this reason I use Adobe Reader 9.5.4 to open a *.pdf from which I need to copy sections of text with formatting. It is not a perfect solution because, if the *.pdf contains fonts that are unavailable in OpenOffice, the closest available font will be used. Unfortunately this is not a long-term solution because Reader 9.5.4 seems to be the last version that the Linux community will get from Adobe. Good luck!

---

### Post by Kevin McCready on 2013-10-05
Thanks rsgangr
Adobe Reader 9.5.5 (current in the repository) didn't do it, even with paste special. Can it be hard for a competent programmer to figure this one out? After all, if it displays correctly on the screen ...
BTW when installing it via Synaptic you have to click on details and select Yes from the small terminal displayed in the dialogue box. This particular reader also puts massive overhead on the CPU so I'm gonna deinstall now.
Back to the drawing board.

---

