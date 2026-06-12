---
title: "sudo by default? permission?"
date: 2010-09-25
forum: Packaging and Compiling Programs
---

### Post by 2009Prius on 2010-09-25
Hello new here and new to ubuntu (unix for that matter). :)

When I try to use mkdir or svn or cmake in the terminal window I always need to use sudo even though I do limit myself to the /home or /usr/src directories. :confused: What am I doing wrong? How do I avoid typing sudo every time? Thanks!

---

### Post by Bachstelze on 2010-09-25
You don't have write permission to /usr/src, that's normal (you can add yourself to the src group if you want to have it). For your home dir, however, you shouldn't have to use sudo. Probably you used sudo when you didn't have to, so it created a dir owned by rood in your home dir. You can probably safely chown it back to you.

---

