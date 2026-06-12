---
title: "Sed: remove all but last consecutive matching line?"
date: 2011-04-11
forum: Programming Talk
---

### Post by mahy on 2011-04-11
Hello,

I've got this problem: Whenever **two or more** lines matching "@@@@@" occur consecutively, I would like to remove all but the last one. Example file:

```

@@@@@ One
Another line

@@@@@ One
@@@@@ Two
@@@@@ Three
@@@@@ Four
Yet another line

```

Desired outcome:

```

@@@@@ One
Another line

@@@@@ Four
Yet another line

```

I'd like to solve this in sed. Thanks very much in advance for any suggestion!

---

### Post by kurum! on 2011-04-11
why sed only?
```


$ ruby -00 -ne '$_.gsub!(/^.*(@@@@@)/m,"\\1"); puts $_' file
@@@@@ One
Another line

@@@@@ Four
Yet another line



```

or  even awk

```

$ awk 'BEGIN{RS="";ORS="\n\n"}{ gsub(/.*@@@@@/,"@@@@@") }1'  file

```

---

### Post by mahy on 2011-04-11
Unfortunately, we don't have Ruby installed on our company servers, and, AFAIK, sed is generally faster than awk. The awk solution looks good though, have to try it out. THX.

---

### Post by mahy on 2011-04-11
I tried the AWK script and it has some problems:

1.) All characters before "@@@@@" (not included in my example) in every matching line get deleted.
2.) There is also a special line containing more than five @'s, that one should not be matched
3.) All lines after the **last** line matching @@@@@ in the whole input file get deleted :(

---

### Post by kurum! on 2011-04-11
> **mahy said:**
> AFAIK, sed is generally faster than awk.
that's so not true.

---

### Post by kurum! on 2011-04-11
> **mahy said:**
> I tried the AWK script and it has some problems:

1.) All characters before "@@@@@" (not included in my example) in every matching line get deleted.
2.) There is also a special line containing more than five @'s, that one should not be matched
3.) All lines after the **last** line matching @@@@@ in the whole input file get deleted :(

The awk script does not have problem. The problem lies with you. Why?  I failed to comprehend why my example awk command would work if your provided examples contains discrepancies from what you have described. Does it not occur to you that you should provide clear examples to your question so that people would not waste time giving you answers that does not meet your requirement?

To show you why it does work with your initial examples
```

$ cat file
@@@@@ One
Another line

@@@@@ One
@@@@@ Two
@@@@@ Three
@@@@@ Four
Yet another line

$ awk 'BEGIN{RS="";ORS="\n\n"}{ gsub(/.*@@@@@/,"@@@@@") }1'  file
@@@@@ One
Another line

@@@@@ Four
Yet another line


```

---

### Post by mahy on 2011-04-15
I'm sorry for wasting your time. I couldn't however post an actual file, because it's a confidential company stuff. I tried to make the example both simple and informative, but I forgot to take all options into consideration. Sorry for that.

As for the sed vs. awk thing, I can't really comment on it. My colleagues told me to prefer sed, that's all.

---

