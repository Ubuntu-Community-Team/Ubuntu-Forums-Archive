---
title: "parsing &lt;link&gt;&lt;/link&gt; tag"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2014-01-30
Hi friends,

I am using following code in a bash script to filter article url links from a rss feed

```
wget -q -O- ${url} |\
grep "<link>"

```

Output of the code is 

<link>http://www.somewebsite.com/dir/path/to/a/article-30-jan-2014</link>
<link>http://www.somewebsite.com/dir/path/to/a/article-29-jan-2014</link>
<link>http://www.somewebsite.com/dir/path/to/a/article-28-jan-2014</link>
<link>http://www.somewebsite.com/dir/path/to/a/article-24-jan-2014</link>
<link>http://www.somewebsite.com/dir/path/to/a/article-23-jan-2014</link>

Now how do I remove the link tag to get only url strings? In fact I need to filter url of just latest article and then write it to a .txt file
Thanks in advance

---

### Post by sujitrjadhav on 2014-01-30
Got the solution !


```
wget ${feed} -O - 2>/dev/null | \
xmlstarlet sel -t -m "/rss/channel/item" \
-n -v "link" |  grep "${d}"
```

---

