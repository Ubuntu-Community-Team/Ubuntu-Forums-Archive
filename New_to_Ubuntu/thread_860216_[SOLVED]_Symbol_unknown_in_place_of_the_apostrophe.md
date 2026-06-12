---
title: "[SOLVED] Symbol unknown in place of the apostrophe symbol"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-07-15
Please see the screenshot, attached.

I get a symbol that looks like a little box, with 4 numbers in it like this:

00
92

This is always where the ' (apostrophe) symbol is supposed to be.

I searched the forum for the word apostrophe,and came up with only 1 post. That talked about foreign keyboards, and I'm in the U.S. and installed Hardy for the U.S., with a very plain vanilla selection of keyboard. (i.e., it should 'just work'.

Anybody know what this is about? How to fix it?

---

### Post by bumanie on 2008-07-15
Do you get this when browsing the internet or is it in open office?

---

### Post by LowSky on 2008-07-15
What font are you usind have you installed the microsoft core fonts?

---

### Post by Mark_in_Hollywood on 2008-07-15
1. I get the odd symbol in Firefox for surfing. Mostly, I guess if I paste something into openoffice I also get the 'box'.

2. Appearance/Preferences/Fonts seems to be mostly "Sans" -- see attached screenshot

---

### Post by annda on 2008-07-15
the problem is caused by non-Unicode character map used by the person who typed the text. what they have typed is actually not an apostrophe but a right single quote, which looks similar but is a different character.

more info:
[http://ubuntuforums.org/showthread.php?t=758508](http://ubuntuforums.org/showthread.php?t=758508)
[http://ubuntuforums.org/archive/index.php/t-486079.html](http://ubuntuforums.org/archive/index.php/t-486079.html)

---

### Post by Mark_in_Hollywood on 2008-07-15
> **annda said:**
> the problem is caused by non-Unicode character map used by the person who typed the text. what they have typed is actually not an apostrophe but a right single quote, which looks similar but is a different character.

more info:
[http://ubuntuforums.org/showthread.php?t=758508](http://ubuntuforums.org/showthread.php?t=758508)
[http://ubuntuforums.org/archive/index.php/t-486079.html](http://ubuntuforums.org/archive/index.php/t-486079.html)

I read the posts at both threads above. I now know what the problem is caused by:

Does anyone have a solution? They are not in either of the two URLs above.

---

### Post by pauper on 2008-07-15
Regarding Firefox.

You can change any website encoding here

View--Character Encoding--More Encodings--*


I would suggest you to check your "intl.charset.default" value.
 

Type in Location Bar field:

about:config

Now in Filter field:

intl.charset.default

Double-click on Value field. Set it to Western (ISO-8859-1)

"ISO-8859-1 is (according to the standards at least) the default encoding of
documents delivered via HTTP with a MIME type beginning with "text/"."
Source:
[http://en.wikipedia.org/wiki/ISO-8859-1#ISO-8859-1]("http://en.wikipedia.org/wiki/ISO-8859-1#ISO-8859-1")


An alternative way:

Edit--Preferences--Content--Fonts&Colors--Advanced

Set "Character Encoding": Western (ISO-8859-1), OK.


Now, any time you go to a website where charset is not defined, Firefox
will set it to your "intl.charset.default" value. 

But in any other case you'll have set it manually via 

View--Character Encoding...


For more settings check this link:
[http://kb.mozillazine.org/Category:Configuration]("http://kb.mozillazine.org/Category:Configuration")

---

### Post by Mark_in_Hollywood on 2008-07-15
ISO-8859-1 

is the set encoding in both the about:config

and the

Edit/Preferences/Content/Fonts & Colors/Advanced.

There was nothing to change.

---

### Post by pauper on 2008-07-15
Let me clear something up.

Western (ISO-8859-1) is default value of "intl.charset.default" in Firefox.
Just wanted to make sure that you have that value set.

Let's recap: if some page states that it's encoded in Central European
(Windows-1250) than Firefox will display it as Central European
(Windows-1250), as long as that encoding is supported; BUT if charset is
missing than Firefox will fallback to "intl.charset.default"--and you are at
the odds.

By having set "intl.charset.default" to ISO-8859-1, you have a better
chance to have those pages recognized properly since this standard is more
common on the AVERAGE than UTF-8. But it all DEPENDS on kinds of sites you
surf.

So you get garbled pages when two conditions are met:
1) charset is not defined;
2) charset differs from "intl.charset.default".

As I mentioned to fix that you need to go to View--Character Encoding... and
set it to a proper one by GUESSING. But this will work just for that page
only.

It's not Firefox at fault, but a particular web-disigner, who for some reason
didn't specify charset.

Try this link:
[URL="http://www.catb.org/~esr/jargon/html/index.html"]http://www.catb.org/~esr/jargon/html/index.html
[/URL]
Do you see Â symbols?

Go to View--Page Source and look in the header for charset value.

Now, try this link:
[URL="http://www.gnu.org/"]http://www.gnu.org/
[/URL]
Both of them are encoded in UTF-8.

---

