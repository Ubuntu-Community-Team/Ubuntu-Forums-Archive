---
title: "How to execute php code from an html form post action"
date: 2008-08-19
forum: Programming Talk
---

### Post by tc101 on 2008-08-19
On a php page, main.php, I have an html form with post method.  It starts out something like this:

<form method="post"  action="https://checkout.google.com/blah/blah/blah

In addition to doing the post to checkout.google.com, I would also like to execute some php code on main.php.  How do I code the form post action to do this?

I think what I am really asking is if there is a way to have 2 actions when you post a form, and how best to do that.

---

### Post by mike_g on 2008-08-19
If I understand you correctly then you might want to have the form post to main.php then redirect to google. you can redirect using:
```

//Do stuff
header("Location: http://someurl.com");
```

One issue with this is that you cant redirect after you start writing html. So you cant write an new form out in main an post it on automatically w/o drawing another page. 

If the data you are sending on is not sensitive then you could pass the data on in the url; something I did in the past to deal with the issue. Something like:
```
//Do Stuff
header("Location: http://someurl.com?something=".$_POST['something']);
```

---

### Post by cdenley on 2008-08-19
You could have the form POST to you, then the server post the data to google.

[http://us3.php.net/manual/en/function.http-post-fields.php](http://us3.php.net/manual/en/function.http-post-fields.php)

Something like
[php]
http_post_fields("https://checkout.google.com/blah/blah/blah",$_POST);
[/php]
I'm not sure if SSL will work with that function, though.

---

### Post by tc101 on 2008-08-20
I think http_post_fields is exactly what I need, but in the code below, I get an error message, 
Call to undefined function: http_post_fields()


<p>Recieve01<p>
<?php 
$item = $_POST['item_description_1'];
print $item; 
$resp = http_post_fields("recieve02.php",$_POST);  
?>

---

### Post by cdenley on 2008-08-21
Apparently that function is not compiled into php by default. You have to add it.
```

sudo apt-get install php5-dev curl libcurl4-gnutls-dev
pecl download http://pecl.php.net/get/pecl_http-1.6.1.tgz
sudo pecl install pecl_http-1.6.1.tgz

```
Then add "extension=http.so" to /etc/php5/apache2/php.ini, reboot apache.
There might be other dependencies I already had installed which I'm not aware of.

---

### Post by tc101 on 2008-08-21
This is being hosted on GoDaddy.  So does this mean that if GoDaddy hasn't installed it I can't use it?

---

### Post by cdenley on 2008-08-21
yes

---

### Post by tc101 on 2008-08-21
I have put in a support ticket to GoDaddy asking them if they have installed pecl.php.net.  Maybe I just need to use a php.ini to get it to work.  Right now I have no php.ini on my site.

But if I can't use http_post_fields(), is there another way, after posting from a form on one page to another page where I do some database stuff, to then post the data that came from the original form to checkout.google.com?

---

### Post by cdenley on 2008-08-21
I don't think there is a way of sending an HTTP post without the HTTP extension. I suppose you might be able to connect with fsockopen, then talk to the web server directly, but then it wouldn't use encryption.

An alternative would be to output a new form, possibly with hidden variables, that the user can then submit. Maybe you can have javascript submit it automatically, too.

---

### Post by tc101 on 2008-08-21
That sounds like a good idea and is probably what I will do unless I can get http_post_fields() to work.

---

### Post by tc101 on 2008-08-21
Well the support at GoDaddy is not great.  I asked this question:

[B][I]I am building a site using PHP.
pecl.php.net is an add on module that contains the function http_post_fields(). When I try to run code containing http_post_fields() on GoDaddy I get a message saying:

Call to undefined function: http_post_fields()

How can I use this in my PHP code running on GoDaddy?



[/I][/B]
and got this answer:

[I][B]Thank you for contacting Online Support.

It appears that this is a scripting issue as the function you are calling is not defined. Unfortunately we cannot provide technical support or assistance for any third party code, scripting or applications beyond ensuring proper connection strings are in place for database and hosting connectivity. You will need use an internet search engine or our Help Center to find more information concerning your issue(s).

Please let us know if we can assist you in any other way.


[/B][/I]

So I guess I'll go with the suggestion of having the form pass control to a new page where I will do all database processing and then build a new form using php and then have them press the button again.

---

### Post by mikejen on 2008-08-22
mmmmm had I known godaddy was involved id have stayed away!!!

anyhow post data from a form is a nightmare. none of your solutions work for me, this is what i have

form 1
<form enctype="multipart/form-data" action="subscribe1.php" method="post">
<p>
Name: <input type="text" id="aname" size="20" maxlength="40">
<p>
Email: <input type="text" id="anemail" size="20" maxlength="40">
<p>


<input type="submit">
</form>


press submit and it calls up subscribe1.php whis is as follows:

<?php

echo 'hi'; 
echo  $_POST['aname']; 
echo 'email';
echo  $_POST['anemail'];

?>

now can anyone tell me why i dont see any form data coming through?


cheers

michael (which would have been mikejenkinson.com but i mistakenly asked godaddy if it was available. they went out and bought it so not now available)

---

### Post by -grubby on 2008-08-22
> **mikejen said:**
> 
[..]
now can anyone tell me why i dont see any form data coming through?
[..]


the id= bit should be replaced with name=

---

### Post by cdenley on 2008-08-22
The "id" parameter on HTML input is only used for javascript. If you want to POST the data, you have to give it a name.

[HTML]
<form enctype="multipart/form-data" action="subscribe1.php" method="post">
<p>
Name: <input type="text" name="aname" size="20" maxlength="40">
<p>
Email: <input type="text" name="anemail" size="20" maxlength="40">
<p>


<input type="submit">
</form>
[/HTML]

---

### Post by Reiger on 2008-08-22
> **tc101 said:**
> On a php page, main.php, I have an html form with post method.  It starts out something like this:

<form method="post"  action="https://checkout.google.com/blah/blah/blah

In addition to doing the post to checkout.google.com, I would also like to execute some php code on main.php.  How do I code the form post action to do this?

I think what I am really asking is if there is a way to have 2 actions when you post a form, and how best to do that.

Two actions? If action X is to write stuff and action Y is to redirect -- then you can of course combine those in an anchor element.

Essentially you do the following:
[php]
<?php

$data='my formatted string';
$link='<a href="my formatted link">Continue to...</a>'
echo $data;
echo $link;
?>
[/php]
Encapsulated inside the rest of your output code...

But you may also want to let the JavaScript do the redirecting automagically on top of that too.

Created a quick rough version, tested in Opera 9.x:

[html]
<html>
<head>
<script type="text/javascript">
function redirect () {
	var elem=document.getElementById("redirect_link");
	var url=elem.href;
	window.location=url;
}
window.onload = function () {
	setTimeout('redirect();',5000);
}
</script>
<title>Magic redirection by JavaScript</title>
</head>
<body><div>
Observe the magic. Or just click: <a href="prime.hs" id="redirect_link">this link</a>!
</div>
</body>
</html>
[/html]

---

### Post by mikejen on 2008-08-23
Hi

Thank you all for noticing the id bit. it works now as expected.

what a frustrating thing programming is when your eye cant see whats staring you in the face.

again thanks

michael

---

