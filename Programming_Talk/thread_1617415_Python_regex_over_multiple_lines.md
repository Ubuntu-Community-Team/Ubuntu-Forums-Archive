---
title: "Python regex over multiple lines"
date: 2010-11-09
forum: Programming Talk
---

### Post by tommy1987 on 2010-11-09
I've written the following line of Python:


```
re = re.compile("^([A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4})+(,\s*([A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}){1})*$", re.IGNORECASE)
```

Currently I have it in my source code all on one line and it works fine. However it makes for a rather long line and I'd like to split it over several lines e.g.

```
re = re.compile("^([A-Z0-9._%+-]+@
                [A-Z0-9.-]+\.[A-Z]{2,4})+
                (,\s*([A-Z0-9._%+-]+@
                [A-Z0-9.-]+\.[A-Z]{2,4})
                {1})*$", re.IGNORECASE)
```

How can I do this without changing the functionality of the regex?

Thanks!

---

### Post by Arndt on 2010-11-09
> **tommy1987 said:**
> I've written the following line of Python:


```
re = re.compile("^([A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4})+(,\s*([A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}){1})*$", re.IGNORECASE)
```

Currently I have it in my source code all on one line and it works fine. However it makes for a rather long line and I'd like to split it over several lines e.g.

```
re = re.compile("^([A-Z0-9._%+-]+@
                [A-Z0-9.-]+\.[A-Z]{2,4})+
                (,\s*([A-Z0-9._%+-]+@
                [A-Z0-9.-]+\.[A-Z]{2,4})
                {1})*$", re.IGNORECASE)
```

How can I do this without changing the functionality of the regex?

Thanks!

You can use either of these two:

```
rexp = re.compile("^([A-Z0-9._%+-]+@\
[A-Z0-9.-]+\.[A-Z]{2,4})+\
(,\s*([A-Z0-9._%+-]+@\
[A-Z0-9.-]+\.[A-Z]{2,4})\
{1})*$", re.IGNORECASE)

rexp = re.compile("^([A-Z0-9._%+-]+@" \
                      "[A-Z0-9.-]+\.[A-Z]{2,4})+" \
                      "(,\s*([A-Z0-9._%+-]+@" \
                      "[A-Z0-9.-]+\.[A-Z]{2,4})" \
                      "{1})*$", re.IGNORECASE)

```

I replaced your variable 're' with 'rexp', since what happens otherwise is that you lose the reference to the 're' module, and can't do re.compile again.

---

### Post by cdiem on 2010-11-09
Check here: [http://diveintopython.org/regular_expressions/verbose.html]("http://diveintopython.org/regular_expressions/verbose.html")

---

### Post by tommy1987 on 2010-11-10
> **Arndt said:**
> You can use either of these two:

```
rexp = re.compile("^([A-Z0-9._%+-]+@\
[A-Z0-9.-]+\.[A-Z]{2,4})+\
(,\s*([A-Z0-9._%+-]+@\
[A-Z0-9.-]+\.[A-Z]{2,4})\
{1})*$", re.IGNORECASE)

rexp = re.compile("^([A-Z0-9._%+-]+@" \
                      "[A-Z0-9.-]+\.[A-Z]{2,4})+" \
                      "(,\s*([A-Z0-9._%+-]+@" \
                      "[A-Z0-9.-]+\.[A-Z]{2,4})" \
                      "{1})*$", re.IGNORECASE)

```

I replaced your variable 're' with 'rexp', since what happens otherwise is that you lose the reference to the 're' module, and can't do re.compile again.

Thanks a lot, worked well.

---

