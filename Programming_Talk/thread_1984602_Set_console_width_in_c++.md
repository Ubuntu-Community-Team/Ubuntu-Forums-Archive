---
title: "Set console width in c++"
date: 2012-05-22
forum: Programming Talk
---

### Post by Harry.k on 2012-05-22
In windoze, the console width was always 80, so it was easy to make console-guis like cmus and links. In linux, however the width can be changed. This really messed up console programs i ported from windows to linux. is there any way to set the console width? even system() commands would do. I know about "stty cols", but it doesnt resize the window. It would've been fine, but it doesn't work if the terminal window's actual width is less than 80, or whatever you set it to.

---

### Post by Harry.k on 2012-05-22
Just so i'm clear, i want to set the width of the console window, or at least make sure the width doesnt go below 80 columns. The title and the menu items tend to spread over multiple lines if it is too small.

---

### Post by roelforg on 2012-05-22
I dunno, i wouldn't like it if an app kept resizing my console....
But have you tried fetching the size and adjusting your offsets with that?

---

### Post by Harry.k on 2012-05-22
Well, i suppose thats better than resizing the window. How do i get the consoie size? Also, it would be nice to know how to resize the console and restore on exiting.

---

### Post by roelforg on 2012-05-22
> **Harry.k said:**
> Well, i suppose thats better than resizing the window. How do i get the consoie size? Also, it would be nice to know how to resize the console and restore on exiting.
 
Ncurses can do this.
[http://stackoverflow.com/questions/1811955/ncurses-terminal-size](http://stackoverflow.com/questions/1811955/ncurses-terminal-size)

---

### Post by Harry.k on 2012-05-22
I know ncurses. I cant use it coz i use cout extensively. It'll totally mess up the display. Is there an alternative?

---

### Post by dwhitney67 on 2012-05-22
> **Harry.k said:**
> I know ncurses. I cant use it coz i use cout extensively. It'll totally mess up the display. Is there an alternative?

A few posts have offered you suggestions.  I will not repeat these.

A simple answer to your question is "No"; C++ in itself does not offer any means to control the size of the console (terminal).

Now, using a C++ application, you could launch a terminal, using exec or something similar, or even system(), in which you could then run your "real" application.  I do not know if there is a way to prevent the user from resizing the console once it has been launched.

Your application would need to know when to launch a terminal, and when to just run (ie. display menus, output, etc).

---

### Post by Harry.k on 2012-05-22
Launching a new terminal! That seems like a good idea. I'll google for more info. Other than that, is there any non-ncurses way to get console dimensions?

---

### Post by roelforg on 2012-05-22
> **Harry.k said:**
> Launching a new terminal! That seems like a good idea. I'll google for more info. Other than that, is there any non-ncurses way to get console dimensions?
 
The $COLUMNS and $LINES env. vars?

---

### Post by Harry.k on 2012-05-22
Not sure how to read the environment variables, but i'm sure google does. Thanks, roelfrog and dewhitney67.

---

### Post by Harry.k on 2012-11-09
After months of searching, I've had it. Even a simple bash script to launch a custom sized terminal would do. Anyone?

---

### Post by Vaphell on 2012-11-09
```
gnome-terminal --geometry 80x24
```

---

