---
title: "Organize files based on first letter"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by taddy_porter on 2008-05-29
I have a large collection of files in one big directory. I was trying to find an easy way to move them to a subdirectory based on the first letter of the name-basically create a-z folders within the directory and move them there. I can't figure out a way to do that easily. Does anyone know of a bash command that could achieve this?

---

### Post by nick_h on 2008-05-29
No, but you could write a simple bash script.

```
#!/bin/bash
for LETTER in a b c d e f g h i j k l m n o p q r s t u v w x y z; do
	mkdir $LETTER
	find . -maxdepth 1 -type f -iname "${LETTER}*" -exec mv '{}' "${LETTER}" \;
done
```

I suggest you make a backup first.

---

