---
title: "Python3 as default python version?"
date: 2011-04-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Yeeha on 2011-04-30
Title says it all. Will oneiric use python2 or python3 as default python version?

---

### Post by SevenMachines on 2011-04-30
Maybe it'll come out of the summit meeting but i'm fairly sure *lots* of things would break so it would need many hands on the python app bugs.

---

### Post by stmiller on 2011-04-30
The decision will most likely follow debian's lead. As many packages depend on the various debian python related packages, etc.

[http://www.debian.org/doc/packaging-manuals/python-policy/ch-python.html](http://www.debian.org/doc/packaging-manuals/python-policy/ch-python.html)

---

### Post by manzdagratiano on 2011-04-30
`python' on Arch has defaulted to python3, as I realized when trying to run one of my scripts, which complained. They seem to be in pretty good shape, so I think it shouldn't be as bad to switch.

---

### Post by Harry33 on 2011-04-30
> **manzdagratiano said:**
> `python' on Arch has defaulted to python3, as I realized when trying to run one of my scripts, which complained. They seem to be in pretty good shape, so I think it shouldn't be as bad to switch.

During the development of Natty cycle, there was the shift from python2.6 to python2.7.
Of course it would be interesting have python3 (possibly v. 3.2) in Oneiric.
It really should not differ much from what was experienced during Natty cycle.
The python2.7 and python3 can coexist in the same setup.

---

### Post by Yeeha on 2011-05-01
Sure but packages and scripts are going to use default version.

---

### Post by Harry33 on 2011-05-01
> **Yeeha said:**
> Sure but packages and scripts are going to use default version.

True of course.
I just meant during the transitional phase both could be installed.

---

### Post by ikt on 2011-05-02
> **Yeeha said:**
> Title says it all. Will oneiric use python2 or python3 as default python version?

Highly doubt it, maybe 12.10 so there's some room to fix all the breakage before the next LTS after 12.04.

---

### Post by Harry33 on 2011-05-02
> **ikt said:**
> Highly doubt it, maybe 12.10 so there's some room to fix all the breakage before the next LTS after 12.04.

Python3.2 is seriously planned to be part of Oneiric.
This means as many applications as possible will be rewritten against it.
Also, as the total transitition towards python 3.2 will likely not happen, we will see Oneiric have both python2.7 and 3.2 in default installation.
And python2.6 is dropped.

See here:
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-unity2d-qt-cdspace](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-unity2d-qt-cdspace)

---

### Post by ikt on 2011-05-03
> **Harry33 said:**
> This means as many applications as possible will be rewritten against it.

That doesn't change that years and years worth of work can't be changed in 6 months.

---

### Post by Harry33 on 2011-05-03
Well the python3.2 porting has already began now.

See, the latest apt_0.8.14-1ubuntu2 (package apt-utils) depends on libdb5.1 (old apt-utils depended on libdb4.8 ).
Python3.2 also depends on libdb5.1 (python2.7 depends on libdb4.8 ).

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-05-03
Oh come on, Python 2.x to 3.x isn't that radical a change. The changes are minor from a compatibility perspective, there are even scripts to translate python2 to python3. Yes, "years of work" could easily be translated from python2 to python3 in a half a year. No need to stick to the Debian's "release stable, release twice a century" MO.

---

### Post by Harry33 on 2011-05-03
> **ag93igrvigkgdwj1bnr1pw== said:**
> oh come on, python 2.x to 3.x isn't that radical a change. The changes are minor from a compatibility perspective, there are even scripts to translate python2 to python3. Yes, "years of work" could easily be translated from python2 to python3 in a half a year. No need to stick to the debian's "release stable, release twice a century" mo.

+1

---

### Post by dniMretsaM on 2011-05-03
> **ikt said:**
> That doesn't change that years and years worth of work can't be changed in 6 months.

Isn't there a script or something that ports 2.x to 3.x?

---

### Post by dniMretsaM on 2011-05-03
> **harry33 said:**
> +1

+2

EDIT: Oops, this was supposed to be an edit to my last post, lol.

---

### Post by the-ridikulus-rat on 2011-05-06
[http://www.python.org/dev/peps/pep-0394/](http://www.python.org/dev/peps/pep-0394/)

---

### Post by xebian on 2011-05-06
2.7 has most of 3.x backported plus not all libraries have been ported (completely) to 3.x yet like PyGTK IIRC.

---

