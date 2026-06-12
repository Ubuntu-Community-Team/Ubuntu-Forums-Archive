---
title: "php regex for finding SQL parameters"
date: 2012-03-08
forum: Programming Talk
---

### Post by lykwydchykyn on 2012-03-08
I'm trying to write a regex in PHP for finding parameters in a postgresql SQL statement.  Basically, I need a regex for finding words that start with one *and only one* colon, since typecasting in postgresql can use double colons.  For example, in this SQL statement:
```

SELECT entree_name, cost::money FROM menu WHERE meal=:meal

```

I would want the regex to grab "meal" but not "money".

What I have so far is this:
```

/:(\w+)/

```
But of course that grabs "money" too.

Any ideas?

---

### Post by lykwydchykyn on 2012-03-08
I figured it out.

I needed:
```

/[^::]:(\w+)/

```

---

