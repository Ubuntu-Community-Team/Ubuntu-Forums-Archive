---
title: "Basic Bash: Starting applications in term, then closing term..."
date: 2008-05-10
forum: New to Ubuntu
---

### Post by irumat on 2008-05-10
Hi all,

Real newbie question: often I open a terminal and start some applications from there. Say gedit.
```

gedit &
```
or
```

gedit
<CTRL+Z>
bg
```

My question is: is there any way that I can close the terminal window and have gedit continue running? Or do I have to keep the terminal window throughout the period I'm using gedit.

Thanks in advance,

Kind regards,

Irumat

---

### Post by llamakc on 2008-05-10
Type "exit" in the terminal instead of X'ing out of the window. CTRL-d also works.

So for example:

```

$ pidgin &

```

Now I want to kill that terminal, so I type:

```

exit

```

Again the key combo CTRL-d also will exit the terminal.

---

### Post by sdennie on 2008-05-10
Type:

```

disown

```

In the terminal before closing it.

---

### Post by Joeb454 on 2008-05-10
You run ```
(gedit &)
``` this is what I do whenever I want to do the same as you do ;)

Obviously replace gedit with whatever app you want to run :p

---

### Post by llamakc on 2008-05-10
> **vor said:**
> Type:

```

disown

```In the terminal before closing it.

Is that a bash builtin? I didn't find a man page for it. Neat. I've become fond of using CTRL-d myself, but it is always fun to learn something new.

---

### Post by sdennie on 2008-05-10
Yeah, that's a builtin.  I believe you can also say:

```

disown -a

```

To disown all processes started by that shell.

---

### Post by irumat on 2008-05-10
Thanks guys, disown and CTRL+D both work!

Cheers!

---

### Post by Separ on 2008-05-10
You could also run commands from the run dialog by hitting Alt+F2.

---

