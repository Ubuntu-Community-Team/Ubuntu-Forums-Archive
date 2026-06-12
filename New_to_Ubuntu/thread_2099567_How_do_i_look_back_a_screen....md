---
title: "How do i look back a screen..."
date: 2012-12-29
forum: New to Ubuntu
---

### Post by robertthebruce on 2012-12-29
when I lshd i get a long result that i do not know how to go back and see what is there....

sure, it is easy enough in putty, but on the actual pc screen i cant work out how....

i can even work out what to search for, the terms are too wde and i havnt lucked on it....

an assist would be good

---

### Post by Sealbhach on 2012-12-29
Pipe it through less or more

```
sudo lshw | less
```

You can  also change your terminal profile so it allows you to scroll back more.

.

---

### Post by steeldriver on 2012-12-29
do you mean lshw? anyhow a few options are

1. use SHIFT-PgUp / SHIFT-PgDn key combinations in the terminal

2. use 'less' to paginate the command output

```
lshw | less
```and then use SPACE to go forward and b to go backward (q to quit)

3. redirect the output to a file so you can look at it in your favorite editor

```
lshw > hw.txt
```4. [for lshw in particular] you can format the output as HTML and look at it in your browser

```
lshw -html > hw.htm
```

---

### Post by robertthebruce on 2012-12-29
yep i did mean lshw...

many thanks for the assist...

---

