---
title: "PHP-Gtk2 post-compile issues in Jaunty"
date: 2009-06-24
forum: Programming Talk
---

### Post by madcat8 on 2009-06-24
We're trying to move a php-gtk2 app into Ubuntu.  Tried several compile suggestions, all results the same.  PHP-Gtk2 compiles okay, but we can't use gridlines or button tips, etc, all new features with the most recent source code for php-gtk2.  Verified that we are compiling to that version, using php 5.2.

Configure just standard, nothing exotic.

Any suggestions?

---

### Post by Tibuda on 2009-06-24
Are you trying to compile your php application or compile php-gtk itself?

---

### Post by Vadi on 2009-06-25
You got php-gtk2 compiled to begin with? Last time I tried, there were errors.

update: well, seems they got a patch for this: [http://www.opsat.net/temp/buildfix.diff](http://www.opsat.net/temp/buildfix.diff)

---

