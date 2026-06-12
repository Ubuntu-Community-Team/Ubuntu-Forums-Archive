---
title: "Reg exp: String not in pattern (PHP)"
date: 2011-03-19
forum: Programming Talk
---

### Post by yc2 on 2011-03-19
Hello,

I have problems matching patterns NOT containing a string. Below are two examples and further down their output.

The first works as intended: if the preceding fruit is not 'lemon' or 'grapefruit', the following word is changed to sweet.

In the second example I want to change any HTML-tag where x is not = 'grapefruit' or 'lemon' to x=sweet.
Ie I _want_ the following output (#2): (but I don't get it)
```
desired output (#2)
<div x=sweet> <span x=sweet> <div x=grapfruit> <div x=sweet>  <span x=lemon>
``` 

As shown in the example the regex catches nothing. I can't get ex. #2 to work.

Brain meltdown now. Assistance appreciated :)

Thanks


code:
```

#1
$string = "mango-sour, banana-sour, lemon-sour, papaya-sour, grapefruit-sour, cherry-sour";
$patt_tst = "/(?<!lemon|grapefruit)-sour/";
echo preg_replace($patt_tst, "\\1-sweet", $string) . "\n";

#2
$string = "<div x=mango> <span x=mango> <div x=grapfruit> <div x=banana>  <span x=lemon> ";
$patt_tst = "/(<[^>]*?)(?>!lemon|grapefruit)[^>]*?>/";
echo preg_replace($patt_tst, "\\1\\2sweet>", $string) . "\n";

```

output:
```

#1
mango-sweet, banana-sweet, lemon-sour, papaya-sweet, grapefruit-sour, cherry-sweet

#2
<div x=mango> <span x=mango> <div x=grapfruit> <div x=banana>  <span x=lemon> 

```

---

