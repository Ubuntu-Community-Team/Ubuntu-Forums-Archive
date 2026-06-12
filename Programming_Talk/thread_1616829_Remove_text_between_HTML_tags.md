---
title: "Remove text between HTML tags"
date: 2010-11-08
forum: Programming Talk
---

### Post by Commander_Bob on 2010-11-08
I am trying to write a script that will download a bunch of pages and remove some text spitting it into a file.

My problem is in trying to remove all the unwanted text. I am not to familiar with sed and need some help.

I need to remove everything between
<td class="noFear-left"> and the next </td>

I've tried 
```
sed 's/<td class="noFear-left">[^<\/td>]*<\/td>//g'
```
but that only removes the first tag (not sure why).

I've also tried 
```
sed 's/<td class="noFear-left">.*<\/td>//g'
```
which over does it matching the first part with a </td> at the end of the file deleting everything.

There are other <td> tags that need to say there.

Any ideas?

EDIT: After messing around with it more I found my problem is that the new lines are messing things up. How can I get it to go over multiple lines?

This is my full command right now.
```
cat page_2.html | sed -e ':a;N;$!ba;s/.*class="noFear" border="0">//g;s/<\/table>.*//g;s/<tr>//g;s/<\/tr>//g;s/<td class="noFear-number">[^<\/td>]*<\/td>//g;s/<td class="noFear-left">[^<\/td>]*<\/td>//g' -e "s/&rsquo;/'/g" -e "s/&mdash;/-/g"

```

---

### Post by Joeb454 on 2010-11-08
*Thread moved to **Programming Talk**.*

You should hopefully get the answer you're looking for here :)

---

### Post by gebregl on 2011-01-22
* is greedy and tries to get the largest possible match.
try *? instead for a non-greedy match.

```

sed 's/<td class="noFear-left">.*?<\/td>//g'

```

Brackets can only be used to match or not match a single character. I.e. [^ab] will match a single character that's not an 'a' or a 'b'.

---

