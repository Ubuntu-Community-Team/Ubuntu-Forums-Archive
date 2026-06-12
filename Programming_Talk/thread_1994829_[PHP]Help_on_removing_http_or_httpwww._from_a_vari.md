---
title: "[PHP]Help on removing http:// or http://www. from a variable"
date: 2012-06-03
forum: Programming Talk
---

### Post by kenweill on 2012-06-03
Variable:
$website["WebsiteURL"]

$website["WebsiteURL"] value could be:
"http://www.google.com" or 
"https://www.google.com" or
"http://google.com" or
"https://google.com" .

I wanted to know what to do on $website["WebsiteURL"] which produces an output of only "google.com".

I found out about preg_replace () but I don't know how to use it.
Can anyone please help me do this via preg_replace or any other function that removes the http parts of the variable which only produces "google.com" (just an example) as an output?

Thanks.

---

### Post by roelforg on 2012-06-03
As long as it's a valid url, parse_url will work. (the host section of the result is what you're after).
[http://php.net/manual/en/function.parse-url.php](http://php.net/manual/en/function.parse-url.php)

---

### Post by roknron on 2012-06-03
Why not use <?php $website="http://www.google.com"; 
                             echo ltrim($website,"http://www."); 
                    ?>

---

### Post by roelforg on 2012-06-04
> **roknron said:**
> Why not use <?php $website="http://www.google.com"; 
echo ltrim($website,"http://www."); 
?>
 
Because the OP said that sometimes there is https instead of http and sometimes the url doesn't have www. prepended, so your way won't work.

---

### Post by kenweill on 2012-06-05
Currently it's http:// and [http://www](http://www). that needs to be removed.

And currently I'm using substr to remove http:// on "http://site.com" links but the same method doesn't work with the one's with www as it only removes the http:// part.

---

### Post by roelforg on 2012-06-05
> **kenweill said:**
> Currently it's http:// and [http://www](http://www). that needs to be removed.

And currently I'm using substr to remove http:// on "http://site.com" links but the same method doesn't work with the one's with www as it only removes the http:// part.

```

$domain=parse_url($website["WebsiteURL"],PHP_URL_HOST);
echo "The domainname is: ".$domain;

```

---

### Post by kenweill on 2012-06-07
> **roelforg said:**
> ```

$domain=parse_url($website["WebsiteURL"],PHP_URL_HOST);
echo "The domainname is: ".$domain;

```

I just tried this code based on your code:

[PHP]echo "The domainname is: ".parse_url($website["WebsiteURL"],PHP_URL_HOST);[/PHP]

And still works like the substr. Except that it still doesn't remove www if the URL have www.

Originally, I'm applying it as Title tags

[PHP]<title><?php echo $website["WebsiteName"]." Coupons - Promotion Codes, Coupon Codes for ".parse_url($website["WebsiteURL"],PHP_URL_HOST) ?></title>[/PHP]

Perhaps, it's possible to put another function inside parse_url which filters out www if it exist in the URL.
I just don't know what function and how to apply it.

---

### Post by steeldriver on 2012-06-07
well if you want to try preg_replace the regex would be something like (optional 's', optional 'www.') 

```
#https?://(www\.)?#

``````
preg_replace('#https?://(www\.)?#', '', '{{your data}}');
```I played with  your examples here ==> [http://www.solmetra.com/scripts/regex/index.php](http://www.solmetra.com/scripts/regex/index.php) and it seems to work

However if the system provides a higher level function (i.e. parse_url) it's usually best to use it if you can, likely a lot more thought has gone into handling corner cases.

---

### Post by roelforg on 2012-06-07
> **kenweill said:**
> I just tried this code based on your code:
 
[PHP]echo "The domainname is: ".parse_url($website["WebsiteURL"],PHP_URL_HOST);[/PHP]
 
And still works like the substr. Except that it still doesn't remove www if the URL have www.
 
Originally, I'm applying it as Title tags
 
[PHP]<title><?php echo $website["WebsiteName"]." Coupons - Promotion Codes, Coupon Codes for ".str_replace("www.","",parse_url($website["WebsiteURL"],PHP_URL_HOST)) ?></title>[/PHP]
 
Perhaps, it's possible to put another function inside parse_url which filters out www if it exist in the URL.
I just don't know what function and how to apply it.
I modded your code to do what you want.

---

### Post by kenweill on 2012-06-10
> **roelforg said:**
> I modded your code to do what you want.

Thanks a lot. It works. :)

---

