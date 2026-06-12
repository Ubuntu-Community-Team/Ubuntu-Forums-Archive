---
title: "Syslog-ng FIFO issue"
date: 2011-09-22
forum: Programming Talk
---

### Post by btown1987 on 2011-09-22
So I set my destination as follows...

destination d_pipe { pipe("/var/run/some_pipe.fifo"); };

This works fine and all of the logs come through nicely. However when I try to apply a template to it, I get nothing at all in the fifo.

destination d_pipe { pipe("/var/run/some_pipe.fifo" template("$HOST $SOURCEIP $MSG") template-escape(no));};

any ideas?

---

