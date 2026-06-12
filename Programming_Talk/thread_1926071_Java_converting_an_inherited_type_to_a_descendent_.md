---
title: "Java: converting an inherited type to a descendent type"
date: 2012-02-15
forum: Programming Talk
---

### Post by Sidneyaks on 2012-02-15
Nevermind, I found the answer in the DataOutputStream constructor.

[COLOR="Silver"]Ok, I'll be straight up, I'm working on homework, HOWEVER, this question is not about the assignment in particular, but something I'm having trouble with. In the homework, we're supposed to be working on a webserver that processes HTTP requests, and we're doing so in java. The only problem is, I haven't touched java for three semesters and thus am still relearning it. I've been hugging onto the java documentation for dear life, but I seem to be stuck on something.

As part of the assignment, I need to get a _[COLOR="Blue"][DataOutputStream]("http://docs.oracle.com/javase/1.4.2/docs/api/java/io/DataOutputStream.html")[/COLOR]_ class from a [COLOR="blue"]_[Socket]("http://docs.oracle.com/javase/1.4.2/docs/api/java/net/Socket.html#getOutputStream()")_[/COLOR]. Unfortunately, the closest I can get from Socket is the _[COLOR="blue"][OutputStream]("http://docs.oracle.com/javase/1.4.2/docs/api/java/io/OutputStream.html")[/COLOR]_. Now, DataOutputStream inherits OutputStream, so I don't see any reason I can't cast OutputStream to DataOutputStream in the program.. The problem is, I can't remember how to do that or if java will even let me. If anyone could point me in the right direction, I would really appreciate it. Thanks.

```

      DataOutputStream os = mainSock.getOutputStream();

```[/COLOR]

---

