---
title: "[SOLVED] Syntax highlighting in terminal"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by phantomgunex on 2008-10-09
Is there a way to get syntax highlighting in gnome-terminal? like 'cd' will be a different colour from the path??/:guitar:

---

### Post by SeanHodges on 2008-10-09
Theres a setting in you .bashrc called:

#force_colored_prompt=yes

Uncomment it and you should get your pretty colours :)

---

### Post by phantomgunex on 2008-10-09
where can you find the file?

---

### Post by DirtDawg on 2008-10-09
In your home folder. "ls -a" to see it if using a terminal or CTRL+H to show hidden files in Nautilus.

EDIT: I tried uncommenting the suggested line, but I can't tell any difference at all. Am I missing something?

---

### Post by kerry_s on 2008-10-09
there's a section in bashrc that tells you what to do.

---

### Post by bodhi.zazen on 2008-10-09
There are a number of links google will take you too ...

[http://www.pixelbeat.org/docs/terminal_colours/](http://www.pixelbeat.org/docs/terminal_colours/)

---

### Post by DirtDawg on 2008-10-09
> **kerry_s said:**
> there's a section in bashrc that tells you what to do.
I don't have that section in my bashrc. Looks like those lines have been wrapped in a conditional statement. Are you using an old version?

---

### Post by kerry_s on 2008-10-10
> **DirtDawg said:**
> I don't have that section in my bashrc. Looks like those lines have been wrapped in a conditional statement. Are you using an old version?

yeah, i'm using etch so it's a little old.
sorry had no idea it's changed that much.
mine are commented out because i do my own>

```
PS1=' DIR: \[\033[01;34m\]\w\[\033[00m\] \n~> '
```

---

### Post by SeanHodges on 2008-10-10
Theres a typo in the .bashrc script:

```
force_colored_prompt=yes
```

should be:

```
force_color_prompt=yes
```

Change this. then restart bash (close and open your terminal)

Your example shows you want the command name to appear in a different colour to the arguments you are passing in (which my suggestion will not do). I haven't seen this done - obviously that doesn't mean it's impossible, I just don't know how you would do it in bash.

I suggest you have a google around, or give the fish shell a try:

[http://www.fishshell.org/](http://www.fishshell.org/)

```
sudo apt-get install fish
```

---

### Post by Kiefer Rodriguez on 2008-10-10
Wow, looks cool.

---

### Post by Sycron on 2008-10-10
indeed

---

### Post by phantomgunex on 2008-10-17
Thanks for all you help! I finally had syntax highlighting in terminal! A million thanks!:KS

---

