---
title: "Help with SED"
date: 2010-06-08
forum: Programming Talk
---

### Post by msjones on 2010-06-08
Im working on a program that integrates with our case management system to send SMS messages to our clients via clickatel. Im struggling a little with sed and would greatly appreciate some help.

When our users enter a mobile number they are entering it in standard format with a space: 07816 012345. I need to turn it into the following: 447816012345.

I have no problem removing the space, its just that initial zero. How do I tell sed to replace the fisrt zero in the string, but ignore any others that may occur?

Thanks

---

### Post by Some Penguin on 2010-06-08
In a regular expression, ^ usually matches beginning of string if the ^ is the very first character.
You may also want to consider leading word boundaries before the 0.

---

### Post by Bachstelze on 2010-06-08
More specifically:

```
firas@tsukino ~ % echo "07816012345"| sed 's/^0/44/'
447816012345

```

---

### Post by disabledaccount on 2010-06-08
#@!$.... errror resistant version:
```
~$: echo "phone: 0 78-160-123.45 a" | sed -n 's_[^0-9]__g;s_^0_44_p'
```;)

---

### Post by DaithiF on 2010-06-08
You'll probably want to strip out any non-digit characters, whether spaces, parentheses, dashes, etc that a user might add.  Using tr in combination with sed would be one way to do this:

e.g.
```
for number in "07816012345" "(0781) 601 2345" "0781-601-2345" " (0781) 601-2345 "
do
echo "$number" | tr -d -c '[0-9]' | sed 's/^0/44/'; echo
done

447816012345
447816012345
447816012345
447816012345

```

---

### Post by geirha on 2010-06-08
If you are using bash, you can also do it without sed
```

#!/bin/bash
read -p "Phone number: " number
n=44${number#0} n=${n// }
echo "[$number] -> [$n]"

```
If you want to remove any non-digit instead of just spaces, like DaithiF mentions, then
```
n=${n//[!0-9]}
```

[http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)

---

### Post by disabledaccount on 2010-06-08
> **DaithiF said:**
> You'll probably want to strip out any non-digit characters, whether spaces, parentheses, dashes, etc that a user might add.  Using tr in combination with sed would be one way to do this: (...)There's no need to use tr -> see my sed line -> it strips out everything but digits ;)

But, **geirha** gave the best solution till now - no pipes, no forking ;)

---

