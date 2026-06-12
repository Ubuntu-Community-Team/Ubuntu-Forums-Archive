---
title: "PHP Globals and Values"
date: 2011-06-06
forum: Programming Talk
---

### Post by bcn17 on 2011-06-06
I am building a website utilizing minimal PHP. My first application was using includes. I have inserted the following inside various elements such as <nav></nav> to streamline website wide changes.

```
<?php include($_SERVER['DOCUMENT_ROOT']."/static/nav.php"); ?>
```

As you can see, I also used the Global variable (Not sure if that is precisely correct terminology) when "including" my 'nav.php' file. At first I was just using relative links. But then I decided it would be a lot easier if I could just do everything in relation to root. Then I discovered the HTML, CSS, and PHP think of different directories as root. 

I believe that PHP considers '/' the actual root directory on the server, while HTML and CSS use the domains root directory (or the directory that the file being executed is in?) 

Anyway, utilizing the $_SERVER['DOCUMENT_ROOT']. text works, although I wasn't sure why it wasn't like this:
> <?php include("$_SERVER['DOCUMENT_ROOT']/static/nav.php"); ?>

Note that I dropped the '.' and put the $_SERVER['DOCUMENT_ROOT'] inside the quotes with the /static/nav.php. 

This seems much more intuitive to me, consider that I figured it would just substitute the text '/var/www' directly for the $_SERVER['DOCUMENT_ROOT']. 

What is the '.' for and why does it have to be outside the quotes??

Also, I wasn't able to get this method to work when the include was inside carrots. For instance. I have an include link to 'links.php' 

The 'links.php' file looks like such: 

```
<link rel="stylesheet" type="text/css" href="<?php include(root_path); ?>/css/reset.css" />
<link rel="stylesheet" type="text/css" href="<?php include(root_path); ?>/css/master-style.css" />
<link rel="icon" type="image/png" href="<?php include(root_path); ?>/images/blue.png" />
```

I could not make the previous server-'document_root' method work inside the <link /> element. But after creating an .htaccess file and adding the line:

```
php_value root_path "/var/www"
```

I was able to make it work.

I don't understand why I couldn't use the first method. This was the only way I could get this to work. Additionally, I couldn't use this method in the first scenario because it would involve putting an include inside an include. 

Do I need to use both of these methods depending on the circumstances, or should I be able to utilize just one? 

Any knowledge you would care to share on these topics, what is actually happening, what you recommend etc would be greatly appreciated!

---

### Post by SeijiSensei on 2011-06-06
$_SERVER is an array of information provided by the web server software, Apache in this case.  I recommend creating a page that consists solely of the command

```
<? phpinfo() ?>
```

If you put this code into something like "info.php" and view it with a browser, you'll see a vast array of information about your server and its PHP settings.

$_SERVER['DOCUMENT_ROOT'] refers to the contents of the DocumentRoot directive in the <VirtualHost> container for a particular site.  By default in Ubuntu the DocumentRoot is "/var/www" as defined in /etc/apache2/sites-enabled/000-default.

Next, I suggest dumping $_SERVER['DOCUMENT_ROOT'] entirely and just defining a PHP variable that specifies the location of the included file(s).  Something like:

```

# note the trailing slash at the end
$includes="/path/to/include/directory/";

```

Then you can use "include($includes."script.php")" rather than the clunkier SERVER definition.  I usually keep all my code outside the DocumentRoot, so I define a custom include directory in every script I write.

The dot is the concatenation operator connecting two strings.  The code $includes."script.php" means take the contents of $includes and prepend it to "script.php".  You'll find yourself using the dot more and more if you do much PHP scripting.

I believe the reason "$_SERVER['DOCUMENT_ROOT']/script.php" doesn't work is that the parser can't determine that the string is supposed to be a concatenation.  I discovered this problem years ago, and now regularly use include($something."script.php") out of habit.

