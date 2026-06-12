---
title: "Which programs help me build a TUI?"
date: 2018-04-07
forum: Programming Talk
---

### Post by stlu on 2018-04-07
Hi,

For a long time I have wanted to enhance my bash scripts with an interface other than input statements using the "read" command.  I have become aware of two so far: dialog and whiptail.

I am about to start reading some information on curses/ncurses, which I found this tutorial from an older thread on the topic: [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/).  It worries me that users say it isn't easy to use.

If there is any more software that I should know about when deciding how to make a TUI, let me know.  Also if there is a site that gives advice or tutorials for dialog or whiptail, that would be great too.

---

### Post by sudodus on 2018-04-07
I use **dialog** for this purpose.

```
sudo apt install dialog
```

I think you can find many good tutorials. Browse the internet, and use a tutorial, that suits your purpose. That is how I learned how to use dialog.

You can also refer to the manual

```
man dialog
```

---

