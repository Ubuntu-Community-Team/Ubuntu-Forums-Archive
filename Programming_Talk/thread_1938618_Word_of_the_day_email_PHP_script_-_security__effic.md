---
title: "Word of the day email PHP script - security / efficiency check"
date: 2012-03-10
forum: Programming Talk
---

### Post by East Asia Student on 2012-03-10
Hi all, would just like to ask for your expertise here.

I've written this PHP script which runs with cron to pick a line from a text file and send it as a "word of the day" email.

[PHP]<?php

//The name of the tab-separated text file containing the vocab list
$vocab_file = "path to text file";

//Read the vocab text file
$vocab_list = file($vocab_file); 

//Grab a random line from the vocab text
$todays_item_string = $vocab_list[array_rand($vocab_list)];

//Make that line into an array (tab separated)
$todays_item_array = explode("\t", $todays_item_string, 4);

//Get the details of today's word fromt that array
$word = $todays_item_array[0];
$reading = $todays_item_array[1];
$meaning = $todays_item_array[2];

//The information for the email
$recipient = "email address";
$subject = $word . " (" . $reading . "): " . $meaning;
$message = "
<html>
<head>
</head>
<body>
<p>Today's word of the day is <span style='font-size:x-large;'>" . $word . "</span> (" . $reading . "), which means " . $meaning . "</p>
<p style='font-size:7em; text-align:center;'>" . $word . "</p>
</body>
</html>";
$headers  = 'MIME-Version: 1.0' . "\r\n";
$headers .= 'Content-type: text/html; charset=utf-8' . "\r\n";

//Send the email with today's word
mail($recipient, $subject, $message, $headers);
?>[/PHP]Currently it works exactly as I wanted it to. What I'd like to ask here is:


[LIST]
[*]Could it be made more efficient?
[*]Is it secure?
[/LIST]
Regarding the security, I run the script from a folder not in www, and the .htaccess in that folder is:

```
Order Deny,Allow
Deny From All
Allow From localhost

```The vocab file is 644 and the script itself is 740. Any security concerns there?

I'd be really grateful for any help with this! :p

---

