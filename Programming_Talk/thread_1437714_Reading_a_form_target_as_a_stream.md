---
title: "Reading a form target as a stream"
date: 2010-03-24
forum: Programming Talk
---

### Post by Raff1 on 2010-03-24
Hey! I am playing around with php and forms. I am currently sending information from myPage.php to externalPage.php:
```
<FORM action="externalPage.php" method="post">
```
On submit I get moved to externalPage.php where the processed form input appears.

What I would like to do is to receive the page source of externalPage.php as a stream I can read with fopen() either in myPage.php or perhaps myPage2.php. Opening externalPage.php in a new tab and get the steam from there is a less favorable solution, but I will settle for that if needed.

I hope someone can help me out with this, as I need to process the information I get back from externalPage.php automatically :p

Thanks

---

### Post by januzi on 2010-03-24
You could use .ajax from jQuery and curl. There will be three steps:
1. (at the form) onsubmit="send_form(this); return false;" 
2. (at the script) 
```

function send_form( form ) {
$.ajax({
   type: "POST",
   url: "some.php",
   data: "name=John&location=Boston",
   success: function(msg){
     alert( "Data Saved: " + msg );
   }
 });
}

```[FONT=Verdana]
3. some.php:
a) get data from $_POST and create a string 'postfields': key=value&key2=value2...
b) $c = curl_init() ;
c) curl_setopt (url + post + postfields + returntransfer)
d) $page = curl_exec($c)[FONT=monospace];
[FONT=Verdana]e) [/FONT][/FONT][/FONT]echo $page; ( == msg)

---

### Post by Raff1 on 2010-03-25
Thanks for your reply, but I am afraid both ajax, curl and stuff is unfamiliar concepts to me. I was hoping there was possible to do this using php.

So, using the mention method, I need to send the form from a page utilizing ajax, and redirect it somehow using curl to a php page where I can read the stream?

I am afraid the method you scetched up was a bit compact for me. I will however try to look into the keywords you gave me, and ajax and this curl business. Thanks again for your reply!

Oh, and I have no control over the external page at all by the way. I am a bit unsure if you meant is should implement some stuff there as well?

I also wonder how one can extract info from another open tab in your browser using php and fread. :p

---

### Post by januzi on 2010-03-25
> **Raff1 said:**
> Thanks for your reply, but I am afraid both ajax, curl and stuff is unfamiliar concepts to me. I was hoping there was possible to do this using php.

[http://www.php.net/manual/pl/curl.examples-basic.php](http://www.php.net/manual/pl/curl.examples-basic.php)

> 
So, using the mention method, I need to send the form from a page utilizing ajax, and redirect it somehow using curl to a php page where I can read the stream?

Yep.

> 
Oh, and I have no control over the external page at all by the way. I am a bit unsure if you meant is should implement some stuff there as well?

[http://pl2.php.net/manual/pl/simplexml.examples-basic.php](http://pl2.php.net/manual/pl/simplexml.examples-basic.php) (it should work with html)

---

### Post by Raff1 on 2010-04-03
I am starting to see what this is about now. This cURL busyness is about executing an url without opening the page and saving its contents in a variable I can use afterwards. Very handy, and juts the thing I need indeed. :)

> a) get data from $_POST and create a string 'postfields': key=value&key2=value2...
b) $c = curl_init() ;
c) curl_setopt (url + post + postfields + returntransfer)

Hmm... I think you will have to be more literate on the c) statement. url + post + postfields + returntransfer ..?

What I have used so far is:
```
$url = "http://itgk.idi.ntnu.no/oving/oving2a/prosesserskjema.php";
$postfields = "key=banana&key2=apple&key3=fox";

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
$output = curl_exec($ch);

```

Can you be entitely spesific about how the argument of the curl_setopt() should look like? I don't know how I can formulate the url + post + postfields + returntransfer thing.

If I get this right, then the parameters from $postfields will be sent to $url and be processed.

Thanks for your time :P

---

### Post by new_tolinux on 2010-04-03
Is this some kind of homework assignment?

