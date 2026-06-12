---
title: "Simple Text Editor (Without tabs!)"
date: 2007-04-18
forum: Programming Talk
---

### Post by Naatan on 2007-04-18
Hi,

I'm looking for a decent text editor that supports syntax highlighting for web source code (html/javascript/css/php) but does NOT have tabs!

I very much prefer a text editor when each opens in their own window, like every single app these days has tabs and none of them have the feature to disable tabs :(

So does anyone know a decent text editor that does not have tabs?

Oh and it should be a GUI as I need to be able to launch it when editing files over FTP

Thanks in advance :)

---

### Post by tkjacobsen on 2007-04-18
tea  or maybe nedit -- found in the repos.

---

### Post by Naatan on 2007-04-18
it has tabs :(

---

### Post by yabbadabbadont on 2007-04-18
Nano.  Yes, it is a text mode app, but it runs fine in a terminal window.

---

### Post by duff on 2007-04-18
[http://www.gnomefiles.org/app.php/Scratchpad](http://www.gnomefiles.org/app.php/Scratchpad)

---

### Post by WW on 2007-04-18
```

$ gedit file1.txt  &
$ gedit file2.txt --new-window &

```
Just a suggestion... I'm not sure if that will meet your needs.

---

### Post by AdamG on 2007-04-18
The simplest thing may be to simply use Gedit and just not use the tabs. 

Even if you're using GNOME, I would consider Kwrite too. It's really an excellent program and I used it (and KATE, it's big sister) while on both GNOME and XFce. It obviously doesn't integrate as well as I would have liked, but I greatly perferred it to Gedit.

---

### Post by kerry_s on 2007-04-18
Geany, you can turn off everything and have nothing but a plain text pad. You need to use geany -i if you want it to always use a new instance. You just use the open with and in the enter command put geany -i and check the make default or whatever. Have fun. (sudo apt-get install geany)

---

### Post by snoop on 2007-04-19
There is also one editor for gnome called Scribes (i believe it has no tabs). [http://scribes.sourceforge.net/](http://scribes.sourceforge.net/)

---

### Post by Naatan on 2007-04-19
Thanks guys, though none of them really fit what I was looking for.. most of them had tabs :(

I'm using gvim now, after tweaking rcvim a bit it works just right! :)

---

### Post by Naatan on 2007-04-20
> **snoop said:**
> There is also one editor for gnome called Scribes (i believe it has no tabs). [http://scribes.sourceforge.net/](http://scribes.sourceforge.net/)

Scribes is awesome! :O exactly what I was looking for :D

I also really like scratchpad but I don't like the fact that I would manually have to create  a new file with appropreate extension in order for me to use it properly..

Thanks for the advice guys :)

---

### Post by gummibaerchen on 2007-04-20
**Scribes** seems to fit to your needs perfectly.

They (the Scribes devs) seem to dislike tabs as well ;)

[http://scribes.sourceforge.net/](http://scribes.sourceforge.net/)

---

