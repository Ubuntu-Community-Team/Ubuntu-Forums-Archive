---
title: "Problems Stroing Results in Shell Script"
date: 2009-02-04
forum: Programming Talk
---

### Post by Tek-E on 2009-02-04
Hello Everybody.

I am working on a very simple script that takes scrambled words and unscrambles them by matching the scrambled words letter by letter with a text file.

So here is my problem.  I am taking each word ( for example: hello) and storing each letter of hello into a variable.
This is how I am doing it.
```

a='echo "hello" | cut -c 1-1'

```
Then my plan was to use grep to search the textfile holding the unscrambled words. by doing this.
```

cat wordlist.txt | grep $a

```
Sorry...Just realized an unecessary use of cat.
It should be like this I suppose.
```

grep $a wordlist.txt

```
But I am getting a long list of errors.
So I use echo to see if the variable I assigned (a) is holding the information I want it to which should be the letter h, but its not. It holds echo "hello" | cut -c 1-1

I guess is how do I store the results of
echo "hello" | cut -c 1-1 into another variable so that I can use them with grep?

If you have any questions regarding what I just "attempted" to explain please let me know!!

Thank you to anyone willing to help!
:)

---

### Post by lykwydchykyn on 2009-02-04
In this line:
```

a='echo "hello"|yadayadayada'

```
you are using single quotes.  What you wanted was backticks (on US keyboards, its usually on the tilde key).  You can also use parenthesis and a $, like so:
```

a=$(echo "hello" | blah)

```

---

### Post by Tek-E on 2009-02-04
Perfecto!
worked like a charm!
Thank you very much!

---

