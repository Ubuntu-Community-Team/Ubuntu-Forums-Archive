---
title: "PHP function to request web page without redirect?"
date: 2009-09-06
forum: Programming Talk
---

### Post by eXcentra on 2009-09-06
I'm trying to find a function that behaves like:
[PHP]
header("Location: http://example.com/script.php?submit=hello%20world");
[/PHP]
without the redirect, meaning that the function should send a request to a predefined url without redirecting. (Don't know if this makes sense or if I'm using the right terminology).

The function should behave like entering "[FONT="Courier New"]http://example.com/script.php?submit=hello%20world[/FONT]" into the browser, except that the action is done in the background... as opposed to [FONT="Courier New"]header()[/font] directly redirecting to that specific URL.

For example, let's say I made a script such that if I enter "[FONT="Courier New"]http://example.com/script.php?submit=hello%20world[/FONT]" into my browser, it'll do various things with the string (ie. submit to database, etc).

I have a separate [FONT="Courier New"]submit.php[/font] with a form and text input. And here is my problem:
I want to be able to type anything into the text input, and once I click the form's "submit," I want PHP to make a request to [FONT="Courier New"]http://example.com/script.php?submit=blahblahblah[/font], ie. I want PHP to emulate a user actually inputting the URL into their browser and going to that webpage to carry out various other PHP activities, except I want it done in the background.

ie. I could use [FONT="Courier New"]header()[/font] which does what I want, BUT it explicitly redirects the user to the webpage with the URL. I want PHP to do this discreetly, under the hood, in the background, without redirecting.

Any ideas?

---

### Post by Reiger on 2009-09-06
[php]
/* 
 * read file accepts any URL accepted by fopen()
 * what it does is reading from a handle returned by fopen()
 * then sending it to stdout: effectively streaming data 
 * 
 * you should do some http magic first to send appropriate MIME headers
 */
readfile("{$_GET['submit']}");
[/php]

---

### Post by januzi on 2009-09-06
AJAX

```

 function function_name( params ) {
     $.ajax({
   type: "GET",
   url: "file.php",
   data: "id="+id,
   success: function(msg){
      $("#id").html( msg ) ;
   }
 });
}

```

---

### Post by Mirge on 2009-09-06
> **januzi said:**
> AJAX

```

 function function_name( params ) {
     $.ajax({
   type: "GET",
   url: "file.php",
   data: "id="+id,
   success: function(msg){
      $("#id").html( msg ) ;
   }
 });
}

```

This assumes you already have jQuery included, btw.

---

### Post by Reiger on 2009-09-06
And it doesn't quite do everything "behind the scenes"... that is you must have a "hosting" website of sorts to "inject" the target data into.

---

### Post by credobyte on 2009-09-06
Why not to use curl library ? 

[php]$url = "http://www.domain.com/submit.php";
$postvar = "from=me&to=you";

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_FAILONERROR, 1);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);
curl_setopt($ch, CURLOPT_RETURNTRANSFER,1);
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS, $postvar);

$result = curl_exec($ch);
curl_close($ch);
[/php]

---