It's normal to get your info in variables, like there's a line in myform.html:
```
<INPUT TYPE="TEXT" NAME="place" SIZE="30">
```And read that in [FONT=monospace]e[/FONT]xternalPage.php like:
[php]$place=$_POST["place"];[/php]or (more correct) :
[php]IF ($_POST["place"] != "") {
$place=$_POST["place"];
}
else {
$place="Unknown";
}[/php]After that you can do "as much as you like" with the input, before displaying any HTML that uses (or not uses) the input from myform.html

You can even combine "myform.html" and "myform.php" into one (myform.php) by using:
[php]IF $_POST["somefield"] != "") {
//do something with the information send through the form
}
else {
//present the form
}[/php]

---

### Post by januzi on 2010-04-03
Take a look at the [http://php.net/manual/en/function.curl-setopt.php](http://php.net/manual/en/function.curl-setopt.php) and search for the **CURLOPT_POST** and **CURLOPT_POSTFIELDS**. As for postfields You could use normal array: $postfields = array( 'key' => 'value', 'key2' => 'value2' ) ;

---

### Post by Raff1 on 2010-04-04
Hmm, I seem to have confused you, because I am well aware off everything in your post, new_tolinux. It isnt fetching the parameters which is the problem.

The only reason I do this directly:
[php]$postfields = "key=banana&key2=apple&key3=fox";[/php]
is to test a bit without the hassle of making an actual form. 

And no, this isn't a homework assignment ;) It is a subtask i need to accomplish in able to get a bigger application to run on my homepage.

What I want to test, is if I can send the parameters over to the page in $url utilizing the curl_setopt(). What was suggested was:
> c) curl_setopt (url + post + postfields + returntransfer).

I took a peek at the dokumentation as suggested by januzi:
> Take a look at the [http://php.net/manual/en/function.curl-setopt.php](http://php.net/manual/en/function.curl-setopt.php) and search for the CURLOPT_POST and CURLOPT_POSTFIELDS. As for postfields You could use normal array: $postfields = array( 'key' => 'value', 'key2' => 'value2' ) ;

And I see now that what he meant by curl_setopt (url + post + postfields + returntransfer), is actually that I need to use SEVERAL curl_setopt() statements. I wish this had been made clear much earlier, cos I interpreted those + in a much more literate manner. I will do some more testing now and come back with my progress. ^^

---

### Post by new_tolinux on 2010-04-04
> **Raff1 said:**
> Hmm, I seem to have confused you, because I am well aware off everything in your post, new_tolinux. It isnt fetching the parameters which is the problem.
////
You did confuse me and it's still confusing me a bit.
But I'm sorry that I've asked you if it's a homework-assignment, since it looked to me as "doing the simple things the hard way", which is in most cases..... homework.

---

### Post by Raff1 on 2010-04-04
Thanks for all you help! Looks like I got all I need now. I implemented the principles in this test script, where the target is in $url and the form sends back to itself before sending to the real target. The output from the external page is stored in $output so I can use it further to extract the information I need. the cURL framework is excellent! I appreciate your help januzi. :)

**test.php**
[php]
<?php

$url = "http://itgk.idi.ntnu.no/oving/oving2a/prosesserskjema.php";

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_POSTFIELDS, $_POST);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
$output = curl_exec($ch);
curl_close($ch);

print "$output <br/>";

?>

<form action = "test.php" method = "post">

<input type = "text" name = "foo" />
<input type = "text" name = "bar" />
<input type = "submit" />

</form>
[/php]

> You did confuse me and it's still confusing me a bit.
But I'm sorry that I've asked you if it's a homework-assignment, since it looked to me as "doing the simple things the hard way", which is in most cases..... homework.

No problem :-) And the target of $url is actually from an old homework exercise I had ages ago :P Its a generic form target which will display all the form parameters and values, which is perfect for my test purposes ;) I will try to implement this principle in my real application now. ^^

Cheers!

---

### Post by Raff1 on 2010-04-04
I managed to implement it now, but it doesn't work because the site i submit information to uses javascripting. All I get as output is:

```

		<HTML>
		<HEAD>
		</HEAD>
		<SCRIPT language="javascript">
		function init(loc)
		{
			top.location=loc;
		}
		</SCRIPT>
		<BODY onload="init('login.php');">
		</BODY>
		</HTML>

```

The information I need will be displayed once the body loads properly. Also, when the body has loaded, this is what gets displayed when I view the source code. How can I get access to the actual information that get generated in the body eventually? :S

---

