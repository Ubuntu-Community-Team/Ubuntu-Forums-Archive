---
title: "dependancy hell"
date: 2007-09-01
forum: Programming Talk
---

### Post by nonewmsgs on 2007-09-01
i have anjuta and it whined about automake and libtool.  that's ok.  then i make a little hello world console program and i get this

***No targets specified and no makefile found.


what's the deal

---

### Post by scooper on 2007-09-02
That usually means you have to run ./configure in the project directory.  I don't know how anjuta plays into it.  I've never used it.  Sorry if I'm missing the point.

---

### Post by peabody on 2007-09-02
> **nonewmsgs said:**
> i have anjuta and it whined about automake and libtool.  that's ok.  then i make a little hello world console program and i get this

***No targets specified and no makefile found.


what's the deal

I haven't used anjuta before, but it sounds like it expects you to create a makefile for your project.  Create a new text file in your project folder called Makefile.  Here's an easy example of a Makefile
```

hello: hello.c
        gcc -o hello hello.c

```

NOTE: THE SPACING BEFORE THE 'gcc' MUST BE A TAB CHARACTER!  That's very important in makefiles.

---

### Post by badactress on 2007-09-02
Did you create a new project when you started, or just a new file?

When you create a project Anjuta creates the makefile for you. It'll run all the autoconfig nonsense in the output window at the bottom of the screen & if the last thing it says is 'successful' then your project is all ready to go with a makefile, autoconfig etc all set up.

If it reports unsuccessful, or if you just create new file to start, then you're on your own creating your own makefile.

Of course if it does report unsuccessful, it means there's probably something else as well as automake & libtool that you need to install.

---

### Post by nonewmsgs on 2007-09-02
heh.  i tried it again and it worked.  yay! magic code gnomes have helped or sometihng.  thank you all for your help.

im surprised no one uses anjuta?

---

