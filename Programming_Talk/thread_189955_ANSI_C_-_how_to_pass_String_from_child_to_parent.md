---
title: "ANSI C - how to pass String from child to parent ?"
date: 2006-06-05
forum: Programming Talk
---

### Post by B0rsuk on 2006-06-05
Hey

I almost finished one of my university programs. It's a very simple Instant Messaging-like program. It operates on BSD sockets; a server and a number of clients. It's based on an example our teacher gave us.
It's finished in 95 percent, but I suddenly realized I can't save a message in server's "database". To my horror, it turned out I update the database... inside a child process. So I actually only update child's copy of it.

**I need a quick dirty, and simple hack to pass a string** (single word/token, actually) **from child to parent.** Is there a simple way to do it ? Exit returns only integers, right ?
I know of functions getpid() and getppid(), but they don't sound very useful for this particular scenario. I'm a beginner programmer, there's little time left and I can't think of a simple solution.

To give you an idea, here's how the 'server database' mockery looks like:

```

struct dane {
    int ID;
    char czyja[9];
    char skrzynka[20];
};

```

```

   struct dane wpis[] = {
	{0, "filemon", "a"},
	{1, "bonifacy", "b"},
	{2, "dziadek", ""},
	{3, "babcia", "c"},
	{-1, "EOF", "EOF"},
    };

```

Forks are handling incomming socket connections in the way I don't exactly understand (I used a working example), but I need to write to **PARENT's**
strcpy(wpis[3].skrzynka, wiadomosc);      
field.

Please, can you help ? It's the last thing I have to fix in this program  : (

---

### Post by daneel_olivaw on 2006-06-06
well the most standard way in unix to exchange data between processes are pipes.. a pipe is an array of two file descriptors, one is for writing and one is for reading; the parent creates the pipe, then forks (so that the child and the parent share the two file descriptors) and then each of the parent and child close the one direction that they don't use.

[this]("http://beej.us/guide/") is a great collection of tutorials for C programming language.. take a look at it

I avoid you searching as u dont have time :P [this]("http://beej.us/guide/ipc/pipes.html") is the pipe section.

cheers

---

### Post by B0rsuk on 2006-06-06
Thanks a lot !
It's actually a bit embarassing, because we did have a few lectures (and programs using) pipes. Anyway, I got the pipe idea while in work.

After  I returned, I tried to use **named** pipes, but it felt like squaring the circle: I wasn't able to pass the descriptor, because 
1) both mkfifo and (I think) mknod return only success or failure, not descriptors.
2) as soon as I open the pipe file in parent before forking, it gets blocked... which is nice for synchronisation, but not in this particular case. nonblock flag wouldn't do me any good.

I completely forgot about unnamed pipes (because I never learned to use them with C), and they seem to be **the** tool for the job ! Thanks.

---

### Post by daneel_olivaw on 2006-06-08
you're welcome :)

---

