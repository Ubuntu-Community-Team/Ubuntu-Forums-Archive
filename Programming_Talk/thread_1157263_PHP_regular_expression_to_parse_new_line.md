---
title: "PHP regular expression to parse new line"
date: 2009-05-12
forum: Programming Talk
---

### Post by mohtasham1983 on 2009-05-12
Hi,

I'm trying to extract some information from an html document using regular expression. 

For example, I want to extract the "Results1" and "Results2" from a document that has the following information:

```

<li>
    <b>Title1: </b>
     Results1
</li>
<li>
    <b>Title2: </b>
     Results2
</li>

```

I use the following regular expression:
[PHP]@\<li\>(.*)\</li\>@[/PHP]

This one returns everything inside the first <li> block. While I still need to extract everything inside the second <li> block.

That's why, to get the information inside the second block, I use the following regular expression:

[PHP]@\<li\>\<b\>Title2: \</b\>(.*)\</li\>@[/PHP]

I think because the <b> tag comes in a new line after <li>, it's not able to find it. I searched on a lot of PHP regular expressions tutorial, but couldn't find any way to add new line to my regular expression. 

Any idea how to eliminate my new line problem?

---

### Post by Reiger on 2009-05-12
If your first pattern works fine why not use preg_match_all(), far as I can see it should match the second block too... ?

---

### Post by mohtasham1983 on 2009-05-12
Thank you for the reply. I really appreciate it.

Now, I'm facing a new problem. 

Isn't (.*) supposed to extract everything in between? 

Using the method you mentioned, I can get the following tags perfectly file:

```

<li>
    <b>Title1: </b>
     Results1
</li>
<li>
    <b>Title2: </b>
     Results2
</li>

```

However, if there's any space after <b>, the result is not shown up. For example, the following won't be extracted:

```

<li>
    <b> Title1: </b>
     Results1
</li>
<li>
    <b> Title2: </b>
     Results2
</li>

```

EDIT: I just realized the problem is not with the space. It's the problem with new line again. It means the following doesn't work:
```

<li>\n
    <b>Title1:</b>\n
     Results1
</li>
<li>\n
    <b>Title2:</b>\n
     Results2
</li>

```

---

### Post by ghostdog74 on 2009-05-12
use (.*?) for non-greediness

---

