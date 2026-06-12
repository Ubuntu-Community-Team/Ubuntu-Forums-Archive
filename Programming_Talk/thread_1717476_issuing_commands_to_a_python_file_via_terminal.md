---
title: "issuing commands to a python file via terminal"
date: 2011-03-29
forum: Programming Talk
---

### Post by ki4jgt on 2011-03-29
How do I take -command from the terminal using a python file?

---

### Post by kostkon on 2011-03-29
The simple way is to use the [*sys.argv*]("http://docs.python.org/release/2.6.5/library/sys.html#sys.argv") list variable that contains all the command line arguments that are passed to your script/application.

The more advanced/failsafe way is to use the [*optparse*]("http://docs.python.org/release/2.6.5/library/optparse.html") module.

Hope that helps.

---

### Post by ki4jgt on 2011-03-30
> **kostkon said:**
> The simple way is to use the [*sys.argv*]("http://docs.python.org/release/2.6.5/library/sys.html#sys.argv") list variable that contains all the command line arguments that are passed to your script/application.

The more advanced/failsafe way is to use the [*optparse*]("http://docs.python.org/release/2.6.5/library/optparse.html") module.

Hope that helps.

Thanks. . . For some reason, I had titled that bash in my mind. So I spent 15 minutes looking up how to do bash in Python. That's what happens when I stay up late. . . but yeah that's good :-)

---

