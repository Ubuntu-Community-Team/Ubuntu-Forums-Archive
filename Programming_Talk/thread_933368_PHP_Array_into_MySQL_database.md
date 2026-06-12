---
title: "PHP Array into MySQL database"
date: 2008-09-29
forum: Programming Talk
---

### Post by mister_doctor on 2008-09-29
Without going into details, I am a PHP newb, and programming newb in general, so please bare with.

I am trying to write a PHP app that will take data from a text file (list of servers) and use it to update a single field in MySQL-based table (software build number). The contents of the text file is used to decide what rows will be updated. The data to be entered into said field comes from a form on another page.

The array loads fine according to a foreach(), and the data is being received from the form. Where I run into problems is getting the data to actually update.

I've included my sloppy-*** newb-code below:

```
<?php

/*
"stream" comes from a hidden field in the previous page, there are more then one form pages for now.
"build" comes from the text input in the previous page

*/

$stream = $_POST[stream];
$build = $_POST[build];
$filename = "$stream.txt";
$arealist = file($filename);

// TEST array output

foreach ($arealist as $list)
{
	echo "$list <br />";
}

// TEST $build OUTPUT

echo "$build <br />";


// MySQL crap

// Connect and select database
	$link = mysqli_connect("localhost", "user", "password", "dbname") or die('Could not connect');
	$query = "UPDATE table set Build = '$build' where Area ='$area'";
//	$result = mysqli_query($link, $query);


// $rows = mysqli_affected_rows();

foreach ($arealist as $area)
{
	$result;
	echo "$area updated. <br />";

}

mysqli_close($link);


?>
```

The specific problem is that only the last server in the array is updated. And yet the output from the loop reads:

```

server01 updated. 
server02 updated. 
server03 updated. 
server04 updated. 
server05 updated. 
server06 updated. <--- only row that actually updated

```

I'm starting to think that maybe i've got some bad formatting somewhere, or I'm just not handling UPDATE queries properly.

If anyone has any simple solutions, that would be fantastic. Hell, if someone just tells me "your doing it wrong", I can live with that too.

Thank you in advance.

---

### Post by Mindzai on 2008-09-29
Just of the top of my head so let me know if there are errors, I havent checked:

[php]<?php

// array indexes should be in single quotes to avoid a NOTICE level error
$stream = $_POST['stream'];
$build = $_POST['build'];
$filename = "$stream.txt";
$arealist = file($filename);

// this is a nicer way of viewing an array as it shows the proper structure
echo '<pre>';
print_r($arealist);
echo '</pre>';

// TEST $build OUTPUT
echo "$build <br />";

// Connect and select database
$link = mysqli_connect("localhost", "user", "password", "dbname") or die('Could not connect');

// now, you either update in a loop like so:
/*
foreach ($arealist as $area) {
    $result = mysqli_query("UPDATE table SET Build = '$build' WHERE Area='$area'");
    echo "$area updated. <br />";
}
*/

// OR, you can get tricky with your SQL syntax and save yourself lots of queries :)
foreach ($arealist as $area) {
    $when .= "WHEN $area THEN '$build' ";                    
    $where .= "$area,";
}
$where = rtrim($where, ', '); 
$result = mysqli_query("UPDATE table SET Build = CASE Area $when END WHERE Area IN ($where)");

mysqli_close($link);
?>[/php]

I've put notes in the comments but by all means shout if you need clarification.

---

### Post by ghostdog74 on 2008-09-29
> **mister_doctor said:**
>  $rows = mysqli_affected_rows();
[/CODE]


it should be $rows = mysqli_affected_rows($results); then check for value of $rows.

---

### Post by Mindzai on 2008-09-30
Actually according to the PHP manual it the only parameter is a link identifier, in the above code $link. Aplogies if this is what you meant, but I inferred from the name of your variable that it contains a resource identifier as returned from a query rather than a link identifier as returned from the mysqli_connect function.

---

### Post by ghostdog74 on 2008-09-30
yes its the db handle, not the results from query.

---

