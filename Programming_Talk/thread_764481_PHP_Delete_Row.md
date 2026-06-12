---
title: "PHP Delete Row"
date: 2008-04-23
forum: Programming Talk
---

### Post by Squizz on 2008-04-23
Hi there,

I seem to be having a bit of difficulty deleting a row.

Basically, this is supposed to print out all of the records with an edit and a delete button next to each record.

The update works just find, but the delete button gives the success message and no error.  I tried putting in an 'or die' line, but that gave no errors either. 

As far as I can see, I haven't made a simple mistake, although I'm sure there's a better way to do this than using two if statements.

Can anybody point me in the right direction please?


[php]
<?php include("include/connect.php"); ?>
<?php include("editdeleteall.php"); ?>
<b>Edit/Delete List of Authors</b><br />
<table>
<tr>
<td>ID</td><td>Name</td></tr>
<?php
$author_name = $_POST['author_name'];
$author_id = $_POST['author_id'];

if ($_POST['update']){
$query = mysql_query("UPDATE Author SET author_id='$author_id', author_name='$author_name' WHERE author_id='$author_id'");
$query;
echo "Database Updated Successfully";
}
if ($_POST['delete']) {
$query2 = mysql_query("DELETE FROM Author WHERE author_id='$author_id'");
$query2;
echo "Record Deleted Successfully";
}

$result = mysql_query("SELECT * FROM Author");

while ($cell = mysql_fetch_array($result)) {

printf("<td><form action=\"edauthor.php\" method=\"post\"><textarea name=\"author_id\">%s</textarea></td><td><textarea name=\"author_name\">%s</textarea></td><td><input name=\"update\" type=\"submit\" value=\"Edit\" /></form></td><td><form action=\"edauthor.php\" method=\"post\"><input name=\"delete\" type=\"submit\" value=\"Delete\" /></form></td>", $cell["author_id"], $cell["author_name"]);


printf("</tr><tr>");
}


?>
</table>
[/php]

---

### Post by mssever on 2008-04-23
> **Squizz said:**
> [php]if ($_POST['delete']) {
$query2 = mysql_query("DELETE FROM Author WHERE author_id='$author_id'");
$query2;
echo "Record Deleted Successfully";
}[/php]

First, you don't need to put $query2 a second time; it doesn't do anything. Do [php]echo mysql_error();[/php] to get any error messages from the last query. You'll probably find something interesting there. echoing $query2 might also prove insightful.

---

### Post by Squizz on 2008-04-24
> **mssever said:**
> First, you don't need to put $query2 a second time; it doesn't do anything. Do [php]echo mysql_error();[/php] to get any error messages from the last query. You'll probably find something interesting there. echoing $query2 might also prove insightful.

Neither of them produce any output, it just gives the successful message and leaves the row in the table....

---

### Post by mssever on 2008-04-24
> **Squizz said:**
> Neither of them produce any output, it just gives the successful message and leaves the row in the table....

I misspoke. I meant to suggest that you echo your SQL string. E.g., [php]$query_string = "DELETE FROM Author WHERE author_id='$author_id'";
echo $query_string;
$success = mysql_query($query_string);
if($success) echo "Success.";
else die(mysql_error());[/php]Note that your code will print a success message no matter what happens, because you don't test your query before printing your success message.

EDIT: You also really need to indent your code properly. It's much easier to read that way.

---

### Post by Squizz on 2008-04-24
DELETE FROM Author WHERE author_name=''Success.

I got the above message, but the record is still there and refusing to move!

---

### Post by mssever on 2008-04-24
> **Squizz said:**
> DELETE FROM Author WHERE author_name=''

Don't you see the problem? Is author_name really supposed to be ''? Isn't author_name supposed to have a value?

---

### Post by Squizz on 2008-04-29
got it, ty matey ;)

---

