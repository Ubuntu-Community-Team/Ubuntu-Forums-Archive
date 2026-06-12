---
title: "php and sql"
date: 2006-10-12
forum: Programming Talk
---

### Post by darth_vector on 2006-10-12
i am having a weird issue with php and sql (using oracle). i am saving a persons username using the $_SESSION array then trying to use that value to retrieve data from the database, as in```
//setup for db
if($connect,...){
  $stmt=oci_parse($connect,"select * from something s where s.name=:name");
  $name=$_SESSION['name'];
  oci_bind_by_name($stmt,":name",$name);
  //execute and display code
}
```
the weird thing is that if i print $name i get exactly the expected username, but the query doesn't work unless i put the (same) name in manually, as in:```
//setup for db
if($connect,...){
  $stmt=oci_parse($connect,"select * from something s where s.name=:name");
  **$name="my name";**
  oci_bind_by_name($stmt,":name",$name);
  //execute and display code
}
```

i have been on this for hours; any help would be great!

---

### Post by redbull_monsta on 2006-10-12
try 

$name=$_SESSION[[COLOR="red"]"[/COLOR]name[COLOR="red"]"[/COLOR]];

---

### Post by darth_vector on 2006-10-12
thanks, but that didn't work...

not a huge fan of php i must say :-k

---

### Post by ohgod on 2006-10-13
The kinds of quotes you use (' vs ") shouldn't matter, I believe.

I had a strange problem once where I had a session var $_SESSION["username"] and a local var $username.  Apparently, there's a feature of PHP that links local vars to session vars of the same name (when I changed the local $username var, $_SESSION["username"] changed as well).  It took me a while to figure this one out.

So, this might not help, but could you try using a different local variable?  (like $name2 or something)

---

### Post by darth_vector on 2006-10-15
Thanks for the tip, I tried it, but it didn't work. I have also tried passing the username straight into the bind statement like this```
oci_bind_by_name($stmt,":name",$_SESSION["username"]);
```and a million variations on everything discussed so far.

---

