---
title: "simple bash idiocy"
date: 2010-12-12
forum: Programming Talk
---

### Post by koszta on 2010-12-12
Hi I am totally missing something...
I have a file that has double quotes in it and I want to escape them first (so that I can read lines in bash afterwards... how do I do that? 
 
I tried :

sed "s/\"/\\\"/g" file.php 
 
and it did nothing

I tried tr '\"' '\\\"' < file.php

and nothing :(
I know it is stupid ...what am i missing ? 

thnx

---

### Post by Arndt on 2010-12-12
> **koszta said:**
> Hi I am totally missing something...
I have a file that has double quotes in it and I want to escape them first (so that I can read lines in bash afterwards... how do I do that? 
 
I tried :

sed "s/\"/\\\"/g" file.php 
 
and it did nothing

I tried tr '\"' '\\\"' < file.php

and nothing :(
I know it is stupid ...what am i missing ? 

thnx

I think you're doing something unnecessarily roundabout if you first escape the " in the file (and what happens to an already escaped "?), but I don't know what you will do with the file anyway.

This works:

```
sed "s/\"/\\\\\"/g"
```

and this:

```
sed 's/"/\\"/g'
```

I don't think 'tr' can replace one character with several.

---

### Post by trent.josephsen on 2010-12-12
> **koszta said:**
> I have a file that has double quotes in it and I want to escape them first (so that I can read lines in bash afterwards...

I wish you would clarify this, because it sounds like you're trying to do something completely unnecessary.

---

### Post by saulgoode on 2010-12-12
> **koszta said:**
> 
I tried :

sed "s/\"/\\\"/g" file.php 
 
and it did nothing
:
:
I know it is stupid ...what am i missing ? 
Since you are using soft quotes around the entire substitution expression, BASH is stripping the escapes before they are passed to 'sed'.

Instead, try using hard quoting:

 **[INDENT]sed 's/\"/\\\"/g' file.php[/INDENT]**

---

### Post by Arndt on 2010-12-12
> **saulgoode said:**
> Since you are using soft quotes around the entire substitution expression, BASH is stripping the escapes before they are passed to 'sed'.

Instead, try using hard quoting:

 **[INDENT]sed 's/\"/\\\"/g' file.php[/INDENT]**

Similar to what I wrote. In what way is it better?

---

### Post by saulgoode on 2010-12-12
> **Arndt said:**
> Similar to what I wrote. In what way is it better?
Sorry, I had just woken from a nap and hadn't read your post accurately. Your way is actually better because it removes some unnecessary escaping.

---

