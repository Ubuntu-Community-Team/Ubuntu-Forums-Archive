---
title: "bash script help"
date: 2011-01-18
forum: Programming Talk
---

### Post by treyphan on 2011-01-18
Hello,

If this isn't the place to ask this type of question feel free to point me to the right place... 

I'm trying to figure out a way to write a bash script that copies a set of files one at a time from one directory to another and then starts over. 

In other words 

cp /home/user1/file1 /home/user2/
cp /home/user1/file /home/user2/
cp /home/user1/file /home/user2/
etc 

repeat


I think I am just over thinking this and will feel silly when someone points out how easy it is.... 

Any ideas? 

thanks,

C

---

### Post by Vaphell on 2011-01-18
you want an endless loop that copies the same files over and over?
what do you need it for because that sounds like a bad approach

either way endless loop
```
while ((1))
do
  ...
done
```

---

### Post by treyphan on 2011-01-18
> **Vaphell said:**
> you want an endless loop that copies the same files over and over?
what do you need it for because that sounds like a bad approach

either way endless loop
[code]while ((1))
do
  ...
done[/done]

I know that sounds very strange but it is too simulate a production situation that can't be reproduced any other way. I know it sounds bad but it a very long story and I really dont have a better option. LOL that is so simple that I feel even sillier than I thought I would. I guess its such a weird need that I never even thought about it. 

I'll give it a shot! 

thanks!

---

### Post by Vaphell on 2011-01-18
strange but ok :)
consider putting **sleep <time in seconds>** inside the loop in case you don't want a constant disk thrashing.

---

### Post by shawnhcorey on 2011-01-19
> **treyphan said:**
> Hello,

If this isn't the place to ask this type of question feel free to point me to the right place... 

I'm trying to figure out a way to write a bash script that copies a set of files one at a time from one directory to another and then starts over. 

In other words 

cp /home/user1/file1 /home/user2/
cp /home/user1/file /home/user2/
cp /home/user1/file /home/user2/
etc 

repeat


I think I am just over thinking this and will feel silly when someone points out how easy it is.... 

Any ideas? 

thanks,

C

Copy all non-hidden files:
```
$ cp -r /home/user1/* /home/user2
```

Copy all files:
```
(cd /home/user1 ; tar cBpf - .) | (cd /home/user2 ; tar xvBpf -)

```

---

