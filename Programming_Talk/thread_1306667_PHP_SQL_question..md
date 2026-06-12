---
title: "PHP SQL question."
date: 2009-10-30
forum: Programming Talk
---

### Post by hockey97 on 2009-10-30
Hi, I want to know could a sql Where clause use more then one field?

let me explain. I want to do something like this:

```
SQL ->  ("SELECT * FROM places WHERE country = $country  , state = $state , city = $city catagory = $catagory");
``` 

I want to know if I can use more then one condition in the where clause and if so how do I seperate each condition?

do I just use ,  or use  . . inbetween the conditions then followed after by a , ?

my goal here is to query search postings made by users for only their country,state/region,city, and the catagory. Like what the postings about.

I want to use those values to grab only matching values from the database and display them.

So how would I do this correctly. what do I need to use to seperate each filed = too values...

Thanks you for your time.

---

### Post by konqueror7 on 2009-10-30
you use 'AND' to connect conditions, say

```
SELECT * FROM table1 WHERE column1 = 1 AND column2 = 2
```

this will get you the data matching all the given conditions, you may want also to just make a wildcard using 'LIKE'. for more info [here]("http://www.w3schools.com/sql/default.asp")

---

### Post by OpenGuard on 2009-10-30
Use AND / OR ..

P.S. - [COLOR=Gray]field = 'value'[/COLOR], not [COLOR=Gray]field = value[/COLOR]

---

### Post by hockey97 on 2009-10-30
would I be able to also add a OR in those conditions?

Cause I want to allow the users to either select a city name or type in a zip code. So in the sql I want to use either one but not both.

---

### Post by hockey97 on 2009-10-30
ok thanks. THe reason I ask this is that I am getting a error. 

here is my exact sql code ```
"SELECT * FROM postings WHERE state ='$state' AND Country ='$country' AND city ='$city' AND/OR zip code ='$zipcode'  AND item ='$item'")
```

The error I get is: ```
Warning: mysql_num_rows(): supplied argument is not a valid MySQL result resource in ... line 22
```

Line 22 is  mysql_num_rows($query1) and $query1 has the query listed above with the code to excute the query.

---

### Post by OpenGuard on 2009-10-30
AND and OR are 2 separate keywords: [http://www.w3schools.com/Sql/sql_and_or.asp](http://www.w3schools.com/Sql/sql_and_or.asp)

---

### Post by korvirlol on 2009-10-30
[FONT=monospace]try this


[/FONT]```
$q = mysql_query("SELECT * FROM postings WHERE state ='".$state."' AND Country ='".$country."' AND city ='".$city."' AND/OR zip code ='".$zipcode."'  AND item ='".$item."'")
```

putting variables in a string without something telling it that it contains variabls is always risky

---

### Post by hockey97 on 2009-10-30
I gave those a try and still get the same error. I been trying other stuff also and doing google searches. 

I still can't get it going. I will try and figure it out.

---

### Post by korvirlol on 2009-10-30
are you sure the query is correct? that error usually means the query has failed.

change your code to:

$query = mysql_query(*your query*) or die (mysql_error());

or

$query = mysql_query(*your query*) or print mysql_error();

if you dont like using die (some programmers dont, i just think they are anal).

---

### Post by mike_g on 2009-10-31
> I gave those a try and still get the same error. I been trying other stuff also and doing google searches.

I still can't get it going. I will try and figure it out.
Remove the "AND/OR" part of your query and replace it with "OR". OR returns true if either or both conditions are met. XOR only returns true when one, not both conditions are true.

---

