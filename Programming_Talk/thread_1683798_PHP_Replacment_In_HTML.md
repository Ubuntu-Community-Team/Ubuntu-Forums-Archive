---
title: "PHP: Replacment In HTML"
date: 2011-02-08
forum: Programming Talk
---

### Post by Sailor5 on 2011-02-08
Greetings! 

So I've across a dilemma. To put it bluntly, if I had the following HTML source.```
<a href="http://web.com/dest.php">link</a>
<a href="http://anotherweb.org/dest.php">link1</a>
<a href="http://webs.net/destination.php">link2</a>
```How could I change it to.```
<a href="host.com/p.php?h=web.com&p=dest.php">link</a>
<a href="host.com/p.php?h=anotherweb.org&p=dest.php">link1</a>
<a href="host.com/p.php?h=webs.net&p=destination.php">link2</a>
```So as you can see we have three different url's in the page. I need to alter the link to my own php file. Whilst passing the host name & path as a keyword. The url's will of course be different each time.

How could I do this?

---

### Post by kartabosh on 2011-02-08
why are you trying to do that?

---

### Post by lykeion on 2011-02-08
You can use regular expression and [preg_match_all]("http://php.net/manual/en/function.preg-match-all.php") to find the link address and the link name. Something like this:
[PHP]$regexp = "<a\s[^>]*href=(\"??)([^\" >]*?)\\1[^>]*>(.*)<\/a>";
if(preg_match_all("/$regexp/siU", $input, $matches)) {
   // $matches[2] = array of link addresses 
   // $matches[3] = array of link names
}[/PHP]
Then you can use [parse_url]("http://php.net/manual/en/function.parse-url.php") to find the http, hostname, path, etc of the link address.

I recommend that you look up regular expressions because there'll always come a time when you need it in programming.
Another specific tip specific to PHP is to search and consult the [official PHP manual]("http://php.net/manual/enindex.php") (which is quite good).

---

