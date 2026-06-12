---
title: "MSEide not work"
date: 2007-03-28
forum: Programming Talk
---

### Post by Attid on 2007-03-28
i update ubuntu from 6.06 to 6.10
when i run mseide : 

./mseide
An unhandled exception occurred at $080DC65F :
egui : Invalid inputmanager tinternalapplication .
$080DC65F
$080DC78A
$0807727F
$08064113
$081AEA28
$08059B1D
$0804B85E 

my LANG=ru_RU.utf8 but if i run with locale ru_RU.win1251 or us_US all work .

this problen has only ubuntu  
[sample]("http://thread.gmane.org/gmane.comp.compilers.free-pascal.general/7139/focus=7203")

why my locale don`t get some "input manager"?

---

### Post by Attid on 2007-04-15
it but like it
[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/68594](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/68594)

**
It is bug in /usr/share/X11/locale/locale.dir
For work in ru_RU.utf8 locale it is necessary to replace lines
ru_RU.UTF-8/XLC_LOCALE ru_RU.UTF-8
with lines
en_US.UTF-8/XLC_LOCALE ru_RU.UTF-8

---

