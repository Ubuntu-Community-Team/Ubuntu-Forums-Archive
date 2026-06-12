---
title: "gtk hello world: &quot;gtk.h: No such file&quot;"
date: 2009-12-24
forum: Programming Talk
---

### Post by schmolch on 2009-12-24
Im trying to compile a simple gtk hello world program but get this error msg:```

No package 'gtk+2.0' found
helloworld.c:1:21: error: gtk/gtk.h: No such file or directory
```

I have libgtk2-0.dev installed and gtk.h is at /usr/include/gtk-2.0/gtk/gtk.h

I tried to compile it with geany and on the command-line with 
```
gcc -Wall -g helloworld.c -o helloworld pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`
``` as instructed in the book.

Can somebody please tell me why in the "§%!"§$ it does not work?

---

### Post by dwhitney67 on 2009-12-24
Three possibilities...

1.  You are a bad typist;
2.  Your book is wrong (ie has a typo);
3.  You do not have GTK+-2.0 installed on your system.

From the statement you posted, I am wagering #1 is the culprit.  This part of your gcc statement is missing the backtick (`) character:
```

pkg-config --cflags gtk+-2.0`

```

---

### Post by Physical Hook on 2009-12-25
The first thing to check is whether you've installed libgtk2.0-dev. If everything seems to be in place, use the following command.

```
gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0 --libs gtk+-2.0`

```
[COLOR=Gray]Source: [http://library.gnome.org/devel/gtk-tutorial/stable/x111.html](http://library.gnome.org/devel/gtk-tutorial/stable/x111.html)[/COLOR]

---

### Post by schmolch on 2009-12-25
Thanks for putting up with my stupidity.
Those backticks are a bitch though.

---

### Post by I am &gt;= Wes on 2009-12-26
Did anyone get some sort of workaround for Geany working?  I love it, not that I'm uncomfortable with the command line (I use Archlinux generally, but haven't had the patience to install it on my netbook), I would just prefer to not have to think about it and just click a button.

---

### Post by schmolch on 2009-12-27
You just have to add > `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`
to Geany's compile and build commands.
They are not in the preferences (which is why i could not find them first) but in the build-menu.

---

### Post by I am &gt;= Wes on 2009-12-27
> **schmolch said:**
> You just have to add 
to Geany's compile and build commands.
They are not in the preferences (which is why i could not find them first) but in the build-menu.

Duly noted sir. I shall fix it now and report any problems (though I doubt there'll be any).

---

### Post by pirog on 2010-02-07
hm, I use Makefile in Geany - try it.

i also used gedit+terminal, then moved onto Geany and then onto NetBeans.
Gedit+terminal: worked like a charm
Geany: didn't bother with compiler options - used Makefile instead
NetBeans:
```
main.c:3:17: warning: gtk.h: No such file or directory
```
ah, i'm going back to simpler tools. Gedit/Geany rock!:guitar:
nano??? hahaha!

---

### Post by LKjell on 2010-02-07
When you get use to vim everything else seems so inconvenient.

---

### Post by pirog on 2010-02-07
> **LKjell said:**
> When you get use to vim everything else seems so inconvenient.

You know, LKjell, I have never used vim, just nano. I am not so sure as to why I've never used it, but there you go :)

cheerio

---

### Post by LKjell on 2010-02-07
> **pirog said:**
> You know, LKjell, I have never used vim, just nano. I am not so sure as to why I've never used it, but there you go :)

cheerio

vimtutor is a very nice introduction.

---

### Post by pirog on 2010-02-07
> **LKjell said:**
> vimtutor is a very nice introduction.

LKjell, I haven't even got vim installed. I'll give it a try after the Super Bowl ;) thanks

---

### Post by LKjell on 2010-02-07
vim.tiny is installed otherwise you have uninstalled it in karmic

---

### Post by pirog on 2010-02-07
> **LKjell said:**
> vim.tiny is installed otherwise you have uninstalled it in karmic

hah, you are right. i don't think vimtutor installed (vim runtime?). I used emacs for a while, but i could never get used to it. i did a lot of Latex work and emacs wasn't what i looked for.

I was recently browsing forums for best editor for programmers/writers/students and came to the conclusion that there is the best editor... and it is different for everyone. sounds lame, but it is true.

---

### Post by pbrane on 2010-02-07
An easier way to compile a GTK+ app on the command line is
```
gcc $(pkg-config --cflags --libs gtk+-2.0) -o appname app.c
```

I prefer to use a text editor ( emacs or gedit ) and terminal.

---

### Post by pirog on 2010-02-07
> **pbrane said:**
> An easier way to compile a GTK+ app on the command line is
```
gcc $(pkg-config --cflags --libs gtk+-2.0) -o appname app.c
```

i'don't know... what's wrong with?:
```
make
```
quite short and you just add files as:
```
FILES = src0.o src1.o src3.o ... 
```
if at all necessary :)
personal choice i guess. thanks for the input pbrane ;)

---

### Post by pbrane on 2010-02-07
> **pirog said:**
> i'don't know... what's wrong with?:
```
make
```
quite short and you just add files as:
```
FILES = src0.o src1.o src3.o ... 
```
if at all necessary :)
personal choice i guess. thanks for the input pbrane ;)

I agree with you. I personally use autoconf tools to create projects. But I was responding to the OP. The backtic syntax can lead to confusion sometimes. So instead of backtics use the *$(...)* syntax. And you don't need to use *pkg-config* twice, once for *--cflags* and again for *--libs*, they can be combined.

---

### Post by pirog on 2010-02-07
> **pbrane said:**
> I agree with you. I personally use autoconf tools to create projects. But I was responding to the OP. The backtic syntax can lead to confusion sometimes. So instead of backtics use the *$(...)* syntax. And you don't need to use *pkg-config* twice, once for *--cflags* and again for *--libs*, they can be combined.

soz. yeah, sure this is a good example for compiling through terminal especially when you don't want to get messy with Makefiles. yet you don't have to define pkg-config flags twice, just use $(FLAGS) for substitution. It does not really make difference when you use libs or cflags (whether at compile or linking stages) and hence you can use pkg-config just once. then again, everyone likes doing it their way ;)

---

### Post by blade__tang on 2010-05-29
I have the same question,but I have resolved it. Cause my language  version of ubuntu is Chinese, I have to translate the button from  Chinese to English. Maybe there will be a littile mistake. Select  buile->set buile parameters.

compile:gcc -Wall -c "%f" `pkg-config --cflags --libs gtk+-2.0`
buile:gcc -Wall -o "%e" "%f" `pkg-config --cflags --libs gtk+-2.0`

Then have a try again

---

