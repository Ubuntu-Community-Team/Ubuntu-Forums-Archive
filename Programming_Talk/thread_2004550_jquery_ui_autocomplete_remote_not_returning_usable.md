---
title: "jquery ui autocomplete remote not returning usable json data"
date: 2012-06-16
forum: Programming Talk
---

### Post by cdaringe on 2012-06-16
Hi all:

I wish to have an autocomplete feature on my site that dynamically requires requeries my MySQL database as the user enters in information.

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

This works!  But that var, 'test', is static.  Ironically enough, the search.php page generated that very bock of test, but i manually copied and pasted it's output into the js here, with a preceding "var test = ...;".  So, when I uncomment source: "./search.php" (confirmed, file does exist in the same dir), and also comment out "source: test", why does the autocomplete run unsuccessfully?  I know the query is good, because I already tested output!

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
	//json_encode($jsonItems);
	print json_encode($pn_queries);

?>

```

---

