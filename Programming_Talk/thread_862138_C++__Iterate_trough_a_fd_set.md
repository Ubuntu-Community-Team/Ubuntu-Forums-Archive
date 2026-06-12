---
title: "C++ : Iterate trough a fd_set ?"
date: 2008-07-17
forum: Programming Talk
---

### Post by Khao on 2008-07-17
Hey,
I'm programming a socket server for a small game with my friends and I was if there is anyway to iterate trough an fd_set?

After a call to select(maxfd+1, &readfds, NULL, NULL, $timeout) readfds has all the file descriptors associated with sockets that I can read from. The only downside is I can't find any way of iterating torugh it other than to iterate trough all my sockets and call FD_ISSET(i, &readfds);

I've googled a LOT to find a way to do this and haven't found anything, is there a way to do this or do I have to loop trough all the existing connections?

Thanks!

---

### Post by dwhitney67 on 2008-07-17
I think the way you are currently doing (that is, iterating) is the only practical way.

The other options at your disposal is dedicate an individual program or an individual thread for each client.  That way, when select() indicates that there is data to be read on the socket, you know exactly which client is sending the data.

---

### Post by Khao on 2008-07-17
I managed to find some definition of the structure fd_set when searching 'typedef fd_set' on google! :D Actually, an fd_set is an array of long, and it is used as a bit mask to remember which socket has data to read from. For example when you do
FD_ISSET(5, my_fd_set);
it returns the fifth bit of the first long in the array, so it is 1 if the socket 5 has data to read, 0 otherwise.

With this information, these is some optimisation I can do with the current loop : Instead of looping over every socket, I can loop over every long in the array. If long == 0, then that makes 32 users (a long is 32 bits long) that do not have data to read from. When long != 0, I will use bitwise operators to find which users have data to read from.

Here's the typedef of fd_set for those interested : 

```
#if !defined(_XPG4_2) || defined(__EXTENSIONS__)
typedef  struct fd_set {  <fd_set>
#else
typedef  struct __fd_set {
#endif
 long    fds_bits[__howmany(FD_SETSIZE, FD_NFDBITS)];
} fd_set;  <typedef:fd_set>
```

---

