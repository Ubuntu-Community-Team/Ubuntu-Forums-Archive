---
title: "Two PHP questions for the PHP gurus"
date: 2009-06-16
forum: Programming Talk
---

### Post by akvino on 2009-06-16
I am venturing into OO PHP and have some Object handling question, and form handling quesion that some of you might know the answer:

1) If I have a function that will create new object on the request - is php at any point aware that another object with the same name might be used and pass the handle by reference - or does it just replace the current object with the new one, or something else?

Here is the example code:

$myobject = new Object();
//and then again if you repeat 
$myobject = new Object();  
What will this result in?
--------------------------------------------------
2) Form question - If you have database and want to retrieve the results from one column, and put it into drop down list form - what is the best way to do it? 

I found some syntax and tried it when placing mysqli_array function into while loop and printing it on the screen, but if I want to build a form out of the values passed from the database - there has to be an easier way?

---

### Post by s.fox on 2009-06-16
Hi,

Do you mean something like this?

```

include ("db.php");
$sql = "SELECT name FROM contacts";
$result=mysql_query($sql) or die ("$sql");
while($rows=mysql_fetch_array($result)){
    $name = $rows['name'];
}

```You could then have the variable or array,  whichever you choose populate a drop down menu by echoing out equivalent HTML.  

Remember double quote  = \" and single quote = \'

Any problems please post back :)

-Ash R

---

### Post by akvino on 2009-06-16
> **Ash R said:**
> Hi,

Do you mean something like this?

```

include ("db.php");
$sql = "SELECT name FROM contacts";
$result=mysql_query($sql) or die ("$sql");
while($rows=mysql_fetch_array($result)){
    $name = $rows['name'];
}

```You could then have the variable or array,  whichever you choose populate a drop down menu by echoing out equivalent HTML.  

Remember double quote  = \" and single quote = \'

Any problems please post back :)

-Ash R


Yes that is why I used or tried in essence. Can you give me a snippet on how to populate drop down form with the array? Thanks a million.

---

### Post by s.fox on 2009-06-16
Hi,

Try something like this:
```

<?php
include ("db.php");
$query = "SELECT name FROM contacts"; 
$result= mysql_query($query) or die ("$query");                        
echo ("<select id='name' name='customer'>"); 
while($rows = mysql_fetch_array($result)){
    $name = $rows['name'];
    echo ("<option value='$name'>$name</option>");
}
echo ("</select>");
?>
```

-Ash R

---

### Post by Reiger on 2009-06-16
(1) In PHP a variable name is like an inode in a filetable: a variable does not correspond to a value, but rather to the location of a value.

This has a few consequences:
(a) You can assign multiple names to the same content using the $first = &$second syntax. (Changing $second results in the same changes being visible in $first.)
(b) Shooting yourself in the foot becomes trivial when you do raw operations on the `inode table'.


(2) The example you posted is a classic which has its own name in functional programming: destructive update. It is one of those things pure functional languages do away with, and imperative languages can't do without. What you did is allocating a variable (in some table), creating an object and associating it with the new record in the variable table. Then you orphaned the object in favour of a new object and re-associated the record in the variable table with this new record: the orphan is to be destroyed by the garbage collector whenever it decides to go and free some memory.

It is also not worth bothering with thinking about destructive update in (managed) imperative languages that feature automatic memory management: it only gives you headaches.

---

### Post by akvino on 2009-06-16
> **Ash R said:**
> Hi,

Try something like this:
```

<?php
include ("db.php");
$query = "SELECT name FROM contacts"; 
$result= mysql_query($query) or die ("$query");                        
echo ("<select id='name' name='customer'>"); 
while($rows = mysql_fetch_array($result)){
    $name = $rows['name'];
    echo ("<option value='$name'>$name</option>");
}
echo ("</select>");
?>
```

-Ash R
Yes that will do. Thanks. I'll try it out.

---

### Post by akvino on 2009-06-16
> **Reiger said:**
> (1) In PHP a variable name is like an inode in a filetable: a variable does not correspond to a value, but rather to the location of a value.

This has a few consequences:
(a) You can assign multiple names to the same content using the $first = &$second syntax. (Changing $second results in the same changes being visible in $first.)
(b) Shooting yourself in the foot becomes trivial when you do raw operations on the `inode table'.


