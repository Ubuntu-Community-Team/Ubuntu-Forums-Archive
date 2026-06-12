---
title: "php glob() returns an empty array"
date: 2010-05-12
forum: Programming Talk
---

### Post by epicoder on 2010-05-12
For some reason, whenever I use glob() to search a directory for files, it will always return an empty array. To see if I had a syntax error, I made this very small test snippet...
[PHP]<?php
foreach(glob('*.txt') as $file)
{
    echo $file."\n";
}
?>[/PHP]
and put it in a directory with two text files in it. glob() still returned an empty array.

---

### Post by roccivic on 2010-05-12
It's probably no consolation to you, but your snippet works just fine here.
Dunno, maybe reinstall PHP?

---

### Post by epicoder on 2010-05-12
Hmmm.... Now it works again. Weird.

---

