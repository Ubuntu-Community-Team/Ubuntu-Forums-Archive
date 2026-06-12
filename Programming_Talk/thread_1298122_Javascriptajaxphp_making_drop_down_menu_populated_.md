---
title: "Javascript/ajax/php making drop down menu populated by a database..."
date: 2009-10-22
forum: Programming Talk
---

### Post by hockey97 on 2009-10-22
Hi, I am currently been working on making code to make a drop down get populated by whats in the database.

The drop downs I have is one for countries another for states another for cities. 

I succeeded on making the 2nd drop down to populate based on the first one which is countries.

Now I have a hard time to get cities to populate based on what state was selected.

here is the code I have: 


Main  page with the drop down menus:
```
<?php
include("..../mysqldata.php");
include("..../paging.php");
session_start();
//if($_SESSION["username"]==""){
//$_SESSION["logged"]=0;
//exit("Sorry your not logged in, please log in.");}
//if ($_SESSION["logged"] == 1) {
/*if ($_GET["page"]>="1") {
echo"<script type=\"text/javascript\">
window.location = \"http://www.chillenvillen.com/paging.php\"
</script>
"; exit();}*/
?>
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
<link rel="stylesheet" type="text/css" href="/market/market.css" />
<title>Open Market</title>
<script type="text/javascript" src="/pngFix/jquery-1.3.2.min.js"></script>
<script type="text/javascript" src="/pngFix/mootools.js"></script>

  <script type="text/javascript" src="/pngFix/carousel.us.js"></script>
<script type="text/javascript" src="/pngFix/jquery.pngFix.js"></script>
<script type="text/javascript" src="/pngFix/prototype.js"></script>
<script type="text/javascript">

	$(document).ready(function(){

		$(document).pngFix()});
</script>
<script language="javascript" type="text/javascript">

function getXMLHTTP() { 

		var xmlhttp=false;	

		try{

			xmlhttp=new XMLHttpRequest();

		}

		catch(e)	{		

			try{			

				xmlhttp= new ActiveXObject("Microsoft.XMLHTTP");

			}

			catch(e){

				try{

				xmlhttp = new ActiveXObject("Msxml2.XMLHTTP");

				}

				catch(e1){

					xmlhttp=false;

				}

			}

		}

		 	

		return xmlhttp;

    }

	

	function getState(country) {		

		

		var strURL="/libs/findState.php?country="+country;

		var req = getXMLHTTP();

		

		if (req) {

			

			req.onreadystatechange = function() {

				if (req.readyState == 4) {

					// only if "OK"

					if (req.status == 200) {						

						document.getElementById('States').innerHTML=req.responseText;						

					} else {

						alert("There was a problem while using XMLHTTP:\n" + req.statusText);

					}

				}				

			}			

			req.open("GET", strURL, true);

			req.send(null);

		}		

	}

	function getCity(country,state) {		

		var strURL="/libs/findCity.php?country="+country+"&state="+state;

		var req = getXMLHTTP();

		

		if (req) {

			

			req.onreadystatechange = function() {

				if (req.readyState == 4) {

					// only if "OK"

					if (req.status == 200) {						

						document.getElementById('City').innerHTML=req.responseText;						

					} else {

						alert("Error:\n Cannot Proccess City Find request.\n Please Contact the website admin about this error.");

					}

				}				

			}			

			req.open("GET", strURL, true);

			req.send(null);

		}

				

	}

</script>

</head>
<body>
<img id="mlogo"src="/Artwork/marketlogo.png">
<img id="menu"src="/Artwork/menubackground.png">
<div id="form1">
</div>
<form name="market" action="/market/" method="POST">
<a id="select">Select a Market location:</a>
<a id="country_text">Select A Country:</a>
<select name="id" id="country" onChange="getState(this.value)">
<option value="AF">Afghanistan </option>
<option value="BR">Brazil</option>
<option value="CA">Canada</option>
<option value="CN">China</option>
<option value="EG">Egypt</option>
<option value="FR">France</option>
<option value="DE">Germany</option>
<option value="HK">Hong Kong</option>
<option value="IN">India</option>
<option value="IR">Iran</option>
<option value="JP">Japan</option>
<option value="MK">Macedonia</option>
<option value="MX">Mexico</option>
<option value="NL">Netherlands</option>
<option value="PA">Panama </option>
<option value="SA">Saudi Arabia </option>
<option value="UAE">United arab Emirates</option>
<option value="US">United States</option>
<option value="GB">United Kingdom</option> 
<option value="VE">Venezuela</option>
</select>
<a id="state_text">Select A State/Province:</a>
<select name="id" id="States">
<option><b> Select A Country First</b></option>
</select>
<a id="City_text">Select A City:</a>
<select name="id" id="City">
<option> Select A State First</option>
</select>
<a id="item_text">Items:</a>
<select name="id" id="items">
<option value="Automobiles">Automobiles</option>
<option value="software">Software</option>
<option value="ch">Computer Hardware</option>
</select>
<a id="zip_text">Enter a zip code:</a>
<input id="zip" type="text" name="zip" maxlength="5" size="4">
<input id="submit" type="submit" name="submit" value="Submit">
</form>
</body>
</html>
```

