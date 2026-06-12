---
title: "C and Glade"
date: 2008-01-18
forum: Packaging and Compiling Programs
---

### Post by berghem on 2008-01-18
hi, I compiled my application with glade, but when run my application i have this error

stefano@stefano-desktop:~/glade/prova1$ ./prova
/home/stefano/.themes/Xenon/gtk-2.0/gtkrc:285: Impossibile trovare il file di immagine in pixmap_path: "panel-bg.png"

translate
Impossible to find the image the file in pixmap_path: "panel-bg.png"


/home/stefano/.themes/Xenon/gtk-2.0/gtkrc:288: Background image options specified without filename

Can you help me?

Sorry for my english

---

### Post by quandary on 2008-01-19
Linux is case-sensitive.
Check the spelling of your filenames.


You maybe have a capital letter in a filename where there should be a non-capital letter - or vice-versa...

---

