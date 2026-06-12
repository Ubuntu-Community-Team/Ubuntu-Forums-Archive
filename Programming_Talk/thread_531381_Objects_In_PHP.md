---
title: "Objects In PHP"
date: 2007-08-21
forum: Programming Talk
---

### Post by playing_with_matches on 2007-08-21
Hey guys.  Im trying to teach myself PHP, and I was able to get Drop Down Lists populated through a database with help from: [http://ubuntuforums.org/showthread.php?t=528251](http://ubuntuforums.org/showthread.php?t=528251) .  However, now I am trying to get them populated in a similar fashion, only this time using objects (i've spent a long time trying to get this to work... to no avail)

Now I'm familar with oop in other languages (C++, JAVA), but for some reason this is not making sense.  Could anyone explain why it's not working? (the drop down menu doesn't have any entries in it at all).  

code for the class:

```

<?php
class getstuff {

  var $host = "test";
  var $user = "test";
  var $pass = "test";
  var $db = "test";
  var $mysqli="";
 
 public function getstuff() {
  
 }  
 
 public function populate_systems() {
  
   $mysqli = new mysqli($host, $user, $pass, $db);
   if (mysqli_connect_errno()) {
     die("Unable to connect!");
   }
  
   $query="CALL sp_systemlist()";  //NOTE: I know this works.  as it works great when I don't try to use objects
   $result= $mysqli->query($query);
   return $result;
 }  //END populate_systems() 
}   
?>

```

and the calling form:
```

<html>
<body>
<p>
  <?php 
    require_once "getstuff.php";
    $getstuff=new getstuff();
  
?> 
</p>
<p>
  <label>
  <select name="systems" >
      <?php
        $result = $getstuff->populate_systems();
	    while($row = $result->fetch_object()) 
	    { 
	  ?>
	    <option value="<?php echo $row->systems_name;  ?>"> <?php echo $row->systems_name; ?></option>
					 
      <?php
	  }
	 ?>    
  </select>
 
  </label>
  
</p>
</body>
</html>

```

Anyone know what the problem is?  Thank you!

---

### Post by playing_with_matches on 2007-08-22
I guess a better question would be: is it even possible?

---

### Post by playing_with_matches on 2007-08-22
Ok, for anyone who was curious or runs into a similar problem.  In order to use the variables in the class, you need to use:

$this->variablename;

So, here's an example:

```

class car {

  var $color;
  
  public function car() {  //constructor
   
    $this->color="red";  

  }
}

```
Hope that helps anyone stuck on what I was.

---

### Post by LaRoza on 2007-08-22
> **playing_with_matches said:**
> Ok, for anyone who was curious or runs into a similar problem.  In order to use the variables in the class, you need to use:

$this->variablename;

```

    $this->color="red";  

```


I have used PHP4 mostly, thanks for the incentive to learn the OO aspects of PHP.

By the way, the $this variable (or pointer) is common when accessing member data, it is in C++, Python (as "self"), and Java.

---

