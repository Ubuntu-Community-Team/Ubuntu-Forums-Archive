---
title: "What happened to all the threads??"
date: 2004-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by nixn00b on 2004-11-16
on my regular route to see if someone answered my question, I noticed that it and all the howto's are gone.

so, I'll take this oppertunity to ask again, in regards to the webserver howto, How do I configure Ubuntu to start the webserver/mysql on bootup, for all users, not just the session, ie before session begins?

---

### Post by jdong on 2004-11-16
Set your forum options to show more than just the last day.

---

### Post by p!=f on 2004-11-16
[QUOTE=nixn00b]on my regular route to see if someone answered my question, I noticed that it and all the howto's are gone.[/QUOTE]  I'm not sure but I think the HOWTOs move to the main website at [http://www.ubuntulinux.org]("http://www.ubuntulinux.org"), the documentation section.
  
  [QUOTE=nixn00b]
 so, I'll take this oppertunity to ask again, in regards to the webserver howto, How do I configure smoothwall to start the webserver/mysql on bootup, for all users, not just the session, ie before session begins?[/QUOTE]  These forums are dedicated to Ubuntu Linux. Asking this question at [http://community.smoothwall.org/forum/]("http://community.smoothwall.org/forum/") might be more effective.
 Basically, installing the appropriate package (whatever package management system SmoothWall uses) is sufficient (ie. mysql-server, apache).

---

### Post by nixn00b on 2004-11-16
[QUOTE=p!=f]I'm not sure but I think the HOWTOs move to the main website at [http://www.ubuntulinux.org]("http://www.ubuntulinux.org"), the documentation section.
  
    These forums are dedicated to Ubuntu Linux. Asking this question at [http://community.smoothwall.org/forum/]("http://community.smoothwall.org/forum/") might be more effective.
 Basically, installing the appropriate package (whatever package management system SmoothWall uses) is sufficient (ie. mysql-server, apache).[/QUOTE]
 oops, that was meant to read ubuntu, not smoothwall, been configuring both today, minds all over da place!
in regards to installing the appropriate packages, thats what I'd done, but I installed them from source, not using apt, but that doesn't add the appropriate scripts to rc.d, I'm a little confused in ubuntu as it isn't so simplistic, there are many rc*.d , and I'm unsure as to which is the right one, and what they all do!

---

