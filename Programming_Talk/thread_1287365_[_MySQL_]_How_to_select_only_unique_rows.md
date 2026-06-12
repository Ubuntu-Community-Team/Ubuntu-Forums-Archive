---
title: "[ MySQL ] How to select only unique rows ?"
date: 2009-10-10
forum: Programming Talk
---

### Post by OpenGuard on 2009-10-10
[php]$query = mysql_query("SELECT DISTINCT alias FROM accounts");[/php]This will return all unique alias fields, but I need other row fields as well. I mean, I need something like *[COLOR=DimGray]SELECT * FROM[/COLOR]* *[COLOR=DimGray]accounts[/COLOR]*, but only if current alias isn't already selected. Currently there are no duplicate entries, but I know they can occur.

[IMG]http://i37.tinypic.com/30w36hj.png[/IMG]

Any ideas ? I know I could select all unique aliases and then go through a loop and select all values, one by one, but there should be an easier way of doing this ?

---

### Post by v8YKxgHe on 2009-10-10
Can you explain further? Not quite understanding what you mean. Only to select rows where 'alias' only exists once? So it would select those 3 rows in the image, but if there were 2 rows with the same 'alias' value, it would not be returned?

---

### Post by OpenGuard on 2009-10-10
> **AlexC_ said:**
> Can you explain further? Not quite understanding what you mean. Only to select rows where 'alias' only exists once? So it would select those 3 rows in the image, but if there were 2 rows with the same 'alias' value, it would not be returned?

In this case, it would return 3 rows, but if I would add another row with an alias "wmz" ( which already exists ), it would still return only 3 rows, not 4 ( as there would be 2 "wmz" alias rows ). I simply need something similar to DISTINCT, except, I need it to return a full row, not only some specific fields value.

---

### Post by hal10000 on 2009-10-10
SELECT alias FROM accounts

---

### Post by OpenGuard on 2009-10-10
> **hal10000 said:**
> SELECT alias FROM accounts

It'll select all rows, which means that if there will be two identical aliases, I will get them both. The idea is to create a form with <select>, where I should see only unique values, not 2x "wmz", 1x "wmr", etc.!

```
SELECT DISTINCT alias FROM accounts
```

This will return only alias column .. is there a way to edit this query so that it would return the whole row, not only alias field ?

---

### Post by NoaHall on 2009-10-10
```
SELECT alias FROM accounts WHERE alias=alias
```
?

Not quite sure what you want though.

---

### Post by Tony Flury on 2009-10-10
If you had this data : 

```

Alias      Name
wmz        Tony
xyp        Michael
wmz        Barry

```

What would you want the query to return - for instance if you could get it to only return one row with the alias "wmz", what value for Name would you want it to return ?

---

### Post by hal10000 on 2009-10-10
> This will return only alias column .. is there a way to edit this query so that it would return the whole row, not only alias field ?

try

SELECT DISTINCT alias, id, name, account FROM accounts

---

### Post by OpenGuard on 2009-10-10
> **Tony Flury said:**
> If you had this data : 

```

Alias      Name        Commission
wmz        Tony            0.02
xyp        Michael          0.00
wmz        Barry           0.02

```What would you want the query to return - for instance if you could get it to only return one row with the alias "wmz", what value for Name would you want it to return ?

Ok, firstly, I modified your example ( I hope that's ok ? ). You see, no matter how many wmz's you will add, commission field will always be the same. I need to get all unique aliases and associative commission rates.

The output should be something like this:
```
wmz - 0.02
xyp - 0.00
```

---

### Post by OpenGuard on 2009-10-10
> **hal10000 said:**
> try

SELECT DISTINCT alias, id, name, account FROM accounts

[COLOR=Black]Bingo![/COLOR] Thank you :)

---

