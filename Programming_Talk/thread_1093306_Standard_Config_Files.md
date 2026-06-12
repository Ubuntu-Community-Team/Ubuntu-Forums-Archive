---
title: "Standard Config Files"
date: 2009-03-11
forum: Programming Talk
---

### Post by sq377 on 2009-03-11
Is there a standard library (for c) to handle parsing config files?  I've found a few, but it just seems redundant that almost every app out there writes their own parser.  I'm writing an app where I'll need one, and I'm toying with the idea of using XML.  Is there a reason I shouldn't?  If so, what should I be using?

Thanks

---

### Post by stroyan on 2009-03-11
My first thought is ```
apt-cache search xml | grep -- -dev | grep -vi c++
```

(Yes.  I think in CLI commands.) ;)

---

### Post by sq377 on 2009-03-11
I already know i'd use libxml2-dev, but I haven't seen many apps use xml for the config file.  Just curious why that is.

---

### Post by cabalas on 2009-03-11
I just did a quick apt-cache search and came up with two possibilities 

[dot.conf]("http://www.azzit.de/dotconf/") - which is a c library

[libclaw]("http://libclaw.sourceforge.net/index-en.html") - which is c++ library which provides a class for config files.

Also in regards to why people don't use xml much for config files I think it is just because it's too much for what is generally just a file of name - value pairs.

---

### Post by nvteighen on 2009-03-11
> **sq377 said:**
> I already know i'd use libxml2-dev, but I haven't seen many apps use xml for the config file.  Just curious why that is.
Well, Firefox does...

---

### Post by Reiger on 2009-03-11
Firefox is a slightly out-of-the-ordinary app though. ;)

Anywho a link (debate) about the issue with its pros & cons + alternatives: [http://cafe.elharo.com/xml/plain-text-config-files-are-confusing/](http://cafe.elharo.com/xml/plain-text-config-files-are-confusing/)

---

### Post by sujoy on 2009-03-24
i guess yaml is a lot simpler.
isnt there a standard config parser for C? or do we have to use other libraries?

---

### Post by kknd on 2009-03-24
You can use Lua scripts as config files, since Lua is very small.

---

