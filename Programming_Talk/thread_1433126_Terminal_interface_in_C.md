---
title: "Terminal interface in C"
date: 2010-03-18
forum: Programming Talk
---

### Post by pswoo on 2010-03-18
I know stdin, stdout, etc. and how to read/write to them, but some programs (e.g. nano, pine, man) use the terminal in a different way - e.g. selecting of terminal text as though it were a button, editing of multiple lines of text, etc. Then, when they exit, the interface is gone. How is this done?

---

### Post by Compyx on 2010-03-18
Take a look at the curses/ncurses library: [http://en.wikipedia.org/wiki/Curses_%28programming_library%29]("http://en.wikipedia.org/wiki/Curses_%28programming_library%29").

---

