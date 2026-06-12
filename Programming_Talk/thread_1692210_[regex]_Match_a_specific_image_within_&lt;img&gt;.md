---
title: "[regex] Match a specific image within &lt;img&gt;"
date: 2011-02-21
forum: Programming Talk
---

### Post by Pyro.699 on 2011-02-21
Hey

Im having some problems matching an image type held within a string. What i want to do is find all <img> tags that contain php scripts. I have made several atempts at it but get stuck when the regex fails and then goes on to another tag and copies the whole thing...

The one i have now is [B]<img.*?src=['"](.*?\.php.*?(?:['"])).*?>

[/B]The problem with that is if i had this text:
[php]
<a href='http://www.example.com/url_a.php'><img src='http://www.example.com/url_a.png' /></a><a href='http://www.example.com/images.php?src=url_b' ><img src='http://www.example.com/image.png'></a>[/php]
it will capture the group:
[php]
http://www.example.com/url_a.png' /></a><a href='http://www.example.com/images.php?src=url_b
[/php]

I would have liked it to capture:
[php]http://www.example.com/images.php?src=url_b[/php]
instead

Thanks
~Cody

---

### Post by Pyro.699 on 2011-02-21
I think i should have it...

**<img.*?(['"][^'"]*(?=php)[^'"]*).*?>**

Let me know if you see any potential problems with it :)

Thanks
~Cody

---

### Post by Trooper_Max on 2011-02-21
It's very helpful to use an online regular expression tester to play with your regular expressions... or a scripting language.

I used to use: [http://www.regular-expressions.info/javascriptexample.html](http://www.regular-expressions.info/javascriptexample.html)

But after searching again, this looks really nice: [http://regexpal.com/](http://regexpal.com/)
(does special highlighting and everything)

But maybe you're already doing that...

Anyway, you'll see that I don't think your expression matches what you want... And based on your example, it sounds like you actually want to match a php script url linked to in the anchor tag (<a>) that surrounds the image tag, which is quite a bit more complex.

If that's what you want, then you might move more towards:

[PHP]<a.*?(['"][^'"]*(?=php)[^'"]*).*?>.*?<img.*?</a>[/PHP]

I'd probably be sure to make it case insensitive and throw more allowances for spaces in the tags and such in there though...

Can you more precisely define what you're trying to match?

~Troop

---

### Post by Pyro.699 on 2011-02-21
I actually use: [http://gskinner.com/RegExr/](http://gskinner.com/RegExr/) xP

And i dont want the link inside the <a href i want the image path... basically i want to find all images that are not real images; but rather ones that were generated with php scripts. That being said a more pseudo look at it would be anything matching <img scr="<some path>.php<some args>" />

Thanks
~Cody

---

### Post by Trooper_Max on 2011-02-24
Sorry I didn't get back to you sooner, this is what I came up with:

```
<img[^>]*\ssrc\s*=\s*(("[^"]*\.php[^"]*")|('[^']*\.php[^']*'))\s*/?\s*>
```I used [^>] to match any non-greater-than character to ensure the stuff I'm matching is still in the same tag. I also broke apart the cases of quotes and single quotes to ensure they match up (didn't want to bother using a backreference) and allow for the other type of quote within.

Here are a few simple test cases:

```
match: <img src="test.php"/>
match: <img src='test.php'>
match: <img src='test.php?a="b"'>
no match: <img title="php" src="test.png">
no match: <img src='test.png'> text <a href="test.php">
```

I recommend coming up with your own test cases as well. It's hard to come up with a "perfect" regular expression, because a lot of times the stuff you're trying to match might be bordering the limits of regular languages, so it's more practical just to make sure it meets all the cases you care about. Sometimes this can simplify your expression too... you don't want to let your expression get super ugly while you expand it again and again to meet numerous corner cases you might not care about. When you have an expression that seems to work, try to come up with test cases that will break it and then you can keep these cases around for testing your next attempts.

Note though, it's certainly feasible for a website to use scripts on the backend to dynamically generate an image, regardless of the url you're using to request it. (They could have what looks like a simple .png actually served by a php script... not usually the case though unless images are stored in a database)

~Troop

---

### Post by Rany Albeg on 2011-02-24
```
rany:~/Desktop$ grep -o "http://[^\']*" your_text
http://www.example.com/url_a.php
http://www.example.com/url_a.png
http://www.example.com/images.php?src=url_b
http://www.example.com/image.png
rany:~/Desktop$ grep -o "http://[^\']*" your_text | grep '/[^.]*.php'
[COLOR="Red"]http://www.example.com/url_a.php
http://www.example.com/images.php?src=url_b[/COLOR]
```

I hope I understand you correctly.

---

### Post by Portmanteaufu on 2011-02-25
> **Pyro.699 said:**
> Hey

Im having some problems matching an image type held within a string. What i want to do is find all <img> tags that contain php scripts. I have made several atempts at it but get stuck when the regex fails and then goes on to another tag and copies the whole thing...


Your post reminded me of an [ article that I read a long while back]("http://www.codinghorror.com/blog/2009/11/parsing-html-the-cthulhu-way.html") that warned of the complications inherent to trying to parse HTML using regular expressions.

If you aren't too tied to the idea of using RegEx, take a look at using an actual PHP toolset for parsing HTML. You can see an example of how to do it [here.]("http://www.phpro.org/examples/Parse-HTML-With-PHP-And-DOM.html")

It looks as though you could do something like:
```
$image_tags = $dom->getElementsByTagName('img');
```
and then iterate over $image_tags evaluating their "src" attribute for the presence of '.php'.

Hope that helps!

---

