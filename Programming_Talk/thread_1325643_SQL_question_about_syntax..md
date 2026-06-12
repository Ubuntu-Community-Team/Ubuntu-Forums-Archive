---
title: "SQL question about syntax."
date: 2009-11-13
forum: Programming Talk
---

### Post by hockey97 on 2009-11-13
Hi, I just want to know how I can use AND and OR  in the where clause.

What I mean is for example lets say I want to grab posts made by people in a country,state,city.  

Yet in the form I allow to  select the city from the drop down menu or they can  directly type the zip code in a text box. 

now in the query I want to search for all the values that match with the country,state, city or zip. 

I want them to use either city or zip code. either one.  How can I do this.

I  am putting AND to everything. I just want only city and zip to have a OR where either one would be good. 

How would I write the AND and OR out after the where clause?

I was told to do something like this :

```
 SELECT * FROM table WHERE country = $country AND state = $state AND ( city = $city OR zipcode = $zip
``` 

that code is just the theory just notice where city and zipcode is at I was told to put ()  that way it's still part of AND  and inside the and are 2 values that are OR.

---

### Post by doas777 on 2009-11-13
well, the trick is to use parentheses. the keywords are literally 'AND' & 'OR', so thats easy enough.

Select thing1, thing2 from tTable Where thingID = 99 AND (thing1 = 'hello' OR thing2 = 'goodbye')

think of each boolean as returning a value (including the OR expression in parens).
in this case the expression in parens will return either true (if one or the other or both are true) or false (if both are false)

AND
TT = T
TF = F
FT = F
FF = F

OR
TT = T
TF= T
FT = T
FF = F

---

### Post by hockey97 on 2009-11-14
ok here is my query : ```
mysql_query("SELECT * FROM postings  WHERE state ='".$state."' AND Country ='".$country."' AND city ='".$city."' OR zipcode ='".$zipcode."'  AND item ='".$item."' LIMIT $s,$limit")
```

that is what I have now. I know about that logic your talking about ,and,or,nor etc. 

I am just trying to find out how in sql syntax do we do it. 

the query above it If I do this:```
mysql_query("SELECT * FROM postings  WHERE state ='".$state."' AND Country ='".$country."' AND (city ='".$city."' OR zipcode ='".$zipcode."')  AND item ='".$item."' LIMIT $s,$limit")
```

I get a none working query.  I won't get any errors just no results. If I don't have the () in then I get results and if I try and not give city value and leave it blank but give a zip code value I won't get results. 

I only can get results if I put the city value. 

I just want it so that  either one could be used. If  a user wants to type in the zip code then they could or if they want to select it from a drop down menu they can do it that way too. Just making a option for the user to decided which route they want to take.

---

### Post by doas777 on 2009-11-16
so are you passing in a null if either city or zip are not present?

---

