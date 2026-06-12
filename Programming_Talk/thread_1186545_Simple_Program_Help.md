---
title: "Simple Program Help"
date: 2009-06-13
forum: Programming Talk
---

### Post by ahop on 2009-06-13
I am a self-taught (amateur) programmer, sticking to PHP and javascript for web-programming.  I suppose I could build the application I am looking for with PHP, but really my needs are for a very simple script.  Here is what I am looking for:

I am looking to create a script that I can execute to pull all the images from my camera's SD card and save them in two places: (a) an external backup drive, (b) my local hard drive.  I am not sure what language would be best, and if anyone can help me put together something, I would be very grateful.

The images are stored as ```
/path/to/SD/Card/101_0613/IMG00001.PEF
```
*Note that the folder is saved with a number (101) followed by the month and date; file extension is capitalized*

I would like them saved as ```
/path/to/local/drive/for/processing/IMG00001.pef
``` and ```
/path/to/external/drive/for/archive/200906/IMG00001.pef
```
*Note the folder has been changed to year and month; file extension is now lower case*

If anyone has any thoughts on how to start (what language?) or any code snippets that would be awesome.

---

### Post by Mirge on 2009-06-13
If you're familiar with PHP already, use the PHP CLI to create a script that'll do it.

---

### Post by soltanis on 2009-06-13
A bash script would serve your purposes most easily (or a script written in whatever shell you use).

---

### Post by ahop on 2009-06-13
> **Mirge said:**
> If you're familiar with PHP already, use the PHP CLI to create a script that'll do it.

Hmmm . . . what a brilliant idea.  I have never really messed around with executing PHP from the command line before.  What a whole new world of possibilities! Thanks :)

Here is what I came up with:

```

<?php

$year = date('Y', time());
$source = "/path/to/SD/Card/";
$archive = "/path/to/external/drive/for/archive/";
$process = "/path/to/local/drive/for/processing/";

if(is_dir($source)){
	if($so = opendir($source)){
		while(($folder = readdir($so))!== false){
			if(preg_match('/[0-9]{3}_([0-9]{4})/', $folder, $date)){
				@mkdir($archive . $year . $date[1], 0777);
				@mkdir($process . $year . $date[1], 0777);
				if($si = opendir($source . $folder)){
					while(($file = readdir($si))!== false){
						if(preg_match('/([a-zA-Z0-9]*)\\.PEF/', $file, $name)){
							$newname = $name[1] . ".pef";
							$from = $source . $folder . "/" . $file;
							$to1 = $archive . $year . $date[1] . "/" . $newname;
							$to2 = $process . $year . $date[1] . "/" . $newname;

							echo "MOVING {$from} TO {$to1} . . .";
							if(copy($from, $to1)){ echo "complete\n"; }
							else{ echo "error\n"; }

							echo "MOVING {$from} TO {$to2} . . .";
							if(copy($from, $to2)){ echo "complete\n"; }
							else{ echo "error\n"; }

							echo "\n";
						}
					}
				}
				closedir($si);
			}
		}
		closedir($so);
	}
}
?>

```

I might still tweak it some, but for now it works pretty well.  I welcome comments from anyone who has any ideas.

---

### Post by Mirge on 2009-06-13
Now re-create it using PHP-GTK ([http://gtk.php.net/](http://gtk.php.net/)) or PHP-Qt ([http://www.php-qt.org/](http://www.php-qt.org/)).

Just kiddin :). Glad you got what you wanted done!

---

### Post by ahop on 2009-06-14
That's above my pay grade ;)

Thanks.

---

