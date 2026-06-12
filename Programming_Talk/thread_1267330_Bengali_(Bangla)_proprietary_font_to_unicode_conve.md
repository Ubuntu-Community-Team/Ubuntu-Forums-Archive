---
title: "Bengali (Bangla) proprietary font to unicode conversion"
date: 2009-09-15
forum: Programming Talk
---

### Post by alexyz on 2009-09-15
I've have data in Bengali language (Bangladesh) that I need to convert to unicode.

The data is encoded using an outdated non-unicode approach, in which the font has Bengali characters in place of latin characters.  Because of this, you MUST use this particular font, unlike unicode.

I'm not sure if I'm using precisely the right terminology here, but one way to understand the problem is to look at the font using a font viewer or character map.  You see Bengali characters in the "Latin" character space where normally you see "ABCDEF..." .  With a unicode font you see "ABCDEF..." in the "Latin" character space, and the Bengali elsewhere in its own space.  Here's another explanation:  [http://www.bornosoft.com/kb_interface/efont.htm](http://www.bornosoft.com/kb_interface/efont.htm)

* It might be possible to convert this data using the **recode** or **iconv** commands, but I'm not sure what the "from" encoding should be.  I'd prefer a command-line, script-able solution rather than a GUI.

The font being used is called SulekhaT.

I've done extensive searching with no luck.  Probably because I should be searching in Bangla!  ](*,)  Any help would be most appreciated!

---

### Post by Reiger on 2009-09-15
By far the easiest thing to do would be to create a converted that takes <binary-text-like-data> and converts it to <UTF-text>.

You simply have to find equivalents in your data of the following:
[http://en.wikipedia.org/wiki/Bengali_script#Bengali_in_Unicode](http://en.wikipedia.org/wiki/Bengali_script#Bengali_in_Unicode)

Then use that table for substitution of the outdated character format with UTF equivalents...

---

### Post by alexyz on 2009-09-15
> **Reiger said:**
> You simply have to find equivalents in your data of the following:
[http://en.wikipedia.org/wiki/Bengali_script#Bengali_in_Unicode](http://en.wikipedia.org/wiki/Bengali_script#Bengali_in_Unicode)


Thanks for the response, that would work.

I should have said, I realize I could do the mapping myself but am looking for a simpler solution (especially because I don't read Bengali. :) )  And it seems like the sort of problem someone must have solved already.  Thanks though, sorry I wasn't clear about that.

---

