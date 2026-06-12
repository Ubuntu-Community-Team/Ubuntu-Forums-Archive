---
title: "[SOLVED] Aptitude vs apt-get"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by BGFG on 2008-07-10
Hi All,
I've bee googling aptitude vs apt-get and havn't been able to find a recent 'vs' discussion for Hardy Heron. I just want to know if the two are now on equal ground with the advent of Hardy or does one or the other still hold the advantage in terms of package management and dependancies ?

Till now I've been using apt-get primarily and havn't really had problems. But i'd still like your opinions on the best way.

---

### Post by SunnyRabbiera on 2008-07-10
both have remained the same, no big changes...
I doubt things will alter, as in their current state both do a great job at what they do.
Apt is a great package manager on its own, and aptitude makes a great front end for it.

---

### Post by konungursvia on 2008-07-10
Used to be that apt-get managed dependencies less carefully than aptitude, but now they are both almost flawless.

---

### Post by BGFG on 2008-07-10
Cool, thanks guys. i'll try out aptitude but i think i'm already an apt guy.

---

### Post by prolapse on 2008-07-11
I've been using aptitude exclusively since I installed hardy, what would the consequences of starting to use apt-get all the time now be?

The primary reason I want to know this is because i don't think there is an aptitude equivilant to "apt-get build-dep *[package name]*" but i don't want to create any issues for myself later on by mixing the two.

---

### Post by jpeddicord on 2008-07-11
> **prolapse said:**
> I've been using aptitude exclusively since I installed hardy, what would the consequences of starting to use apt-get all the time now be?

The primary reason I want to know this is because i don't think there is an aptitude equivilant to "apt-get build-dep *[package name]*" but i don't want to create any issues for myself later on by mixing the two.

There should be no problem using apt-get. Like previous posters have said, apt-get and aptitude have become almost identical for managing packages. The only major difference is that aptitude will automatically install "recommended" packages, while apt-get only installs "depended" packages. So with aptitude you might get a bit more bulk/features.

---

### Post by sdennie on 2008-07-11
To add to what jacobmp92 said, aptitude also doesn't mind when you try to install a package that doesn't exist.  For instance:

```

sudo aptitude install not_a_real_package a_real_package

```

Will still install a_real_package.  Whereas:

```

sudo apt-get install not_a_real_package a_real_package

```

Will simply fail.  Whether or not that's desirable behavior is up to you (I don't think it is).

---

