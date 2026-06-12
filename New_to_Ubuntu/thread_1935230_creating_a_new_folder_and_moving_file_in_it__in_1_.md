---
title: "creating a new folder and moving file in it  in 1 command"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by mferarri on 2012-03-03
Hi UbuntuForums,

I'm trying to do 2 commands at once. I have 1 file:
examples.desktop

I want to make a new folder named "other" and put that file in it. How can i do this in 1 command?

atm, im doing this:

```
mkdir other

mv examples.desktop other
```

---

### Post by GWBouge on 2012-03-03
You can combine the commands with '&&'.  If the first command completes successfully, it'll do the second.

```
mkdir other && mv examples.desktop other
```

---

### Post by mferarri on 2012-03-03
> **GWBouge said:**
> You can combine the commands with '&&'.  If the first command completes successfully, it'll do the second.

```
mkdir other && mv examples.desktop other
```

wow, thanks dude. you rock.

---

