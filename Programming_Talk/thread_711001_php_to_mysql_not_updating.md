---
title: "php to mysql not updating"
date: 2008-02-29
forum: Programming Talk
---

### Post by Squizz on 2008-02-29
Hi there, I'm trying to learn a bit of php, and can't figure out why the script isn't updating the db.  The echo isn't showing at the end either.  I have a feeling I've missed something obvious, so if anyone could spot it then that would be grand!  It gets the data from the db and displays it properly, then gives me the option of editing it, but if I press submit it just loops without updating.

[php]
<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html  xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Edit Content</title>
<meta http-equiv="Content-Type" content="text/html;charset=utf-8" />
</head>
<body>
<?php include("../include/cmsconnect.php"); ?>
<?php
if(!isset($cmd)) 
{
   $result = mysql_query("SELECT * FROM content ORDER BY id"); 
   while($r=mysql_fetch_array($result)) 
   { 
      $title=$r["title"];
      $id=$r["id"];    
      echo "<p><a href='edit.php?cmd=edit&amp;id=$id'>$title - Edit</a></p>";
      echo "<p></p>";
    }
}
?>

<?
if($_GET["cmd"]=="edit" || $_POST["cmd"]=="edit")
{
   if (!isset($_POST["submit"]))
   {
      $id = $_GET["id"];
      $sql = "SELECT * FROM content WHERE id=$id";
      $result = mysql_query($sql);        
      $row = mysql_fetch_array($result);
      ?>
	  
      <form action="edit.php" method="post">
      <input type=hidden name="id" value="<?php echo $row["id"] ?>">
   
      User:<INPUT TYPE="TEXT" NAME="user" VALUE="<?php echo $row["user"] ?>" SIZE=30><br>
      Title:<INPUT TYPE="TEXT" NAME="title" VALUE="<?php echo $row["title"] ?>" SIZE=30><br>
      Category:<INPUT TYPE="TEXT" NAME="cat" VALUE="<?php echo $row["cat"] ?>" SIZE=30><br>
      content:<TEXTAREA NAME="content" ROWS=10 COLS=30><?php echo $row["content"] ?></TEXTAREA><br>
   
      <input type="hidden" name="cmd" value="edit">
   
      <input type="submit" name="submit" value="submit">
   
      </form>

   
<?
   if ($_POST["$submit"])
   {
      $user = $_POST["user"];
      $title = $_POST["title"];
      $cat = $_POST["cat"];
      $content = $_POST["content"];


      $sql = "UPDATE content SET user='$user',title='$title',cat='$cat',content='$content' WHERE id='$id'";

      $result = mysql_query($sql);
      echo "Thank you! Information updated.";
   }
}
}
?>
</body>
</html>
[/php]

---

### Post by cb951303 on 2008-02-29
you should lock the table before you do the update so that when more than one people tries to update, there is no collision

```

 $sql = "LOCK TABLES content; UPDATE content SET user='$user',title='$title',cat='$cat',content='$content' WHERE id='$id; UNLOCK TABLES'";

```

---

### Post by Squizz on 2008-02-29
Useful to know, but for now I'm more concerned about getting it to work!

I've amended it so the table is locked now though, but still the edit isn't sticking.

---

### Post by cb951303 on 2008-02-29
Ok, your $id variable is never defined in the scope of third if. You need the define it there. or better move $id = $_GET["id"];
 line to the scope of first if.

also there should be a if-else statemnt there not if-if ;)

EDIT: I'm not sure what your code tries to do but at least "update" should work this way

```

<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Edit Content</title>
<meta http-equiv="Content-Type" content="text/html;charset=utf-8" />
</head>
<body>
<?php
	if(!isset($cmd)) 
	{
		$result = mysql_query("SELECT * FROM content ORDER BY id"); 
		while($r=mysql_fetch_array($result)) 
		{ 
			$title=$r["title"];
			$id=$r["id"]; 
			echo "<p><a href='edit.php?cmd=edit&amp;id=$id'>$title - Edit</a></p>";
			echo "<p></p>";
		}
	}

	if($_GET["cmd"]=="edit" || $_POST["cmd"]=="edit")
	{
		$id = $_GET["id"];
		
		if (!isset($_POST["submit"]))
		{
			$sql = "SELECT * FROM content WHERE id=$id";
			$result = mysql_query($sql); 
			$row = mysql_fetch_array($result); ?>

<form action="edit.php" method="post">
<input type=hidden name="id" value="<?php echo $row["id"] ?>">

User:<INPUT TYPE="TEXT" NAME="user" VALUE="<?php echo $row["user"] ?>" SIZE=30><br>
Title:<INPUT TYPE="TEXT" NAME="title" VALUE="<?php echo $row["title"] ?>" SIZE=30><br>
Category:<INPUT TYPE="TEXT" NAME="cat" VALUE="<?php echo $row["cat"] ?>" SIZE=30><br>
content:<TEXTAREA NAME="content" ROWS=10 COLS=30><?php echo $row["content"] ?></TEXTAREA><br>

<input type="hidden" name="cmd" value="edit">
<input type="submit" name="submit" value="submit">
</form>
	<?                 }
		else
		{
			$user = $_POST["user"];
			$title = $_POST["title"];
			$cat = $_POST["cat"];
			$content = $_POST["content"];

			$sql = "LOCK TABLES content; UPDATE content SET user='$user',title='$title',cat='$cat',content='$content' WHERE id='$id', UNLOCK TABLES";

			$result = mysql_query($sql);
			echo "Thank you! Information updated.";
		}
	}
?>

</body>
</html> 

```

EDIT2: Always clean the strings that you get from user before you query mysql. google for mysql_real_escape_string() ;)

---

### Post by mssever on 2008-02-29
Stripping your code to just the if statements and indenting it correctly reveals this:
[php]<?
if(!isset($cmd)) 
{
   //stuff here
}
?>
<?
if($_GET["cmd"]=="edit" || $_POST["cmd"]=="edit")
{
   if (!isset($_POST["submit"]))
   {
      //stuff here
      if ($_POST["$submit"])
      {
         //your update is here
      }
   }
}[/php]So you can see that your if($_POST["submit"]) will alwaus be false. But you called $_POST["$submit"], which probbly isn't what you want.

---

### Post by Squizz on 2008-03-01
Thanks very much for your help guys, will rewrite my code on monday!

---

