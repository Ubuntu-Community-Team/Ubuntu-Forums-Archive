---
title: "Populating List In PHP"
date: 2007-08-17
forum: Programming Talk
---

### Post by playing_with_matches on 2007-08-17
I'm trying to learn PHP to add to my collection of languages that I know, and I am running into a problem.  I want to populate a Drop Down List with entries from a MySQL database.  When I run my code, it gives me two blank entries (it has the number of entries right in the list, but the values are blank.)  My code looks like:

```

<body>
<?php
  // set server access variables
  $host = "test";
  $user = "test";
  $pass = "test";
  $db = "test";
  $mysqli = new mysqli($host, $user, $pass, $db);
  $populate="CALL sp_systemlist()";
  
  if (mysqli_connect_errno()) {
    die("Unable to connect!");
}
?>
  
<form id="Browse" name="Browse" method="post" action="">
    <label>System
  <select name="system_name">
    <?php
	  $result = $mysqli->query($populate);
	  while($row = $result->fetch_object()) 
	  {
	    
	?>
	    <option value="<?php echo $row->systems_name;  ?>">
					 
	<?php
	  }
	  ?>    
	      
  </select>
  </label>
</form>
</body>

```

I know that the stored procedure works, and that there actually is stuff in the database.  Anyone have any ideas?

---

### Post by Mirrorball on 2007-08-17
What happens if you add this code to your page?
```

echo (int) $result; // If the output is 0, the query didn't work.
print_r($row);

```

---

### Post by Compyx on 2007-08-19
You'll need to provide some labels to go with the values, for example:
```

<option value="1">Gentoo</option>
<option value="2">Ubuntu</option>
<option value="3">Debian</option>
...

```

So either do this:
```

<option value="<?php echo $row->systems_name;  ?>"><?php echo $row->systems_name; ?></option>

```

or this:
```

<option><?php echo $row->systems_name;  ?></option>

```

Without providing a `value="..."` to the option element, the value returned by the control will be that of the label.

Hope this helps..

---

### Post by playing_with_matches on 2007-08-19
> You'll need to provide some labels to go with the values, for example:
Code:

<option value="1">Gentoo</option>
<option value="2">Ubuntu</option>
<option value="3">Debian</option>
...

So either do this:
Code:

<option value="<?php echo $row->systems_name;  ?>"><?php echo $row->systems_name; ?></option>

or this:
Code:

<option><?php echo $row->systems_name;  ?></option>

Without providing a `value="..."` to the option element, the value returned by the control will be that of the label.

Hope this helps..

Ah thank you!  This did the trick!  Thanks  a lot for the help guys, I can continue my endeavor  now!

---

