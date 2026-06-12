---
title: "PHP - inlcude external webpage"
date: 2009-09-07
forum: Programming Talk
---

### Post by Johnsie on 2009-09-07
Hi, I'm looking for something like this:

[PHP]
include('http://www.example.com/example.php');
[/PHP]

The thing is that I don't want example.php on the other guys server to be able to do anything on my server. I just want his script to function as it normally does for people who access that page using a browser. I just want my script to download the output of example.php and display it. If you're familiar with facebook application development that might help you understand what I'm talking about.

What is the best way to do this? Basically I'm wanting to embed the contents of another web page on my web page without using Iframes.  (With permission from the owner)

---

### Post by januzi on 2009-09-07
You can use:
1. file_get_contents
2. fopen + stream_get_contents
3. fsockopen
4. curl[COLOR=#000000][COLOR=Black][COLOR=#0000BB][/COLOR][/COLOR][COLOR=#007700]

[COLOR=Black]Curl should be fine.[/COLOR]
[/COLOR][/COLOR]

---

### Post by Johnsie on 2009-09-07
Thanks, I used:
[PHP]
$content = file_get_contents('http://www.example.com/example.php');
if ($content !== false) {
   // do something with the content
echo "$content";
} else {
   // an error happened
}[/PHP]

I think that downloads the file and outputs it. Just gonna run some rests on it to make sure it cant execute anything on my server. Now I just need to write my own equivalent to FBML  and  also use str_replace to block out any javascripts.

---

### Post by januzi on 2009-09-07
Oh, I forgot. You have to rewrite all "src", "href", etc, to match new address, eg:
```

<img src="gfx/picture.jpg" /> => <img src="http://www.site.com/gfx/picture.jpg" />

```
Without that all images, javascripts would not work.

---

### Post by credobyte on 2009-09-07
[php]echo file_get_contents("http://www.google.com");
[/php]

As this function can be disabled in server level ( it'll return null ), another way of achieving this is to use CURL library.

---

### Post by Johnsie on 2009-09-07
I must've enabled it because it works for me. I think I was playing around with some get codes before sometime. I think I'll just make the other guys have to include the full url to their images.

---

### Post by credobyte on 2009-09-07
> **Johnsie said:**
> I must've enabled it because it works for me. I think I was playing around with some get codes before sometime. I think I'll just make the other guys have to include the full url to their images.

By default it's enabled and you can use this function even if it's disabled, however, if you disable it, no one will be able to use it against yourself ( file_get_contents(YOU) would result in a big failure ).

---

### Post by Reiger on 2009-09-07
Note that CURL is not a guaranteed-to-be-available library: i.e. by the time you deploy your code on servers that have file_get_contents() to remote (or other virtual) hosts disabled, you will probably have noticed that CURL isn't exactly standard package either (PHP includes wrappers for it by default but there are dependencies and configuration options to take care of; especially on Windows -- dunno if that applies to you).

---

