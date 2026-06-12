---
title: "[SOLVED] Change Directory to output of command"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by maandverband on 2008-11-29
In the English version of Ubuntu you can type

```

cd ~/Desktop

```

to CD to the Desktop. This doesn't work in other languages, because the names are localized. When typing the command

```

xdg-user-dir DESKTOP

```

the output of this command will tell you the location of the Desktop for the current user. For example /home/USERNAME/Bureaublad. Now you know you have to CD to Bureaublad instead of Desktop.

Is there a way to give the output of the xdg-user-dit command to the cd command, using the pipe character or something? I can't figure out how to do this.

This way I don't have to think about the language of the user, because the command will work for every language.

---

### Post by PmDematagoda on 2008-11-29
You can do something like that by using the command in this way(sort of like piping input):-
```
cd `xdg-user-dir DESKTOP`
```
the " ` "s are not single quotes, but backward quotes(or whatever they are called). You may be able to set this as a special command by specifying it as an alias in .bashrc.

---

### Post by maandverband on 2008-11-29
Thank you very much. I already tried your command using double quotes and using single quotes, but it never came to my mind to try the command using backward quotes.

---

