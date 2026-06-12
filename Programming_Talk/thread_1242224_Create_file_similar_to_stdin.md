---
title: "Create file similar to stdin"
date: 2009-08-16
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-08-16
I want to create a file that when read, the reading program must wait for it to be filled (whether by human or program)

try:
```
# cat /dev/stdin
```

this could be used it 1000's of ways, but I would use it to create a dynamic playlist that mplayer could read. Basically, you invoke mplayer with a playlist that when read calls another program to provide content.

... PS ...

after writing this, I tried "mplayer -playlist /dev/stdin". This failed, because mplayer reads the whole playlist before running!

if someone knows a way to get around that by forcing mplayer to read playlist a song at a time, I would appreciate it.

...    ...

But the First question it still going

---

### Post by soltanis on 2009-08-16
You might want to consider a FIFO pipe. Read the man page for the mkfifo (1) command, then pipe it into the program you want. Reading from the pipe will block until another program writes to it (i.e. it is filled with information).

Data written to FIFOs doesn't make it to the disk; it's buffered in kernel memory.

However, these pipes are finicky -- when using them myself I have run into many a problem.

---

### Post by Lux Perpetua on 2009-08-17
This might be an example of what you're looking for: [http://forums.devshed.com/showthread.php?p=1926035#post1926035](http://forums.devshed.com/showthread.php?p=1926035#post1926035)

See the attachment in the post by Scorpions4ever. It creates a fake device, /dev/fibonacci, that spits out Fibonacci numbers when you read from it. That at least shows you that it can be done, as well as giving you an idea of the type of work that may be in store for you.

---

