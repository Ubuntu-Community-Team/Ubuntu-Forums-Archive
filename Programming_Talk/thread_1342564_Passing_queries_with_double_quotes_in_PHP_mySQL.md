---
title: "Passing queries with double quotes in PHP mySQL"
date: 2009-11-30
forum: Programming Talk
---

### Post by jingleheimer76 on 2009-11-30
How can I deal with users sending varibles with double quotes (") in PHP variables that will be used to build mySQL

I would like to allow users to store double quotes in the database, but how do I do that? In the example below, if someone puts a double quote in the Name variable, I am hosed.

```

$sql="INSERT INTO Recipes (recipe_name)
VALUES (\"$_POST[Name]\")";
    
echo "<p> the query: " . $sql . "</p>";
        
if (!mysql_query($sql,$con))
  {
  die('Error: ' . mysql_error());
  }
echo "<p>1 record added to Recipe table</p> ";

```

---

### Post by -grubby on 2009-11-30
[http://php.net/manual/en/function.mysql-real-escape-string.php](http://php.net/manual/en/function.mysql-real-escape-string.php)

I'd look into that.

---

### Post by Finalfantasykid on 2009-12-01
You could also try the [ereg_replace]("http://php.net/manual/en/function.ereg-replace.php") function.  Just do something like this.

```
$newString = ereg_replace("\"", "&quot;", $_POST[Name]);
```I think that will work :/

EDIT:  Lame, I just realized that the function is depricated...

---

