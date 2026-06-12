---
title: "MySQL Error"
date: 2007-08-06
forum: Programming Talk
---

### Post by dhtseany on 2007-08-06
Hi all, got a new one. Everytime I try to insert data into mysql I get this following error:

```

Duplicate entry '' for key 2

```

The first time I try to add the info, it goes through without a problem. However, when I try to continue and add the next piece of info, the error pops up and continues to annoy me until I delete the data that went in fine the first time. Please note this is happening in both MySQL and the PHP code I first ran into this problem with.

Here is the PHP code that is generating the error:

```

<?php

include "add_cc.php";

if(isset($_POST['submit']))

{

  $firstname=$_POST['firstname'];
  $lastname=$_POST['lastname'];
  $coname=$_POST['coname'];
  
  if(strlen($firstname)<1)

  {

      print "You did not enter a URL.";

  }

  else if(strlen($lastname)<1)

  {

      print "You did not enter a button.";

  }
  else if(strlen($coname)<1)
  {
  		print "Problem with company name.";
	}
	
  else

  {

    $insertbutton=("INSERT into  user (FirstName, LastName, coname) values('$firstname','$lastname','$coname')");

    mysql_query($insertbutton) or die(mysql_error());

    print "Added information. Click <a href='add.php'>here</a> to continue.";

  }



}

else

{

    print "<form action='add.php' method='post'>";

	print "Company Name:<br>";
	
	print "<input type='text' name='coname' size='20'><br>";

    print "First Name:<br>";

    print "<input type='text' name='firstname' size='20'><br>";

    print "Last Name:<br>";

    print "<input type='text' name='lastname' size='20'><br>";

    print "<input type='submit' name='submit' value='submit'></form>";

 

}

?>

```

**Any ideas?**

Thanks,

Sean

---

### Post by Wybiral on 2007-08-06
Not sure what the problem is... But you really should not be sending information straight from $_POST to a SQL query. It's susceptible to injection.

Make it a habit of retrieving soon-to-be SQL query data with "mysql_real_escape_string"

Such as '$firstname=mysql_real_escape_string($_POST['firstname']);'

Just some friendly advice... Unprotected queries are a dangerous thing.

EDIT:

BTW, I might be able to figure the problem out if I know how the table is structured. Maybe someone else will know just from the error message, but it wouldn't hurt to post the table structure.

---

### Post by dhtseany on 2007-08-06
Thanks for responding and sorry if this is hard to read. If so, I'll try it again.

Sean
[IMG]http://www.lakecs.net/img/mysql_structure.jpg[/IMG]

---

### Post by Wybiral on 2007-08-06
I can't tell from the picture, is 'id' set as the primary key?

EDIT:

Wait... Is anything set to be unique by chance, that might be getting a duplicate on from not filling in the other columns? The other columns in the table should default to '', so if they are set to be unique then adding two users without setting them will cause a duplicate problem.

---

### Post by dhtseany on 2007-08-06
Yes, I'm 99% sure the id field is set as the primary key.

[http://www.lakecs.net/img/pic1.jpg]("http://www.lakecs.net/img/pic1.jpg")

How bout that?

---

### Post by Wybiral on 2007-08-06
How about the unique thing?

(I edited my previous post, in case you didn't see it, sorry about that).

EDIT:

Also, I've never used that site so I don't know what it all means... But since everything has a "U" next to it... Is it unique?

---

### Post by dhtseany on 2007-08-06
For the sake of reference, you made me think and I figured it out. The problem was because I had the user name field set to unique and because I was attempting to add another row without a user name specified it was seeing two rows w/o user names and assuming they were duplicates. Thanks for responding though :)

Later

Sean

---

### Post by Wybiral on 2007-08-06
Awesome (nice signature btw).

But don't forget to make those queries safe!

---

