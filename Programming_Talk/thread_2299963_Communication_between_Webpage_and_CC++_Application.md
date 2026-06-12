---
title: "Communication between Webpage and C/C++ Application"
date: 2015-10-22
forum: Programming Talk
---

### Post by phil77 on 2015-10-22
Hi!

I have an Apache webserver running a webinterface (HTML/PHP/Javascript). I'd like to send some commands to a C/C++ application running on the same system as the webserver and also return the status of the application to the webinterface. There are very few commands to be sent, like "start measurement" or "calibrate". 

My only idea to handle this was with a text document where both the application and the webpage have access to and are able to share information. I don't like this solution because then i have to read and interprete the file frequently which makes the system slow.

I'm struggling to find any useful information about how to send information between the webpage and the application in a more direct way... I found something called CGI, would this be the right technology?

I don't need a step by step instruction but some keywords to google would be really helpfull!


Thanks!

---

### Post by nknwn on 2015-10-22
CGI is a way to go
Random tutorial:
[https://www.cs.tut.fi/~jkorpela/forms/cgic.html](https://www.cs.tut.fi/~jkorpela/forms/cgic.html)

---

### Post by ian-weisser on 2015-10-22
You can also try REST
Then your commands look something like htttp://my_server/do_something
And the http reply header (or page) includes the response.

REST can work using simple python; it doesn't require apache.

Be VERY CAREFUL allowing external connections to run commands on your machine.
SSH is often a safer and simpler way to use applications on a different machine. It, of course, does not use apache either.

---

### Post by SeijiSensei on 2015-10-23
You can use any of the various [program execution functions in PHP]("http://php.net/manual/en/ref.exec.php") to invoke a command-line program.  You do need to pay attention to permissions since the program will be run with the permissions Apache runs as, user and group "www-data".  But it's pretty easy to invoke a program, retrieve its output, and display it in a web page using PHP.  

Here's the example given for the basic shellexec() function which returns any output as a single string:
```

<?php
$output = shell_exec('ls -lart');
echo "<pre>$output</pre>";
?>

```
In essence, shellexec() works the same way as the backtick (`) or $() operator in bash. There are other functions that put the results into an array.

---

### Post by marcus_s on 2015-10-24
If you want to retrieve data from a server, you can also use the **cURL** library.

Tutorial and documentation for that:
[http://curl.haxx.se/libcurl/c/example.html](http://curl.haxx.se/libcurl/c/example.html)

---

