---
title: "bash"
date: 2008-08-26
forum: Programming Talk
---

### Post by martin_legion on 2008-08-26
Hello, I'm programming some bash scripts and I was wondering how could I add a line at the end of a file, without overwriting anything.
I need to add the name and value of a variable in a .conf file.
¿Any sugestions?

Thanks

---

### Post by rogeriopvl on 2008-08-26
```
echo "whatever you want to add" >> file.conf
```

this does what you need

---

### Post by rangalo on 2008-08-26
```

echo "Whatever you want to append" >> file

```

should work.

---

### Post by rangalo on 2008-08-26
@rogeriopvl:

you were faster :)

---

### Post by martin_legion on 2008-08-26
> **rangalo said:**
> @rogeriopvl:

you were faster :)

:lolflag:
Thanks, I was using only one ">"
Now I know the difference between using > and >> :P

---

### Post by monkeyking on 2008-08-26
I would most likely just do a 

```

echo -e "\n" >>yourfile 

```

---

