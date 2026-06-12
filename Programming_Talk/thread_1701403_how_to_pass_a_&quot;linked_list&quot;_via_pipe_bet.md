---
title: "how to pass a &quot;linked list&quot; via pipe between child processes!"
date: 2011-03-06
forum: Programming Talk
---

### Post by erogol on 2011-03-06
I need to pass a linked list via unnamed pipe that is created by the parent process between one child process to another child (created by the same parent). However I am not sure that it is proper to pass it by address of the head node or the complete structure or any other way.

Thanks for help....

---

### Post by MadCow108 on 2011-03-06
you have to serialize it, send the bytes over the pipe and deserialize it again on the other side.

or you use shared memory to directly use the memory address (but beware of synchronization issues)
[http://beej.us/guide/bgipc/output/html/multipage/shm.html](http://beej.us/guide/bgipc/output/html/multipage/shm.html)

---

### Post by erogol on 2011-03-07
but I need to use pipe IPC so it is not the shared memory...

---

### Post by erogol on 2011-03-07
> **MadCow108 said:**
> you have to serialize it, send the bytes over the pipe and deserialize it again on the other side.

or you use shared memory to directly use the memory address (but beware of synchronization issues)
[http://beej.us/guide/bgipc/output/html/multipage/shm.html](http://beej.us/guide/bgipc/output/html/multipage/shm.html)


but I need to use pipe IPC...

---

### Post by Tony Flury on 2011-03-07
So you will have to serialise the data.

You can't just pass a linked list complete with addresses since an address which is heap data in one process might be code space in another process.

Your best bet I think would be iterate round your linked list in your sending process, serialise each node in some form, send that node down the pipe - and for the receiving end to de-serialise the node and add that node to its own linked list.

Depending how often you need to send the lists, and the size of the lists etc this could get horribly inefficient.

I would question why you think you need to do this - it suggests a bad design to me.

Also : What about synchronisation between the lists which will exist in two different processes, which is the master source ?

---

### Post by SledgeHammer_999 on 2011-03-07
I now that I am not directly answering your question but since you mentioned IPC: Have you considered using [DBus](http://www.freedesktop.org/wiki/Software/dbus) for IPC? I think it has support for transfering link lists(I may be wrong). But if you're looking for performance I don't think it will fit the bill

---

### Post by rnerwein on 2011-03-08
> **erogol said:**
> I need to pass a linked list via unnamed pipe that is created by the parent process between one child process to another child (created by the same parent). However I am not sure that it is proper to pass it by address of the head node or the complete structure or any other way.

Thanks for help....
high
may be this is a hin - have a look at the : mmap call ( MAP_SHARED ).
put your list into this memory ( that's the way i'll will do it ).
the child will inherit the address - and --> the fastest I/O is no I/O.
( if the link lists are very big and you have enough memory on your box have a look at " huge pages" too.
ciao

---

