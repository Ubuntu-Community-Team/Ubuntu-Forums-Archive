---
title: "How do I combine single pdfs into a single mutipage pdf"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by bwallum on 2008-09-11
Hi

I have 5 scanned in pages in pnm format. They are five seperate files at the moment. I would like to combine them into a single multipage pdf file.

Has anybody any experience of this and if so, what is the best package to use.

Regards
Bob

---

### Post by gvartser on 2008-09-11
insert the scanned images into an OpenOffice document then use the export to PDF feature in OpenOffice.

/g

---

### Post by iaculallad on 2008-09-11
On your terminal:

```
sudo apt-get install pdftk
```

and to execute it:

pdftk file_1.pdf file_2.pdf file_3.pdf cat output file.pdf

---

### Post by bwallum on 2008-09-11
> **gvartser said:**
> insert the scanned images into an OpenOffice document then use the export to PDF feature in OpenOffice.

/g

Thanks, but OOo doesn't recognise the pnm format. I may have to scan again and output to a different format.

---

### Post by bwallum on 2008-09-11
> **iaculallad said:**
> On your terminal:

```
sudo apt-get install pdftk
```

and to execute it:

pdftk file_1.pdf file_2.pdf file_3.pdf cat output file.pdf

I loaded up the application and it appeared to work but couldn't read pnm files....so I converted the pnm to png in Gimp and then combined the images in OO Draw, then exported to pdf. Amazingly I could read the multi page pdf clearly.....

Thanks for your help, I'll take another look at pdftk when I have some spare time. Isn't Uby good, always learning something!

---

