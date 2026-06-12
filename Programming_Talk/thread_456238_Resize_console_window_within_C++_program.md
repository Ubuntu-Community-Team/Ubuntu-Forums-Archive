---
title: "Resize console window within C++ program"
date: 2007-05-27
forum: Programming Talk
---

### Post by nrwilk on 2007-05-27
Heya everyone,

I am having fun writing a little ncurses app with C++, and I want to be able to resize the console window from within the application.  Does anyone know how I can do this?  I would like to be able to check the columns and rows, and if the window is too small, resize it.

I found this, but it doesn't seem to work in Konsole:
```
\e[8;50;80t
```

I do have konsole set to allow resizing.

Is there any way to make sure that a C++ program will be able to resize the console window, no matter which one it is running in?

Thanks for any help!

nrwilk

---

### Post by linfidel on 2007-05-27
Are you sure you want to do this?  If the program is only for you, it's fine, but if others are using it, you will probably only manage to annoy them.  Users can make it whatever size they want, and may prefer doing things their own way, like most Linux users. :)

---

### Post by nrwilk on 2007-05-30
> **linfidel said:**
> Are you sure you want to do this?  If the program is only for you, it's fine, but if others are using it, you will probably only manage to annoy them.  Users can make it whatever size they want, and may prefer doing things their own way, like most Linux users. :)

Yeah, I doubt it will ever be seen by anyone other than me.  Just for fun and learning.  I know I would hate it if my console window was resized without my permission.  Also, the resize will be optional, with the default choice being a negative.

So, I just want to experiment with it.

---

### Post by winch on 2007-05-30
if you use [dcop]("http://www.volny.cz/bwian/dcop.html") to resize the konsole window.

```

dcop konsole-<konsole PID> konsole-mainwindow#1 resize 700 500

```

Locks you into using konsole and requires you have the PID of the konsole your program is running in.

---

### Post by nrwilk on 2007-06-23
> **winch said:**
> if you use [dcop]("http://www.volny.cz/bwian/dcop.html") to resize the konsole window.

```

dcop konsole-<konsole PID> konsole-mainwindow#1 resize 700 500

```

Locks you into using konsole and requires you have the PID of the konsole your program is running in.

Yeah, but I'd like it if it wasn't specific to Konsole.  Isn't there some easy, standard way to resize a console window?  If there isn't, then there should be.

---

