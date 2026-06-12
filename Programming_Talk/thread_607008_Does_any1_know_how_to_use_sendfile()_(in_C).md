---
title: "Does any1 know how to use sendfile() (in C) ?"
date: 2007-11-08
forum: Programming Talk
---

### Post by raul_ on 2007-11-08
Why doesn't this work??

```

...
n = sendfile(socket_fd,file_fd, NULL, 255);

```

```

[raul@horus myserver]$ ./myclient nexus.rnl 40000
Trying to connect
Connected to server
ERROR writing to socket: Bad file descriptor

```

I can use read and write, but I wanted to use sendfile for cleaner code :(

---

### Post by gradedcheese on 2007-11-09
Ah, in Linux that won't work.  From "man sendfile":

> 
Presently  (Linux  2.6.9):  in_fd, must correspond to a file which sup&#8208;
ports mmap(2)-like operations (i.e., it cannot be a socket); and out_fd
must refer to a socket.

Applications  may  wish  to  fall  back to read(2)/write(2) in the case
where sendfile() fails with EINVAL or ENOSYS.


My guess: sendfile() does everything inside the kernel, which in this case isn't very secure, while read/write make userspace->kernel trips each time, so they don't allow it.  But I'm not sure.

EDIT: hmm, but the order of arguments is:

```

ssize_t sendfile(int out_fd, int in_fd, off_t *offset, size_t count);

```

so then as I understand it, that should work?  What return value do you get?

---

### Post by raul_ on 2007-11-10
Sorry for the late response, i've been away. It just returns -1. The error message is the one on the original post.

I'm just using normal read and write, but with sendfile i wouldn't have to create a buffer with a limited size and do several readings. I think...

---

### Post by gradedcheese on 2007-11-10
Well, for what it's worth, -1 is generally:

```

#define EPERM            1      /* Operation not permitted */

```

...so, just a guess: try running your test code with 'sudo'?  What port are you using to communicate over?

---

### Post by raul_ on 2007-11-10
It's not a permission problem =\ i'm using 40000 but that's just arbitrary. I guess i'll stick to the standard write and read procedures.

When I get sendfile working i'll post it here :)

---

### Post by rejuvenate on 2010-02-10
i am new to socket programming and need to build a ftp server how to recieve file at the client if i use sendfile().
thnx in advance

---

### Post by Sinkingships7 on 2010-02-10
> **rejuvenate said:**
> i am new to socket programming and need to build a ftp server how to recieve file at the client if i use sendfile().
thnx in advance

Welcome to the wooorld of tomorrooooww!

This post is over two years old, so you'll probably want to start a new thread. Although I commend you greatly for using the search feature so efficiently. =]

---

