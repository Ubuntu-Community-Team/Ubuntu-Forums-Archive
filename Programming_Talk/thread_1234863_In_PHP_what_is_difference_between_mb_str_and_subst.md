---
title: "In PHP what is difference between mb_str and substring?"
date: 2009-08-08
forum: Programming Talk
---

### Post by kapi on 2009-08-08
Am watching a few tutorials (PHP academy) on youtube and wondered what the difference was between mb_substr and the substring function mentioned on w3schools.

---

### Post by Tibuda on 2009-08-08
mb is the prefix for multibyte string. substring will only work with ASCII chars, not special characters. I had much trouble because my language got many non-ASCII characters, and UTF support is not native in PHP. See [http://us2.php.net/manual/en/book.mbstring.php](http://us2.php.net/manual/en/book.mbstring.php)

---

### Post by kapi on 2009-08-08
Thanks very much for explaining.

Much appreciated :-)

---

