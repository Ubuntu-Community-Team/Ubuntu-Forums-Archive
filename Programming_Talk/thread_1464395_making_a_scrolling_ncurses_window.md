---
title: "making a scrolling ncurses window"
date: 2010-04-28
forum: Programming Talk
---

### Post by guest_user on 2010-04-28
ok so I'm creating a basic server software and I would like to implement the interface in ncurses such that whenever a client connects it would print out a message on the ncurses window, if there's an error it would also print out a message. Each message would be on a newline but when the window fills up, I would like to make it scroll upwards one line at a time, I would also like the user to be able to press up arrow or down arrow to navigate the log messages so how can I implement such functionality, what functions do I call, etc?

---

### Post by guest_user on 2010-04-28
bump

---

### Post by guest_user on 2010-04-30
bump

---

### Post by phrostbyte on 2010-04-30
I've done some ncurses programming, but the core API is a bit low level (really limited to moving the cursor around, printing text in colors, and other such things). There is some libraries built on top of it. My suggestion to you is to look at the source code of the less utility, which does what you want.

apt-get source less

---

### Post by phrostbyte on 2010-04-30
The brute force way to do it with ncurses would be to clear the screen and redraw the buffer anyway. I wouldn't be surprised if that's exactly what less does anyway.

eg (this is pseudo-code):

```

clear();
for(int i=0; i<buffersize; ++i) {
  mvprintw(i, 0, *some_array_pointing_to_lines_of_text);
}

```

---

### Post by gil_johnson on 2010-05-02
> **guest_user said:**
> ok so I'm creating a basic server software and I would like to implement the interface in ncurses such that whenever a client connects it would print out a message on the ncurses window, if there's an error it would also print out a message. Each message would be on a newline but when the window fills up, I would like to make it scroll upwards one line at a time, I would also like the user to be able to press up arrow or down arrow to navigate the log messages so how can I implement such functionality, what functions do I call, etc?
If you are going to do a lot with nCurses, get a copy of  "Programmer's guide to nCurses" by Dan Gookin. Its available used through Amazon, $10-12 plus $4 shipping within the US. About half the book is a tutorial, which also highlights the, ahh...., idiosynchrasies of nCurses. The rest of the book is a reference. Scrolling is well covered.
It has saved me many headaches, for instance the 'add string' function wraps to the next line if it reaches the edge of the window. The 'add formated string' function doesn't. Characters beyond the edge of the window just disappear.
NCurses is kind of a hack, dating back to the days before graphics terminals were common.
Good luck - Gil

---

### Post by rnerwein on 2010-05-03
> **guest_user said:**
> ok so I'm creating a basic server software and I would like to implement the interface in ncurses such that whenever a client connects it would print out a message on the ncurses window, if there's an error it would also print out a message. Each message would be on a newline but when the window fills up, I would like to make it scroll upwards one line at a time, I would also like the user to be able to press up arrow or down arrow to navigate the log messages so how can I implement such functionality, what functions do I call, etc?

hi
have a look at that basic little c-program - using a example about scrolling.
to compile it run: sh scroll.c --> the output will be the executeable scroll. ( don't wonder about the "sh .."
have a look at the first lines of the source after doing a gzip -d scroll.c.gz )
have fun

ciao
ups where my *.gz file

---

### Post by rnerwein on 2010-05-03
> **guest_user said:**
> ok so I'm creating a basic server software and I would like to implement the interface in ncurses such that whenever a client connects it would print out a message on the ncurses window, if there's an error it would also print out a message. Each message would be on a newline but when the window fills up, I would like to make it scroll upwards one line at a time, I would also like the user to be able to press up arrow or down arrow to navigate the log messages so how can I implement such functionality, what functions do I call, etc?

hi
have a look at that basic little c-program - using a example about scrolling.
to compile it run: sh scroll.c --> the output will be the executeable scroll. ( don't wonder about the "sh .."
have a look at the first lines of the source after doing a gzip -d scroll.c.gz )
have fun

ciao

hope the attachement is here now

---

