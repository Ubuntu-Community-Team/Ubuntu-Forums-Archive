---
title: "MySQL slows waaaaaay down"
date: 2009-02-09
forum: Programming Talk
---

### Post by blake82 on 2009-02-09
Hi All,

I've run into trouble with this analysis program I'm writing.

I have a mysql table that has ~ 13.5 billion rows in it, with about 500,000 new entries being added daily. The table has 18 columns, which include about 5,000 distinct names and the time and date info of when the data was captured.

I have a python script that goes through and pulls out the data for each name for a given date range and then sorts it.

When I first start the script, it runs along pretty fast (about 0.09 sec for each name), then it starts to slow way the hell down to a couple seconds per name.

One of two things starts to happen. First, mysql decides not to use both cores at 100%, not sure why. That, or it will start using the disk really heavily.

I've run mysqlreport, and it has plenty of query and key cache, so I don't know what's going on.

Any ideas?

---

### Post by Gordon Bennett on 2009-02-09
Barring a bug, this type of performance drop really depends on your machine's configuration.

It looks like the application is filling up memory, causing the underlying OS to start paging out blocks of RAM to disk.

For example, say each retrieved entry takes up 64 bytes - by the time you get to 67 million entries it will already be filling up a 4GB memory machine.

Add to that the overhead of the sorting algorithm you are using (stack/heap allocation if it is recursive), the OS plus resident libraries/daemons footprint among other things and the number is even lower.

If you start seeing lots of disk activity when it slows down, that is what is happening.

---

### Post by slavik on 2009-02-09
I'm interested ... after you sort the data, what do you do with it then?

---

### Post by Ferrat on 2009-02-09
As Gordon stated the problem is probably memory and that it starts using the disk might mean that it has run out of ram and having to read more directly from the disk = much much slower having to swap all the time, also Slaviks question is a good one, since you don't really say what the DB is for I can only guess but have you thought about separating the information?

Since you sort it, make the "main" DB just keep last say 7 days, then transfer to a secondary DB keeping records but not being actively used like the first one? 
and make the script be able to access that if needed? 
Might be more coding etc but would probably bring down the memory usage?
If you need the all the data as comparison the script could use a third DB or add that to the first that just adds up the first and second DB and keeps the comparison data? 

Just throwing a few ideas out there

---

### Post by Gordon Bennett on 2009-02-09
> **blake82 said:**
> Hi All,

I've run into trouble with this analysis program I'm writing.

I have a mysql table that has ~ 13.5 billion rows in it, with about 500,000 new entries being added daily. The table has 18 columns, which include about 5,000 distinct names and the time and date info of when the data was captured.


Also, from the '~13.5 billion' number I gather you are mapping IP addresses to the data.

From this point on we are in the realm of large-number-set optimal database design and relational data.

For example, say I had a 1:trillion chance in rolling the number 2 on a (many sided :P ) dice.  One option would be to make a trillion-entry table that flags which row I have rolled at - however, that means there will be a large amount of redundant data.

An option would be to keep the table empty until a roll is made, then just add the roll number with associated data.

As for sorting large amounts of data, exploit the fact that you can divide what you are dealing with into blocks; if you are dealing with IP ranges you can partition the address ranges like so:

A table for IP ranges: 0.x.x.x
A table for IP ranges: 1.x.x.x
A table for IP ranges: 2.x.x.x
A table for IP ranges: 3.x.x.x
A table for IP ranges: 4.x.x.x
...  and so on...

With that you have reduced your sorting size problem 256-fold.  Even more if you subdivide it further.  There's more you can do - it depends on the resources that your processing machine has available to it and the underlying database structures used to represent the data.

---

### Post by blake82 on 2009-02-09
At first I thought it was a memory issue also. However, both the key and query caches are well below their limits according to mysqlreport, and there's plenty of system memory to spare, so I'm not sure that's the issue.

@ slavik:  This is a pet project that automatically creates efficient algorithms to solve complex mathematical and analysis problems without any sort of human interaction. It works really well on (relatively) simple problems, but larger problems require substantially more data so it can identify all the relevant variables, and this slowdown is pretty much putting things on hold.

Is there a way to revert MySQL startup settings to their default? I may have bunged something up fiddling around with them...

Also, I should probably point out that I'm extremely inexperienced with database programming and administration, so please share any 'so obvious it's not even worth mentioning' ideas.

Thanks!

Blake

---

### Post by Gordon Bennett on 2009-02-09
> **blake82 said:**
> At first I thought it was a memory issue also. However, both the key and query caches are well below their limits according to mysqlreport, and there's plenty of system memory to spare, so I'm not sure that's the issue.

Blake

Ok if the database is behaving, what about this bit:

> **blake82 said:**
> I have a python script that goes through and pulls out the data for each name for a given date range and then sorts it.

How much memory/data is the script taking up - does it pull in the whole lot before sorting it?

Enter in 'top' from the commandline when your process starts noticeably slowing down and the disk activity increases - take a note of the values in bold e.g.:

Mem:   **1016812k total**,   **976480k used**,    **40332k free**,    81180k buffers
Swap:  1253028k total,     **1952k used**,  1251076k free,   467276k cached

Also, the top three cpu-using processes.

What do you get?

---

### Post by blake82 on 2009-02-09
I'm using ORDER BY foo ASC in the query

The whole query looks like this:

```
Select * FROM `db`.`data` WHERE day BETWEEN x AND y AND name = z ORDER BY timeSec ASC
```

And I'm running it for each name, so basically the same query, ~5,000 times, and only the "z" value changes each time.

Then the data goes into a list in python. However, by my estimates, that should only take up roughly 300MB of RAM (I only load 1 - 2 days at a time)

---

### Post by blake82 on 2009-02-09
Thanks Gordon, let me try that when I get home

---

### Post by blake82 on 2009-02-10
Here's what it says when the HD use becomes heavy

```
Mem:   3111020k total,  3022040k used,    88980k free,   264444k buffers
Swap:  4988172k total,     4940k used,  4983232k free,  1123492k cached
```

---

### Post by Gordon Bennett on 2009-02-11
> **blake82 said:**
> Here's what it says when the HD use becomes heavy

```
Mem:   3111020k total,  3022040k used,    88980k free,   264444k buffers
Swap:  4988172k total,     4940k used,  4983232k free,  1123492k cached
```

Hmm - ok, so it's not paging out - that makes me think MySQL is having to load/reload large chunks of the database within its allocated buffer.  How much is given to the MySQL process in terms of memory/cache - can you change it (as a test) to 2x or 4x its current value?

---

### Post by blake82 on 2009-02-11
Actually, I think I got it figured out.

MySQL was caching all of the queries, and would slow down once it's query cache was full. Since I don't have any duplicate queries, I've added 

```
SQL_NO_CACHE
```

to the query, and now it's running pretty fast.

Also, I tweaked a lot of the other cache settings based on their usage from mysqlreport, and that sped things up a bit too. I guess bigger isn't always better :/

Thanks

---

