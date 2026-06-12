---
title: "Ubuntu Shortcuts"
date: 2024-01-07
forum: New to Ubuntu
---

### Post by maxitum on 2024-01-07
Windows has a lot of cool shortcuts for different Purposes. Can u recommend some that u can't live without in ubuntu?

---

### Post by #&amp;thj^% on 2024-01-07
you may find these useful: [https://itsfoss.com/ubuntu-shortcuts/](https://itsfoss.com/ubuntu-shortcuts/)

---

### Post by maxitum on 2024-01-07
Thanks :)

---

### Post by Rubi1200 on 2024-01-08
> **1fallen said:**
> you may find these useful: [https://itsfoss.com/ubuntu-shortcuts/](https://itsfoss.com/ubuntu-shortcuts/)
+1

As good a place to start as any.

My personal favourite: Ctrl+Alt+T to open a terminal.

Once you are more familiar with Linux, you will hopefully become good friends with the terminal :-)

---

### Post by ActionParsnip on 2024-01-08
What shortcuts do you use and we can advise more accurately. In computing in general, try to think "How can I achieve X?" rather than "What are all the things?" and you'll be less frustrated. 

CTRL + ALT + T is a good one to bring up a terminal, really handy

---

### Post by TheFu on 2024-01-08
> **maxitum said:**
> Windows has a lot of cool shortcuts for different Purposes. Can u recommend some that u can't live without in ubuntu?

You can create any keyboard acceleration chord you like and connect it to any program/script you like.

I love symbolic links - that was my first thought when you used the term "shortcut".   [https://en.wikipedia.org/wiki/Symbolic_links](https://en.wikipedia.org/wiki/Symbolic_links)  which can be used to make any file appear in multiple places.  Since almost everything is a "file" in Linux/Unix, that is extremely powerful.

---

### Post by VMC on 2024-01-08
I use "aliases" to make shorter-cuts. For example: one item in my alias file,  **lsb='lsblk -o name,fstype,label,uuid'**.

---

### Post by him610 on 2024-01-08
++ aliases   You can roll your own shortcuts.

I define mine in .bash_aliases

---

### Post by TheFu on 2024-01-08
*aliases* and *shell functions* here too.  

There should be a few threads in these forums about our favorite aliases, but they pop-up from time to time in normal troubleshooting posts as well.  If I use something more than 20 times that is longer than 5 characters to type, I'll probably setup a 3-character alias for it.  No need to type so much.

---

### Post by ajgreeny on 2024-01-09
The alias i use most is probably
**alias q='exit'**
So much quicker than using the mouse in the top corner or typing exit (I'm a slow typist!)

---

### Post by ActionParsnip on 2024-01-09
> **ajgreeny said:**
> The alias i use most is probably
**alias q='exit'**
So much quicker than using the mouse in the top corner or typing exit (I'm a slow typist!)

Or just use CTRL + D

---

### Post by TheFu on 2024-01-09
> **ActionParsnip said:**
> Or just use CTRL + D

<cntl>-d

But don't get too happy doing it.  It will close lots of windows, if they have/gain focus.

One of my main shortcuts is to have the focus follow the mouse, not raise the window, and not require any clicks to give focus.  This way, data from a larger window higher in the Z-stack can be viewed but other things can be entered into a window under it.  It does take getting used to and it makes having distinct border colors required between the single window with focus and all the others that don't have focus.

I also have the window manager title bar setup to lower or raise in the z-stack based on which mouse button is clicked, middle mouse will iconify it.  I don't think Gnome supports this. Heck, I don't know if most of the other window managers do.  This is one of the key reasons that I really dislike newer programs that reject the window manager control over borders (or don't have borders at all).  Looking at you gnome-disks.  It breaks my workflow when they don't behave properly, according to standards that have been around 30 yrs.

---

