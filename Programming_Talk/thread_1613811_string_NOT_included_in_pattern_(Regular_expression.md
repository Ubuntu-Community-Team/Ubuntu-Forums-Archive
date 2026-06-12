---
title: "string NOT included in pattern (Regular expressions, PHP)"
date: 2010-11-04
forum: Programming Talk
---

### Post by yc2 on 2010-11-04
Hello,

I use preg_replace, PHP5.

I wish an entire string NOT to be present in the search pattern. For example, I wish this:
```
xxxmango-sourxxxbanana-sourxxxlemon-sourxxxpapaya-sour

```
to be changed into this:
```
xxxmango-sweetxxxbanana-sweetxxxlemon-sourxxxpapaya-sweetxxx

```
i.e.
The pattern xxx[any word]-sour should be changed into xxx[any word]-sweet except where [any word]=lemon

My original problem regards parsing urls and not fruit ;)

Can someone please give the corresponding preg_replace command or similar.

Thanks.

I read this, but I just couldn't get it work
[http://stackoverflow.com/questions/1172873/regex-to-match-a-pattern-but-exclude-a-set-of-words](http://stackoverflow.com/questions/1172873/regex-to-match-a-pattern-but-exclude-a-set-of-words)

---

### Post by yc2 on 2010-11-05
Finally got it, by the help of this page:
[http://www.phpro.org/tutorials/Introduction-to-PHP-Regex.html#10](http://www.phpro.org/tutorials/Introduction-to-PHP-Regex.html#10)
```
$string = "xxxmango-sourxxxbanana-sourxxxlemon-sourxxxpapaya-sour";
echo preg_replace("/(?<!lemon)-sour/", "\\1-sweet", $string);
// echos: xxxmango-sweetxxxbanana-sweetxxxlemon-sourxxxpapaya-sweet

```

---

