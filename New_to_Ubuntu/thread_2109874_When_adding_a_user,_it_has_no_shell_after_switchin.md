---
title: "When adding a user, it has no shell after switching to it"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by Houmie on 2013-01-28
Hi,

I hhave created a new user:

```
sudo useradd celery
```

now when I switch to it:

```
sudo su celery
```

It has no shell, it is always just a $, no matter where I switch to e.g. cd /etc/ it still shows $. Its very annoying, am I missing something?

Many Thanks,

---

### Post by elgordodude on 2013-01-28
-s can be used to define a user's shell, usually /bin/bash

```
sudo useradd celery -s /bin/bash
```

---

