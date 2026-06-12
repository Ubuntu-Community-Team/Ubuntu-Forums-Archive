---
title: "[SOLVED] [PHP] make seconds into minutes"
date: 2008-11-08
forum: Programming Talk
---

### Post by ELD on 2008-11-08
Basically i have a field people fill out that i want whatever number they put in to be turned into minutes, as currently if they stick "15" in obviously by defualt in time it would be seconds.

How would i multiply to minutes?

---

### Post by pp. on 2008-11-08
There are sixty (60) seconds to one minute. Was that the question?

---

### Post by s.fox on 2008-11-08
i would look at mktime

documentation can be found [here]("http://uk2.php.net/mktime")

EDIT: if you are totally stuck and clueless I have a complete working solution.

---

### Post by LaRoza on 2008-11-08
> **ELD said:**
> 
How would i multiply to minutes?

By 60, usually.

---

### Post by pp. on 2008-11-08
> **LaRoza said:**
> By 60, usually.

Or, rather, by 1/60.

---

### Post by gpsmikey on 2008-11-08
Actually, you **divide** seconds by 60 to get minutes.  Make sure you handle it as a float, not an integer or 15 seconds would come out to be 0 minutes instead of 0.25 :)

mikey

---

### Post by ELD on 2008-11-08
So can i not just times everything by 60 since that will actually be accurate in terms of seconds?

A note: i will be comparing it against a timestamp.

This is the current function which checks seconds, i wish to modify to check minutes.

```

function check_post_timer()
{
	global $db, $site_config;
	
	// make safe
	$member_id = $db->quote_smart($_SESSION['mid']);
	
	// get the members last post time
	$sql_timer = "SELECT `post_timer` FROM `members` WHERE `member_id` = {$member_id}";
	$query_timer = $db->query($sql_timer);
	$timer = $db->fetch_array($query_timer);
	
	// check that the time has passed for them to be able to post again
	
	// now
	$timedate = strtotime(gmdate("d-m-Y H:i:s"));
	
	// check difference
	$checker = $timedate - $timer['post_timer'];
	
	if ($checker >= $site_config['post_timer'])
	{
		return true;
	}
	
	else
	{
		return false;
	}
}

```

---

### Post by ELD on 2008-11-09
Any word on what i can do?

---

### Post by Tony Flury on 2008-11-09
if you have a time measurement in minutes then multiply by 60 to get that in seconds - it really is that simple.

if you have the measurement in seconds the divide by 60 to get minutes.

what else - apart from that - do you need to know ?

---

### Post by ELD on 2008-11-09
Well if i divide 15 seconds by 60 that gives me 0.25 but im pretty sure there is about 900 seconds in 15 minutes ;).

I think your saying it the wrong way round mate.

I am not working with timestamps btw, just simple actual numbers.

---

### Post by pp. on 2008-11-09
> **ELD said:**
> Well if i divide 15 seconds by 60 that gives me 0.25 but im pretty sure there is about 900 seconds in 15 minutes ;).

Your first post in this thread says that you have a number which is in seconds (15) and you wanted to compute how much that is in minutes. Since one minute usually has 60 (sixty) seconds, 15 seconds would indeed amount to one quarter of a minute. 

You calculate a time in minutes from a time in seconds by dividing the number of seconds by 60. That's because one minute has sixty seconds. You calculate a time in seconds from a time in minutes by multiplying the number of minutes by sixty.

---

### Post by tom66 on 2008-11-09
- Minutes to seconds: m * 60
 - Seconds to minutes: s / 60
 - Minutes to hours: m / 60
 - Hours to minutes: h * 60
 - Hours to seconds: h * 60 * 60 or h * 3600 

What else...?

---

### Post by ELD on 2008-11-09
> **pp. said:**
> Your first post in this thread says that you have a number which is in seconds (15) and you wanted to compute how much that is in minutes. Since one minute usually has 60 (sixty) seconds, 15 seconds would indeed amount to one quarter of a minute. 

You calculate a time in minutes from a time in seconds by dividing the number of seconds by 60. That's because one minute has sixty seconds. You calculate a time in seconds from a time in minutes by multiplying the number of minutes by sixty.

Yeah but i need it in actual seconds.
So for 15 minutes it will be 15 * 60.

All i needed was for someone to tell me to multiply whatever the number is by 60 and you get the seconds :P

---

### Post by pp. on 2008-11-09
> **ELD said:**
> All i needed was for someone to tell me to multiply whatever the number is by 60 and you get the seconds :P

:confused:

---

### Post by ELD on 2008-11-09
Look there are 60 seconds in 1 one minute right.

I was wondering how to get the seconds of any number of minutes put in, so i said "15", so you just do 60 * 15.

It was simple and i probably didn't make it out to be.

---

### Post by drubin on 2008-11-09
Please take a look at [http://dev.mysql.com/doc/refman/5.0/en/date-and-time-functions.html#function_date-format](http://dev.mysql.com/doc/refman/5.0/en/date-and-time-functions.html#function_date-format) you can do the formatting in sql.

---

### Post by ELD on 2008-11-10
It is not a sql issue, it is just a php comparing numbers issue.

---

### Post by arveeee on 2008-11-10
Do you even know php at all?
> 
<?php
$var=15;  //this is your input value

echo $var;              // display the input value. Will say: 15
echo "<br>";            // make upcoming text on a new line

$var=$var * 60;         // multiply the input value by 16

echo $var;              // display the variable again. This time it will say: 900

?>


Hopefully this example code will help you understand how to do what you're trying to do. Their input in minutes will be shown as seconds after the multiplication.

---

### Post by ELD on 2008-11-10
Yes i do know php thank you hence me showing the function i did before and i already said i know how to do it now (although if that was aimed at someone else sorry).

At least you actually understood what i wanted though, all i needed was to multiply by 60.

---

### Post by LaRoza on 2008-11-10
> **ELD said:**
> 
At least you actually understood what i wanted though, all i needed was to multiply by 60.

Well, I think we all got that (look at my first post), but that seemed...too obvious.

---

### Post by ELD on 2008-11-10
> **LaRoza said:**
> Well, I think we all got that (look at my first post), but that seemed...too obvious.

Ah yes so you did, just the people posting after you confused the crap out of me by saying different things heh.

Anyway this is solved now :), thanks everyone! :KS

---

