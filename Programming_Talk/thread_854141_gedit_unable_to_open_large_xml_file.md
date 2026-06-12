---
title: "gedit unable to open large xml file"
date: 2008-07-09
forum: Programming Talk
---

### Post by badperson on 2008-07-09
I'm not sure what the problem is, I don't think it's file size. 

The xml has a lot of different processing instructions, doctype markup, etc...when I try to open with gedit, it just hangs and I have to do a force quit. 

I tried changing the encoding to utf-8, but that didn't work;

anyone else ever run into that problem? 
jason

---

### Post by Zugzwang on 2008-07-09
What is the file size of the XML file?

What is the consumption of CPU time when the program seems to hang (use "top" to find out)? Please copy&paste here a sample output of "top". This will also tell us about your memory/swap configuration. What it looks like can be seen [here]("http://en.wikipedia.org/wiki/Top_%28Unix%29").

---

### Post by odyniec on 2008-07-09
I've had similar trouble opening large or complex XML files with gedit. What worked for me was using [XML Copy Editor]("http://xml-copy-editor.sourceforge.net/") -- you should be able to find it in the repositories.

---

### Post by badperson on 2008-07-10
thanks for the replies, since this is data from work I think I'll err on the side of caution and not post it here, 

but I think the filesize wasn't an issue; I had two files from the same dtd, one big, one not so big, I so I don't think it was that. 

I basically decided it's a good opportunity to dig in and learn emacs. 
thanks again!!
bp

---

