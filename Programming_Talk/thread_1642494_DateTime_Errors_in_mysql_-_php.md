---
title: "DateTime Errors in mysql - php"
date: 2010-12-10
forum: Programming Talk
---

### Post by v1ad on 2010-12-10
What i am trying to do is insert the current date and time into a mysql variable called datetime. 
also be able to call it and display it properly in php->html. 
Some help would be appreciated :[

here is the mysql table.
```

create table sales (
		salesid int unsigned not null auto_increment primary key,
		customerid int unsigned not null,
		userid int unsigned not null,
		productinfo varchar(512),
		amount float(6,2),
		date	datetime not null	
);


```

and here is the msql query from php.

```

		$query = "insert into sales values (NULL, '".$id."', '".$userid."', '".$info."', '".$total."', 'NOW()')";
		$result = mysqli_query($db, $query);
		if (!$result) {
			echo "<br />Error updating sales<br />";
			exit(1);
		}


```

it inserts into the database but the datetime is all zeros..

---

### Post by Arndt on 2010-12-10
> **v1ad said:**
> What i am trying to do is insert the current date and time into a mysql variable called datetime. 
also be able to call it and display it properly in php->html. 
Some help would be appreciated :[

here is the mysql table.
```

create table sales (
		salesid int unsigned not null auto_increment primary key,
		customerid int unsigned not null,
		userid int unsigned not null,
		productinfo varchar(512),
		amount float(6,2),
		date	datetime not null	
);


```

and here is the msql query from php.

```

		$query = "insert into sales values (NULL, '".$id."', '".$userid."', '".$info."', '".$total."', 'NOW()')";
		$result = mysqli_query($db, $query);
		if (!$result) {
			echo "<br />Error updating sales<br />";
			exit(1);
		}


```

it inserts into the database but the datetime is all zeros..

I'm not sure I remember these things, but might it be the case that you should write

NOW()

rather than

'NOW()'

?

---

### Post by v1ad on 2010-12-11
solved, thanks. i went with date(Y-m-d H:i:s, time());

---

