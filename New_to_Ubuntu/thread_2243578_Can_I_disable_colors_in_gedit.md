---
title: "Can I disable colors in gedit?"
date: 2014-09-09
forum: New to Ubuntu
---

### Post by skitter on 2014-09-09
I've noticed that gedit changes the font to the color red if the first character in the line is a number.  I'd like the text to always be the same color.  Is there a way to change this?

---

### Post by vasa1 on 2014-09-10
I don't use gedit now but gedit and some other text editors have several "styles" which you may see under "Preferences" or "Options".

Then there are also the various scripting languages (formats). If you have inadvertently chosen a language or format that does this type of coloring, play around until you find one that suits you.

---

### Post by jimmy-frydkaer on 2014-09-10
To understand Gedit more read this:

[https://en.wikipedia.org/wiki/Gedit](https://en.wikipedia.org/wiki/Gedit)

The coloring is part of the syntax-highlighting

---

### Post by mcduck on 2014-09-10
like jimmy-frydkaer said, the colors depend on syntax highlighting, which is used for various programming and scripting languages and other similar documents. Theya re usually detected based on the file name extension, or in some cases by a specifc text on the first lien of the document.

So, as long as your file has the normal .txt extension, it shouldn't get any syntax highlighting unless you specifically tell Gedit to threat the fiel as something else than just text. If yu ahve by accident changed the fiel's view mode to other than plain text, you can just go to View->Highlight Mode->Plain Text.

---

