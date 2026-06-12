---
title: "Need a library to read configuration files on C++"
date: 2008-11-17
forum: Programming Talk
---

### Post by jucas_lo on 2008-11-17
Hi!
I'm searching for a good stable and up-to-date library to read configuration and settings from a file (instead of using defines all over the place!)

I've found libconfig0 in the repositories but it is a C library and i'd like to use a real C++ library....

any help would be appreaciated!!!

thx!!

---

### Post by nvteighen on 2008-11-17
What are you trying to do, may I ask? Configuration files in UNIX/Unix-like systems are text files, so you should able to open them without hassle... Maybe this library has better parsing abilities, but I just don't see the need of such a library besides that (which could easily be replaced by using Perl... but that's another story).

Or am I missing the point?

---

### Post by mihaiv on 2008-11-17
Use glib GKeyFile. glib is written in C but you have a C++ wrapper for it (glibmm).

---

### Post by kknd on 2008-11-17
If your config is very simple, implemente your own parser.
Othrwise, I recommend you to use Lua, and then your configuration can be programmed =).

A sample configuration:

[config.lua]
```
general = {
    name = "My name",
    blabla = 10
}

optional = {
    sadd = 90,
    other = { a = 10, b = 20}
}
```

And etc.

---

### Post by issih on 2008-11-17
Be like me and pointlessly write an XML parser and validation engine... I have no idea why I did it, so don't ask, it seemed sensible at the time.

---

### Post by jucas_lo on 2008-11-18
Thanks for your reply mihaiv!!!

I finally used GKeyFile from gtkmm, I used it all day and it was exactly what i needed...

thanks!

ps. and dont worry issih that was my next step so you're not the only one ;-)

---

### Post by tanderson on 2008-11-19
I used a project involving xml and I used codesynthesis xsd compiler. I was really impressed!

---

### Post by issih on 2008-11-19
Using someone else's already developed library.... less of your sensible rational advice :)

---