The term "[globals]("http://www.php.net/manual/en/language.variables.scope.php")" refers to any variable that is available to both the main script and to any functions defined within that script via the "globals" command.  Anything like "$includes" is a global; all the globals are also accessible in the $GLOBALS array which is defined automatically.  So both $includes and $GLOBALS['includes'] contain the identical value.  Things like $_SERVER are also global.  PHP calls these "[superglobals]("http://www.php.net/manual/en/language.variables.superglobals.php")" to distinguish them from ordinary globals like $var.  Superglobals are available even in class libraries, though ordinary globals are not.

Hope this helps!

---

### Post by Petrolea on 2011-06-06
As SeijiSensei already said, the dot ('.') operator is for "putting stuff together".

For example:
[PHP]echo "Hello" . " " . "world!";[/PHP]

would print "Hello world!" (without quotes of course).

In Java you would use '+' operator, in C++ '>>' and so on.

---

### Post by bcn17 on 2011-06-09
> **SeijiSensei said:**
> $_SERVER is an array of information provided by the web server software, Apache in this case.  I recommend creating a page that consists solely of the command

```
<? phpinfo() ?>
```

If you put this code into something like "info.php" and view it with a browser, you'll see a vast array of information about your server and its PHP settings.

$_SERVER['DOCUMENT_ROOT'] refers to the contents of the DocumentRoot directive in the <VirtualHost> container for a particular site.  By default in Ubuntu the DocumentRoot is "/var/www" as defined in /etc/apache2/sites-enabled/000-default.

Next, I suggest dumping $_SERVER['DOCUMENT_ROOT'] entirely and just defining a PHP variable that specifies the location of the included file(s).  Something like:

```

# note the trailing slash at the end
$includes="/path/to/include/directory/";

```

Then you can use "include($includes."script.php")" rather than the clunkier SERVER definition.  I usually keep all my code outside the DocumentRoot, so I define a custom include directory in every script I write.

The dot is the concatenation operator connecting two strings.  The code $includes."script.php" means take the contents of $includes and prepend it to "script.php".  You'll find yourself using the dot more and more if you do much PHP scripting.

I believe the reason "$_SERVER['DOCUMENT_ROOT']/script.php" doesn't work is that the parser can't determine that the string is supposed to be a concatenation.  I discovered this problem years ago, and now regularly use include($something."script.php") out of habit.

The term "[globals]("http://www.php.net/manual/en/language.variables.scope.php")" refers to any variable that is available to both the main script and to any functions defined within that script via the "globals" command.  Anything like "$includes" is a global; all the globals are also accessible in the $GLOBALS array which is defined automatically.  So both $includes and $GLOBALS['includes'] contain the identical value.  Things like $_SERVER are also global.  PHP calls these "[superglobals]("http://www.php.net/manual/en/language.variables.superglobals.php")" to distinguish them from ordinary globals like $var.  Superglobals are available even in class libraries, though ordinary globals are not.

Hope this helps!

Thank you so much for the response. The <? phpinfo() ?> command is really cool! 

In regards to php variables, I am having trouble defining a variable in the manner you described. If I want to define and call a variable in the manner you described, after some googleing I figured I needed to do something like this.

```
<?php
$includes = "/includes/directory/";
?>

```

However, I don't know where to put this code. It doesn't seem to work in .htaccess (without the <?php ?> of course). And, I can't use an include to put this script in the <head></head> elements (if that would even work) because I wan't my include to use the variable, and that would create a circular scenario. 

I read about a php.ini file. But apparently these need to be in each directory. I need to somehow create my path directory variable in a single file, and have the variable be callable in at least two settings. The first being inside an include like this:
```

<element>
<? php include($includes."/static/something.php") ?;>
</element>

```

And the second something like this:
```
<link rel="stylesheet" type="text/css" href="<?php include($includes."/css/reset.css"); ?>"  
```

However, neither of these options is working for me  using the .htaccess line: ```
php_value includes "/var/www"
``` 

I just can't figure out how to set a variable that will be recognized anywhere the string is found. Something I can call useing the $ symbol.

Additionally, on my local machine I can change what ever I want, however on my webhosting server I am only privy to a particular directory inside /home, so I won't be able to edit all files.

