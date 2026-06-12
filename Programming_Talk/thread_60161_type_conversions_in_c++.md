---
title: "type conversions in c++"
date: 2005-08-26
forum: Programming Talk
---

### Post by robert crowther on 2005-08-26
Thought I'd poke my nose into xml (within c++). I'm using,

libxml2

Writing simple xml files is ok, reading them is ok, but I'm retrieving them into a variable of type,

xmlChar*

which is libxml2's own type, described as,

 "a null terminated sequence of utf-8 characters. And only utf-8! You need to convert strings encoded in different ways to utf-8 before passing them to the API. This can be accomplished with the iconv library for instance."

Can anyone suggest how to get these into a string type? Or know how this is usually done?  There may be some hint in the libxml2 documentation, or even a routine, but I've found the extensive site rather bewildering. I'd like something naturally Ubuntu, but if there isn't anything, I'll follow your lead.


While I'm here (if you have an answer to the last, you can probably help here too)

Since I'm writing for GUI's, I'm doing quite a few character/number type casts. These are very simple (eg. "900" to 900), so rather than work securely, I wrote a nasty little routine. Could anyone point me towards some appropriate libraries?    



Robert

---

### Post by LordHunter317 on 2005-08-26
Umm, libiconv, as mentioned, will be able to  give you a char* in whatever locale you want, which you can construct a std::string from.

---

### Post by thumper on 2005-08-29
[QUOTE=robert crowther]Since I'm writing for GUI's, I'm doing quite a few character/number type casts. These are very simple (eg. "900" to 900), so rather than work securely, I wrote a nasty little routine. Could anyone point me towards some appropriate libraries? [/QUOTE]
I find the best the [boost](http://www.boost.org) [lexical_cast](http://www.boost.org/libs/conversion/lexical_cast.htm).

```
std::string amount("125.25");
double d = boost::lexical_cast<double>(amount);
std::string s = boost::lexical_cast<std::string>(d);

```

---

