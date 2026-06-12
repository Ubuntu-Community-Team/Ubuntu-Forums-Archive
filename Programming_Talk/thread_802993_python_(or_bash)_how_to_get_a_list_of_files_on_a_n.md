---
title: "python (or bash) how to get a list of files on a networked (ubuntu) computer"
date: 2008-05-21
forum: Programming Talk
---

### Post by days_of_ruin on 2008-05-21
Everytime I try to do it with ssh it messes up because it switches to
that computer which just messes everything up.Is there a way to do it
without messing anything up.

---

### Post by geirha on 2008-05-22
Could you elaborate on how it gets "messed up"?

And how about doing it this way?
```

ssh other_host "find /" >other_host.list

```

---

### Post by days_of_ruin on 2008-05-22
> **geirha said:**
> Could you elaborate on how it gets "messed up"?

And how about doing it this way?
```

ssh other_host "find /" >other_host.list

```
So can other_host.list be anything?How do I access it?

---

### Post by days_of_ruin on 2008-05-22
Okay it saves it to a file.So I just have to open the file to get the data:D
Thanks man!I owe you one.

---

