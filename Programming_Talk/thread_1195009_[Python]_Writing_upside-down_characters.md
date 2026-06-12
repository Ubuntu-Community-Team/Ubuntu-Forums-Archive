---
title: "[Python] Writing upside-down characters"
date: 2009-06-23
forum: Programming Talk
---

### Post by unutbu on 2009-06-23
I would like to make a command-line python program to translate [a-zA-Z] strings into their "upside-down" equivalent:

&#729;&#647;u&#477;l&#592;&#652;&#305;nb&#477; "u&#653;op-&#477;p&#305;sdn" &#633;&#305;&#477;&#613;&#647; o&#647;u&#305; s&#387;u&#305;&#633;&#647;s [z-&#592;z-&#592;] &#477;&#647;&#592;lsu&#592;&#633;&#647; o&#647; &#623;&#592;&#633;&#387;o&#633;d uo&#613;&#647;&#654;d &#477;u&#305;l-pu&#592;&#623;&#623;o&#596; &#592; &#477;&#670;&#592;&#623; o&#647; &#477;&#670;&#305;l plno&#653; &#305;

I used this to list all the utf8 characters:
[PHP]
#!/usr/bin/env python
codec='utf8'
for num in range(32,65536):
    achr=unichr(num)
    print("'':%s, # %s"%(num,achr.encode(codec)))
[/PHP]

Using that list, I was able to come up with this:
[PHP]
#!/usr/bin/env python
# -*- encoding: utf-8 -*-

import sys
rot180={
    'a':592, # &#592;
    'b':5227, # &#5227;
    'd':1088, # &#1088;
    'e':600, # &#600;
    'h':1063, # &#1063;
    'l':645, # &#645;    
    'p':599, # &#599;
    'r':633, # &#633;
    't':647, # &#647;
    'v':8743, # &#8743;
    'w':653, # &#653;
    'y':654, # &#654;
    'A':5578, # &#5578;
    'B':5626, # &#5626;
    'C':390, # &#390;
    'D':5613, # &#5613;
    'E':8707, # &#8707;
    'O':2848, # &#2848;
    'R':5512, # &#5512;
    'T':639, # &#639;
    'U':1055, # &#1055;
    'V':923, # &#923;
    '3':5620, # &#5620;
    }

input_str=sys.argv[1]
print(''.join([unichr(rot180.get(achr,ord(achr))).encode('utf8') for achr in input_str]))
[/PHP]
In so far as it goes, it works okay:
```

% upsidedown.py Howdy
Ho&#653;&#1088;&#654;
```

The problem is, I don't have a complete set of upside-down characters.

