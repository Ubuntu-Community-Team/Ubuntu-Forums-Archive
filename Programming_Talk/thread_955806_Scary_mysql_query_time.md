---
title: "Scary mysql query time"
date: 2008-10-22
forum: Programming Talk
---

### Post by likwid on 2008-10-22
I'm having a hellish time with a mysql query.

It goes like this. I have three tables, one is of items, another of categories which each item falls into one of, the other tokens which each item has multiples of.

The point of the tokens are to allow the user to search for an item by multiple characteristic. For example, something may be 'red' *and* 'round', i need my query not to use an IN which is 'red' *or* 'round'. 

The query would return the categories rather than the items and the number of found items within each category.

Here are some tables:

items
+------+-------+--------------------+
|id | name   |  desc       | itemCat|
+------+-------+--------------------+
| 1 | item 1 | item desc 1 |   4    |
| 2 | item 2 | item desc 2 |   3    |
| 3 | item 3 | item desc 3 |   1    |
| 4 | item 4 | item desc 4 |   3    |
+------+-------------------|--------+


cats
+----+-------------------+
| id | name | des        |
+----+-------------------+
| 1 | cat 1 | Cat desc 1 |
| 2 | cat 2 | Cat desc 2 |
| 3 | cat 3 | Cat desc 3 |
| 4 | cat 4 | Cat desc 4 |
| 5 | cat 5 | Cat desc 5 |
| 6 | cat 6 | Cat desc 6 |
| 7 | cat 7 | Cat desc 7 |
+----+------+------------+


itemToks
+-------+---------+
| itemId |  tok   |
+-------+---------+
| 1      | green  |
| 1      | round  |
| 1      | large  |
| 2      | small  |
| 2      | yellow |
| 3      | small  |
| 3      | blue   |
| 4      | small  |
| 4      | red    |
+-------+---------+

What I would hope returned is something like this when searching for small:

+----+-----+-------+
| id | cat | count |
+----+-----+-------+
| 0 | Cat1 | 0     |
| 1 | Cat2 | 1     |
| 2 | Cat3 | 0     |
| 3 | Cat4 | 1     |
| 4 | Cat5 | 0     |
+----+-----+-------+

and something like this when searching for small and red:


+----+-----+-------+
| id | cat | count |
+----+-----+-------+
| 0 | Cat1 | 0     |
| 1 | Cat2 | 0     |
| 2 | Cat3 | 0     |
| 3 | Cat4 | 1     |
| 4 | Cat5 | 0     |
+----+-----+-------+

note that matches must be of both characteristic so IN statements don't work. 

So, any ideas because I've spent hours on this and got nowhere.. :D

---

### Post by bruce64 on 2008-10-22
I guess a good place to start would be the sql statement you created and we can go from there.  

select 
from 
where

---

### Post by likwid on 2008-10-23
[PHP]SET FOREIGN_KEY_CHECKS = 0;

CREATE TABLE `cats` (
`id` int(10) unsigned NOT NULL auto_increment,
`name` varchar(100) NOT NULL,
`des` varchar(100) NOT NULL,
PRIMARY KEY (`id`),
UNIQUE KEY `name` (`name`)
) ENGINE=InnoDB AUTO_INCREMENT=8 DEFAULT CHARSET=latin1;

insert into `cats` values('1','cat1','Cat desc 1'),
('2','cat2','Cat desc 2'),
('3','cat3','Cat desc 3'),
('4','cat4','Cat desc 4'),
('5','cat5','Cat desc 5'),
('6','cat6','Cat desc 6'),
('7','cat7','Cat desc 7');

CREATE TABLE `items` (
`id` int(10) unsigned NOT NULL auto_increment,
`name` varchar(100) NOT NULL,
`des` varchar(100) NOT NULL,
`catId` int(10) unsigned default NULL,
PRIMARY KEY (`id`),
UNIQUE KEY `name` (`name`)
) ENGINE=InnoDB AUTO_INCREMENT=8 DEFAULT CHARSET=latin1;

insert into `items` values('1','item 1','item desc 1','2'),
('2','item 2','item desc 2','3'),
('3','item 3','item desc 3','7'),
('4','item 4','item desc 4','3'),
('5','item 5','item desc 5','5'),
('6','item 6','item desc 6','6'),
('7','item 7','item desc 7','1');

CREATE TABLE `itemToks` (
`itemId` int(10) unsigned NOT NULL,
`tok` varchar(100) NOT NULL,
PRIMARY KEY (`itemId`,`tok`)
) ENGINE=innoDB DEFAULT CHARSET=latin1;

insert into `itemToks` values('1','green'),
('1','large'),
('1','round'),
('2','small'),
('2','yellow'),
('3','blue'),
('3','small'),
('4','red'),
('4','small'),
('5','large'),
('5','orange'),
('5','square'),
('6','medium'),
('6','pink'),
('6','triangular'),
('6','yellow'),
('7','massive'),
('7','purple'),
('7','round'),
('8','brown'),
('8','tiny');

SET FOREIGN_KEY_CHECKS = 1; [/PHP]
[PHP]

SELECT c.id
     , c.name
     , COALESCE(matches.cnt, 0) AS count
  FROM cats AS c
LEFT OUTER
  JOIN ( SELECT COUNT(*) as cnt
              , id
           FROM items as i
         INNER
           JOIN itemToks as it
             ON it.itemId = i.id
		  WHERE it.tok in ('green', 'round', 'small')
          GROUP
             BY id ) AS matches
    ON c.id = matches.id[/PHP]


Problem with this is that the query returns queries where a token is green OR round OR small when I want tokens that are all of these characteristics returned.

---

### Post by DrMelon on 2008-10-23
You could try "+" instead of "," between the things you're looking for. Like:

