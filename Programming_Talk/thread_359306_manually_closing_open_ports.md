---
title: "manually closing open ports"
date: 2007-02-11
forum: Programming Talk
---

### Post by orlox on 2007-02-11
I'm currently programming something that uses tcp/ip sockets...
The problem is that it usually end up terminating in a bad way, leaving ports open.
So, I need to find a way to manually close this ports, cause the only solutions I have right now, are to restart the PC every time this happens, or change the ports used in the code.....

any help??

---

### Post by lnostdal on 2007-02-11
you want to do this:
```

int yes = 1;
if(setsockopt(sockfd, SOL_SOCKET, SO_REUSEADDR, &yes, sizeof(int)) == -1) {
  perror("setsockopt");
  exit(1);
 }

```

..see `man 2 setsockopt', and `man 7 socket' for info about the options

---

### Post by orlox on 2007-02-11
actually, I was looking for a sort of terminal command that would do the job, something like:

```
$portClose 12345
```

So it closes the port 12345 that my app left open...

---

### Post by lnostdal on 2007-02-11
> **orlox said:**
> actually, I was looking for a sort of terminal command that would do the job, something like:

```
$portClose 12345
```

So it closes the port 12345 that my app left open...

lol - no you're not -- you're looking for `SO_REUSEADDR' as stated above

---

### Post by ZylGadis on 2007-02-11
There should be a process holding the socket.
```
lsof -i :12345
```
will tell you the process that currently holds port 12345. You can kill it afterwards.

---

### Post by lloyd mcclendon on 2007-02-12
if you have a bunch open within a given range you could loop over them,

low=12345; high=23456; for i in `seq $low $high` ; do pid=`lsof -i :$i | awk '{getline;print $2}'` ; if [ ${#pid} -gt 0 ] ; then kill -s 9 $pid ; fi ; done

---

### Post by lnostdal on 2007-02-12
you've not mentioned language in this post, but if you're using Java - see:
[http://java.sun.com/j2se/1.5.0/docs/api/java/net/ServerSocket.html#setReuseAddress(boolean](http://java.sun.com/j2se/1.5.0/docs/api/java/net/ServerSocket.html#setReuseAddress(boolean))

---

