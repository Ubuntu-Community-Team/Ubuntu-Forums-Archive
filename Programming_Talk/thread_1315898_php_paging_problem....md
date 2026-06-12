---
title: "php paging problem..."
date: 2009-11-05
forum: Programming Talk
---

### Post by hockey97 on 2009-11-05
I for some reason not geting any results showing up but no error messages at all.

here is the code of the paging page:

```
<?php
session_start();
include('/home/aaron/websites/domain.com/libs/database_lib.php');
$data=new database;
$data->database_start();
mysql_select_db("Market"); 
$_SESSION['country']  =$_POST["country"];
$_SESSION['state'] =$_POST["States"];
$_SESSION['city'] = $_POST["City"];
$pages =$_GET["page"];
$country = $_POST["country"];
$state = $_POST["States"];
$city = $_POST["City"];
$item = $_POST["items"];
$zipcode = $_POST['zip'];
$s =1;
$limit =10;
if(!$page || $page = 0 || !is_numeric($page)){
$page = '1';}
else{$page=$pages;}
$query1 = mysql_query("SELECT * FROM postings WHERE state ='".$state."' AND Country ='".$country."' AND city ='".$city."' OR zipcode ='".$zipcode."'  AND item ='".$item."'")or die("Error In Query " . mysql_error());
$numbers = mysql_num_rows($query1);
    $total_pages =ceil($numbers/$limit);
    $query2 = mysql_query("SELECT * FROM postings  WHERE state ='".$state."' AND Country ='".$country."' AND city ='".$city."' OR zipcode ='".$zipcode."'  AND item ='".$item."' LIMIT $s,$limit") or die("Error In Query " . mysql_error());
echo"<html>
<head>
<link rel=\"stylesheet\" type=\"text/css\" href=\"/market/market.css\" />
<title>Market Area For $city,$state</title>
</head>
<body>
<img id=\"mlogo\" src=\"/Artwork/marketlogo.png\">
<img id=\"menu\" src=\"/Artwork/menubackground.png\">
";
while($r =mysql_fetch_array($query2)){
$itemimage = $r["Item_Image"];
$message = $r["Message"];
$item_name = $r["ITEM"];
echo"<img src=\"$itemimage\"><a>$item_name</a>
<a id=\"message\">$message</a>";}

echo"<img src=\"$itemimage\"><a>$item_name</a>
<a id=\"message\">$message</a>";}
if($p>0){
echo"<a href=\"/market/open_market_list_2.php?page=$p--.start=$s.act=$view\"><-</a>";
}
if($p>0){
echo"<a href=\"/market/open_market_list_2.php?page=$p++.start=$s.act=$view\">Next<br>-></a>";
}

$i =$total_pages;
$s =0;
$p =1;
while($i>0){
$i--;
$p++;
$s+10;
echo "<a href=\"/market/open_market_list_2.php?page=$p.start=$s.act=$view\">$p</a></body></html>";
}
?>
```


Then here is the code that is runned in the browser when this page is runned.

```
<html>
<head>
<link rel="stylesheet" type="text/css" href="/market/market.css" />
<title>Market Area For Detroit,MI</title>
</head>
<body>
<img id="mlogo" src="/Artwork/marketlogo.png">
<img id="menu" src="/Artwork/menubackground.png">
<img src=""><a></a>
<a id="message"></a><a href="/market/open_market_list_2.php?page=2.start=0.act=">2</a></body></html>

```

So the problem is that I am not getting results showing up on the page.

Any ideas what you think the problem is. Do you think my query is wrong?

---

### Post by korvirlol on 2009-11-05
Doesnt look like it is returning any rows, so id say somethig is wrong with the query. If there is no error, then the query is executing, but something in the logic of the query is not correct.

also... im not quite sure what youre going for here:

if p is > 0, it will execute both of those statement, which i dont think you want.

```
if($p>0){
echo"<a href=\"/market/open_market_list_2.php?page=$p--.start=$s.act=$view\"><-</a>";
}
if($p>0){
echo"<a href=\"/market/open_market_list_2.php?page=$p++.start=$s.act=$view\">Next<br>-></a>";
}
```

---

### Post by hockey97 on 2009-11-06
well, I made those with >0 to make  those next arrows and previous arrows to show up.  I will still play around with that. 

