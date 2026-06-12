---
title: "variabe substitution in python?"
date: 2007-02-17
forum: Programming Talk
---

### Post by fadder on 2007-02-17
Hi, 

I'm trying to learn python, starting from a perl background. I'd like to do the
equivalent to the following perl code:
```

foreach $i ( 23, 45, 67 ) {
          open(IN,"<file$i.dat");
or, 
          system(" do-something-with-$i ")
}
```

So that $i is replaced by relevent numbers. I know that in python I could do something
like   f="file%d.dat" % i and then open that file on  another line, but is there a way 
to do this in-place? I am so used to perl's usage where I can subtitute anything anywhere i  a string.

Thanks for any tips.

---

### Post by JDahl on 2007-02-17
```

for i in [10,20,30]:
    f = open('file%i.txt'%i)

```

---

### Post by fadder on 2007-02-17
Ooops, I'm embarassed it was that simple. I'm sure I had tried similar thngs and got stuck, but can't think of an example just now.

Thanks!

---

