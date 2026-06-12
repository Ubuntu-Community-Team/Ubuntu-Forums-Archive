---
title: "[SOLVED] qcad saved my drawing then when opened nothing appears!"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by farsight on 2008-07-14
Hi all,

Just wondering whether anyone has come across or knows a solution to the following problem.

Problem: Having drawn my drawing within the QCAD program I clicked save and saved the drawing to my home directory in the .dxf format. I then tried to reopen the file and voila my drawing was no where to be seen.

If it is any use to anyone with a possible solution to reacquiring this image when I tried to reopen the file I got a message saying that no program was able to open that particular file format. Using open with I simply typed in QCAD which got it to load QCAD but, as stated, not the drawing.

Any help would be fantastic, 
regards, Farsight.

---

### Post by braddcadd on 2008-07-14
does it have a large file size? Places->Home Folder-> (view as list)

What happens when you open Qcad and draw a single line and try to save that?  Same result?

---

### Post by farsight on 2008-07-14
Hey,

The troublesome file was 12.9 kb overall while a test with just a single line as the content was 11.0 kb. The test saved perfectly well and loaded fine. This is most bizarre!

I've tried looking on google for any similar occurrences and found just one with a solution saying open with qcad %s, which in my situation did not work unfortunately.

Any ideas?

Regards,
Farsight

---

### Post by braddcadd on 2008-07-14
If it is a simple drawing, you may be able to open the dxf file with a text editor (gedit or geany).  You could compare the "broken" file to a "working" of similar format.

Actually, "Kompare" (Applciation->Add/Remove->search for Kompare) is a great tool to compare text files.

A dxf file is just a text file with a strict format.  
( [http://en.wikipedia.org/wiki/DXF_file](http://en.wikipedia.org/wiki/DXF_file) )

Do you think there is a chance your last save was before you drew any lines?  (sorry, had to ask)

---

### Post by farsight on 2008-07-19
Hey sorry for the delay with getting a reply back to you, I haven't had internet access :( I don't believe the save was made before I drew any lines :) I have just redrawn the object and have had no such problems since then, so I must conclude for now that this was a human error on my part, somehow! 

If I get anything similar I will post again.
Thanks for all the help anyway :)

Regards,
Farsight

---

