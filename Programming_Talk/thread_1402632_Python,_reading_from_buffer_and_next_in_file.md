---
title: "Python, reading from buffer and next in file"
date: 2010-02-09
forum: Programming Talk
---

### Post by HarrisonNapper on 2010-02-09
Two questions:

EDIT: I answered my own question for question 1. Would definitely like to know question 2, though. I know that I can use pickle for what I want to do with both, but if I can read from the buffer, it would be handy.

1. I'm writing a little test program that does nothing more than make an array of arrays from the items in a file. So take this test file:

> 1a
1b
1c
2a
2b
2c
...
14cI've written:

```

f=open('test.txt','r')
b=0
a=' '
a=str(a)
while b<15:
     for i in f:
          a[b]=i, i+1, i+2
          i+=2
     b+=1

```It gives (understandably) that I cannot concatenate str and int objects. So in summary, question one is how do I specify the next line in the series for the for loop for i in f?


Question 2 is if anyone knows where the buffer in interactive mode (at the CLI) is stored on Windows systems and Unix-based systems severally? I have Ubuntu at home, Windows (>.<) at work. And particularly if anyone knows how or whether I can read from that buffer, so that if I write some code in python I can save it with something similar to for i in buffer(0-5): <enter, tab> f.write(i).

Cheers.

---

