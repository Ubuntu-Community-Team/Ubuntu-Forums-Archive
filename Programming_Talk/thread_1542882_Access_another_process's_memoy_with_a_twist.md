---
title: "Access another process's memoy with a twist"
date: 2010-07-31
forum: Programming Talk
---

### Post by astropirit on 2010-07-31
I have been looking for a method for a while now that would allow me to access another process's memory without causing it to freeze. But with all of my googling I have found nothing :-(

so, my question is: Is there a way to not lock a process while accessing it's "/proc/[PID]/mem" interface?

Thanks!

---

### Post by PaulM1985 on 2010-07-31
This can be done with Java and C# by creating remote objects.  You create a remote object which acts as a server and the client (which is on another process) can then connect to this object and call methods and view the public instance variables of the object.

For C# google "Remoting" and for Java google "RMI"

Paul

---

### Post by astropirit on 2010-07-31
thanks for you reply, I understand IPC, however in this scenario I am working with an unknown process which isn't written by me.

---

### Post by napsy on 2010-07-31
It's impossible (at least I don't know of a way) to access other process memory without explicit support from that process. The address space of the process is protected by the system so you can't just access it's memory.

---

### Post by astropirit on 2010-07-31
Actually, you can using the ptrace() system call and /proc/[PID]/map + /proc/[PID]/mem   interfaces. I'm looking for a work around for the problem of the process waiting while being read. It doesn't crash the process it just makes it wait while your process is reading and writing to it's virtual memory.

---

