---
title: "[SOLVED] PATH Environmental variable setup"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-05-27
I am trying to figure out how to setup a program in the PATH Environmental list.  In the programs instructions it said the program needed to be added to PATH.  Is there a way to check what is in the PATH list?

---

### Post by sdennie on 2008-05-27
It depends on where the application installed.  If it installed into a normally used place, it's already in the path.  Try this:

```

which name_of_the_program_you_want_to_run

```

If nothing comes up, you'll have to manually add it.  The way I would recommend doing that is to edit ~/.bashrc and, at the bottom, place the following:

```

export PATH=${PATH}:/place/you/installed/your/app

```

You'll have to start a new terminal before that change will apply.  To make it apply to application launchers, I think you'll have to log out and then back in.

Edit:
Actually read the post.  To see the path just:

```

echo $PATH

```

---

