---
title: "vim: search/replace sentences (not words)"
date: 2010-10-14
forum: Programming Talk
---

### Post by l3ecl on 2010-10-14
in vim, what's the most efficient way of choosing sentences that meet XYZ criteria and deleting the rest?

for example, I would like to delete all sentences that do not start with void. 

> void set_first_name(string in_first_name);
 string first_name();
 void set_last_name(string in_last_name);
 string last_name();
 void set_composer_yob(int in_composer_yob);
 int composer_yob();
 void set_composer_genre(string in_composer_genre);
 string composer_genre();
 void set_ranking(int in_ranking);
 int ranking();
 void set_fact(string in_fact);

---

### Post by r-senior on 2010-10-14
Does it have to be in vim? Why not just drop back to the shell and grep it:

```

$ grep ^void myFile > myNewFile

```

---

### Post by spjackson on 2010-10-14
> **l3ecl said:**
> in vim, what's the most efficient way of choosing sentences that meet XYZ criteria and deleting the rest?

for example, I would like to delete all sentences that do not start with void.
I don't have an answer for sentences. However, to delete all **lines** that do not begin with void do
```

:v/^void/d

```

---

### Post by nebu on 2010-10-14
its pretty simple
--
if u want to leave empty lines
```

:%s/^\s*void.*//

```

if not
```

:%s/^\s*void.*\n//

```



---EDIT
(oops... i read ur question wrong!! spjackson has answer for u!! :P)

---

