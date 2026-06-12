---
title: "Some help with PHP"
date: 2009-03-05
forum: Programming Talk
---

### Post by gjoellee on 2009-03-05
Hi, I am writing a program named Kubus in PHP (it is some sort of an offline website), and I am going to make Kubus  be able to have addons. I don't know how to write the code I need!

OK, here are the facts:
All addons are installed in ./addons/<addon name>
All addons will have an index file, called "addindx.php", which is located in ./addons/<addon name>/addindx.php

I must have a php/css/html/js script that can search that folder(s) for the "addindx.php" and create a link to each addindx.php that exists (just simple <a href="URL">name</a>).

Note: The user might, install or remove the addons

If you need any more info, please tell...

---

### Post by jimi_hendrix on 2009-03-05
for the actual addon part you could use eval()  but that compromises security

---

### Post by Tibuda on 2009-03-05
I believe this is what you are looking for.[PHP]<?php
$addins = glob('addins/**/addindx.php');
foreach ($addins as $addin) {
  printf('<a href="%s">%s</a>', $addin, $addin);
}
?>[/PHP]You just need to find a way to get the addin name.

---

### Post by Peter76 on 2009-03-06
Hi, having flue and so being chained to my bed and learning PHP, I came up with the following solution:

[PHP]<?php
	echo '<ul id="addons">'.PHP_EOL;
	define( ADDONDIR, 'addons/' );			//define addon directory
	define( AINDEXNAME, 'addindx.php' );		//define name of addon index files
		
	$addon_contents = scandir( ADDONDIR );			// list contents in addon directory in array
	foreach( $addon_contents as $addon_item ) {
		$exclude = array( '.', '..' );
		if ( !in_array( $addon_item, $exclude ) && is_dir( ADDONDIR.$addon_item ) ) { // walk through addon dir and exclude .. and . and check if item is a dir. !NB is_dir needs absolute path to work.
			$addon_item_contents = scandir( ADDONDIR.$addon_item );
			if ( in_array( AINDEXNAME, $addon_item_contents ) ) { // Check if index file exists
				echo '<li><a href="'.ADDONDIR.$addon_item.'/'.AINDEXNAME.'">'.$addon_item.'</a></li>'.PHP_EOL;
			}
		}
	}
	echo '</ul>'.PHP_EOL;
?>[/PHP]

As said, I'm quite new to PHP, so if somebody has a better idea to this or some other tips I would like to hear it very much.
Hope this helps the OP as well.

---

### Post by Reiger on 2009-03-06
> **danielrmt said:**
> I believe this is what you are looking for.[PHP]<?php
$addins = glob('addins/**/addindx.php');
foreach ($addins as $addin) {
  printf('<a href="%s">%s</a>', $addin, $addin);
}
?>[/PHP]You just need to find a way to get the addin name.

Expanding this approach so it does the full magic:
[php]
$addons = glob('addons/**/addindx.php');
echo "<ul>";
foreach ($addons as $addon) {
   $bits = explode('/',$addon);
   $name = $bits[1]; // as per OP's specification of dir structure/names
   echo "<li><a href="$addon">$name</a></li>";
}
echo "</ul>";
[/php]

---

### Post by gjoellee on 2009-03-06
> **Reiger said:**
> Expanding this approach so it does the full magic:
[php]
<?php
$addons = glob('addons/**/addindx.php');
echo "<ul>";
foreach ($addons as $addon) {
   $bits = explode('/',$addon);
   $name = $bits[1]; // as per OP's specification of dir structure/names
   echo "<li><a href="$addon">$name</a></li>";
}
echo "</ul>";
?>
[/php]

Gives, ```
**Parse error**:  syntax error, unexpected T_VARIABLE, expecting ',' or ';' in **/path/to/file.php** on line **9**
```this is line 9

```
   echo "<li><a href="$addon">$name</a></li>";
```and I need one more thing. I don't have clean URL, so I must include a "?c=" in the URL so it reads of "index.php". That way I don't have to copy the theme files, and the content of my index.php again.

And one more thing: The name of the addon is stored in "addons/**/info/name.inc"

---

### Post by Peter76 on 2009-03-06
```
echo "<li><a href="$addon">$name</a></li>";
```

You should either escape the double qoutes like this:

```
echo "<li><a href=\"$addon\">$name</a></li>";
```

Or write it like this with single quotes ( Better IMHO )
```

echo '<li><a href="'.$addon.'">'.$name.'</a></li>';
```

Could you be a bit more elaborate on the not having a clean url thing? I haven't got a clue what you mean :-)

Good luck

---

### Post by Reiger on 2009-03-06
Ah I'm typing faster than I think or mistype what I think...
[php]
echo "<li><a href='$addon'>$name</a></li>";
[/echo]

Now with the unclean URL you presumably meant:
```

echo "<li><a href='**index.php?c=$addon**'>$name</a></li>"

```

That still leave the name to be resolved properly, though. Did you mean that the name of the dot inc file [name].inc is the name of the addon or that you can only know the name by reading a file always called name.inc?

If the latter:
[php]
$bits = explode('/',$addon);
$bits[2] = 'info/name.inc';
$path = implode('/',$bits);
/*
Now add code which reads & parses the file refered to by $path.
The name of the addon should be stored in $name.
*/
echo "<li><a href='index.php?c=$addon'>$name</a></li>";
[/php]

---

### Post by gjoellee on 2009-03-06
> **Reiger said:**
> Ah I'm typing faster than I think or mistype what I think...
[php]
echo "<li><a href='$addon'>$name</a></li>";
[/echo]

Now with the unclean URL you presumably meant:
```

echo "<li><a href='**index.php?c=$addon**'>$name</a></li>"

```That still leave the name to be resolved properly, though. Did you mean that the name of the dot inc file [name].inc is the name of the addon or that you can only know the name by reading a file always called name.inc?

If the latter:
[php]
$bits = explode('/',$addon);
$bits[2] = 'info/name.inc';
$path = implode('/',$bits);
/*
Now add code which reads & parses the file refered to by $path.
The name of the addon should be stored in $name.
*/
echo "<li><a href='index.php?c=$addon'>$name</a></li>";
[/php]

Yes. Inside the "name.inc" there is one line that contains the name. In this case the name.inc looks like this:
```
Random Tux
```"Random Tux" is written on line #1, and name.inc does not include any more than that.

However your code, does not give any errors now, but all I can see now is the "dot" from the <ul><li> tags. And after that, nothing. The name does not appear!

I can change the name to any file type, so if you need it to by as a .txt file, I will make the name in a .txt file.

---

### Post by gjoellee on 2009-03-07
BUMPedibum

---

### Post by gjoellee on 2009-03-08
pmub <-- Read backwards!

---

### Post by Tibuda on 2009-03-08
[http://www.php.net/manual/en/function.file-get-contents.php](http://www.php.net/manual/en/function.file-get-contents.php)

[PHP]<?php
$addins = glob('addins/**/addindx.php');
foreach ($addins as $addin) {
  $name = file_get_contents(dirname($addin) . '/name.inc');
  printf('<a href="%s">%s</a>', $addin, $name);
}
?> [/PHP]

---