---

### Post by Petrolea on 2011-06-09
> **bcn17 said:**
> Thank you so much for the response. The <? phpinfo() ?> command is really cool! 

In regards to php variables, I am having trouble defining a variable in the manner you described. If I want to define and call a variable in the manner you described, after some googleing I figured I needed to do something like this.

```
<?php
$includes = "/includes/directory/";
?>

```

However, I don't know where to put this code. It doesn't seem to work in .htaccess (without the <?php ?> of course). And, I can't use an include to put this script in the <head></head> elements (if that would even work) because I wan't my include to use the variable, and that would create a circular scenario. 

I read about a php.ini file. But apparently these need to be in each directory. I need to somehow create my path directory variable in a single file, and have the variable be callable in at least two settings. The first being inside an include like this:
```

<element>
<? php include($includes."/static/something.php") ?;>
</element>

```

And the second something like this:
```
<link rel="stylesheet" type="text/css" href="<?php include($includes."/css/reset.css"); ?>"  
```

However, neither of these options is working for me  using the .htaccess line: ```
php_value includes "/var/www"
``` 

I just can't figure out how to set a variable that will be recognized anywhere the string is found. Something I can call useing the $ symbol.

Additionally, on my local machine I can change what ever I want, however on my webhosting server I am only privy to a particular directory inside /home, so I won't be able to edit all files.

Session variables can be accessed everywhere. Look them up.

---

### Post by v8YKxgHe on 2011-06-09
> Session variables can be accessed everywhere. Look them up.

That's really not a good idea for what he's wanting to do.

bcn17, why do you even need this var? How often do you plan on even changing your directory structure? Read [http://php.net/include](http://php.net/include) to understand how PHP will find the file you're wanting (you don't need to give it an absolute path)

> However, I don't know where to put this code. It doesn't seem to work in .htaccess (without the <?php ?> of course). 

This shows you need to step back and go back to even more basics. .htaccess is an Apache feature that lets you tweak the server configuration, it has 100% nothing to do with PHP so of course putting PHP code in this file will just result in an internal server error within Apache.

I suggest you read through [http://devzone.zend.com/article/627](http://devzone.zend.com/article/627) and the PHP manual before you continue.

---

### Post by roccivic on 2011-06-09
> **bcn17 said:**
> Anyway, utilizing the $_SERVER['DOCUMENT_ROOT']. text works, although I wasn't sure why it wasn't like this:

Note that I dropped the '.' and put the $_SERVER['DOCUMENT_ROOT'] inside the quotes with the /static/nav.php. 
> <?php include("$_SERVER['DOCUMENT_ROOT']/static/nav.php"); ?> 
This seems much more intuitive to me, consider that I figured it would just substitute the text '/var/www' directly for the $_SERVER['DOCUMENT_ROOT']. 

What is the '.' for and why does it have to be outside the quotes??


You can use curly brackets to delimit variables in a double quoted string, for example this will work as expected and include the correct file:
[PHP]<?php include("{$_SERVER['DOCUMENT_ROOT']}/static/nav.php"); ?> [/PHP]

This is not only useful with arrays but also with plain variables, for example:
[PHP]<?php
  $myvar = "Hello ";
  echo "{$myvar}World";
?>[/PHP]
will print:
```
Hello World
```

but
[PHP]<?php
  $myvar = "Hello ";
  echo "$myvarWorld";
?>[/PHP]

will print nothing and throw an "Undefined variable $myvarWorld" E_ALL 'notice' exception.

On an unrelated note, include is not function call, but a language construct so
[PHP]
<?php
  include("myfile.php");
?>
[/PHP]
and
[PHP]
<?php
  include "myfile.php";
?>
[/PHP]
are actually equivalent.

Rouslan

---

### Post by Petrolea on 2011-06-10
> **AlexC_ said:**
> That's really not a good idea for what he's wanting to do.


I was just answering the question :). But really, why not just use plain include?

---

### Post by holes88 on 2011-07-15
Yeah I would use php_info(); or use include('');

---

