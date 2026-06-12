---
title: "Problem: perl negative look-ahead assertion in multi-line mode"
date: 2013-05-22
forum: Programming Talk
---

### Post by cibalo on 2013-05-22
Hello,

I has updated/modified my mysql database in my computer recently. I have to re-code all my php files such that an extra statement has to be inserted before the last mysql_query call. It may have more than one mysql_query call in some of my php files.

I try to use a negative look-ahead assertion to make such a change as follows.

I would like to insert just one "new_insert" line before the "coding line 4". And my php file looks like this.
```
$ echo -e "coding line 1 test 1\ncoding line 2 mysql_query 2\ncoding line 3 test 3\ncoding line 4 mysql_query 4\ncoding line 5 test 5"
coding line 1 test 1
coding line 2 mysql_query 2
coding line 3 test 3
coding line 4 mysql_query 4
coding line 5 test 5
```
Then I perl-regex with negative look-ahead assertion in multi-line mode (/smg or /sg or /mg) like this:
```
$ echo -e "coding line 1 test 1\ncoding line 2 mysql_query 2\ncoding line 3 test 3\ncoding line 4 mysql_query 4\ncoding line 5 test 5" | perl -pe '/mysql_query(?!.*mysql_query)/smg && print "new_insert\n"'
coding line 1 test 1
new_insert
coding line 2 mysql_query 2
coding line 3 test 3
new_insert
coding line 4 mysql_query 4
coding line 5 test 5
```
However, my "coding line 2" gets changed too. And that is not what I'm looking for.

Or, perl negative look-ahead assertion doesn't like me! Can you please let me know what I'm missing?

Thank you very much in advance!!!

Best Regards,
cibalo

---

### Post by trent.josephsen on 2013-05-22
Each time through the loop, the pattern gets matched only against the current line, disregarding the rest of the file. That pattern will match the last occurrence of the string 'mysql_query' on any line that contains it at least once.

Much like your last thread, you're trying to do something complex with regular expressions when what you really need is a very simple expression and some plain old code. I'd push each input line onto a stack until I find one that matches /mysql_query/, then flush the stack to output and start over... when you're out of input you'll have a stack that contains everything from the file's last mysql_query line to the end. Then just print new_insert followed by @lines. I'd provide pseudocode but I gotta go. Good luck.

---

### Post by schragge on 2013-05-22
Instead of pseudocode, I provide a sed expression for this:
```
sed -nr '1h;1!H;${g;s/(.*)(\n.*mysql_query)/\1\nnew_insert\2/p}'
```
You may also want to have a look at [post=12591593]this post[/post] for several variations of the same theme.

---

### Post by cibalo on 2013-05-23
Hello trent.josephsen and schragge,

Thank you very much for your valuable replies.

> **trent.josephsen said:**
> Each time through the loop, the pattern gets matched only against the current line, disregarding the rest of the file.

> **schragge said:**
> Instead of pseudocode, I provide a sed expression for this:
```
sed -nr '1h;1!H;${g;s/(.*)(\n.*mysql_query)/\1\nnew_insert\2/p}'
```

I follow schragge's algorithm and provide a perl expression as follows.

```
$ echo -e "coding line 1 test 1\ncoding line 2 mysql_query 2\ncoding line 3 test 3\ncoding line 4 mysql_query 4\ncoding line 5 test 5"|perl -0pe 's/(.*)(\n.*?mysql_query.*?\n)/$1\nnew_insert$2/sm'
coding line 1 test 1
coding line 2 mysql_query 2
coding line 3 test 3
new_insert
coding line 4 mysql_query 4
coding line 5 test 5
```

---

### Post by trent.josephsen on 2013-05-23
It's the same algorithm, just applied to the whole file at once.

[quote=jwz]Some people, when confronted with a problem, think &#8220;I know, I'll use regular expressions.&#8221;   Now they have two problems.[/quote]

I always defended regular expressions when this quote has come up, but now maybe I see what Zawinski was talking about.

---

