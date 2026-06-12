---
title: "Where is Eclipse?"
date: 2006-11-12
forum: Programming Talk
---

### Post by Salvatore Di Fazio on 2006-11-12
Hi guys,
before start I would say excuse me becouse I posted the same thread in "Installation & Upgrade" but I had not received any answer.

I had upgraded the system from drapper to edgy and I would like to install eclipse IDE on my system through apt or sympatic.

If I looking for the package I don't find it:

Code:
```

salvo@ubuntu:~$ sudo apt-cache search eclipse
ecj-bootstrap - bootstrap version of the Eclipse Java compiler
ecj-bootstrap-gcj - bootstrap version of the Eclipse Java
                    compiler (native version) openoffice.org-dev
                    - OpenOffice.org SDK -- development files

```

How can I resolve it?
Tnx

---

### Post by llonesmiz on 2006-11-12
You need to enable the universe repository. System->Administration->Software Sources then check "community mantained open source software". After that do:

sudo apt-get update

and then search again.
Good luck.

---

### Post by Salvatore Di Fazio on 2006-11-12
Thank you very much

---

