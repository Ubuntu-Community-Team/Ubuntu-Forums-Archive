---
title: "Foreach with Multidimensional Array"
date: 2009-11-05
forum: Programming Talk
---

### Post by MTGap on 2009-11-05
I'm trying to echo this multidimensional array, but I'm having trouble as to what to actually do:

[PHP]$CurTimeStamp = time();
$CurDateName = date("l");
echo $CurDateName;
$Email = "";
define('DB_EVENTS',	DB_PREFIX.'aw_ec_events');

/*-------------------------------------------------------+
| Upcoming Events Search - Sunday
+--------------------------------------------------------*/

if ($CurDateName=="Thursday") {
$Day7 = "600937";
$CurDate7 = date("Y-m-d",$CurTimeStamp + $Day7);
$CurDate = date("Y-m-d",$CurTimeStamp);

echo $CurDate7;

echo $CurDate;

echo "Sunday";

$result = dbquery("SELECT * FROM ".DB_EVENTS." WHERE ev_start BETWEEN '$CurDate' AND '$CurDate7' ");
	if (dbrows($result)) {
		echo dbrows($result);
		$i = 0;
		while($row = mysql_fetch_assoc($result)) {
			foreach($row as $column=>$val) { 
				$arr[$i][$column] = $val; 
			} 
			$i++; 
		} 
		$Email = "1";
		echo "Email";
			
/*-------------------------------------------------------+
| Creation of Email Message - Sunday
+--------------------------------------------------------*/	
$subject = "Upcoming Events This Week";

foreach ($arr['ev_title'] as $key => $data) {

$eventinfo = "<ul>";
$eventinfo .= "<li><a href='http:///infusions/aw_ecal_panel/view_event.php?id=".$arr['event_id'][$key]."'/>$data</a>";
$eventinfo .= " on ".$arr['ev_start'][$key]." from ".$arr['ev_start_time'][$key]." ".$arr['ev_start_ampm'][$key]." </li>";
$eventinfo .= "</ul>";

$message =  "<html><table><tr><td><img src='http:///images/calendar.png' /></td><td><h1 style='font-size:125%'>$subject</h1></td></tr>";
$message .= "<tr><td colspan='2'><hr>The following events are taking place this week: <br /><br />$eventinfo</td></tr><tr><td colspan='2'>";
$message .= "<a href='http:///news.php'><img src='http:///images/logo.png' /></a></td></tr></table></html>";	
			}
				} 
}[/PHP]

This was written within php-fusion so some functions are used from its maincore. However I'm having trouble with this foreach statement: foreach ($arr['ev_title'] as $key => $data) {

I'm not sure how to do it... any help. The rest of the code does work though.

---

### Post by korvirlol on 2009-11-05
to access a multidimensional with foreach generally:

[PHP]foreach($arr as $first){
     foreach($first as $second){
         //do work with each array element as $second
     }
}[/PHP]

---

### Post by MTGap on 2009-11-05
Well I tried this: 

[PHP]foreach ($arr as $first) {
	foreach ($first as $second) {

$eventinfo = "<ul>";
$eventinfo .= "<li><a href='http:///infusions/aw_ecal_panel/view_event.php?id=".$second['event_id']."'/>".$second['ev_title']."</a>";
$eventinfo .= " on ".$second['ev_start']." from ".$second['ev_start_time']." ".$second['ev_start_ampm']." </li>";
$eventinfo .= "</ul>";

$message =  "<html><table><tr><td><img src='http:///images/calendar.png' /></td><td><h1 style='font-size:125%'>$subject</h1></td></tr>";
$message .= "<tr><td colspan='2'><hr>The following events are taking place this week: <br /><br />$eventinfo</td></tr><tr><td colspan='2'>";
$message .= "<a href='http:///news.php'><img src='http:///images/logo.png' /></a></td></tr></table></html>";	
			}
				   }
				} 
}[/PHP]

And I just ended up getting this:

> Notice: Uninitialized string offset: 0 in /home/troop1/public_html/eventmail.php on line 63

Notice: Uninitialized string offset: 0 in /home/troop1/public_html/eventmail.php on line 63

Notice: Uninitialized string offset: 0 in /home/troop1/public_html/eventmail.php on line 64

Notice: Uninitialized string offset: 0 in /home/troop1/public_html/eventmail.php on line 64

Notice: Uninitialized string offset: 0 in /home/troop1/public_html/eventmail.php on line 64

Which is all of the array's I have in the $eventinfo variable

---

### Post by korvirlol on 2009-11-05
$arr, $first, $second was an example... you will have to supplement your own appropriate array and foreach variable names with that syntax

---

### Post by MTGap on 2009-11-05
I thought I did, what am I doing wrong?

---

### Post by korvirlol on 2009-11-05
The code you posted: 
[PHP]
foreach ($arr as $first) { 
    foreach ($first as $second) { 
[/PHP]

was from the example i gave you. if in fact this is what you are using it wont run.

---

### Post by MTGap on 2009-11-05
Well then can you explain to me how to get it to work?

---

### Post by korvirlol on 2009-11-05
your code:

[PHP]
foreach ($arr['ev_title'] as $key => $data) { [/PHP]

So, even though $arr is a multidimensional, you arent accessing a multi-dimensional array. 

The syntax of the foreach loop you have is, for every element i the array pointed to by $arr['ev_title'] the value is $data, and the key (which is ev_title) is $key.

so try to access the elements in your foreach loop as $data, and not as $arr['evstart'][$key]

---

### Post by MTGap on 2009-11-05
Okay well I get the following errors because of 'ev_title' (Which should be part of the array) 

Undefined index: ev_title
Invalid argument supplied for foreach()


So I've tried: 

[PHP]foreach ($arr as $key => $data) {[/PHP]

And: [PHP]".$data['ev_title']."[/PHP] etc... 

There are no errors and it outputs correctly but it only shows one of the arrays and not all 3.

---

