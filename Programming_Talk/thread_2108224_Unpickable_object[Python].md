---
title: "Unpickable object[Python]"
date: 2013-01-24
forum: Programming Talk
---

### Post by 0x8BADF00D on 2013-01-24
Hi there,

I would like to serialize a socket object(actually it's a dictionary that contain a socket object).
I have read about Pickle but, a socket object could not be picklable.
Any suggesstions?

---

### Post by NilPointer on 2013-01-24
Yes, socket can't be pickled. There's nothing can be done about that. It's because you can't really "save" connection, i.e. if one machine closes connection (or stops communication), other machine will break connection on it's end, too. Even if you would save connection state (socket), deserializing won't work since connection would be already broken anyway. So, that's why socket is not picklable.

Although, it's quite possible to save data, required to reestablish connection (such as IP, port, etc) and create new socket from that data at unpickle time. Of course, that would require moving socket out of dictionary.

---

### Post by 0x8BADF00D on 2013-01-24
> **NilPointer said:**
> Yes, socket can't be pickled. There's nothing can be done about that. It's because you can't really "save" connection, i.e. if one machine closes connection (or stops communication), other machine will break connection on it's end, too. Even if you would save connection state (socket), deserializing won't work since connection would be already broken anyway. So, that's why socket is not picklable.

Although, it's quite possible to save data, required to reestablish connection (such as IP, port, etc) and create new socket from that data at unpickle time. Of course, that would require moving socket out of dictionary.

i'm developing instant messaging software and my idea was to save a connection 
and use it later and when the socket is invalid I will recognize the specefied user and then communicate thourgh it.

---

### Post by NilPointer on 2013-01-24
Sorry, but I don't understand what are you trying to do. You are planning to identify user by saved socket? How exactly you're planning to do that?

---

### Post by micahpage on 2013-01-24
this pretty much says it all:

> Although, it's quite possible to save data, required to reestablish  connection (such as IP, port, etc) and create new socket from that dataYou can do what you are trying to do just from saving the ip and port info, as "saving the connection" is saving the ip and port etc.

---

