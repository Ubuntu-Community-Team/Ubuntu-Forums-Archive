---
title: "[SOLVED] php Question"
date: 2008-09-10
forum: Programming Talk
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

### Post by mike_g on 2008-09-10
I'm not sure if this is the easiest way to go about this, but heres my suggestion:

You could count the number of lines in the file by doing something like:
```
$lines = substr_count($content, '\n');
```
Then get a substring starting at the number of lines -50:
```
$line_no = ($lines-50 > 0) ? $lines-50: 0;
//get line start position
$pos = strnpos($content, '\n', $line_no); //using custom strnpos function
$content = substr($content, $pos);
```
From what I can tell on php.net there seems to be no function to get the position of the nth occurrence of a substring, but someone had posted a function to do this:
```
<?php

function strnpos($base, $str, $n)
    {       
        if ($n <= 0 || intval($n) != $n || substr_count($base, $str) < $n)  return FALSE;
       
        $str = strval($str);
        $len = 0;
       
        for ($i=0 ; $i<$n-1 ; ++$i)
        {
            if ( strpos($base, $str) === FALSE ) return FALSE;
           
            $len += strlen( substr($base, 0, strpos($base, $str) + strlen($str)) );
           
            $base = substr($base, strpos($base, $str) + strlen($str) );
        }
        return strpos($base, $str) + $len;
    }

?>
```
I havent tested it but hopefully it should do the job.

---

### Post by WorldTripping on 2008-09-10
I used
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

### Post by Reiger on 2008-09-10
Hmm there may be a better way but...
[php]
$lines = file($file_name);
$limit=count($lines); // or whatever the function is called that returns the size of an array...
for($k=$limit-50;$k<$limit;$k++)
    echo $lines[$k];
[/php]

Should do the trick?

---

