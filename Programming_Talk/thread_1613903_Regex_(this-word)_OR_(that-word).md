---
title: "Regex: (this-word) OR (that-word)"
date: 2010-11-05
forum: Programming Talk
---

### Post by Menolly on 2010-11-05
Hello all!
I know you can use java to search for this-letter or that-letter (for example [ab] will be true for a or b, or gr[ae]y will be true for gray or grey), but can I search for this-word or that-word (for example returning true for either "help" or "assist"). I tried googling the problem, but I'm not even sure how to word my search.
Thanks!

---

### Post by Some Penguin on 2010-11-05
```

Pattern fooOrBarPattern = Pattern.compile("(foo)|(bar)");

```

---

### Post by yc2 on 2010-11-05
This is PHP regex, but any regex will do it I think. The pattern is (rose|tulip).
rose or tulip is exchanged for flower
```
$string = " cat rose dog tulip parrot ";
$string = preg_replace("/(rose|tulip)/", "flower", $string);
echo $string;
// Will echo: cat flower dog flower parrot 

```
You can also ask for them to be delimited as individual words:
(\brose\b|\btulip\b)

---

