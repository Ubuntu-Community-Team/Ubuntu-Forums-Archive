---
title: "ruby, rails and ubuntu"
date: 2011-11-14
forum: Programming Talk
---

### Post by F.G. on 2011-11-14
hi folks,

I'm trying to setup an environment to program ruby on rails in. it seems that there is mess of information about this, but much of it is outdated or wrong.

where i'm at is this:

Ive got ruby 1.8.7, rails 2.3.5, i've also got Netbeans 6.9 + ruby & rails plugin, sublime text 2 and Eclipse installed.

here are the issues:

on Sublime text 2 the IDE won't load at all, it gives me a segfauly eg:
```
/usr/bin/sublime-text-2: line 2:  5967 Segmentation fault      /usr/lib/sublime-text-2/sublime_text $*

```

on Netbeans i when i try to make a ruby on rails app it says i don't have rails install (but i do). if i click install then it asks me for my root password, which i duly give it, but it comes up as the wrong password.

Eclipse I haven't really had a proper stab at sorting out, but i feel that this should all be alot easier to configure.

so, does anyone have any hand-held solutions for installing and configuring a ruby on rails development environment? 

any help will be much appreciated.

---

### Post by F.G. on 2011-11-14
update:  new version of sublime released earlier today works fine, and the bug has been fixed.

key to getting ruby and rails and rake all installed is to follow a tutorial to install RVM (ruby version manage?) and it's pretty helpful, to get the most updated versions from github.

i've yet to actually make a rails app, but hopefuly soon i'll be there.

---

