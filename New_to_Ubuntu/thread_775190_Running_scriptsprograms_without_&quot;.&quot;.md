---
title: "Running scripts/programs without &quot;./&quot;"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by FugitivePuppeT on 2008-04-29
This is possible right? My professor has a bash script that has hundreds of commands that are meant to be ran w/out ./ rather than reading hundreds of lines of code, can I make my system do this?

---

### Post by RealPSL on 2008-04-29
This is just a function of your PATH variable and telling it to search the current directory. Doing this is generally not good security practice but you can at least see it in action if you do this at the command prompt

```
export PATH=$PATH:.
```

The period at the end tells it to search the current directory which means that you will not longer have to specify the current directory by typing ./some_script_name. You can make the change permanent by adding the above line to the end of your $HOME/.profile. The above will apply to the terminal you change it in.

From a security perspective you have to make sure you trust the system and the files you execute before making that change.

---

### Post by FugitivePuppeT on 2008-04-29
Thanks, worked like a charm

---

