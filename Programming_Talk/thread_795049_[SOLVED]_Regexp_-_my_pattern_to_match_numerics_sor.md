---
title: "[SOLVED] Regexp - my pattern to match numerics sort of works, but not 100%"
date: 2008-05-15
forum: Programming Talk
---

### Post by Asham on 2008-05-15
Hello fellow developers,

I am trying to identify numbers from a string but it's not going so well.

The text, which is a servlet request param, can be in the following formats:

1. "foo [COLOR="green"]XXX YY[/COLOR] bar"
2. "[COLOR="green"]XXX YY[/COLOR] foo bar"
3. "foo bar [COLOR="green"]XXX YY[/COLOR]"

XXX YY are always next to eachother but sometimes comes without a space inbetween, eg. XXXYY.


I thought this regexp would work, but it doesn't. Only sometimes.
```

String searchTerms = request.getParameter("query");
final String regexp = "^(\\d{3}\\s?\\d{2})+$";
Pattern pattern = Pattern.compile(regexp);
Matcher matcher = pattern.matcher(searchTerms);

String num;
if (matcher.matches()) {
	num = matcher.group();
}

```

Do you see where I messed up?

Adam

---

### Post by meastp on 2008-05-15
```
"^(\\d{3}\\s?\\d{2})+$"
```

I'm only guessing here, as I don't have any documentation at hand, but remember that ^ means beginning of string. Therefore, your regex would match the second string, but not the first and third.

I'm going to write some pseudocode:

"^[^0-9]*([0-9][0-9] [0-9][0-9][0-9])"

or

"([0-9][0-9] [0-9][0-9][0-9])"

(you could use + and *, but those are more greedy)

---

### Post by aks44 on 2008-05-15
As already pointed out by meastp, ^ matches the beginning of the string. Additionally, $ matches the end of the string.


Just remove both and you'll get the RE you want.


Also, I'm not sure you really want that + to be there (which means: one or more).

---

### Post by Asham on 2008-05-16
Nope, it still doesn't match the numbers. :(

I removed ^ and +$ as you suggested. 

Any other ideas? I'm not very familiar with regexps!

---

### Post by meastp on 2008-05-16
try [http://www.regular-expressions.info/tutorial.html](http://www.regular-expressions.info/tutorial.html)

It's a really good tutorial and reference.

If this did not match:

```
"([0-9][0-9] [0-9][0-9][0-9])"
```

Then it is not the regex that is wrong, unless Java(if that's the language you are using) has very different regex notation.

It looks like you are referring to a object, and not its members, or the first result every time.
```
num = matcher.group();
```

In python ```
.group()[0]
``` would give the first result
```
.group()[1]
``` would give the second result

and loop
```

for item in matches.groups() :
  print item

```

But I'm not very familiar with Java, so I'm not sure.

---

### Post by Asham on 2008-05-16
Thanks guys! The fault is on me, I didn't read the Java API properly.

Using matcher.[COLOR="Green"]find()[/COLOR] instead of matcher.[COLOR="Red"]matches()[/COLOR] and the method behaves as I want it to.


It's friday today so I hope you can forgive me for stealing some of your time. ;)

---

### Post by meastp on 2008-05-16
no worries! Glad you sorted it out :)

---

