---
title: "Natural language Java class? (Need alphabet length)"
date: 2011-01-18
forum: Programming Talk
---

### Post by noah++ on 2011-01-18
Hi,

In an introductory CS course, I am writing a Java program that operates on the letters of the alphabet. To avoid using a magic number like *ALPHABET_LENGTH=26*, I thought it would be neat to obtain the right alphabet length based on the language of the local system. Does Java give me a way to extract that information, one that's reliable across Windows, OS X and Linux?

---

### Post by unknownPoster on 2011-01-18
This may not be exactly what you want, but this simple Java class will tell you the system locale language.

```

[COLOR=#7f0055]**class **[/COLOR][COLOR=#000000]SystemLocale[/COLOR]
[COLOR=#000000]{[/COLOR]
[COLOR=#ffffff]  [/COLOR][COLOR=#7f0055]**public static void **[/COLOR][COLOR=#000000]main(String[] args) [/COLOR]
[COLOR=#ffffff]  [/COLOR][COLOR=#000000]{[/COLOR]
[COLOR=#ffffff]    [/COLOR][COLOR=#000000]String locale = System.getProperty([/COLOR][COLOR=#2a00ff]"user.language"[/COLOR][COLOR=#000000]);[/COLOR]
[COLOR=#ffffff]    [/COLOR][COLOR=#000000]System.out.println([/COLOR][COLOR=#2a00ff]"The Locale of the system is: "[/COLOR][COLOR=#000000]+locale);[/COLOR]
[COLOR=#ffffff]  [/COLOR][COLOR=#000000]}[/COLOR]
[COLOR=#000000]}

```
[/COLOR]

---

### Post by worksofcraft on 2011-01-18
soz multi post

---

### Post by worksofcraft on 2011-01-18
soz double post

---

### Post by worksofcraft on 2011-01-18
lol I'm really sorry about this - I got "this web page is unobtainable" and then when I look back there are oodles of copies... IDK what happened here :shock:

---

### Post by worksofcraft on 2011-01-18
> **noah++ said:**
> Hi,

In an introductory CS course, I am writing a Java program that operates on the letters of the alphabet. To avoid using a magic number like *ALPHABET_LENGTH=26*, I thought it would be neat to obtain the right alphabet length based on the language of the local system. Does Java give me a way to extract that information, one that's reliable across Windows, OS X and Linux?



There are functions like isLetter but short of testing all the possible Unicode code points and counting the ones that are letters AFIK there is no way to get that also you will find that the alphabetical sequence that different languages use is not necessarily ordered the same as the numerical code points.

IMO the whole thing is kind of ill conceived... more like something that crawled out of a swamp of primordial plankton than a design really.... but oops (slaps wrist) back to the topic:

My advice would be to provide a translatable string containing the alphabet and then different locales can put their own alphabets in there as a translation in whatever sequence they want and you can get it's length with alphabet.length()

---

### Post by noah++ on 2011-01-18
Thanks. With such complications ahead, I think I'll stick with the magic number.

> **worksofcraft said:**
> lol I'm really sorry about this

Yeah, that happened to me too at about the same time. Posting seemed to fail, but then duplicates appeared later.

---

### Post by worksofcraft on 2011-01-18
> **noah++ said:**
> Thanks. With such complications ahead, I think I'll stick with the magic number.



Yeah, that happened to me too at about the same time. Posting seemed to fail, but then duplicates appeared later.

It's not actually that hard, I haven't programmed in Java for 15 years never did much in it to start with TBH. Only recently picked up C++ again, so you will have to excuse my poor syntax but all you have to do is define something like:

```

String alphabet = "abcdefghijklmnopqrstuvwxyz";

```

Then one day in the future if you ever do want to support other alphabets in other locales you can read all about the gettext package and how to make your string translatable... into any other locale.

You can also already guess at methods you might one day create to allow the alphabetical order to be defined by said string too ;)

---

### Post by nvteighen on 2011-01-19
Hm... it depends on what you're doing.

The "magic number" approach is tricky, because you're assuming that all alphabets are iterable like the Latin alphabet. I mean: that you'll be able to generate the alphabet by starting from a certain ASCII/Unicode code and then happily iterating up to the last code... But this assumption should be confirmed: what if some alphabet places diacritics or special characters in the middle of letters?

I'd go for the alphabet string too, regardless of whether you want to internationalize this or not. There are several advantages on defining the alphabet's order the way you like, e.g. depending on what your intentions are, you can decide whether 'â' is one "character" or the combination of 'a' and '^'... or whether '^' should be considered part of the alphabet at all.

---

