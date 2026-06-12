---
title: "Problem serving MIME type using PHP"
date: 2006-04-21
forum: Programming Talk
---

### Post by Ferio on 2006-04-21
Hi, I've got a blog at [http://www.tecniferio.com]("http://www.tecniferio.com"); I created it using [http://www.textpattern.com]("http://www.textpattern.com"), which is a CMS very similar to WordPress. The point is that I'm using XHTML 1.1, and I'm seeing everywhere that it **must **(as specified by W3C) be served with "application/xhtml+xml" MIME type.

Since TextPattern is a PHP-based CMS, I've tried to add

[PHP]if ((isset($_SERVER["HTTP_ACCEPT"]) and
stristr($_SERVER["HTTP_ACCEPT"], "application/xhtml+xml")) or
stristr($_SERVER["HTTP_USER_AGENT"], "W3C_Validator") )
{
header("Content-type: application/xhtml+xml");
print("<?xml version=\"1.0\" encoding=\"utf-8\"?>\n");
}
else
{
header("Content-type: text/html; charset=utf-8");
}[/PHP]

at the beginning of my index.php (as stated in several pages I've seen), what will make my page be served as "application/xhtml+xml" to web browsers that support it, and "text/html" to the ones that don't (mainly IE). Anyway, I can't get it to work, and since I have no idea on PHP, I'm not sure about what I'm not doing well.

My index.php is:

[PHP]<?php

/*
$HeadURL: http://svn.textpattern.com/development/4.0/index.php $
$LastChangedRevision: 804 $
*/

    // Make sure we display all errors that occur during initialization
    error_reporting(E_ALL);
    @ini_set("display_errors","1");

    if (@ini_get('register_globals'))
        foreach ( $_REQUEST as $name => $value )
            unset($$name);
    define("txpinterface", "public");

    // Use buffering to ensure bogus whitespace in config.php is ignored
    ob_start(NULL, 2048);
    $here = dirname(__FILE__);
    include './textpattern/config.php';
    ob_end_clean();

    if (!isset($txpcfg['txpath']) )    { 
        header('Status: 503 Service Unavailable'); header('HTTP/1.0 503 Service Unavailable');
        exit('config.php is not ok or not found. If you would like to install, go to [/subdir]/textpattern/setup/'); 
    }

    include $txpcfg['txpath'].'/publish.php';
    textpattern();
?>[/PHP]

and the beginning of the content of my page that I typed using TextPattern is:

[HTML]<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" dir="ltr">
    <head>
        <base href="<txp:link_to_home />" />
        <link rel="stylesheet" href="<txp:css />" type="text/css" media="screen" />
        <meta http-equiv="content-type" content="application/xhtml+xml; charset=utf-8" />[/HTML]

I'm giving all this information because I'm not sure about where's what I'm not doing correctly. Any help will be welcome, thanks in advance!

---

### Post by LordHunter317 on 2006-04-21
I wouldn't bother.  *No* browser currently parses and deals with application/xhtml+xml 100% correctly, to my knowledge.  It was certainly the case sometime ago.  Not according to the way W3C says you should, anyway.  As long as you don't include <?xml>, everythign will be ok.

As for your code, it's not escaped properly, so it's not going to work.  The color formatting here should help you spot it.

---

### Post by Ferio on 2006-04-22
OK, thanks, I think I was having some paranoia with all this webpages saying that I must serve it properly, I hope that TextPattern developers manage to do it in the future, since XHTML 2.0 will only work being served as "application/xhtml+xml".

As for my code, I can't say where it's nost escaped properly; I have no idea on PHP, and XHTML has been validated using 3 different validators. But the page works!

---

### Post by mostwanted on 2006-04-22
Serving with the correct MIME-type is possible. Google "content negotiation".

---

### Post by Ferio on 2006-04-22
Oh, yes, I've seen different types of content negotiation in every page about this XHTML 1.1 problem, but none of them seems to work, or at least I don't know how to make them work: using PHP, using Python, using .htaccess...

---

### Post by LordHunter317 on 2006-04-22
> **Ferio]since XHTML 2.0 will only work being served as "application/xhtml+xml".[/quote]According to the W3C, XHTML 1.0 and 1.1 will only work served as such also, but they clear do.

You'd only want to serve it as such if you want to treat it as both an XML document and an HTML document.  For pages your serving to end-users, you don't want or need that.

[quote]As for my code, I can't say where it's nost escaped properly said:**
> Look at the colors, it's at the top where you generate your xml response.  As posted, I don't see how the code is even running.

[quote=mostwanted]Serving with the correct MIME-type is possible. Google "content negotiation".Won't actually work for this.

---

### Post by mostwanted on 2006-04-22
Insert this at the top of your page:

```
<?php
// Content negotiation, set correct mime-type as long as it's accepted
header("Vary: Accept");
if (stristr($_SERVER[HTTP_ACCEPT], "application/xhtml+xml")) 
    header("Content-Type: application/xhtml+xml; charset=utf-8");
else
    header("Content-Type: text/html; charset=utf-8");
?>
```

But you're better off using HTML 4. It has much better support, especially if you plan on using JavaScript along with your page. XHTML 1 offers nothing over HTML 4 as of now, wait till XHTML 2 before switching.

---

### Post by Ferio on 2006-04-23
I've tried several solutions like this one you're giving me, but none of them has worked, I don't know why. Anyway, I'm using JavaScript in my page and it does work. This whole XHTML 1.1 is not even beginning to make sense in my head, to be true :S Maybe I'll switch back to HTML 4 after all.

---

### Post by Ferio on 2006-04-23
Uf, I think I should study harder this whole thing, 'cos it's becoming messy in my head. Every modification I've made to my XHTML code has been added because I've seen in several different blogs and forums that it's the right path to follow, but I don't even know why! The thing is that Gecko-based web browsers render my page properly and IE has only a few minor problems.

I'll try to study harder on these subjects, and I'll try to learn some PHP, and let's see what I can do. Thanks a lot!

---

### Post by mostwanted on 2006-04-23
[QUOTE=Ferio]I've tried several solutions like this one you're giving me, but none of them has worked, I don't know why. Anyway, I'm using JavaScript in my page and it does work. This whole XHTML 1.1 is not even beginning to make sense in my head, to be true :S Maybe I'll switch back to HTML 4 after all.[/QUOTE]

I wasn't saying JS doesn't work, I'm saying there'll be problems at some point because many well-known JS functions do not exist for XML pages, and the replacements (you can tell by their usually being labeled with NS in front of them) don't work in all browsers.

And just use HTML 4. There's nothing to gain from using XHTML. Really. I used to think like you that I should just use XHTML because it's the newer one, but it's only putting more problems on your shoulder and you gain nothing from it. Nothing at all.

---

### Post by Ferio on 2006-04-23
Oh, yes, I've read that, for instance, document.write() doesnt' work, but the same functionality can be achieved by using DOM (of which I've got no idea, by I don't need this particular functionality).

Dunno, I'll think about it, it's probable that I switch back to HTML till the time to walk into greener pastures arrives.

---

