---
title: "Php Form"
date: 2007-01-08
forum: Programming Talk
---

### Post by nikolaos on 2007-01-08
I have a database and when i construct the table with the values, i want an 'EDIT' and a 'REMOVE' buttons to appear next to each entry.
Here is the code.
```
while ($name_row = mysql_fetch_row($result)) {
         print("<FORM METHOD=POST ACTION=\"$self\">");
         print("<TR ALIGN=LEFT>");
         for($i=1;$i<$n;$i++)
 { print("<TD>$name_row[$i]</TD>");}
   print("<TD><INPUT TYPE=submit NAME=EDIT VALUE=$name_row[0]></TD>");
   print("<TD><INPUT TYPE=submit NAME=REMOVE VALUE=$name_row[0]></TD>");
   print("</FORM>");
   print("</TR>"); 
```

....what i am trying to do is, create a FORM so i can post the EDIT and REMOVE buttons passing the id number as a value (individually) for each entry.
The thing is that i can't figure out how to retrieve the data with $_POST['EDIT']. If the code is not totally wrong can you suggest something? Or can you give a (correct) idea on how to do it?
Thanks in advance.

---

### Post by indytim on 2007-01-08
Nikolaos,

I do things entirely different from your approach.  But anyways, looking at your code:

1.  You don't need to iterate the form open within your while statement (opening the form on each row read from your quiery).
2.  Within your program, have you supplied code to act upon if your field variables contain content ($EDIT , $REMOVE)?

ie:
[PHP]if isset($REMOVE)
{
$sq1="delete from table1 where id='$REMOVE'";
<BLAH>
}

[/PHP]

IndyTim

---

### Post by nikolaos on 2007-01-08
Hi indytim, thanks for the quick answer,

1) I want to define that each group of 'EDIT' and 'REMOVE' buttons are unique (i.e. with its own values). I though that i can distinct them by putting them on different FORMS and therefore retrieve the data easier with the $_POST[] method.
   
2)that is what i am trying to figure out, how to pass the id (which is stored in the value field) with the $_POST[] method.

i think my approach basically sucks, can you suggest a different-better approach?

---

### Post by Isoss on 2007-01-08
I am not sure what is it that you are trying to do exactly, but from what you have posted I guess what you need is to send the value of the id using <input type="hidden" name="id" value="$name_row">

I don't know why you are using fetch_row, if I were you I'd use fetch_assoc or fetch_array and then would use $name_row['id'] ...

---

### Post by nikolaos on 2007-01-08
Thanks man, i 'll give it a try and post any problems a might encounter

---

### Post by smartbei on 2007-01-08
What I would do is implement an html array. Like this:
```

<?php
if(isset($_POST['EDIT'])) {
	$key = array_keys($_POST['EDIT']);
	$key = $key[0];
	//$key now has the id of the row that you wanted to edit.
}
if(isset($_POST['REMOVE'])) {
	$key = array_keys($_POST['REMOVE']);
	$key = $key[0];
	//$key now has the id of the row that you wanted to remove.
}
echo "<FORM METHOD='post' ACTION=''><table>";
while ($name_row = mysql_fetch_row($result)) {
	print("<TR ALIGN='left'>");
	for($i=1;$i<$n;$i++)
		print("<TD>$name_row[$i]</TD>");
	print("<TD><INPUT TYPE='submit' NAME='EDIT[{$name_row[0]}]' VALUE='EDIT' /></TD>\n");
	print("<TD><INPUT TYPE='submit' NAME='REMOVE[{$name_row[0]}]' VALUE='REMOVE' /></TD>\n");
	print("</TR>");
}
echo "</table>";
echo "</FORM>";
?>

```
Or, you could indeed make them seperate forms and use a hidden field to hold the id.

Just by the way - it is generally recommended to surround attribute values with quotes (" or ') in HTML 4.01 (which this looks like) (I did this in my example).

---

