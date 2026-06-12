---
title: "MySQL find missing numbers in table"
date: 2010-08-08
forum: Programming Talk
---

### Post by jflaker on 2010-08-08
I think this is easy, but not sure

MySQL table with a single integer field populated with a numeric series.

I need to find all missing numbers.

Thanks

---

### Post by Bachstelze on 2010-08-08
Ordered or not?

---

### Post by jflaker on 2010-08-08
> **Bachstelze said:**
> Ordered or not?

Don't care...just want to figure out the missing numbers.  There are about 13.5K records

---

### Post by DaithiF on 2010-08-08
Hi,
theres a slightly long-winded though foolproof way to do this, and a couple of quick shortcuts you may be able to take depending on your circumstances.

First the short-cut ways:
1. create a sequence of integers and look for ones which don't appear in the table.  Unfortunately theres no inbuilt ability in MySQL to generate a sequence of integers so you have to do it in various kludgey ways incrementing variables:
```
select b.id from (select @row:=0) a, (select @row:=@row+1 as 'id' from some_large_table where @row < <some_limit> ) b
where b.id not in (select id from <your_table>);

```This requires that you have a table that you know has more rows than the max. id in your target table.

2. join the table to itself, joining on id and next highest id, limiting the output to rows with a gap of > 1.  This will output ranges of missing numbers, rather than 1 per line, so for example if you were missing numbers 3, 6, 7 and 8 you would get output like:
3  3
6  8
if thats ok, then:
```
select a.id + 1, min(b.id) -1 as 'next_id' from your_table a, your_table b
where a.id < b.id
group by a.id
having (next_id - a.id)  > 0;
```

3. and the foolproof way: create a stored procedure which generates a temporary table with a sequence of integers, then select from that where no entry exists in the target table.  In the stored procedure you can use a loop (which you can't use interactively) to create the sequence.
see [http://stackoverflow.com/questions/2495487/number-sequence-in-mysql](http://stackoverflow.com/questions/2495487/number-sequence-in-mysql)
for an example of such a procedure

---

### Post by jflaker on 2010-08-08
```
select a.id + 1, min(b.id) -1 as 'next_id' from your_table a, your_table b
where a.id < b.id
group by a.id
having (next_id - a.id)  > 0;
```

this worked.  Took about 3 minutes to run, but I got what I needed!

Thanks!

---

