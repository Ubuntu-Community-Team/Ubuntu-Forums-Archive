---
title: "PHP Help"
date: 2008-05-14
forum: Programming Talk
---

### Post by jquickuk on 2008-05-14
hi all.

i have some code that looks easy enough but it isn't working please help.

the code is


```
<?

include 'dbconnect1.php';



$sql="INSERT INTO users (FullName, Username, Password, Group)
VALUES
('$_POST[FullName]','$_POST[Username]','$_POST[Password]','$_POST[Group])";

if (!mysql_query($sql))
  {
  die('Error: ' . mysql_error());
  }
echo "user added";


?>
```

but it brings up the error

Error: You have an error in your SQL syntax near 'Group) VALUES ('Bonny Ramsay','BRAM','123434','3)' at line 1

any ideas why it isnt working?

The database has the follwing fields

FullName
Username
Password
Group

Thanks in advance

---

### Post by LaRoza on 2008-05-14
You are missing the closing quote around: $_POST[Group]

---

### Post by jquickuk on 2008-05-14
No didnt work same error message

---

### Post by dwhitney67 on 2008-05-14
I'm a little new to PHP programming, thus my only experience is what I have learned from "PHP, MySQL, and Apache" (3rd Edition).

Here's a sample INSERT statement from the book; notice how it differs from your statement.  Could that be the problem?

[PHP]
// connect to the database
$mysqli = mysqli_connect( "localhost", "userID", "password", "myDB" );

...

// add to master_name table
$add_master_sql = "INSERT INTO master_name (date_added, date_modified, f_name, l_name)
                   VALUES (now(), now(), '".$_POST["f_name"]."', '".$_POST["l_name"]."')";
$add_master_req = mysqli_query( $mysqli, $add_master_sql )
                  or die( mysqli_error( $mysqli ) );[/PHP]

---

### Post by LaRoza on 2008-05-14
> **jquickuk said:**
> No didnt work same error message

Are you checking the values being sent? I am rusty on using MySQL. Test the SQL first with MySQL. If it works, it is the values that are causing the errors. You are passing $_POST variables directly do a database. You should never do that unless you don't mind getting errors and wiping the database.

---

### Post by LaRoza on 2008-05-14
> **dwhitney67 said:**
> I'm a little new to PHP programming, thus my only experience is what I have learned from "PHP, MySQL, and Apache" (3rd Edition).

Here's a sample INSERT statement from the book; notice how it differs from your statement.  Could that be the problem?


Those are newer MySQL functions. This is where PHP has issues; it has thousands of functions in the global namespace.

---

### Post by jquickuk on 2008-05-14
hmmm im completly new toall this.

I think i have posted it first. Here is the full code

```

<?



include 'dbconnect1.php';


 if ($_SERVER['REQUEST_METHOD'] == "POST") 
    {
        # escape data and set variables
     
        $FullName = addslashes($_POST["FullName"]);
		$Username = addslashes($_POST["Username"]);
		$Password = addslashes($_POST["Password"]);
		$Group = addslashes($_POST["Group"]);


$sql  = " INSERT INTO users ";
$sql .= " (FullName, Username, Password, Group ) VALUES "; 
sql .= "( '$FullName', '$Username', '$Password', '$Group' )";



       //execute SQL statement
        $result = mysql_query($sql);

        //check for error
        if (mysql_error()) { print "Database ERROR: " . mysql_error(); }

print "<h3>user Added</h3> ";
}


?>	




```

---

### Post by dwhitney67 on 2008-05-14
> **LaRoza said:**
> Those are newer MySQL functions. This is where PHP has issues; it has thousands of functions in the global namespace.

Probably so!  Nevertheless, the PHP code I provided earlier works like a charm under Ubuntu 7.04.

---

### Post by Sportingfan on 2008-05-14
This code seems perfect. Only mistake i see is a missing $-sign at the third $sql string. But that's probably a typo?!

Please give an example input on which the error shows. What types of sql fields are you using for fullname, username, password and group?

---

### Post by rickh57 on 2008-05-14
One potential issue that I see is that you have a column named "group". That is a reserved word in MySQL, so that may cause problems. You should rename it to "groupname" or something so that you aren't using a reserved word.

[MySQL Reserved Words]("http://dev.mysql.com/doc/mysqld-version-reference/en/mysqld-version-reference-reservedwords-5-0.html")

---

### Post by bloeper on 2008-05-14
Renaming of group isn't necessarily...

i think you can do it like this:

[php]
<?



include 'dbconnect1.php';


 if ($_SERVER['REQUEST_METHOD'] == "POST") 
    {
        # escape data and set variables
     
        $FullName = addslashes($_POST["FullName"]);
		$Username = addslashes($_POST["Username"]);
		$Password = addslashes($_POST["Password"]);
		$Group = addslashes($_POST["Group"]);


$sql  = " INSERT INTO users ";
$sql .= " (`FullName`, `Username`, `Password`, `Group` ) VALUES "; 
sql .= "( '$FullName', '$Username', '$Password', '$Group' )";



       //execute SQL statement
        $result = mysql_query($sql);

        //check for error
        if (mysql_error()) { print "Database ERROR: " . mysql_error(); }

print "<h3>user Added</h3> ";
}


?>
[/php] 

By adding ` to the names.. it gives mysql the command to read it as column name and not as an command...

(atleast at my knowing, correct me if i'm wrong)

---

### Post by rickh57 on 2008-05-14
That will work, too, but as a database developer, I know from experience that using reserved words just causes confusion. For my own coding, I never use them for column names.

---

### Post by bloeper on 2008-05-15
Depends on when you do it, if you work in a project with multiple people you can better don't used reserved words.
If you work for an project on you're own there's nothing to it, because you know why you did it.

---

### Post by Soulsmith on 2008-05-15
I think rickh57 might have something there, also you're missing a semi-colon at the end of your query before the closing quote and php line terminator

---

