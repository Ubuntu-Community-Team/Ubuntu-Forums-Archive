---
title: "bash (curses?) file selection dialog"
date: 2014-07-31
forum: Programming Talk
---

### Post by 1clue on 2014-07-31
Hi,

I'm trying to make a more idiot-proof file selector.

I need to make a script that lists the files in a specific directory, lets the user select it with up and down arrows (or even with a number) and then returns the name when they press return.

Is there a file dialog of some sort already out there?

Thanks.

---

### Post by 1clue on 2014-07-31
I found it.  I had to load the 'dialog' package.  Solved.

---

### Post by 1clue on 2014-07-31
Actually it seems these dialogs suck pretty bad.

---

### Post by sudodus on 2014-07-31
If you intend to use them yourself (only), you will learn using the file selectors of ***dialog***. They are very different from standard file selectors, but I would not say unintuitive, once you know that you use what is in the bottom box (and the top box(es) are only for putting things into the bottom box), they are quite nice.

But if you intend to make it for other people, you need something easier to use. In graphical desktops there is also ***zenity***, that has a file selector, that works like people are used to.

I have recently revamped ***mkusb*** from a crude text interface to dialog menus, that I like, except the selectors for files and directories. And I use zenity for that purpose, when that can run (in graphical desktops). See these links

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[https://help.ubuntu.com/community/mkusb/pictures#General_file_selector](https://help.ubuntu.com/community/mkusb/pictures#General_file_selector)

---

### Post by 1clue on 2014-07-31
It's to help a select few people who are not Linux-savvy and don't have time or desire to become that way.

This is for a non-gui environment, Ubuntu Server 12.04.

I coded it in groovy, since that's a language we need and the one they're  most familiar with.  No curses, it just prints an enumerated list of options in the directory and a readline to pull the number.  And it also shows existing symbolic links in the directory pointing to any given file as well, pretty handy for the purpose I think.

It's done, so I guess that's over.  Thanks.

---

### Post by sudodus on 2014-08-01
Your solution is similar to the previous interface of ***mkusb***. I used plain bash writing to standard output and letting people select by means of a number according to an enumerated list of option. I think it is good enough for a small group of people who are used to working with the command line interface :-)

---

