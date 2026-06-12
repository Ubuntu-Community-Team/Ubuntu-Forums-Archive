---
title: "Quick vim question... pardon my noobish..."
date: 2008-02-23
forum: Programming Talk
---

### Post by Gen2ly on 2008-02-23
I begin typing my document and its all done or sorta done, and I'd like to be able to take a better look at it but highlighting isn't on yet.  Can I turn it on without saving the document and reloading it?

---

### Post by LaRoza on 2008-02-23
```

:syntax on

```

---

### Post by Gen2ly on 2008-02-23
Nope :( :( :(

Other ideas?

---

### Post by LaRoza on 2008-02-23
Did you install vim-full?

```

sudo aptitude install vim-full

```

vim-tiny is installed by default, and lacks many features including syntax highlighting.

---

### Post by Gen2ly on 2008-02-23
Appreciate the fast reply.  I think I learned why I'm not getting the formatting - the file ends with .php so I believe it is syntaxed as php - attached jpg.

Is it possible to change the type of syntax?

---

### Post by LaRoza on 2008-02-23
Most likely, but I don't know how.

---

### Post by ghostdog74 on 2008-02-23
you should look at the vim website to see if it has any enhancements of such things. See if [this]("http://www.vim.org/scripts/script.php?script_id=1571") could help. Otherwise, use another editor

---

### Post by Gen2ly on 2008-02-23
doh!... I got it :)

I had seen in previously.  Here's to memory.  #-o

```
:setfiletype html
```

---

### Post by stroyan on 2008-02-23
You can set the syntax with 
   :set syntax=php

You can learn more about syntax with
   :help syntax

---

