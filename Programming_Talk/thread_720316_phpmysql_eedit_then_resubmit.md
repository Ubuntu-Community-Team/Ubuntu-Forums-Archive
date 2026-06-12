---
title: "php/mysql eedit then resubmit"
date: 2008-03-10
forum: Programming Talk
---

### Post by patty522 on 2008-03-10
hey guys/gals i have been messing around with some mysql/php while out of work. Cant stand any more day time tv ARHHH. i need some fresh eyes to look at this.

What it does - it pulls records from mysql and make each record a link. if you click the link it allows you to edit that record then you can sumit it to mysql to replace the old record.
Problem - it doesnt submit the record or it does'nt update.

any help would be good.

<?php include 'connect.php'; ?>
<?php

if(!isset($cmd))
{
//display all the questions
$result = mysql_query("select * from question order by ID");

while($r=mysql_fetch_array($result))
{
//grab the name and the ID of the question
$name=$r["name"];
$ID=$r["ID"];

//make the name a link
echo "<a href='edit.php?cmd=edit&ID=$ID'>$name - Edit</a>";
echo "<br>";
}
}
?>
<?
if($_GET["cmd"]=="edit" || $_POST["cmd"]=="edit")
{
if (!isset($_POST["submit"]))
{
$ID = $_GET["ID"];
$sql = "SELECT * FROM question WHERE ID=$ID";
$result = mysql_query($sql);
$myrow = mysql_fetch_array($result);
?>

<form action="edit.php" method="post">
<input type=hIDden name="ID" value="<?php echo $myrow["ID"] ?>">

name:<INPUT TYPE="TEXT" NAME="name" VALUE="<?php echo $myrow["name"] ?>" SIZE=30><br>
question:<TEXTAREA NAME="question" ROWS=10 COLS=30><? echo $myrow["question"] ?></TEXTAREA><br>
date:<INPUT TYPE="TEXT" NAME="date" VALUE="<?php echo $myrow["date"] ?>" SIZE=30><br>

<input type="hIDden" name="cmd" value="edit">

<input type="submit" name="submit" value="submit">

</form>

<? } ?>
<? //put the edited stuff back on the server
if ($_POST["$submit"])
{
$name = $_POST["name"];
$question = $_POST["question"];
$date = $_POST["date"];

$sql = "UPDATE question SET name='$name',question='$question',date='$date' WHERE ID=$ID";
$result = mysql_query($sql);
echo "Thank you! Information updated.";
}
}
?>

cheers

---

### Post by bmeyer on 2008-03-12
Try doing some basic troubleshooting to narrow down the issue.

Try replacing the submit section with the following.  If the TEST heading shows up on the page, you know the form is properly being submitted.  If it does not, than the issue has something to do with the form handling.  The mysql_error call will display SQL error information if your update statement is malformed (make sure to change the $CONNECTION variable name to whatever you named your connection in connect.php).

I also changed the first if statement -- using isset() is a better practice:
[PHP]<? //put the edited stuff back on the server
if (isset($_POST["$submit"]))
{
echo '<h1>TEST</h1>';

$name = $_POST["name"];
$question = $_POST["question"];
$date = $_POST["date"];

$sql = "UPDATE question SET name='$name',question='$question',date='$date' WHERE ID=$ID";
$result = mysql_query($sql);

echo mysql_error($CONNECTION);

echo "Thank you! Information updated.";
}
}
?>[/PHP]

---

