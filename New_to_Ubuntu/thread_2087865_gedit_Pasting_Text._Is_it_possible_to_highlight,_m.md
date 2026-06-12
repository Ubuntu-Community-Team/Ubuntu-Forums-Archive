---
title: "gedit: Pasting Text. Is it possible to highlight, make text bold, color etc"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by hannah187 on 2012-11-24
Hi ..
very simple beginners question.

Action: pasting /typing normal text (not writing script) in gedit.

Question: Is it possible to [COLOR="Red"]color[/COLOR] / make **bold** part of these texts.

I basically want to highlight important part of the texts. This can be easily done in open office / libre office but I like to use gedit as it is lightweight. Please note that I am not writing any scripts.

Advice if there is any pluglins I need to download for this purpose.

Many thanks

---

### Post by vasa1 on 2012-11-24
I don't think that what you want is possible with gedit even with plug-ins. Abiword from the repos is lighter than LibreOffice. You could look at that.
Alternatively, you could use an html editor.

---

### Post by llamabr on 2012-11-24
As gedit is a text editor, and not a word processor, it's probably the wrong tool for what you want.  In a text editor, there's no reason to color text yourself, particularly since, as you say, you're not writing scripts.

Maybe say more about what you want to do, and we can pick out the best tool for you.

---

### Post by DuckHook on 2012-11-24
The purpose of gedit is to generate pure unadulterated text files for such things as config files where the last thing wanted are escape characters of the sort used for colour and bolding. Therefore it is incapable of any fancy formatting.

---

### Post by hannah187 on 2012-11-25
> **llamabr said:**
> 
Maybe say more about what you want to do, and we can pick out the best tool for you.

Definitely all the answers were in the right direction. And now I know that it is not possible in gedit. Thanks.

Task: Want to highlight/color / make bold part of texts that I am writing.

Req: The lightest tool that will allow me to do the above task, plz.

Many thanks

---

### Post by vasa1 on 2012-11-25
**Retext** from the Software Center? It does bold, italics, indents, etc using markdown. It has a preview mode. No color.

---

### Post by llamabr on 2012-11-25
So what you're doing is word processing, not text editing.  So what you want is a word processor.  Take your pick:

```
~$ apt-cache search word processor | grep word
calligrawords - word processor for the Calligra Office Suite
calligrawords-data - data files for Words word processor
libreoffice-writer - office productivity suite -- word processor
openoffice.org-writer - office productivity suite -- word processor
abiword - efficient, featureful word processor with collaboration
abiword-common - efficient, featureful word processor with collaboration -- common files
abiword-dbg - debugging symbols for abiword word processor
docvert - converts word processor files to HTML
docvert-libreoffice - converts word processor files to HTML using LibreOffice
docvert-openoffice.org - converts word processor files to HTML using LibreOffice
libabiword-2.9 - efficient, featureful word processor with collaboration -- shared library
libabiword-2.9-dev - efficient, featureful word processor with collaboration -- development files
libbitmask1 - supports multi-word bitmask operations
simplyhtml - Java word processor based on HTML and CSS
wordgrinder - a simple word processor that runs in a terminal
wordnet-grind - WordNet lexicographer files processor

```

---

### Post by hannah187 on 2012-11-25
> **llamabr said:**
> So what you're doing is word processing, not text editing.  So what you want is a word processor.  Take your pick:


Thanks a lot. I have now installed abiword. Does what I want to do.

Regards

---

