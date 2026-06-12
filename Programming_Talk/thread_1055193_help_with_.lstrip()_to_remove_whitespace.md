---
title: "help with .lstrip() to remove whitespace"
date: 2009-01-30
forum: Programming Talk
---

### Post by pluckypigeon on 2009-01-30
```

for i in range(111111,999999):
      print  "test", i 

```


output > test 111111
..and so on


I'm trying to remove the whitespace between test and the numbers.

I tried implementing ".lstrip" but I can't work out where to put it.

Any help would be really appreciated

Thanks in advance.

---

### Post by pluckypigeon on 2009-01-30
Nevermind

I forgot to convert the integer 

```


for i in range(111111,999999):
	print "test" + str(i) .lstrip()  


```

---

### Post by rajeev1204 on 2009-01-30
There is no need to use lstrip here.

The + operator will remove the whitespace for you and concatenate the strings

---

### Post by pluckypigeon on 2009-01-30
> **rajeev1204 said:**
> There is no need to use lstrip here.

The + operator will remove the whitespace for you and concatenate the strings

:redface: I was just coming back to change that before anyone saw...

thanks anywho:)

---

### Post by snova on 2009-01-30
> **pluckypigeon said:**
> I'm trying to remove the whitespace between test and the numbers.

I tried implementing ".lstrip" but I can't work out where to put it.

It wouldn't matter where you put it. The **print** statement automatically puts a space in between each of its arguments. To get around it you'd have to use string concatentation, as you've already figured out.

---

### Post by fiddler616 on 2009-01-30
> **snova said:**
> The **print** statement automatically puts a space in between each of its arguments. To get around it you'd have to use string concatentation, as you've already figured out.
Suppose I *wanted* whitespace, would it be with commas instead of +s?

---

### Post by rajeev1204 on 2009-01-31
> **fiddler616 said:**
> Suppose I *wanted* whitespace, would it be with commas instead of +s?


Well,a comma is always required to print multiple strings.But if you need an extra whitespace,put it in like so ...

```
print "hello    ","forums"
```

This will print extra whitespaces after hello as you can see from code.

---

### Post by WW on 2009-01-31
> **pluckypigeon said:**
> Nevermind

I forgot to convert the integer 

```


for i in range(111111,999999):
	print "test" + str(i) .lstrip()  


```
You could also use a format string:

```

for i in range(111111,999999):
	print "test%d" % i 


```

---

### Post by rajeev1204 on 2009-02-01
> **WW said:**
> You could also use a format string:

```

for i in range(111111,999999):
	print "test%d" % i 


```

Ya this is the best way.Thanks for this.

---

