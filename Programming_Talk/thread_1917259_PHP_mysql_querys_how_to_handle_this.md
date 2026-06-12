---
title: "PHP mysql querys how to handle this?"
date: 2012-01-29
forum: Programming Talk
---

### Post by hockey97 on 2012-01-29
How can you in php/ mysql  have one query but have the where clause to have the values optional.

The where clauses  would say select all data where country is US, state is Florida and city is orlando. 

I want those to be optional. So, the only thing you need is just the country.

If I put where country is U.S then it should grab all items in the U.S

that is all that is needed...however, if the client is looking for local area type of items. Then they will have to select the state and city.

I then need to extend that where clause to where  country is U.S and state is Florida and city is Miami. I could use City or zip code. 

How, can I create a query where the where clause would use country as the only value needed. If state and city are passed then would add them.

if just country and state are passed then the user will look for a statewide search on items. 


I need to know how to construct the query so that all the query needs to work is the country. Yet, at the same time allow users to give more specific searches or querying. So the where clause should be extended. So if we add state and city but the client dosen't pass such values then I don't want the query to break. 

any ideas?

---

### Post by rlwpub on 2012-01-30
Build the query string with if($country != "") if($state != "") etc.. And use .= to keep adding additional parts to the query string as needed.

If you add the WHERE clause to the initial string you can set a check variable to let you no if you added anything after it, and if not, then strip off the " WHERE" from the end of the query string.

---

### Post by dazman19 on 2012-01-30
The Short answer is to have PHP construct your query.

Longer answer (if you are a bit more advanced at PHP) : Consider using objects, then you can write validation member functions to check if the SQL is valid before firing it down to the database, have it throw an error if it is not.. 

Heres some simple code for the short answer. 

[PHP]

$whereBits = "";

if($restrictOnColumn2 == true)
{
    $wherebits.=" WHERE `column2` LIKE '{$someVar}'";
}

$query = "SELECT `column1` FROM `table` {$whereBits}";

$resource = mysql_query($query);

while($resultLine = mysql_fetch_assoc($resource))
{
//do something
}
[/PHP]

In this case if you want to select column1 (with no restrictions) the query will still be successful.

---

