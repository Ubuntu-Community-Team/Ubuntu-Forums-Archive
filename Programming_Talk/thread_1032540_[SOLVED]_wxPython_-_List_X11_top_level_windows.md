---
title: "[SOLVED] wxPython - List X11 top level windows"
date: 2009-01-06
forum: Programming Talk
---

### Post by MaxVK on 2009-01-06
Hi, I'm using wxPython on Ubuntu.

I need to get a list of the open top level windows, preferably identified by their titles, although I might need the actual window ID at some point as well.

Iv been hunting about for this for hours and so far Iv found nothing at all!

Can anyone help please?

Cheers

Max

---

### Post by irfan798 on 2009-01-06
I am not sure but maybe you can try an external script like sh

[http://docs.python.org/library/os.html?highlight=exec#os.execve]("http://docs.python.org/library/os.html?highlight=exec#os.execve")

---

### Post by MaxVK on 2009-01-06
Thanks irfan798, I followed your idea and came up with this:

```
os.system("wmctrl" + " -l > tmpfile")
```

Because os.system waits for the command to finish it means I can then load tmpfile and do whats needed to split the information I require.

Cheers

Max

---