### Post by januzi on 2010-04-04
Submit data to the form's destination or to the login.php.

---

### Post by Raff1 on 2010-04-04
> **januzi said:**
> Submit data to the form's destination or to the login.php.

Sending to login.php instead of kgb.php was completely fruitless. When I send from the my form to the external page, [www.external.net/kgb.php](www.external.net/kgb.php), all the information I need is displayed and all is well. The page source of the resulting page I watch is the same as what I fetched using cURL:

```
<HTML> 
<HEAD> 
</HEAD> 
<SCRIPT language="javascript"> 
function init(loc)
{
	top.location=loc;
}
</SCRIPT> 
<BODY onload="init('login.php');"> 
</BODY> 
</HTML> 
```

There should be a way to see the code of what the browser obviously sees and is able to display when running "init('login.php');". When I view source, I dont see it, and I obviously don't save the text I am really interrested in in my $output either. I googled a bit around, and it seems this problem isnt exactly trivial. Expecially not when I do not know a lot about the finesses of JS myself.

Any other suggestions? :D

---

### Post by januzi on 2010-04-04
So, you have to be like a browser:
1. get headers (look for session id and cookie) from the curl 
2. use those headers to fetch page

Example:
There is a form at the page. You put nickname and password and click the submit button. The browser goes to the "action" with the nickname=x&password=y... . It gets several strings: headers and page source. There are cookie "logged_in" and header "location". The browser saves cookie information and goes to the specified location. This time it is using cookie data. PHP scripts checks $_COOKIE and finds that there is a "logged_in" cookie with acceptable value. The browser gets page source as a logged user.

---

### Post by Raff1 on 2010-04-29
> **januzi said:**
> So, you have to be like a browser:
1. get headers (look for session id and cookie) from the curl 
2. use those headers to fetch page

Example:
There is a form at the page. You put nickname and password and click the submit button. The browser goes to the "action" with the nickname=x&password=y... . It gets several strings: headers and page source. There are cookie "logged_in" and header "location". The browser saves cookie information and goes to the specified location. This time it is using cookie data. PHP scripts checks $_COOKIE and finds that there is a "logged_in" cookie with acceptable value. The browser gets page source as a logged user.

I investigated further into headers and cookies.
This is the relevant part of my code atm, where $url is the external page, and I have added _FOLLOWLOCATION and _HEADER as TRUE since last.
```

	$ch = curl_init();
	curl_setopt($ch, CURLOPT_URL, $url);
	curl_setopt($ch, CURLOPT_POSTFIELDS, $_POST);
	curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
	curl_setopt($ch, CURLOPT_FOLLOWLOCATION, TRUE);
	curl_setopt($ch, CURLOPT_HEADER, TRUE);

	$cont = curl_exec($ch);
	$len = strlen($cont);
	curl_close($ch);

	$myFile = "test.txt";
	$fh = fopen($myFile, 'w') or die("can't open file");
	fwrite($fh, $cont);
	fclose($fh);

```

_FOLLOWLOCATION yealed no difference at all, and _HEADER just added the top information here:

```

TTP/1.1 100 Continue

HTTP/1.1 200 OK
Date: Thu, 29 Apr 2010 15:07:50 GMT
Server: Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny8 with Suhosin-Patch mod_ssl/2.2.9 OpenSSL/0.9.8g
X-Powered-By: PHP/5.2.6-1+lenny8
Expires: Mon, 26 Jul 1997 05:00:00 GMT
Last-Modified: Thu, 29 Apr 2010 15:07:50 GMT
Cache-Control: no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 182
Content-Type: text/html

		<HTML>
		<HEAD>
		</HEAD>
		<SCRIPT language="javascript">
		function init(loc)
		{
			top.location=loc;
		}
		</SCRIPT>
		<BODY onload="init('login.php');">
		</BODY>
		</HTML>

```

None of this is particularily useful, so I dont see how headers can get my any further in getting the generated code. I checked out the relevant cookies. They seemed to contain only "boring" information like SESSION_ID, and some other integers to keep track of my login. I doubt i will get anything useful from that either. I hope I am wrong.:P

So I at a loss when it comes to extracting the generated source code. I understand that it is executed and derived locally at my own computer, and that being part of the reason why its so complicated. But the browser evetually sees the information, and so should my script as well is what I am thinking.

---

