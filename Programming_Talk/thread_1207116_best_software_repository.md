---
title: "best software repository?"
date: 2009-07-07
forum: Programming Talk
---

### Post by sandyd on 2009-07-07
I need a php script (like gforge) that can handle several projects and link to svn repositories
does such a script exist?
p.s. can only use php scripts as i don't ahve shell access to webserver.

---

### Post by JordyD on 2009-07-07
> **carlee said:**
> I need a php script (like gforge) that can handle several projects and link to svn repositories
does such a script exist?
p.s. can only use php scripts as i don't ahve shell access to webserver.
I am no PHP ninja, but I read that you can use system() to do command-line stuff, and the results will be returned. So you can use system("ls") to get a directory listing. So if you know how to get to svn via command-line, you can probably use system().

There are obvious problems with this, like the possibility that svn isn't on the server, but again, I'm no PHP ninja, so I'm just taking a stab in the dark here.

---

