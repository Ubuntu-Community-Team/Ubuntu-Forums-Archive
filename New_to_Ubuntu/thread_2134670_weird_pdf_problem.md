---
title: "weird pdf problem"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by balbecdaze on 2013-04-11
SOLVED see post 4
There's this document I need to have, PDF.  But when I download it onto my Ubuntu or Mint computer, some of the images don't show the words.  Here's a pic of how it looks on Ubuntu:

[ATTACH=CONFIG]241234[/ATTACH]

But the blue boxes should have words in them.  Well they do have words in them, I just can't see them.

Any ideas?

---

### Post by balbecdaze on 2013-04-11
The words are there because I can mouse over them and copy and paste them, I just can't see them!  Is there a way to change the colour of the fonts or something?

---

### Post by tgalati4 on 2013-04-11
What program was used to create the diagram?  Typically, you would highlight the text box and click "bring to front".  It's possible that when the image was pasted into the document the alignment tags didn't transfer.  When it is rendered as a PDF the blue boxes are covering your text because they are listed first in the object's xml--without the tags to force them to the back or text to the front.

So depending on how you created the diagram, this may not be a PDF problem.

---

### Post by Impavidus on 2013-04-12
Possibility 1: The text has the same colour as the boxes.
Possibility 2: The text is behind the boxes.
Possibility 3: You have missing fonts. The creator of this pdf may have assumed his fonts are present on every computer and therefore has not embedded them, but they may not be present on most Linux machines. This is common but bad practice: the standard clearly says only a hand full of fonts can be assumed present and built-in in every pdf interpreter. That is why pdf is supposed to be portable.

You could try and load your pdf in inkscape and fiddle around (change colours, reorder objects, change fonts) until you get something readable. Or you could try and find out which fonts are used but not embedded in the pdf (in evince, go to properties->fonts) and install them. But that may not be easy.

---

### Post by balbecdaze on 2013-04-12
Thanks Impavidus.  I installed inkscape and no fiddling required, the boxes were readable right away.  I suspect that a ticked checkbox that said something like "replace fonts with nearest installed font" solved the problem given your possibility 3.

---

### Post by Impavidus on 2013-04-12
You're welcome.

---

