---
title: "Php: Remove first line from text file"
date: 2009-01-04
forum: Programming Talk
---

### Post by Dr Small on 2009-01-04
There should be someway to do this, only I have tried for several hours and nothing has worked properly.

Basically, I am setting a limit on how many lines this specific file may have. If the lines exceed limit, then remove the first line from the file and add the new line to the bottom. Sounds simple enough, eh?

The real problem is, getting rid of the first line. Is there any simple way to do this? If not, coming up with a function to do it would be suitable, yet my brain is just about out of spontaneous idea cells for the night.

Any help would be appreciated.
Dr Small

---

### Post by ghostdog74 on 2009-01-04
there are few ways:
1) if the file is not very big, get them all into array
```

$file="file";
$data = file_get_contents($file);

```
from there, remove the first element using array functions, which i will leave you to do yourself. 

2) read the first line, then continue the rest
```

$file=fopen("file","r");
$line=fgets($file);
while ( ($line = fgets($file,4096)) !==FALSE) {
  echo "$line";
}
   fclose($file);

```

---

### Post by Reiger on 2009-01-05
To read a file into an Array you use the file() function, not file_get_contents() which is used to read it into a String instead:

[php]
$filename = "/path/to/foo.txt"; // file name 
$LIMIT = 42;
$newLine = "bar"; // whatever is to be appended.
$file = file($filename);
$count = count($file);
if($count == $LIMIT) {
   $file = array_splice(&$file,0,1);
   $count = $LIMIT-1;
}
$file[$count]= $newLine;
file_put_contents($filename,implode(PHP_EOL,$file));
[/php]

The second approach has some benefit if you can write to that file at the same time as well...

---

### Post by Dr Small on 2009-01-05
> **Reiger said:**
> To read a file into an Array you use the file() function, not file_get_contents() which is used to read it into a String instead:

[php]
$filename = "/path/to/foo.txt"; // file name 
$LIMIT = 42;
$newLine = "bar"; // whatever is to be appended.
$file = file($filename);
$count = count($file);
if($count == $LIMIT) {
   $file = array_splice(&$file,0,1);
   $count = $LIMIT-1;
}
$file[$count]= $newLine;
file_put_contents($filename,implode(PHP_EOL,$file));
[/php]

The second approach has some benefit if you can write to that file at the same time as well...
That may work, although I haven't tried it. The tip about the array is what got my going in the right direction. Here's what I came up with and it worked, so I am happy for now :)
[php]$file = file(dirname(__FILE__)."/../tmp/rss_{$icao}-{$format}");
$newarray = array(
            0 => $datastring."\n",
            1 => $file[0],
            2 => $file[1],
            3 => $file[2],
            4 => $file[3]
            );

$fp = fopen(dirname(__FILE__)."/../tmp/rss_{$icao}-{$format}", "w");
foreach ($newarray as $line){
       fwrite($fp, $line);
}[/php]

Basically, I made a new array out of the old one, move the pieces around, opened the file with "w" to overwrite it, and wrote the new array to file. This way, the top string always gets pushed down one, and the bottom line never gets added to the new array, thence cuts it off.

Thanks for the help guys. I really do appreciate it!

Dr Small

---

