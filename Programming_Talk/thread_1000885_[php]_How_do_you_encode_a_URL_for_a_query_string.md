---
title: "[php] How do you encode a URL for a query string?"
date: 2008-12-03
forum: Programming Talk
---

### Post by altonbr on 2008-12-03
I'm trying to encode a URL and pass it in a query string (I know there are better ways of performing this, but this is a must in my situation. Just pretend it is out of my control.)

[PHP]<?php

$url = 'http://example.com?pid=12&uid=200'
echo 'http://test.com?url='.urlencode($url);

?>[/PHP]

The resulting URL is invalid as

> [http://test.com?url=http://example.com?pid=12&uid=200](http://test.com?url=http://example.com?pid=12&uid=200)

because urlencode() doesn't seem to work. Neither does rawurlencode(). What am I supposed to use to produce this:

> [http://test.com?url=http%3A%2F%2Fexample.com%3Fpid%3D12%26uid%3D200](http://test.com?url=http%3A%2F%2Fexample.com%3Fpid%3D12%26uid%3D200)

---

### Post by pp. on 2008-12-03
From the looks of it, urlencode() encodes a complete URL and not a part which is to be enclosed in an URL.

Therefore, I presume you should first form the complete URL and urlencode that.

---

### Post by altonbr on 2008-12-03
> **pp. said:**
> From the looks of it, urlencode() encodes a complete URL and not a part which is to be enclosed in an URL.

Therefore, I presume you should first form the complete URL and urlencode that.

Their [documentation]("http://ca.php.net/urlencode") shows it being used in parts to build a query string.

I think their is another function for the type of escaping I am trying... I just can't remember what it is called.

---

### Post by s.fox on 2008-12-03
That looks fine to me. You should be able to retrieve it just fine using :

$passedVar = $_GET['url'];

Why do you think its invalid?

---

### Post by Sydius on 2008-12-03
As an alternative, you can use base64_encode and replace the invalid characters with valid ones.  See the first comment to [http://us3.php.net/base64_encode](http://us3.php.net/base64_encode)

---

### Post by altonbr on 2008-12-03
> **Ash R said:**
> That looks fine to me. You should be able to retrieve it just fine using :

$passedVar = $_GET['url'];

Why do you think its invalid?

It's invalid because their is a query string inside a query string and PHP gets confused. It can't pass it properly.

> **Sydius said:**
> As an alternative, you can use base64_encode and replace the invalid characters with valid ones.  See the first comment to [http://us3.php.net/base64_encode](http://us3.php.net/base64_encode)

I wish I could use something as simple as that, but I'm actually passing this URL to another website via query string.

Does anyone know what it's called when you turn ':' into '%3A' and '//' into '%2F%2F'?

---

### Post by s.fox on 2008-12-03
you could just use string replace

<?php
$originalString = "I like red";
$originalString = str_replace("red","green",$originalString);
echo $originalString;
?>

hope this helps

---

### Post by altonbr on 2008-12-03
> **Ash R said:**
> you could just use string replace

<?php
$originalString = "I like red";
$originalString = str_replace("red","green",$originalString);
echo $originalString;
?>

hope this helps

But then I have to know what characters are not allowed and what '%##' number to assign them to.

I have some resources on it:
[LIST]
[*][You can use JavaScript's encodeURIComponent]("http://weierophinney.net/matthew/archives/133-PHP-decoding-of-Javascript-encodeURIComponent-values.html") (unfortunately not an option for me)
[*][A guy with a similar problem, but they don't touch on how he's encoding/decoding]("http://www.jeroenwijering.com/?thread=9455")
[*][RFC 1738 reference]("http://www.blooberry.com/indexdot/html/topics/urlencoding.htm")
[*][UTF16 version of urlencode()]("http://ca.php.net/manual/en/function.urlencode.php#82483")
[/LIST]

So I guess urlencode() is doing it's job, I just need ':', '/', '?', etc. to be encoded.

Maybe I will just make a manual function using 'str_replace()', thanks!

---

