---
title: "question about the echo command"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by goutham0506 on 2012-10-19
hi friends, i'm very new to linux and this forum

i was actually trying out commands in the terminal and while trying out the echo command i tried the below,

the input i gave:

echo `aaaaa("bbbbb", "ccccc", "ddddd", "eeeee");`

the output that came:

aaaaa(bbbbb, ccccc, ddddd, eeeee);

the output i wanted

aaaaa("bbbbb", "ccccc", "ddddd", "eeeee");

what should i do to include the double quotes in the output?
can it be done with echo or any other command should be used?
thanks for helping this Linux noob!

---

### Post by buckyaustin on 2012-10-19
You could try using the "man" command with echo to gain more insight to the bash shell. This should give you the manual to go with echo. Also knowing this means if you have any questions like this in the furtur you can solve the problem all by yourself.

---

### Post by SlugSlug on 2012-10-19
> **goutham0506 said:**
> hi friends, i'm very new to linux and this forum

i was actually trying out commands in the terminal and while trying out the echo command i tried the below,

the input i gave:

echo `aaaaa("bbbbb", "ccccc", "ddddd", "eeeee");`

the output that came:

aaaaa(bbbbb, ccccc, ddddd, eeeee);

the output i wanted

aaaaa("bbbbb", "ccccc", "ddddd", "eeeee");

what should i do to include the double quotes in the output?
can it be done with echo or any other command should be used?
thanks for helping this Linux noob!

you need to escape the quotes..

```
 echo "aaaaa(\"bbbbb\", \"ccccc\", \"ddddd\", \"eeeee\")"
```

---

### Post by newb85 on 2012-10-19
> **buckyaustin said:**
> Read what other people have to say. No matter how experienced you are, you don't know everything.

How true...

---

