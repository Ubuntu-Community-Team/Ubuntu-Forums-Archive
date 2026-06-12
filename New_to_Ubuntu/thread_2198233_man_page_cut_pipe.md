---
title: "man page cut pipe"
date: 2014-01-07
forum: New to Ubuntu
---

### Post by Kevin McCready on 2014-01-07
I'm not very good with man pages. 

I'd rather have them as a text file. Is there a way to pipe a man page to a text file?

I want to be able to cut and paste stuff from man files.

---

### Post by dennis13 on 2014-01-07
That's easy. Just use redirection to send the man output to a file. Like this:
[B]
[FONT=courier new]man ls > ls.txt[/FONT][/B]

Also when you're using the terminal application of your desktop application you don't need to copy man pages to text files. Just highlight the text you want to copy with the mouse and use a right click to copy it the clipboard. You can also press Shift+Ctrl+C in Gnome Terminal instead of using the context menu.

Best, Dennis

---

### Post by squakie on 2014-01-07
What about man xxxx > somefilename.someextension?

I just did a man find > mytest.txt and it looks like what you are looking for.

---

### Post by Kevin McCready on 2014-01-07
actually I tried that before I posted and only got the first page

---

### Post by Kevin McCready on 2014-01-07
oops
it only had one page.

---

### Post by dennis13 on 2014-01-07
Ooops, it worked fine for me. But I was trying on Fedora, which shouldn't make a difference however.

You can also try the following (see [FONT=courier new]**man man**[/FONT] for details)

Produce UTF8 text: [FONT=courier new]**man -Tutf8 ls > ls.txt**[/FONT]
Or if the above doesn't work: [FONT=courier new]**man -P cat ls > ls.txt**[/FONT]
Produce postscript file: [FONT=courier new]**man -Tps ls > ls.ps**[/FONT]
Create HTML and open in Firefox: [B][FONT=courier new]man --html=firefox ls[/FONT]
[/B]
However you can still copy/paste text from the terminal without saving to a text file.

Dennis

---

