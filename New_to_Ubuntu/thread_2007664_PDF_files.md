---
title: "PDF files"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by DaveMcC on 2012-06-21
How can I edit a 4 page PDF file down to one page, I need to delete page's 2, 3, and 4

Dave

---

### Post by mastablasta on 2012-06-21
you can import the PDF into libre office draw (draw, not writer), but you need to install pdf import plugin or something like that form software center.

---

### Post by Kakers on 2012-06-21
You could try PDF Mod or PDF Editor also available on the software centre.

---

### Post by dcsoldschool53 on 2012-06-21
Try PDF Shuffler. You can actually get it from the Ubuntu software center.

---

### Post by Xernie on 2012-06-21
Try pdftk. It's a very useful tool; it's in the repos. To do what you want, go to the terminal and run pdftk like this:

```
pdftk your-file.pdf burst
```

which will give you one PDF for each page. You can read more about it [here]("http://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/").

---

### Post by Michael Dooley on 2012-06-21
> **DaveMcC said:**
> How can I edit a 4 page PDF file down to one page, I need to delete page's 2, 3, and 4

pdfsam allows both splitting and merging pdf files. It is available in the repos and in the software center. Simple and effective.

---

### Post by HermanAB on 2012-06-21
+1 PDFShuffler

---

