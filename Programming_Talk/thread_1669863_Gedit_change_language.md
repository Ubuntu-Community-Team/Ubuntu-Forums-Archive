---
title: "Gedit change language"
date: 2011-01-18
forum: Programming Talk
---

### Post by x32jsf on 2011-01-18
Hi! I cant change my Gedit language. 
there is no option in preferences. When i installed it the language was automatically set to my country's language but i dont like it because its not my mother language, and i wannna to set ENGLISH as default. I google-d it for many dayz but no result. Any idea?

---

### Post by psihodelia on 2011-10-26
I have exactly the same problem. I've just installed gedit and I can't set English as default interface language, it's now in German.


> **x32jsf said:**
> Hi! I cant change my Gedit language. 
there is no option in preferences. When i installed it the language was automatically set to my country's language but i dont like it because its not my mother language, and i wannna to set ENGLISH as default. I google-d it for many dayz but no result. Any idea?

---

### Post by Vaphell on 2011-10-26
you can force gedit to run with different locale
```
LANG=C gedit
```
C is a fallback locale, but you can also use en_US.UTF-8 or whatever.

if you want to have that permanently, i guess you will need to modify gedit launchers to include LANG=...

to make a system wide change try modifying Exec=.... line in
/usr/share/applications/gedit.desktop
to Exec=sh -c 'LANG=C gedit %U'

only for your account
copy the file above to ~/.local/share/applications/
and modify

---

