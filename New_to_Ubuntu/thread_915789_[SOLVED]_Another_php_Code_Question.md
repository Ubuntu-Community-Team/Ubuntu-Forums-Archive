---
title: "[SOLVED] Another php Code Question"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by WorldTripping on 2008-09-10
I have this php code:

```
<?php
	if (isset($_GET['strMessage'])){
		if (file_exists('log.html')) {
		   $f = fopen('log.html',"a+");
		} else {
		   $f = fopen('log.html',"w+");
		}
		$write = isset($_GET['write']) ? $_GET['write'] : "Hidden";
		$message  = isset($_GET['strMessage']) ? htmlspecialchars($_GET['strMessage']) : ".";
		$line = "<p><span class=\"txtLogChatName\">$write: </span><span class=\"txtLogChatMessage\">$message</span></p>";
		fwrite($f,$line."\r\n");
		fclose($f);

		echo $line;

	} else if (isset($_GET['all'])) {
		$flag = file('log.html');
		$content = "";
		foreach ($flag as $value) {
			$content .= $value;
			}
		echo $content;
	}
?>
```

As you can see, it looks for the file 'log.html' and outputs it to screen.

How can I limit the output to the final 50 rows in 'log.html'

It is for a very simple flatfile chatroom and I don't want the whole of 'log.html' output when someone goes to the page.

Cheers in advance.

---

### Post by jemate18 on 2008-09-10
> **WorldTripping said:**
> I have this php code:

```
<?php
	if (isset($_GET['strMessage'])){
		if (file_exists('log.html')) {
		   $f = fopen('log.html',"a+");
		} else {
		   $f = fopen('log.html',"w+");
		}
		$write = isset($_GET['write']) ? $_GET['write'] : "Hidden";
		$message  = isset($_GET['strMessage']) ? htmlspecialchars($_GET['strMessage']) : ".";
		$line = "<p><span class=\"txtLogChatName\">$write: </span><span class=\"txtLogChatMessage\">$message</span></p>";
		fwrite($f,$line."\r\n");
		fclose($f);

		echo $line;

	} else if (isset($_GET['all'])) {
		$flag = file('log.html');
		$content = "";
		foreach ($flag as $value) {
			$content .= $value;
			}
		echo $content;
	}
?>
```

As you can see, it looks for the file 'log.html' and outputs it to screen.

How can I limit the output to the final 50 rows in 'log.html'

It is for a very simple flatfile chatroom and I don't want the whole of 'log.html' output when someone goes to the page.

Cheers in advance.

May be guys from the php forum may help...
No biggie..

---

### Post by WorldTripping on 2008-09-10
> **jemate18 said:**
> May be guys from the php forum may help...
No biggie..

Ah, OK

Could someone move it for me then please ?

Cheers.

---

### Post by NoReflex on 2008-09-10
I guess you could replace the for loop with a system command like : 
```
system("tail -n 50 log.html",$ret_val);
$content = $ret_val;
```

Best wishes,
NoReflex

---

### Post by WorldTripping on 2008-09-10
> **NoReflex said:**
> I guess you could replace the for loop with a system command like : 
```
system("tail -n 50 log.html",$ret_val);
$content = $ret_val;
```

Best wishes,
NoReflex

As suggested, I used
```
system("tail -n 25 log.html", $ret_val);
$content = $ret_val;
```

and it seems to work OK, except for a '0' that works its way down the screen of comments.

It must be something to do with the code I added as it wasn't there before.

It moves every time the timer refreshes the screen. I'll look into that later though.

```

<?php
	if (isset($_GET['strMessage'])){
		if (file_exists('log.html')) {
		   $f = fopen('log.html',"a+");
		} else {
		   $f = fopen('log.html',"w+");
		}
		$write = isset($_GET['write']) ? $_GET['write'] : "Hidden";
		$message  = isset($_GET['strMessage']) ? htmlspecialchars($_GET['strMessage']) : ".";
		$line = "<p><span class=\"txtLogChatName\">$write: </span><span class=\"txtLogChatMessage\">$message</span></p>";
		fwrite($f,$line."\r\n");
		fclose($f);

		echo $line;

	} else if (isset($_GET['all'])) {
		$flag = file('log.html');
		$content = "";
[COLOR="Red"]		system("tail -n 25 log.html", $ret_val);
		$content = $ret_val;[/COLOR]

		echo $content;
	}
?>

```

Thanks for everyones time.

---

