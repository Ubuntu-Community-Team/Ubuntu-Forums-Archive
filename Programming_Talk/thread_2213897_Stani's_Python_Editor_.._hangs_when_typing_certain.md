---
title: "Stani's Python Editor .. hangs when typing certain patterns"
date: 2014-03-29
forum: Programming Talk
---

### Post by dragonfly41 on 2014-03-29
I'm using Stani's Python Editor 0.8.4h as my default python editor on Ubuntu 12.04 32bit.

Default python version is Python 2.7.3 (although I also have python 3.2  installed)

When I am typing certain patterns into a comment in an open py file .. e.g. just typing "core.py" .. a pattern with a .py extension .. this causes SPE to freeze.

I can only get out of this freeze of SPE by running command [COLOR=#0000ff]sudo pkill python[/COLOR] .. but by then I've lost my recent code edits between frequent file saves.

Any way of troubleshooting these freezes of SPE? Perhaps I should use python3 instead of 2.7?

I do have other editors such as Geany, Komodo, Anjuta etc. I can use but I find SPE quite useful .. when it doesn't freeze on me.  In all other respects SPE is a fine editor.

Thanks.

---

### Post by dragonfly41 on 2014-03-31
SOLVED .. by going into SPE Preferences > Editor

and adding "core" into Autocomplete - Ignore.

It seems that comments strings after "#" are being parsed (I don't know why) and inserting the string core.py into my comments strings causes a freeze.  The freeze actually occurs when I typed the dot after typing "core".  It is the dot which triggers the autocomplete method.

[color=maroon][Later edit]
I found that this freeze still occurs if I type names of other local *.py files into my comments. It seems that autocomplete kicks in at the dot in the file name typed in comments.
So the fix I now use is to just deactivate autocomplete preference setting while I'm adding blocks of comments.[/color]

---

