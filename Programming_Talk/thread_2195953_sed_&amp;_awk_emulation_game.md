---
title: "sed &amp; awk emulation game"
date: 2013-12-27
forum: Programming Talk
---

### Post by sha1sum on 2013-12-27
Hello guys/gals,

Lately I've been studying programming a lot, and especially sed and awk. As a game to improve my skills, I often try to write small sed and awk commands that replicate bash commands. For example:

```

head file.txt

# with sed and awk:
sed '10q'  file.txt 
awk 'NR<11' file.txt 
```

```

grep 'regex' file.txt

# with sed and awk:
sed -n '/regex/p' file.txt
awk '/regex/' file.txt 
```

```

cat file.txt

# with sed and awk:
sed '' file.txt
awk '1' file.txt 
```

```

wc -l  file.txt

# with awk:
awk 'END{print NR}' file.txt

```

Do you guys know other sed or awk command imitations?

---

### Post by Vaphell on 2013-12-27
```
wc -l  file.txt
sed -n '$=' file.txt
```

---

### Post by sha1sum on 2013-12-27
Nice one! Much shorter than my awk counterpart. Good find sir.

---

