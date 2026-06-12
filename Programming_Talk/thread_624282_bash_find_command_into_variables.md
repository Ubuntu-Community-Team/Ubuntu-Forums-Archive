---
title: "bash find command into variables"
date: 2007-11-26
forum: Programming Talk
---

### Post by DouglasAWh on 2007-11-26
alright, I found [http://lowfatlinux.com/linux-find-files.html](http://lowfatlinux.com/linux-find-files.html) which was useful, and a few tangential posts here, but nothing that really gets to the meat of this situation.  

I can do
```

#!/bin/bash
altDir=$(find /public/html/cosi -name "wiki.phtml")
echo $altDir

```

but, what I'd like to do is give each file path it's own variable, so that I can built a web page on the fly


Something like the following (though I'm not sure it will work...just throwing the line together off the top of my head)
```

echo "<a href=\"$var\">doman.org/$var</a>

```

Obviously, I'd have to truncate the returned file path at after /html/, but I'll worry about that later.  I think that the URL I gave in the first sentence will help me with that issue.


And while I'm at it, does anyone know if wiki.phtml is in every version of mediawiki?  I've posted about this elsewhere, but since it's a similar issue, I thought I'd mention here too.

THANKS!  (on both questions!)

---

### Post by nanotube on 2007-11-26
make a list out of it, then loop over the list:

quick example (may be slightly off):

```
altDir=( $(find /public/html/cosi -name "wiki.phtml") )
for ((i=0; i < ${#altDir[*]} ; i++))
do
    echo <a href=\"${altDir[$i]}\">doman.org/${altDir[$i]}</a>
done
```

to simplify the loop, you can use the "item in list" type of loop:
```
altDir=( $(find /public/html/cosi -name "wiki.phtml") )
for item in ${altDir[*]}
do
    echo <a href=\"${item}\">doman.org/${item}</a>
done
```

and for "future reference", i might direct you toward the "advanced bash scripting guide" :)

---

### Post by DouglasAWh on 2007-11-27
neither of the above work.  It keeps spitting out a newline error.  I'm looking into it and will post when resolved.

EDIT: ok, item gets made correctly (echoed out item).  Thus, I need to figure out the newline issue AND figure out how to deal with dir with spaces.

---

### Post by mssever on 2007-11-27
> **DouglasAWh said:**
> figure out how to deal with dir with spaces.

Unless you know otherwise, always surround variable references in double quotes. That will prevent unwanted shell expansion. Examples: ```
"$var"
"This is a string containing $var"
cp "$var1" "$var2"
```

---

### Post by DouglasAWh on 2007-11-27
> **mssever said:**
> Unless you know otherwise, always surround variable references in double quotes. That will prevent unwanted shell expansion. Examples: ```
"$var"
"This is a string containing $var"
cp "$var1" "$var2"
```

I'm not sure you understood what I meant by dir with spaces.  I meant that /dir/subdir/sub dir/wiki.phtml shows up as 

/dir/subdir/sub
dir/wiki.phtml

The find commands locates them correctly, but at current the items do not work correctly.

Now, your point is still valid, but since you quoted that particular statement of mine, I thought I would clarify.

---

### Post by ghostdog74 on 2007-11-27
another way
```

find /path -name "yourfile" -exec echo {} "testing" \;    

```
run the above and see what it looks like, then adapt the above to your actual requirement.

---

### Post by DouglasAWh on 2007-11-27
> **ghostdog74 said:**
> another way
```

find /path -name "yourfile" -exec echo {} "testing" \;    

```
run the above and see what it looks like, then adapt the above to your actual requirement.

The problem with that is that I just want it to echo out the HTML and that will print the dir and then the HTML.

---

### Post by volanin on 2007-11-27
```
#!/bin/bash

IFS=$'\n'
FILES=`find /public/html/cosi -name wiki.phtml`

for FILE in $FILES; do
    echo "STARTSTRING" $FILE "ENDSTRING"
done
```

In one line:

```
IFS=$'\n'; for FILE in `find /public/html/cosi -name wiki.phtml`; do echo "STARTSTRING" $FILE "ENDSTRING"; done
```

Or using **ghostdog74** style:

```
find /public/html/cosi -name wiki.phtml -exec echo "STARTSTRING" {} "ENDSTRING" \;
```

---

### Post by nhandler on 2007-11-27
To expand:

```
find /public/html/cosi -name "wiki.phtml -exec echo "<a href=\"{}\">{}</a>" \;
```

I think that should work

---

