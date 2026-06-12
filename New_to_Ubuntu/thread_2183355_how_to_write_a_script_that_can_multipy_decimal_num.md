---
title: "how to write a script that can multipy decimal numbers"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by Taati_Barao on 2013-10-24
Hi

I try to figure out and spent 6 hours on the net looking for help  on how can i write simple script that can multiply decimal numbers with no luck, here is an example

```
a=2 
b=2.2
answer= `expr $a \* $b`
echo "$a * $b = $answer"
```

when i run the script and there was an error "expr: syntax error * 2.2 = "




Thanks

---

### Post by sudodus on 2013-10-24
You can use ***bc***

example

```
 echo "scale=3; 0.8*0.7"|bc
```

---

### Post by Taati_Barao on 2013-10-24
thanks for the quick reply, may i ask you a question is it correct if a do like this

a=2 
b=2.2
echo "scale=3; $a*$b"|bc

---

### Post by drmrgd on 2013-10-24
Try it out for yourself!

Seriously, though, that works fine, and you can also skip the echo and pipe by redirecting the string right into bc:

```

a=2
b=2.2
bc <<< "scale=3; $a*$b"
4.4

```

---

### Post by vasa1 on 2013-10-24
Useful thread! I learned about **bc** and **<<<**  :)

---

### Post by Taati_Barao on 2013-10-27
Thank you very much

---

### Post by Taati_Barao on 2013-10-27
Thanks guys for the help

---

### Post by sudodus on 2013-10-28
You are welcome :-)

Please click on **Thread Tools** at the top of this page and mark the thread as SOLVED. It will help other people searching for a solution of similar problems.

---

### Post by VMC on 2013-10-28
You learn something everyday. I've used bash for years. First time I came across "<<<" usage.  A *Here String* indicator, as opposed to a *Here Document* "<<". Interesting
> Here Strings. A variant of here documents, the format is:  <<<word

Just marking for further reference. Thanks for bringing up this topic and answers.

---

