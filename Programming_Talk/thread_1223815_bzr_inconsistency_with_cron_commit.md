---
title: "bzr inconsistency with cron commit"
date: 2009-07-26
forum: Programming Talk
---

### Post by rosslaird on 2009-07-26
My bzr repo commits perfectly from the command line (or from within emacs); but whenever I try to run it through cron (for a daily automated commit, for example), I get this:

```
aborting commit write group: UnicodeEncodeError('ascii', u'/home/ross/docs/office/writing/04/ep\u0456graph.tex', 36, 37, 'ordinal not in range(128)')
bzr: ERROR: exceptions.UnicodeEncodeError: 'ascii' codec can't encode character u'\u0456' in position 36: ordinal not in range(128)
```

Various files with non-ASCII characters cause this problem. 
Ideas?

Ross

---

### Post by keithweddell on 2010-05-26
I know this is an old thread but I am currently researching the same problem.  Has anyone found a solution?

Keith

---

### Post by ssam on 2010-05-26
cron runs in a clean environment. the unicode error suggests a locale issue.

might help to change the cron command from
```

bzr commit whatever

```
to
```

LANG=en_GB.utf8 bzr commit whatever

```
maybe replace en_GB.utf8 with whatever "echo $LANG" gives you.

see 'man 5 crontab' for more details

---

### Post by keithweddell on 2010-05-26
Yeah I already tried that but still got the same error.  Thanks for the reply though.

Keith

Edit: Actually, your post made me think again and I think I've got it now.  I'm using:

```
export LANG=en_GB.UTF-8
```

---

