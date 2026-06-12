---
title: "Using CVS in Anjuta 2.0.2"
date: 2006-08-20
forum: Programming Talk
---

### Post by rko618 on 2006-08-20
I've compiled Anjuta 2.0.2 from sources and am trying to get it add my project to CVS.  I have cvs installed and the CVS plugin activated in Anjuta and when I select CVS -> Commit I get this error message

```

/usr/bin/cvs -z3 commit -m 'no log message'
cvs commit: No CVSROOT specified! Please use the '-d' option
cvs [commit aborted]: or set the CVSROOT environment variable.
CVS command failed! - See above for details
```

In terminal I entered this commands:
```

export CVSROOT=/home/rob/cvs
cvs init
```

But that doesn't seem to work.  This is my first time setting up cvs so I'm somewhat new to this.  Help appreciated!

---

