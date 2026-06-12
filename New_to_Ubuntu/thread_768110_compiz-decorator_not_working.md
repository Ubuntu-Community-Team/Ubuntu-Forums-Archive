---
title: "compiz-decorator not working"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by krytol on 2008-04-26
Hi first post!!

I just upgraded from gutsy to hardy with a clean install but still using my old /home partition. Everything is ok but when i have compiz turned on, my windows decoration gets kinda strange. un focused windows have sometimes no or stripped decorations. now i have to use emerald to stop this from happening. How can i fix this problem? i like to use compiz-decorator more. Thanks in advance!

Screenshot attatched

---

### Post by blackbeastofaarrgh on 2008-04-29
having the same problem. any help would be nice.

---

### Post by Sjovan on 2008-04-29
are you shure that window deceration is checked in the compiz-manager? if it is... try --> emerald --replace & disown <--- in the terminal.

---

### Post by blackbeastofaarrgh on 2008-04-30
> **Sjovan said:**
> are you shure that window deceration is checked in the compiz-manager? if it is... try --> emerald --replace & disown <--- in the terminal.

emerald isn't installed on this machine. the decoration is there, just only on focused windows

---

### Post by blackbeastofaarrgh on 2008-04-30
I think I've got it, guys! :)
It was, as I suspected, a transparency problem.
Open up gconf-editor (Alt-F2, type that in, enter), and navigate to apps -> gwd. Set the value for "metacity_theme_opacity" to 1. The windows don't look as "pretty" when unfocused, but this seems to do the trick for now.

Thanks goes to [this post]("http://ubuntuforums.org/showpost.php?p=4830131&postcount=7").

Screenshot attached.

[ATTACH]68088[/ATTACH]

---

