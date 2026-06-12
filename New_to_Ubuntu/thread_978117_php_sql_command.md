---
title: "php sql command"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by GoldStarDad on 2008-11-10
I am trying to call some info from my sql database and print it out as a mailing address.

Name
Address
City State
Zip
<space>
<space>
NEXT ADDRESS
<space>
<space>
ETC>

I have the data base calls working BUT the output for each address is all on one line.

Name Address City State Zip

What do I need to do to make it output the way I need to make my address labels??

HERE IS THE CODE

> <?php
//connect to database
$mysqli = mysqli_connect("localhost", "host", "password", "database");

	$display_block = "<h1>Mother and Address</h1>";

	//get all addresses
	$get_addresses_sql = "SELECT pf_mothers_name, pf_m_street_address, pf_m_city_state, pf_m_zip
	                      FROM community_phpbb_profile_fields_data";
	$get_addresses_res = mysqli_query($mysqli, $get_addresses_sql); 

		while ($add_info = mysqli_fetch_array($get_addresses_res)) {
			$name =$add_info['pf_mothers_name'];
			$address = $add_info['pf_m_street_address'];
			$citystate = $add_info['pf_m_city_state'];
			$zipcode = $add_info['pf_m_zip'];	
				
					$display_block .= "$name $address $citystate $zipcode<br />";

			
}
//close connection to MySQL
mysqli_close($mysqli);
?>
<html>
<head>
<title>My Records</title>

</head>

<body>
<?php echo $display_block; ?>
</body>
</html>

---

### Post by ohzopants on 2008-11-12
Add some <br />'s to your $display_block variable.  You should put one in wherever you want a line break.

---

### Post by GoldStarDad on 2008-11-12
Thanks ohzopants, 

That worked great. 

It is amazing being able to get help from professionals on the other side of the world simply by asking. With the economy the way it is right now in the USA my small non-profit organization is operating on a shoestring budget. I am trying to do everything possible myself, thanks so much for your assistance.

NOW, is there a way to have it **populate a template for printing**?

I would like to have them printed out to a _Avery Mailing Label Template_ that is two columns,  2 addresses wide x 10 addresses long (20 per page)

Right now with your <br/> suggestion, this code will output to a single column of addresses.


<<<<<<
<?php
//connect to database
$mysqli = mysqli_connect("localhost", "host", "password", "database");

	$display_block = "<h1>Mother and Address</h1>";

	//get all addresses
	$get_addresses_sql = "SELECT pf_mothers_name, pf_m_street_address, pf_m_city_state, pf_m_zip
	                      FROM community_phpbb_profile_fields_data";
	$get_addresses_res = mysqli_query($mysqli, $get_addresses_sql); 

		while ($add_info = mysqli_fetch_array($get_addresses_res)) {
			$name =$add_info['pf_mothers_name'];
			$address = $add_info['pf_m_street_address'];
			$citystate = $add_info['pf_m_city_state'];
			$zipcode = $add_info['pf_m_zip'];	
				
					$display_block .= "$name<br /> $address<br /> $citystate<br /> $zipcode<br /><br />";

			
}
//close connection to MySQL
mysqli_close($mysqli);
?>
<html>
<head>
<title>My Records</title>

</head>

<body>
<?php echo $display_block; ?>
</body>
</html>
>>>>>>>>>>>>>>>>>>>>>>

---

### Post by ohzopants on 2008-11-12
I'm no professional, but I'm glad I could help.

For the template thing, you may want to look into using tables.  Unfortunately, I have no idea how to do that properly.

Can you access the separate entries in $display_block? (e.g. $display_block[1] or $disply_block(1))

---

### Post by GoldStarDad on 2008-11-12
YES, I am the webmaster and I have FULL access to EVERYTHING.

I am accessing an sql database with tables that were set up by phpbb 3.0 with custom fields. 

This code we are working on right now is just sitting in a folder in the Admin. I just point my browser at the folder and it gives me the display in  my browser. My ultimate goal is to have a command to send it to the printer where it will print out onto the Avery Labels. 

NOTE: I have the Avery Label Template in a Word2007 doc. Maybe an import command? I really am way over my head here. Help

Michael

---

### Post by ohzopants on 2008-11-13
What I meant by accessing the separate entries of $display_block is whether or not that variable is some type of array.  If it is an array then you can just make a simple table using a for loop.

Something like this (note that I haven't done HTML in nearly forever and never got much past "Hello world" in PHP):
```

<table>
<?php
for ( $i = 0; $i <= SizeOf($display_block); $i += 1) {
    if ( $i % 2 = 0 )
	echo "<tr><td>";
	echo $display_block[i];
	echo "</td>";
    else
        echo "<td>"
	echo $display_block[i];
	echo "</td></tr>";
}
?>
</table>

```

---

### Post by GoldStarDad on 2008-11-14
Now I am really lost, :confused: Where would I insert that code?

Dazed & Confused a.k.a. Michael

---

### Post by indytim on 2008-11-14
I would suggest getting a book on basic php and give it an hour of study.  Either that or get someone locally that is versed in the php **basics**.  The questions that you are asking are understandable, but you need the basics to move forward.  It's probably not realistic to have the forum generate and debug your code for you.  

Just some thoughts.

IndyTim

---

### Post by hyper_ch on 2008-11-14
if you want to make a serial letter/lables or so with that data, use CVS instead (comma separated values).

Basically the output should then look like this:

```

FIELD1,FIELD2,FIELD3,FIELD4
FIELD1,FIELD2,FIELD3,FIELD4
FIELD1,FIELD2,FIELD3,FIELD4
FIELD1,FIELD2,FIELD3,FIELD4

```
This can then easily being imported into spreadsheet and you can then easily create a serial letter/labels with that.

---

