---
title: "PHP debugger not properly configured"
date: 2011-03-21
forum: Programming Talk
---

### Post by Faoesch on 2011-03-21
So first of all what I did to configure my computer with apache I followed this tutorial: [ApacheMySqlPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

So, I would like to learn PHP and the problem is now that I made my program "Hello World!" and when I try to run it as a Weg Page it tells me that the requested URL could not be found and if I try to run it as a PHP Script it tells me:
[B]Error launching 'test(1)'

The session could not be started.
In order to generate debug information, please make sure that the debugger is properly configured as a php.ini directive.[/B]

So now I'm stuck with my Eclipse and an error message. I hope someone can help me.

Thanks in advance :)

---

### Post by SeijiSensei on 2011-03-21
Try 

```
sudo cp helloworld.php /var/www
```

Then open [http://localhost/helloworld.php](http://localhost/helloworld.php) in a browser.

To run PHP scripts from the command line, you need to install the php5-cli package.  Then you can use "php /path/to/helloworld.php" to see the results from the prompt.

---

### Post by Faoesch on 2011-03-21
Sorry to disappoint you but that didn't work at all. I think you misunderstood me as well. I wanted to open the PHP file from eclipse. When I want to open the file with PHP Web Page it goes to: [http://localhost/test/test.php](http://localhost/test/test.php) which I think is correct but it doesn't show me what I've done.

As well it doesn't show me the mistakes I've done. Because I'm new to PHP I don't know if I'm making something wrong from the beginning. Do I have to compile it first or is that automatically?

My programm:
```
<?php
echo "Hello World!";
?>
```

---

### Post by SeijiSensei on 2011-03-21
Let's start with some basics.  After that, you need to read some documentation.

PHP is a scripting language that is primarily designed for web applications.  When an HTTP server like Apache encounters a script with a .php extension, it invokes a parser (Apache's so-called "mod_php") that interprets the script.  Any output that is created, typically in the form of an HTML document, is sent to a client's web browser.

I have no idea how one would run a PHP script from within Eclipse. 

I write all my code using a text editor (jed in my case).  Suppose I create a file called script.php.  I'd then place the script in a directory served from Apache (by default on Ubuntu /var/www and its descendants) and then point my browser at [http://server.example.com/script.php](http://server.example.com/script.php).  The output displays in my browser.  Typically web developers construct HTML output, though it can also be plain text.

So your first task should be to get your Apache/PHP implementation up and running.  (The other alternative, as I said before, is to install the php5-cli package and run scripts from the command line with "php /path/to/script.php".)  When you get to the point where you can see the "It works!" page by browsing to your server's [http://localhost/](http://localhost/) URL, you're ready to move on to the next step of creating some PHP scripts and depositing them in a directory like /var/www so they can be served by Apache.

One extremely informative script that you should run early in your career is this one:

```
<?php phpinfo() ?>
```

You'll see an enormous array of information about PHP and many other features of the Apache server as well.

Here's a good place to start: [https://help.ubuntu.com/10.04/serverguide/C/web-servers.html](https://help.ubuntu.com/10.04/serverguide/C/web-servers.html)

BTW. your "Hello, world!" script itself is fine.  You need to focus on Apache and mod_php now.

---

### Post by Faoesch on 2011-03-22
Thanks for the help. It works now. Not really because of you but thanks for the time you invested to help me.
I had to update my eclipse and needed a plugin form zend. Now I can programm it with Eclipse and it shows me in the Window below what output it has.

Before I updated my eclipse the problem even there when I tried to copy the php file to the /etc/www. No idea why but now everything works as it should.

Thanks again and have a nice day :)

---

