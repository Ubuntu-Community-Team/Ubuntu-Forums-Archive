---
title: "PHP preg_match / regex question"
date: 2012-07-05
forum: Programming Talk
---

### Post by ghandi69_ on 2012-07-05
Ok guys...

I grabbed some html code using the following command...

$content = file_get_contents('http://www.baseball-reference.com/players/d/dunnad01.shtml');

I am trying to grab all the text between "162 Game Avg" and the closest "</tr>" that follows it.

I'm basically using prag_match($pattern, $content, $match), but have been trying for quite some time now with no luck.

Would anyone be willing to view the source code of the above link... do a search for 162 Game Avg to see the portion of the page I'm looking at... and maybe give a few pointers?

Thanks for your time,

---

### Post by steeldriver on 2012-07-05
are you trying to match across multiple lines? if so then I think you will need the 's' modifier

[http://stackoverflow.com/questions/2240348/php-preg-replace-regex-that-matches-multiple-lines](http://stackoverflow.com/questions/2240348/php-preg-replace-regex-that-matches-multiple-lines)

[http://php.net/manual/en/reference.pcre.pattern.modifiers.php](http://php.net/manual/en/reference.pcre.pattern.modifiers.php)

---

### Post by spjackson on 2012-07-05
How about
```

<?php
  $content = file_get_contents('http://www.baseball-reference.com/players/d/dunnad01.shtml');

  if (preg_match('#(162 Game Avg)(.*?)(</tr>)#s', $content, $matches)) {
    echo $matches[2];
  }
  else {
    echo "not found\n";
  }
?>

```The s modifier at the end allows the dot to match newlines. The (.*?)  does a non greedy match so that we stop at the first </tr>.  There's more to do if you want to make it case insensitive etc.

---

### Post by ghandi69_ on 2012-07-05
> **spjackson said:**
> How about
```

<?php
  $content = file_get_contents('http://www.baseball-reference.com/players/d/dunnad01.shtml');

  if (preg_match('#(162 Game Avg)(.*?)(</tr>)#s', $content, $matches)) {
    echo $matches[2];
  }
  else {
    echo "not found\n";
  }
?>

```The s modifier at the end allows the dot to match newlines. The (.*?)  does a non greedy match so that we stop at the first </tr>.  There's more to do if you want to make it case insensitive etc.

Thanks I will give that a try.

I ended up doing a work around that isn't as clean but was able to give me the functionality I was looking for.  I still need to learn Regex though so I will be trying to understand the code you provided.  Here is what I ended up doing.

```
public function Player($name, $url){
	
		$this->name = $name;
		$content = file_get_contents($url);
		$matches = explode("\n", $content);
		$num = count($matches);
		$marker;
		for($i=0; $i < $num; $i++){
			if(strpos($matches[$i], "162 Game Avg")){
				$marker = $i;
			}
		}
```

---

