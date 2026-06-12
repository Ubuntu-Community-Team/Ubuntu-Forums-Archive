---
title: "Environment variables in Eclipse"
date: 2009-08-19
forum: Programming Talk
---

### Post by stair314 on 2009-08-19
Eclipse doesn't seem to inherit environment variables from any of my shells. There's been a thread about this before which is closed now: [http://ubuntuforums.org/showthread.php?t=452752]("http://ubuntuforums.org/showthread.php?t=452752")

In that thread, we never heard for sure if the OP got their issue fixed. The main reply was that Eclipse might be using sh instead of bash, but that's not the issue because I have a .profile and my environment variables show up in sh.

I'm using getenv() in Java and it's returning null for variables that are defined if I open a shell.

The "Run" dialog in Eclipse has an option (which I have selected) to "Append environment to native environment" which seems to imply it is inheriting an environment from somewhere. Does anybody know how to get it to work?

---

### Post by drader on 2009-09-02
Had the same issue, I basically followed the advice in the link you provided.

My issue was that I set environment variables in my .bashrc and eclipse is ran under /usr/sh (which is linked to dash). I moved my environment variables to my .profile, sourced .profile and .bashrc and relaunched eclipse. I can now reference environment variables (tested in ant scripts).

---

