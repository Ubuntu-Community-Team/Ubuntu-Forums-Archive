---
title: "shell script: run aptitude interactively"
date: 2009-03-24
forum: Programming Talk
---

### Post by GrfyGrumpyBear on 2009-03-24
I'm setting up a script to use aptitude to install xorg, Slim, and midori

Now the problem is, I need the user to interact with aptitude. Is this possible?:

```

#!/bin/bash
sudo aptitude install xorg slim icewm menu midori
```

---

### Post by AnarchyMaster on 2009-03-24
how about the read command?

---

### Post by GrfyGrumpyBear on 2009-03-24
can you give an example with the script?

---

### Post by AnarchyMaster on 2009-03-24
I think they'd have to type the data in before you run the app, is that okay?

---

### Post by GrfyGrumpyBear on 2009-03-24
they run it from the command line.

---

### Post by GrfyGrumpyBear on 2009-03-24
like:
they run it like: (i think)
```
(bash) user@example:~$ ./myscript.sh
```

---

### Post by shatterblast on 2009-03-24
You could probably implement that idea just fine.  You might just add a note to the user to "right click on the script file after downloading, click on the Permissions tab across the top, and then put a check next to 'Allow executing file as a program.'" After that, you could advise to "click Run in Terminal after double-clicking it."  It should ask for the user's password then all should be good.  Pretty simple.  Friends or customers typically like more clicking and less typing for some reason unless it's e-mail or whatever.

---

### Post by Sindre on 2009-03-24
If you want to program a script that does intelligent choices, you want to look at "expect".
You can probably make a one-liner with "apt-get" instead of aptitude as well, that installs it with the default options.

---

### Post by GrfyGrumpyBear on 2009-03-24
No, the script is intended to run on the command-line version of ubuntu.

And I tell the user to chmod first.

Now, a side question: would installing xorg with -qq in apt-get have anything like debconf to run? (like configuration)

---

### Post by GrfyGrumpyBear on 2009-03-24
oh, and I tell the user to run su first.

---

### Post by GrfyGrumpyBear on 2009-03-25
Bump?

---

### Post by Dougie187 on 2009-03-25
What are you trying to write a script to do this for? Also, what kind of user interactions are you needing?

---

### Post by nvteighen on 2009-03-25
I really don't get this... If you want an "interactive" (whatever you mean by that) aptitude:

```

aptitude

```

And voilà, you get a very nice TUI.

If you want to use command lines, aptitude already does that...

---

### Post by GrfyGrumpyBear on 2009-03-26
I make the user run a script in bash to install some programs - but will the script be interactive in case debconf appears and other stuff?

See the first post for the script.

---

### Post by GrfyGrumpyBear on 2009-03-26
Bump?

---

