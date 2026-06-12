---
title: "Help with my shell script?"
date: 2009-10-28
forum: Programming Talk
---

### Post by jordanae on 2009-10-28
I'm not sure if this is the right place for this, but here it goes:

I just wrote a shell script to run to clean up my desktop. It's extremely simple:

```
mv /home/jordan/Desktop/gnome-terminal.desktop /home/jordan/clean_up/gnome-terminal.desktop
rm /home/jordan/Desktop/*
mv /home/jordan/clean_up/gnome-terminal.desktop /home/jordan/Desktop/gnome-terminal.desktop

```

It works, but whenever I run the script the terminal icon wont show up on the desktop. I ran an ls -l on my desktop and it showed up, and when I logged out and back in again it showed up. Is there a way to fix this?

---

### Post by -Sparx- on 2009-10-28
You can try to reload the desktop (folder).
When you have the desktop in front of you hit "C-r" (ctrl and the 'r' button). Just as you would refreshing a webpage in firefox.

---

### Post by sisco311 on 2009-10-28
Assuming that it's a bash script you can use !(filename) to match anything except filename.

i.e.
```

shopt -s extglob
rm ~/Desktop/!(gnome-terminal.desktop)
```

```
man bash | less --pattern\="extglob"
```

---

### Post by jordanae on 2009-10-28
> **sisco311 said:**
> Assuming that it's a bash script you can use !(filename) to match anything except filename.

i.e.
```

shopt -s extglob
rm ~/Desktop/!(gnome-terminal.desktop)
```

```
man bash | less --pattern\="extglob"
```

Thanks a lot. But what does the shopt command do? I'm on my phone right now so I can't run a man or info command :/

---

### Post by yknivag on 2009-10-28
> **jordanae said:**
> Thanks a lot. But what does the shopt command do? I'm on my phone right now so I can't run a man or info command :/

> shopt [-pqsu] [-o] [optname ...]
    Toggle the values of variables controlling optional shell behavior. With no options, or with the -p option, a list of all settable options is displayed, with an indication of whether or not each is set. The -p option causes output to be displayed in a form that may be reused as input. Other options have the following meanings:<snip>

Taken from [http://www.linuxmanpages.com/man1/shopt.1.php](http://www.linuxmanpages.com/man1/shopt.1.php)

Essentially -s causes the extglobs option to be set in the shell behaviour options. extglobs allows the use of globs (such as !) in filenames.

---

### Post by phrostbyte on 2009-10-28
You might need to do this:

nautilus --restart

---

### Post by geirha on 2009-10-29
This covers mostly the same as the man-page on globs [http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob), but has some examples of use too.

---

