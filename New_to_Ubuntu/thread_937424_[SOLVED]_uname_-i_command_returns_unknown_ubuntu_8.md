---
title: "[SOLVED] uname -i command returns unknown ubuntu 8.04 lts"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by MRM0607 on 2008-10-03
Dear Ubuntu Form users,

I wanted to know the platform information for my machine running on ubuntu 8.04 LTS.

When I type the command uname -i, it returns 'unknown'. It does not help me. Is there anything I can do to solve the problem.

I will appreciate your reply.

Thank you.
Mamta Mohan

---

### Post by Dr Small on 2008-10-03
Try:
```
uname -m
```

---

### Post by sharke on 2008-10-03
> **MRM0607 said:**
> Dear Ubuntu Form users,

I wanted to know the platform information for my machine running on ubuntu 8.04 LTS.

When I type the command uname -i, it returns 'unknown'. It does not help me. Is there anything I can do to solve the problem.

I will appreciate your reply.

Thank you.
Mamta Mohan

unam -r will output kernel uname -a will output kernel & processor info.
regards
Sharke

---

### Post by MRM0607 on 2008-10-04
> **sharke said:**
> unam -r will output kernel uname -a will output kernel & processor info.
regards
Sharke

Dear user,

as suggested above both option and another option suggested 'uname -m' do not help me.

In order to download correct software for my work I need to know bit information. That information is available via 'uname -i' which returns 'unknown'

Another issue I encountered that 'arch' command returns

bash: arch: command not found

I would appreciate if somebody can guide me to find correct information and explain the reason and suggest If I have to install something or change some options.

Thank you.

---

### Post by hexwind on 2010-01-11
> **Dr Small said:**
> Try:
```
uname -m
```
This one worked for me. Thanks.

---

### Post by triplec-mike on 2011-10-02
> **Dr Small said:**
> Try:
```
uname -m
```
 
It worked for me too!
Thanks a lot!:popcorn:

---

### Post by oldos2er on 2011-10-02
Closed, necromancy.

---

