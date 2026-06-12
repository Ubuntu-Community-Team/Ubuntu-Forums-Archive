---
title: "Things needed to Program in C"
date: 2007-03-18
forum: Programming Talk
---

### Post by Kramxel on 2007-03-18
Hi
I'm sure this as been asked a thousand times, but after using the search button and browsing numerous post, I found no answer.

I want to program in C, I'm using emacs to write the code and gcc for compiling.
The thing is I don't know which files to enable.

I'm getting errors on "Can't find stdio.h", and my emacs look isn't right also.
It shows plain text, and I've seen that emacs can get all colourfull when programing (functions are lit in one colour, variables in other, etc.), and that's just not happening.

Thanks in advance.

---

### Post by Wybiral on 2007-03-18
Type this in the terminal:

```
sudo apt-get install build-essential
```

That's really all you need to start.

---

### Post by Kramxel on 2007-03-18
Cool
I can compile now, though my emacs issue remains...
Thanks

---

### Post by Kalixa on 2007-03-18
> **Kramxel said:**
> Cool
I can compile now, though my emacs issue remains...
Thanks

I am no where as experienced in emacs as you are, since I have barely ever tried it, but I would imagine there is a menu which includes the word syntax, which is where you should be able to have variables loops etc. get different colors.

---

### Post by Mr. C. on 2007-03-18
Also install the development man pages - no self-respecting C programmer goes without them! :-)
```

sudo apt-get install manpages-dev
```

MrC

---

### Post by lnostdal on 2007-03-18
```
M-x global-font-lock-mode
```

you can set it permanently in your ~/.emacs file .. (here is my setup btw. [http://nostdal.org/~lars/writings/emacs.html](http://nostdal.org/~lars/writings/emacs.html) )

---

### Post by monkeyking on 2007-03-18
you should also enable paranthesis matching
```
M-x show-paren-mode
```

---

### Post by Kramxel on 2007-03-18
Now emacs is just how I like him to be!

Time to start working on it...

Thanks everyone!

---

