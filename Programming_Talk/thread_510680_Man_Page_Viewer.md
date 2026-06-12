---
title: "Man Page Viewer?"
date: 2007-07-26
forum: Programming Talk
---

### Post by fatsheep on 2007-07-26
Is there a program that will allow me to search and display man pages on my system in a friendlier format such as HTML?  Sometimes looking at black text on a white screen in a terminal can get a little hard on the eyes...

---

### Post by duff on 2007-07-26
```
# yelp man:printf
# yelp 'man:printf(3)'
```

---

### Post by kerry_s on 2007-07-27
Alt+f2, type> xman

---

### Post by tqk on 2007-07-30
> Alt+f2, type> xman
```
xman -notopbox -bothshown &
```
However, when I tried this in Xubuntu recently, it came back saying the system was missing Xman manpages.  I have't tracked the problem down yet.  :(

---

### Post by cwaldbieser on 2007-07-30
> **tqk said:**
> ```
xman -notopbox -bothshown &
```
However, when I tried this in Xubuntu recently, it came back saying the system was missing Xman manpages.  I have't tracked the problem down yet.  :(

Try
```

$ export MANPATH=/usr/share/man
$ xman

```

---

### Post by Torajima on 2007-07-30
> **fatsheep said:**
> Is there a program that will allow me to search and display man pages on my system in a friendlier format such as HTML?  Sometimes looking at black text on a white screen in a terminal can get a little hard on the eyes...

Well, you could just save it as a text file, and view it with whatever program you wished.

```
man mv >> mv.txt
```

---

### Post by dwblas on 2007-08-02
1) apt-get install man2html, also I think w3m will read man pages.  I also use info2man to get info pages into something that can be used.  W3m man link:
[http://linux.die.net/man/1/w3mman](http://linux.die.net/man/1/w3mman)
2) gman and xman will display manpages (xman is installed on most *buntu's).  I have not used either.
3) I have heard that Konqueror will read manpages.  I don't use KDE, but it is something like man://manpage_name.
4) [http://polyglotman.sourceforge.net/](http://polyglotman.sourceforge.net/) converts as well
5) whichman is a man page search tool
6) Some text/wordprocessors have manpage plugins.  You will have to Google for the one you use

---

### Post by dwblas on 2007-08-02
> Well, you could just save it as a text file, and view it with whatever program you wished.
man mv >> mv.txtI'm not sure if this tip works, but the point is well taken.  You can just gunzip the man page and view it with a text processor.  If you use midnight commander, it will read them as is, i.e. gzipped

---

### Post by nitro_n2o on 2007-08-02
> **fatsheep said:**
> Is there a program that will allow me to search and display man pages on my system in a friendlier format such as HTML?  Sometimes looking at black text on a white screen in a terminal can get a little hard on the eyes...

[http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

white on black is certainly better than black on white

---

### Post by tqk on 2007-08-06
Thanks very much.  Defining MANPATH is the solution.  Xman works perfectly once that's done.

---

### Post by HermanAB on 2007-08-06
If using Kubuntu, you can type man://whatever in Konqueror.

---

### Post by peertje888 on 2010-02-17
As superuser you could make a script /usr/bash/gman with for example:
```
man $1 > ~/.cache/manpage;geany ~/.cache/manpage
```Replace geany with your favorite editor, if the file is empty, the man page was not found.
Don't forget to update the file's permisions:
```
chmod +x /usr/bin/gman
```

---

### Post by ibuclaw on 2010-02-17
Wow.

1) Old Thread, Closing.

2) The best solutions are the simplest.
Visit Ubuntu's manpage website: [http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

Regards
Iain

---

