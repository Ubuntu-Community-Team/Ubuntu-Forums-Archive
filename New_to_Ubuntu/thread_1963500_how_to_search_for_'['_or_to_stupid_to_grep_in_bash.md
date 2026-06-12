---
title: "how to search for '[' or to stupid to grep in bash"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by hekastos on 2012-04-22
I know its not ubuntu, but I am sure its pretty easy for you to answer, I  just seem a bit stupid today. I want to count the occurence of the sign   [   -the sign called square bracket- in a file.
grep -c \[ mytext.txt
does not do it.
Sorry for this stupid question and thank you very much for any hint!

---

### Post by SeijiSensei on 2012-04-22
How about "\\\[" instead?  Worked for me.  

Using "\\" escapes the "\" then "\[" escapes "[" so you end up with "\[".

And, this is hardly a stupid question.  It took me a while to understand how escaping works in bash.

---

### Post by Vaphell on 2012-04-22
it's best to use quotes to prevent bash from interpreting syntax-related characters. On top of that [ in regexes has its special meaning too and needs escaping to act as an ordinary char. you can achieve that with \ or with closing them in, wait for it... square brackets (enumeration of allowed chars)

```
$ echo $'[a[\n]b]'
[a[
]b]
$ echo $'[a[\n]b]' | grep '[[]'
[a[
$ echo $'[a[\n]b]' | grep '[]]'
]b]
$ echo $'[a[\n]b]' | grep '\['
[a[
$ echo $'[a[\n]b]' | grep '\]'
]b]
$ echo $'[a[\n]b]' | grep '[][]'
[a[
]b]
```

---

### Post by Hadaka on 2012-04-22
Here is a nice little "get your feet wet" bash guide link.
Its has some very useful explanations.

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by hekastos on 2012-04-23
thanks a lot! you made my day!

---

