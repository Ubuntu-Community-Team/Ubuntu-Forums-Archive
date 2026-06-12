---
title: "[Python] Socket to multiple clients"
date: 2010-10-20
forum: Programming Talk
---

### Post by Psycho.mario on 2010-10-20
I am writing a sort of job queue/scheduler for python, with python clients. The number of clients is unlimited (could be >65536), so i want to have all the connections as one object, so i can send the same data to all the nodes simultaneously, like:
```
allnodes_socket.write(data)
```
rather than
```
node1_socket.write(data)
node2_socket.write(data)
...
```
Is it possible to achieve this in python? I realise i could use a function with a for loop in it, but that isn't the kind of simultaneous i am looking for. 

Thanks

---

### Post by Zymus on 2010-10-20
I don't believe it could be unlimited, because the server can only be connected to with < 65535 ports(1 port - 1 client)

I think you could do a vector and basically do something like
```

for x, socket in vector:
    socket.write(data)


```

---

### Post by Psycho.mario on 2010-10-20
Sorry, I meant I *wanted* the number of clients to be unlimited, which is why I wanted to have one port on the server for multiple clients. But if this is impossible, I will have to set a limit. I suppose it's going to be unfeasible I would have > 65536 clients/nodes anyway.

Thanks

p.s. what do you mean by 'vector'?

---

### Post by Zymus on 2010-10-20
A vector is like... a resizable array. basically it can grow/shrink with one function call.
Like a list, I can't remember if python has a vector/list module.

---

### Post by Psycho.mario on 2010-10-20
I don't really understand. Can you give me an example? If not in python then in C or something?

---

### Post by dwhitney67 on 2010-10-20
> **Psycho.mario said:**
> I am writing a sort of job queue/scheduler for python, with python clients. The number of clients is unlimited (could be >65536)...

Good luck!  At most 65535 sockets can be opened on your system at any given time.  Thus your server will not be able to handle the number of clients you anticipate *at the same time*.

The server can manage how many clients can connect by keeping a counter, and restricting the counter to a certain level.  The server can also manage the backlog (ie number) of clients *attempting* to connect at any given moment.

As for managing which clients are connected, usually that is kept track of using various means.  If you have one handler for all clients, then create a "watch" set of file (socket) descriptors, looking for activity from the client.  Alternatively, you can spawn a new process, or thread, per client.  Of course, there are system limitations that must be considered.

---

### Post by Zymus on 2010-10-20
I haven't used lists in C/*, but I have in Java. so here's a brief example of that:

```

import java.util.Vector;

public class Main {
    public static void main(String[] args) {
        Vector<Integer> numbers = new Vector<Integer>();//Create a dynamically sized list of Integer elements
        for(int i = 0; i < 10; i++) {
            numbers.add(i);//Add an element with the value of 'i'
        }
        numbers.remove(4);//remove the element whose value is '4'
        for(int i = 0; i < numbers.size(); i++) {
            System.out.println(numbers.get(i));//send each number in 'numbers' to the screen
        }
    }
}

```

output:
> 
0
1
2
3
5
6
7
8
9


---

### Post by Psycho.mario on 2010-10-20
I think i understand now. I think in python it would be:
```
numbers=[]
for i in range(0,10):
   numbers.append(i)
for i in numbers:
   print i
```

---

### Post by Zymus on 2010-10-20
Ya, i think that's how you do it. I don't have much experience with python.

---

