---
title: "how to determine the available heap size"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by smita raj on 2008-10-06
hi 
Can anybody tell how to determine the available heap size?

---

### Post by jamesrl on 2008-10-11
I'm pretty sure the available heap size is equivalent to the amount of free memory you have, which you get by going to the terminal and running

```
free -m
```

---

### Post by smita raj on 2008-10-13
I think this gives the info about RAM size n all. Is RAM size in linux is equal to Heap size?

---

### Post by jamesrl on 2008-10-14
I'm by no means an expert on the specifics of linux memory management, but my understanding is that the heap is just [the large pool of unused memory]("http://en.wikipedia.org/wiki/Dynamic_memory_allocation#Details") on your computer that a program can dynamically grab memory from when it needs it.  You get that info from free -m (look in the last two rows, in the free column).  If you want to know how much of your memory is used by any specific program use ```
top
``` (personally I prefer htop but you have to install it first  [sudo apt-get install htop])

You can also get more information about memory usage by

```
cat /proc/meminfo
```

---

### Post by smita raj on 2008-10-14
Hi thanks for the information. 
Do you know how frequently /proc/meminfo file get updated?
Do you know any api which returns the heap size?

---

### Post by jamesrl on 2008-10-14
Files in /proc/ aren't files in a traditional sense, as in they aren't read off the hard drive, the data is generated when you go to look at them.  It's a pseudo-filesystem (see "man proc") or just recognize that running ls -l shows all files as 0 bytes in there.

I don't know what you specifcally mean by needing an API.  If you want to get how much available memory you have left (e.g., memory that is available for the heap to use), you can type for example:
```

free -m | grep /+ | gawk '{ print $4 }'

```
e.g., if you need it in a bash script you could do
```

available_memory=`free -m | grep /+ | gawk '{ print $4 }'`

```
and you have a variable $available_memory that you can use in comparisons or what not.

---

### Post by smita raj on 2008-11-03
Thanks for help.
Actually I am completely new to linux. And I have to write a function which will return the heap size. That's why I was asking for API's. Anyways thanks.

---