(2) The example you posted is a classic which has its own name in functional programming: destructive update. It is one of those things pure functional languages do away with, and imperative languages can't do without. What you did is allocating a variable (in some table), creating an object and associating it with the new record in the variable table. Then you orphaned the object in favour of a new object and re-associated the record in the variable table with this new record: the orphan is to be destroyed by the garbage collector whenever it decides to go and free some memory.

It is also not worth bothering with thinking about destructive update in (managed) imperative languages that feature automatic memory management: it only gives you headaches.


I assumed something like this would happen - so in essence once the handle is removed php invokes garbage cleaning destructor, kills the old object, and allocates memory for the new one.

---

### Post by fr4nko on 2009-06-16
> **akvino said:**
> 
1) If I have a function that will create new object on the request - is php at any point aware that another object with the same name might be used and pass the handle by reference - or does it just replace the current object with the new one, or something else?

I think an simple ways of obtaining what you want is by using the GLOBALS array and just chek it in advance if the variable has been defined. The GLOBALS array contains all the global variables and you can use it like an ordinary array. So the following code should make the affair:
```
function object_generator() {
    return new Object();
}

function mydefine($name, $generator) {
    if     (! array_key_exists($name, $GLOBALS)) {
        $GLOBALS[$name] = $generator();
    }
}

# equivalent to : $a = object_generator()
mydefine('a', 'object_generator');

```As you can see it use the function array_key_exists to check if the variable has been already defined. Note that you need to use the 'generator' technique because if you pass a new object to the 'mydefine' function a new object will be created but not used, so it will be a waste of resources and execution time.

Francesco

---

### Post by Reiger on 2009-06-16
> **akvino said:**
> I assumed something like this would happen - so in essence once the handle is removed php invokes garbage cleaning destructor, kills the old object, and allocates memory for the new one.

No. Not quite. The most important thing here is that, yes destructor code (if any) is run, but no this does not mean that the old object is actually killed at all. It is only killed when the Garbage Collector decides that it should be. You cannot truly kill an object[1], you can merely orphan it.

For another file system analogy: deleting a file does not mean erasing its contents from disk: all it does is removing any meta data about its existence (removing its entry in the file table). Then to the OS it counts as deleted, and there is a gap in the disk layout which may or may not get filled when a new file is created. Likewise, destructive update in an managed environment with garbage collection means simply that you can no longer access the old value by its former name. Conceptually it is deleted, but in practice it still exists as a node in the heap with no connection to the symbol table that is used for variable names.

For another analogy: compare the `rm' command with unset(). It does about the same: it removes a given record from the inode table. *It never removes any contents whatsoever from the actual storage medium!*

[1] : Not entirely accurate. The problem is that if you had code like this:
[php]
<?

$toDie = new ObjectToDie();
function killer() {
  global $toDie;
  $toDie->__destruct(); 
}

killer(); // let's try to destroy the object?
echo "What's this {$toDie->toString()}??",PHP_EOL;

class ObjectToDie {
  function __construct() {
    echo "Hello {$this->toString()}!",PHP_EOL;
  }
  function toString() { return "World"; }
  function __destruct() {
    echo "Farewell, cruel {$this->toString()}! ...",PHP_EOL;
  }
}
?>
[/php]

The destructor is called outside of the scope in which the object was declared in. For reasons which are probably good but I don't know about yet would guess that they involve the automatic clean up after a return statement; the __destruct() code is run but the object on which it is run is not the same as that which it was supposed to be run on (copy on write!). And FYI, this will for similar reasons not work either (however it is rather more safe since the destructor will be called only once, namely when the object is truly killed at the program exit):
[php]
function killer() {
 global $toDie;
 unset($toDie);
}[/php]
And:
[php]
function killer(&$toKill) {
 $toKill->__destruct();
}
[/php]

---

