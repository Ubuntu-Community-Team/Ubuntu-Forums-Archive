---
title: "PHP/MySQL - ORDER by Date?"
date: 2008-11-27
forum: Programming Talk
---

### Post by Johnsie on 2008-11-27
Hi, Im trying to pull some data out of a table in order of date


My query is a follows:
> $tquery = "SELECT TransDate,RefNo,TransPointsAmount from $tableName WHERE Member='$thisMemberID'ORDER BY TransDate ASC";


The format of the data in the TransDate field is dd/mm/yy (UK style). When I perform my query the results are not in order. Is there any way I can get this to work by changing the query rather than changing the format of every record. 


Ps. I use phpmyadmin.  Will changing the field description  for TransDate help?

Thanks to anyone who can help

---

### Post by Johnsie on 2008-11-27
The answer to my problem was:

> 
$tquery = "SELECT TransDate,RefNo,TransPointsAmount FROM $tableName
    WHERE Member='$thisMemberID' ORDER BY STR_TO_DATE(TransDate, '%d/%m/%y') ASC"; 

---

### Post by drubin on 2008-11-27
> $tquery = "SELECT TransDate,RefNo,TransPointsAmount FROM $tableName
WHERE Member='$thisMemberID' ORDER BY STR_TO_DATE(TransDate, '%d/%m/%y') ASC"; 

Judging by this you are storing your date information in a varchar/text field. I would suggest changing this to a date/datetime/time field if you can. (If this is a realitivly new project)

This will not only speed up performance but might even decrease your db size as mysql will be able to correctly store/proccess/validate your data.

---

