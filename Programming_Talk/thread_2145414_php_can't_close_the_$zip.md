---
title: "php can't close the $zip"
date: 2013-05-15
forum: Programming Talk
---

### Post by maclenin on 2013-05-15
Not clear what still needs doing.

I have this small bundle of php (zipTest.php)...
[PHP]<?php
$zip=new ZipArchive();
$files=array('a.txt', 'b.txt', 'c.txt');
$zipname='abc.zip';
if ($zip->open($zipname, ZipArchive::CREATE) !== TRUE) {die ('Could not open archive');}
foreach ($files as $file) {$zip->addFile($file) or die ('Could not add file');}
echo 'numFiles:', $zip->numFiles, '<br>status:', $zip->status;
$zip->close() or die ('<br>Could not close file');
?>[/PHP]
...in a virtually / locally hosted domain in my /home/directory....

Both /home/directory (drwxrwxr-x 2 homeUser homeUser) and zipTest.php (-rw-rw-r-- 1 homeUser homeUser) seem to have the requisite reads and writes in place to allow the abc.zip file to be built and written to the /home/directory (by the homeUser). 

When I access zipTest.php via the browser (as homeUser), this is what appears...
```
numFiles:3
status:0
Could not close file
```
...showing (it seems) that the ZipArchive is created, three files (a, b and c) are added to it (numFiles:3) and that all is so far so good (status:0) - until zipTest.php fails to close (finish creating) abc.zip!

Thanks for any suggestions.

NB: I have also "777'ed" both the directory and php file, which I thought might address potential www-data / apache permissions issues - with the same results.

---

### Post by SeijiSensei on 2013-05-15
I'd start by reading the comments posted [here](http://www.php.net/manual/en/ziparchive.close.php).

---

### Post by maclenin on 2013-05-15
**SeijiSensei!**

I think this [link]("http://davidwalsh.name/create-zip-php") is, perhaps, the best way to answer your question.

I have, essentially, put together a condensed version of the script, without the due dilligence that constitutes its first half....

...and, yep - I'd seen the comments you reference - and that's partly the reason I've come calling, because I feel that I am not violating any of those requirements....

Thanks, again, for any thoughts.

---

### Post by SeijiSensei on 2013-05-15
Well, you always write the file manually by using exec() to add each file with the command-line ZIP program.

```

<?php
$archive="myarchive.zip";

foreach ($filelist as $file) {
    exec("zip $archive $file");
}
?>

```
Or you could write a file to /tmp with the list of filenames to archive, then run "zip $archive -i $filelist" from exec().

---

### Post by maclenin on 2013-05-15
**SeijiSensei!**

I am pretty certain I have figured it out - it's a www-data permissions issue (after having performed a more comprehensive "777" test).... 

This [post]("http://ubuntuforums.org/showthread.php?t=2064042&p=12267362#post12267362"), actually, got me thinking more concertedly about sussing out www-data write permissions....

I think I'll stick with my original $zip line - and just tinker until I find a "match"....

Thanks for the commentary.

---

