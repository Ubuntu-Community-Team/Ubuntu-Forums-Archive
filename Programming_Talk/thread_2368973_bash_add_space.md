---
title: "bash add space"
date: 2017-08-17
forum: Programming Talk
---

### Post by MikeCyber on 2017-08-17
Hi
I simply want to add space in a line with bash. For ex:
echo $id      $idd          xp$c >> ./mass.txt
should give something alike:
```
id               idd                                xp
and not:
id idd xp
```
Thanks

---

### Post by TheFu on 2017-08-17
The forum has "code tags" - Adv Reply (# button) - or in the Advanced Editor - or am I missing the question completely?
```
echo $id       $idd        xp$c          >>         ./mass.txt
```

So I was completely missing the point.
You can just quote everything.
```
echo "$id       $idd        xp$c        "  >>         ./mass.txt
```

---

### Post by spjackson on 2017-08-17
```

echo "$id       $idd        xp$c      "    >>         ./mass.txt

```
or something like...
```

printf "%-10s, %7s %8s   \\n" "$id" "$idd" "xp$c" >>         ./mass.txt

```
depending on how many spaces you want where and whether you want data left or right justified within a field. See 'info printf' for details.

---

### Post by MikeCyber on 2017-08-18
Thanks. I'll try in the next days.

---

