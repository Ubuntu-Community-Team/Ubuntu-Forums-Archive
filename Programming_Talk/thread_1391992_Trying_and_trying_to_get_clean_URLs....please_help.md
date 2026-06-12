---
title: "Trying and trying to get clean URLs....please help!"
date: 2010-01-27
forum: Programming Talk
---

### Post by gjoellee on 2010-01-27
My websites server did not have enough php memory to run drupal, therefor I decided to write the website by hand, but I will not start creating pages n' stuff before I get clean URL's. I have googled it, but I cannot find something that works.

-I use Apache
-My unclean URLs look like this [http://www.stupidreality.org/](http://www.stupidreality.org/)**?q=**example"

I don't really know if you need more info, so just ask :)

---

### Post by mikejonesey on 2010-01-27
if you are asking what an unclean url is, 

a clean url is short, descriptive and does not use the get method.

unclean urls are anything else;

using the following code will enable you to render pages via the index.php;

.htaccess
```

SetEnv APPLICATION_ENV development 
RewriteEngine On 
RewriteCond %{REQUEST_FILENAME} -s [OR] 
RewriteCond %{REQUEST_FILENAME} -l [OR] 
RewriteCond %{REQUEST_FILENAME} -d 
RewriteRule ^.*$ - [NC,L] 
RewriteRule ^.*$ index.php [NC,L]

```

index.php
```

<?php
header("content-type: text/html"); //the preffered page type
$uri=$_SERVER['request_uri'];
if($uri=="astringfromdb/")
{
include("code-base-for-page-type");
}
else
{
//no page like that
header(error..404/301 redirect codes go here);
exit();
}
?>

```

this enables you to easily render urls like [http://www.example.com/i-am-info.html](http://www.example.com/i-am-info.html) and [http://www.example.com/all-about-ubuntu.html](http://www.example.com/all-about-ubuntu.html)

---

### Post by gjoellee on 2010-01-27
Thanks...some issues though.

I get this error:
```
**Warning**:  Cannot modify header information - headers already sent  by (output started at  C:\Users\Cookie\Documents\xampp\htdocs\stupid\index.php:6) in **C:\Users\Cookie\Documents\xampp\htdocs\stupid\index.php**  on line **7**
```

this is line 7:
```
header("content-type: text/html"); //the preffered page type
```

I hardly know any PHP, so I don't know how to solve it.

---

### Post by Finalfantasykid on 2010-01-27
I have had that problem before when modifying cookie information.  I think I was able to fix it by moving the that php above the HTML header information.

---

### Post by gjoellee on 2010-01-27
> **Finalfantasykid said:**
> I have had that problem before when modifying cookie information.  I think I was able to fix it by moving the that php above the HTML header information.

That solved it...but I noticed one more thing that is even more serious...If I in example click on a link now nothing happens! I need o be able to "load pages into my index.php" to say it that way. I want to use relative links, but as it is now I can't. The 404 page does not work either. (Try [www.stupidreality.org]("http://www.stupidreality.org") and click on "Click here for more info" and see what happens...). The index.php looks like this now:

```
<?php header("Content-Type: text/html");
        $uri=$_SERVER['request_uri'];
        if($uri=="$q") {
            include("inc/main.php");
        }
        else {
                header(inc/404);
                exit();
        } 
?>

<head>
    <link rel="stylesheet" type="text/css" href="theme/style.css" />
</head>

<body>
</body>

<footer>
    <div id="footy">
        &copy; StupidReality.org 2009-2010
    </div>
</footer>

```Before I asked for clean URLs, it looked like this, and links wordet "that way":
```
<head>
    <link rel="stylesheet" type="text/css" href="theme/css/style.css" />
</head>

<body>
            <?php
                $q = $_GET['q'];
                if(!isset($q)) {
                    $q = "main";
                }
                
                include("$q.php");
            ?>
</body>

<footer>
    <div id="footy">
        &copy; StupidReality.org 2009-2010
    </div>
</footer>
```That code gave me what I wanted, except clean URL's and a 404 page.

I hope I did not confuse ya too much!

---

### Post by kamaji792 on 2010-01-27
Just a couple of things.

As you discovered the **header()** must be called before any HTML output is generated.

You say the page 404 does not work.
```

        else {
                header(inc/404);
                exit();
        }
```

I think that wants to be something like:
```

        else {
                header('Location: http://error_404.html');
                exit();
        }
```
Hope that helps if I have not got the wrong end of the stick.

[edit] Additionally the code at the top:
```

<?php header("Content-Type: text/html");
        $uri=$_SERVER['request_uri'];
        if($uri=="$q") {
            include("inc/main.php");
        }

```
The **if($uri=="$q")** - well **$q** has not been assigned a value, so that will always fail.  I think you are supposed to be checking that **$uri** is a valid file name.

In which case the **include(...);** line should be **include($uri);**

You could try **if( file_exists($uri) )**.  That is at least testing the there is a file.

I am hoping that I am not making a complete fool of myself.  I have only been playing around with PHP seriously for about a year (part-time).
[/edit]

---

### Post by gjoellee on 2010-01-27
> **kamaji792 said:**
> Lots of stuff....

I actually don't know if I've done it right accord to you, so take a look here:
```

<?php header("Content-Type: text/html");
        $uri=$_SERVER['request_uri'];
          if($uri=="$uri") {
            include("inc/main.php");
        }
        else {
                header('Location: http://stupidreality.org/404.html');
                exit();
        }
?>

```Still nothing...

If you go to [www.stupidreality.org](www.stupidreality.org) you will notice that the link gives you "another page", but it is just the same page without the css style. When the link is correct it is supposed to say "The link finally works!"

---

### Post by Hellkeepa on 2010-01-27
HELLo!

Oh, my... I think you both should read a bit more up on HTTP headers, and input validation. Oh, and both "clean" and "unclean" URLs (as you describe them) use the GET method. The "clean" variant is only different in that it uses Apache's RewriteEngine to generate the key-value pairs from non-existing URLs.

Then to the security issues:
[list=1][*]```
 if($uri=="$uri") {
```
This does absolutely nothing, it's like checking for 1 == 1. Or asking if you are you. In other words, it'll always return true.
What you want to use is the function "[is_file ()](http://www.php.net/is_file)" to check if the file exists before trying to include it.
[*]No validation of the page name, meaning a potential hacker can write _anything_ and get it included. This includes malicious code from third-party sites, or system files containing passwords.
[*]"REQUEST_URI" is not what you want here, especially not to try and include the file from it. Print it out to the console, and you'll see what I mean. Look again at the code you used before. The mod_rewrite method acts just the same as your old method, as far as the PHP-script is concerned.
[*]Always send the "404 Not Found" header when using your own error messages, otherwise all the search engines are told that the file does indeed exist. (They see "HTTP 200 OK".)[/list]
This is the method I use, to include files:
[php]// Retrieves and validates the page requested, only letters a-z are allowed. "main" is the default page.
$Action = ($Action = substr (strtolower (preg_replace ('([^a-zA-Z])', '', $_GET["action"])), 0, 20)) ? $Action : "main";

// Construct the path to the included file.
$File = "include/{$Action}.php";

// Show the 404 message if the requested page doesn't exist.
if (!is_file ($File)) {
    header ("404 Not Found");
    include ("404.html");
    die ();
}

// Include the file.
include ($File);

?>[/php]
Happy codin'!

---

### Post by gjoellee on 2010-01-28
I am using your code now, s this is m index.php:

```
<?php 
// Retrieves and validates the page requested, only letters a-z are allowed. "main" is the default page.
$Action = ($Action = substr (strtolower (preg_replace ('([^a-zA-Z])', '', $_GET["action"])), 0, 20)) ? $Action : "main";

// Construct the path to the included file.
$File = "inc/{$Action}.php";

// Show the 404 message if the requested page doesn't exist.
if (!is_file ($File)) {
    header ("404 Not Found");
    include ("inc/404.html");
    die ();
}

// Include the file.
include ($File);

?> 
 
<head>
    <link rel="stylesheet" type="text/css" href="theme/style.css" />
</head>
<body>
</body>
<footer>
    <div id="footy">
        &copy; StupidReality.org 2009-2010
    </div>
</footer>
```But, still there are issues:

[LIST]
[*]The 404 page does not work
[*]It does not look like the index.php applies to other pages than "main.php" as the CSS link (found in the index) does not apply on other pages. You will notice it if you click on the link at [www.stupidreality.org]("http://www.stupidreality.org").
[*]Relative links still does not work (kind of). I can't ie. use **<a href="index.php">Click me!</a>**. It will just add "index.php" on your URL.
[/LIST]

This is the code found on the link on the website:
```
<a href="inc/test">Click here for more info</a>
```


NOTE: My .htaccess looks like this now:
```
RewriteEngine On
RewriteRule ^([a-z]+)/([a-z\-]+)$ /$1/$2.php [L]
```

---

### Post by hessiess on 2010-01-28
Mixing up Logic and display code is error prone(as you have already found with the header problem), is hard to read and thus also hard to maintain.

If you want to do clean URLS you will inevitably end up handling all pages through a single entry point, the index.php file. In order to do this without making an unmaintainable mess of source code you need to place a dispatcher of some kind in front of a bunch of handler functions, one per page, which handle requests.

A dispatcher can be as simple as a (large) switch statement, a callback table or an object registry. Though at this point you are a third of the way towards implementing a simple MVC framework.

> 
Relative links still does not work (kind of). I can't ie. use <a href="index.php">Click me!</a>. It will just add "index.php" on your URL.

This is inevitable and, if you think about it, is doing exactly what relative URL's are suppose to do, address files relative to the current directory, regardless of the actual file layout on the server. The browser only sees the rewritten URL's. Basically ALL URL's have to be absolute, though you can generate the URL's server side to be relative to the current directory, allowing the code to work from a subdirectory or out of the root of a server with no change to the code.

---

### Post by Hellkeepa on 2010-01-28
HELLo!

I should probably have noticed that the above example is just a few lines from my MVC-based framework, and is in no way a complete example; It's just the bare essentials to showcase the general idea.
The rewrite engine also needs to send all requests to the index file, where the target is set to "index.php?action=$1". Also, the actual "include ()" line, from your code, should have been placed between the BODY-tags.

Your new .htaccess completely circumvents the use of a central index-file, and is based upon 1 complete file per viewable page. In and of itself a system that does work, but entails more work to maintain, and is more prone to errors. Mainly due to the mixing of business logic and display logic, as mentioned by **hessiess**, but also due to the seperation of the code into the HTML-structure of "header", "footer" and "body". (One function is spread over three different files, or more, in the worst case.)

Happy codin'!

---

### Post by gjoellee on 2010-01-28
Thanks for trying to help, but it got solved by a friend.

---

### Post by kamaji792 on 2010-01-28
OK, I am not sure I entirely get why clean URLs are a good idea.  But I thought I would have a go.

So on my test server I have **CleanURL/index.php**
```

<?php
$action = $_GET['ac'];

// Construct the path to the included file or display the main.
if ( ! isset($action) )
   $action = 'home';

$file = "Include/{$action}.php";

// Show the 404 message if the requested page doesn't exist.
if (!is_file ($file)) {
    header ("404 Not Found");
    include ("Include/404.html");
    die ();
}

// Display the file.
?>
<html>
<head>
<title>$action - This site</title>
</head>
<body>
<?php
include ($file); 
?>
</body>
</html>

```

I have a home page **CleanURL/Include/home.php**:
```
<h1>Home Page</h1>
<p>This is home page</p>
<p>Go to <a href="index.php?ac=page1">Page 1</a> page.</p>
<p>Go to <a href="index.php?ac=page2">Page 2</a> page.</p>
<p>Go to <a href="index.php?ac=not_a_page">non existant</a> page.</p>
```

I have a test page **CleanURL/Include/page1.php**:
```
<h1>Page 1</h1>
<p>This is page 1<p>
<p>Go to <a href="index.php">home</a> page.</p>
<p>Go to <a href="index.php?ac=page2">Page 2</a> page.</p>
```

I have (for completeness) a second test page**CleanURL/Include/page2.php**:
```
<h1>Page 2</h1>
<p>This is page 2<p>
<p>Go to <a href="index.php">home</a> page.</p>
<p>Go to <a href="index.php?ac=page1">Page 1</a> page.</p>
```

And finally to handle errors **CleanURL/Incluce/404.html**:
```
<html>
<head>
<title>404 Page not found</title>
</head>
<body>
<h1>Error 404 - Page not found</h1>
<p>Please contact... webmaster@this.com</p>
<p>Go to <a href="index.php">home</a> page</p>
</body>
</html>
```

Start by calling **[http://arwen/CleanURL/index.php](http://arwen/CleanURL/index.php)** and you are in.

Obviously big thanks to **Hellkeepa** who I cribbed the index.php page from (being a bear of small brain I did not understand the first line of code so I left it out, but I am working on it).

Hope this help or someone can point out what I am doing wrong.

**Bah! he's solved it** (note to self must type quicker)

Any way all the best

---

### Post by Hellkeepa on 2010-01-29
HELLo!

I can't see anything wrong in there, **Kamaji792**, other than that first line you left out. Which was perhaps the most important line of them all, as it was the entire security of the script. :-P
I've broken it up a bit, and used the full IF-syntax, so that it'll be easier to understand:
[php]// Ensure that only letters a-z are accepted as the filename, stops people from being able to include arbitrary files.
$Action = preg_replace ('([^a-zA-Z])', '', $_GET["action"]);

// Shorten down and make the input lower case, so that we don't have to worry about capitalization on top of everything.
$Action = substr (strtolower ($Action), 0, 20);

// If no data was sent, or passed the validation, make sure the content file for the index page is selected.
if (empty ($Action)) {
	$Action = "main"; 
}
[/php]

**gjoellee**: Do you think you could post what was wrong, and what you did to fix it? I'm sure lots of people will appreciate it, later on.

Happy codin'!

---

