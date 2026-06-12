---
title: "[B]Being able to run foomatic from the command line.[/B]"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by cristo-father on 2008-05-29
Hi everyone.
How can i run foomatic from comand line?
Thanks.

---

### Post by unutbu on 2008-05-29
cristo-father, I don't have foomatic installed, so I can't answer you directly. However, here are a few ways you can find the answer for yourself:

1) open System>Preferences>Main Menu. Right-Click on foomatic. Select Properties. It will show you the command that is run.

2) run foomatic from the gnome-panel menu, or however you usually do it. Then open a terminal and type
```

ps axuww | grep foomatic
```

The `ps` command shows all processes (programs) running on your machine. The `grep` command filters out all the processes except ones that contain the word foomatic. In the final column on the right you will see the command that was used to launch foomatic.

---

