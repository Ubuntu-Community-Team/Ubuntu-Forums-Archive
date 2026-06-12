---
title: "Problem with .htaccess"
date: 2009-08-15
forum: Programming Talk
---

### Post by cosmin86200 on 2009-08-15
Hey guys..

I have a problem with a apache-php-mysql server.

I have a php project, and my biggest issue is that I want the links to be structured like:
**domain_name.com/variable1/variable2/variable3/variable4**

PHP doesn't see those variables in .htaccess.

Any ideas?

---

### Post by Mirge on 2009-08-15
use mod_rewrite

---

### Post by cosmin86200 on 2009-08-15
mod_rewrite is enabled and working. I modified that allowoverwrite directive too.

It still doesn't work..

---

### Post by v8YKxgHe on 2009-08-15
> PHP doesn't see those variables in .htaccess.

What variables? PHP has 100% nothing to do with .htaccess. You're simply rewriting the URL via mod_rewrite using rewrite rules in ***Apache***. For example, changing 'foo/bar/car' into 'index.php?a=foo&b=bar&c=car', or 'index.php?url=foo/bar/car' etc etc.

You then use PHP to do what ever you want with those values.

---

### Post by cosmin86200 on 2009-08-15
Thanks for reply... That's actually my problem.

It isn't changing 'foo/bar/car' into 'index.php?a=foo&b=bar&c=car', becouse PHP doesn't read the $_GET variables from server.

For example, for 'foo/bar/car', my $_GET array is empty.

I know what .htaccess and mod_rewrite mean, sorry if I am not clear with my problem.

Any ideeas where the problem is?

---

### Post by v8YKxgHe on 2009-08-15
What are the rewrite rules you're using?

---

### Post by cosmin86200 on 2009-08-15
here's my .htaccess file till now:
RewriteEngine On
RewriteBase /rts_game/

#SETTLEMENT
RewriteRule ^settlement/(.*)$ settlement.php?settlement=$1 [N,L]
RewriteRule ^settlement$ settlement.php [N,L]
RewriteRule ^choose_settlement$ choose_settlement.php [N,L]

---

### Post by v8YKxgHe on 2009-08-15
ok, and do these rewrite rules? i.e going to 'settlement/foobar' takes you to the page you want?

Edit: btw, you have some random spaces in your rules:

> $4&a ction=$5&offer_id=$6 [N,L]
> $3&actio n=$4 [N,L]

---

### Post by cosmin86200 on 2009-08-15
"btw, you have some random spaces in your rules:" - these spaces are added from this forum's editor... they are correct in the .htaccess file, without spaces.

"settlement/foobar" - no, becouse the variable 'foobar' isn't read by php.

going only to 'settlement' on the other hand, will work, and will access the settlement.php page.

every link that has the format: page/var1/var2 doesn't work...

if I will change the slash with other character, for example: page-var1-var, works perfectly.

I don't know why this is happening, but I had this problem in the past on ubuntu...

I'm curious why this is happening...

Any advices?

---

### Post by v8YKxgHe on 2009-08-15
> "settlement/foobar" - no, becouse the variable 'foobar' isn't read by php.

There is no variable foobar anywhere. which is correct. What actually happens when you go to 'settlement/foobar' is more what I wanted to ask I guess.

Try changing the (.*) to (.*?), since .* is a greedy match (at least in PCRE, and IIRC, Apache also uses PCRE).

Edit: Nevermind, I see your issue most likely. Why are you using both N and L ([N,L])? I assume you really mean 'NC', which makes the rule case insensitive. That is probably confusing the thing. You'll mostly want '[NC,QSA,L]'

---

### Post by cosmin86200 on 2009-08-15
What happens when I go to 'settlement/foobar'?
It goes to the settlement.php page [which is set in .htaccess] but without the $_GET['settlement'] = 'foobar'... ignoring that $_GET array that should be returned by apache.

I tried to change (.*) with (.*?) but same result...

---

### Post by cosmin86200 on 2009-08-15
Ok...

"You'll mostly want '[NC,QSA,L]'"

Tried it... and doesn't work. Same problem. $_GET isn't instantiated on the server side...

---

### Post by v8YKxgHe on 2009-08-15
```
<?php var_dump( $_GET ); ?>
```
Paste output of that in the settlement.php page when you attempt to go to 'settlement/foobar'

---

### Post by cosmin86200 on 2009-08-15
here's the output: 

**array(0) {}**

$_GET is empty...

---

### Post by v8YKxgHe on 2009-08-15
and same for $_SERVER please

---

### Post by cosmin86200 on 2009-08-15
-message deleted-

---

### Post by v8YKxgHe on 2009-08-15
Ok, now can you post your real .htaccess file? ;) I say real because you originally had 'RewriteBase /rts_game/' in it, and no where is 'rts_game' being used in any paths.

In fact, just use this to test:

```
<IfModule mod_rewrite.c>
	RewriteEngine on
	RewriteRule ^settlement/(.*)$ settlement.php?settlement=$1 [NC,QSA]
</IfModule>
```

There is something you're not telling us :P

---

### Post by cosmin86200 on 2009-08-15
It's the same... I have a windows machine and a virtual one with ubuntu.. I modified just the folder of the application from the linux version.. That's all... I was lasy to go into the virtual machine.

---

### Post by cosmin86200 on 2009-08-15
Same thing... it still doesn't work...

If you really want, I can paste the version from Ubuntu, but it's identical..

---

### Post by v8YKxgHe on 2009-08-15
Only thing I can suggest then, check your Apache error log (defaults to /var/log/apache2/error.log if using the Apache2 packages provided by Ubuntu and have not changed that).

That will 100% work (what I gave you), so somewhere you have something epically setup up wrong (such as not allow PHP to register $_GET superglobal, which you'd have to *know* you did that), or simply are 'doing it wrong'.

Edit: I've just gone to [http://86.122.151.78:81/wardore/settlement/2](http://86.122.151.78:81/wardore/settlement/2) and unless you're currently playing around, it does not take me to the settlement page, but redirects to [http://86.122.151.78:81/wardore/home](http://86.122.151.78:81/wardore/home).

---

### Post by cosmin86200 on 2009-08-15
I checked the error logs.. and nothing...

the $_GET variable works... it does this problem only if I set slashes in the .htaccess file..

---

