---
title: "search and replace in a single line html file"
date: 2015-01-26
forum: Programming Talk
---

### Post by neogeo1128 on 2015-01-26
Hi, 

I have a programming issue
I want to search and replace the following html from : 

original html : 
<a href="http://abcd.com/result.asp?programid=A123" border="0">Peter</a> 
<a href="http://abcd.com/result.asp?programid=B253" border="0">Mary</a> 
<a href="http://abcd.com/result.asp?programid=C568" border="0">LEE</a> 
<a href="http://abcd.com/result.asp?programid=A613" border="0">ABC</a> 
<a href="http://abcd.com/result.asp?programid=E566" border="0">DEF</a> 
..... 

to a new html file : 
<a href="http://abcd.com/result.asp?programid=A123" border="0">Peter (A123)</a> 
<a href="http://abcd.com/result.asp?programid=B253" border="0">Mary (B253)</a> 
<a href="http://abcd.com/result.asp?programid=C568" border="0">LEE (C568)</a> 
<a href="http://abcd.com/result.asp?programid=A613" border="0">ABC (A613)</a> 
<a href="http://abcd.com/result.asp?programid=E566" border="0">DEF (E566)</a>  

search some website and they advised me using sed command to achieve this 

sed "s/<a\ href\=\"http\:\/\/abcd\.com\/result.asp?programid=\(.\+\)\"\ border=\"0\">\(.\+\)<\/a>/<a\ href\=\"http\:\/\/abcd\.com\/result.asp?programid=\1\"\ border=\"0\">\2 (\1)<\/a>/g" <index.html

IT WORKED! 

but....the problem is the area need do search and replace is in JUST A SINGLE LINE  (that is ...no <CR>return in each </a> thereafter)

ACTUAL:
<a href="http://abcd.com/result.asp?programid=A123"  border="0">Peter</a><a  href="http://abcd.com/result.asp?programid=B253"  border="0">Mary</a><a  href="http://abcd.com/result.asp?programid=C568"  border="0">LEE</a><a  href="http://abcd.com/result.asp?programid=A613"  border="0">ABC</a><a  href="http://abcd.com/result.asp?programid=E566"  border="0">DEF</a>

So how can I do search and replace with this?

Thanks a lot !

---

### Post by ofnuts on 2015-01-26
Things get a lot simpler when you use a sed separator which is not "/" (so you don't have to escape plenty of things) and use single quotes are around the whole thing (no need to escape double quotes).

This said, the main problem is that the matching is "greedy" and to make sure that sed won't look too far, instead of having it match any character with ".\+" you tell to match any character which is not the first character that should be outside the match: "[^>]+". For instance in "<aaa>something<bbb>", "<.\+>" matches "<aaa>something<bbb>" while "<[^>]\+]>" only matches "<aaa>" because the ">" after "aaa" cannot be matched by the [^>].

TL;DR:
```

sed 's!<a href="http://abcd.com/result.asp?programid=\([^"]\+\)" border="0">\([^<]\+\)</a>!<a href="http://abcd.com/result.asp?programid=1" border="0">\2(\1)</a>!g'

```

---

