---
title: "How to make GnuCash fonts behave"
date: 2006-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by FourBrane on 2006-01-02
After installing GnuCash (any of the current versions which still use GTK1), you may discover that the program is basically useless because of inappropriate (crazy! ugly! fuggly!) fonts. That's what happened to me. 

Here's a solution.

First, select a decent font by running the xfontsel command. It brings up a truly horrid-looking klunker screen which, however, does let you make font choices and see what they will look like. (The interface must have been designed by Soviet-era engineers.)

ASFAIK, xfontsel doesn't affect gtk1 font useage, but it lets you see fonts
available for selection. Make your choices and write down the specification
line which was built as you made your selections of weight, size, etc.
In my case, my font choice added up to:
-adobe-helvetica-medium-r-normal-*-14-100-100-100-p-76-iso8859-1

Now, you must manually add this specification to /etc/gtk/gtkrc.utf-8 which is
where GnuCash goes to decide its fonts (non-English users will need to poke around in the gtk directory for their brand).

$sudo gedit /etc/gtk/gtkrc.utf-8

My default file looked like:
style "default-text" {
       fontset = "-*-ariale-medium-r-normal--*-100-*-*-*-*-iso10646-1,\
       		  -*-helvetica-medium-r-normal--*-100-*-*-*-*-*-*"
}

class "GtkWidget" style "default-text"

I edited the fontsel set to look like:
       fontset = "-adobe-helvetica-medium-r-normal-*-14-100-100-100-p-76-iso8859-1,\
		-*-ariale-medium-r-normal--*-100-*-*-*-*-iso10646-1,\
       		  -*-helvetica-medium-r-normal--*-100-*-*-*-*-*-*"

(This just inserted my preferred choice at the top of the default list with a comma forward slash after it.)
Voila! Gnucash becomes readable.

---

