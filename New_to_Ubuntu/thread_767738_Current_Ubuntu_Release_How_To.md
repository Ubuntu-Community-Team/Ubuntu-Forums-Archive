---
title: "Current Ubuntu Release How To"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by fire-fly on 2008-04-25
Hi
How can I find out the current ubuntu release installed ?

Thanks in advance
Cheers
fire-fly

---

### Post by Cypher on 2008-04-25
```

cat /etc/issue

```

---

### Post by nhandler on 2008-04-25
Go into a terminal (Applications->Accessories->Terminal). Type the following command:

```
cat /etc/issue
```

It should say what version of Ubuntu you have.

8.04=Hardy (Most Recent)
7.10=Gutsy
7.04=Feisty
6.10=Edgy
6.04=Dapper

---

### Post by RealPSL on 2008-04-25
You may want to try this one too:

```
lsb_release -rd
```

Which produces something like this:

```
Description:    Ubuntu 7.10
Release:        7.10
```

---

### Post by kostkon on 2008-04-25
Or just go to *System -> Administration -> System Monitor* and select the *System* tab.

---

### Post by fire-fly on 2008-04-26
Hi people
Thanks :d

---

