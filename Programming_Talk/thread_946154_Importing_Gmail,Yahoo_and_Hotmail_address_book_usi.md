---
title: "Importing Gmail,Yahoo and Hotmail address book using PHP 5"
date: 2008-10-13
forum: Programming Talk
---

### Post by ivikas on 2008-10-13
Hello all,

           Can anybody tell me how to import gmail,yahoo and hotmail address book using PHP 5 as i need it to do a social network site.Any help will be highly appreciated.

Thanks in advance

---

### Post by Reiger on 2008-10-13
These email services can (all) export their addressbook as a CSV file. (List of rows of comma-separated-values). The Gmail service gives you (or rather your clients) help on how to do that, I suggest displaying the same step by step help in your upload form. ;)

using:
[php]
/*
Pre process the data by dissolving each line into an array of its values;
Strip delimiting quotes, if any.
*/
$parsedData=array();
$toParse = file($uploaded_a_book);
foreach($toParse as $k => $sentence) {
$parsed=explode(",",$sentence);
foreach($parsed as $n=>$p)
  $parsed[$n]=trim(preg_replace('/("|\')(.*)("|\')/','$2',$p));
$parsedData[$k]=$parsed;
}
/*
Process the data by querying the array using the (all numeric) keys to refer to data-items, in order.
*/
[/php]

---