[PHP]WHERE it.tok in ('green' + 'round' + 'small') [/PHP]

Might work. Not sure though.

---

### Post by pp. on 2008-10-23
In other words, you want to count an item if it is associated both with a 'red' token and a 'round' token. That's two joins, not one.

---

### Post by kernelhaxor on 2008-10-23
say u r searching for 'small' and 'red'
```

select cats.id, cats.name, count(*)
from cats, items, itemToks it1, itemToks it2
where cats.id = items.itemCat and it1.itemId = items.id and it2.itemId = items.id
      and it1.tok = 'small' and it2.tok = 'red'
group by cats.id, cats.name
```

The above query has two joins coz u hav two tokens 'small' & 'red' .. u wud need three joins if u hav three tokens and so on ..

There might be a better way to do it although I doubt it .. let me know if that doesnt work

---

### Post by likwid on 2008-10-23
Thanks all for replies. 

DrMelon, That doesn't work I'm afraid.

pp and kernel, It looks indeed like it's multiple joins which is a total pain as there will be varying numbers of tokens. I can dynamically build the query in php though which is ok, but if anyone has a better idea, that would be great.

kernel, your query works great except for the fact I need count = 0 returned, rather than just those with count > 0. For example kinda like:

[PHP]+----+------+-------+
| id | name | count |
+----+------+-------+
|  1 | cat1 |     2 | 
|  2 | cat2 |     1 | 
|  3 | cat3 |     1 | 
|  4 | cat4 |     1 | 
|  5 | cat5 |     0 | 
|  6 | cat6 |     0 | 
|  7 | cat7 |     1 | 
+----+------+-------+
[/PHP]
rather than
[PHP]+----+------+-------+
| id | name | count |
+----+------+-------+
|  1 | cat1 |     2 | 
|  2 | cat2 |     1 | 
|  3 | cat3 |     1 | 
|  4 | cat4 |     1 | 
|  7 | cat7 |     1 | 
+----+------+-------+
[/PHP]
If anyone does have a better solution, ie one using something similar to an IN statement where I can throw the tokens between parenthesis, i'd be very grateful.

Cheers all!

---

### Post by DrMega on 2008-10-23
Does MySQL support the EXISTS keyword? If it does, you could put something like this in your WHERE clause:

```

WHERE EXISTS(SELECT itemToks.id FROM itemToks WHERE tok = 'red')
AND EXISTS(SELECT itemToks.id FROM itemToks WHERE tok = 'round')

```

(Note, if you do that, you don't need to join to the itemToks in your main query).

---

### Post by likwid on 2008-10-23
Thanks for reply.:)

Looks like EXISTS works but I think I still need a join, otherwise the query recognises that the combination of tokens exist and returns all categories.

---

### Post by DrMega on 2008-10-23
> **likwid said:**
> Thanks for reply.:)

Looks like EXISTS works but I think I still need a join, otherwise the query recognises that the combination of tokens exist and returns all categories.

You'll still need a join, as you'll need to join to category. I meant that you won't need to join to itemToks.

---

### Post by pp. on 2008-10-23
> **likwid said:**
> 
pp and kernel, It looks indeed like it's multiple joins which is a total pain as there will be varying numbers of tokens. I can dynamically build the query in php though which is ok, but if anyone has a better idea, that would be great.

If the values of the tokens are constant, you might want to look into crosstabs. That's not, perhaps, a 'better' idea, but it is a different one.

> **likwid said:**
> kernel, your query works great except for the fact I need count = 0 returned, rather than just those with count > 0. For example kinda like:

From my rusty SQL experience: isn't this what the left, right, outer etc. joins are about?

---

### Post by DrMega on 2008-10-23
> **pp. said:**
> From my rusty SQL experience: isn't this what the left, right, outer etc. joins are about?

Time for a quick rundown on SQL joins:

You get INNER joins and OUTER joins. We mostly use INNER, so much so that often you don't need to specify INNER as it is assumed by default.

You also get, LEFT, RIGHT and FULL joins.

If you have two tables, TableA and TableB, and you want to join them:

FROM TableA
INNER JOIN TableB
ON idA = idB

...gives you the joined tables where there are records in TableA with a matching foreign key to table B and there are records in TableB with a key match to TableA. I.e. you only get records where there is a match in both.

FROM TableA
LEFT JOIN TableB
ON idA = idB

...gives you all the records in TableA and where there is a match in TableB you get the records, otherwise you get the fields but with NULL values.

FROM TableA
RIGHT JOIN TableB
ON idA = idB

...gives you matching records in TableA and all the records from TableB. Where there is no match in TableA you get nulls in the fields from that table (ie it is the opposite of a LEFT join)

FROM TableA
FULL OUTER JOIN TableB
ON idA = idB

...gives you ALL the records from both tables, joining them where possible and leaving nulls where there is no match in one or the other.

Obviously you might then go on to restrict the result set using a WHERE clause.

---

### Post by kernelhaxor on 2008-10-23
getting count 0 ones is simple ..so yeah use my query with one of those outer joins (I think you wanna use left outer) and  you will get categories with count 0 too ..
let me know if tht doesnt work ..

---

### Post by likwid on 2008-10-24
Thanks everyone very much for help. Here is a working query:
[PHP]SELECT c.name, COUNT(X.name) FROM cats c
LEFT JOIN
(
  SELECT i.`name`, i.catid, COUNT(*) as ct
  FROM items i
  INNER JOIN itemtoks t ON i.id = t.itemid AND t.tok IN ('green','round','large')
  GROUP BY i.`name`
  HAVING ct > 2
) as X
ON c.id = X.catid
GROUP BY c.name
[/PHP]:D

---

