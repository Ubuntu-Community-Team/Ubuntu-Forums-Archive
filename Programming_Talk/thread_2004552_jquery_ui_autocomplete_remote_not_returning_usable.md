---
title: "jquery ui autocomplete remote not returning usable json data"
date: 2012-06-16
forum: Programming Talk
---

### Post by cdaringe on 2012-06-16
Hi all:

I wish to have an autocomplete feature on my site that dynamically re-queries my MySQL database as the user enters in information.

I have my main html/php/js page the looking like this:

```

<script type="text/javascript">

  $(function() {

   var test =[{"label":"AAA","value":"A"},{"label":"CEEZ ON MY KNEES!","value":"C"},{"label":"DDeeeS","value":"D"},{"label":"DAVES FAVORITE PART","value":"DAVE"},{"label":"BLAH","value":"B"},{"label":"HELLO FRIENDS","value":"02-2223"},{"label":"little chiuauauas","value":"04-1234"},{"label":"DOS PUPPIES","value":"05-2342"},{"label":"UNOS PEPITOS","value":"11-1111"},{"label":"FUNTIMES","value":"02-1235"}];


    $( "#pn" ).autocomplete({
      //source: "./search.php"
      source: test
    });
  });
...
</script>


```

This works!  But that var, 'test', is static.  The search.php page I want to use to update the autocomplete list generated that very bock of data for the test variable, but i manually copied and pasted it's output into the js here, with a preceding "var test = ...;".

So, when I uncomment source: "./search.php" and also comment out "source: test", why does the autocomplete run unsuccessfully?  I know the query code is good, because I already tested output!

search.php:
```

<?php

	
	$term=strtoupper($_GET['term']);

	$query = "SELECT pn,description FROM item WHERE CONCAT(description,pn) LIKE '%".$term."%' LIMIT 10";
	$result = mysql_query($query);

	while($row=mysql_fetch_array($result)) {
		$jsonItems['label']=$row['pn']."::".$row['description'];
		$jsonItems['value']=$row['pn'];
		$pn_queries[]=$jsonItems;
	}
	print json_encode($pn_queries);

?>

```

Any tips are welcomed!  Thanks guys.

-Chris

---

### Post by cdaringe on 2012-06-16
The answer to my problem was remarkably simple.  When the user on the client side enter stuff, the dB connection setup that the server used to generate the page is scrapped!  thus, there were no active permissions for my search.php to use the db.  I had to rebuild in my connection script into the search script in order for the server to return the json values.

props to shoky in the jquery freenode irc room for showing me the networks tab in crome to monitor requests

---