According to [http://www.sevenwires.com/play/UpsideDownLetters.html](http://www.sevenwires.com/play/UpsideDownLetters.html), the characters come from the "Latin Extended" and "International Phonetic Alphabet" character sets.

I've looked these character sets here: file:///usr/share/doc/python2.5/html/lib/standard-encodings.html but couldn't find them.

Do you know what encoding I should be using to access upside-down characters?

---

### Post by simeon87 on 2009-06-23
I don't think that every arbitrary character has an upside-down equivalent in some character set so I think the best you can do is to manually create a mapping between characters and their upside-down equivalent.

For example, in the source of the webpage that you mentioned, it also uses a table to lookup the upside-down character.

---

### Post by unutbu on 2009-06-23
Thanks simeon87. Indeed, I don't mind making a dictionary by hand, even though it feels icky :)

I've only made a cursory run through the utf-8 character set to build the rot180 dictionary as it stands so far. 

The problem is, I'm not sure I'm going to find a complete set of upside down characters even for [a-z] in utf8.

[http://www.sevenwires.com/play/UpsideDownLetters.html](http://www.sevenwires.com/play/UpsideDownLetters.html) demonstrates that javascript can do it. I'd like to be able to do it in Python.

Should I just keep looking through my list of utf8, or am I looking in the wrong place?

---

### Post by unutbu on 2009-06-23
Oh, I'm so silly. The javascript code is visible if you click View>Page Source... LOL

---

### Post by unutbu on 2009-06-23
Here is the finished script. It can do everything [http://www.sevenwires.com/play/UpsideDownLetters.html](http://www.sevenwires.com/play/UpsideDownLetters.html) can do, but from the command-line.
(I also added a few capital letters.)

Many thanks to simeon87 for his help.
 
[PHP]#!/usr/bin/env python
# -*- encoding: utf-8 -*-
import sys

__usage__='''
upsidedown.py "The quick brown fox jumps over the lazy dog."
&#729;&#387;op &#654;z&#592;&#645; &#600;&#613;&#647; &#633;&#600;&#652;o sd&#623;u&#638; xo&#607; u&#653;o&#633;q &#670;&#596;&#305;uq &#600;&#613;&#65248;
'''

rot180={
    'a' : u'\u0250', # &#592;
    'b' : u'q',
    'c' : u'\u0254', # &#596;
    'd' : u'p',
    'e' : u'\u0258', # &#477;
    'f' : u'\u025F', # &#607;
    'g' : u'\u0183', # &#387;
    'h' : u'\u0265', # &#613;
    'i' : u'\u0131', # &#305;
    'j' : u'\u027E', # &#638;
    'k' : u'\u029E', # &#670;
    'l' : u'\u0285', # &#645;    
    'm' : u'\u026F', # &#623;
    'n' : u'u', # u
    'p' : u'd',
    'r' : u'\u0279', # &#633;
    't' : u'\u0287', # &#647;
    'u' : u'n',
    'v' : u'\u028C', # &#652;
    'w' : u'\u028D', # &#653;
    'y' : u'\u028E', # &#654;
    '.' : u'\u02D9', # &#729;
    '[' : u']',
    '(' : u')',
    '{' : u'}',
    '?' : u'\u00BF', # ¿
    '!' : u'\u00A1', # ¡
    "\'" : u',', 
    '<' : u'>',
    '_' : u'\u203E', # &#8254;
    '"' : u'\u201E', # &#8222;
    '\\' : u'\\',
    ';' : u'\u061B', # &#1563;
    '\u203F' : u'\u2040', # &#8255; --> &#8256;
    '\u2045' : u'\u2046', # &#8261; --> &#8262;
    '\u2234' : u'\u2235', # &#8756; --> &#8757;
#     'A':u'\u15CA', # &#5578; (viewable in emacs, but not in terminal)
#     'B':u'\u15FA', # &#5626; (viewable in emacs, but not in terminal)
    'C':u'\u0186', # &#390; (viewable in emacs, but not in terminal)
#     'D':u'\u15ED', # &#5613; (viewable in emacs, but not in terminal)
    'E':u'\u2203', # &#8707; (viewable in emacs, but not in terminal)
#     'N':u'\u2d4d', # &#11597; (viewable in terminal, but not in emacs)
#     'O':u'\u0B20', # &#2848; (viewable in emacs, but not in terminal)
#     'R':u'\u1588', # &#5512; (viewable in emacs, but not in terminal)
    'T':u'\uFEE0', # &#65248;
    'U':u'\u041F', # &#1055;
    'V':u'\u039B', # &#923;
#     'V':u'\u2d37', # &#11575; (viewable in terminal, but not in emacs)
#     'Y':u'\u2d43', # &#11587; (viewable in terminal, but not in emacs)
#     '2':u'\u2D52', # &#11602; (viewable in terminal, but not in emacs)
#     '3':u'\u15F4', # &#5620; (viewable in emacs, but not in terminal)
    }

input_str=sys.argv[1]
print(''.join(reversed([rot180.get(achr,achr) for achr in input_str])))
[/PHP]

If anyone can explain why certain unicode characters are viewable in emacs, but not from a gnome-terminal, and vice versa, I'd really like to know. (See the commented-out source code for examples.)

---

