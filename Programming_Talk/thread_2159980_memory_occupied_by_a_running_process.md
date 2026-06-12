---
title: "memory occupied by a running process"
date: 2013-07-05
forum: Programming Talk
---

### Post by IAMTubby on 2013-07-05
Hello,
I wrote the following perl script which reads in 34955 bytes of data from a hexfile. My basic aim is to see if the size is greater with and without the buffer into which I read the contents.So I added a sleep to the code and did **ps -aux | grep myperlscript;** and **pmap -x <pid>** while the process was sleeping.
_However, the size was the same with and without the **undef $buffer;**. This line was added as a free(in C) equivalent of perl_

```
#!/usr/local/bin/perl

open (FILE,'myhex.dat') or die "could not open file myhex.dat";
read(FILE,$buffer,34955);
undef $buffer;**#Was expecting to get different memory sizes with and without this line, while the process is 'sleep'ing**


print "going to sleep";
sleep 50;
print "came back from sleep";


close (FILE);

```

Please advise.
Thanks.

---

### Post by trent.josephsen on 2013-07-05
There is no equivalent to free() in Perl. undef decrements the reference count on an object so the reference counting garbage collector (Perl has two garbage collectors that run at different times) can reclaim the memory used for it. ($buffer = 'hello, world'; would have the same effect.) You cannot request that memory be released to the OS. Even if there was a free() equivalent, see [this recent thread](http://ubuntuforums.org/showthread.php?t=2159835) -- it probably would not release the memory back to the OS anyway. Acquiring and releasing memory is expensive. See also [http://www.perlmonks.org/?node_id=732263](http://www.perlmonks.org/?node_id=732263).

Are you encountering memory issues? Memory that has been allocated and reclaimed by the garbage collector should be transparently re-used when the same process needs more later. If you're starving other processes or using a large fraction of available memory, you should probably reconsider your algorithm. Otherwise, the usual advice is to forget about it. RAM is cheap.

---

