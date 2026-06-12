---
title: "preg_match number has only 0's and 8's (PHP)"
date: 2011-08-22
forum: Programming Talk
---

### Post by tocleora on 2011-08-22
I need a preg_match that will verify a number only contains 0's and 8's.  For example:

080 would be true
380 would be false
088 would be true
000880 would be true
1238 would be false

Sorry for over clarifying I'm not sure I'm explaining it well so I wanted to make sure.  Can anyone help?

---

### Post by sisco311 on 2011-08-22
*[^08]* will match any character, but a 0 or 8. I don't know much about PHP, but this seams to work:
[php]
$regexp='*[^80]*';
$number="000801";

if (preg_match($regexp, $number)){
    print_r("false");
}
else{
    print_r("true");
}
[/php]

---

### Post by tocleora on 2011-08-22
That did the trick! Thank you very much!

---

### Post by v8YKxgHe on 2011-08-23
Don't use regex for this, use [http://php.net/strpos](http://php.net/strpos)

---

