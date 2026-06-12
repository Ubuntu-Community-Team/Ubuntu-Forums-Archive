---
title: "Learning PHP: Trouble with function that alters array"
date: 2009-01-06
forum: Programming Talk
---

### Post by Joshuwa on 2009-01-06
Hi,

I've been spending the last few days trying to learn PHP, and one of the examples I've come up with to try and use arrays has got me scratching my head.

Basically, I've created a function *remove_lake()* which takes two arguments: the name of a lake, and the name of the array hopefully containing the lake. It then searches the array, and if the lake is found, it removes it from the array. If not found, it tells you that lake wasn't in the array.

What I'm noticing is that when calling my function and giving it the variables to be used, no change occurs.

I'm thinking it may be a scope issue, but being new to PHP, I'm not sure yet how to get around it.

Here is my code (please note: the assignment in *remove_lake()* is on purpose, and is not a botched attempt at comparison)
[PHP]<?php

// Setup base array with lakes
$locations = array('Sheila Lake', 'Houghton Lake', 'Four Mile Lake',
                   'Leeke Lake', 'Green Lake');

// Define some functions to operate on the array
function show_lakes($in_data) {
    $lakes = count($in_data);
    print "There are $lakes lakes stored in the array:";
    print "<br />";

    foreach($in_data as $place) {
    print "$place <br />";
    }
}

function remove_lake($lakename, $lakearray) {
    // the following assignment is deliberate
    if($key = array_search($lakename, $lakearray)) {
        unset($lakearray[$key]);
    }
    else print "<br />## That lake was not found. ## <br /><br />";
}

// test the functions
print " --showing default array -- <br />";
show_lakes($locations);
print "<br /><br />";

// add a new lake
$locations[] = 'Joslin Lake';

print " --showing additional entry to array -- <br />";
show_lakes($locations);
print "<br /><br />";

// remove a previous lake
print " --showing removal of entry from array -- <br />";
remove_lake('Green Lake', $locations);
show_lakes($locations);
print "<br /><br />";


?>[/PHP]

Thanks all; any guidance or hints are much appreciated! :D

---

### Post by Bachstelze on 2009-01-06
It is indeed a scope issue. Normally, when you pass the [font="monospace"]$lakearray[/font] argument to your [font="monospace"]remove_lake()[/font] function, a copy of this object is created in memory, and the function will only be able to manipulate that copy, not the original (here, the [font="monospace"]$locations[/font] object in your main program).

You have three ways to achieve the desired goal:

-> Make the [font="monospace"]$locations[/font] variable accessible from inside your function using the [font="monospace"]GLOBAL[/font] keyword. This is usually considered bad practice and you should avoid it, but here's an example for information:

```
firas@nobue ~ % cat test.php
<?php
$locations = array("foo", "bar");

function remove_lake($lakename)
{
        GLOBAL $locations;
        // the following assignment is deliberate
        if(($key = array_search($lakename, $locations)) !== false) {
                unset($locations[$key]);
        }
        else print "<br />## That lake was not found. ## <br /><br />";
}

remove_lake("foo");
var_dump($locations);
?>
firas@nobue ~ % php test.php
array(1) {
  [1]=>
  string(3) "bar"
}

```

-> Use the return value of the function to pass the modified array to the rest of your program:

```
firas@nobue ~ % cat test.php
<?php
$locations = array("foo", "bar");

function remove_lake($lakename, $lakearray)
{
        // the following assignment is deliberate
        if(($key = array_search($lakename, $lakearray)) !== false) {
                unset($lakearray[$key]);
                return $lakearray;
        }
        else {
                print "<br />## That lake was not found. ## <br /><br />";
                return NULL;
        }
}

$locations = remove_lake("foo", $locations);
var_dump($locations);
?>
firas@nobue ~ % php test.php
array(1) {
  [1]=>
  string(3) "bar"
}

```

-> Use object-oriented programming, but that will take a bit more work. ;) You can stick with #2 for now.


Also, notice that I changed the test in your function. Try to find out by yourself why yours was wrong. ;)

---

### Post by Bachstelze on 2009-01-06
It is indeed a scope issue. Normally, when you pass the [font="monospace"]$lakearray[/font] argument to your [font="monospace"]remove_laje()[/font] function, a copy of this object is created in memory, and the function will only be able to manipulate that copy, never the original (here, the [font="monospace"]$locations[/font] object in your main program).

You have three ways to achieve the desired goal:

-> Make the [font="monospace"]$locations[/font] variable accessible from inside your function using the [font="monospace"]GLOBAL[/font] keyword. This is usually considered bad practice and you should avoid it, but here's an example for information:

```
firas@nobue ~ % cat test.php
<?php
$locations = array("foo", "bar");

function remove_lake($lakename)
{
        GLOBAL $locations;
        // the following assignment is deliberate
        if(($key = array_search($lakename, $locations)) !== false) {
                unset($locations[$key]);
        }
        else print "<br />## That lake was not found. ## <br /><br />";
}

remove_lake("foo");
var_dump($locations);
?>
firas@nobue ~ % php test.php
array(1) {
  [1]=>
  string(3) "bar"
}

```

-> Use the return value of the function to pass the modifier array to the rest of your program:

```
firas@nobue ~ % cat test.php
<?php
$locations = array("foo", "bar");

function remove_lake($lakename, $lakearray)
{
        // the following assignment is deliberate
        if(($key = array_search($lakename, $lakearray)) !== false) {
                unset($lakearray[$key]);
                return $lakearray;
        }
        else {
                print "<br />## That lake was not found. ## <br /><br />";
                return NULL;
        }
}

$locations = remove_lake("foo", $locations);
var_dump($locations);
?>
firas@nobue ~ % php test.php
array(1) {
  [1]=>
  string(3) "bar"
}

```

-> Use object-oriented programming, but that will take a bit more work. ;) You can stick with $2 for now.


Also, notice that I changed the test in your function. Try to find out by yourself why yours was wrong. ;)

---

### Post by Joshuwa on 2009-01-06
Thanks for such a fast and informative reply!

I'm guessing my test is wrong because nothing was actually being compared; I was thinking that just assigning $key a value would make it operate as if I just used *if(non-zero value)* so that it would evaluate as true.

But now I realize that if the lake being searched for was the first in the array, it would assign $key = 0, which would make the statement false and prevent *unset()* from ever occurring.

That may not be all that was wrong with it (don't tell me yet :D), so I'm definitely going to be giving that some thinking on my way home.

Thanks again for the help :)

---

### Post by Reiger on 2009-01-06
I'm surprised nobody has yet mentioned that PHP is aware of pass-by-reference (aka pointers):
[php]
<?php

$array[0]="foo";

function bar($array) {
	$array[0]="bar";
}

bar(&$array);

die(var_dump($array));

?>
[/php]
Three guesses what this outputs? ;)

---

