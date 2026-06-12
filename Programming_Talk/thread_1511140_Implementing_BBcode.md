---
title: "Implementing BBcode"
date: 2010-06-16
forum: Programming Talk
---

### Post by gillespiea on 2010-06-16
Hi all!
I've been learning PHP, Mysql and CSS over the past few months. And i wasn't really doing anything with it. Then things went the wrong way up with my datacenter cutting off access to my server as someone had found a flaw with the website system i was using (rather than creating a site myself i used e107). So i was told that i was no longer able to use e107 on there servers as the security flaw was making the cpu usage go sky high.

So anyway. I spent a couple of days making my new site and i need to be able to use BBcode on the forums (and posibly my news posts).
I've looked about and i cant find how to incorporate it into my pages. Anyone have experience in doing this that they can share with me?

Alastar.

---

### Post by DanielWaterworth on 2010-06-16
It shouldn't be difficult to do with regular expressions. Validate it first (make sure each opening tag has a closing tags), then replace each bb tag with the corresponding html one. You can find reference here [http://en.wikipedia.org/wiki/BBCode](http://en.wikipedia.org/wiki/BBCode)

---

### Post by gillespiea on 2010-06-16
I'm not too sure how to even start implementing it. I may be able to do some php coding but i aint great at it and i use alot of books for help lol.

Thanks for your reply

---

### Post by DanielWaterworth on 2010-06-16
If you leave the validation for a moment then it's str_replace that you want for the most part. Something like:
[PHP]$var = str_replace("[b]", "<b>", $var);
$var = str_replace("[/b]", "</b>", $var);[/PHP]
will give you bold. I haven't programmed in php for a while (it's a horrible language), but I think that's right.

---

### Post by gillespiea on 2010-06-16
Ah ok excellent! So i could just make a page with this (plus more) in it and include it on the pages required?

---

### Post by DanielWaterworth on 2010-06-16
I'm not quite sure what you mean. Somewhere, you'll get posts from the database. You then run the posts through a function that'll convert to HTML which is started above.

---

### Post by gillespiea on 2010-06-16
Basically i can have the bbcode replace strings in a file elsewhere on the server. Then on my forums i can include the file (through php include). Having this included in the pages will then mean that when the browser reads the [b] code it will then "see" from the included file that its to change it too <b>?

---

### Post by johnl on 2010-06-16
I would use the PEAR module, [HTML_BBCodeParser](http://pear.php.net/package/HTML_BBCodeParser/).

---

### Post by Compyx on 2010-06-16
> **johnl said:**
> I would use the PEAR module, [HTML_BBCodeParser](http://pear.php.net/package/HTML_BBCodeParser/).

+1

Although a simple BBcode parser isn't that hard to write, there are still a lot of pitfalls, such as users embedding html code in their posts (which needs to be filtered out), and unbalanced/unsupported tags (do you attempt to fix them, or do you simply discard them?).

Most PEAR modules are well written and have pretty decent documentation, so why reinvent the wheel when the work is already done for you. Although as an exercise, it can be great fun: in the process you'll notice a simple 'replace bbtag with html tag' approach doesn't quite work, and you'll appreciate the work the people behind HTML_BBCodeParser have done, and use that module anyway ;)

---

### Post by gillespiea on 2010-06-16
Thanks all for your help. Been looking at all of this and ... well getting confused in the mountains of code but i'm sure i will figure it out haha.
Thanks again

---

