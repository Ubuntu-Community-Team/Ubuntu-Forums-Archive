---
title: "Quick PHP strings question"
date: 2010-03-10
forum: Programming Talk
---

### Post by yaztromo on 2010-03-10
I'm trying to escape a single quote within single quotes. The PHP website says use a backslash, so why does the following code throw a parse error?

```

$test_string='escaping a single quote like so: \'';
echo ($test_string);

```

---

### Post by v8YKxgHe on 2010-03-10
It doesn't, simple. Code will work just fine. Your parse error is somewhere else, what is the full code?

Also, as echo is a language construct and not a function you do not need the parenthesis. i.e. echo $foo; will work just fine.

---

