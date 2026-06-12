---
title: "[SOLVED] Where is &amp;quot;/usr/share/applications/screen &amp;amp; graffics&amp;quot; please"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by davwar on 2008-05-05
I must be missing something very obvious but can some one give me the full path name to:

/usr/share/applications/screen & graffics

for the life of me I can't find it.

Thank you

---

### Post by SunnyRabbiera on 2008-05-05
you mean a link to screens and graphics right?
the command should be gksu displayconfig-gtk

---

### Post by Oldsoldier2003 on 2008-05-05
> **davwar said:**
> I must be missing something very obvious but can some one give me the full path name to:

/usr/share/applications/screen & graffics

for the life of me I can't find it.

Thank you

what are you looking for in there? you could do this
```

cd /usr/share/applications/
ls -al | more
```

---

### Post by Oldsoldier2003 on 2008-05-05
> **SunnyRabbiera said:**
> you mean a link to screens and graphics right?
the command should be gksu displayconfig-gtk

ah i couldn't for the life of me see where he was going with this. yeah its not listed in any of hardy's default menus. could be because the desktop team doesn't like it... i called it up and ran test and it told me that my vieo card and monitor dont work lol!

---

### Post by davwar on 2008-05-05
I'm having a problem with screen resolution  and 8.04 recognising the correct monitor. (new install using Wubi into XP)

I was told that I should go to:
"/usr/share/applications/screen & graffics"
and nothing else.

Sorry - very much a first time user.

Is the above info on the web forum or maybe is it info on my PC?
(I was thinking that it was info on the web)

I'm now guessing that it's a path on my PC and that I should execute the commands in your replys??
which should give me info on what my hardware/config is??
and then somehow allow me to modify the configuration??

The 'screen resolution utility' has not helped me at all.

Thank you for any help

---

