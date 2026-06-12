---
title: "Bash scipt list files"
date: 2012-08-14
forum: Programming Talk
---

### Post by conradin on 2012-08-14
Hi all,
Im trying to do what I thought would be very simple yet Im stuck. 
I want to list the php files in a directory, and insert relative links to them in a web page. 

what I have puts an entire list of the files in a single tag and repeats for the number of tags. Can some one point to where Im going wrong, and offer a solution?

```
#!/bin/bash
touch tickle. me.php pink.php


touch index.html
echo "<!DOCTYPE html>" >> index.html

echo "<html>" >> index.html
echo "<body> ">> index.html

v=`ls *.php | grep php`
echo "<p> <a href="$v ">The a tag" $v"</a></p>" >> index.html

echo "</body>" >> index.html
echo "</html>" >> index.html
```

---

### Post by Lars Noodén on 2012-08-14
Maybe something like this, remember to escape the quotes as needed:

```

[s]for v in $(ls *.php);[/s]
for v in *.php
do echo "<p> <a href=\"./$v\">The a tag \"$v\"</a></p>" >> index.html;
done

```

It will only get values for the current directory and not recursively.

Edit: as per corrections below.

---

### Post by steeldriver on 2012-08-14
iirc it's safer to use shell globbing rather than $(ls ...) 
```
for v in *.php; do
  *stuff*
done
```

---

### Post by conradin on 2012-08-14
Thanks Lars! 
I knew someting like that was possible but couldn't think of it, and that I was going astray when i started writing temp files with sed line inserts. This is much simpler! Thank you for the help!

---

### Post by sisco311 on 2012-08-14
> **steeldriver said:**
> iirc it's safer to use shell globbing rather than $(ls ...) 
```
for v in *.php; do
  *stuff*
done
```

True. *for file in $(ls *.ext)* is one of the most common errors that BASH programmers make ( BashPitfalls 001 ;) ).

---

### Post by Lars Noodén on 2012-08-14
Thanks for the correction, steeldriver and sisco311.  I've read the BashGuide, BashFAQ, and BashPitfalls many times.  Maybe one of these times it will sink in.

---

