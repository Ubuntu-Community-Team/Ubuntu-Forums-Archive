---
title: "opendir() in PHP can only read current directory"
date: 2007-11-07
forum: Programming Talk
---

### Post by altonbr on 2007-11-07
I have an extremely simple script taken from [http://ca3.php.net/opendir](http://ca3.php.net/opendir) to count files inside a directory.

How come my top two $dir paths don't return a value? Is it a limitation of php-cli to read outside of the current directory?

```
<?php

//get path of directory containing this script
//$dir = "/home/brett/.wine/drive_c/Program\ Files/Rockstar\ Games/Grand\ Theft\ Auto\ Vice\ City/mp3/";
//$dir = "/home/brett/.wine/drive_c/Program Files/Rockstar Games/Grand Theft Auto Vice City/mp3/";
$dir = './';

//open a handle to the directory
$handle = opendir($dir);

//intitialize our counter
$count = 0;

//loop through the directory
while (false !== ($file = readdir($handle))) {
//evaluate each entry, removing the . & .. entries
	if (is_file($file) && $file !== '.' && $file !== '..') {
		$count++;
	}
}
echo ("-- $count files \n\r");

?>
```

---

### Post by ghostdog74 on 2007-11-07
because $dir has been assigned a new value each time. the final value of $dir is "./". if you want to get 3 different directories, you can loop over them.

---

### Post by carlosjuero on 2007-11-07
as ghostdog says, you are reinitializing $dir each time you assign a value to it in the top of the script - very bad method. You can loop through the values as ghostdog says, or you can assign the values to a $dir array ($dir[1] = first, $dir[2] = second, $dir[3] = third) example:

```

<?php

//get path of directory containing this script
$dir[1] = "/home/brett/.wine/drive_c/Program\ Files/Rockstar\ Games/Grand\ Theft\ Auto\ Vice\ City/mp3/";
$dir[2] = "/home/brett/.wine/drive_c/Program Files/Rockstar Games/Grand Theft Auto Vice City/mp3/";
$dir[3] = './';

//open a handle to the directory
//Added: Loop through the 3 folders in the array
for ($x = 1; $x < 4; $x++) {
$handle = opendir($dir[$x]);

//intitialize our counter
$count = 0;

//loop through the directory
while (false !== ($file = readdir($handle))) {
//evaluate each entry, removing the . & .. entries
	if (is_file($file) && $file !== '.' && $file !== '..') {
		$count++;
	}
}
echo ("-- $count files in $dir[$x] \n\r");
}
?>

```

---

### Post by altonbr on 2007-11-07
LOL. Oh lord. I should have commented them out. I just wanted to show you the other two choices I tried before './'. I never actually ran the script like that, sorry. I edited the post above.

---

### Post by carlosjuero on 2007-11-07
> **altonbr said:**
> LOL. Oh lord. I should have commented them out. I just wanted to show you the other two choices I tried before './'. I never actually ran the script like that, sorry. I edited the post above.
Ahh ok, now it makes sense. Have you tried the chdir() command to change PHP to the directory you want to count? [usage: chdir(path)]

---

