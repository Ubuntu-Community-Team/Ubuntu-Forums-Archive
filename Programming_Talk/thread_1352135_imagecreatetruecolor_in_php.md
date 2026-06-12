---
title: "imagecreatetruecolor in php?"
date: 2009-12-11
forum: Programming Talk
---

### Post by abhilashm86 on 2009-12-11
i'm building a contact form along with captcha, i'm getting this error on execution? why is it so?
can anyone try this and tell me what is wrong? is there any alternative to this?
 [PHP]<?php



session_start();



$string = '';



for ($i = 0; $i < 5; $i++) {

	 
	$string .= chr(rand(97, 122));

}



$_SESSION['rand_code'] = $string;



$dir = 'fonts/';



$image = imagecreatetruecolor(170, 60); //here is error??

$black = imagecolorallocate($image, 0, 0, 0);

$color = imagecolorallocate($image, 200, 100, 90);  

$white = imagecolorallocate($image, 255, 255, 255);



imagefilledrectangle($image,0,0,399,99,$white);

imagettftext ($image, 30, 0, 10, 40, $color, $dir."arial.ttf", $_SESSION['rand_code']);



header("Content-type: image/png");

imagepng($image);



?>
[/PHP]

error given from php,

Fatal error: Call to undefined function imagecreatetruecolor() in /var/www/captcha.php on line 16




also is there any difference between echo and print statements in php?

---

### Post by Physical Hook on 2009-12-11
> Depending on your PHP and GD versions this function is defined or not. With    PHP 4.0.6 through 4.1.x this function always exists if the GD module is    loaded, but [COLOR=Red]calling it without GD2 being installed PHP will issue a fatal    error and exit[/COLOR]. With PHP 4.2.x this behaviour is different in issuing a    warning instead of an error. Other versions only define this function, if    the correct GD version is installed.   Have you installed [COLOR=Green]php5-gd[/COLOR] ?

---

### Post by abhilashm86 on 2009-12-12
yes did it, thanks.......
what about my second question, any difference between echo and print in php?

i think its silly to ask, but i'm learning php scripting, i really don't find difference at this point!!

---

### Post by v8YKxgHe on 2009-12-12
echo and print are very similar, however print acts more like a function (they are both language constructs, not functions) and has a return value of always 1. For example:

[php]1 < 5 ? echo 'less than' : 'more than'; # PHP fatal error
1 < 5 ? print 'less than' : 'more than'; # Works just fine.[/php]

However in that above example, it is far easier to just do:

[php]echo 1 < 5 ? 'less than' : 'more than';[/php]

Basically, use print when you need a return value for some reason (and for it to act like a function), other wise - really just use echo, or any. Up to you. People say that echo is faster, however - that 'faster' is an incredibly small amount that it is not even worse the argument.

---

### Post by abhilashm86 on 2009-12-13
> **AlexC_ said:**
> 

Basically, use print when you need a return value for some reason (and for it to act like a function), other wise - really just use echo, or any. Up to you. People say that echo is faster, however - that 'faster' is an incredibly small amount that it is not even worse the argument.

thanks for showing that difference, i'l get to know more as i dig into php!!

---

### Post by Hellkeepa on 2009-12-13
HELLo!

I'd also like to point out that the [PHP manual](http://www.php.net/manual/en) is a great resource for these kind of questions. To look up on a known function, just use "php.net/<function>" as the URI.
Like this:
[php.net/echo](http://www.php.net/echo)
[php.net/print](http://www.php.net/print)

Happy codin'!

---

