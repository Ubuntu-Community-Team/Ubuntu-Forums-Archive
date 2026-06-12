---
title: "postscript files?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by garyed on 2008-07-29
I download a lot of ps files instead of printing them & I can't view them unless I convert them to pdf files. I use Evince viewer & it shows nothing when I open the ps file up. If I use a text viewer or Open Office it opens but I only see the lines of code.
Is that normal?
I think at one time I could view ps files so I wonder if I could have changed some setup in the viewer.

---

### Post by ModelM on 2008-07-29
I know nothing about it but I thought that's what Ghostscript was for.

---

### Post by unutbu on 2008-07-29
Try gv:
```

gv FILENAME
```

I think it comes standard with the system, but if not,
you may need to install the 'gv' package.

---

### Post by hrod beraht on 2008-07-29
[Evince]("http://www.gnome.org/projects/evince/") has built-in support for postscript files. I'm viewing one right now with Evince.

Do your files have a .ps extension?
What happens if you right-click on one? Does it give the default option of *Open with "Document Viewer"*. If not, can you select "Document Viewer" under *Open with other application*?

Bob

---

### Post by garyed on 2008-07-29
> **hrod beraht said:**
> [Evince]("http://www.gnome.org/projects/evince/") has built-in support for postscript files. I'm viewing one right now with Evince.

Do your files have a .ps extension?
What happens if you right-click on one? Does it give the default option of *Open with "Document Viewer"*. If not, can you select "Document Viewer" under *Open with other application*?

Bob

They open by default in Evince but just a blank screen shows up.
The file sizes are around 200k or more & I know the coding is there because
when I convert the same files to pdf they open fine in Evince 0.8.1
I'm just wondering if there's some setting I'm missing.

---

### Post by captain_rob on 2009-06-04
I have exactly the same problem. Ubuntu 9.04 64 bits.

---

### Post by attila82 on 2010-07-06
> **garyed said:**
> They open by default in Evince but just a blank screen shows up.
The file sizes are around 200k or more & I know the coding is there because
when I convert the same files to pdf they open fine in Evince 0.8.1
I'm just wondering if there's some setting I'm missing.

I've similar problem with ubuntu 10.04 LTS amd64.

Evince (the same with gv) doesn't read old postscript generated with python & matplotlib, and I must rebuild them. Anyway, the result are low quality contour plots.

If I pass these files to my colleagues, they look good.
Furthermore, if I convert them to pdf (pstopdf) they're are perfect.

I installed again every python/postscript packages and also evince, but nothing changed.

Any idea?

---

