---
title: "wrong locale with language"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by owiknowi on 2011-10-16
just installed ubuntu 10.04.3_64 us again (had to... my bad...)
during installation i'm asked for the preferred system language (english) and the time zone (amsterdam, netherlands).

one could expect that thus final system language is english and locale nl_NL (metric, €, . istead of , and time a.s.o.), not so.

in language support only english and english speaking locations are shown. installing a lot extra nl/dutch packages, except for system language, which causes dual language menu's.

even: $ sudo locale-gen nl_NL.UTF8 (or iso8859) doesn't change a thing.

how do i set the right locale when using english as system language?

---

### Post by like coffee on 2011-10-16
I'm using english language with norwegian locale.
I changed the locale in system settings>language support>regional formats after installing.

Edit: sorry this is for 11.10 reading fail.

---

### Post by owiknowi on 2011-10-16
also in 10.04.3 the "language support" section "text" offers those possibilities, but alas...

---

### Post by owiknowi on 2011-10-20
madjr came up with a link to [a working solution](http://ubuntuforums.org/showthread.php?t=1864750).

make sure though that /user/share/i18n/ is up to date to, so probably best to read the whole post.

---

