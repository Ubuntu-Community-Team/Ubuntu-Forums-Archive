---
title: "Why does ustring exist?"
date: 2010-12-05
forum: Programming Talk
---

### Post by DarkAmbient on 2010-12-05
Im rather new to gtkmm. Since I've started I've gotten a bit curious why you need (Glib's) ustring. 

To me, ustring seems to work alot like and looks alot like (std's) string. So why doesn't gtk+ make use of std::string?

Hopefully this isn't one of those dumb questions. ;-)
Cheers ~ R

---

### Post by SledgeHammer_999 on 2010-12-05
From the Glib::ustring [docs](http://library.gnome.org/devel/glibmm/unstable/classGlib_1_1ustring.html)

> **Detailed Description**

Glib::ustring has much the same interface as std::string, but contains Unicode characters encoded as UTF-8.

**About UTF-8 and ASCII**

    The standard character set ANSI_X3.4-1968 -- more commonly known as ASCII -- is a subset of UTF-8. So, if you want to, you can use Glib::ustring without even thinking about UTF-8. 

    Whenever ASCII is mentioned in this manual, we mean the real ASCII (i.e. as defined in ANSI_X3.4-1968), which contains only 7-bit characters. Glib::ustring can not be used with ASCII-compatible extended 8-bit charsets like ISO-8859-1. It's a good idea to avoid string literals containing non-ASCII characters (e.g. German umlauts) in source code, or at least you should use UTF-8 literals. 

    You can find a detailed UTF-8 and Unicode FAQ here: [http://www.cl.cam.ac.uk/~mgk25/unicode.html](http://www.cl.cam.ac.uk/~mgk25/unicode.html)

**Glib::ustring vs. std::string**

    Glib::ustring has implicit type conversions to and from std::string. These conversions do not convert to/from the current locale (see Glib::locale_from_utf8() and Glib::locale_to_utf8() if you need that). You can always use std::string instead of Glib::ustring -- however, using std::string with multi-byte characters is quite hard. For instance, std::string::operator[] might return a byte in the middle of a character, and std::string::length() returns the number of bytes rather than characters. So don't do that without a good reason. 

    In a perfect world the C++ Standard Library would contain a UTF-8 string class. Unfortunately, the C++ standard doesn't mention UTF-8 at all. Note that std::wstring is not a UTF-8 string class because it contains only fixed-width characters (where width could be 32, 16, or even 8 bits).

But I can't seem to understand how to handle unicode/encodings in C++...

---

### Post by DarkAmbient on 2010-12-05
A'right, thank you. To be honest I still don't fully get it. But it's due to my lack of knowledge on encoding I guess. Should probably read up some on that first. Never really been bothered by it, from what I remember.

---

### Post by worksofcraft on 2010-12-05
Unicode supports all the characters from all the languages on the world and so there are many more than you can encode in a single byte.

Some clever guy invented utf-8 which is fully compatible with 7 bit ASCII but then uses multi byte sequences (with the 8th bit set) to encode ALL the unicode characters. You can actually store these sequences in std::string but if you then try indexing characters in the string it will get it wrong and maybe return a single byte out of a multi byte sequence.... so Gtk::ustring has fixed that :)

Try it with a non ascii character and see for yourself... here is one that you can cut and paste and test:

[php]
printf("strlen(€)=%d\n", strlen("€"));
[/php]

---

### Post by DarkAmbient on 2010-12-10
> **worksofcraft said:**
> Unicode supports all the characters from all the languages on the world and so there are many more than you can encode in a single byte.

Some clever guy invented utf-8 which is fully compatible with 7 bit ASCII but then uses multi byte sequences (with the 8th bit set) to encode ALL the unicode characters. You can actually store these sequences in std::string but if you then try indexing characters in the string it will get it wrong and maybe return a single byte out of a multi byte sequence.... so Gtk::ustring has fixed that :)

Try it with a non ascii character and see for yourself... here is one that you can cut and paste and test:

[php]
printf("strlen(€)=%d\n", strlen("€"));
[/php]

Ah almost missed your response. Thanks for your explanation, easy to follow. :-)

That line code gave me "strlen(€)=3". strlen is length of the string right? (just woke up, so I'm a'lil slow)  Is it possible to tell the compiler to change encoding (temporary or permanent even?) to understand both utf-8 and the encoding € is in at the same time?

---

### Post by Vaphell on 2010-12-10
strlen treats all strings as arrays of 1byte chars and returns number of bytes occupied by the string. Single non-ascii utf8 char has 2 or more bytes

[http://en.wikipedia.org/wiki/UTF-8](http://en.wikipedia.org/wiki/UTF-8)
as you can see euro is 3byte long

character '&#8364;' = code point U+20AC
= 00100000 10101100
&#8594; 11100010 10000010 10101100
&#8594; hexadecimal E2 82 AC

simply don't use non-ascii in your code (const strings should be fine) and if you need to work with non-ascii strings use a suitable class for them. There is no way around it.

---

### Post by DarkAmbient on 2010-12-13
Thanks for clarifying Vaphell. In the future I think I'll rather stay away from non-ascii strings. (Unless I really can't avoid "them", that is) But it seems like things could get more or less complicated, working with 'em.

---

