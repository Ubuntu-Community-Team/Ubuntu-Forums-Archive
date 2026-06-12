---
title: "A tricky bit of mySQL"
date: 2008-06-25
forum: Programming Talk
---

### Post by mikeym on 2008-06-25
Sorry again for this fairly non-ubuntu related question. 

I'm trying to make a mySQL SELECT statement that calculates a page number for me using a FLOOR statement. The problem is that the calculation depends on a second SELECT. It looks like this in pseudo-SQL.

```

SELECT `name` , `bbcode` AS 'title', 'chat' AS 'type', `edited` AS 'date', CONCAT(`page`, '?page=', CONVERT(FLOOR(

(SELECT COUNT(`chatid`) 
FROM `chat`
WHERE `date` < `date.parentselect`)
/ 10

) USING latin1)) AS 'url', CONVERT( ''
USING latin1 ) AS 'image'
FROM `chat`
WHERE `edited` >= '$yesterday' 
ORDER BY `edited` DESC
LIMIT 0 , 15

```

Basicly I'm trying to use the result of COUNT from a select satement within a select statement. Probably the trickiest bit is that the internal SQL statement depends on one of the fields from the parent select. 

The idea is to create a page reference for one of the fields but this depends on how many records come before the record ordered by date. 

Thanks for any ideas.

---

### Post by henchman on 2008-06-25
Iam not quite sure if i understood your problem right, but i believe you would like to know how to access the value of the outer select from the inner select. If it's this, here's how to do it:

```
SELECT `name` , `bbcode` AS 'title', 'chat' AS 'type', `edited` AS 'date', CONCAT(`page`, '?page=', CONVERT(FLOOR(

(SELECT COUNT(`chatid`) 
FROM `chat`
WHERE `date` < outerTable.date)
/ 10

) USING latin1)) AS 'url', CONVERT( ''
USING latin1 ) AS 'image'
FROM `chat` AS outerTable
WHERE `edited` >= '$yesterday' 
ORDER BY `edited` DESC
LIMIT 0 , 15
```

As iam not familiar with how to use the backtick-characters i could just guess where to place them. This should work and you can try setting backticks later on :)

---

