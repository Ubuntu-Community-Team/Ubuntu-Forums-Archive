---
title: "How does gdb control auto-complete?"
date: 2008-11-09
forum: Programming Talk
---

### Post by stair314 on 2008-11-09
I noticed that before you launch gdb, it actually influences what sort of things can be autocompleted in a call to it.
i.e., if I had a file called example.txt and an executable called demo
I could use tab to autocomplete
gdb d
to gdb demo
but I could not use tab to autocomplte
gdb e
to
gdb example.txt

Does anybody know how gdb does that? It would be cool to control auto-completion to my own program's command line arguments, but I have no idea how to write code that executes before the application is launched.

---

### Post by stylishpants on 2008-11-09
Bash knows which file extensions are valid for which applications.
```
 man bash | less -p '^   Programmable Completion' 
```


You can see how it works here:
```
/etc/bash_completion
```

You can write your own completions too, but don't add them to that file since it gets updated from time to time.  Instead, make a new file in /etc/bash_completion.d/ and add your completions to that.

---