Here is the findstate.php file 

```
<?php
include("....database_lib.php");
$country=$_GET['country'];
$data=new database();

$data->database_start();
$database="Location";
$data_table="State";
$where_equal=$country;
$logic="";
$other_field="";
$where="country";
$field="value,state";
$no_conditions='2';
$find=$data->query_find($database,$data_table,$where_equal,$where,$field,$logic,$other_field,$no_conditions);
while($row=mysql_fetch_assoc($find)) {
$value=$row['value'];
$state=$row['state'];
echo"

<option value=\"$value\">$state</option>";
}?>

```
Then here is the findcity.php
```

<?php
include("....database_lib.php"); 
$country=intval($_GET['country']);
$state=intval($_GET['state']);

database_start();
$database="Location";
$data_table="State";
$where_equal="$country";
$where="country";
$logic="AND";
$other_field="state='$state'";
$no_conditions='2';
$find=query_find($database,$data_table,$user,$where,$field,$logic,$other_field,$no_conditions);

$data_table="";
$where_equal="$state";
$where="state";
$find2=query_find($database,$data_table,$user,$where,$field,$logic,$other_field,$no_conditions);
echo"

<option>Select City</option>";

 while($row=mysql_fetch_array($find)||$row2=mysql_fetch_array($find2)) { 
$city=$row['city'];
$state=$row['state'];
$city2=$row2['city'];
$state2=$row2['state'];

echo"<option value=\"$state\">$city</option>";
echo"<option value=\"$state2\">$city2</option>"; 
};
?>

``` 

The database_lib.php is my own class system that does the query and handles the database type code.


The problem arises at the findstate.php file. I was told I am supposed to put the select tags  meaning I have to generate the drop down again with the function getcity with the onchange event. I tried that and the results was creating a dropdown menu inside the state drop down menu. 

So the problem here is that I am confused as to how I should be able to run the javascript function getcity since I already created the state drop down menu but didn't populate it until the php file was runned.

Any ideas what I should or could do?

---

### Post by mike_g on 2009-10-22
In your first dropdown you change the state when a country is selected:
```
<select name="id" id="country" onChange="getState(this.value)">
```
But when you select a state there is no onChange trigger:
```
<select name="id" id="States">
```
You could do something like:
```
<select name="id" id="States" onchange="getCity(document.getElementById('city').value, this.value)">
```
I havent tested it, but it might work.

Also, why are you including jquery and mootools then hand coding all the AJAX yourself. I'd learn to use the libraries as cross browser ajax is a pain in the *** to get working like this when you can have it done for you.

---

### Post by hockey97 on 2009-10-22
I got it to work but just now I can't get cities drop down menu to just list cities only of the State that the user/client selected.

---

### Post by hockey97 on 2009-10-23
ok, I got it to work and populate just one problem that arised. 

it's my sql query. For the cities I did a query to grab data out of the database that state =  the 2 states initiials meaning like MI,OH,CA,NV etc...

What I want the city to populate is only the states that were selected. So far right now it will grab all that is in the database so it won't matter if you pick a state is would just list all the cities that are in my database. 

I just want it to only populate the cities that are in the database for that particular state.

I did a ```
"select city from state  where value= var state";
```

that is the theory what I did.  I am selecting the city which stores the cities of that state.  I have have the database table named state. I then do a where value = var state. 

The variable state holds the 2 value letters of each state like CA,MI,LA,NV etc..  

The problem right now is that if the user selected the US country and the state OHIO I want to query and populate the city drop down menu that only the cities in OHIO will be listed in the drop down menu. Currently this dosen't happen it will only show every city saved in the database.

even tough I said to select the city where state = var state  

state location has the 2 letters rep of each state. So does the var state.

So in those case the query is saying select city names where state(OH)=var state (OH) 

so it supposed to grab only the cities in the database that are in the State of Ohio. Yet this dosen't happen instead it just gives a list of all cities in the U.S

---

### Post by januzi on 2009-10-23
1. replace mysql_fetch_array with mysql_fetch_assoc
2. paste one of those queries that are generated by query_find

---

