---
title: "BASH odd behavior question"
date: 2010-09-29
forum: Programming Talk
---

### Post by jamesisin on 2010-09-29
I understand *type f* to mean file and *type d* to mean directory.  However, when I run this command:

```
find . ! -type f -name \*.cue
```

I get only directory results yet when I run this command:

```
find . ! -type d -name \*.cue
```

I get only file results.

How/why does the recursion alter the behavior of *find*?

---

### Post by Bachstelze on 2010-09-29
! means logical NOT. ;)

---

### Post by jamesisin on 2010-09-29
Oh, I see.  I thought it (*!*) related to recursion.  Looks like *find* is recursive by default and I was just negating (oppositizing) my *type* argument.

---

### Post by Bachstelze on 2010-09-29
Yup. You can run find with [font=monospace]-d 0[/font] if you want to run it non-recursively.

---

### Post by jamesisin on 2010-09-29
Very good.  I don't, but it's good to know.

Can you answer a related question?

If I want *find* to return an absolute path, how would I alter my syntax above?

I'd like *find* to create an array loaded with the absolute file paths according to my criteria.

---

### Post by amauk on 2010-09-29
use an absolute path when running find

instead of
find . (find in current directory and below)
use
find /path/to/dir (find in /path/to/dir and below)

use relative paths as input
get relative paths as output

---

### Post by jamesisin on 2010-09-29
> **amauk said:**
> use an absolute path...
find /path/to/dir

If I substitute **/home/[username]/Desktop/folderimworkingin** in my code above (replacing the .) *find* stops acting on sub-folders, it stops behaving recursively.

---

### Post by jamesisin on 2010-09-29
However, if I use **/home/[username]/Desktop/folderimworkingin/*** I do get recursion.  Is there a danger in using this wildcard in this manner?

---

### Post by amauk on 2010-09-29
> **jamesisin said:**
> If I substitute **/home/[username]/Desktop/folderimworkingin** in my code above (replacing the .) *find* stops acting on sub-folders, it stops behaving recursively.

it shouldn't
you sure you're not passing anything else to find that restricts it's behaviour
(-maxdepth, etc.)

---

### Post by jamesisin on 2010-09-29
> **amauk said:**
> you sure you're not passing anything else

I am testing exactly the line of code displayed in the original post (though I have substituted *-type f* for *! -type d*).

---

### Post by jamesisin on 2010-09-29
Never mind.  My evil twin is being an idiot.

---

