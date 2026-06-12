---
title: "Perl Documentations on Kdevelop"
date: 2006-05-31
forum: Programming Talk
---

### Post by Hoffmann on 2006-05-31
I am running Kdevelop on Gnome. When I try to see the Perl documentation from that IDE, I get:

An error occurred while loading man: perlsyn: 
Could not start process Unable to create io-slave:
 klauncher said: Unknown protocol 'man'.

How can I solve this problem?
Thanks!

---

### Post by asimon on 2006-06-01
[QUOTE=Hoffmann]I am running Kdevelop on Gnome. When I try to see the Perl documentation from that IDE, I get:

An error occurred while loading man: perlsyn: 
Could not start process Unable to create io-slave:
 klauncher said: Unknown protocol 'man'.

How can I solve this problem?
Thanks![/QUOTE]
The kio slave for man is part of package 'kdebase-kio-plugins'. If you have installed kdevelop without the rest of kubuntu-desktop you may not have it installed (in which case it would be good if kdevelop would suggest or recommend that package).

---

### Post by Hoffmann on 2006-06-01
[QUOTE=asimon]The kio slave for man is part of package 'kdebase-kio-plugins'. If you have installed kdevelop without the rest of kubuntu-desktop you may not have it installed (in which case it would be good if kdevelop would suggest or recommend that package).[/QUOTE]
Hello asimon,

I just installed 'kdebase-kio-plugins', and now I can read the Perl documents from Kdevelop. 
Thanks for the hint.

---

