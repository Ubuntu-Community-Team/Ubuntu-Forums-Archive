---
title: "Best Way To Access Ubuntu Routing Table Details"
date: 2013-03-02
forum: Programming Talk
---

### Post by jeraldpaul on 2013-03-02
Hi ppl,

I am working on a project which has something to do with working on the kernel routing table.
So for my part, this is what I intend to achieve through a C program:

[COLOR=#ff0000][B][I]1. Get a count of the number of entries in the linux kernel routing table.
2. Get the exact memory occupied by linux kernel routing table.
3. Get details of some statistics like how many times if is the routing table being looked up.
4. Get details of some statistics like how often is the routing table being updated.[/I][/B][/COLOR]

This is what I know and am doing:

1. I believe that routing table is stored at /proc/net/route and we **cannot **access its size through the C programming method struct stat
2. I use **popen **to read the output of one of the following command to get the size of the routing table:
    a) wc -c | netstat -rn
    b) wc -c | ip route
3. So I am using the **wc** with the plugs **-c** and **-l** to do my stuff I am doing but I believe it is really inefficient if my routing table has millions of entries and if I do this wc thing very frequently 


Got any bright ideas better than mine?


Cheers,
me

---

### Post by r-senior on 2013-03-02
> **jeraldpaul said:**
> I am working on a project which has something to do with working on the kernel routing table.
If it's homework, you can say so.

> 1. I believe that routing table is stored at /proc/net/route and we **cannot **access its size through the C programming method struct stat
Why would its size help? If you could get the size that would be the number of characters.

> 2. I use **popen **to read the output of one of the following command to get the size of the routing table:
Why not just open the file and read it in C?

> a) wc -c | netstat -rn
I think you misunderstand you the pipe works. Also "wc -c" will give the number of characters, which is not what you want.

> 3. So I am using the **wc** with the plugs **-c** and **-l** to do my stuff I am doing but I believe it is really inefficient if my routing table has millions of entries and if I do this wc thing very frequently
Make it work, then make it work well is an old adage, but still a good one.

---

### Post by jeraldpaul on 2013-03-02
unfortunately i do not know of a way to know the size of the file '/proc/net/route' other than counting the number of characters.. struct stat does not work.. so u can understand that if the file contains of millions of characters, it will take long.. the routing table i am working with will have millions of entries (actually its a project, not a homework).. therefore number of characters is equal to number of byte = size..

sorry that was a type.. i use popen on [B]wc -c < /proc/net/route

[/B]frequently reading a file with millions of characters is inefficient..
Is there any place in the kernel from where I could directly access the number of entires in the kernel routing table or its size..
I think the following formula would give an idea of the number of entries
[B]Number of Entries = (Size of Routing Table Storage File '/proc/net/route') / 128


[/B]

---

### Post by jeraldpaul on 2013-03-02
Actually.. the following will also work.. 

netstat -rn | wc -l
ip route | wc -l

but then again its again inefficient when the number of entries is very very large.. i am doing monitoring of the kernel routing table so will need to grab these stats periodically.. therefore an efficient way is very important..

---

### Post by jeraldpaul on 2013-03-04
Hi All,

Does anyone have a better idea of fetching the size of the file /proc/net/route ?

---

