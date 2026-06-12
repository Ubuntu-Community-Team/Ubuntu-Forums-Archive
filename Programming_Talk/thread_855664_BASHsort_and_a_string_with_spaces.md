---
title: "BASH/sort and a string with spaces"
date: 2008-07-10
forum: Programming Talk
---

### Post by altonbr on 2008-07-10
Is it possible to sort a string of words using sort?

```
echo 'joe abbey john anirudh steph' | sort
```

I looked at the man page and thought I could use -t with " " but that didn't seem to work.

---

### Post by HalPomeranz on 2008-07-10
The sort program only works on a line-by-line basis.  So if each of your words was on a separate line, then sort would work.  

I'm guessing the list of words is in a variable in your shell script?  You could do something kind of hack-y like this:

```

str='joe abbey john anirudh steph'
for i in `echo $str`; do
    echo $i
done | sort

```

That would output the names in sorted order, one per line.

---

### Post by rye_ on 2008-07-10
Perl-related scripting languages are especially good at this....

Ruby Code
[PHP]
ruby -e 'puts "joe abbey john anirudh steph".split(/\s+/).sort'
[/PHP]

Ryan

---

### Post by ghostdog74 on 2008-07-10
> **rye_ said:**
> Perl-related scripting languages are especially good at this....

any language/tools that provides regexp, string manipulation functions can do this.

---

### Post by ghostdog74 on 2008-07-10
> **altonbr said:**
> Is it possible to sort a string of words using sort?

```
echo 'joe abbey john anirudh steph' | sort
```

I looked at the man page and thought I could use -t with " " but that didn't seem to work.

```

# echo 'joe abbey john anirudh steph'|tr " " "\n"|sort|tr "\n" " "

```

---

### Post by HalPomeranz on 2008-07-10
> **ghostdog74 said:**
> ```

# echo 'joe abbey john anirudh steph'|tr " " "\n"|sort|tr "\n" " "

```

Nice one.

---

### Post by maxadamo on 2009-05-02
> **altonbr said:**
> Is it possible to sort a string of words using sort?

```
echo 'joe abbey john anirudh steph' | sort
```

I looked at the man page and thought I could use -t with " " but that didn't seem to work.

This is to explain how and when "-t" can be used:

you can see the difference between:
echo -e "1/2/3\n3/3/1"|sort -t/ -k3
echo -e "1/2/3\n3/3/1"|sort

You allow sorting the two rows, using the third field, and the separator is set to "/".
But it's still sorting rows, and not words in the same row.

---

