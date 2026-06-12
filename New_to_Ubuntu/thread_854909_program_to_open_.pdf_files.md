---
title: "program to open .pdf files"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by jimgeiser on 2008-07-09
When I open a .pdf file it opens with Evince, How do I get it to open with Adobe Reader. I have the program and it works fine when you open Adobe Reader and ask it to open a file, but when a .pdf file shows up on the internet Ubuntu (Firefox) uses Evince. In that other system you can set the association. Is there a way to do that in Ubuntu?

---

### Post by AOZ on 2008-07-09
next time u see a pdf file right click it and clcik open with adobe.

---

### Post by iaculallad on 2008-07-09
Or try changing Firefox settings on opening file types. Edit->Preferences, under the "Content" portion -> File Types, click on manage and try to change the PDF setting.

---

### Post by steveneddy on 2008-07-09
You need to install the Medibuntu repositories, then in terminal

```
sudo apt-get install acroread acroread-escript acroread-plugins
```

then when you have a .pdf file, right click, go to Properties, select the Open With tab and select Adobe Reader.

If you want to read .pdf file in Firefox

```
sudo apt-get install mozilla-acroread
```

---

