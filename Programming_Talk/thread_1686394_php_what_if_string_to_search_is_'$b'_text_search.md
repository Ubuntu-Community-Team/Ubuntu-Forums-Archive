---
title: "php what if string to search is '$b' text search?"
date: 2011-02-12
forum: Programming Talk
---

### Post by sdowney717 on 2011-02-12
like do this 

 $pos = strpos($fileline, "$b");

will that work since the editor is showing $b as a variable?
what I want is for strpos to look for $b itself as text.
do you backslash escape it?

---

### Post by Vaphell on 2011-02-12
not that i know anything about php but if it's anything like bash with strings try single quotes '$b'
[http://php.net/manual/en/language.types.string.php](http://php.net/manual/en/language.types.string.php)
according to that page ' ' is literal string and " " is string with variable expansion.
of course escaping works too.

---

### Post by s.fox on 2011-02-13
Hello,

I would use single quotes as it will be treated as a literal string.

-s.fox

---

### Post by xtremethegreat1 on 2011-02-13
You wanna use single quotes. Double quotes will just show the value of $b in quotes.
Example:

```
$b = 'Hello'
echo $b;
```

Output:
```
Hello
```

```
echo '$b';
```

Output:
```
$b
```

```
echo "$b";
```

Output:
```
Hello
```

---

