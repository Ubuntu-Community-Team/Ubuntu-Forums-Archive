---
title: "How to access file type association information?"
date: 2011-08-18
forum: Programming Talk
---

### Post by Zapster on 2011-08-18
Hello,

I want to write an application which needs access to the file type association in ubuntu. E.g. get a list of all installed applications which are able to play mp3 song. I am not quite sure which part of ubuntu is responsible for this. Is it some freedesktop.org standard or a gnome thing? Is it possible to access this information using glib or any other "default" api?

Additionally, is it possible to get the information present in the .desktop files (name, icon, exec, ...) for these applications?

Many thanks in advance,

zap

PS: I am planning to use python but any language is just fine.

---

### Post by shashanksingh on 2011-08-18
There is a file command I know in bash.

file <path to fle>

this gives some info about the type, even if it is without an extension.

Im not sure if this is what you want, but this may just give some clue.

---

