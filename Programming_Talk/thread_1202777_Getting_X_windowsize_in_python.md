---
title: "Getting X windowsize in python"
date: 2009-07-02
forum: Programming Talk
---

### Post by Xlksjdsa on 2009-07-02
Does X provide a way to get window sizes of running apps through python or bash?

---

### Post by smartbei on 2009-07-02
How about using xwininfo?
```

xwininfo -name "<THE WINDOW's NAME>"

```
prints out a bunch of info about the window. From there it should be simple to get the sizes. If you are having trouble with it, post. (:-)).

If you want to get all the windows:
```

xwininfo -root -tree

```
But this will require much more complicated processing. Play around with xwininfo a bit, maybe you will find something that fits you better. Try running it without arguments.

---

### Post by Xlksjdsa on 2009-07-02
Thanks! This will be helpful :)

---

### Post by Xlksjdsa on 2009-07-02
Is there a way to also set the window size?

---

### Post by unutbu on 2009-07-02
You could install the wmctrl package. It allows you to control windows from the command-line.

To list all windows:
```

wmctrl -l
```

To resize/move a window:```


wmctrl -e 1,0,0,500,500 -r mozilla   
```

This moves the "mozilla" window's upper-left corner to 0,0 and resizes it to 500x500.

---

### Post by Xlksjdsa on 2009-07-03
Thanks, that's pretty much what I was looking for. One last thing... is there an easy way to get X11 cursor position? I tried looking at the pygtk package, but that seems to be for creating windows; I only want to modify existing windows.

---

### Post by unutbu on 2009-07-03
To find the absolute mouse position (relative to the root window) in python, you could use this:

[http://www.unix.com/unix-dummies-questions-answers/26069-cursor-position.html#post302313453](http://www.unix.com/unix-dummies-questions-answers/26069-cursor-position.html#post302313453)

or

[http://ubuntuforums.org/showpost.php?p=7249747&postcount=7](http://ubuntuforums.org/showpost.php?p=7249747&postcount=7)

The first link requires that you install the python-xlib package.
The second link requires that you run "python setup.py build"
to compile a small C library.

---

### Post by UbuKunubi on 2009-07-04
I know this may be a little late, but the OP may also find xdotool of some use...have a google.

all the best,
Ubu

---

