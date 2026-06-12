---
title: "[php] How to use Trim?"
date: 2010-12-12
forum: Programming Talk
---

### Post by sandyd on 2010-12-12
I currently have a function to fetch tweets with a specific hashtag from my twitter account
```

[INDENT] <?php
		// the function
 /**
 * @desc Get latest tweet from a Twitter account
 * @param string The account's username
 * @return string The tweet
 */
 function get_latest_tweet($username)
 {
 $url = "[http://search.twitter.com/search.atom?q=&tag=$tag&from=$username&rpp=1](http://search.twitter.com/search.atom?q=&tag=$tag&from=$username&rpp=1)";
 $content = file_get_contents($url);
 $content = explode('', $content);
 $content = explode('', $content[1]);
 return html_entity_decode($content[0])
 }
 // now use it
 $my_username = 'dolphinaura';
 $tag = 'mood';
 echo get_latest_tweet($my_username);
 ?>

```
It works well enough, but I can't figure out how to remove the actual hashtag I used (in this case, #mood) from the status.

I was thinking of using trim.
help?
[/INDENT]

---

### Post by sandyd on 2010-12-13
bump

---

### Post by Arndt on 2010-12-13
> **sandyd said:**
> I currently have a function to fetch tweets with a specific hashtag from my twitter account
```

[INDENT] <?php
		// the function
 /**
 * @desc Get latest tweet from a Twitter account
 * @param string The account's username
 * @return string The tweet
 */
 function get_latest_tweet($username)
 {
 $url = "[http://search.twitter.com/search.atom?q=&tag=$tag&from=$username&rpp=1](http://search.twitter.com/search.atom?q=&tag=$tag&from=$username&rpp=1)";
 $content = file_get_contents($url);
 $content = explode('', $content);
 $content = explode('', $content[1]);
 return html_entity_decode($content[0])
 }
 // now use it
 $my_username = 'dolphinaura';
 $tag = 'mood';
 echo get_latest_tweet($my_username);
 ?>

```
It works well enough, but I can't figure out how to remove the actual hashtag I used (in this case, #mood) from the status.

I was thinking of using trim.
help?
[/INDENT]

What is the "status" you mention? And how did you mean to use 'trim'? Show us your attempt.

---

### Post by sandyd on 2010-12-13
> **Arndt said:**
> What is the "status" you mention? And how did you mean to use 'trim'? Show us your attempt.
The status is the tweet with the specific hashtag on my twitter acclunt.

For example, if I tweet

1. > hi #hi
2. > hi #mood

Only #2 will be fetched to my blog and used as the status (you can see it on the top of [http://dolphinaura.com](http://dolphinaura.com) right now) because it uses the #mood tag.

However, the issue is that the tag is displayed in the status.

Currently, what ive tried
```

<?php
		// the function
 /**
 * @desc Get latest tweet from a Twitter account
 * @param string The account's username
 * @return string The tweet
 */
 function get_latest_tweet($username)
 {
 $url = "[http://search.twitter.com/search.ato...username&rpp=1]("http://search.twitter.com/search.atom?q=&tag=$tag&from=$username&rpp=1")";
 $content = file_get_contents($url);
 $content = explode('', $content);
 $content = explode('', $content[1]);
** $content = trim($content,'#mood');**
 return html_entity_decode($content[0])
 }
 // now use it
 $my_username = 'dolphinaura';
 $tag = 'mood';
 echo get_latest_tweet($my_username);
?>

```
however, that just gives the output of 'A'

---

### Post by TheOrangePeanut on 2010-12-13
Why not just use a replace to remove the tag?

```

$fetched_status = str_replace("#mood", '', $fetched_status);

```

---

