---
title: "test for filetype with no error o/p"
date: 2006-12-24
forum: Programming Talk
---

### Post by pickarooney on 2006-12-24
I'm trying to test for the existence of a file type and perform an action on all files of that type, but don't want to get an error output if the filetype doesn't exist.

Both snippets below throw up errors depending on whether or not the filetype exists.

```

if [ -f *.txt ]
then
  rm *.txt
fi

```
or
```

for file in *.txt
do
   rm $file
done

```

---

### Post by po0f on 2006-12-24
pickarooney,

`rm -f`.

---

### Post by pickarooney on 2006-12-24
True, that works for the example I gave. However, if I expand the if/for loops to perform any other actions besides **rm** I still get errors. They're not serious errors, as the script still works, it's just a bit messy.

---

### Post by po0f on 2006-12-24
pickarooney,

```
[FONT="Courier New"]if [ -f *.txt ]; then
    <some_command> 2>/dev/null
    <some_other_command> 2>/dev/null
fi[/FONT]
```

---

### Post by pickarooney on 2006-12-24
Yeah, that'll work. Thanks :)

---

