---
title: "transition to Glib::ustring"
date: 2010-09-27
forum: Programming Talk
---

### Post by worksofcraft on 2010-09-27
For internationalization I wanted to start using the Glib::ustring class instead of std::string because many functions will work correctly with utf-8.

Now currently my little test program localizes numbers as follows:
```

$> ./a.out 3210
length=40Val=3210 number = 3,210, financial = $ 32.10
$> export LANG=zh_CN.utf-8
$> ./a.out 3210
length=52Val=3210 number = &#19977;&#20336;&#20108;&#25342;, financial = &#21441;&#20336;&#36144;&#25342;

```

... so you see is working just fine with plain old C++ strings even though it's handling full utf-8 characters.

Now I got the impression the transition to Glib::ustring would make methods like length() work correctly but that otherwise the transition from std::string be quite painless so I bunged the following in my main include file:
```

#if 1
#include <glibmm/ustring.h>
#define string Glib::ustring
#else
#include <string> // STL strings
#endif

```

To be sure after recompiling, my output in English is working just as it did before, but my output for Chinese now reads:
```

$> ./a.out 3210
length=52Val=3210 number = ä¸&#8240;ä½°äº&#338;æ&#8249;¾, financial = åä½°è´°æ&#8249;¾

```

So my question is, whether this be teh right way to change over to use ustrings or do I need to do something else?

p.s. well actually the templates I'm using for Chinese numbers might not be quite right at the moment, but it's teh handling of utf-8 character set I'm trying to fix in this instance.

---

### Post by worksofcraft on 2010-09-28
Mystery solved... ustring has two push_back methods: one takes a char and the other a gunichar, so the poor thing was converting the utf-8 bytes into more utf-8 sequences as if they were unicode chars :D

So problem solved by casting them to char. Evidently it **is** that simple to switch from C++ string to Glib::ustring :D

---

### Post by worksofcraft on 2010-09-28
With all those unicode handling routines in Glib I thought it be a cinch to remove my home brewed utf-8 get and put routines, but somehow standard libraries never seem to do what you want:

```

gunichar g_utf8_get_char(const gchar *p);

```

To me it seems patently obvious that having extracted the gunichar one would want the pointer in the utf-8 string to be advanced passed whatever utf-8 coded bytes defined it and ready to get the next one :popcorn:

However this routine doesn't do that! Am I supposed to now add extra code to advance said pointer depending on how many utf-8 bytes were there? In that case it seems kind of pointless to use the library function in the first place because it's not that hard to assemble the unicode as I scan the utf-8

-sigh- :confused:

---

