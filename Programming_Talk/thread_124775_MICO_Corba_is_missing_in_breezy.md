---
title: "MICO Corba is missing in breezy"
date: 2006-02-02
forum: Programming Talk
---

### Post by m9dhatter on 2006-02-02
why is mico corba in warty and in hoary but not in breezy? 
i added hoary in my repository and installed mico taking care not to pull any hoary dependencies. it installed properly, but i am failing to compile any mico corba code.
lots of different errors from uncompilable header files to library dependencies.. can anyone help?

---

### Post by asimon on 2006-02-02
[QUOTE=m9dhatter]why is mico corba in warty and in hoary but not in breezy? [/quote]
[The Debian maintainer of mico orphaned the package](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=268868). No one else stepped forward to take over maintainership of the package. The package was thus removed from Debian unstable and as a result is no longer auto-imported into Ubuntu (the old package as is probably don't even compile).

---

### Post by m9dhatter on 2006-02-02
[QUOTE=asimon][url=http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=268868]The ...The package was thus removed from Debian unstable and as a result is no longer auto-imported into Ubuntu (the old package as is probably don't even compile).[/QUOTE]

well, it doesnt. i tried using gcc 4. i will try using a lower gcc version to compile... it might work. i will post more details later. thanks for the reply.

---

