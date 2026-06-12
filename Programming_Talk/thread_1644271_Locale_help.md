---
title: "Locale help"
date: 2010-12-13
forum: Programming Talk
---

### Post by el_diablo on 2010-12-13
HI...
can anyone please tell me how to know the languages supported by CURRENT LOCALE.

I m trying to convert some application in HINDI

---

### Post by worksofcraft on 2010-12-13
There is an environment variable named "LANG" that the system uses.
e.g. on my computer at the command prompt:

```

$> echo $LANG
en_NZ.UTF-8

```

so I'm apparently using New Zealand English with utf-8 character encoding.

if I run my "hello world" application I get:
```

$> ./hello
Hello, world!
How are you?

```

I can change my language from the command line... e.g.:
```

$> export LANG=fr_CA.utf-8
$> ./hello
Salût le Québec!
Ça va, les gars?

```

but I only get translated text for the applications that I installed French translations for. Otherwise it still comes out in English... or whatever was built into the application.

You can download "internationalization.html" from [http://code.google.com/p/speaknumber/downloads/list](http://code.google.com/p/speaknumber/downloads/list) for some more explanations.

---

