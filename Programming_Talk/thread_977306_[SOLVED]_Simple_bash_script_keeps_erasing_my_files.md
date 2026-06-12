---
title: "[SOLVED] Simple bash script keeps erasing my files randomly"
date: 2008-11-10
forum: Programming Talk
---

### Post by u-slayer on 2008-11-10
I wanted to write a simple script that would read all the files given to it and replace double spaces with tabs. It works, sometimes but it also seems to randomly erase my files:(. Pls help.:confused:

```

for f in "$@"; do
	echo -e "$f "
	cat "$f" | sed 's/\x20\x20/\t/g' > "$f"
done
```

---

### Post by geirha on 2008-11-10
Problem is that " > file " truncates the file. And that may happen before the cat command gets the chance to read the file. sed has an option (-i) to do the change "in place". 

```
sed -i 's/  /\t/g' "$@"
```

---

### Post by u-slayer on 2008-11-10
Thanks geirha, that worked.:)

---

