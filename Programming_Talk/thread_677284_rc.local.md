---
title: "rc.local"
date: 2008-01-24
forum: Programming Talk
---

### Post by jd65pl on 2008-01-24
rc.local is not used in debian, is the same true for ubuntu?

Thanks

j

---

### Post by mssever on 2008-01-24
By default, Ubuntu's rc.local is blank. But, if you put something there, it will be run. However, you might be interested in checking out Upstart, which is Ubuntu's new event-driven boot system.

---

### Post by jd65pl on 2008-01-24
So if I want something to start on boot it will be executed if it is in rc.local? Does anyone have any documentation on the ubuntu boot methods?

Thanks for your answer!

J

---

### Post by mssever on 2008-01-24
> **jd65pl said:**
> So if I want something to start on boot it will be executed if it is in rc.local?Sure. Or you can write a standard init script. Or you can use Upstart.
> Does anyone have any documentation on the ubuntu boot methods?
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

