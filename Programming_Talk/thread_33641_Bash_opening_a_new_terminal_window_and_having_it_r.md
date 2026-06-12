---
title: "Bash: opening a new terminal window and having it run a command"
date: 2005-05-11
forum: Programming Talk
---

### Post by shakin on 2005-05-11
Simple question: I have a bash script that needs to open a gnome terminal and pass in a command as a paramater.

eg.

gnome-terminal 'vi filename'

but of course that example doesn't work.

Any ideas are appreciated.

Thanks.

---

### Post by bihe on 2005-05-11
[QUOTE=shakin]Simple question: I have a bash script that needs to open a gnome terminal and pass in a command as a paramater.
...
[/QUOTE]

e.g. gnome-terminal -e 'ssh [email]root@foo.bar[/email]'

~$ man gnome-terminal
> -e, --command=STRING
>                Execute the argument to this option inside the terminal.

works the same with xterm, konsole, ...

---

### Post by shakin on 2005-05-11
[QUOTE=bihe]e.g. gnome-terminal -e 'ssh [email]root@foo.bar[/email]'

~$ man gnome-terminal
> -e, --command=STRING
>                Execute the argument to this option inside the terminal.

works the same with xterm, konsole, ...[/QUOTE]

Thanks, but that actually didn't work. It launched the new window but failed to execute any commands. I did get it to work with the -x option:
```

gnome-terminal -x ssh root@foo.bar

```

---

### Post by rocuan on 2010-05-31
Great tip Thanx!

---

