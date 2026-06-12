---
title: "sed return regular expression"
date: 2009-05-30
forum: Programming Talk
---

### Post by wesg on 2009-05-30
I'm writing a script that uses webpages to collect data, and I need to find numbers between a specific string, which is perfect for regex.

The string I'm searching in is show/xxxx/summary.html (it's a Google search result) and I want to extract the xxxx within that. 

So far I've used the variable declaration of ```
echo $var | sed 's/show\/(.*)\/summary\.html/1/' 
``` but saves the entire $var variable again. How can I get just the numbers?

---

### Post by mobilediesel on 2009-05-30
> **wesg said:**
> I'm writing a script that uses webpages to collect data, and I need to find numbers between a specific string, which is perfect for regex.

The string I'm searching in is show/xxxx/summary.html (it's a Google search result) and I want to extract the xxxx within that. 

So far I've used the variable declaration of ```
echo $var | sed 's/show\/(.*)\/summary\.html/1/' 
``` but saves the entire $var variable again. How can I get just the numbers?

```
echo $var | sed 's/show\/[COLOR="Red"]\[/COLOR](.*[COLOR="Red"]\[/COLOR])\/summary\.html/[COLOR="Red"]\[/COLOR]1/' 
```

I colored my additions in red. those backslashes should do the trick.

---

### Post by wesg on 2009-05-30
Thanks, mobilediesel. I realized that the variable I was using is actually a single long line, and sed returns lines with the matching results, so that's why I got the whole thing. How can I get just pieces of the line?

---

### Post by ghostdog74 on 2009-05-30
awk
```

# awk '/summary\.html/{gsub(/.*show\/|\/summary.html/,"");print}' file
xxxx


```

---

### Post by wesg on 2009-05-30
thanks ghostdog, this gets me closer. RIght now it prints everything from the number I want, but goes to the end of the file. How can I get it to clip everything after the number too?

---

### Post by slavik on 2009-05-30
.*?

---

### Post by stroyan on 2009-05-30
You can get the result you want with sed my adding ".*" before the leading "show" and after the trailing "html".

```
echo $var | sed 's/.*show\/\(.*\)\/summary\.html.*/\1/'
```

If the input had some other lines without the pattern in them then you would use a "-n" option and a "p" directive in the sed command to print only matching lines.
```
echo $var | sed -n 's/.*show\/\(.*\)\/summary\.html.*/\1/p'
```

If you already have a single line with the pattern in it, then you can easily strip off the unwanted part of $var using bash parameter expansion.
The "##" and "%%" substitutions remove leading and trailing patterns.

```
V1="${var##*show/}"; V2="${V1%%/summary.html*}"; echo "${V2}"
```

---

### Post by wesg on 2009-05-30
OK, I figured it out. I used the earlier solution, then added an awk delimiter to only print the first part. Thanks for all your help.

---

### Post by ghostdog74 on 2009-05-30
> **wesg said:**
> thanks ghostdog, this gets me closer. RIght now it prints everything from the number I want, but goes to the end of the file. How can I get it to clip everything after the number too?

put .* after summary\.html, eg summary\.html.*

---

### Post by wesg on 2009-05-31
One last question...

I found egrep, which is actually what I should have been using before hand, but I need help with a regex statement. 

```
$search"([^a]+)"
```

is my current expression, and instead of not including a, I want to not include the closing anchor tag (</a>). Unfortunately, this type of expression doesn't seem to allow that. How can I make the expression match everything up to the closing anchor tag?

---

### Post by ghostdog74 on 2009-05-31
> **wesg said:**
> One last question...

I found egrep, which is actually what I should have been using before hand, but I need help with a regex statement. 

```
$search"([^a]+)"
```

egrep+grep+sed+cut+wc+etc == awk

> 
is my current expression, and instead of not including a, I want to not include the closing anchor tag (</a>). Unfortunately, this type of expression doesn't seem to allow that. How can I make the expression match everything up to the closing anchor tag?
show examples of what you want to match.

---

### Post by slavik on 2009-05-31
> **ghostdog74 said:**
> egrep+grep+sed+cut+wc+etc == awk


throw a shell in there and you got perl :P

---

