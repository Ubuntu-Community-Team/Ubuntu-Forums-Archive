---
title: "locales"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by owiknowi on 2011-10-17
in what file are the settings for the locales (not the system language but for time and date format, currency, metrics, a.s.o.) stored?

and can i edit/change those setting manually or do i first have to install extra packages in oder to make that work?

btw. it's for u10.04.3_64 us (language english, time zone netherlands/amsterdam).
i can't change these settings in "system / administration / language support / text"

---

### Post by gsmanners on 2011-10-17
I think you might need dconf-editor for that (in the dconf-tools package). The setting would be system/locale (I think).

---

### Post by owiknowi on 2011-10-17
the locales for nl just seem to be missing? installed language-support-nl too, but nope.

where are the localizations stored (not the system language)?

btw. installing the complete language (gnome) packs, leaves me with a dual-language system...

---

### Post by owiknowi on 2011-10-18
urgent

i really need to set the locale to netherlands/dutch on my english system ubuntu 10.04.3_64 installation.
now i get problems with wrong values for time, currency, metrics, etc.

installing all dutch language packs, causes mixed menus, appearing in two languages.

so: where do i set the right locale, by hand or command line, if system/administration/language support/text doesn't work?

thanks for any help!

---

### Post by owiknowi on 2011-10-18
so i've taken the hard way and installed, and purged and reinstalled all dutch translations and removed all english translations.
thus, leaving the rather unwilling system a bit dazed & confused (like i am from the lack of answers on this question...)

the command "$ locale" showed that the system just made up something from the available bunk still left in /usr/share/i18n/locales (see attachment). it picks one at random afaik.
and i may add that all dutch localizations/translations were installed! but they just won't show up.

is this a build in feature from ubuntu 10.04.3_64 or...

---

### Post by owiknowi on 2011-10-20
madjr came up with a link to [a working solution](http://ubuntuforums.org/showthread.php?t=1864750).

make sure though that /user/share/i18n/ is up to date to, so probably best to read the whole post.

---

