---
title: "getting a return value from a function called from a p_thread"
date: 2010-03-08
forum: Programming Talk
---

### Post by TMagic*04 on 2010-03-08
I'm trying to set up a socket to listen on a particular port for multicast packets arriving. Once the packet arrives I want to return it to the main thread, and relaunch the listener. I can launch a thread using pthread,  however I'm struggling to figure out how I can return the packet back to the main thread for processing.
Any advice, ideas, or suggestions would be much appreciated.

---

### Post by dwhitney67 on 2010-03-08
Just allocate a chunk of memory on the heap to store the packet data; return the pointer to this memory location via the static pthread method.

Assuming your doing the code in C:
```

void* myThread(void* arg)
{
   char packet[80];

   /* do something in thread, like receive the packet */
   while (waitingForPacket)
   {
   }

   /* got packet */
   char* buffer = malloc(sizeof(packet));
   memcpy(buffer, packet, sizeof(packet));

   return (void*)buffer;
}

int main(void)
{
   pthread_t tid;
   pthread_create(&tid, 0, myThread, 0);

   char* packet = 0;

   pthread_join(tid, (void**)&packet);
}

```
I have not compiled this code, and obviously not tested it.  An alternative is to return the packet via the 'arg' parameter passed to pthread_create() (which above, I passed a null).

---

### Post by TMagic*04 on 2010-03-08
Great idea, dwhit I owe you another one thanks. The problem with moving from Java/C# and the like to C/C++ is that you don't get used to exploiting memory to its full benefits.

Anyway thanks again!

---

