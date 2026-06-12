---
title: "Confusion about for clause"
date: 2009-04-21
forum: Programming Talk
---

### Post by huangyingw on 2009-04-21
hello, to explain, I write a simplest script as follow:
=========================================
#! /bin/sh
dir=/home/huangyingw/folder/
for file in "`find ${dir} -type f`";
do 
		echo prefix${file}
done
=========================================
the contents under /home/huangyingw/folder/ are two meaningless files:a,b.
the actua result is, 
=========================================
prefix/home/huangyingw/folder/b /home/huangyingw/folder/a
=========================================
it seems that the "for" clause would pass all the value once to file, then do the do loop only once. Is my understaind correct?
In fact, I am expecting following result. If I want to get following result, where should I go?
=========================================
prefix/home/huangyingw/folder/b
prefix/home/huangyingw/folder/a
=========================================

---

### Post by Bodsda on 2009-04-21
Hi, in future try to use ```
[ /code] tags around your code to help display it, what you need is a newline character near the end, try this

[code]
#! /bin/sh
dir=/home/huangyingw/folder/
for file in "`find ${dir} -type f`";
do
echo prefix${file}
echo -e "\n"
done

```

Hope this helps,

Bodsda

p.s I havent tested the whole thing, but i think it should work :)

---

### Post by ghostdog74 on 2009-04-21
use the find command with a while loop
```

find .... |while read FILE
do

done

```
using for loop with find will break on files names with spaces if not careful.

---

### Post by Arndt on 2009-04-21
> **Bodsda said:**
> Hi, in future try to use ```
[ /code] tags around your code to help display it, what you need is a newline character near the end, try this

[code]
#! /bin/sh
dir=/home/huangyingw/folder/
for file in "`find ${dir} -type f`";
do
echo prefix${file}
echo -e "\n"
done

```

Hope this helps,

Bodsda

p.s I havent tested the whole thing, but i think it should work :)

I rather think that it's the double quotes that do it - they make the whole result from the ` ` thing into one string.

And I haven't tested it either.

---

### Post by somnusnoctem on 2009-04-21
You could try this:

```

#! /bin/sh
dir=/home/huangyingw/folder/
find "$dir" -type f | while read file
do
echo prefix"$file"
done

```

Find and for loops don't always play nicely together. If you have newline characters in your filenames, you might even need to try out something different than the above. The following is a good place to look: [http://www.macgeekery.com/tips/cli/handling_filenames_with_spaces_in_bash](http://www.macgeekery.com/tips/cli/handling_filenames_with_spaces_in_bash)

---

### Post by huangyingw on 2009-04-26
> **Bodsda said:**
> Hi, in future try to use ```
[ /code] tags around your code to help display it, what you need is a newline character near the end, try this

[code]
#! /bin/sh
dir=/home/huangyingw/folder/
for file in "`find ${dir} -type f`";
do
echo prefix${file}
echo -e "\n"
done

```

Hope this helps,

Bodsda

p.s I havent tested the whole thing, but i think it should work :)
Yes, thank for your guide. I would use the code quote when applying new thread.

---

