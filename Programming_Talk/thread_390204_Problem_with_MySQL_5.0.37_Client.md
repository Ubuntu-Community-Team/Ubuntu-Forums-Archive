---
title: "Problem with MySQL 5.0.37 Client"
date: 2007-03-21
forum: Programming Talk
---

### Post by sgornick on 2007-03-21
Just a heads-up to anyone contemplating installing the latest MySQL 5.0 binaries (5.0.37), there is a bug that changed keystroke handling under gnome-terminal that makes the client quite difficult to use.
[http://bugs.mysql.com/bug.php?id=27195](http://bugs.mysql.com/bug.php?id=27195)
 
I reverted back to using the previous binary release (5.0.27).  There is no fix being worked on yet.  If you do want 5.0.37, I guess you could use the client under xterm instead of gnome-terminal ...

---

