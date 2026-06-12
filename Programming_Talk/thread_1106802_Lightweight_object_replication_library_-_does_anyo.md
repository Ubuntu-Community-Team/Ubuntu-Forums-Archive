---
title: "Lightweight object replication library - does anyone know something like this?"
date: 2009-03-26
forum: Programming Talk
---

### Post by Delever on 2009-03-26
I am looking for lightweight library to efficiently replicate objects and their states over shared memory or over network. What i am looking specifically, is the ability to define relevant object scope for different clients, replicate only relevant data and do that in real time.

For example, client A creates object of type A on server. This object is owned by client A, and has possibility to attach property of type B, which is initially empty. Client B creates object B on server, he can see there is object A already created, so he connects object B to object A as it's property. Client A gets notified that object B is connected, and since it owns parent object, it can change any properties of object B, and client B gets notified of all changes.

This would allow development of some amazing scenarios, so I am looking how to implement this. Preferable language is C, or, if some library is really good, C++.

Inspiration from: Unreal engine network replication, rabbitmq (AMQP)

---

