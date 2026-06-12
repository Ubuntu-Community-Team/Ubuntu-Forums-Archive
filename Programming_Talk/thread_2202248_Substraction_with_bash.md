---
title: "Substraction with bash"
date: 2014-01-28
forum: Programming Talk
---

### Post by Muriel_Gros-Baltha on 2014-01-28
Hello !

I have a list of numbers:
```
 0
30
52
63
...

```

I would like to substract the number i to the number i + 1 :
30-0=30
52-30=22
63-52=11
...

In order to obtain this :
```

30
22
11
...
```

Any idea how to do this with bash ?

Thanks a lot !

Muriel

---

### Post by sudodus on 2014-01-28
You can use ***bc*** or directly in bash with $(( simple arithmetic operations ))

```
new=0
'loop start'
old=$new
read new
echo $(( $new - $old ))
'loop end'
```

---

### Post by Muriel_Gros-Baltha on 2014-01-28
Hello,
Thanks a lot for your answer.
This makes sense to me this loop.
However, where do I define the name of the input and output ?
Sorry, I am new in all of this!
Muriel

---

### Post by sudodus on 2014-01-28
Please describe what you want to do with ***more details***, the particular problem that you want to solve. The more you tell about it, the easier it will be to help. Otherwise we have to guess, and the advice might suit some other problem or task.

If you know very little about bash, I suggest that you start with some ***tutorial*** about it. You can easily find several tutorials when you browse the internet, and I suggest that you look briefly at some of them and start reading more carefully, a tutorial that suits you.

---

### Post by Muriel_Gros-Baltha on 2014-01-28
Indeed, I have been reading tutorials. I start to use awk and sed, using regexp... I keep on reading but very often I want to do something and try to but I don't find a way.

I was not clear enough apparently: the list that I want to work on is saved in file and I want to obtain the substraction in a file called output.

Thanks.

Muriel

---

### Post by sudodus on 2014-01-28
> **Muriel_Gros-Baltha said:**
> Indeed, I have been reading tutorials. I start to use awk and sed, using regexp... I keep on reading but very often I want to do something and try to but I don't find a way.

I was not clear enough apparently: the list that I want to work on is saved in file and I want to obtain the substraction in a file called output.

Thanks.

Muriel

Make a script like this and save it in a file (for example with the name ***subtract***)

```

#!/bin/bash

read old
while read new
do
 if [ "$new" != "" ]
 then
  echo $(( $new - $old ))
  old=$new
 fi
done

```

Keep your data in a file (for example with the name **input**)

 ```

0
30
52
63

```

And run it with

```
bash subtract < input
```

to write to the terminal and

```
bash subtract < input > output
```

to write to the file **output**

---

### Post by Muriel_Gros-Baltha on 2014-01-28
OK, it's working, thanks a lot for your help !

---

### Post by Vaphell on 2014-01-28
let me guess, these numbers are the ones you extract with sed in your another thread?

If that's the case, then sudosus words that we need detail and context are correct. Noobs often fixate on some solution they try to put together from pieces of information, meanwhile the proper solution is often entirely different or can be achieved with 1 tool capable of doing it all.

---

