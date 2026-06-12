---
title: "broken symbolic link"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by siddhanta on 2011-09-27
hi,
i am trying to install oracle10gr2 and for that i have to set some parameters.
so, i have to change the default replacement of /bin/sh from dash to bash
i ran the following command

[PHP]ln sf bash bin/sh [/PHP]

and the output is

lrwxrwxrwx 1 root root 4 2011-09-28 03:04 [COLOR="Red"] /bin/sh [/COLOR] ->[COLOR="Red"] bash [/COLOR]

firstly why the red color. Is something wrong with it.
secondaly in my /bin folder i can  find "dash" but there is no "bash". Is it a error??
thirdly when am tryin to open "sh" file in /sh, its showing broken. 

So,please, help. I am new to ubuntu.
I am using ubuntu 11.04

thanx

---

### Post by haqking on 2011-09-27
> **siddhanta said:**
> hi,
i am trying to install oracle10gr2 and for that i have to set some parameters.
so, i have to change the default replacement of /bin/sh from dash to bash
i ran the following command

[PHP]ln sf bash bin/sh [/PHP]

and the output is

lrwxrwxrwx 1 root root 4 2011-09-28 03:04 [COLOR="Red"] /bin/sh [/COLOR] ->[COLOR="Red"] bash [/COLOR]

firstly why the red color. Is something wrong with it.
secondaly in my /bin folder i can  find "dash" but there is no "bash". Is it a error??
thirdly when am tryin to open "sh" file in /sh, its showing broken. 

So,please, help. I am new to ubuntu.
I am using ubuntu 11.04

thanx

red usually means archived/compressed or broken symbolic link

see here for bash/dash etc [https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

your interactive shell should be bash anyways, its only that sh points to dash

i think ;-)

---

### Post by siddhanta on 2011-09-27
thanx for reply

when i go to the property of /bin/sh its showing link broken.

So how to solve this error.

---

### Post by siddhanta on 2011-09-27
This link cannot be used, because its target "bash" doesn't exist.

how to get rid of this error..

---

### Post by haqking on 2011-09-27
> **siddhanta said:**
> This link cannot be used, because its target "bash" doesn't exist.

how to get rid of this error..

```
whereis bash
```

should be in /bin/bash

---

