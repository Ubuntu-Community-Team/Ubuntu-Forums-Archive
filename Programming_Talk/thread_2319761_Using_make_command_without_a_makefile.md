---
title: "Using make command without a makefile"
date: 2016-04-07
forum: Programming Talk
---

### Post by william105 on 2016-04-07
new guy learning programming with C in ubuntu
Using a hello.c for example
From some video tutorial I saw the teacher can use "make hello" to compile the hello.c without setting up a Makefile in current directory
And the command goes like 
$make hello
gcc   -g  -Wall     hello.c       -o       hello
I tried to use make on my own ubuntu 14.04
I installed build-essential and tried out the same hello.c
$make hello
cc      hello.c      -o    hello
It goes like above
How can I make changes to get -g, -Wall or any other flags?

---

### Post by spjackson on 2016-04-07
You can control the behaviour of make by setting appropriate environment variables, in this case
```

export CFLAGS=-g -Wall
export CC=gcc
make hello

```

---

