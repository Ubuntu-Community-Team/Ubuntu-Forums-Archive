---
title: "wc -l with just the number"
date: 2007-12-04
forum: Programming Talk
---

### Post by DouglasAWh on 2007-12-04
I want to use wc -l in bash, but only want to return the number, not the file I searched for and put that in a var.  Is there a flag to do that or is there a short little code snippet I could use to make such a thing happen?

Thanks!

---

### Post by ghostdog74 on 2007-12-04
several ways
```

# set -- $(wc -l file)
# echo $1
15

```

```

var=$(wc -l |awk '{print $1}')

```

```

#var=$( wc -l file | cut -d" " -f1)

```

---

### Post by DouglasAWh on 2007-12-04
great!  didn't know about the $1

so, I guess the next question is, how do I count the lines is a variable?  I had a variable first and decided printing to a file and then counting that file would work, but it seems like I'm walking along two sides of a triangle.

Thanks again!

---

### Post by ghostdog74 on 2007-12-05
> **DouglasAWh said:**
> great!  didn't know about the $1

so, I guess the next question is, how do I count the lines is a variable?  I had a variable first and decided printing to a file and then counting that file would work, but it seems like I'm walking along two sides of a triangle.

Thanks again!

not very clear on what you want to do.
show an example of what you want to do

---

### Post by DouglasAWh on 2007-12-05
```

dirlist=`find /public/html/cosi -name wiki.phtml -exec echo "<a href=\"http://www.ibiblio.org/"{}"\">www.ibiblio.org/"{}"</a><br /><br />" \; | sed -e s!/public/html/!!g -e s/wiki.phtml/index.php/g`

```

I'd like to just count the lines in dirlist.  I think I could do this with a loop, but I don't have it down yet.  I'm working on it.

---

### Post by ghostdog74 on 2007-12-05
what is the actual output of this:
```

find /public/html/cosi -name wiki.phtml -exec echo "<a href=\"http://www.ibiblio.org/"{}"\">www.ibiblio.org/"{}"</a><br /><br />" \; | sed -e s!/public/html/!!g -e s/wiki.phtml/index.php/g

```

you can still pipe it   to wc -l  , however, show that output first before we suggest anything else.

---

### Post by DouglasAWh on 2007-12-05
Here's the whole script at current.

```

#!/bin/bash

dirlist=`find /public/html/cosi -name wiki.phtml -exec echo "<a href=\"http://www.ibiblio.org/"{}"\">www.ibiblio.org/"{}"</a><br /><br />" \; | sed -e s!/public/html/!!g -e s/wiki.phtml/index.php/g`

echo "$dirlist" > /public/html/inls668/n00b.txt

set -- $(wc -l /public/html/inls668/n00b.txt)

# for item in $dirlist {$i=0, $i++}

# echo $i

echo "<div id=\"content\">$dirlist<br /><br />Total Number of Wikis Hosted at ibiblio.org: $1</div>" > /public/html/inls668/wiki.html

```

I guess the problem is where to do the pipe to wc, since I've already got a -exec and a pipe to sed.

Here's the output of the entire script: [http://www.ibiblio.org/inls668/wiki.html](http://www.ibiblio.org/inls668/wiki.html)

Notice the commented out loop.  It's in no way a finished product.

Thanks again!

---

### Post by geirha on 2007-12-05
This should count all wiki.phtml files in /public/html/cosi/:
```
numwikis=`find /public/html/cosi -name wiki.phtml | wc -l`
```

Do you really need to store the output of that find|sed in a variable?

---

### Post by ghostdog74 on 2007-12-05
so what did you get for this:
```

set -- $(wc -l /public/html/inls668/n00b.txt)
echo $1

```

---

### Post by ghostdog74 on 2007-12-05
> **DouglasAWh said:**
> 
I guess the problem is where to do the pipe to wc, since I've already got a -exec and a pipe to sed.
you just add a pipe  wc -l after the sed and see what happens. try that

---

### Post by DouglasAWh on 2007-12-05
> **ghostdog74 said:**
> so what did you get for this:
```

set -- $(wc -l /public/html/inls668/n00b.txt)
echo $1

```

3.  It's the number that is generated in the HTML fragment in the URL I posted: [http://www.ibiblio.org/inls668/wiki.html](http://www.ibiblio.org/inls668/wiki.html)


As somewhat of an aside, I've been told (in person, no less) that I should use some sort of readdir instead of find.  I think this is opendir in Perl, but I only know bash and PHP.

---

### Post by geirha on 2007-12-05
> **DouglasAWh said:**
> 3.  It's the number that is generated in the HTML fragment in the URL I posted: [http://www.ibiblio.org/inls668/wiki.html](http://www.ibiblio.org/inls668/wiki.html)


As somewhat of an aside, I've been told (in person, no less) that I should use some sort of readdir instead of find.  I think this is opendir in Perl, but I only know bash and PHP.

Then perhaps the person was referring to [readdir](http://php.net/readdir)() in PHP, since you are creating HTML-code (which is quite common to use PHP to do)

---

