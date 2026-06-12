---
title: "PHP- Best Way To Build Dynamic Query"
date: 2008-12-27
forum: Programming Talk
---

### Post by s.fox on 2008-12-27
Hi,

I have written some php that builds a dynamic query by comparing every word in a string to several different database fields.   The string can be any length.   This script does work and produces the correct SQL but I wondered if it was the 'best' way of doing it.  Any comments would be appreciated.

[php]<?php
#get text string
$text = "This is some text";
#find out how many words are in the string
$count = count(explode(" ", $text));
#remove one because loop plays up later otherwise.
$count = $count -1;
#explode the string into an array
$part=explode(" ", $text);
#start of sql
$startSQL = 'select * from table WHERE ';

#build dynamic sql and compare every word in the original string to several different fields
for ( $counter = 0; $counter <= $count; $counter += 1) {
    $loopingSQL .= "field1  LIKE ".'"%'."$part[$counter]".'%"'." OR ";
    $loopingSQL .= "field2  LIKE ".'"%'."$part[$counter]".'%"'." OR ";
    $loopingSQL .= "field3  LIKE ".'"%'."$part[$counter]".'%"'." OR ";
}
#tidy up the end of the looping sql by removing the last OR from the end of the string
$loopingSQL = substr_replace($loopingSQL ,"",-3);
#concatenate $startSQL with $loopingSQL 
$completeSQL = $startSQL.$loopingSQL;
#echo out finished sql
echo $completeSQL;
?>[/php]

---

### Post by Dr Small on 2008-12-27
That's actually a very interesting concept. I should try something like that for a search query.

---

### Post by s.fox on 2008-12-27
I thought maybe some people would use an array to do this sort of thing.    When I am done with this search function I am going to make a little more complex by using it with ajax so the end user doesn't have to click submit all the time. 

Before I do that however I need to filter out certain words such as "a" and "the".   I could do a string replace at the beginning of the script but again I am not sure if its the best way of handling the problem.

---

### Post by Reiger on 2008-12-27
> **Ash R said:**
> Hi,

I have written some php that builds a dynamic query by comparing every word in a string to several different database fields.   The string can be any length.   This script does work and produces the correct SQL but I wondered if it was the 'best' way of doing it.  Any comments would be appreciated.

[php]<?php
#find out how many words are in the string
$count = count(explode(" ", $text));
#remove one because loop plays up later otherwise.
$count = $count -1;
[/php][php]
#build dynamic sql and compare every word in the original string to several different fields
for ( $counter = 0; $counter <= $count; $counter += 1) {
    $loopingSQL .= "field1  LIKE ".'"%'."$part[$counter]".'%"'." OR ";
    $loopingSQL .= "field2  LIKE ".'"%'."$part[$counter]".'%"'." OR ";
    $loopingSQL .= "field3  LIKE ".'"%'."$part[$counter]".'%"'." OR ";
}
[/php]

You could generalize this further (saves the expensive count() call too):

[php]
$num_fields = 3; // app/db logic known to programmer beforehand...
$base = 1; // app/db logic: a 0-based or 1-based indexed array of fields?
foreach($fieldNum=$base;$fieldNum<($base+$num_fields),$fieldNum++)
 foreach($part as $counter=> $value)
     $loopingSQL.="field$fieldNum  LIKE \"%$value%\" OR ";
[/php]

EDIT: An interesting variation to the theme I personally use for XPATH queries is to use the $k=>$v pairs of PHP arrays for some runtime magic:
[PHP]
/*
        Compile parametrised xpath query strings; by using a keyed $xpath_args array to provide substitutes for variable content.
        */
        function compileXPATHQuery($xpath_args) {
                $query=array(
                'download'=>'/trace/download[id/text() = \'$id\' or name/text() = \'$name\']',
                'insert'=>'/trace',
                'base_id'=>'/trace/@count',
                'find_count'=>'/trace/download[count/text() = \'$count\']',
                'find_date'=>'/trace/download[date/text() = \'$date\']',
                'find_url'=>'/trace/download[url/text() = \'$url\']'
                );
                
                foreach(array('key','id','name','count','date','url') as $var)
                        eval("\$$var = isset(\$xpath_args['$var']) ? \$xpath_args['$var'] : -1;");
                
                if($key != -1)
                        eval('$query="'.$query[$key].'";');
                else
                        $query=false;
                
                return $query;
        }
[/PHP]

---

### Post by s.fox on 2008-12-27
> **Reiger said:**
> You could generalize this further (saves the expensive count() call too):

[php]
$num_fields = 3; // app/db logic known to programmer beforehand...
$base = 1; // app/db logic: a 0-based or 1-based indexed array of fields?
foreach($fieldNum=$base;$fieldNum<($base+$num_fields),$fieldNum++)
 foreach($part as $counter=> $value)
     $loopingSQL.="field$fieldNum  LIKE \"%$value%\" OR ";
[/php]

Not a bad idea, thanks.    Unfortunately I can't use the first loop because the fields aren't called field1-3.   Second loop is viable though.

Incidently by expensive do you mean in terms of memory use?

Once again,  thanks for your thoughts

EDIT:  I have never used XPATH before.  Time for a little read methinks :)  

Thanks

---

### Post by Reiger on 2008-12-27
> **Ash R said:**
> Not a bad idea, thanks.    Unfortunately I can't use the first loop because the fields aren't called field1-3.   Second loop is viable though.

Ah well, you can always create an array of field names:
foreach(array(/*insert names*/) as $fieldName). And then replace the "field$fieldNum" bit with "$fieldName". ;)

> Incidently by expensive do you mean in terms of memory use?

No, not really. (unless it is both recursively implemented and you're traversing a *very* large array; in which case you may smash the stack) Given the capabilities of a PHP array I would assume that it is based on a recursive data structure like a B+ Tree, though.\

Anyways: what I meant is that counting all items in an array sounds suspiciously resource-consuming (a large array is a large amount of wasted clock cycles if you can avoid it) to me; I try to avoid those functions as much as possible -- and if I know I'll be traversing the exact same array just a milisecond later on, the foreach() syntax let's me do that.

---

### Post by s.fox on 2008-12-27
> **Reiger said:**
> 
No, not really. (unless it is both recursively implemented and you're traversing a *very* large array; in which case you may smash the stack) Given the capabilities of a PHP array I would assume that it is based on a recursive data structure like a B+ Tree, though.\

Anyways: what I meant is that counting all items in an array sounds suspiciously resource-consuming (a large array is a large amount of wasted clock cycles if you can avoid it) to me; I try to avoid those functions as much as possible -- and if I know I'll be traversing the exact same array just a milisecond later on, the foreach() syntax let's me do that.

Thanks for clearing that up for me.   Much appreciated.

Can anyone think of a better way to exclude certain words from the search?  The only ways I can think of is string replace or some sort of array, although the array may make things overly complicated.

Many thanks.

---

