---
title: "[PHP] link parsing"
date: 2008-06-17
forum: Programming Talk
---

### Post by ELD on 2008-06-17
I am trying to find out how to find links with "http://" or "www." or both together and turn them into an actual html link and then the code to un-parse them too.

There is no tutorial i can find on the web that has this! And it seems to me such a simple thing :(:confused:

---

### Post by geirha on 2008-06-17
Try searching for "php url regular expression" on google. A lot of the hits has examples on regular expressions matching urls starting with [http://.](http://.) From that, you might manage to make one to match hostnames starting with 'www.' as well.

---

### Post by ELD on 2008-06-17
Well using the search term you gave me i found something that looked promising, but it didn't work :(

```

//URL: Replace URLs with HTML links
preg_replace('\b(https?|ftp|file)://[-A-Z0-9+&@#/%?=~_|!:,.;]*[-A-Z0-9+&@#/%=~_|]', '<a href="\0">\0</a>', $text);

```

Fond on - [http://www.roscripts.com/PHP_regular_expressions_examples-136.html](http://www.roscripts.com/PHP_regular_expressions_examples-136.html)

---

### Post by geirha on 2008-06-17
Apparently a bit incomplete that one. A slight modification and it appears to work:
[php]
   $text = "a link to http://google.com yes?\n";
   $text.= "another link: http://ubuntuforums.org/showthread.php?t=831828\n";
   echo preg_replace("`\b(https?|ftp|file)://[-A-Za-z0-9+&@#/%?=~_|!:,.;]*[-A-Za-z0-9+&@#/%=~_|]\b`", '<a href="\0">\0</a>', $text);
[/php]

---

### Post by ELD on 2008-06-17
Thanks how can that be changed to parse links that don't have a "http://" or "https://" etc in them? if it only has "www." it won't parse it :(

---

### Post by geirha on 2008-06-17
At the manual page for preg_replace, some of the comments contain examples for matching urls. Haven't tested any of them, but this one looks like it's worth trying: [http://www.php.net/manual/en/function.preg-replace.php#77787](http://www.php.net/manual/en/function.preg-replace.php#77787)

---

### Post by ELD on 2008-06-17
I already tried that one, and it didn't work, the one you fixed above is the only one i have found that pretty much fully works, just need it edited to add in "http://" if it only has "www."

---

### Post by geirha on 2008-06-17
Ok, had to test it myself then. Here's the above regex in addition to the one at php.net. 
[php]
<?php
   $text = "a link to http://google.com yes?\n";
   $text.= "another link: http://ubuntuforums.org/showthread.php?t=831828\n";
   $text.= "a link without http:// www.ubuntu.com for example\n";
   $text.= "or maybe a link to a google search www.google.com/search?hl=en&q=php \n";
   $text = preg_replace("`\b(https?|ftp|file)://[-A-Za-z0-9+&@#/%?=~_|!:,.;]*[-A-Za-z0-9+&@#/%=~_|]\b`", '<a href="\0">\0</a>', $text);
   $text = preg_replace("/\s(www\.([a-z][a-z0-9_\..-]*[a-z]{2,6})([a-zA-Z0-9\/*-?&%]*))\s/i", " <a href=\"http://$1\">$2</a> ", $text);
   echo $text;
?>
[/php]

It's a bit easier to have two regular expressions for this. Having one that matches both cases becomes a bit more complex.

---

### Post by ELD on 2008-06-17
Right i am starting to get it now, i have tested it and it works, although the first link to the ubuntu thread is perfect, when you don't include "http://" in it then it only parses out as "ubuntu.com" for example, the link is correct with the rest, but the links text only has the domain and extension?

Heres the example:
[http://forum.prxa.info/test.php](http://forum.prxa.info/test.php)

And you will see what i mean.

And one last edit, how would you stop it from parsing links that are inbetween a certain type of "bbcode" for example ['url=url here]some text here[/url'] (without the single quotes, they are there to stop ubuntu forum vb parsing it).

---

### Post by LoneWolfJack on 2008-06-17
Regular expressions are awfully slow so they should be avoided wherever possible. Below is a code snipped that I extracted from one of my custom built PHP classes. I quickly adapted it for your purpose, optimizing and expanding it would be your job...

```

$i = 0;
$output = 'www.foo.bar alea iacta est www.bar.foo';
$key = 'www';
$val = '<a href="';
while($i<1000)
	{
	$startpos = strpos($output,$key);
	if(!$startpos && substr($output,0,strlen($key))!=$key)
		{break;}
	$endpos = (int)strpos($output,' ',$startpos);
	!$endpos?$endpos=strlen($output):true;
	$var = substr($output,$startpos+strlen($key)+1,$endpos-$startpos-strlen($key));
	$temp = substr($output,0,$startpos).$val.'http://'.$var.'">'.$var.'</a>'.substr($output,$endpos+1,strlen($output));
	$output = $temp;
	$i++;
	}

echo $output;

```

---

### Post by ELD on 2008-06-17
Well for code readability that code is pretty horrible and massively confusing to look it.

I am not ungrateful i just prefer to use easier to read methods so for 1, i can understand them and 2, every forum software i have ever seen uses regex from bbcode, link parsing etc etc, so they can't be that slow.

And for my application it won't be used all the time, so it won't matter too much.

---

### Post by geirha on 2008-06-17
> **ELD said:**
> Right i am starting to get it now, i have tested it and it works, although the first link to the ubuntu thread is perfect, when you don't include "http://" in it then it only parses out as "ubuntu.com" for example, the link is correct with the rest, but the links text only has the domain and extension?

Heres the example:
[http://forum.prxa.info/test.php](http://forum.prxa.info/test.php)

And you will see what i mean.
 

Look at the replacement string: " <a href=\"http://$1\">$2</a> "
$0 will be replaced with the entire matched string, $1 will be replaced with everything inside the first set of (), $2 the second set of () and so forth. So try changing $2 to $1 for example.

Now the first regex one uses a bit different syntax, but the principal is the same. \0 is the entire match, \1 is the first set of () and so forth.

> **ELD said:**
> 
And one last edit, how would you stop it from parsing links that are inbetween a certain type of "bbcode" for example ['url=url here]some text here[/url'] (without the single quotes, they are there to stop ubuntu forum vb parsing it).

The easiest way out, is to make sure the bbcodes are translated first, so then you'll have anchors instead of [url]s. Then, as the second regular expression does, make the first regular expression also match a whitespace before and after. That way, [php]<a href="http://google.com">http://google.com</a>[/php] will not match, since there's no whitespace around the urls, but [php]<a href=" http://google.com"> http://google.com </a>[/php] will have one match.

When the bbcode has been replaced, you probably won't have any such whitespace around the urls, so it'll probably be safe.

I recommend you read up on regular expressions. It can be quite handy to know.

---

### Post by ELD on 2008-06-17
Thanks so much for your amazing help "geirha", i have got it to work nicely on the test page now, i will have to have a play with the url bbcode thing to see how that works out, have bookmarked this thread so i can always post here if i cannot get it to work.

---

### Post by LoneWolfJack on 2008-06-17
> 
Well for code readability that code is pretty horrible and massively confusing to look it.


You should see the C implementation of preg_replace(). ;)

> 
I am not ungrateful i just prefer to use easier to read methods so for 1, i can understand them and 2, every forum software i have ever seen uses regex from bbcode, link parsing etc etc, so they can't be that slow.


It's a matter of preference. If you're a performance geek, you will avoid regex like the plague. If you don't really care about performance, there's no reason not to utilize regex-oneliners.

As for speed... PHP pages that I build NEVER take longer than 0.2 seconds to load on an average server. In fact, 90% of the pages delivered take about 0.05 seconds (not just the SQL query - the entire page!). Again, if it doesn't matter to you if you site takes a second or two to load, that's ok.

For me... well... it always makes me grin when I get a "wow, this site is fast!" from one of my users. :)

---

### Post by ELD on 2008-06-17
> **LoneWolfJack said:**
> You should see the C implementation of preg_replace(). ;)



It's a matter of preference. If you're a performance geek, you will avoid regex like the plague. If you don't really care about performance, there's no reason not to utilize regex-oneliners.

As for speed... PHP pages that I build NEVER take longer than 0.2 seconds to load on an average server. In fact, 90% of the pages delivered take about 0.05 seconds (not just the SQL query - the entire page!). Again, if it doesn't matter to you if you site takes a second or two to load, that's ok.

For me... well... it always makes me grin when I get a "wow, this site is fast!" from one of my users. :)

Well everyone has their own preference. hehe

Although i have somehow now created a bug the test page will parse everything fine, but when i put it into my app it won't parse "www.google.com/search?hl=en&q=php" but it will parse the other test links

Here is a page showing it:
[http://forum.prxa.info/viewtopic.php?tid=21](http://forum.prxa.info/viewtopic.php?tid=21)


How wierd is that?

---

### Post by geirha on 2008-06-17
Hm, the '&' in the last link there, has been replaced by '&amp;', which the regular expression won't, and probably shouldn't, match (since the url would've pointed to [http://www.google.com/search?hl=en&amp;q=php](http://www.google.com/search?hl=en&amp;q=php) instead). The forum software probably does that change.

---

### Post by ELD on 2008-06-17
The problem is if i put the link regex before it makes html into safe code, then the links href part all gets buggered up too.

And now the post parser seem completely utterly broken :(, it won't parse new lines into brs nopw either, ARGH

(btw its my forum software)

---

### Post by ELD on 2008-11-18
Just thought i would update, i got it mostly working now bar one thing
```

$post = preg_replace("/\s(www\.([a-z][a-z0-9_\..-]*[a-z]{2,6})([a-zA-Z0-9\/*-?&%]*))\s/i", " <a href=\"http://$1\">$1</a> ", $post);

```

That seems to do nowt, it should parse web addresses without a http:// by it but it just leaves them?

---

### Post by drubin on 2008-11-18
Just so you know there are predefined regular expressions for matching this. :)

The bad news is it is 7kb of pure regular expression. :(
[http://www.terminally-incoherent.com/blog/2007/08/24/biggest-regex-in-the-word/](http://www.terminally-incoherent.com/blog/2007/08/24/biggest-regex-in-the-word/)

Thought it was relevant.

---

### Post by ELD on 2008-11-18
I need readable code though not some messy stuff from 1999 heh.

And the download isn't even there anymore :P

---

### Post by drubin on 2008-11-18
> **ELD said:**
> I need readable code though not some messy stuff from 1999 heh.

And the download isn't even there anymore :P

Readable no!! but the spec still stands URLS haven't changed in syntax since then :)

Can't believe they removed the link. I was a freeky cool and scary regular expression!!! (I don't think any one would actually use it though)

---

### Post by ELD on 2008-11-18
Heh well i need something practicle and usable lol

---

