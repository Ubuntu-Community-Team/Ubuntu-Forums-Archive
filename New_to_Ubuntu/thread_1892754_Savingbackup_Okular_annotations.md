---
title: "Saving/backup Okular annotations?"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by Alex.C on 2011-12-08
Hello,

I'm currently using Okular for study purposes. However, i noticed that the annotations, highlights, etc aren't saved in the PDF itself. About that subject i found these answers in Okular FAQ's 

[http://okular.kde.org/faq.php#addedannotationsinpdf](http://okular.kde.org/faq.php#addedannotationsinpdf)

**Why the newly added annotations are not in my PDF document?**
Short answer: Okular cannot change the annotations in PDF documents.

Longer answer: the library used for reading PDF documents (Poppler) does not allow changing the annotations inside a PDF document. Also, due to the fact that Okular allows you to annotate in any kind of document it supports (even if that format does not support annotations), _Okular saves the annotations internally in the local data directory for each user_.

**How can I annotate a document and send it to a friend/colleague/etc?**
Since KDE 4.2, Okular has the _"document archiving" feature. This is an Okular-specific format for carrying the document plus various metadata related to it (currently only annotations)_.
You can save a "document archive" from the open document by choosing "File -> Export As -> Document Archive".
To open an Okular document archive, just open it with Okular as it would be eg a PDF document.[/CODE]

So, is there any way to backup the local data directory where Okular saves the annotations, so if i need to reinstall the OS i won't lose them?

Or if i choose "File -> Export As -> Document Archive", i can save the document in a pendrive, reinstall the OS and Okular, and then continue working in the PDF without losing my annotations?

Thanks a lot!

---

### Post by llamabr on 2011-12-08
My guess would be yes.  In any case, you could give it a try to find out.

My other guess is that in your home directory, you'll find a ~/.ocular/ or ~/.Ocular/ directory, where it stores all these data.  If you don't see it, I'll install the program and have a look.

---

### Post by Alex.C on 2011-12-08
> **llamabr said:**
> My other guess is that in your home directory, you'll find a ~/.ocular/ or ~/.Ocular/ directory, where it stores all these data.  If you don't see it, I'll install the program and have a look.

llamabr, thanks for answering. I haven't found that directory...
i'll try to do some annotations and highlights in a PDF, export that pdf as document archive to a pendrive ["File -> Export As -> Document Archive"], and then make a complete removal of Okular. Then i'll re-install Okular and open the pdf to check if the annotations are saved and if is possible to continue working with the document. Thanks

---

### Post by Alex.C on 2011-12-12
> **Alex.C said:**
> llamabr, thanks for answering. I haven't found that directory...
i'll try to do some annotations and highlights in a PDF, export that pdf as document archive to a pendrive ["File -> Export As -> Document Archive"], and then make a complete removal of Okular. Then i'll re-install Okular and open the pdf to check if the annotations are saved and if is possible to continue working with the document. Thanks

Worked fine!
(to be sure after uninstalling okular i removed the annotations kept in /home/alexc/.kde/share/apps/okular/docdata)

---

