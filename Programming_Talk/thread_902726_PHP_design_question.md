---
title: "PHP design question"
date: 2008-08-27
forum: Programming Talk
---

### Post by tc101 on 2008-08-27
What is the best design for a simple online update of a database in PHP?  

This is what I am thinking of doing, but there may be a much better way:

menu.php just has 3 links to 3 other pages: insert.php, update.php, delete.php

insert.php has an html form that lets the user enter all data, then it goes to write.php

update.php has an html form that accepts the record id, then goes to update2.php which reads that record, uses it to fill in the fields in and html form that the user can change, then goes to write.php

delete.php has an html form that lets the user enter the id of the record to be deleted and goes to write.php

write.php connects to the database and according to a switch set from the sending page, either inserts, updates or deletes the record.

I know this will work, but it involves 6 pages and I wonder if there is a better simpler solution that I am not thinking of.

---

### Post by mssever on 2008-08-27
Consider using a PHP framework. CodeIgniter has great documentation, so it's my preferred PHP framework. By using the framework, you'll learn good designs which don't involve mixing PHP and HTML as newbies usually do.

---

### Post by Reiger on 2008-08-27
Well it seems that a Framework is as of yet a bit over the OP's head.

To answer you question: why would you spend 3 scripts to handle DB interaction; instead of one to handle all of it + front-ends that handle the HTML -> PHP -> HTML side?

Generic DB script:
[php]
<?php
function delete([args]) {
/* code */
}
function update([args]) {
/* code */
}
function insert([args]) {
}
?>
[/php]

Generic form creator:
[php]
<?php
function delete_form() {
}
function insert_form() {
}
function update_form() {
}
switch($_GET['do']) { /* determine what to do */
case 'insert' : insert_form();
... 
}
?>
[/php]

Generic form handler:
[php]
<?php
require('my_db_script.php');

$args=array(); 
/* make copy which we can modify without losing the original */
foreach($POST as $k => $v);
  $args[$k]=$v;

switch($_GET['do']) { /* determine what to do */
case 'insert' : instert($args);
...
}
?>
[/php]

EDIT: Note how I assume you'll be using the $_GET superglobal to specify *what behaviour you get*; and $_POST for the required params.

---

### Post by tc101 on 2008-08-27
Reiger, thanks for taking the time to type in that sample code.  Now that you've shown me, it all seems obvious.

mssever, thanks for the suggestion on codeigniter.  I will be looking into that.

---

### Post by abhinav420420 on 2008-08-28
codeigniter is a much better option than writing 6-7 pages for the same purpose

---

### Post by Mickeysofine1972 on 2008-08-28
I have to agree with the last couple of suggestions as I use Code Igniter professionally and its a absolute life saver and very easy to learn too.

check out one of my current projects done with CI at [http://northland.king-design.co.uk](http://northland.king-design.co.uk)


Mike

---

### Post by Griff on 2008-08-28
Hrm.  Maybe I read through this too quickly, but a simple conditional may be able to solve your multiple page problem as well.  Let's say you have a variable $name you get from a form and would like to process that name on the same page.
```

<?php

  $name=htmlentities($_GET["name"]);

  if ($name='') {
    echo ('
      <FORM action="this_page.php" method="GET" />
        <LABEL>Name: <input type="text" name="name" id="name"> </LABEL> <BR>
        <input type="submit" value="Go!" />
      </FORM>');

  }

  else {
    //process $name on the same page!
  }

?>

```

---

### Post by mssever on 2008-08-28
> **Griff said:**
> Hrm.  Maybe I read through this too quickly, but a simple conditional may be able to solve your multiple page problem as well.  Let's say you have a variable $name you get from a form and would like to process that name on the same page.
Be vary careful with this approach. I used that kind of design in my early projects. It scales vary poorly, and before too long, those files became increasingly difficult to manage. I occasionally have to do maintenance on those projects and it's really difficult.

It will save a lot of trouble if you separate the view from the rest of the code. That's what MVC is all about.

---

### Post by tc101 on 2008-08-30
Thanks again everyone for continuing all the useful suggestions.  I am learning a lot.

---

