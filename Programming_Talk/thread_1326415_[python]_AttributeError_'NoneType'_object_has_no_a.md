---
title: "[python] AttributeError: 'NoneType' object has no attribute 'name'"
date: 2009-11-14
forum: Programming Talk
---

### Post by altonbr on 2009-11-14
```
for category in categories:
    if cat.name == category.name:
        print 'Yes'
    else:
        print 'No'
```

results in

>     if cat.name == category.name:
AttributeError: 'NoneType' object has no attribute 'name'

I'm first and foremost a PHP programmer and in PHP, we're allowed to run if statements on null objects...

How can I run this if statement in python where 'cat.name' may or may not be empty/null and 'category.name' will always be full as it's parsing through a loop...

---

### Post by diesch on 2009-11-14
The problem is that either *cat* or *category* is *None*. You have to check that before you access *cat.name* or *category.name*, e.g.

```
if cat is not None and category is not None: ...
```

---

### Post by Can+~ on 2009-11-14
> **altonbr said:**
> I'm first and foremost a PHP programmer and in PHP, we're allowed to run if statements on null objects...

And you can do that too in python

[PHP]>>> None == None
True[/PHP]

The thing is one of your variables (apparently, "cat") is None, so you're basically saying

[PHP]None.name[/PHP]

Which is, of course, a wrong behaviour.

---

