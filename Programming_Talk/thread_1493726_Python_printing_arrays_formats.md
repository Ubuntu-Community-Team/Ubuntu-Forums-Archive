---
title: "Python: printing arrays formats"
date: 2010-05-26
forum: Programming Talk
---

### Post by nbo10 on 2010-05-26
Hi all,
I have numpy arrays that I want to print across the terminal CL. No matter how wide I make the terminal the array only print 4-5 doubles and then starts a new line. Is there any way to control the print format? I've looked into numoy.set_printoptions, but that doesn't seem to help. thanks

---

### Post by ssam on 2010-05-26
playing with
```

numpy.set_printoptions(linewidth=1e6, edgeitems=1e6)

```
seems to do the job.

another option is to just do it yourself. for a 2d array:
```

for line in my_array:
    for element in line:
        print element,
    print

```

---

