---
title: "Set doxygen output encoding..."
date: 2007-07-17
forum: Programming Talk
---

### Post by tomane on 2007-07-17
Hello everyone,
I'm using doxygen to build the documentation  of a C project that I'm working on.
It has been working fine given my doxygen experience, the only annoyance being that the generated html has a wrong header with the character encoding <meta> set to ISO8859-1 instead of UTF8. This makes the html files look ugly because I'm portuguese and the docs contain a *lot* of accented characters :(

I'm using kedevelop 3.4.0 and doxygen version is 1.5.1 on feisty
I haven't found any workaround for this so far...
Any ideas?

Cheers,
--to

---

### Post by tomane on 2007-07-24
No ideas? :(
I thought this would be something simple to tackle...

--Qin

---

### Post by orzetto on 2007-07-27
Hi Tomane,
I found this while looking for a solution to the same problem (in my case the language is Norwegian):
[http://linuxfr.org/~liberf0rce/24886.html](http://linuxfr.org/~liberf0rce/24886.html)

The article is in French, I suppose a Portuguese can read most of it... anyway, it says that Doxygen 1.5.2 supports Unicode, but I am unsure as to how I can install it. On Feisty the present version is 1.5.1 (which is also the one you and I are using).

I am a relative newbie to Debian-like distros (myself, I run Kubuntu at work), and I am more used to Gentoo packaging (at home). Do you happen to know how to mark 1.5.2 (if it is in the repositories at all), or how to add it locally, or where I can find some documentation?

I know I could just compile it from source, but I would prefer to use apt-get so the system stays clean (I hate to have to keep the configured source around so I can run "make uninstall" on them when I upgrade).

---

### Post by tomane on 2007-07-27
Hi,
thanks for the pointer, it seems to address our problem.
If I chose to display the page using UTF8 encoding things are displayed fine. The problem is that the HTML header declares ISO8859 and the browser is fooled into the wrong encoding. Is there any way to trick doxygen into producing the encoding <meta> with UTF8?

I'm not experienced with package management, but if there is one, we can manually install a more recent package for debian and it should be fine.
Cheers,
--Qin

---

### Post by orzetto on 2007-07-27
A possibility, however kludgy, is to use the method I am using now... simply run sed after doxygen:

```
doxygen Doxyfile
sed -i -e "s/charset=iso-8859-1/charset=utf-8/g" html/*html
```

It is quite ugly, but gets the work done.
You could probably obtain a similar result by running recode and changing the text files from UTF-8 to Latin-1 (I suppose Portuguese is in Latin-1 as well).

---

### Post by tomane on 2007-07-27
That's a great Idea, thanks for the tip!

Cheers,
--Qin

---

### Post by prabyan on 2009-06-10
You can edit doxyfile (configuration file) and replace UTF-8 to ISO-8859-15.

---

