---
title: "Gedit - file size info"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by abcuser on 2008-06-05
Hi,
in Ubuntu 8.10 I would like to see info about file size editing in Gedit program. Is is possible to display this info in program's status bar? I am really used to this kind of info from Ultra-Editor on Windows XP. I write article and I constantly need info about file size (which is the same as number of characters).

Any idea?
Thanks,
Abcuser

---

### Post by indytim on 2008-06-05
Under Tools -> Document Status you will find the information that you are looking for.  Can't help with the constant display though:(.

IndyTim

---

### Post by sdennie on 2008-06-05
I don't use gedit but, bringing it up, there is an option in the Tools menu called Document Statistics that can give that information.  I don't see a way to put that in the status bar though.  I think gedit is really just meant to be a basic editor and, if you are looking for something more configurable, you may want to google around and see if something else better suits your needs.  I personally use vim (which is incredibly configurable) but, there is a fairly high barrier to entry using that editor and it may not be what you are looking for.

Also, this isn't what you are looking for but, it's worth pointing out that this can also be done from the command line with:

```

wc some_file.txt

```

The three numbers will be number of lines, number of words and number of characters (bytes).

---

