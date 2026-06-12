---
title: "PHP / ajax Display size of sql table (always display current size)"
date: 2013-03-04
forum: Programming Talk
---

### Post by Xender1 on 2013-03-04
I am working on a simple website using html,css,php, and some jquery currently (sliders). Currently when they are logged in it shows how many other users are also logged in. I have this all in a mysql table called users. So when they login and are on main.php, the screen shows how many other people are also logged in (the COUNT of users). What I want is for this to always be the most up to date value...currently if I remove some users from the database, the value only changes when I refresh the page. I was thinking about having a function on a set timeout counter that would query this statement and get the value (or monitor the database for a change before querying but efficiency is not my highest priority atm). I am sort of lost as to how to go about this ..... I believe ajax is the solution though. Any tips or suggestions would be great.

Some sample code I have now:
```

	try {
		$dbconn = new PDO('mysql:host=localhost;dbname='.$config['db'], $config['user'], $config['pass']);
	} catch (Exception $e) {
		die ("[!] couldn't conncect to database " . $config['db']);
	}

	$sql = "SELECT count(*) FROM users WHERE time < :mytime"; 
	$stmt = $dbconn->prepare($sql); 
	$stmt->execute(array(':mytime'=>$user['time'])); 
	$pos = $stmt->fetchColumn();

//end php and the html is

      <h3> <?php echo $pos . " users ahead of you"; ?></h3>

```

---

### Post by greenpeace on 2013-03-04
Hey, 

Should be simple to write a simple php script that queries the DB, and returns the number of active users, and then call from your page it over ajax.  You'd need to think about:

1. the (totally separate) PHP script to return the number of active users
2. the js function on your page making an ajax call to that script
3. the processing of the return value, and updating the page.

After that, have a look at the **setInterval** javascript method to keep making the call to your PHP script.

Then have a think about all those calls to your DB, and set the interval appropriately.  :)

Good luck!
Gp

---

### Post by Xender1 on 2013-03-04
> **greenpeace said:**
> 
1. the (totally separate) PHP script to return the number of active users


Thank you very much, I was having a hard time wrapping my head around dealing with the program flow and then returning/updating. What you said really cleared up how this process works! I have actually not done many php 'scripts' so going to be checking them out on how to return a variable. Thanks again!

---

### Post by greenpeace on 2013-03-04
no worries, glad to help :)  

In terms of returning the values, just an echo at the end of the script should do it.. in fact, you should be able to test it by simply opening the page with your browser. 

good luck!
Gp

---

### Post by Xender1 on 2013-03-04
Hey just figured I would let you know I got it to work!! Got my getXmlHttp() function returning the correct object based on browser, and the HandleResponse to update the .innerHTML of the right element. My php script executes the sql I had above and then echos it back. Appreciate your help!!

```

//<script>
                var qVar = setInterval(function(){updateCount()},5000);

		function updateCount()
		{
		  var xmlHttp = getXmlHttp();

		  xmlHttp.onreadystatechange = function()
		  {
			if(xmlHttp.readyState == 4)
			{
			  HandleResponse(xmlHttp.responseText);
			}
		  }
		  var url = 'getCount.php?go='+document.getElementById('idpass').value;
		  xmlHttp.open("GET", url, true); 
		  xmlHttp.send(null);
		}

```

---

### Post by greenpeace on 2013-03-05
hey!  Brilliant!  :)  It's not that complicated once you get your head around the flow, eh?  :)

Don't forget to mark the thread as "solved"... ;)

Gp

---

