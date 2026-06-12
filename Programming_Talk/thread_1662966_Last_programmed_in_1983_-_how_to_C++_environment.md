---
title: "Last programmed in 1983 - how to C++ environment"
date: 2011-01-09
forum: Programming Talk
---

### Post by JimAcorn on 2011-01-09
Hi,

It's been quite a while since I programmed.  Back in the day when punch cards were the input device primarily.  

There has been something I wanted to try to program.  I'm planning on learning C++ however I'm not sure which package to download from the Ubuntu Software Center.  

I've not worked with an IDE before.  I've browsed through the C++ listings in the Ubuntu Software Center and there are a lot.  Libraries etc.  Is there a package where the whole shooting match that one would need is available?   

**OR** is there article or articles on starting about the environment.  Loops, conditionals, indexing etc I feel confident about handling. It's just developing the programs as far as compiling and running etc.  

Thank you.

Have a Great Day,
Jim

---

### Post by worksofcraft on 2011-01-09
I think you can get all the essential developer tools simply by typing:
```

sudo apt-get install build-essential

```
at the command line.

Some people like the [QT package]("http://qt.nokia.com/products/developer-tools/") from Nokia which is like an integrated development environment with everything you need, but others like [Gtk]("http://library.gnome.org/devel/gtkmm-tutorial/2.21/gtkmm-tutorial.html") which is the basis for the Gnome Desktop.

---

### Post by Ceyx on 2011-01-09
Hi Jim,

Check this out : [http://cartan.cas.suffolk.edu/oopdocbook/opensource/main.html](http://cartan.cas.suffolk.edu/oopdocbook/opensource/main.html)

It is a university course that covers the basics of C++ and QT....

Regards

---

### Post by GregBrannon on 2011-01-09
Review the stickies in this sub forum.

---

### Post by nvteighen on 2011-01-09
Welcome back. You'll be amazed on how things have developed :)

What you really need is a compiler and somewhere to type your code. The compiler is g++ and you've been shown how to install it. Then comes the issue on text editors vs. IDEs... Try some, but don't neglect text editors like emacs or vim, which are quite powerful and have the advantage of not being too intrusive in the compilation and debugging configuration.

---

