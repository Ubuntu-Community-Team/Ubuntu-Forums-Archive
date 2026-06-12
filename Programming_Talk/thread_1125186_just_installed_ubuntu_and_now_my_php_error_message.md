---
title: "just installed ubuntu and now my php error messages are gone"
date: 2009-04-14
forum: Programming Talk
---

### Post by Xenobug on 2009-04-14
Ok, I just installed intrepid ibex and apache, mysql and php and all that. works like a charm but now I'm not getting any error messages from php.

for example, if I have something like

```

$a = array()

```

I'm just getting a blank page.

If I have

```

$a = explode('',$a);

```

I'm getting no error message at all even though the page is generated just fine.

On my windows machine I'll get a parse error for the first and a warning about the missing declaration for $a for the second example. in ubuntu I'm getting nothing even though I set errors to E_STRICT and display_errors to "on" in my php.ini and phpinfo() shows that the settings are in effect indeed.

This really is a killer as I just can't go by logfiles to debug.

Any help would be appreciated.

---

### Post by Arndt on 2009-04-14
> **Xenobug said:**
> Ok, I just installed intrepid ibex and apache, mysql and php and all that. works like a charm but now I'm not getting any error messages from php.

for example, if I have something like

```

$a = array()

```

I'm just getting a blank page.

If I have

```

$a = explode('',$a);

```

I'm getting no error message at all even though the page is generated just fine.

On my windows machine I'll get a parse error for the first and a warning about the missing declaration for $a for the second example. in ubuntu I'm getting nothing even though I set errors to E_STRICT and display_errors to "on" in my php.ini and phpinfo() shows that the settings are in effect indeed.

This really is a killer as I just can't go by logfiles to debug.

Any help would be appreciated.

I don't have much to contribute, but how does the command line invocation of php behave? (Note that it uses a different php.ini.)

---

### Post by Xenobug on 2009-04-15
had to install php-cli for that, but it's not giving an error either...

---

### Post by Arndt on 2009-04-15
> **Xenobug said:**
> Ok, I just installed intrepid ibex and apache, mysql and php and all that. works like a charm but now I'm not getting any error messages from php.

for example, if I have something like

```

$a = array()

```

I'm just getting a blank page.

If I have

```

$a = explode('',$a);

```

I'm getting no error message at all even though the page is generated just fine.

On my windows machine I'll get a parse error for the first.



What parse error do you get, by the way? I don't get one for the first example, and it looks OK to me.

---

### Post by Sense on 2009-04-15
Do you have something at the next lines? If there's nothing there, there's nothing to conflict with.

---

### Post by Xenobug on 2009-04-15
*cough* guys, "$a = array()" is an unterminated command, it's missing the semicolon.

try

```

$a = array()
echo "test";

```

you will either get a parse error on line 1 (which is how PHP should behave) or just a blank page, which happens just in ubuntu and makes debugging impossible.

---

### Post by Arndt on 2009-04-16
> **Xenobug said:**
> *cough* guys, "$a = array()" is an unterminated command, it's missing the semicolon.

try

```

$a = array()
echo "test";

```

you will either get a parse error on line 1 (which is how PHP should behave) or just a blank page, which happens just in ubuntu and makes debugging impossible.

Yes, of course. I just naively copied the exact text and ran it, and since it was the only statement, it worked. But you have more code than that.

But what does the CLI version of PHP do in that case? Does it never say anything at all? Or can it execute and print the result of correct statements?

There is a debugger for PHP, but I haven't used it yet.

---

### Post by Sense on 2009-04-16
What happens if you call add the following statement before the line of code:
[PHP]error_reporting(E_ALL);[/PHP]

If it does show an error afterwards you could report a bug against Ubuntu because of the default error reporting level. Otherwise we need to dig deeper.

---

### Post by Xenobug on 2009-04-16
with

```

<?PHP
$a = array()
echo "test"
?>

```

PHP-CLI says "Parse error: syntax error, unexpected T_ECHO in /home/xenobug/Desktop/test.php on line 3".

When running the same file through the webserver, I get nothing. Adding error_reporting() doesn't yield anything.

---

### Post by Reiger on 2009-04-16
The problem may be in the webserver configuration (which could've been configured not to send errors). Incidentally, why are you using the uppercase PHP instead of the lowercase php for <?php ?>

---

### Post by Xenobug on 2009-04-16
how would the webserver block PHP error messages? after all, the webserver won't be able to tell error messages and valid html code appart...

other than that, I'm using <?PHP out of habit.

---

### Post by Xenobug on 2009-04-18
I'm still having this problem. Any chance you guys are going to help me to fix it? I'd hate going back to windows just because of such a minor issue, but I can't work like that. :(

---

### Post by simeon87 on 2009-04-18
> **Xenobug said:**
> I'm still having this problem. Any chance you guys are going to help me to fix it? I'd hate going back to windows just because of such a minor issue, but I can't work like that. :(

Did you check the web server configuration, like posted earlier? There may be a setting overruling the error_reporting() function.

---

### Post by Xenobug on 2009-04-18
can you be more specific on what I would be looking for? can't find anything in httpd.conf or sites-enabled that would look like it could be blocking error messages.

also, error messages like "Strict Standards: Non-static method fooclass::foofunction() should not be called statically in /home/xenobug/Desktop/www/foo/index.php on line 86" are getting through.

---

### Post by simeon87 on 2009-04-18
> **Xenobug said:**
> can you be more specific on what I would be looking for? can't find anything in httpd.conf or sites-enabled that would look like it could be blocking error messages.

I must say my knowledge on this is a bit rusty; some options that you could try (related to the configuration of the web server):

[LIST]
[*][Using php.ini to enable errors](http://www.washington.edu/computing/web/publishing/php-ini.html#display_errors)
[*][Use .htaccess to enable errors](http://support.easystreet.com/hosting/unix/dynamic-config.htm#phperror)
[/LIST]

---

### Post by Reiger on 2009-04-18
Try the following:
```

<?PHP error_reporting(E_ALL); something-very-wrong; echo 'A bunch of notices should have appeared above!'; ?>
<?php error_reporting(E_ALL); something-very-wrong; echo 'Similar bunch of notices are to be expected above!'; ?>

```

Save that as verywrong.php or some other *.php file in (a) your current www directory: /home/xeno*foo/
And in the default www directory of Apache 2 on Ubuntu: /var/www/

On /var/www/ I get:
```

Notice: Use of undefined constant something - assumed 'something' in /var/www/verywrong.php on line 1

Notice: Use of undefined constant very - assumed 'very' in /var/www/verywrong.php on line 1

Notice: Use of undefined constant wrong - assumed 'wrong' in /var/www/verywrong.php on line 1
A bunch of notices should have appeared above!
Notice: Use of undefined constant something - assumed 'something' in /var/www/verywrong.php on line 2

Notice: Use of undefined constant very - assumed 'very' in /var/www/verywrong.php on line 2

Notice: Use of undefined constant wrong - assumed 'wrong' in /var/www/verywrong.php on line 2
Similar bunch of notices are to be expected above!

```

---

### Post by Xenobug on 2009-04-18
ok, never mind, I'm an idiot. I didn't read the comment in php.ini about E_STRICT not thoroughly enough. I was assuming E_ALL is included in E_STRICT. well, it's not, so I have to do E_ALL|E_STRICT to get both.


sorry for wasting your time.

---

