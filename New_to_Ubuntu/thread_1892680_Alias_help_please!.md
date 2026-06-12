---
title: "Alias help please!"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by oli.kerr on 2011-12-08
Hello all,

I'm trying to make an alias 'mkmfix' to avoid having to type in 

[PHP]/bin/sh ~/mfix/model/make_mfix[/PHP]

Everytime I want to make an mfix.exe file. I currently have:

[PHP]alias mkmfix='/bin/sh ~/home/oli/mfix/model/make_mfix'[/PHP]

In my bashrc file, and have tried a few alterations but no luck!

Thanks in advance,
Oli

---

### Post by hakermania on 2011-12-08
The '~' means '/home/oli', so, it should be
[COLOR=#000000][COLOR=#0000BB]alias mkmfix[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#DD0000]'/bin/sh /home/oli/mfix/model/make_mfix'[/COLOR][/COLOR]

After editing the .bashrc file, try starting a new terminal window to see if it works.

---

### Post by oli.kerr on 2011-12-08
Easy! How I didn't pick up what '~' means is pretty pathetic...

Thanks mate.

---

