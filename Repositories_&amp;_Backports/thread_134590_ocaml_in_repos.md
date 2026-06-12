---
title: "ocaml in repos"
date: 2006-02-22
forum: Repositories &amp; Backports
---

### Post by tassou on 2006-02-22
Hello,

I can not retrieve some packages related to ocaml :

```

root@ubuT42:/home/paul # apt-get install ocaml
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  ocaml-base ocaml-nox
Suggested packages:
  xlibs-dev tcl8.4-dev tk8.4-dev ocaml-doc libgdbm-dev
Recommended packages:
  ledit
The following NEW packages will be installed:
  ocaml ocaml-base ocaml-nox
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 7754kB of archives.
After unpacking 32.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
0% [Waiting for headers]

```

stalled.

Thank you for any advice

Tassou

---

### Post by tassou on 2006-02-27
I solved it finally. It was not a repository problem but a local apt problem.
 apt-get clean solved it.

Thanks

---

