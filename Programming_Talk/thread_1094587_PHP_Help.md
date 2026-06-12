---
title: "PHP Help"
date: 2009-03-12
forum: Programming Talk
---

### Post by unplugged23 on 2009-03-12
Hey guys,

I'm pretty new to PHP so I don't know a whole lot about it. Right now i have some PHP code on an html page that looks like this:
```
<p align=center><form action="includes/process.php?action=update" method="post">
```This is supposed to control the following text input box: ```
<input type="text" name="u" id="input" value="Enter Your Website's URL And Press Enter" class="urlinput" size="60">
``` And it does, the problem is, it needs something to do after the text box is updated and someone pushes enter. Now I have a PHP file (that someone else wrote) that I would like to use that looks like this: ```
<?php
// PHP Proxy
// Responds to both HTTP GET and POST requests
//
// Author: Abdul Qabiz
// March 31st, 2006
//

// Get the url of to be proxied
// Is it a POST or a GET?
$url = ($_POST['url']) ? $_POST['url'] : $_GET['url'];
$headers = ($_POST['headers']) ? $_POST['headers'] : $_GET['headers'];
$mimeType =($_POST['mimeType']) ? $_POST['mimeType'] : $_GET['mimeType'];


//Start the Curl session
$session = curl_init($url);

// If it's a POST, put the POST data in the body
if ($_POST['url']) {
	$postvars = '';
	while ($element = current($_POST)) {
		$postvars .= key($_POST).'='.$element.'&';
		next($_POST);
	}
	curl_setopt ($session, CURLOPT_POST, true);
	curl_setopt ($session, CURLOPT_POSTFIELDS, $postvars);
}

// Don't return HTTP headers. Do return the contents of the call
curl_setopt($session, CURLOPT_HEADER, ($headers == "true") ? true : false);

curl_setopt($session, CURLOPT_FOLLOWLOCATION, true); 
//curl_setopt($ch, CURLOPT_TIMEOUT, 4); 
curl_setopt($session, CURLOPT_RETURNTRANSFER, true);

// Make the call
$response = curl_exec($session);

if ($mimeType != "")
{
	// The web service returns XML. Set the Content-Type appropriately
	header("Content-Type: ".$mimeType);
}

echo $response;

curl_close($session);

?>

```The problem is, I don't know how to get the text box and this PHP file to work together to produce the results I want. I would like for the outcome to be a decent proxy. I figured this would be the best place to make this post. Any ways, thanks for any help, I am new to PHP! :D

---

### Post by bapoumba on 2009-03-13
Moved to PT.

---

### Post by lapubell on 2009-03-13
well for one thing, your input box is named 'u', and your variable in the php script is looking at the POST variables for one called 'url'.  So first, i think your variable names don't match.

second, you are passing a GET variable and POST variables in your form.
> 
<form action="includes/process.php?action=update" method="post">


that question mark just set $_GET['action'] to "update" which you probably don't need.  I ususally stick with one type or the other ($_GET or $_POST).

I would change your input box's name to "url" and try it again.

---

### Post by drubin on 2009-03-13
> **lapubell said:**
> that question mark just set $_GET['action'] to "update" which you probably don't need.  I ususally stick with one type or the other ($_GET or $_POST).

or $_REQUEST that looks at both get and post variables

---

