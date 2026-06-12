---
title: "accented characters in source"
date: 2010-08-14
forum: Programming Talk
---

### Post by worksofcraft on 2010-08-14
According to [http://www.gnu.org/software/gettext/FAQ.html#nonascii_strings](http://www.gnu.org/software/gettext/FAQ.html#nonascii_strings)
the POSIX standard demands we only use ASCII characters in strings in our C and C++ source code.

This is a bit a nuisance for people who want to program output in foreign languages that do use accents, but the alleged reason is that compile time and run time character coding might not match.

Now more modern languages like Java don't have that problem because they specify that it will all be coded in UTF-8, a super set of ASCII that should allow us to use just about any glyph from any language on our planet.

However many people may still be operating with older ISO character code pages because currently Linux does not default to UTF-8 :shock:

Like me, you may want to change these defaults, and here is how I changed mine:

```

In file /usr/share/i18n/SUPPORTED you will find all
the recognized locales with entries like:

en_US.UTF-8 UTF-8
en_US ISO-8859-1
en_US.ISO-8859-15 ISO-8859-15

as you can see, unless otherwise specified English speaking
US residents will be using ISO-8859-1... watch:

$> sudo locale-gen en_US
Generating locales...
  en_US.ISO-8859-1... done
Generation complete.

I don't want that, so I changed it as follows:

en_US UTF-8
en_US.ISO ISO-8859-1
en_US.ISO-8859-15 ISO-8859-15

```

and now
$> export LANG=en_US

selects UTF-8 character encoding and I can put any characters I like in my source code and get them out again in my output :)

Note: What I don't know is if there is any disadvantage to doing this :oops: so do post your thoughts, thanks :)

---

### Post by worksofcraft on 2010-08-16
Oh well that solved the problems in C and C++, but I find a different set of problems with Python!

```

#!/usr/bin/python
# -*- coding: UTF-8 -*-
import gettext
gettext.bindtextdomain('uber', '/home/cjs/Desktop/uber')
gettext.textdomain('uber')
_ = gettext.gettext
# output a string with a non ascii character in it
print _('UTF-8 Über Ascii')

```

It works fine, and sure why shouldn't I be able to use a foreign word in my output?!

However say I want to translate it into another language...
When called from Python, gettext flatly refuses, whereas it works from C and C++!

I thought it was supposed to be the other way round and work fine from languages that DO support non ascii text?! :confused:

Sigh - Has anyone managed to use translations with Python programs that are not native English?

p.s.do you think people would read my threads if I made the title more interesting?
Like what if I called this one "Über annoying in Python!" Oh yesah and I'm called worksofcraft cuz before I decided to study Linux I had an arts and craft shop... and works-of-art are all arty-pharty but crafts take skill, dedication & perseverance ;)

---

