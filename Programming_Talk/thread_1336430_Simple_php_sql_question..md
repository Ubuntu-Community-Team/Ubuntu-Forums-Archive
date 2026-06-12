---
title: "Simple php sql question."
date: 2009-11-24
forum: Programming Talk
---

### Post by hockey97 on 2009-11-24
I need some help. I want to know using php sql to use OR in a query.

Let me explain in detail:

I have a html form which asks the user for country,state,city,zip_code 

I will use these values to query the database for specific data for those specific inputs. 

I want the city and zip_code to be logicly use as OR. Meaning that the user only needs to select a city or type the exact zip_code. Either one should still be able to grab the data from the database.

Here is the code I used:```
SELECT * FROM postings  WHERE state ='".$state."' AND Country ='".$country."' AND city ='".$city."' OR zipcode ='".$zipcode."'AND item ='".$item."' LIMIT $s,$limit"
```

I tried to use Where(first values goes here meaning with city value) Or (value of zip code); 

when I tried that code concept. I get a white screen with an error saying the syntax is wrong where limit starts at.


The query is supposed to grab all data based on that users form inputs. I am creating a paging effect. That is why I use the limit code.

Yet I want the user to input either the city name or zip_code.

how should I be doing this? I played around with the code but got nothing right now.

Currently the code only works when you input the country,state,city name. It won't allow to have the city name blank and use a zip code.

---

### Post by tturrisi on 2009-11-24
> SELECT * FROM postings  WHERE state ='".$state."' AND Country ='".$country."' AND city ='".$city."' OR zipcode ='".$zipcode."'AND item ='".$item."' LIMIT $s,$limit"

Too many mistakes there to point 'em all out.

examples:
```
SELECT *
FROM orders
WHERE (quantity > 2 AND customer = 'Smith')
OR (quantity > 0 AND customer = 'Jones')

```

```
$sql = "SELECT * FROM postings WHERE (state = $state AND Country = $country AND city = $city) OR (zipcode = $zipcode AND item = $item) LIMIT 1";
```

---

