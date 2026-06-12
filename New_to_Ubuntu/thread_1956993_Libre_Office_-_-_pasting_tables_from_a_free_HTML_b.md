---
title: "Libre Office - - pasting tables from a free HTML book"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by haplorrhine on 2012-04-12
First of all, this is legal because it's for personal use, and reading the "Terms of Use and Privacy Statement" will tell you so.  The link to them is at the bottom of the page.  However, if you're specialized for dealing with copy-rights, you can double-check the legality for me.

Here are the two problems, and solving either one is enough.
I am copying the online HTML version of this book into Libre Office, but I'm having problems with the tables.
[http://www.nap.edu/openbook.php?record_id=9826&page=6](http://www.nap.edu/openbook.php?record_id=9826&page=6)
That link goes to the first page containing the table I'm currently trying to copy.  That page copies as a table fine, but the next page of the table (page 7) won't paste into Libre Office as a table.  It's bugging me.  Exactly the same thing happened with the table of contents which was also formatted as a table.  Helping me get past this would be one solution.
At the top of each page, there is a link to the "page image."  I can also copy these images into Libre Office, but they're too blurry even after I fit them to the pages, so I only did that for the table of contents.  Telling me how to make the pasted images less blurry would be an alternate solution.

I already looked at used copies, but none of them are less than $55 even on Amazon.

sincere thanks,
Haplorrhine

---

### Post by anejo on 2012-04-12
and **Ctrl+Shft+V** doesn't help...?

---

### Post by alphacrucis2 on 2012-04-12
It worked for me. Copying from FF 11 to LO 3.5.2.2.

After some experimenting, I discovered that it doesn't work if I only select from exactly from the Om... on the second page. If I select from the horizontal bar on the line above that it works (even though the bar doesn't actually get selected by the browser). I guess that there some html table tags that don't make it to the clip board if you only select from the exact beginning of the text. At least that is my guess.. I would blame the browser rather than LO as LO can only deal with what ends up in the clipboard.

---

### Post by haplorrhine on 2012-04-12
> **alphacrucis2 said:**
> It worked for me. Copying from FF 11 to LO 3.5.2.2.

After some experimenting, I discovered that it doesn't work if I only select from exactly from the Om... on the second page. If I select from the horizontal bar on the line above that it works (even though the bar doesn't actually get selected by the browser). I guess that there some html table tags that don't make it to the clip board if you only select from the exact beginning of the text. At least that is my guess.. I would blame the browser rather than LO as LO can only deal with what ends up in the clipboard.
That solved it.   When selecting the to-be-copied text, I just had to put my pointer *above* the top dividing line before releasing the mouse button.
so simple

Thanks!

---

