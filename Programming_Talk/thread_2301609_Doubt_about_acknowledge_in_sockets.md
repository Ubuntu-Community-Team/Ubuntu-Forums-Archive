---
title: "Doubt about acknowledge in sockets"
date: 2015-11-03
forum: Programming Talk
---

### Post by mfvpcrec on 2015-11-03
Hello guys! I need an answer to a very silly question.
I need to know if I send information from a socket to another socket but i send the information with a while as:

```
while(i!=100000000)
{
     send(i);
     i++
}
```

And in another socket i have

```
while()
{
   recv(info);
}
```

The information should arrive ok to the second socket or I need down the velocity using an acknowledge?
Could happen that the message sent arrived broken?
 Could happen that some buffer of TCP could get fill?


Thanks!

---

