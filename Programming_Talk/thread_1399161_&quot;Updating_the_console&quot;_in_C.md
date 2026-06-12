---
title: "&quot;Updating the console&quot; in C"
date: 2010-02-05
forum: Programming Talk
---

### Post by heamaster on 2010-02-05
Hello!
Sometimes (in all cool programs) you see that the console is "updated", meaning that not writing to the console over and over it just seems like the text is changing, for example in top. It looks like the screen is updating. How is this done?

---

### Post by LKjell on 2010-02-05
Check out ncurses

---

### Post by MadCow108 on 2010-02-05
by using an appropriate library like ncurses

to a very limited degree you can do some stuff by using the carriage return \r to overwrite your previous output

---

### Post by Sporkman on 2010-02-05
Check out ANSI terminal codes:

[http://www.termsys.demon.co.uk/vtansi.htm](http://www.termsys.demon.co.uk/vtansi.htm)
[http://ascii-table.com/ansi-escape-sequences-vt-100.php](http://ascii-table.com/ansi-escape-sequences-vt-100.php)

---