I am just focusing on the query. Something  went wrong where I won't get any results. i checked the variable values used in the query and all checks out good. 

I can't find anything really wrong with the  query. Can someone just look over my query and try and find any errors about it. I am still looking over it and trying to find out where I went wrong. I even checked the fields in the database to make sure it's right. Is mysql database case sensitive? 

Cause I have fields with some capital letters etc. Yet all of it still matched with the database field,whatever that was in my query fields matched the database. like state,country,city, etc.

---

### Post by hockey97 on 2009-11-08
well, how would you do a  sql query using more then one value for the where clause and used a limit clause. 

Cause I need to grab only the rows that contain a match to the country,state,city, and a math to the type of item that is posted. 

For example if I want to look for cars. I then would go to the drop down menu and find automobiles. So this should grab any cars/trucks in that country,state,city I wanted to look at.

anything I put inside the while fetch loop wont appear. Like if I put echo something in their then it won't echo.

I am supposed to get just one result right now. I have one thing in the database for testing purposes.

---

### Post by korvirlol on 2009-11-08
just going on what youre saying, you wont need a limit clause in your query. If you are trying to match results based on certain criteria, then limit will only limit the number of matching items returned. For example, if your query is correctly pulling the results defined in your where clause, and you use a limit, say 4, it will only return 4 rows matching the criteria. Im not sure if youre trying to achieve something else with the limit, but this is typically what limit does.

Are you using the limit to achieve pagination? If this is the case, i'd suggest you let php do the work with printing the proper rows for pagination. Thats how ive always done it.

> 
Cause I need to grab only the rows that contain a match to the country,state,city, and a math to the type of item that is posted.

```

$q = mysql_query("select * from postings where country = '".$country.'' and state = '".$state.'' and city = '".$city.'' ");
```

something like that would work to return all the rows for that country, state and city then you can print only the appropriate rows using php. You could use something like a get variable defining which page the user is looking at, then you can do some math on the rows to show only the appropriate ones per page.


At first, try to keep the query simple to make sure that it is pulling the right rows, once you get it working, then add more restrictive clauses to it.

---

### Post by hockey97 on 2009-11-08
ok, I found the problem. It was a stupid mistake. I kept looking at the code. Then decided to look at the values. I notice my limit values was 1 and 10 meaning it started at 1 and ended at 10. Yet I looked at it and was like ummm this dosen't look good. I knew in programming 1 resutl starts at 0 so I just changed the one to a 0 and boom I see the results now. 

Thanks for the help. You gotta love programming.... lol :p

---

### Post by v8YKxgHe on 2009-11-08
How nice of you to let your dear end users to alter that fine MySQL query you have there!

Read up on SQL Injection and ways to protect against it.

---

### Post by hockey97 on 2009-11-08
Hi, ya I am aware of sql injections and hacking methods. 

I wrote many classes that takes care of the security aspects of the website.

sql injections is one of them. I plan to use the classes and implement them into my site at the last stage before making the site go live. 

Right now I am just developing the functioning of the website. Once all that is done and I am ready to go live I will spend about 2 to 4 weeks on nothing but adding in the classes to my site and making sure the site is secure. I know a bunch of hackers and students that I know that are in security IT classes where they focuse on learning how to secure websites and networks. I can always have them ask their professor questions that could assist at helping make the site secure. 

I have a monitoring system that will be implemented on my site that monitors every activity and checks out if the person is doing hacking activities based on what and how the person is using my site. I also have a way to help prevent dos attacks (denial of service attacks). 

So I am not going light on securing my site. But thanks for the heads up. ):P

---

### Post by hockey97 on 2009-11-10
Hi, I just got one more question. Can I add css to the paging system?

Like it wont overlap?  Like I am using a while look with php. In the html code if I add a css file to add css values this inclues positining would it the html element overlap one anohter.

for example lets say I put image to absolute 400px. but this is for all images that are generated threw pagination. would the loop make every image to be exactly at 400px making it will overlap the previous image shown. 

Or would the loop just force the image down because of the html tags being recreated so it will  be 400px left but the top if it was 400px for the first one then the second one will sitll be 400px but would move it down because it's a whole new html tag. 

I want to use css to position texts and images being paginated.

---

