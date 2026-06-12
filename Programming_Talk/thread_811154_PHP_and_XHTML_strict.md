---
title: "PHP and XHTML strict"
date: 2008-05-28
forum: Programming Talk
---

### Post by themusicwave on 2008-05-28
Hey everyone,

So I already know some PHP and am now trying to learn XHTML.  I know HTML fairly well, and am just trying to make the transition to XHTML and CSS.

Anyways, I would like to embedd a php script into an XHTML Strict page.  I was wondering how this can be done.

I beleive that CDATA may be the answer, but so far I've had no luck.  If anyone could provide an example I would be grateful.

Thanks,

jon

---

### Post by LaRoza on 2008-05-28
> **themusicwave said:**
> Hey everyone,

So I already know some PHP and am now trying to learn XHTML.  I know HTML fairly well, and am just trying to make the transition to XHTML and CSS.

Anyways, I would like to embedd a php script into an XHTML Strict page.  I was wondering how this can be done.

I beleive that CDATA may be the answer, but so far I've had no luck.  If anyone could provide an example I would be grateful.


PHP is executed on the server, it isn't part of the markup. There can be no example as the question as stated doesn't really make sense.

---

### Post by themusicwave on 2008-05-28
Let me provide an example of what I used to be able to do in simple HTML

<html>
<head><title>PAGE TITLE</title></head>

<?php
$someval = $_GET['somefield'];
?>
<body>

The output:<BR>
<?php
print $someval;

?>
</body>

</html>


Perhaps this is no longer possible in XHTML because it is considered a bad practice?  I could also just simply make a script that outputs a whole page based on the GET values I suppose.  Is this the way it should be done?

---

### Post by LaRoza on 2008-05-28
> **themusicwave said:**
> Let me provide an example of what I used to be able to do in simple HTML

Perhaps this is no longer possible in XHTML because it is considered a bad practice?  I could also just simply make a script that outputs a whole page based on the GET values I suppose.  Is this the way it should be done?

Ok, I will do a bit of explaining of PHP. PHP is executed on the server. Anything not in <?php?> tags is echo'd. So:

[php]
Absolute Gibberish
<?php 
//There is PHP code here
?>
[/php]

The code is executed and the document is then servered. All that arrives at the client is the plain text. This text can be anything, including XHTML.

For PHP, it is easy to mix code and markup. This can make small tasks easier (like echoing an ip address or something) but it makes anything larger a pain if done that way. You should keep the code separate from the markup.

---

### Post by soapytheclown on 2008-05-29
> **themusicwave said:**
> Let me provide an example of what I used to be able to do in simple HTML

<html>
<head><title>PAGE TITLE</title></head>

<?php
$someval = $_GET['somefield'];
?>
<body>

The output:<BR>
<?php
print $someval;

?>
</body>

</html>


Perhaps this is no longer possible in XHTML because it is considered a bad practice?  I could also just simply make a script that outputs a whole page based on the GET values I suppose.  Is this the way it should be done?

to be fair u can use it exactly like that except remember in XHTML its <br /> not <BR>! but as Laroza said its easier to maintain the code if u keep large chunks of php separate from the XHTML instead of weaved in.

---

### Post by themusicwave on 2008-05-30
In my actual page I do have the <br />, I was just typing that example for this post.  Thanks for pointing it out though.

Strangely my server gives me a parse error when I include the XHTML strict declarations in the page.  As soon as I take them otu the page works.  When I put them in the page gets a parse error.  However, If I comment out the php with <!-- then the page will parse as XHTML...

Very confusing..any ideas?

Thanks,

Jon

---

### Post by LaRoza on 2008-05-30
> **themusicwave said:**
> In my actual page I do have the <br />, I was just typing that example for this post.  Thanks for pointing it out though.

Strangely my server gives me a parse error when I include the XHTML strict declarations in the page.  As soon as I take them otu the page works.  When I put them in the page gets a parse error.  However, If I comment out the php with <!-- then the page will parse as XHTML...

Very confusing..any ideas?

Thanks,

Jon
Is it really the server giving the parse error?

Is the server actually executing PHP?

Is the server using the short hand <? php tags? (If you have an xml declaration, that can cause problems)

---

### Post by Mickeysofine1972 on 2008-05-30
I also suggest you use :
```
error_reporting(E_ALL)
```

during your debug/development stage too if it isn't already on.

Mike

---

### Post by themusicwave on 2008-05-30
I can confirm my server is running php and does work if I just make a php script that has no xhtml in it.

I'll try the error reporting and let you know.

Thanks again,

Jon

---

### Post by Verminox on 2008-05-30
> **themusicwave said:**
> In my actual page I do have the <br />, I was just typing that example for this post.  Thanks for pointing it out though.

Strangely my server gives me a parse error when I include the XHTML strict declarations in the page.  As soon as I take them otu the page works.  When I put them in the page gets a parse error.  However, If I comment out the php with <!-- then the page will parse as XHTML...

Very confusing..any ideas?

Thanks,

Jon


It seems that what you are trying to say is being misinterpreted by all those who replied, so let's just use code examples and post the error messages so that we are all clear what we mean.

As a test, here is a sample XHTML 1.0 Strict page with a few php tags...

xhtml_test.php
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
  <head>
    <title>XHTML 1.0 Strict Test</title>
  </head>
  <body>
    <p>Foo: <?php echo ($_GET['foo'] ? $_GET['foo'] : 'undefined'); ?></p>
  </body>
</html>
```

Here is the output when I call [http://localhost/xhtml_test.php?foo=Bar](http://localhost/xhtml_test.php?foo=Bar)

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
  <head>
    <title>XHTML 1.0 Strict Test</title>
  </head>
  <body>
    <p>Foo: Bar</p>
  </body>
</html>
```

Which is perfectly valid XHTML 1.0 Strict. 

As LaRoza pointed out, PHP is server side script, so it will execute and provide the echo'd output to the browser, and only this output should be validated for XHTML, not the PHP script itself. If you are getting PHP's Parse Errors, it's probably because of wrong syntax or maybe you are putting the DOCTYPE inside the <?php ?> tags (it should be outside). 

If the problem still persists, do post your code and the error message you receive.

---

