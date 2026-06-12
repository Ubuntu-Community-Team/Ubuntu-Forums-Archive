---
title: "Keyword highlighting for my console"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by anothrguitarist on 2008-06-06
I'm trying to change my console so it displays keywords in color. What I'm trying to achieve is something similar to syntax highlighting, but for my console. I was able to add a little bit of color with my ls command, but that's as far as I got. Does anyone know a simple way to improve my console? For the record, I would be willing to use either the GNOME terminal or konsole.

Thanks.

---

### Post by sdennie on 2008-06-06
What keywords are you referring to?  Specifically, what program do you want highlighting for?

---

### Post by anothrguitarist on 2008-06-06
I'm not entirely sure of what I want, but I think that a color-coded console will be more readable.

Some of the things that I *would* like to be colored are directories and programs, but there are probably other things that would be nice as well.

---

### Post by sdennie on 2008-06-06
There are lots of things you can do to make the console more colorful.  You can find guides to doing this but, for example, I have this in my ~/.bashrc file:

```

export PS1="${debian_chroot:+($debian_chroot)}\[\033[0;36m\]\u\[\033[0;31m\]@\h:\[\033[1;37m\]\w\$ "

```

That changes the prompt to be similar to the default prompt but with colors.  You should also look at the dircolors command (man dircolors on the command line).  You can use that to further customize ls colors.  Apart from that, you'd have to be a bit more specific in what you want to change.

---

