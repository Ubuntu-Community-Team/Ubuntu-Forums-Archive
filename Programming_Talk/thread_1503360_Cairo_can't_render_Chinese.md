---
title: "Cairo can't render Chinese?"
date: 2010-06-06
forum: Programming Talk
---

### Post by kahumba on 2010-06-06
Hi,
Cairo doesn't render Chinese at all, have a look at the screenshot.
The string itself is ok, since when I print it to the command line right before issuing "cr->show_text(sFileName);" it prints: "&#22825;&#23433;&#38272;&#24291;&#22580;" - thus the string itself is ok.
I'm using gtkmm & Lucid Lynx.

I found other folks talking about similar issues back in 2008:
[http://lists.cairographics.org/archives/cairo/2008-July/014504.html](http://lists.cairographics.org/archives/cairo/2008-July/014504.html)

Anyone familiar with the matter or any suggestions?

I'm not Chinese nor have anything to do with it, I just want my app to work properly.

---

### Post by splicerr on 2010-06-06
You'll want to use Pango for that.

> 
 Cairo has two sets of text rendering capabilities: 
 
[LIST]
[*]     The functions with *text* in  their name form cairo's     *toy* text API.  The toy API takes UTF-8  encoded     text and is limited in its functionality to rendering simple     left-to-right text with no advanced features.  That means for  example     that most complex scripts like Hebrew, Arabic, and Indic scripts are     out of question.  No kerning or correct positioning of diacritical  marks     either.  The font selection is pretty limited too and doesn't handle  the     case that the selected font does not cover the characters in the  text.     This set of functions are really that, a toy text API, for testing  and     demonstration purposes.  Any serious application should avoid them.
[*]     The functions with *glyphs* in  their name form cairo's     *low-level* text API.  The low-level API  relies on     the user to convert text to a set of glyph indexes and positions.   This     is a very hard problem and is best handled by external libraries,  like     the [COLOR=Cyan]_[pangocairo]("http://library.gnome.org/devel/pango/stable/pango-Cairo-Rendering.html")_[/COLOR] that is part of the Pango text layout and rendering  library.     Pango is available from [http://www.pango.org/](http://www.pango.org/).
[/LIST]

[http://www.cairographics.org/manual/cairo-text.html#cairo-text.description](http://www.cairographics.org/manual/cairo-text.html#cairo-text.description)


---

### Post by kahumba on 2010-06-06
Thanks,
I searched for "pangomm tutorial" and the only thing I've found is another guy asking for this with no reply:
[http://www.mail-archive.com/gtkmm-list@gnome.org/msg11963.html](http://www.mail-archive.com/gtkmm-list@gnome.org/msg11963.html)
Anyone aware of any pango(mm) tutorial?

---

### Post by jyaan on 2010-09-20
There is a little bit of info here: [http://cairographics.org/FAQ/#using_pango](http://cairographics.org/FAQ/#using_pango)

---

